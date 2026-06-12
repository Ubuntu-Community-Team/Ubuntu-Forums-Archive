---
title: "Password protected NTFS partitions?"
date: 2009-04-26
forum: Security
---

### Post by RAMWolff on 2009-04-26
Hi,

I need some help.  

I just installed Kubuntu on my second hard drive, at first the boot loader errored out and I freaked thinking I would be locked out of Vista too, luckily the Kubuntu CD I burned got me back in.  I got brave and decided to try to boot into Kubuntu and it seems the boot manager fixed itself so there I was in the BEYUTIFUL KDE 4 and started looking around.  It's been YEARS since I've been in Linux so this was all new with sound working right off the bat, the internet connection working right off the bat but there was something new... passwords were asked of me for each of the NTFS drives I tried to access.  I've never had that before and quite frankly I don't know what the passwords would be.  

Is there some settings I need to adjust in Vista to allow for access of these drives.  Interestingly enough when I was test driving Kubuntu using the CD I wasn't locked out of my other drives at all.  So that's kinda weird to me!!  :confused:

In any case I'm sitting here in Vista until I hear back from one of you good folks.  

Kubuntu is really quite nice, both the Ubuntu version running Gnome as well!!  I think I'll end up downloading and installing that as well.  I used to run Mandrake then it became Mandriva (what a name) and then XP got better and well I do graphics in Photoshop and Poser so I gave in and went back to Windows full time.  Now I'm curious again and it's allot better and I like Ubuntu much much better!!  

Thanks for the help! :)

Richard ;-)~

---

### Post by cholericfun on 2009-04-27
during install you were asked to submit a pasword
you need it for all sorts of things incl. installing new software/ updating etc.

you werent asked for passwords in the LiveCD cause there it doesnt ask you to set a password up so basically all you do in the LiveCD is root

---

### Post by RAMWolff on 2009-04-27
Thanks, yea, got it figured out.  

I do have one other issue, I figured I'd just continue on in this thread, hope that's OK.  

GRUB is flawed or broken.  When I don't have the install disk with the option to boot from the disk in the drive and it's just a fresh boot GRUB stalls with an error and just sits there.  My main OS is VISTA and it's got allot of important projects on it so it's important to be able to boot successfully into both OS's.  Is there a way to remove GRUB and replace that with something that's a bit more solid that can boot both OS's with out all this error crap or having to keep the installation CD in the drive at all times in order to get past the GRUB boot up error??  

If so what boot manager would you suggest.  Free is always nice but I'm willing to pay a small fee if need be.  

Thanks for the help! 

Richard ;-)~

---

### Post by cariboo on 2009-04-27
You can use you LiveCD to repair grub, have a look at this [thread=224351]howto[/thread].

---

### Post by RAMWolff on 2009-04-27
Thanks kindly!!  

One more little thing.  When I minimize windows I can't see them.  Where the heck are they?? LOL

---

### Post by Atolla on 2010-05-05
Hey,

I have the problem that after clean installing Kubuntu 10.04 Lucid Lynx I have to fill in the root password every time I want to access my NTFS partitions. This is especially bothersome since Amarok on startup does not see the part of my music on those partitions.

I tried to chown the mounted partitions but this has no effect, they stay root:root owned.

Anyone got any ideas?

---

### Post by OpSecShellshock on 2010-05-05
I'm not sure it would work to change the ownership or permissions while it's mounted. Have you tried unmounting and then making the changes, or maybe editing the fstab and restarting?

---

### Post by Atolla on 2010-05-05
There, I fixed it!

Here [http://ubuntuforums.org/showthread.php?t=970435](http://ubuntuforums.org/showthread.php?t=970435) I found the way to fix it is to install and run this little wizard:

```
sudo apt-get install ntfs-config
```

Which fixes the issue I had!

Thanks for this fstab thing; ntfs-config configures it properly to automatically mount the windows partitions.

---

