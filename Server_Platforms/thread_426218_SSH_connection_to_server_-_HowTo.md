---
title: "SSH connection to server - HowTo"
date: 2007-04-28
forum: Server Platforms
---

### Post by Roman78 on 2007-04-28
I have a ubuntu 6.06 server running. It's running fine now. But i want to make a SSH connection to te server to mantain the server. 

For windows i use PuTTY, that's working fine. But now i want to connect a Ubuntu 6,10 desktop computer to the server, but how???

I can't work whit the man pages and also internet gives no good ansers.

Server ip is 192.168.2.11 and the SSH port is changed to 220.

---

### Post by Bubba Ho-Tep on 2007-04-28
Open a command line.

type : 

sudo ssh -D 220 -l userrname servername (or server IP)


the -D switch alters the port to whatever you want (220 in this case) and cos you are using sudo it will try to log in as root - so use the  -l switch to specify which user you want to log in as.

And mate you need to learn to work with the man pages - I didn't know myself how to specify the port it took me 15 seconds to find out.

man ssh 

to search a man page type a "/" and then your search term. So I did /port which led me to the D switch.

---

### Post by gunthr on 2007-04-28
Why not just...

ssh username@servername -p 220

---

