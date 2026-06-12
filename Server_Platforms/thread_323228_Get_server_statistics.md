---
title: "Get server statistics"
date: 2006-12-21
forum: Server Platforms
---

### Post by rado_london on 2006-12-21
Hi
I just installed XAMPP and did a server.
I want to find a program which is CLI and shows the server stats in realtime. By stats I mean how many users are logged in,what is the system load etc

Well Im waiting for your responces

Thanks

---

### Post by maddog39 on 2006-12-21
There is no such thing as far as I know. However, I do believe there are some PHP scripts that do some things similar.

---

### Post by MJN on 2006-12-22
Does **top** not suffice?
 
Mathew

---

### Post by rado_london on 2006-12-22
> **MJN said:**
> Does **top** not suffice?
 
Mathew

Yeah I will use top. :)

---

### Post by tjansson on 2006-12-23
I have installed gkrellmd on my servers and monitors them realtime through a ssh tunnel. See this picture: [http://www.tjansson.dk/phpAlbum/main.php?cmd=imageview&var1=screenshots%2Fgkrellm.png&var2=1](http://www.tjansson.dk/phpAlbum/main.php?cmd=imageview&var1=screenshots%2Fgkrellm.png&var2=1)

Yet another solution is phpsysinfo.

---

### Post by cyracks on 2006-12-23
[http://www.zabbix.com/](http://www.zabbix.com/)

---

### Post by MJN on 2006-12-23
Guys, the OP said it needs to be CLI so put your flashy toys away! ;)
 
Mathew
 
(I am a fan of GKrellM though!)

---

### Post by petok on 2006-12-24
top is nice, but htop is better;)

---

### Post by rado_london on 2006-12-24
> **petok said:**
> top is nice, but htop is better;)

Just tried htop and I must say it is amaizing:D:D
Thanks for the advice:)

---

