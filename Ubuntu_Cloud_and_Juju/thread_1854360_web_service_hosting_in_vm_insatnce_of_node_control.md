---
title: "web service hosting in vm insatnce of node controller"
date: 2011-10-04
forum: Ubuntu Cloud and Juju
---

### Post by chetna on 2011-10-04
I have running VM instance in node controller of UEC.

I  have apache tomcat web server running in that VM  instance.

I have deployed web services in apache tomcat web server and tried connecting to that  web  service from client.But unable to do so.

Can  you please suggest as to how to connect to the web services hosted in vm  instances of node controller from clients browser (i am using mozilla firefox).


I tried with URL 

[https://172.16.32.60:8080/mywebservice/index.jsp](https://172.16.32.60:8080/mywebservice/index.jsp)

(where 172.16.32.60 is public-ip of my VM instance  and 8080 is the port where tomcat server is running)


But it gives following error

The connection has timed out

The server at 172.16.32.60 is taking too long to respond.


Can someone please suggest how to resolve this issue.I will really appreciate some suggestions to resolve this.

Thanks in advance...

---

### Post by lcman on 2011-10-06
> **chetna said:**
> I have running VM instance in node controller of UEC.

I  have apache tomcat web server running in that VM  instance.

I have deployed web services in apache tomcat web server and tried connecting to that  web  service from client.But unable to do so.

Can  you please suggest as to how to connect to the web services hosted in vm  instances of node controller from clients browser (i am using mozilla firefox).


I tried with URL 

[https://172.16.32.60:8080/mywebservice/index.jsp](https://172.16.32.60:8080/mywebservice/index.jsp)

(where 172.16.32.60 is public-ip of my VM instance  and 8080 is the port where tomcat server is running)


But it gives following error

The connection has timed out

The server at 172.16.32.60 is taking too long to respond.


Can someone please suggest how to resolve this issue.I will really appreciate some suggestions to resolve this.

Thanks in advance...

I've never worked with tomcat but I believe it is only accessible by apache because it's apache that is going to serve the app. When a script is requested, apache will ask tomcat server to process the script and send the output. Apache will then return something to the client.

Now, I might be wrong! You should make sure apache is running before doing anything:
```
ps aux | grep apache2
```

---

