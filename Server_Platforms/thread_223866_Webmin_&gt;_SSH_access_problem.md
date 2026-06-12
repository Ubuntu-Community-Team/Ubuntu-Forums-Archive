---
title: "Webmin &gt; SSH access problem"
date: 2006-07-27
forum: Server Platforms
---

### Post by ktgeorge on 2006-07-27
I installed webmin. I try to connect from net with ssh login over webmin (section others), but i see the error "There is no SSH server running on www.***.com" port 22". But sshd runs on port 22 because i can connect from putty. Any ideas?

---

### Post by muzzamo on 2007-03-19
I have this same problem... can anyone else help?

---

### Post by ariejan on 2007-03-19
is [www.***.com](www.***.com) the same addess as where you are accessing webmin? 

This is a JAVA issue. An applet loaded from example1.com cannot connect to any other address than example1.com. This is to prevent JAVA applets from connecting to other sites than the user intends. 

Why not just use putty anyways? Webmin is a security risk waiting to be exploited at some point.

---

### Post by duvan on 2007-06-20
I have the same problem
I still want to resolve the issue
Webmin is an amazing piece of software for admins

---

### Post by duvan on 2007-06-20
under servers go to SSH and click configuration make sure you have the correct port.
Try to restart the SSH 
The java applet from SSH/telnet client is suppose to come up, if not make sure java is working properly on your computer.

---

### Post by dsartain6wt2 on 2007-11-15
I'm having the same issue...I can connect to my server via SSH through port 290 with putty, both by domain and local IP, but when I use webmin I get that "There is no SSH Server on domain on port 290" error...do I have to have java installed on the server for this to work??  Wouldn't that have installed as a webmin dependancy??

I have java on my pc (both of them) and it works fine on other things...


Ideas???

---

