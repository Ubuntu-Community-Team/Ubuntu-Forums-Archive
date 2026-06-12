---
title: "Can't get correct output for .jsp"
date: 2009-11-10
forum: Server Platforms
---

### Post by chandubaba on 2009-11-10
<html>
<body>
hi
</body>
</html>

I wrote this as date.jsp 

but the output in browser is this

<html>
<body>
hi
</body>
</html>

exact same thing

I have started apache by running command sudo /etc/init.d/apache2 start
and then run in browser [http://localhost/date.jsp](http://localhost/date.jsp)
the file saved in the default path for apache configration
/var/www/
so how to view the date.jsp file?

---

### Post by mrsteveman1 on 2009-11-10
Rename it date.html and the browser should render it.

If you're doing java servlet programming you'll need tomcat or something running to serve the page.

---

### Post by chandubaba on 2009-11-10
yeah i want to do jsp programming .. and it is my first program... I have tomcat but don't know how to use it to serve the page! Please tell me how to do it.

---

### Post by mrsteveman1 on 2009-11-12
My experience with tomcat extends only to installing the Subsonic streaming server 4 years ago, sorry :)

There must be some tutorials on servlet programming around here though.

---

### Post by sicn on 2009-11-16
Do "apt-get install tomcat6" (you dont need Apache2 in your case). If you haven't installed Java already, it will install a lot of packages, i.e. openjdk, tomcat, a number of java libraries.

When it is done, you should have a folder called /var/lib/tomcat6/webapps

In this folder you do following

1.) mkdir -p myfirstjsp/WEB-INF
2.) in myfirstjsp/WEB-INF you create a web.xml, which contains:
```

<web-app xmlns="http://java.sun.com/xml/ns/javaee"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd"
 version="2.5">
 <display-name>MyFirstJavaApp</display-name>
 <welcome-file-list>
  <welcome-file>index.jsp</welcome-file>
 </welcome-file-list>
</web-app>

```
I know, this is a real mouthful, but believe me. after a while you will easily understand these things and most development tools actually do this for you!

3.) Create an index.jsp in myfirstjsp (this is the "welcome-file", i.e. the file which is loaded by default if you don't enter any in the browser) which contains something "java"-ish, i.e.

```

<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
  <head>
     <title>Hello World!</title>
  </head>
  <body>
    <%= "The answer: " + (7*6)%>
  </body>
</html>
 
```

4.) Start Tomcat by typing /etc/init.d/tomcat6 start
5.) Go to your browser and type [http://localhost:8080/myfirstjsp](http://localhost:8080/myfirstjsp)

So, what is the <%=%>-thingy? It's a JSP Scriptlet, it will parse Java code and produce standard text from it and embedd it in your HTML... In your case you should see a page saying "The answer: 42".

And why is it myfirstjsp? Well, the folder we created is called myfirstjsp, wasn't it? ;)

And last but not least, what is the web.xml for? Well, it is the Web Application Deployment Descriptor. In bigger applications it contains configuration which is necessary so the server knows how to serve all your Servlets, JSPs, etc.

Now good luck with it and hopefully we will soon find you amongst the Java-devoted community of programmers ;)

/Daniel

PS.: Once you understand how JSP and Servlets work, you may want to look at Frameworks like Struts 2.1 or JSF, those will make it a lot easier to write bigger web applications.

---

