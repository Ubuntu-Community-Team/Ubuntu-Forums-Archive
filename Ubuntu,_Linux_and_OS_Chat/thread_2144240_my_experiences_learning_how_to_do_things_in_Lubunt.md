---
title: "my experiences learning how to do things in Lubuntu"
date: 2013-05-11
forum: Ubuntu, Linux and OS Chat
---

### Post by hurtstotalktoyou on 2013-05-11
**I.  Introduction**

**a.  purpose of this document**

I intend this to be a running log of some of my experiences figuring out how to do things in Lubuntu.  You can think of it as a sort of how-to guide for myself, because I'm sure I'm going to forget most of this later.  When it comes time to re-install Lubuntu, or upgrade, or whatever, I will want to have some personal documentation.  But I figure it might be useful to others as well, so I'm making it public here in the "chat" subforum.  Hopefully that is an appropriate place for this.

**b.  why lubuntu?**

Up until recently I had been using Ubuntu 10.04 LTS, but it was getting a bit old and so I decided to upgrade.  Unfortunately I just hate unity, and had problems getting the classic gnome shell working the way I wanted.  But I never liked gnome that much anyway.  It was just better (for me) than the old alternatives of xfe and kde.  So instead I went with Linux Mint Mate 13 LTS, and that has been working pretty well for me so far, with one exception:  It's *slow*!  For instance, I'll click on "places" and count to five before the caja file manager finally pops up.  Playing videos in vlc sometimes takes 10 seconds before they start.  It's extremely annoying.

So for my netbooks I wanted to have something very lightweight, which would have a snappy response and drain minimal battery power.  The natural choices were between xubuntu 12.04 and lubuntu 13.04.  I almost went with xubuntu due to the fact that it has an LTS (lubuntu does not) and has a longer history of official support.  But in the end lubuntu 13.04 won me over with its promise of significantly smaller resource demands.  I have to say, so far I'm glad I made that decision.

**c.  overall impressions**

At the time of this writing, I've only been using lubuntu for a few days, so my initial impressions are limited.  I've discovered several things a like a lot, and several more things which **** me off.  Overall though I'm simply intrigued by the differences between lubuntu and its bigger brothers ubuntu and linux mint mate.  LXDE is a remarkably clean and crisp DE, and I find the experience aesthetically pleasing overall.  And while some things have been difficult to figure out (compared to pre-unity ubuntu or linux mint mate), so far I've been able to do everything I've needed.  For what it's worth, I recommend lubuntu to anyone curious about trying a lightweight system.  I only stress that you will have to learn some new techniques for accomplishing certain common tasks.

**II.  installation**

**a.  dual- and triple-boot systems**

My netbook has Windows, so as usual I use gparted live usb to shrink the Windows partition and create enough free space to install lubuntu.  I doubt gparted is required, but I'm accustomed to it after using it for many years, and I feel like I have better control over what I do when I use it.  Once enough free space has been created, just select "install lubuntu alongside Windows" during the lubuntu installation process, and everything should be fine for a dual-boot.

A triple-boot was a little more of a hassle.  The lubuntu installation wizard doesn't seem to have an option for installing an extra copy of lubuntu on the same machine.  So instead of just creating free space, I resized the first lubuntu partition and created a new ext4 partition in between the first lubuntu installation and its swap partition.  So my hard disk now looks like this:

/dev/sda1 ntfs (Windows recovery)
/dev/sda2 ntfs (Windows)
/dev/sda3 extended
...../dev/sda5 ext4 (lubuntu copy #1)
...../dev/sda7 ext4 (ready for lubuntu copy #2)
...../dev/sda6 linux-swap

Notice that /dev/sda6 and /dev/sda6 are out of order.  Oh well, I haven't noticed any difficulties so far.  Maybe it would have been fine to place the linux-swap partition before lubuntu copy #2, but I wasn't sure, and this works fine.  So whatever.

Even after doing this, though, I needed to tell the lubuntu installation wizard to put "root" on /dev/sda7.  None of this was required for the first lubuntu installation though.  It's only an issue with a second copy on the same computer.

**III.  weird issues**

**a.  drag and drop in pcmanfm**

For some reason, I cannot move files to my home folder by dragging and dropping them.  (But oddly, I can drag and drop files *from* my home folder.)  So in order to "move" files, I right-click and "copy" the file, then "paste" into the home folder and move the copied file to trash.  It's an annoying workaround but I suppose it works.  I have to wonder how on earth this bug got past the developers though.  Seriously, no drag-n-drop?  Bizarre.

**b.  samba shares**

Setting up samba seemed to work just like ubuntu and linux mint mate.  However in order to actually *use* samba, I had to do some strange things.

Accessing lubuntu from other computers is no problem.  But what if you want to access other computers from lubuntu?  Unlike ubuntu/mint, there is no "network" option in the file manager.  And if you just type in "smb:" you will find a "WORKGROUP" folder which refuses to be mounted via mouse clicks.

Instead, to access other samba shares from lubuntu, I had to discover the IP of my workgroup machines.  In LXTerminal type "nmblookup -I <computer name>".  It will return an IP address like 192.168.1.100, and this is what we need.  Then in pcmanfm, type "smb://192.168.1.100" (or whatever is the desired IP).  Then you should see the samba shares on that location.

But wait!  You still won't be able to double-click to browse the shares.  Instead, if you want to access "sharefolder" you will have to type in "smb://192.168.1.140/sharefolder".  That will put you inside the shared folder, and then click-browsing will work at last.

Notice that the name of the other computer is required to make all this work.  But I'm not sure how a person is supposed to discover the computer name if he doesn't know it already.  So let's hope you know it!

**c.  zip files**

Much to my surprise, I discovered that the compression software included with lubuntu can't handle encrypted zip files.  Can it handle regular (unencrypted) zip files?  I don't know.

To make them work, I installed the package p7zip-full, and then used the console command "7z e /path/to/file/filename.zip" to extract.

UPDATE:  It turns out that xubuntu 12.04.2 64-bit can't handle encrypted zip files out-of-the-box either.

**d.  touchpad settings**

If you're like me then you want to disable the annoying "tap to click" function on a laptop/netbook touchpad.  But to accomplish this in lubuntu requires a different approach.  First run

```
gksu leafpad /etc/xdg/lxsession/Lubuntu/autostart
```

(Yes, that's a capital L.)  Then add the line

```
@synclient MaxTapTime=0
```

and save.  Reboot and click-to-tap will be disabled in the lubuntu desktop (although not for the login screen).

**e.  startup applications**

Also in lubuntu, there is no gui for adding/removing startup applications.  As in part d. above, to add a startup app we must run

```
gksu leafpad /etc/xdg/lxsession/Lubuntu/autostart
```

(Again, that's a capital L.)  Then add the line "@yourfavoritestartupapp".

**IV.  other thoughts**

Like I said, I've been pleased and intrigued so far by lubuntu 13.04.  I trust it enough that I am willing to use it on my trip to Israel this summer, where I won't be able to replace it if it gets to be too much trouble.

Oh, one last thing:  I've always wanted the safety of a warning dialog for moving files to trash.  Ubuntu had no option for this, nor does Mint Mate.  Well lubuntu has one!  Rock on LXDE!

---

### Post by vasa1 on 2013-05-12
> **hurtstotalktoyou said:**
> ...
**III.  weird issues**

**a.  drag and drop in pcmanfm**

For some reason, I cannot move files to my home folder by dragging and dropping them.  (But oddly, I can drag and drop files *from* my home folder.)  So in order to "move" files, I right-click and "copy" the file, then "paste" into the home folder and move the copied file to trash.  It's an annoying workaround but I suppose it works.  I have to wonder how on earth this bug got past the developers though.  Seriously, no drag-n-drop?  Bizarre.

...
If you have a Launchpad account, please "me too" [this bug]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1179167") which is related your point above.

Re. "*I have to wonder how on earth this bug got past the developers though.  Seriously, no drag-n-drop?  Bizarre.*" I'm keeping my mouth shut because I wasn't a tester of the pre-release version even though there were repeated requests for testers :)

---

