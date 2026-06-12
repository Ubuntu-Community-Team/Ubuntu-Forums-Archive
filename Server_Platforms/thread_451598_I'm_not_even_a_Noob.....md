---
title: "I'm not even a Noob...."
date: 2007-05-22
forum: Server Platforms
---

### Post by thunderkyss on 2007-05-22
I'm a Network Security & IP protocol idiot. 

I've got questions.. because I'd like to understand.

For starters, it is my understanding, that other folks can access my computer over the internet without me knowing, unless I stop them. Is there anything in Ubuntu that is set up by default to do this, or am I SOL if I don't startup the firewall?? I'm asking as if my computer was hooked directly to my DSL modem.

Second question. Ports. Are these the only way into & out of my computer?? Ports, is that TCP/IP ports, or are there other kinds of "Ports"?? 

& How many of these ports are there??

---

### Post by techpro619 on 2007-05-22
Yea there are all kinds of ports but I don't think Ubuntu in any form has anything open by default, at least the server doesn't.

---

### Post by Chayak on 2007-05-22
Ubuntu is pretty good about not having open ports.  To start off use a strong password and install firestarter.  That will keep the skiddies out.

---

### Post by thunderkyss on 2007-05-22
thanks for replying techpro & chayak...

So, TCP/IP is the only way into my computer, and Ubuntu keeps the doors shut... good.

Now, applications on my computer asks to open ports right?? Let's say Firefox opens a port, & I go to a website. Can anyone else high-jack that connection?? Can that website do things I don't want it to?? Is there something in Firefox or Ubuntu or both to prevent this??

---

### Post by yey365 on 2007-05-22
sudo nmap -sS -sV -P0 127.0.0.1
sudo nmap -sS -sV -P0 youripaddress (find it with ifconfig in terminal)

This will show you the open ports on your system

Jim

---

### Post by Brackish_zygote on 2007-05-23
I know cookies can contain malicious code. I don't know about high jacking a connection. However, it is my understanding that if a port is opened, then it leaves the computer vulnerable to attacks. Isn't this true?

---

### Post by twistedtwig on 2007-05-23
I think for a port to be used in this way something has to be listening to that port.  For example if 5678 was open but nothing listening on it its a dead end so no hacking is possible.

But I could be wrong about that... (hope not).

---

### Post by thunderkyss on 2007-05-23
> **twistedtwig said:**
> I think for a port to be used in this way something has to be listening to that port.  For example if 5678 was open but nothing listening on it its a dead end so no hacking is possible.

But I could be wrong about that... (hope not).

the way I understand it, is that hackers are constantly looking for open ports. So while nothing maybe happening on that open port now, it's just a matter of time before someone uses it.

---

