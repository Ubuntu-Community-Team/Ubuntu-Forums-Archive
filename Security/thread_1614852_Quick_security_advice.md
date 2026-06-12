---
title: "Quick security advice"
date: 2010-11-06
forum: Security
---

### Post by chippy_250 on 2010-11-06
Hi there, I'm a new Ubuntu user and I have read around about security over the internet. I've also read the Sticky about security but I found it very detailed and a lot to take in. Seems to be a bit vague whether any protections is actually needed or not. Would someone just confirm a few things with me and give me some advice also.

1. I get slightly confused with Antivirus, internet security and firewalls. Are they all the same thing? 

2. I haven't installed anything security related yet on Ubuntu. Am I safe to download things, use the internet and buy things online?

3. If I do need an Antivirus, internet security or firewall protection, which would you recommend?

Thanks in advance.

---

### Post by viralmeme on 2010-11-06
> **chippy_250 said:**
> 1. I get slightly confused with Antivirus, internet security and firewalls. Are they all the same thing?

Antivirus software scans any opened/downloaded for a virus signature, if the signature isn't in the database then it doesn't detect it. Downloading and installing software takes a number of steps and requires the root password, so you are safe from the click-and-install variety that are rampant on the Windows platform.

A firewall blocks ports and/or IP addresses. This would be of use if your infected computer tried to connect back to the mothership. With such things as RPC-over-HTML, which is designed to bypass the firewall, this is of minimum use in protecting your computer.

> **chippy_250 said:**
> 2. I haven't installed anything security related yet on Ubuntu. Am I safe to download things, use the internet and buy things online?

Depends where you are downloading from and what you are downloading. Downloading software from the Ubuntu repository is safe. Buying things online is safe as long as you buy from a well-known company.


> **chippy_250 said:**
> 3. If I do need an Antivirus, internet security or firewall protection, which would you recommend?

A fully locked down-and-configured Ubuntu desktop provides sufficient protection. If you want to be really paranoid then boot from the CD when you want to do your online shopping/banking.

---

### Post by Verbeck on 2010-11-06
if you download software from the official repositories, and shop on trusted websites, you're quite safe. 

but there are anti virus software for ubuntu and you might try them for several reasons. read up the following for more info
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

as for a firewall : the firewall which comes with ubuntu (ufw) in disabled by default.
the instructions for the graphical front-end is at [https://help.ubuntu.com/community/Gufwa](https://help.ubuntu.com/community/Gufwa)

---

### Post by CharlesA on 2010-11-06
There are no open ports by default in Ubuntu, so nothing to firewall.

No real no for antivirus, since viruses written for Windows, won't run on Linux. Wine is the exception, since it's able to (sort of) run Windows programs.

As long as you stick to the repos you'll be fine.

---

### Post by chippy_250 on 2010-11-06
> **Verbeck said:**
> if you download software from the official repositories, and shop on trusted websites, you're quite safe. 

but there are anti virus software for ubuntu and you might try them for several reasons. read up the following for more info
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

as for a firewall : the firewall which comes with ubuntu (ufw) in disabled by default.
the instructions for the graphical front-end is at [https://help.ubuntu.com/community/Gufwa](https://help.ubuntu.com/community/Gufwa)

OK I may get Avast then.
As for the firewall, it says on the Ubuntu security advice something "If you use a router to connect to the Internet, the router may already  have a firewall configured which regulates connections from the Internet  to your network."
I do have a router and I have a firewall with a strong password. Would that suggest that I don't need to set up this 'UFW' firewall on Ubuntu?

---

### Post by ajgreeny on 2010-11-06
> **Verbeck said:**
> as for a firewall : the firewall which comes with ubuntu (ufw) in disabled by default.
the instructions for the graphical front-end is at [https://help.ubuntu.com/community/Gufwa](https://help.ubuntu.com/community/Gufwa)
That is not quite the truth.

**ufw is not the firewall in ubuntu**; it is merely the software to configure the firewall rules.  The firewall is iptables which is a standard part of any ubuntu install, and is not disabled.  For most people who are running a standalone desktop system, there is absolutely no need to change anything from the default setup you have at install, and no need to fiddle with ufw settings; you could actually make things less secure if you don't know what you are doing.

If you are running a server, eg mail server, or something of that type, then a tweak of the ufw settings may make sense.  However if you were able to setup a server, I suspect you would not need to ask this question in the first place.

---

### Post by noway2 on 2010-11-06
Activating the firewall won't do much ... if anything for you, in and of itself.    The primary advantage in adding a firewall is that it will prevent problems should  a port inadvertently get opened.  Say for example, you install an application that you don't intend as a dependency and it leaves a port open.  The firewall will effectively keep this port closed.

Virus scanning doesn't have the same meaning as it does in Windows.  Running full scans has an exceedingly low possibility of detecting anything that will cause harm to you Linux system.  The primary advantage is to prevent spread of malware to a Windows based system.  With this in mind, consider the things that you want to scan would be anything that you plan to port elsewhere, like files on a USB stick.

---

### Post by Verbeck on 2010-11-06
> **ajgreeny said:**
> 
**ufw is not the firewall in ubuntu**; it is merely the software to configure the firewall rules.  The firewall is iptables which is a standard part of any ubuntu install, and is not disabled. 

oops. Sorry - my bad :(

---

### Post by HermanAB on 2010-11-06
Howdy,

Linux security is simple:
Ensure that you always use loooong passwords - 9 characters or more.  Then relax and enjoy your Ubuntu system.

---

### Post by WeAreLinux on 2010-11-07
> **chippy_250 said:**
> Hi there, I'm a new Ubuntu user and I have read around about security over the internet. I've also read the Sticky about security but I found it very detailed and a lot to take in.

My exact feelings during my first read coming from XP :). The best advise I was given on here: Ubuntu is not Windows.

1) Use a very strong password! I would also suggest changing the default sudo timeout. The default is 15mins.

[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

2) Surf behind a NAT enabled router. If you don't, you can easily enable UFW.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

3) Forget about Anti-Virus. You don't need it on Ubuntu.

4) Stick with downloading programs in the repos. Don't use additional PPA's unless you trust them (I don't even bother). If you have to get the latest version of a program, make sure it's from a trusted source.

5) Browse the web with Firefox + NoScript add-on.

I found this article useful my first time with Ubuntu: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by I'mGeorge on 2010-11-07
The main thing I always loved about linux it's I don't have to worry about viruses and I've cruised on some hazardous web sites just for the sake of it. I only keep clamav antivirus so I could scan my Windows XP partition from times to times. In my opinion a firewall feeds on too much hardware so it's good Linux doesn't really needs it.

---

