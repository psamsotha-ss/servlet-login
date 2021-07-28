# Simple Servlet Login Example

## Run

```shell
$ git clone https://github.com/psamsotha-ss/servlet-login.git
$ cd servlet-login
$ ./mvnw clean package jetty:run
```

If you are using Windows, use the `mvnw.bat` file. `mvnw` is a wrapper for Maven, similar to the Gradle wrapper. It allows people to run Maven without actually installing Maven locally. The command `mvnw` is just like running `mvn`. The `mvnw(.bat)` script is included in the project. If you have Maven installed locally, you can use `mvn` instead.

## Access Login

Go to `localhost:8000`. There will be a login page. The username is `smoothstack` and the password is `secret`.

## Servlet Code

```java
@WebServlet(name = "LoginServlet", urlPatterns = "/login")
public class LoginServlet extends HttpServlet {

    @Override
    public void doPost(HttpServletRequest request, HttpServletResponse response) throws IOException {
        String username = request.getParameter("username");
        String password = request.getParameter("password");

        if ("smoothstack".equals(username) && "secret".equals(password)) {
            response.sendRedirect("/home.html?user=" + username);
            return;
        }

        response.sendRedirect("/index.html?loginError");
    }
}
```
