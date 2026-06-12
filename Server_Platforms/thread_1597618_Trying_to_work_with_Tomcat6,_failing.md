---
title: "Trying to work with Tomcat6, failing"
date: 2010-10-15
forum: Server Platforms
---

### Post by elebrin on 2010-10-15
I think I need some help with tomcat6.  The easy way to do this would probably to post the file I am trying to compile, and to errors I am getting:
```

import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class HelloWorld extends HttpServlet {
        public void doGet(HttpServletRequest request, 
                          HttpServletResponse response)
                          throws ServletException, IOException {
        PrintWriter out = response.getWriter();
        out.println("Hello, World!");
        }
}

```

Here's the errors:

```

HelloWorld.java:3: package javax.servlet does not exist
import javax.servlet.*;
^
HelloWorld.java:4: package javax.servlet.http does not exist
import javax.servlet.http.*;
^
HelloWorld.java:6: cannot find symbol
symbol: class HttpServlet
public class HelloWorld extends HttpServlet {
                                ^
HelloWorld.java:7: cannot find symbol
symbol  : class HttpServletRequest
location: class HelloWorld
        public void doGet(HttpServletRequest request, 
                          ^
HelloWorld.java:8: cannot find symbol
symbol  : class HttpServletResponse
location: class HelloWorld
                          HttpServletResponse response)
                          ^
HelloWorld.java:9: cannot find symbol
symbol  : class ServletException
location: class HelloWorld
                          throws ServletException, IOException {
                                 ^

```

I remember getting errors like these when my classpath was wrong when I was first learning java, but I have no idea what to even set it to so its using the tomcat stuff.  

Its odd though because the examples in the examples package work (although I suppose those are already compiled), even though I can't find them in the filesystem...

Maybe I just need a solid tutorial on getting started with Tomcat building servlets.  None of the ones I have found have worked.  Sorry for n00bing it up, but can anyone help me?

---

