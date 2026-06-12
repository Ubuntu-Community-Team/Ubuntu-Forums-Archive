---
title: "Terminal Client on Sidekick (danger hiptop)"
date: 2006-02-01
forum: The Cafe
---

### Post by msg on 2006-02-01
Grr, I say.

Im sorta a linux "noob" however I know the basic stuff

My friend downloaded the "Terminal Client" application to my sidekick (its a GRPS internet phone with a full keyboard). He said I could control my Linux box remotely with it. After playing around for 15 minutes, I couldn't get it to work. The app costed 10 bucks, so I dont wanna just delete it. The main menu looks something like this:

-----------------------------------
Name: ______________
Host:   ______________
Protocol: (drop down menu) SSH2/Telnet/Raw

[Connect]     [Save]
-----------------------------------


My "friend" said to put my username in "name" and my IP address under "host" and use SSH2 .... connection failed\\:D/.  Is there something I need to enable on my computer? Help Please!

---

### Post by briancurtin on 2006-02-01
first off, do you have SSH enabled on your computer?

---

### Post by msg on 2006-02-02
Im not sure, how do I enable it?

---

### Post by mishathegoat on 2008-01-02
I also bought Sidekick's "Terminal Client"

...

BUMP

---

### Post by Lostincyberspace on 2008-01-02
You need to install openssh-server
Just run
[QCODE]sudo apt-get install openssh-server[/CODE]
and it should work then.

---

### Post by Crashmaxx on 2008-01-03
> **Lostincyberspace said:**
> You need to install openssh-server
Just run
[QCODE]sudo apt-get install openssh-server[/CODE]
and it should work then.

Little be more to it then that, start with this guide:
[https://help.ubuntu.com/7.10/server/C/openssh-server.html](https://help.ubuntu.com/7.10/server/C/openssh-server.html)

And you will probably need to also forward port 2222 on your router and use something like DynDNS.org to find your computer, and it obviously must be on at the time.

---

### Post by BiiPiiGii on 2009-09-27
I also downloaded it for my phone.  I don't even care to have it control my box, I'd like to chat on IRC with it though and do some other admin stuff.  Anyone know how to configure this program, it would be awesome if someone did.  I use terminal all the time on my unix boxes, I've never seen one like this though.

---

### Post by Xbehave on 2009-09-28
once openssh-server is installed you need to get sshd running, you can do this manually by running
```
/etc/init.d/shhd start
```
or you can turn the sshd service on in your system services.

However you should read [this]("http://www.cyberciti.biz/tips/ssh-public-key-based-authentication-how-to.html") and make sure you secure you do not allow people to login using just a password as you will be brute forced if you do

---

