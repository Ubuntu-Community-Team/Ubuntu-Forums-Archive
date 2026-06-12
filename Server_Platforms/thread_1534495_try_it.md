---
title: "try it"
date: 2010-07-19
forum: Server Platforms
---

### Post by jjcylk on 2010-07-19
I would like to set up a "try it" version of the server. I set up a USB  Server iso (64 bit - 10.4) but when it starts it wants to install. Is there a try it version>

---

### Post by keithweddell on 2010-07-19
I don't think there is.  Do you have Desktop Ubuntu installed? If so you could install virtualbox and then install the server version in a virtual machine.  There are lots of howto's about for VB.

Keith

---

### Post by arrrghhh on 2010-07-19
> **jjcylk said:**
> I would like to set up a "try it" version of the server. I set up a USB  Server iso (64 bit - 10.4) but when it starts it wants to install. Is there a try it version>

This concept you speak of is commonly referred to as a "LiveCD" - I don't believe any exist for ubuntu-server.  However, you can certainly do this with ubuntu-desktop.  If you wish to "try" ubuntu-server before you buy (or install, as is the case here :P) virtual machine would be your best bet...

Anything in particular you wanted to try with ubuntu-server?  Ubuntu-desktop is just a more filled-out version basically (there are some underlying kernel differences with 64-bit...).  So you can still run all your services and the like from the -desktop edition.  With the -server edition you don't get X or Gnome or any of that desktop environment stuff - so making a LiveCD of this version doesn't make a whole lot of sense.

---

### Post by jjcylk on 2010-07-19
i have a desktop pc I bbasically use as a storage device & print server. I have been sharing certain folders. I would like to make it a legit server with linux ( and learn some servr exper). my concern is with my Ipod. I would like to be able access the music. I would like to share the HD to diff user & give each user security or privacy. I might even try to create a mail server.

---

### Post by jjcylk on 2010-07-19
i've never used virtual machines. are they difficult to get going?

---

### Post by arrrghhh on 2010-07-19
Based on your description, there's no reason for you to run ubuntu-server, just stick to ubuntu-desktop.  Any/all applications that run as services on ubuntu-server can be configured just as easily on ubuntu-desktop.

Ubuntu-server doesn't include ANY graphical user interface... most people who manage their iPods want one of those :P

---

### Post by jjcylk on 2010-07-19
> **arrrghhh said:**
> Ubuntu-server doesn't include ANY graphical user interface... most people who manage their iPods want one of those :P
true. i thought you could us something line wine? So i will practice to get better w/ just the desktops running. 

Then I'll convert my wife's laptop...she only reads emails & go shopping at QVC.com:)

---

### Post by arrrghhh on 2010-07-19
Reading emails and shopping at QVC.com would be a great candidtate for Ubuntu's netbook remix NOT the server edition...

I'm also not quite sure with "i thought you could us**e** something **like** wine".  WINE is for running programs that are designed for Windows under Linux... But perhaps I misread your statement?!?

---

### Post by jjcylk on 2010-07-19
Let me re-phrase the question: Would I need to use WINE to access ITunes & keep my IPOD in synch?

---

### Post by jjcylk on 2010-07-19
So how do i share the printer & then how do i find it for a windows XP mo-chine

Forgot to tel you i'm running a live cd setup

---

### Post by phaed on 2010-07-20
> **arrrghhh said:**
> Reading emails and shopping at QVC.com would be a great candidtate for Ubuntu's netbook remix NOT the server edition...

Hmmm, I wonder if anyone has turned a netbook into a server. :-)

---

### Post by arrrghhh on 2010-07-20
> **jjcylk said:**
> Let me re-phrase the question: Would I need to use WINE to access ITunes & keep my IPOD in synch?

If you want to use iTunes, you would need to use wine.  However, there are several programs that are native to Linux that you can use to sync your iPod.  Amarok, RhythymBox and Songbird are just a few that come to mind.

> **jjcylk said:**
> So how do i share the printer & then how do i find it for a windows XP mo-chine

Forgot to tel you i'm running a live cd setup

I wouldn't recommend doing this from the LiveCD.  Any changes you make will be lost - if you want something permanent, install it.  Then we can talk about how to share printers & talk with other machines on your network.

---

