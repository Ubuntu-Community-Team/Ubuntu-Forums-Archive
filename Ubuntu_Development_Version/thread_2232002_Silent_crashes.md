---
title: "Silent crashes"
date: 2014-06-29
forum: Ubuntu Development Version
---

### Post by ubername on 2014-06-29
Hi

I have had my UU partitions crash silently for several weeks now. I tried working through various things to solve the problem to no avail, and have recently needed to get on with some other things so haven't asked here, but these are the symptoms:

I can boot into the partition, nothing seems to be reported during startup (I don't have 'quiet' as a grub option) and I get to Plymouth login.

If I cl-tFx to a different terminal I can usually do some stuff, if I logon to the GUI via Plymouth it usually locks up

Either way after a while it simply hangs. My searches through various system logs etc have come up with nothing. This is happening both ion partitions which have been upgraded from previous ububntu installs and brand new partitions installed from live CD.
After than hang I have to push and hold the power button for ten seconds or so to get to reboot.

I'd be very grateful for any advice in problem solving.

---

### Post by rrnbtter on 2014-06-29
Greetings,
This is what I did. 
Boot into recovery mode. Run the fsck to repair your partition damage from the hard reboots.
Then when back to the recovery screen continue the normal boot process. 
If you get to a desktop session run these commands and then reboot.
sudo chown user:user /home/user/*
sudo chown user:user /home/user/.*
Of course you would replace "user" with your own login.
Mine is booting just perfect after a couples of weeks of crashes.

---

### Post by zika on 2014-06-29
Would not be better if we could see permissions for files in aforementioned folders before You try to change all of them?

---

### Post by Cavsfan on 2014-06-29
If you're trying to login to Unity this will not make any difference. But I was unable to login to gnome flashback (with compiz) on Mint 17 and some how the sessions names got switched.
Just enter this in terminal:
```
cavsfan@cavsfan-MS-7529:~$ cat /etc/upstart-xsessions
# xsessions listed below are run inside an Upstart user session.
gnome
gnome-classic
gnome-fallback
gnome-fallback-compiz
kde-plasma
Lubuntu
Lubuntu-Netbook
lubuntu-nexus7
lxgames
qlubuntu
ubuntu
ubuntustudio
xfce
xubuntu
unity8-x11
unity8-mir
```

My problem was gnome-classic was name gnome-fallback.
Editing that file and changing gnome-fallback to gnome-classic fixed my problem.

I changed all the fallback words above to flashback but they reverted back. All except gnome-classic which makes the difference between looking at a blank screen and it logging in.
I too could Cntl+Alt+F1 to login via CLI and get updates but could not login to gnome flashback. I could login to Unity just fine, which is why I mentioned if you are trying to login to Unity or flashback.
If you're trying to login to Unity then I don't have a clue.

To reboot you can press Cntl+Alt+F1 to login via CLI and then enter sudo reboot. That will reboot your system.

---

