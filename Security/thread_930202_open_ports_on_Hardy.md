---
title: "open ports on Hardy"
date: 2008-09-25
forum: Security
---

### Post by SSVegito888 on 2008-09-25
when i use the command nmap -PS localhost


I get the following:


Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-09-25 19:44 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1710 closed ports
PORT     STATE SERVICE
25/tcp   open  smtp
631/tcp  open  ipp
1241/tcp open  nessus
2628/tcp open  dict



Do I need to close these ports?

How can I find out which program is using smtp?

What is dict?


PS: I am also using firestarter, which is supposed to be blocking ipp from getting out.

---

### Post by amac777 on 2008-09-26
To find out what programs are controlling the listening tcp ports on your computer, use netstat:

sudo netstat -tlp

the -tlp means: t=tcp ports, l=listening ports, p=show program/pid name

Edit: as another user pointed out, to show all the open ports on your computer use: sudo netstat -plntu

---

### Post by TheRoot on 2008-09-26
```
netstat -ntlp
```

Shall give you a complete info about the open/listening ports and what program is using them.

---

### Post by stmurray on 2008-09-26
You are scanning your localhost (127.0.0.1), but you probabably have firestarter set to your network card (eth0).  Therefore, I believe that firestarter isn't going to block traffic to/from 127.0.0.1.  (Somebody correct me if I am wrong, as my knowledge of firestarter is limited).  Therefore, just because your nmap run is showing them open, doesn't mean a remote host will see them that way.  

The best way to do a scan like this is from another machine on the local network.

---

### Post by hyper_ch on 2008-09-26
what makes you think he has firestarter installed?

---

### Post by stmurray on 2008-09-26
He says so:
> **SSVegito888 said:**
> 
PS: I am also using firestarter, which is supposed to be blocking ipp from getting out.

---

### Post by hyper_ch on 2008-09-26
ok ;)

I just wonder why does he use firestarter anyway... oh well...

---

### Post by Kevbert on 2008-09-26
> **SSVegito888 said:**
> when i use the command nmap -PS localhost


I get the following:


Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-09-25 19:44 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1710 closed ports
PORT     STATE SERVICE
25/tcp   open  smtp
631/tcp  open  ipp
1241/tcp open  nessus
2628/tcp open  dict


Do I need to close these ports?

How can I find out which program is using smtp?

What is dict?


PS: I am also using firestarter, which is supposed to be blocking ipp from getting out.

If you are worried that the ports are open to the outside world you can check with GRC's ShieldsUp which can be found [[COLOR="Red"]here[/COLOR]]("http://www.grc.com/default.htm").

---

### Post by cariboo on 2008-09-26
> Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-09-25 19:44 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1710 closed ports
PORT STATE SERVICE
25/tcp open smtp
631/tcp open ipp
1241/tcp open nessus
2628/tcp open dict


Port 25 open tells us that you are running a mail server
Port 631 is only open to localhost unless you've changed the configuration
Port 1241 is self explanatory
Port 2628 looks like the open dictionary

Nessus probably installed the mail server, and it wouldn't surprise me if port 2628 also has something to do with nessus.

My advice wuold be to shut down nessus when you aren't using it.

Jim

---

### Post by SSVegito888 on 2008-09-26
Thanks for all of the info.


I am new to Linux and went crazy while downloading software with Synaptic Package Manager.  I LOVE FREE SOFTWARE!!! I went overboard and had installed a bunch of unnecessary programs, so I just thought it'd be easier just to wipe my hdd with DBAN and reinstall Ubuntu.


Also, Which is a better Front End to Ubuntu's Firewall gufw, firestarter, or would you recommend a different GUI.

Again, I am new to Linux, so I still have the Windows mentality.  I like GUIs. 


PS: I will have to remember that netstat command.


Thanks,

SSVegito888

---

### Post by Kevbert on 2008-09-27
Personally I prefer ufw rather than firestarter.  Firestarter can come up with an error when you first start up (it tries to run too early in the boot cycle) and don't really get on with it.
There's a guide to how to use it [[COLOR="Red"]here.[/COLOR]]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")

---

### Post by hyper_ch on 2008-09-27
> **SSVegito888 said:**
> Also, Which is a better Front End to Ubuntu's Firewall gufw, firestarter, or would you recommend a different GUI.
Why do you need to alter the default settings anyway?

---

### Post by SSVegito888 on 2008-09-27
Someone on this forum suggested I block port 631 (ipp) universely.


Also, eventually, I am going to add an OpenSSH Server.



Thanks,

SSVegito888

---

