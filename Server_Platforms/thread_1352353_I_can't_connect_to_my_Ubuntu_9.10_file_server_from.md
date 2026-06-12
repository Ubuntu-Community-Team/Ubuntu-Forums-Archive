---
title: "I can't connect to my Ubuntu 9.10 file server from my laptop running Ubuntu 9.10"
date: 2009-12-11
forum: Server Platforms
---

### Post by metalf8801 on 2009-12-11
I can't connect to my Ubuntu 9.10 file server from my laptop running Ubuntu 9.10 desktop well sometime I can connect enough to see the files on the server but I can add new files to the server or copy files off the servers from to my laptop.  On the other hand I can connect fully from my desktop running Windows XP.  I used to be able to connect to the server using both computers but its been about a month sins I was able to connect using my laptop.  


any advice you can give me would be great 
thanks 
Dan

---

### Post by munky99999 on 2009-12-11
How about some base info.

Ip addy of each box.
Can you ping each box?
what error pops up?
can other boxes reach the file server?

---

### Post by metalf8801 on 2009-12-11
> **munky99999 said:**
> How about some base info.

Ip addy of each box.
Can you ping each box?
what error pops up?
can other boxes reach the file server?

the ip addresses are dynamic I normally just enter the name of the server 
I can connect to the sever using webmin and Putty from my laptop in case that matters 

I'll get the rest in a minute

---

### Post by metalf8801 on 2009-12-11
yes I can ping the server 

when i try to connect by 
Places > connect to server
then Using SSH 
I get this error 
Cannot display location "sftp://daniel@dilbert/"

---

### Post by PadawanGeek on 2009-12-11
Is the IP for your server (dilbert) in your /etc/hosts file on your laptop?

---

### Post by metalf8801 on 2009-12-11
Now I can connect using Samba which I couldn't do last night so idk whats going on there.  I still can't connect using FTP when I try I get a error message saying "Error connecting: Connection refused"

---

