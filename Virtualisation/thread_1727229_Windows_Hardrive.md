---
title: "Windows Hardrive"
date: 2011-04-12
forum: Virtualisation
---

### Post by nightwarrior51 on 2011-04-12
I know that Parallels for Mac has this feature, but is there a program on Ubuntu that allows you to virtualize using your Windows Hard Drive. I'm currently dual booted with Windows and Linux and I don't like switching to my Windows boot, however, I want to use my files on the Windows HD. Is there a program that can do that?

---

### Post by gareththered on 2011-04-12
Are you trying to virtualise your Windows drive from Ubuntu?

If so, why not install VirtualBox?  Then use raw disks as described in the manual [here]("http://www.virtualbox.org/manual/ch09.html#rawdisk").

---

### Post by nightwarrior51 on 2011-04-13
Thank you so much, I will try when I get home (at school right now).

---

### Post by nightwarrior51 on 2011-04-14
Okay, so I tried it when I got home using this [tutorial]("http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/") and the link you gave and was able to make the machine, but now my problem is that it loads up Ubuntu's splash boot. I double checked to make sure I referenced the right drive and I have. The system BIOS is Virtualbox doesn't really help and when I try to use the keyboard on the splash boot, it's slow. I eventually made my way to the Windows 7 loader, but once I select that, it tells me it failed to boot and asks me to hit Ctrl+Alt+Del.

---

### Post by gareththered on 2011-04-15
That sounds a little worrying.  Have you rebooted your computer to see if it will still boot into Windows?

If all you're after is to access your files on the Windows hard drive then why do you not simply mount the Windows drive while in Ubuntu and access the files from there?

---

### Post by nightwarrior51 on 2011-04-15
I haven't yet. I know I can mount my drive, but it isn't just files I'm after, it's my system. I want to say, use iTunes to sync my iPod (example). It isn't the files as much as the programs and the files together.

---

### Post by gareththered on 2011-04-15
The problem is that if you boot between 'real' Windows and virtual Windows your installation will be confused as to what hardware it's running on.

Apparently, you can use the Hardware Profile option in Windows XP to switch between two different profiles.  For example, one for real Windows and another for running it in Virtual Box.  However, if you're running Windows 7 then this option isn't available.

In the past I installed a fresh install of Windows in Virtual Box and used that to run iTunes.  It would probably be simpler.  You can attach the iPod's USB connection to Virtual Box.

---

### Post by nightwarrior51 on 2011-04-15
I suppose. That's where the idea came about, but I figured that if I can just use that drive, I don't have to worry about it. By the way, I'm using Windows 7 now; I didn't mess anything up while testing around with this. Thank you for all the help. I'm glad my first thread went over so well.

---

### Post by gareththered on 2011-04-15
If it had gone well, you'd be writing your post in Windows within Ubuntu.  On the other hand, it could have gone much worse and you could have no Windows!

Enjoy Ubuntu!  Remember you only need Windows for iTunes.

---

