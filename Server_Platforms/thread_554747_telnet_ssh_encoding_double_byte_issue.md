---
title: "telnet ssh encoding double byte issue"
date: 2007-09-19
forum: Server Platforms
---

### Post by sarath_it on 2007-09-19
I am unsure if this is the right forum to put this question in. 

I have a Java program that saves a clob data from database to a file. the content is UTF-8 encoded. text includes some spanish content

I have to run this program on a server. 

Now interestingly, if i connect to the server using telnet port 23, i have no problem to see data (accented charcters are shown correctly)

but if i connect using SSH, i get all ? in the saved file.

I cannot suspect the program because the only variable here is the port number. 

Any pointers? Does anyone know any setting that is missing in SSH config on the server or the client?

Sarath.

---

### Post by digitalbenji on 2007-09-19
Just to be clear, the server is running SSH or telnet or both?

---

### Post by sarath_it on 2007-09-19
both

---

### Post by digitalbenji on 2007-09-19
I don't know

---

