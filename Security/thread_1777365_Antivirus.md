---
title: "Antivirus"
date: 2011-06-07
forum: Security
---

### Post by dsos30 on 2011-06-07
Hi everyone,

I am going to wipe off Windows from my laptop & install only Ubuntu 11.04.

Do I need to install a antivirus system, I know about the firewall form ubuntu software centre i.e. firewall confiiguration.

Thanks dsos30 newbie...

---

### Post by hakermania on 2011-06-07
no you don't need antivirus

---

### Post by wolfen69 on 2011-06-07
Most people using ubuntu do not need an anti-virus *or* firewall. I've gone to many "bad" websites, and never got a virus.

But if you are downloading a lot of stuff that will be transferred to windows machines, it may be a good idea.

---

### Post by dsos30 on 2011-06-07
Thanks for that mate, was not sure about it.

It must be very safe  operating system to us on the net.

---

### Post by ubudog on 2011-06-07
Yep, Ubuntu and Linux in general is really safe.  Most times, viruses/malware/trojans for Linux will need you to enter your password in order for them to run properly.  :-)  So sit back, and enjoy your new system!

---

### Post by yetiman64 on 2011-06-07
> **hakermania said:**
> no you don't need antivirus

+1, you don't need it for Ubuntu. 

If you are behind a hardware firewall (eg a broadband modem or a router you may not even need a firewall with Ubuntu (no ports open by default on install), unless you install a service/program that opens and listens for connections on a port or acts as a server.

You may want to consider an antivirus if you are in the habit of sending files to Windows users, though many here argue it is the Windows users responsibility. I use Avast myself for on demand scanning of files etc before sending them to Windows users (family members etc.).

Lots of good general information you may wish to read about security in Ubuntu is here, it includes some commentary about viruses and malware :

[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=510812[/COLOR]]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by dFlyer on 2011-06-07
> **dsos30 said:**
> Hi everyone,

I am going to wipe off Windows from my laptop & install only Ubuntu 11.04.

Do I need to install a antivirus system, I know about the firewall form ubuntu software centre i.e. firewall confiiguration.

Thanks dsos30 newbie...

No. The only time an antivirus is warranted with linux is if your running a mail server or worried about transferring files with windows users. Remember linux has built in securities that windows doesn't. There are not any linux specific virus in the wild that I'm aware of.

---

### Post by uRock on 2011-06-07
The firewall is already built in. If you would like to monitor its status, then you can install GUFW via the Ubuntu Software Center. Or you can activate it using the following commands via a terminal.

I do recommend enabling the firewall, especially if you are connecting to the internet via wireless.

To activate, ```
sudo ufw enable
```To check status,```
sudo ufw status
```To disable,```
sudo ufw disable
``` I highly recommend using GUFW if you want to set rules to allow certain incoming connections, such as Secure SHell(SSH).

---

### Post by ubudog on 2011-06-07
+1
GUFW is a great tool.

---

### Post by bodhi.zazen on 2011-06-07
> **ubudog said:**
> +1
GUFW is a great tool.

The best thing about ufw ? The syntax is very similar to the syntax you use for iptables.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

That is the primary reason I advise ufw, so one can then learn iptables if needed.

---

### Post by Pilot824 on 2011-06-08
Tis why I love Ubuntu some more good sir! :D

> **dFlyer said:**
> No. The only time an antivirus is warranted with linux is if your running a mail server or worried about transferring files with windows users. Remember linux has built in securities that windows doesn't. There are not any linux specific virus in the wild that I'm aware of.

---

