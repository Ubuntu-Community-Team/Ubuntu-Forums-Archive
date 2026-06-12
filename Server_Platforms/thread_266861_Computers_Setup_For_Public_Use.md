---
title: "Computers Setup For Public Use"
date: 2006-09-27
forum: Server Platforms
---

### Post by wirelessman on 2006-09-27
First of all I love Ubuntu!  Very easy to install and use!!


My question is, can you build a computer to put in a public place that cann't be harmed?  I have a computer lab in a small town. (10 computers running XP) 
Someone gave out the admin password; now we have a mess!

Can you lock down Ubuntu to be "tough as nails"?

---

### Post by em3raldxiii on 2006-09-27
Well, there are a couple of things to consider.

1.  An admin password is just that ... so if someone gives it out for your Ubuntu computer, well ... you're hooped.  Until you change the PWD of course.

2.  Yes, you can certainly set this up, but someone is going to have to keep admin access.  You may want to develop several "levels" of adminship.  Say a "super" admin, then regular admins who have access to certain applications and directories (so they could create users perhaps), and then maybe power users and then public users.  Something like that.  It wouldn't be terribly difficult, but would likely require a little bit of forethought.  You'd create user groups and add users to specific groups.  Much the same as setting up an FTP server.

3.  You could instead just make a terminal and have it networked to your main server.  I don't know precisely how to set this up, but I have seen it done before.

4.  One of the most effective ways of securing your computer in Linux would be to have the /home directory on a completely separate partition.  That way, if someone fries your Ubuntu installation by gaining access to your root system, you could just re-install the system without affecting the /home directory.

5.  Create a disc-image of your critical system structure (there's an application somewhere that will make a disc-image out of pretty much anything you want) so that you can have a master "fix" disc any time you need it.

Hope that helps!  I am just a fellow user, so I know I probably didn't answer your question precisely, but maybe I gave you some ideas.

Mmm ... also, since Linux is literally "immune" to just about every major virus/adware/worm/spyware etc etc etc, you wouldn't have much trouble anyway.  The worst thing I think you'd get would be people downloading stuff they shouldn't and maybe trying to install software (and since most people are not Linux savvy, you wouldn't have to worry about that much either).

---

### Post by aysiu on 2006-09-28
*kiosktool* for KDE. I believe Gnome has a kiosk application as well.

---

### Post by wirelessman on 2006-09-28
Thanks for your ideas!

---

