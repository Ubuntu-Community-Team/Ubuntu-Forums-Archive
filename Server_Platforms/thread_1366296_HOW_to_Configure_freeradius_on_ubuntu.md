---
title: "HOW to Configure freeradius on ubuntu"
date: 2009-12-28
forum: Server Platforms
---

### Post by sinansas on 2009-12-28
Lately I started to work as student on Network Managament Team of my university.In spite of my knowledge about network is almost none,now I'm supposed to configure a freeradius on ubuntu server that the server should establish contact with cisco 1330ag access point as client,and the access point should serve like a gateway between freeradius server and XP suplicants.I've been working hard to gather some information to set them so but no progress has been made so far.Moreover I never used a unix system before though now I have to configure an ubuntu server..
Thus I kindly request what I should do as first step.

Thanks in advance

P.S. As far as I know freeradius is successfully installed.

---

### Post by badrianiulian on 2009-12-28
Hello
I had a problem once regarding configuring a radius server for the wireless network we have at work
I found the [daloradius]("http://sourceforge.net/projects/daloradius/") interface to have a good guide for making the radius server to work

Hope it works for you too

---

### Post by sinansas on 2009-12-28
Thanks a lot for advice.But I haven't found out whether this program requires GUI supporting OS,neither it has come to run.Obviously the ubuntu which is installed on the server hasn't got GUI feature.So if I need to add GUI feature to the ubuntu,how can I do it?

By the way I can't manage to get to know which ubuntu is installed on the server.Is there any command to acquire such info?

---

### Post by badrianiulian on 2009-12-28
Ok so let's start from the begining
The daloradius GUI is for your simple usage of the radius server.
Basicaly it is a MUST if you don't want to get your hair mixed up in the freeradius configuration files
The GUI is http/php/mysql based (the mysql part is for storing users/accesspoints)
In the archive you will download from the daloradius page, you will find a file called INSTALL and everything you need to know about configuring the GUI/freeradius you will find there

For learning what version of ubuntu you have you could try this command in a terminal: cat /etc/issue

I do suggest you try learning some of the basics before you try browsing through your server (linux structure/commands, mysql basics). Google is your friend. Use it well.

BTW, I once was the same as you and now I'm a happy ubuntu user. So it can be done.

---

### Post by sinansas on 2009-12-29
Sounds promissing mate.I'll try to solve this issue according to your suggestions.Thanks again,I'm grateful.

---

### Post by HuckBerry on 2010-01-13
A web based management console is a nice feature, however I see lots of merit in running a strictly command-line server. @badrianiulian, do you know how to edit the conf for freeradius as I run a command-line only server and am in need of some assistance. The issue may possibly be solved with the GUI equivilent if you are more accustomed to that, and I will do my best to do the command-line equivilents.

---

