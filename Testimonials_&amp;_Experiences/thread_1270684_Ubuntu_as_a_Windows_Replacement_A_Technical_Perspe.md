---
title: "Ubuntu as a Windows Replacement: A Technical Perspective"
date: 2009-09-19
forum: Testimonials &amp; Experiences
---

### Post by deosculate on 2009-09-19
Greetings.  I typically don't write reviews of any sort but Ubuntu has made a very positive impression on me and wanted to share my experiences for anyone else that may be thinking of making the switch from Windows to Ubuntu.

First of all, I'm not using Ubuntu for a typical home desktop replacement.  I'm a senior systems administrator for one of the largest telecommunications companies in the US.  My team manages a wide variety of systems that are both revenue-generating and critical to national infrastructure.  The systems we manage run on everything from Solaris, OpenVMS, RedHat Linux, Windows and everything else in-between.  My personal background and strength are Microsoft products (sorry!).

I had various reasons for wanting to try Ubuntu.  Most of them came down to a lack of flexibility that kept me switching between tools on my Sunray, my laptop, and another Windows box on my desk.  After the 3rd or so blue screen of the day I setup Ubuntu on my personal laptop to see how it'd compare.

I had Ubuntu downloaded, installed and connected to the network within 45 minutes with all drivers automatically installed and the entire system fully working.  That was a pleasant surprise in itself.  Within just an hour or two after first boot I had the Citrix client loaded, Pidgin setup to replace Microsoft Communicator, the Cisco VPN configuration imported, OpenOffice updated, Firefox with Xmarks setup, printers configured, and network shares mapped.

So to put this in a more logical format, here are my experiences with Ubuntu:

**Satisfied**


[LIST]
[*]Initial software load isn't too much or too little -- and with the **command-not-found** package it takes a lot of the guess work out of getting the tools you're used to installed.
[*]Quick install time with good support for even newer hardware.
[*]Software ports or alternatives.  For nearly every tool that was critical I've been able to find a viable alternative or port.  In every case so far the alternatives have been quicker than their counterparts.
[*]**OpenOffice** has fulfilled every Office-related need I've had thus far aside from Visio drawings.  Even with some of the most complex spreadsheets and formatting in Word documents OpenOffice have handled them flawlessly.
[*]Most of the home-grown applications and various small utilities I use can be ran with **wine** or **mono** with no issues.
[*]Overall system performance is much, much better.  With the innate ability for multiple workspaces I no longer even have a need for the multiple monitors I was previously using.
[*]Documentation -- One thing I was worried about was a lack of documentation if I ran into a problem or needed a workaround.  I'm surprised by the amount of resources (especially these forums) that have already documented everything I've needed to research.
[*]Built-in Cisco VPN support.  With the **network-manager-vpnc** package I was able to import my Cisco VPN configuration file and connect within seconds.
[*]The utilities and features integrate much better into Linux and UNIX-based systems.
[/LIST]
[B]
Workarounds[/B]

[LIST]
[*]No real alternative for Outlook.  Initially I installed Outlook on Citrix but display problems and other issues with the Linux ICA client displaying themes forced me away from that.  Now I use **VirtualBox** with Outlook 2007 in Seamless mode.
[*]**OpenSSH** doesn't like putty keys.  However following the instructions [here]("http://blog.padraigkitterick.com/2007/09/16/using-putty-ssh-keys-with-openssh-on-ubuntu/") allows you to convert those putty keys into something that can be read by OpenSSH.
[/LIST]

**Compromises**

[LIST]
[*]I can't find a good alternative to UltraEdit.  I'm using **JEdit** now but it's just not the same.
[*]I can't find a good alternative to Putty Connection Manager.  Instead I'm re-building these connections in **secpanel**.
[*]I can't find a good alternative to mRemote.  Instead I'm using **gnome-rdp** and re-building the connections in there -- although it doesn't have as many configurable options.
[*]Video drivers are not perfect.  Some applications have rendering issues but never enough to cause the application to be unusable.
[/LIST]

All-in-all I'm very happy with my switch.  There hasn't been a single show-stopper that couldn't be overcome yet.  Obviously I wouldn't continue on if it made my work cumbersome, but if anything it's made it more streamlined.  I have a small Windows XP session running through VirtualBox with only 512 MB of RAM allocated to it and it's been more than enough to meet the few shortcomings associated with making the move.

---

### Post by Ms_Angel_D on 2009-09-19
Great Read, thanks for sharing, and welcome to Ubuntu :D

---

### Post by running_rabbit07 on 2009-09-19
Awesome! Welcome to Ubuntu!

---

### Post by Bucky Ball on 2009-09-19
Your knowledge and experience would be a welcome addition to the Ubuntu community ... so welcome!

Glad you're enjoying it so far ...

---

### Post by mjitkop on 2009-09-19
deosculate, I'm glad to see that you are able to use Ubuntu in a professional environment. Good job getting everything set up! \\:D/

I'm interested to know how you got the Citrix client to work. I would like to be able to connect to my company's Citrix server to do some work from home. I am not very good with network setups. Thanks.

---

### Post by longtom on 2009-09-21
Wonderful testimony.  Welcome!

---

### Post by marshmallow1304 on 2009-09-21
Putty is ported, and it's in the repositories.  I've never needed to use it under Linux, but I remember it fondly from my Windows days.

---

### Post by Sylslay on 2009-09-21
Hi, wilkomen!!!!!!!! In Eu.

---

### Post by randrews on 2009-09-21
UltraEdit for linux: [http://www.ultraedit.com/products/uex.html](http://www.ultraedit.com/products/uex.html)

Personally, I'm torn on it. I've got the previous edition on my Vista box, and we use an older version at the office, but I get tired of waiting for it to complete operations and wind up throwing something together in Python. (In UE's defense, though, my data files are thousands to  millions of records long.)

---

### Post by JC Cheloven on 2009-09-21
Congratulations! Not many people is open-minded enough to give a fair opportunity to a new system (specially having been using a different one for years).

Other than technical, there are also some nice values in ubuntu, and in free software as a whole ;-)

---

### Post by lisati on 2009-09-21
Welcome to the Ubuntu family, and thanks for sharing!

---

### Post by anaconda on 2009-09-22
> **deosculate said:**
> Greetings.  
[LIST]
[*]No real alternative for Outlook.  Initially I installed Outlook on Citrix but display problems and other issues with the Linux ICA client displaying themes forced me away from that.  Now I use **VirtualBox** with Outlook 2007 in Seamless mode.
[/LIST]


Welcome to the community.

What do you mean there is NO real alternative to outlook?
Have you tried thunderbird?  When I migrated to ubuntu I just moved my old (outlook) mail to it and have had no problems since.

And about ultraedit.
Some good editors for linux are: kate, qeany, and scite
Yes they are little different from ultraedit, but very good. Currently I use kate, but used to use geany and gedit. 

The real problem (for me) is trying to find a replacement for windiff. I think the best linux one is meld, but it isn't nearly as good as windiff....

---

