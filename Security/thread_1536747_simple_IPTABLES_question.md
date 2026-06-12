---
title: "simple IPTABLES question"
date: 2010-07-22
forum: Security
---

### Post by rugbert on 2010-07-22
Im setting up a new Ubuntu 9.4 server install and am working on the iptables. Im basically just going to drop anything I dont use and change the ports on stuff I do use, BUT I need to be able to run updates or use apt-get to install packages.

right now Im only allowing two things, incoming on ports 80 and my changed ssh port. Im dropping everything else.

But that kill apt for me, I cant update or install new stuff.

I tried ```
iptables -I INPUT 1 -p tcp -s us.archives.ubuntu.com -j ALLOW
```
but the iptable wont take. What should I do?

---

### Post by bodhi.zazen on 2010-07-22
Read about how iptables works =)

You do not need to allow incoming new connections on port 80 to be able to update and you will need to allow traffic to additional ports (53 for DNS for example).

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

So when you connect to a web server, you use a high port (above 1024) on your computer to connect to port 80 on the server.

If you do not understand that concept ^^, you are dead in the water.

---

### Post by rugbert on 2010-07-22
> **bodhi.zazen said:**
> Read about how iptables works =)

You do not need to allow incoming new connections on port 80 to be able to update and you will need to allow traffic to additional ports (53 for DNS for example).

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

So when you connect to a web server, you use a high port (above 1024) on your computer to connect to port 80 on the server.

If you do not understand that concept ^^, you are dead in the water.

I added 
```
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
``` and that worked

---

### Post by bodhi.zazen on 2010-07-22
> **rugbert said:**
> I added 
```
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
``` and that worked

Sweet -)

```
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```Is what I use. Your changes will be lost when you reboot unless you make some adjustments, either a  script, or I prefer iptables-save / iptables-apply , your choice.

Once you learn you way around iptables it becomes a very powerful tool. Keep reading and asking questions.

---

