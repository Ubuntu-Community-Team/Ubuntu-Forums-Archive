---
title: "Lighttpd CGI SHELL script and status code"
date: 2012-07-02
forum: Server Platforms
---

### Post by Tomaok on 2012-07-02
Hello,

I'm used to execute some shell script through Web application ( HTML/Javascript )
with httpd ( on  an embedded system )

I would like to do the same with Lighttpd But i've a problem with the status code which 
seems to be interpreted differently by Lighttpd !

In Fact i don't known how to write this status code for Lighttpd !

With httpd i end my shell script with : echo "HTTP/1.0 204 OK"

If i do the same with Lighttpd , the status returned to browser is always 200 and not 204!
The problem here is that this wrong status send me a popup windows to save the result of my script each time i want to execute this one !

Any  idea to solve this will be very appreciated ...

In another words what i want is to execute a shell script through cgi from my Web apps
without returning content to the browser!
It 's a simple task but i can't find anything  to do that with Lighty !

Bye...

---

### Post by Tomaok on 2012-07-06
la reponse est XMLHTTPrequest

---

