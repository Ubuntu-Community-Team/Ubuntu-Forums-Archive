---
title: "Tomcat/Ant build.xml not compiling"
date: 2008-10-11
forum: Server Platforms
---

### Post by Niffy on 2008-10-11
I'm pretty new to all this tomcat and ant stuff so I'm struggling to get this to work.

I used this guide to install tomcat
[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

and I have installed ant using
sudo apt-get install ant ant-optional

in my folder of the app(/home/machine/Hello)
I ran build.xml
I got the error
```
taskdef class org.apache.catalina.ant.ListTask cannot be found
```
I solved this
```

sudo cp /usr/local/tomcat/lib/catalina-ant.jar /usr/share/ant/lib

```
Any idea how to fix the next problem?  Probably some files not in the correct location?
Now I get the following problem when running ant build
```

Buildfile: build.xml
init:
prepare:
build:
    [javac] Compiling 1 source file to /home/machine/Hello/build/WEB-INF/classes
    [javac] /home/machine/Hello/src/Hello.java:2: package javax.servlet does not exist
    [javac] import javax.servlet.*;
    [javac] ^
    [javac] /home/machine/Hello/src/Hello.java:3: package javax.servlet.http does not exist
    [javac] import javax.servlet.http.*;
    [javac] ^
    [javac] /home/machine/Hello/src/Hello.java:6: cannot find symbol
    [javac] symbol: class HttpServlet
    [javac] public class Hello extends HttpServlet {
    [javac]                            ^
    [javac] /home/machine/Hello/src/Hello.java:12: cannot find symbol
    [javac] symbol  : class ServletException
    [javac] location: class Hello
    [javac]     public void init() throws ServletException {
    [javac]                               ^
    [javac] /home/machine/Hello/src/Hello.java:18: cannot find symbol
    [javac] symbol  : class HttpServletRequest
    [javac] location: class Hello
    [javac]     public void doGet(HttpServletRequest request,
    [javac]                       ^
    [javac] /home/machine/Hello/src/Hello.java:19: cannot find symbol
    [javac] symbol  : class HttpServletResponse
    [javac] location: class Hello
    [javac]                       HttpServletResponse response) throws ServletException,
    [javac]                       ^
    [javac] /home/machine/Hello/src/Hello.java:19: cannot find symbol
    [javac] symbol  : class ServletException
    [javac] location: class Hello
    [javac]                       HttpServletResponse response) throws ServletException,
    [javac]                                                            ^
    [javac] 7 errors

BUILD FAILED
/home/machine/Hello/build.xml:55: Compile failed; see the compiler error output for details.

```

---

