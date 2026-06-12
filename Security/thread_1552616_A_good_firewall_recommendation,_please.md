---
title: "A good firewall recommendation, please?"
date: 2010-08-13
forum: Security
---

### Post by socom1970 on 2010-08-13
Greetings all!

I am new to the Ubuntu/Linix world (less than a week).

I have tried the search, but have had difficulty finding threads on this.

Can someone recommend an excellent firewall to use with Ubuntu?

Thanks very much.

Socom

---

### Post by wojox on 2010-08-13
Check out [UFW]("https://help.ubuntu.com/community/UFW")

---

### Post by FuturePilot on 2010-08-13
UFW/GUFW are the easiest and most recommended.

However, unless you're running some kind of server on you machine you don't really need a firewall as the default desktop setup has no listening services on it. I recommend you check out the Ubuntu Security sticky. There's also a link to it in my signature.

---

### Post by wojox on 2010-08-13
To add I use my Router as my Firewall.

---

### Post by FuturePilot on 2010-08-13
> **wojox said:**
> To add I use my Router as my Firewall.

A good point. If you have a router you're basically already behind a firewall.

---

### Post by cariboo on 2010-08-14
+1 if you've got a router, just make sure you don't have any ports forwarded. With a router a firewall on a computer is just extra icing on the cake.

---

### Post by HermanAB on 2010-08-14
Howdy,

As mentioned numerous times, a properly configured Linux machine doesn't really need a firewall.  An if you don't know how to configure a Linux machine properly, then the firewall probably is not going to help much either. 

The Linux network stack nowadays by default do many of the checks that used to be done with special netfilter rules, so firewall rules are mostly redundant.  My servers do not run any special firewall rules.  They sit on the wild wild web completely naked and stay up for four to seven years, till something wears out - usually a PSU or a CPU fan.

Look at it this way, most commercial firewall devices run Linux.  So, are you going to put a firewall in front of the firewall, recursively?

A firewall is mostly used for the protection of Windows machines.  Underneath every Windows desktop machine, there is a dinky little Linux router lying on the floor amongst the dust bunnies.

A firewall is used to block ports.  If you want to run a service, then that port must be open, so the firewall does nothing for that service.  If you don't want to use a service, then turn it off.  If nothing is listening, then it doesn't matter that the firewall is blocking the port, there is nothing to talk to anyway.  So on a properly configured Linux system, a firewall does nothing and serves no purpose.

On a Windows system, nobody knows what is going on and services can get started accidentally very easily.  Put a naked Windows machine on the wild wild web and it will be zonked out of its mind pretty soon, so there a firewall makes sense.

The most important security thing you can do in Linux is to use looooooong passwords.  You should use passwords of at least 9 characters (I use 16) for all accounts and you should configure PAM to enforce it.

---

### Post by newboyo on 2010-08-14
Hi Socom,

Welcome to Linux!!!

I know how you feel. I too am a Linux newbie and feel naked AND that I have a bulls eye painted on my rear, without a firewall. 

Though all the experts are right, I installed Guarddog.

hope this helps.

New

---

### Post by adit on 2010-08-14
> The most important security thing you can do in Linux is to use looooooong passwords.I am using ubuntu 10.04 desktop version.  No server (ssh, ftp ...) is running in my computer.  I am the only person who can physically access the computer.  But I am connected to internet.
In this situation any long passwords help?  I think there isn't even a need to have a password.
Is there any possibility of hacking this computer (which has no firewall, no password and does not run any servers)?

---

### Post by OpSecShellshock on 2010-08-14
> **adit said:**
> I am using ubuntu 10.04 desktop version.  No server (ssh, ftp ...) is running in my computer.  I am the only person who can physically access the computer.  But I am connected to internet.
In this situation any long passwords help?  I think there isn't even a need to have a password.
Is there any possibility of hacking this computer (which has no firewall, no password and does not run any servers)?

Not likely from the outside, but certainly possible from the inside were you to run across a linked script with an attempted privilege escalation while using a browser. I've never actually seen one, but the web is big and its information is dense.

---

