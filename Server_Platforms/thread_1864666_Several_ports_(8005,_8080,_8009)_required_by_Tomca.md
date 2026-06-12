---
title: "Several ports (8005, 8080, 8009) required by Tomcat Server at localhost:8080"
date: 2011-10-19
forum: Server Platforms
---

### Post by 1cookie on 2011-10-19
hi

I'm trying to configure Eclipse IDE to work with JavaEE and all the bells and whistles in particular Java web Applications. I'm using this tutorial as a bench mark.

[http://www.vogella.de/articles/EclipseWTP/article.html](http://www.vogella.de/articles/EclipseWTP/article.html)

Ive followed all the instructions to the letter, only upon running the Servlet I get the following error:

```

Several ports (8005, 8080, 8009) required by Tomcat v7.0 Server at localhost:8080 are already in use. The server may already be running in another process, or a system process may be using the port. To start this server you will need to stop the other process or change the port number(s).

```As far as i know all components are fine. Apache tomcat (localhost:8080) displays in the browser, ANT is installed correctly etc.

Heres a snippet from the shell:

```

andy@andy-R519-R719:/$ netstat -an | grep LISTEN
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN     
tcp6       0      0 :::9000                 :::*                    LISTEN     
tcp6       0      0 :::8009                 :::*                    LISTEN     
tcp6       0      0 :::10000                :::*                    LISTEN     
tcp6       0      0 :::8080                 :::*                    LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 ::1:48758               :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     



```Can anyone offer some insight as to get Eclipse running my servlets? 

;)

---

