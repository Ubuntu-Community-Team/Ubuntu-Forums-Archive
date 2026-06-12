---
title: "Listening ports?"
date: 2006-02-12
forum: Server Platforms
---

### Post by Jimmey on 2006-02-12
I was wondering about just how secure my laptop really was, earlier this morning. Instead of using nmap to check it out, which I usually point to my static lan IP ( 192.168.1.199 ) I used Ubuntu's network tools to do a netstat. It returned this :
> tcp          127.0.0.1          32770          LISTEN
tcp         127.0.0.1          32771          LISTEN

There where in total four entries similar to this one. So I turned to nmap, and tried with 127.0.0.1 this time, instead of my LAN ip. It produced the same results - And I'm left wondering why there's listening services, that I didn't set up, on at least three pots.

When I checked nmap to my LAN ip, it returned just one open port - the one I want to be open. 

So what's going on? Is Ubuntu using these ports? If not, what is? And are these ports visible to the world?

---

### Post by heimo on 2006-02-12
Run 
```
sudo /etc/init.d/hplip stop
```
and see if those ports are still listening local connections.

---

### Post by Jimmey on 2006-02-12
What does that do?

---

### Post by heimo on 2006-02-12
[quote=Jimmey]What does that do?[/quote]
Stops "HP Linux Printing and Imaging System"

---

### Post by Jimmey on 2006-02-12
Thanks! I just learned something new :)

---

### Post by steve.horsley on 2006-02-12
Those are not a security issue. No machine other than your own is able to connect to port 127.0.0.1. So they are "private" services.

---

