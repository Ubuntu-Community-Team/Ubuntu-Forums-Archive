---
title: "[SOLVED] Upgrading from feisty to hardy via gutsy with CDs"
date: 2008-10-10
forum: Server Platforms
---

### Post by ptolemytoo on 2008-10-10
Hi all

I'm trying to upgrade my Feisty Server 7.04 to 8.04. I've just received my copy of Hardy Heron on CD. Out here in the Third World, we don't have unlimited bandwidth so doing a apt-get dist-upgrade is not an option. That's why I ordered the disk. 

I discovered that I could not upgrade directly from Feisty to Hardy when I ran the "cdromupgrade" shell script. Fortunately I had a copy of Server 7.10 so I tried to run the same script thinking I will upgrade to Gutsy and then to Hardy. Well, there was an error as follows:
---Start---
root@plato:~# /mnt/cdrom/cdromupgrade
can't load DistUpgradeViewGtk (No module named pygtk)
can't load DistUpgradeViewKDE (No module named qt)

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done


A fatal error occured
Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log    ur
report. The upgrade aborts now.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.
Traceback (most recent call last):

  File "/tmp/tmp.XIUHlx4761/gutsy", line 59, in <module>
    app.run()

  File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()

  File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 1234, in
  fullUpgrade
    if not self.prepare():

  File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 320, in
  prepare
    'Yes'

TypeError: askYesNoQuestion() takes exactly 3 arguments (4 given)
---End---

There is no file called: /etc/apt/sources.list.distUpgrade

The file: /var/log/dist-upgrade/apt.log is empty.

The file /var/log/dist-upgrade/main.log reads as follows:
---Begin---
2008-10-10 20:07:58,128 INFO release-upgrader version '0.81' started
2008-10-10 20:07:58,203 WARNING can't import view 'DistUpgradeViewGtk' (No module named pygtk)
2008-10-10 20:07:58,274 WARNING can't import view 'DistUpgradeViewKDE' (No module named qt)
2008-10-10 20:07:58,555 DEBUG lsb-release: 'feisty'
2008-10-10 20:07:58,557 DEBUG _pythonSymlinkCheck run
2008-10-10 20:07:58,757 DEBUG checkViewDepends()
2008-10-10 20:07:58,771 ERROR not handled expection:
Traceback (most recent call last):

  File "/tmp/tmp.XIUHlx4761/gutsy", line 59, in <module>
    app.run()

  File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()

  File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 1234, in fullUpgrade
    if not self.prepare():

  File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 320, in prepare
    'Yes'

TypeError: askYesNoQuestion() takes exactly 3 arguments (4 given)
---End---

Any advice will be appreciated.

Regards

Harry

---

### Post by ptolemytoo on 2008-10-12
Does this mean nobody knows how to solve my problem? Can anyone perhaps advise me as to where I can go for help? I'm stuck.

Thanks

Harry

---

### Post by koenn on 2008-10-12
it looks like a bug in the cdromupgrade script - unless your server is configured so extraordinarily that the upgrade can't handle it. 
In any case, it's a difficult problem.
DOn't attempt to upgrade directly from Feisty to Hardy, it will most likely leave you with a broken system.

Is it an important server ? you're going to need to work around a few things, and that's always risky, especially with upgrades.
You may want to backup your data and your /etc folder in case you need to rebuild your server

I see two possible ways yo go about this. In any case, you're current system needs to be completely up to date so you do apt-get update and apt-get upgrade before you do anything else - bandwith or no bandwith.

Then, 2 ways :

1- do a manual "dist upgrade" -- unsopprted and not recommended

run uname-r to see your current kernel version
you add the cdrom to apt sources list with the "apt-cdrom add" command
run apt-get update; apt-get upgrade
run apt-get dist-upgrade
check the kernel version again

if the kernel hast'n been upgraded, you'll have to do that manually :
look for a suitable kernel with the command apt-cache search linux-image
choose a kernel that matches your hardware (or the old kernel) in specifications (architecture, ...)
install it with apt-get install linux-image-.... (fill in)

run apt-get update and apt-get dist-upgrade again to make sure you have all packages installed (some may have been hold back because your kernel needed updating first)

If you got through all that and solved all errors or warnings (if any), you can reboot. Don't reboot just to try to solve a problem, you'll be left with a half-upgraded, unstable system. You'll need to fix any pending trouble while the system is still up, then reboot.


2- alternative method : make your own repo server
since you have all the required packages on CD, you could build a web server (could be on the same machine), and copy all packages over to it. 
with a bit of additional work (you need also the a Release file and a Packages file, and you might have to pay some attention to the directory structure), and edit your sources list to point to this server.

You now don't need the cdromupgrade script anymore an can attempt to do a normal release upgrade.
A web server with a Release file and a Packages file is normally enough for apt, but i never checked if you can actually run a release-upgrade from it, so this is absolutely untested & completely at your own risk.



3- get support from canonical
contact Canonical and ask if they can support this. They might want to charge you for this, or they might send you new, hopefully bufree, CD's - but it's worth asking

---

### Post by ptolemytoo on 2008-10-14
Thanks very much for your comprehensive reply. I was starting to worry that I had done something wrong and was being ignored. I guess it is a thorny problem and not too many people had answers.

To answer your question, it is not an important server. Certainly no mission critical processes running on it. It's just that I have added a few extras to the basic LAMP installation which I would have to do again. But no worries, I will just reinstall the whole lot from the Hardy CD. 

As a matter of interest, I did try and run the Hardy cdromupgrade script and was informed that a direct upgrade was not possible. The error messages I posted occured when I tried to upgrade from Feisty to Gutsy.

I did run the apt-get update and apt-get upgrade ahead of any attempts.

Thanks again for your help.

Regards

Harry

---

### Post by ptolemytoo on 2008-10-14
Thanks very much for your comprehensive reply. I was starting to worry that I had done something wrong and was being ignored. I guess it is a thorny problem and not too many people had answers.

To answer your question, it is not an important server. Certainly no mission critical processes running on it. It's just that I have added a few extras to the basic LAMP installation which I would have to do again. But no worries, I will just reinstall the whole lot from the Hardy CD. 

As a matter of interest, I did try and run the Hardy cdromupgrade script and was informed that a direct upgrade was not possible. The error messages I posted occured when I tried to upgrade from Feisty to Gutsy.

I did run the apt-get update and apt-get upgrade ahead of any attempts.

Thanks again for your help.

Regards

Harry

---

### Post by koenn on 2008-10-14
yeah, in the end, after writing all that, I was thinking that a reinstall would probably be way easier. 

but it was interesting to think about it in terms of "if this was my problem, what would be my options"

good luck with the install.
If you can, keep a copy of /etc or at least of the config files that you know you've modified or created (such as website definitions for apache or so). It's not always a good idea to copy them into a new install, but at least you'll have the data for reference when setting up your new server.

---

