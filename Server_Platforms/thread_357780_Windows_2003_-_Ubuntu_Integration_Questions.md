---
title: "Windows 2003 - Ubuntu Integration Questions"
date: 2007-02-10
forum: Server Platforms
---

### Post by Drezard on 2007-02-10
Hello, I am a Microsoft Windows 2003 Server Intermediate user. Im looking to intergrate to Ubuntu. Just wondering a few things about it though. 

Number 1: Does it have an add-ons or automatic software on the 6.06 server edition that would be able to do the same thing as a Windows Active Directory for Windows computers. (So basically, I'm looking for some extra software or add-on that can be used as an Active Directory to windows xp prof computers. I have a domain running 20 odd computers all with windows xp prof and I want to upgrade my windows 2003 to Ubuntu. but keep the xp prof on the other computers)

Number 2: Does the Halflife Dedicated Server work with Ubuntu?

Number 3: Does Ubuntu 6.06 server have any default firewalls?

Number 4: What do I need to Remote Desktop from a windows xp prof computer to my Ubuntu 6.06 server?

- Cheers, Daniel

---

### Post by GrammatonCleric on 2007-02-10
Question 1:

It's not automatic but the best fit would be installing OpenLDAP on the Ubuntu server.  And there appears to be a migration path from AD to OpenLDAP.

```
[http://en.opensuse.org/Migrate_from_Active_Directory](http://en.opensuse.org/Migrate_from_Active_Directory)
```Question 2:

You might want to dig around the Gaming Forum...

```
[http://www.ubuntuforums.org/showthread.php?t=85573](http://www.ubuntuforums.org/showthread.php?t=85573)
```Question 3:

Netfilter/Iptables but if you install X windows on your server Firestarter is a nice gui to this.

Question 4: 

Ubuntu Server does not install X Windows by default but if you install X post install. take a look at FreeNX....

```
[http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx](http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx)
```There's always ssh. =)



-GC

---

### Post by genesis[OFT] on 2007-02-10
Hi.

1. Yes and no.  Linux\Ubuntu do NOT have built in SMB Server\Client support - this is all passed and done through a software package called 'Samba'.  It has the ability to act as a File and Print Server as well as a NT-Style Domain Controller\Backup Domain Controller.  It does NOT, however, support becoming a AD Domain Controller, however, it DOES support becoming a AD Domain Member through a little configuration.  Have a look at the Ubuntu Wiki\Samba Documentation for more details.

2. As far as I'm aware, it does - hldsupdatetool does work in Linux as a binary, and thus should in Ubuntu.

3. I don't think so - The default Ubuntu install is quite open to the wide world, if it's not behind a router\hardware firewall of some sort.  There are, however, plenty of ways to turn a Ubuntu box into a Firewall\Router using different pieces of software - these range from Easy (Firestarter) to Medium (Shorewall) to Hard (core IPTables).  There should be Ubuntu Wiki material and support docs for each of the respective pieces of software.

4. You'll want to look into FreeNX.  There is a little bit of installing and configuring to do, however, it's great once you've got it 'goin.

I hope this all helps :).

---

### Post by localzuk on 2007-02-10
> **'genesis[OFT] said:**
> Hi.
3. I don't think so - The default Ubuntu install is quite open to the wide world, if it's not behind a router\hardware firewall of some sort.  There are, however, plenty of ways to turn a Ubuntu box into a Firewall\Router using different pieces of software - these range from Easy (Firestarter) to Medium (Shorewall) to Hard (core IPTables).  There should be Ubuntu Wiki material and support docs for each of the respective pieces of software.


Ubuntu has all ports closed by default. Iptables is installed by default, that is part of the kernel. You just need a front end, or spend some time setting the rules from the command line. Firestarter and Shorewall use iptables.

> **'genesis[OFT] said:**
> 
4. You'll want to look into FreeNX.  There is a little bit of installing and configuring to do, however, it's great once you've got it 'goin.


Or, if you don't want to bog your server down with a GUI (you don't need graphical programs on 99% of servers) you can apt-get install ssh and then use Putty to connect to it  on Windows. Or, if you want a gui, but not like a desktop - you can make use of webmin ([http://www.webmin.net](http://www.webmin.net)) - just make sure you configure SSL for it and maybe more its default port.

---

