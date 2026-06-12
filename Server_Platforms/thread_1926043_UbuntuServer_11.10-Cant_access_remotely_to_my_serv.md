---
title: "UbuntuServer 11.10-Cant access remotely to my server"
date: 2012-02-15
forum: Server Platforms
---

### Post by barezi6 on 2012-02-15
Hi everyone, I configured my new server with ubuntu 11.10, and everything is work great, lamp with php5, mysql, phpmyadmin etc, but i can access to my server by the filezilla, i can access by ssh root, by the terminal on mac os x, but cant access by filezilla, what maybe is wrong? i tried to unblock the 80 ports and 22 ports, but when i tried canyouseeme, it tell me that they still blocked, but in other time i used ubuntu 8.04 LTS and didnt unblock port 22, only port 80, i could acces by the filezilla.

What can i do? 

Thanks :)

---

### Post by brent1975 on 2012-02-15
are you doing sftp://domain.com? port 80 is not something that you need to worry about with ssh. typically all you need to do is open port 22 on the router and enable it on your fire wall on your server if you are using that. What error messages are you getting?

---

### Post by barezi6 on 2012-02-15
> **brent1975 said:**
> are you doing sftp://domain.com? port 80 is not something that you need to worry about with ssh. typically all you need to do is open port 22 on the router and enable it on your fire wall on your server if you are using that. What error messages are you getting?

thanks for the help brent1975, i am using sftp://MyMachineIP and i know that it is well, the error is:

Connection refused

---

