---
title: "Ubuntu server"
date: 2013-11-28
forum: Ubuntu, Linux and OS Chat
---

### Post by ov10fac on 2013-11-28
I have been using Linux for over 30 years.  I started with slackware on about 30 720 disks.  I have always been ready to spend a lot of time getting things running just right.  Thats just been the way things are with Linux.  It wasnt for the faint of heart or novice users.  Well that was then and this is now.  I have been using the newest Fedora Desktop on my laptop for years and love it.  I use Ubuntu on other desktop environments and love it as well.  I have been using Centos as my server platform of choice for many years.  All these new versions have greatly simplified the installation, maintenance and upgrade work of an administrator.

Ok, so I ssid time to try Ubuntu Server.  Wow!!  what a mistake that has turned out to be. Install was easy, as I expected.  But from that point on it went down hill.  Now I expected with a cli only interface there would be a steep learning curve.  But I have been a cli type for many years, so...

First problem trying to set up a static IP.  Modified the interfaces file to no affect.  So tried to find a way to disable dhclient or set up a static ip from within dhclient.  I found little or nothing on the web that helped.  I thought that was very strange.  Took about 5 hours, but finelly got it done by reinstalling the server with the nic turned off.  Hmmmm.  interesting.

Ok, so next was samba.  Took me two days to get it configured for AD DC.  Then two more days to find out how to get it to start at boot time.  Im sure if I was an old time Ubuntu user it would have been easy, but what I found was that there are about three or four different ways to do things, depending on what version of the 12.04 server you are using.  Very confusing.

I finely gave up when I treid to change the SAMBA password complexity.  Could not find anything on how to do that.  Then I found an article on samba-tool.  Installed it and tried to change the complexity.  OOOPs, missing a library.  So back to google, nothing.  A lot of bug reports, but no solution for Ubuntu.  So I have given up.  I really don't have the time to fight this thing any more.  I have several other things to get running like my web development environment, and I dont even want to think about that.  So its back to Centos.  Its been fun for a few days, but jsut not worth the time.

Anyway.  I like Ubuntu as a desktop, but think Ill stick with what I know for servers.

---

### Post by rackit on 2013-11-28
I just installed ubuntu server 12.04.3 LTS I am configuring with webmin. No issues thus far. Give it a whirl... Here are the docs on networking: [http://is.gd/FIiu8W](http://is.gd/FIiu8W)

---

### Post by nerdtron on 2013-11-28
It's really not worth the time especially if you just used the server for about a day or two. You need to immerse your self with a lot of information and a lot of reading which will not take place overnight.
I think your problem is not getting the right documentation. I suggest you google effectively like how I search for something to configure on the server.
Sample google searches:
How to install Ubuntu Server 12.04
How to setup static IP Ubuntu server 12.04
How to install Samba Ubuntu server 12.04
How to install webmin in Ubuntu 12.04

I'm fairly confident you'll find a lot of information on the topic since these are just common tasks to a lot of system administrators in the internet. Have patience and try to practice on a Virtual Machine.
That is how I started learning administering Ubuntu server.
Goodluck.

---

### Post by CharlesA on 2013-11-28
Huh. The last time I installed Ubuntu server, setting a static IP was the same as Debian - edit the interfaces file as there is no network manager. Unless something has changed, that is.

---

### Post by oldos2er on 2013-11-28
Not an Ubuntu support request; moved to Ubuntu, Linux & OS Chat.

---

