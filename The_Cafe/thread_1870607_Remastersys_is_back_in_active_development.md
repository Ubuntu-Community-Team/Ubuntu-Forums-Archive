---
title: "Remastersys is back in active development"
date: 2011-10-27
forum: The Cafe
---

### Post by Fragadelic on 2011-10-27
Due to the number of emails I received I have decided to make time to continue to develop remastersys.

I am planning to include options for distributions to make it easier.  I already have some scripts that I have personally been using for distribution mode remasters and will be including them in the main remastersys package.  As a result I will need dedicated testers for the different variants to help me out in testing.

Please post here, PM me, or email me if you can help out.

---

### Post by Elfy on 2011-10-27
Thread moved to The Community Cafe.

---

### Post by Fragadelic on 2011-10-27
> **forestpiskie said:**
> Thread moved to The Community Cafe.

Thanks.  I wasn't sure where I should put it.

---

### Post by cbowman57 on 2011-10-27
Glad to see Remastersys is active again.

Not sure that I can be of much help but on my system I have 2 Ubuntu installations. Gnome-only built from mini.iso, I have one built from 11.10 & another built from the 12.04 repositories.  If that is something you would like it tested on I would be happy to do it.

---

### Post by Fragadelic on 2011-10-27
Thanks.

Any help with testing would be great.  I actually would like at least a few folks from each variant of ubuntu and being able to help with the versions in testing would help me release newer version sooner.  The one built from mini.iso would be very beneficial as well.  I need to make sure remastersys pulls in all the proper dependencies.

---

### Post by Nixarter on 2011-10-27
Thanks for continuing development of this program! ;)

The only qualm I had with it is that I couldn't figure out how to save the output to some place other than default.  An option to save to an external (or other) drive would be very nice.

---

### Post by Fragadelic on 2011-10-27
> **Nixarter said:**
> Thanks for continuing development of this program! ;)

The only qualm I had with it is that I couldn't figure out how to save the output to some place other than default.  An option to save to an external (or other) drive would be very nice.

Thanks.

The Working Directory part of the /etc/remastersys.conf file is where you would set it.  The only issue right now is if the external drive uses something other than a linux filesystem but I have been trying to figure something out for that.

The issue I have with non-linux formatted drives is due to the fact that some of the important files get copied over to a dummysys folder as they need to be changed and there is no way I would think of changing live system wide files on the working system.  The /var and /etc folders are copied over along with some other blank folders.

I have been thinking of creating a file on the working directory, loop mounting and formatting this file with ext2 and then squashing this area from the loop mounted filesystem.  My only issue with this is that the size can vary greatly and can be over 1GB in some cases.  This poses a problem for fat16 formatted drives.  Fat32 should be fine and ntfs but fat16 is definitely a problem and I haven't found a reliable method of testing for this.

Any ideas or suggestions would be greatly appreciated.  Since I am continuing with it I will need all the help I can get.

---

### Post by cbowman57 on 2011-10-27
That's what I was thinking as well since it doesn't have any bits & pieces left over from a live image installation.

---

### Post by BrokenKingpin on 2011-10-27
I am glad to hear that you are going to continue development on the tool. I have found it very useful in the past, and would for sure try any new version you put out.

It has been a while since I have used it, but I remember having to do a number of manual steps when creating a distribution ISO, so if that could be steam lined a bit I think it would be a lot easier for people to use.

Keep us updated on you progress!

---

### Post by Karlchen on 2011-10-27
Hello, Fragadelic.
> [...] I have decided to make time to continue to develop remastersys. Great! :-D
Had already been wondering whether Remastersys 2.0.18.1 would continue to work fine on Oneiric or Pangolin in the way it had been doing on Lucid.
Good to know Remastersys is alive.

Kind regards,
Karl

---

### Post by Fragadelic on 2011-10-27
> **BrokenKingpin said:**
> I am glad to hear that you are going to continue development on the tool. I have found it very useful in the past, and would for sure try any new version you put out.

It has been a while since I have used it, but I remember having to do a number of manual steps when creating a distribution ISO, so if that could be steam lined a bit I think it would be a lot easier for people to use.

Keep us updated on you progress!

This is exactly what I am planning on adding with the extra scripts I have created for my own use.

My goal is to make it extremely easy to create your own flavour of Ubuntu and all options will be accessible from gui and cli modes.  It will of course always have the backup mode for personal backups as it has always had.

Some folks blindly copy files from the user home folder to /etc/skel and that can cause issues since many apps hard code the home folder in the config file.  This causes the live user creation to fail.

You will be able to easily change the boot splash for the live system.  You will be able to add your custom desktop settings including background, panel placement,etc.  I am also trying to figure out easy ways to customize plymouth, grub, gdm, etc.

When I'm done, your grandmother will be able to make an Ubuntu variant.

---

### Post by Fragadelic on 2011-10-27
> **Karlchen said:**
> Hello, Fragadelic.
 Great! :-D
Had already been wondering whether Remastersys 2.0.18.1 would continue to work fine on Oneiric or Pangolin in the way it had been doing on Lucid.
Good to know Remastersys is alive.

Kind regards,
Karl

The new version will have more features specific to dist mode building and improve the overall process.

I am dedicated to make it a tool that even your grandmother can use to make a flavour of Ubuntu.  As always it will support all window managers and desktop environments.

---

### Post by tea for one on 2011-10-27
> **Fragadelic said:**
> Due to the number of emails I received I have decided to make time to continue to develop remastersys.

I am planning to include options for distributions to make it easier.  I already have some scripts that I have personally been using for distribution mode remasters and will be including them in the main remastersys package.  As a result I will need dedicated testers for the different variants to help me out in testing.

Please post here, PM me, or email me if you can help out.

Good evening

I am delighted to see that you have decided to continue with your splendid Remastersys application.

I am currently testing Ubuntu 11.10 with Unity and also Gnome Shell (version Gnome 3.2) and I have installed Remastersys to see how it performs with the recent Ubuntu OS (Oneiric).

I added your software source via synaptic, downloaded the application without difficulty, the app installed itself seamlessly within the "Other" category.

Here are the results from the jury:-

Custom ISO (OS only - no personal data) - Built in 15 minutes
Create live USB using Ubuntu Start Up Disk Creator - Installed in 10  mins
Boot with live USB - Everything OK
Install to external drive - I am writing this synopsis from the latest installation while listening to 1970s Hippy Music.

As the younger UK brethren say "Result"

Good luck with your future endeavours

---

### Post by inameiname on 2011-10-27
> **Fragadelic said:**
> This is exactly what I am planning on adding with the extra scripts I have created for my own use.

My goal is to make it extremely easy to create your own flavour of Ubuntu and all options will be accessible from gui and cli modes.  It will of course always have the backup mode for personal backups as it has always had.

Some folks blindly copy files from the user home folder to /etc/skel and that can cause issues since many apps hard code the home folder in the config file.  This causes the live user creation to fail.

You will be able to easily change the boot splash for the live system.  You will be able to add your custom desktop settings including background, panel placement,etc.  I am also trying to figure out easy ways to customize plymouth, grub, gdm, etc.

When I'm done, your grandmother will be able to make an Ubuntu variant.


Very cool. Nice to see you back, Fragadelic. I was definitely saddened to hear when you decided to stop development on Remastersys. Although, from what it sounded like, the lack of support and the stretching you thin by helping so many would get to anybody. :P Anyway, I know I am not the only one to say it is good to hear you are back. 

I am also really glad to hear the Backup Mode will still be around. It is huge for me, and that is the biggest criticism I was most curious about regarding your biggest fork for Remastersys, Relinux when I first ran across it was its 'backup' mode. And I agree, the /etc/skel method, if not done correctly, is quite headachy. I still do not quite have it down. Hehe

Well, I cannot wait to see what is in store with Remastersys. Same goes for my grandmother as well. ;)

---

### Post by Fragadelic on 2011-10-27
Thanks.

I received so many emails from people it was overwhelming.  I never realised how many folks were using it successfully as I only get to hear about the problems - lol.

The next version of remastersys will make dist mode much easier while keeping the backup mode as it has always been.

The gui is going to be extended to help folks do some customizations prior to remastering for dist mode.

---

### Post by mrjoeyman on 2011-10-27
> **Fragadelic said:**
> When I'm done, your grandmother will be able to make an Ubuntu variant.

SWEET!!!!!!!!!!!

Btw, my grandmother would like your number!!!:P

---

### Post by lkjoel on 2011-10-27
Cool!
I've fixed many problems in the /etc/group file, and added a feature for adding extra users in the install.
You might want to add some extra customization, as you can know when someone used remastersys ;).

---

### Post by inashdeen on 2011-10-28
all the best. i really need remastersys to build my new distro. btw, just for tips, why is it the ISO file is rather large??

---

### Post by gluni on 2011-10-28
if you wanne try to make it compatible for sabayon (gentoo) i d be happy to test it.

---

### Post by Fragadelic on 2011-10-28
> **inashdeen said:**
> all the best. i really need remastersys to build my new distro. btw, just for tips, why is it the ISO file is rather large??

With the size of apps these days it is difficult to keep a live cd under 700MB.  I may also need to look at the compression level of mksquashfs.  The problem with increasing the compression level is that it can take a long time to decompress on older computers.

---

### Post by lkjoel on 2011-10-28
> **Fragadelic said:**
> With the size of apps these days it is difficult to keep a live cd under 700MB.  I may also need to look at the compression level of mksquashfs.  The problem with increasing the compression level is that it can take a long time to decompress on older computers.
Once, with remastersys, as a challenge to myself, I achieved 530MB, but it was quite difficult, and the system was barely usable.

---

### Post by Fragadelic on 2011-10-28
My current OS of choice is a highly customised Ubuntu 11.04 with the following:

lxdm
lxde - desktop
nautilus for file management and desktop icons/background
libreoffice calc,math and writer
bombono
gnomebaker
vlc
firefox
claws mail
gftp
transmission
xchat
synaptic
leafpad
gimp
shotwell

size is 725MB

I would hardly call that an unusable system - lol.

I could get it under 700MB but then I don't have all the apps I want.

A lot can be achieved when you remove the packages that Ubuntu has by default but aren't needed for most things.  Lots of the X.org fonts for other languages are huge.  localepurge also helps to reduce the size.

I don't bother with dvd's or cd's these days.  I just put it on a usb key with startup disk creator.

---

### Post by Fragadelic on 2011-10-28
I also have a very small media center distro I created that is only 300MB with a customised media center app I made using gambas.

Anything is possible if you are willing to take the time to remove everything that isn't needed and you know what you are doing.

---

### Post by kurt18947 on 2011-10-28
> **Fragadelic said:**
> 
<snip>

size is 725MB

I would hardly call that an unusable system - lol.

I could get it under 700MB but then I don't have all the apps I want.

A lot can be achieved when you remove the packages that Ubuntu has by default but aren't needed for most things.  Lots of the X.org fonts for other languages are huge.  localepurge also helps to reduce the size.

I don't bother with dvd's or cd's these days.  I just put it on a usb key with startup disk creator.

It's great to see Remastersys is again active.  Giving creative individuals a means to distribute their work is is excellent. I don't know how common my problem is but I  have a fairly up-to-date system(2 yrs. old) that won't boot from a USB key unless that key has been formatted with Win7.  A newly purchased key created with Unetbootin or "Create system disk" won't boot, I just get "boot error".  Any computer built in the last 10 years and has an optical drive should boot from a DVD so file size doesn't seem so critical as the ability to use optical media.

---

### Post by Fragadelic on 2011-10-28
The standard iso that remastersys makes can be used by startup disk creator and burned to cd/dvd depending on size.

I'm waiting to hear back from the guy that created the remastersys-gtk gui frontend which is much nicer than my zenity/kdialog bash one.  I've asked him if he wants to join me and have his gui included in remastersys as a lot of the new additions will be gui related.

---

### Post by Fragadelic on 2011-10-28
> **lkjoel said:**
> Cool!
I've fixed many problems in the /etc/group file, and added a feature for adding extra users in the install.
You might want to add some extra customization, as you can know when someone used remastersys ;).

Care to share the issue and fix for /etc/group?

---

### Post by Fragadelic on 2011-10-31
lkjoel - I just checked your latest package and you are doing nothing different than you copied from remastersys for /etc/group.  In fact, all the important parts that actually do the work in relinux are copied from remastersys.  Are these just more claims to try and make relinux look better?

I'm kind of curious why you place the hidden file   
"touch $WORKDIR/.filesystem.squashfs.GENERATED.BY.RELINUX.PROOF"
and check for it.  What does it matter who made the filesystem.squashfs?  There have been times where folks have manually built it and need to use it.

Anyway, best of luck with relinux.

---

### Post by hannysabbagh on 2011-10-31
hi there.

glade to see remastersys back to live :)
i used remastersys many times, it worked great with ubuntu 11.10 with gnome-shell 3.2 and unity,the bad thing is that problem with a kernel that don't Contain "aufs",there will be a problem when booting the system and it will not work, same thing with relinux,i only hope that remastersys don't Depend on aufs,so we can add the kernel we want :)
if you want to test it try to install this kernel:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1-oneiric/")
and remove the old kernel,then create the iso file using remastersys and you will see the problemwhen booting.

thanks.

---

### Post by lkjoel on 2011-10-31
> **Fragadelic said:**
> lkjoel - I just checked your latest package and you are doing nothing different than you copied from remastersys for /etc/group.  In fact, all the important parts that actually do the work in relinux are copied from remastersys.  Are these just more claims to try and make relinux look better?

I'm kind of curious why you place the hidden file   
"touch $WORKDIR/.filesystem.squashfs.GENERATED.BY.RELINUX.PROOF"
and check for it.  What does it matter who made the filesystem.squashfs?  There have been times where folks have manually built it and need to use it.

Anyway, best of luck with relinux.
No, it's in the latest SVN release. It has an incredible number of changes and improvements (just check the configuration file, you'll see what I mean).
Thanks for the idea, I'll add a "manual" option.

---

### Post by Fragadelic on 2011-10-31
> **hannysabbagh said:**
> hi there.

glade to see remastersys back to live :)
i used remastersys many times, it worked great with ubuntu 11.10 with gnome-shell 3.2 and unity,the bad thing is that problem with a kernel that don't Contain "aufs",there will be a problem when booting the system and it will not work, same thing with relinux,i only hope that remastersys don't Depend on aufs,so we can add the kernel we want :)
if you want to test it try to install this kernel:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1-oneiric/")
and remove the old kernel,then create the iso file using remastersys and you will see the problemwhen booting.

thanks.

aufs is used for mounting the live filesystem.  If they are doing something different with the live I'll need to know about it.

---

### Post by Fragadelic on 2011-10-31
> **lkjoel said:**
> No, it's in the latest SVN release. It has an incredible number of changes and improvements (just check the configuration file, you'll see what I mean).
Thanks for the idea, I'll add a "manual" option.

Colin Watson and I discussed something a while back that I'm finally getting a chance to check out.  If it works I'll post details here about it as it does make an impact on the remaster.

I've made my changes and made a test iso.  Just about to try booting and installing from it.

---

### Post by duggum on 2011-10-31
Fragadelic,

Any idea when the download page will be working?

Still getting this when I try to access it from the forum:

> Warning: Invalid argument supplied for foreach() in /home/content/g/e/e/geekydude/html/remastersys/downloads/index.php on line 89

Warning: array_multisort() [function.array-multisort]: Argument #1 is expected to be an array or a sort flag in /home/content/g/e/e/geekydude/html/remastersys/downloads/index.php on line 92
Index of /downloads

Warning: Invalid argument supplied for foreach() in /home/content/g/e/e/geekydude/html/remastersys/downloads/index.php on line 137

Cheers!

d

---

### Post by Fragadelic on 2011-10-31
> **duggum said:**
> Fragadelic,

Any idea when the download page will be working?

Still getting this when I try to access it from the forum:



Cheers!

d

If the repo isn't working you can get it from the direct link.

[http://www.geekconnection.org/remastersys/repository/](http://www.geekconnection.org/remastersys/repository/)

That last one I have there is in the karmic folder.  I am working on the new one right now and hopefully it will be ready shortly(week or so)

---

### Post by c.cobb on 2011-11-01
Great to hear you're working on this again. I use it to build a custom remix of Lucid that I run from a Live USB, and remastersys is very helpful.

One question: What's the way remove the Install icon from the desktop? 

This *used* to be easy. . . When I started remastering earlier this year, removing the install icon was done simply by removing the entry from /etc/skel/Desktop -- however, after running update manager to make everything current, something changed and this no longer works. Is this controlled through a kernel boot option or something now?

Related question: Anyone know of a list somewhere that gives all the kernel boot options available? Even if it's in a source or header file somewhere. . . it would be great to have a reference for this!

---

### Post by Fragadelic on 2011-11-01
> **c.cobb said:**
> Great to hear you're working on this again. I use it to build a custom remix of Lucid that I run from a Live USB, and remastersys is very helpful.

One question: What's the way remove the Install icon from the desktop? 

This *used* to be easy. . . When I started remastering earlier this year, removing the install icon was done simply by removing the entry from /etc/skel/Desktop -- however, after running update manager to make everything current, something changed and this no longer works. Is this controlled through a kernel boot option or something now?

Related question: Anyone know of a list somewhere that gives all the kernel boot options available? Even if it's in a source or header file somewhere. . . it would be great to have a reference for this!

If you are using dist mode then it is placed there by casper during live boot.

If you are using backup mode then it is placed there by remastersys during remastering.  Commenting out the copy section in /usr/bin/remastersys will fix that.

---

### Post by BrokenKingpin on 2011-11-01
> **Fragadelic said:**
> This is exactly what I am planning on adding with the extra scripts I have created for my own use.

My goal is to make it extremely easy to create your own flavour of Ubuntu and all options will be accessible from gui and cli modes.  It will of course always have the backup mode for personal backups as it has always had.

Some folks blindly copy files from the user home folder to /etc/skel and that can cause issues since many apps hard code the home folder in the config file.  This causes the live user creation to fail.

You will be able to easily change the boot splash for the live system.  You will be able to add your custom desktop settings including background, panel placement,etc.  I am also trying to figure out easy ways to customize plymouth, grub, gdm, etc.

When I'm done, your grandmother will be able to make an Ubuntu variant.
That would be quite amazing!

---

### Post by 1roxtar on 2011-11-01
This is great news.  Remastersys has been one of my all-time favorite tools.  It has been a very productive tool by allowing me to create an Ubuntu LiveCD with all the restricted extras and various programs that I find useful.  I get to have my very own complete distro that I can install out-of-the box.  Thank you!!!  I will be testing this with Ubuntu 11.10 and share any feedback.

---

### Post by inameiname on 2011-11-01
> **Fragadelic said:**
> If you are using dist mode then it is placed there by casper during live boot.

If you are using backup mode then it is placed there by remastersys during remastering.  Commenting out the copy section in /usr/bin/remastersys will fix that.

Oh cool. I will have to remember this. I always change my Desktop to '~/.desktop' anyway, and after every Remastersys backup (Backup Mode) I am left with a '~/Desktop' text file in my home directory that needs to be remove. Sounds like this will fix that. Thanks.

---

### Post by c.cobb on 2011-11-01
> **Fragadelic said:**
> [QUOTE=c.cobb;11414899]One question: What's the way remove the Install icon from the desktop?If you are using dist mode then it is placed there by casper during live boot.[/QUOTE]

Thanks, Fragadelic. Sure seems like something changed recently, but what do I know? Anyway, adding a step in /etc/rc.local to remove the file works nicely, fwiw.

---

### Post by Fragadelic on 2011-11-02
> **inameiname said:**
> Oh cool. I will have to remember this. I always change my Desktop to '~/.desktop' anyway, and after every Remastersys backup (Backup Mode) I am left with a '~/Desktop' text file in my home directory that needs to be remove. Sounds like this will fix that. Thanks.

I'll add an option in the config file for this so all you will have to do is decide if you want it or not.

I have some real goodies coming for dist mode in the next version.  Most is done and tested by me.  As soon as I finish it I'll send my gui changes to the remastersys-gtk dev as he has agreed to work on the official gui for remastersys.  I will be putting up an interim package once all my changes are completed and before the final gui is ready so the meat and potatoes can be tested out prior to official release.

---

### Post by Portaro on 2011-11-02
__

Thanks for spread remastersys to our comunnity.

This is my first post in this international forum to say thanks for remastersys continues to 11.10.

Greetings.

---

### Post by lkjoel on 2011-11-02
> **Fragadelic said:**
> I'll add an option in the config file for this so all you will have to do is decide if you want it or not.

I have some real goodies coming for dist mode in the next version.  Most is done and tested by me.  As soon as I finish it I'll send my gui changes to the remastersys-gtk dev as he has agreed to work on the official gui for remastersys.  I will be putting up an interim package once all my changes are completed and before the final gui is ready so the meat and potatoes can be tested out prior to official release.
I can help test it. I have a custom middle-range amd64 box (AMD VISION A6, 8GB RAM, 2TB HD, AMD Radeon HD 6530D).

---

### Post by inameiname on 2011-11-02
> **Fragadelic said:**
> I'll add an option in the config file for this so all you will have to do is decide if you want it or not.

I have some real goodies coming for dist mode in the next version.  Most is done and tested by me.  As soon as I finish it I'll send my gui changes to the remastersys-gtk dev as he has agreed to work on the official gui for remastersys.  I will be putting up an interim package once all my changes are completed and before the final gui is ready so the meat and potatoes can be tested out prior to official release.


Cool. I'll look forward to not having to deal with that ~/Desktop' text file. :) And although I usually use the Backup Mode, I will also have to check what's new with the Distro Mode, as mentioned.

Also, that is great to hear that you have gotten the remastersys-gtk folks on board to help you out with improving the GUI. Maybe with that added assistance you can have a bit more time for making the actual guts of Remastersys even better. ;)

Speaking of Remastersys, do you happen to know why after a backup of my Oneiric system using remastersys it actually retained the auto-login setting I had for it, something that hasn't worked/been done in Natty, or any previous Ubuntu versions for some time? Not to complain or anything, as now my custom.iso live disc auto-logins upon running. I am just curious what would be different, as it is the same version of remastersys used. Oh and by the way, my backup of my 11.10 system worked flawlessly. I had my doubts upon reading so many's woes with doing such.

---

### Post by Fragadelic on 2011-11-03
I have finished with preliminary version of remastersys 3.0.0 for Ubuntu Lucid and newer.

If you would like to test it out, please download the following file and install it.  There are many new features that need to be tested out and this should be tested on a development install and not a real working install as it may bork your system and I will not be held responsible.

With that disclaimer, here is the file.

[http://www.geekconnection.org/remastersys/repository/ubuntu-testing/remastersys_3.0.0-1_all.deb](http://www.geekconnection.org/remastersys/repository/ubuntu-testing/remastersys_3.0.0-1_all.deb)

If you do test it out, please provide me with feedback in this thread.

Changes and additions:

Added option in the gui to choose the background picture for the live boot.
Added option in the gui to choose the background picture for grub.
Added option to copy relevant settings from your user folder into /etc/skel safely.
Added option to create a simple plymouth theme with your own background picture.
Added SQUASHFSOPTS option in the config file for more flexibility.  Using "-comp -xz" in the options will reduce the size of the iso considerably but at the same time may cause issues for older single core processors so don't use this option if your target audience is older PC's.  It also takes much longer to build the squashfs file with this option.
Fixed installer frontend not being installed issue
Other minor fixes and tweaks.

I almost forgot - I changed the iso build portion to make an iso level 3 which may or may not get rid of the 4GB limit per file.  Please test this out with backup mode on larger installs.

What hasn't made it in yet is the option exclude the installer from the desktop of the backup mode but that will be in the final version of 3.0.0 at the latest.

---

### Post by inameiname on 2011-11-03
> **Fragadelic said:**
> I have finished with preliminary version of remastersys 3.0.0 for Ubuntu Lucid and newer.

If you would like to test it out, please download the following file and install it.  There are many new features that need to be tested out and this should be tested on a development install and not a real working install as it may bork your system and I will not be held responsible.

With that disclaimer, here is the file.

[http://www.geekconnection.org/remastersys/repository/ubuntu-testing/remastersys_3.0.0-1_all.deb](http://www.geekconnection.org/remastersys/repository/ubuntu-testing/remastersys_3.0.0-1_all.deb)

If you do test it out, please provide me with feedback in this thread.

Changes and additions:

Added option in the gui to choose the background picture for the live boot.
Added option in the gui to choose the background picture for grub.
Added option to copy relevant settings from your user folder into /etc/skel safely.
Added option to create a simple plymouth theme with your own background picture.
Added SQUASHFSOPTS option in the config file for more flexibility.  Using "-comp -xz" in the options will reduce the size of the iso considerably but at the same time may cause issues for older single core processors so don't use this option if your target audience is older PC's.  It also takes much longer to build the squashfs file with this option.
Fixed installer frontend not being installed issue
Other minor fixes and tweaks.

I almost forgot - I changed the iso build portion to make an iso level 3 which may or may not get rid of the 4GB limit per file.  Please test this out with backup mode on larger installs.

What hasn't made it in yet is the option exclude the installer from the desktop of the backup mode but that will be in the final version of 3.0.0 at the latest.

Hey cool, man. I will have to look at this when I get a few moments. Glad you see you are coming along so much so fast.

So the DistSkel option will actually make a Distro ISO that includes all of my $HOME directory?

---

### Post by Fragadelic on 2011-11-03
> **inameiname said:**
> Hey cool, man. I will have to look at this when I get a few moments. Glad you see you are coming along so much so fast.
I had most of it done except for the gui additions.  I still have to talk to Colin Watson about something we spoke about a while ago as it didn't work out as expected and if that works out it will get even better.

---

### Post by lkjoel on 2011-11-03
> **Fragadelic said:**
> I have finished with preliminary version of remastersys 3.0.0 for Ubuntu Lucid and newer.

If you would like to test it out, please download the following file and install it.  There are many new features that need to be tested out and this should be tested on a development install and not a real working install as it may bork your system and I will not be held responsible.

With that disclaimer, here is the file.

[http://www.geekconnection.org/remastersys/repository/ubuntu-testing/remastersys_3.0.0-1_all.deb](http://www.geekconnection.org/remastersys/repository/ubuntu-testing/remastersys_3.0.0-1_all.deb)

If you do test it out, please provide me with feedback in this thread.

Changes and additions:

Added option in the gui to choose the background picture for the live boot.
Added option in the gui to choose the background picture for grub.
Added option to copy relevant settings from your user folder into /etc/skel safely.
Added option to create a simple plymouth theme with your own background picture.
Added SQUASHFSOPTS option in the config file for more flexibility.  Using "-comp -xz" in the options will reduce the size of the iso considerably but at the same time may cause issues for older single core processors so don't use this option if your target audience is older PC's.  It also takes much longer to build the squashfs file with this option.
Fixed installer frontend not being installed issue
Other minor fixes and tweaks.

I almost forgot - I changed the iso build portion to make an iso level 3 which may or may not get rid of the 4GB limit per file.  Please test this out with backup mode on larger installs.

What hasn't made it in yet is the option exclude the installer from the desktop of the backup mode but that will be in the final version of 3.0.0 at the latest.
What about us terminal geeks? Sure, you added nice features in the GUI, but no features for terminal geeks?

---

### Post by Fragadelic on 2011-11-03
> **lkjoel said:**
> What about us terminal geeks? Sure, you added nice features in the GUI, but no features for terminal geeks?

Since the installer is only gui and you have to have a gui for the live it made no sense to try to create a cli version of my gui.  The gui options require input from the user which would require at least dialog anyway.  True terminal geeks frown upon dialog anyway and would probably know how to do most of those things by hand anyway.

These options are for those that just want to make their own personal backup or distribution with as little fuss as possible.  The thing I might add in the future is customisation for the login manager but since there are so many different ones I haven't done it yet.

The SQUASHFSOPTS is available to terminal geeks via the /etc/remastersys.conf file as usual.

---

### Post by lkjoel on 2011-11-03
Ah ok. So is remastersys-gtk going to be packaged with remastersys 3.0?

---

### Post by Fragadelic on 2011-11-03
> **lkjoel said:**
> Ah ok. So is remastersys-gtk going to be packaged with remastersys 3.0?

That is the plan if the USU team can get it completed.

I had to put up an update so if anyone downloaded this prior to this message they will need to download again.

I also added the do not show the install icon on the desktop for backup mode.

---

### Post by lkjoel on 2011-11-03
> **Fragadelic said:**
> That is the plan if the USU team can get it completed.

I had to put up an update so if anyone downloaded this prior to this message they will need to download again.

I also added the do not show the install icon on the desktop for backup mode.
What about an option to remove remastersys after install?

---

### Post by Fragadelic on 2011-11-03
> **lkjoel said:**
> What about an option to remove remastersys after install?

That would be absolutely absurd as one of the main functions of remastersys is to backup your system to live.  Can't do that if remastersys is removed.

Remastersys is not just for creating a live distribution based on Ubuntu.  It has been used by many folks for the backup mode only.  If it was just for making the initial iso then that would be fine but its more important function is to backup your system.  It has saved me at home when I had a hard drive crash on me.  I was able to get back up and running immediately without a hard drive since my system was backed up to live.

---

### Post by Fragadelic on 2011-11-03
With the new option in squashfs since February of this year(Available to 11.04 and newer Ubuntu's) it allows lzma compression to be used which reduced my 725MB iso to 578MB.  The only drawback is that it can have issues with single core processors as I believe things timeout during boot due to the higher decompression needed.  With a dual core it works fine.

---

### Post by lkjoel on 2011-11-03
OK, I meant the distro mode option.
I've used lzma a lot, but it takes a long time to compress and decompress. I suggest you add an option instead of putting it default.

As you said, remastersys is more for the backup, and less of the distro. Relinux is completely for the distro, and the backup will be removed from it. It would be great if we could give each other ideas for our projects, knowing that they are made for a different purpose.

---

### Post by Fragadelic on 2011-11-03
> **lkjoel said:**
> OK, I meant the distro mode option.
I've used lzma a lot, but it takes a long time to compress and decompress. I suggest you add an option instead of putting it default.

As you said, remastersys is more for the backup, and less of the distro. Relinux is completely for the distro, and the backup will be removed from it. It would be great if we could give each other ideas for our projects, knowing that they are made for a different purpose.

I never said it was for less of the distro.  Different folks use it for different reasons but both are very important and have been from the beginning.  In fact most of the new options are specifically geared towards dist mode to make it easier for folks to customise their systems and make a dist remaster.

Higher compression is important for 2 reasons:

1 - will allow some distro makers to fit on a 700MB cd
2 - will reduce the size of the backup iso making it possible to fit more data on a dvd

Remastersys has always been geared towards both the dist and backup modes which is why I have maintained them both for over 5 years now.  Neither option is going away as long as I continue to develop remastersys.

Sharing ideas is not a bad idea.  It will make both projects better and then folks can use whichever one they prefer or whichever one suits their specific needs better.  Choice is good.

You are already signed up and have been posting on my forum so we can discuss development issues over there if you like.

---

### Post by lkjoel on 2011-11-03
Ah ok thanks for clarifying.

I never said that you should not use higher compression, because I do know how important it is (take for example my Network info script, which outputs: network-info.txt.***bz2.lzma***), I just said that you should add an option.

Sure, or we can contact by email or chat. My email is [email]lkjoel@ubuntu.com[/email], my chat ID is [email]lkjoeldev@gmail.com[/email].

---

### Post by hannysabbagh on 2011-11-03
> **Fragadelic said:**
> aufs is used for mounting the live filesystem.  If they are doing something different with the live I'll need to know about it.
sorry for late.

yes it is,but they are not doing anything for booting the live filesystem those kernels is only for desktop use,but what i am asking for is a tweak/solve/anything but just a solution to make that kernel works with remastersys! D:
 
thanks

---

### Post by ezsit on 2011-11-03
Frag, great to hear you are back in business! I was ready to jump ship to Fedora and learn Revisor after my Lucid install went into EOL status. I am soooo happy to hear you have a renewed determination to keep Remastersys going. 

I have used it exclusively in DIST mode for personal backup purposes since Ubuntu 7.04. Since I keep all data separately backed up on removable hard drives, DIST mode served me well as I prefer to not have the OS installation contain any personal information. This has also allowed me to share my installation with friends and colleagues if I so desire.

Thanks for all the hard work you put into Remastersys. Your's is the only tool that keeps me with Ubuntu and allows me the piece of mind to experiment and always know I can return to a working install in less than 10 minutes.

BTW, I would not bother with increasing the compression at the possible cost of boot time, especially on older computers, since burning to DVD is easy, cheap and USB sticks are cheap and readily available. The size of the CD should not be the determining factor. Anyhow, a DVD reader/writer can be added to an older computer a lot cheaper and easier than making an older computer fast enough to decompress a highly compressed CD for booting purposes. Just a thought.

---

### Post by luk1don on 2011-11-03
Hi Fragadelic, Thanks for developing:P
I thought that mksquashfs default uses lzma and no gzip (earlier was different). I need better compression... 
> #SQUASHFSOPTS="-no-recovery -always-use-fragments **-comp xz** -b 1M -no-duplicates"
I have to uncomment this line. Why option is: -comp xz and not -comp lzma or something? I know, xz it is lzma2, but older lzma probably was better compression level. What about initrd compression, is it possible to change initrd.gz on initrd.lz? (Ubuntu Customization Kit does something like this).
I have:
> Parallel mksquashfs: Using 1 processor
Why? Any options? Should be something like make flag: -j2 or CONCURRENCY_LEVEL=X (kernel compiling), on core duo machines: 3, every time +1.
My sugestion is to change your zenity script output from xterm to normal terminal, xterm is a bit annoying.
> /usr/bin/remastersys: line 264: /home/remastersys/remastersys/dummysys/etc/gdm/gdm.conf-custom: No such file or directory
?

---

### Post by Fragadelic on 2011-11-03
> **ezsit said:**
> Frag, great to hear you are back in business! I was ready to jump ship to Fedora and learn Revisor after my Lucid install went into EOL status. I am soooo happy to hear you have a renewed determination to keep Remastersys going. 

I have used it exclusively in DIST mode for personal backup purposes since Ubuntu 7.04. Since I keep all data separately backed up on removable hard drives, DIST mode served me well as I prefer to not have the OS installation contain any personal information. This has also allowed me to share my installation with friends and colleagues if I so desire.

Thanks for all the hard work you put into Remastersys. Your's is the only tool that keeps me with Ubuntu and allows me the piece of mind to experiment and always know I can return to a working install in less than 10 minutes.

BTW, I would not bother with increasing the compression at the possible cost of boot time, especially on older computers, since burning to DVD is easy, cheap and USB sticks are cheap and readily available. The size of the CD should not be the determining factor. Anyhow, a DVD reader/writer can be added to an older computer a lot cheaper and easier than making an older computer fast enough to decompress a highly compressed CD for booting purposes. Just a thought.

The option is there to change it in the config file and the dialog explains both sets of options.  I will probab,ly leave the default without the extra compression since lucid doesn't support the option anyway.

Thanks for the very kind words about remastersys.

---

### Post by Fragadelic on 2011-11-03
> **luk1don said:**
> Hi Fragadelic, Thanks for developing:P
I thought that mksquashfs default uses lzma and no gzip (earlier was different). I need better compression... 

I have to uncomment this line. Why option is: -comp xz and not -comp lzma or something? I know, xz it is lzma2, but older lzma probably was better compression level. What about initrd compression, is it possible to change initrd.gz on initrd.lz? (Ubuntu Customization Kit does something like this).
I have:

Why? Any options? Should be something like make flag: -j2 or CONCURRENCY_LEVEL=X (kernel compiling), on core duo machines: 3, every time +1.
My sugestion is to change your zenity script output from xterm to normal terminal, xterm is a bit annoying.

?

The actual mksquashfs mode is "-comp xz" and you can see that by just typing mksquashfs in a terminal window and reading the output.  You can change it to "-comp lzo" if you like.  That is why it is an open field in the config file and the gui.  I just caution folks against using wildcards as I tried them and it caused mksquashfs to do absolutely nothing - it failed to create the filesystem.squashfs.  I just chose what seemed to be the best option.

As far as compressing the initrd further I'm not sure since it has to work with Ubuntu's usb creator and the current method works fine.  I'll look into it though.

mksquashfs will use as many processors as you really have.  On the single core system I use it on they use a single thread and on the dual cores they use both.

As for changing the output from xterm I'm afraid that isn't possible due to the fact that remastersys is for all desktops and not just gnome or kde.  What is available in gnome and kde is not always available on all systems.  In fact my own custom setup uses a mix of lxde and gnome(minimal).  xterm is the only thing guaranteed to be on any system with a gui.  Not all window managers use the xdg terminal calls either so I can't use that.  I know you may find it a pain but I have to think about the bigger picture when I am creating remastersys.  It has to work with everything from fvwm and icewm to gnome and kde.

The gdm.conf-custom is there for older gnome versions.  Most settings in this file end up causing casper to fail on user creation adn login so it is left out for dist mode.  Please remember that I try to make remastersys work with as many versions as possible and the oldest version for this one is lucid.

---

### Post by cbowman57 on 2011-11-03
If we encounter a problem is there  modifier for a debug output or do you prefer that we just raise any issues in this thread?

---

### Post by Fragadelic on 2011-11-03
> **cbowman57 said:**
> If we encounter a problem is there  modifier for a debug output or do you prefer that we just raise any issues in this thread?

You can either post here or on my forum.  If you do, there should be a remastersys.log file in the working directory that should have information I can use.  I added some thigns to the log output in this versions as well based on common questions I seemed to ask after seeing the original log output.

---

### Post by cbowman57 on 2011-11-03
> **Fragadelic said:**
> You can either post here or on my forum.  If you do, there should be a remastersys.log file in the working directory that should have information I can use.  I added some thigns to the log output in this versions as well based on common questions I seemed to ask after seeing the original log output.

Good enough, thanks. :)

---

### Post by inobe on 2011-11-03
i first imagined remastersys as being an alternative to windows shadowcopy, backup/ restore etc...

that'll be spot on to what is most wanted, that or the ability to install a deb based distribution with all the custom extras "all at once" 

either or both are priceless.

---

### Post by inameiname on 2011-11-04
> **Fragadelic said:**
> I had most of it done except for the gui additions.  I still have to talk to Colin Watson about something we spoke about a while ago as it didn't work out as expected and if that works out it will get even better.

I figured as much. Well I am sure all of us will keep hoping for it all working out for the better. Hehe

---

### Post by inameiname on 2011-11-04
> **Fragadelic said:**
> That is the plan if the USU team can get it completed.

I had to put up an update so if anyone downloaded this prior to this message they will need to download again.

I also added the do not show the install icon on the desktop for backup mode.


An update where? You mean for the link you gave for remastersys_3.0.0-1_all.deb?

---

### Post by inameiname on 2011-11-04
> **Fragadelic said:**
> That would be absolutely absurd as one of the main functions of remastersys is to backup your system to live.  Can't do that if remastersys is removed.

Remastersys is not just for creating a live distribution based on Ubuntu.  It has been used by many folks for the backup mode only.  If it was just for making the initial iso then that would be fine but its more important function is to backup your system.  It has saved me at home when I had a hard drive crash on me.  I was able to get back up and running immediately without a hard drive since my system was backed up to live.

Precisely. That was my thoughts when I saw that the remastersys fork, relinux, was having it removed as a default. Of course, I know it is more for Distro backups, and as a Backup backup person, having it around for each backup/update is essential.

---

### Post by inameiname on 2011-11-04
> **Fragadelic said:**
> 
As far as compressing the initrd further I'm not sure since it has to work with Ubuntu's usb creator and the current method works fine.  I'll look into it though.


Speaking about Ubuntu's usb creator, do you know why all Remastersys backed-up ISOs, when used with usb-creator-gtk, grey out the persistence space option? This only ever seems to happen with Remastered images, not original ISOs from the distro's website.

---

### Post by qunungnauraq on 2011-11-04
I am running ubuntu 11.10 64 bit with gnome shell 3.2 and most of the gnome shell extensions. I installed and tested remastersys_3.0.0-1_all.deb and the result is that ubuntu gets stuck at checking battery during boot. In order to reboot I need to select rescue mode. Even after uninstalling  remastersys_3.0.0-1_all.deb I still need rescue mode to reboot. I tried two different backup images using paragon backup & recovery with the same results. The other problem is I have not been able to make a persistent live usb using this or the previous version in ubuntu 11.10 with gnome shell 3.2 but have successfully made a non persitent live usb.  I have not tested remastersys with the unity version. I am using a Lenovo Thinkpad T510 with discrete graphics 8GB ram and a 256GB crucial SSD.

---

### Post by Fragadelic on 2011-11-04
> **inameiname said:**
> Speaking about Ubuntu's usb creator, do you know why all Remastersys backed-up ISOs, when used with usb-creator-gtk, grey out the persistence space option? This only ever seems to happen with Remastered images, not original ISOs from the distro's website.

I noticed that starting to happen on my remaster so something changed along the way.  I'll take a look at the usb creator code and see if I can figure it out.  If in fact there is something I can do to correct it, it will be included in the 3.0.0 release.

Any updates I do to it will simply be on the same package so you can just check the timestamp on the download.  It is too much work for me to keep changing the version numbers so I usually just make it the final version number and update it as needed.  This is only for testing though.  Once this gets released, any further updates will get a new version number.

---

### Post by Fragadelic on 2011-11-04
> **qunungnauraq said:**
> I am running ubuntu 11.10 64 bit with gnome shell 3.2 and most of the gnome shell extensions. I installed and tested remastersys_3.0.0-1_all.deb and the result is that ubuntu gets stuck at checking battery during boot. In order to reboot I need to select rescue mode. Even after uninstalling  remastersys_3.0.0-1_all.deb I still need rescue mode to reboot. I tried two different backup images using paragon backup & recovery with the same results. The other problem is I have not been able to make a persistent live usb using this or the previous version in ubuntu 11.10 with gnome shell 3.2 but have successfully made a non persitent live usb.  I have not tested remastersys with the unity version. I am using a Lenovo Thinkpad T510 with discrete graphics 8GB ram and a 256GB crucial SSD.

Can you post the remastersys.log from your install where you remastered from?

If the -comp xz option is in the SQUASHFSOPTS, remove that so it defaults back to the original command I have always used for mksquashfs.  Then run the remaster again.

---

### Post by Fragadelic on 2011-11-04
> **inameiname said:**
> Speaking about Ubuntu's usb creator, do you know why all Remastersys backed-up ISOs, when used with usb-creator-gtk, grey out the persistence space option? This only ever seems to happen with Remastered images, not original ISOs from the distro's website.

I just went through the usb-creator-gtk code and it imposes a minimum of 1024MB

/usr/share/pyshared/usbcreator/misc.py
```
# The minimum size, in megabytes a persistence file can be.
MIN_PERSISTENCE = 1024
MAX_PERSISTENCE = 4096 # VFAT maximum file size.
# Padding for the kernel and initramfs, in megabytes
PADDING = 30
(CAN_USE,     # Obvious.
 CANNOT_USE,  # The partition or disk is too small for the source image.
 NEED_SPACE,  # There is not enough free space, but there could be.
 NEED_FORMAT, # The device has the wrong filesystem type, or the source is a
              # disk image.
) = range(4)

```

So you will need a usb key at least 1GB larger than your iso file in order for the persistent option to show up.

---

### Post by Fragadelic on 2011-11-04
> **inobe said:**
> i first imagined remastersys as being an alternative to windows shadowcopy, backup/ restore etc...

that'll be spot on to what is most wanted, that or the ability to install a deb based distribution with all the custom extras "all at once" 

either or both are priceless.

Have you tried remastersys?

It takes your install and makes a live iso out of it that isn't tied to your hardware.  If your system dies, you just use the dvd iso to put it back like a normal Ubuntu live cd except that it has all your personalized stuff including whatever apps you installed.

This, I believe, is better than anything else since you can run your backed up iso just like your install and if you have it on a usb key with persistence you will even be able to save your settings.

It accomplishes what you mention but in an easy and complete way.  The only issue is the limit imposed by genisomage of 4GB per file on an iso.  genisoimage does have an iso level 3 setting which is what I set as default for this version which may be able to ignore that limit so it can build a larger backup.

Colin Watson and I spoke quite a while back about the ability to have multiple squashfs files and it does work but install will not due to the fact that only the first squashfs file gets remounted to /rofs and/rofs is the source for the install.  I have to sign up to the mailing list again and continue the discussion with him.  I have all the code in the new remastersys to handle this but it is commented out right now.  If in the future Colin can get it to use more than 1 squashfs file in /rofs then I will enable it and it will allow for much larger backups.  I tried changing casper to link all of the squashfs files under /rofs but it wouldn't work.  If I manually did it while in live it worked but for some strange reason it wouldn't during bootup.  The live uses dash and busybox and I used the commands on them fine but it just wouldn't work during boot.

---

### Post by Fragadelic on 2011-11-04
> **qunungnauraq said:**
> I am running ubuntu 11.10 64 bit with gnome shell 3.2 and most of the gnome shell extensions. I installed and tested remastersys_3.0.0-1_all.deb and the result is that ubuntu gets stuck at checking battery during boot. In order to reboot I need to select rescue mode. Even after uninstalling  remastersys_3.0.0-1_all.deb I still need rescue mode to reboot. I tried two different backup images using paragon backup & recovery with the same results. The other problem is I have not been able to make a persistent live usb using this or the previous version in ubuntu 11.10 with gnome shell 3.2 but have successfully made a non persitent live usb.  I have not tested remastersys with the unity version. I am using a Lenovo Thinkpad T510 with discrete graphics 8GB ram and a 256GB crucial SSD.

Remastersys doesn't change anything on your system except install casper which is placed in the initrd.  Everything else does nothing to the base system.  Check your apt sources as sometimes some of the ppa's have versions of the live stuff like casper and ubiquity that aren't standard and can cause issues.  Folks customise them for themselves and have them in their ppa's but they cause problems with normal setups.

In fact, any of the files that remastersys changes are copied to the dummysys folder and altered there so the base system is left untouched.

---

### Post by cbowman57 on 2011-11-04
Ok, tried dist mode on 12.04 minimal installation with Gnome only.

Live session works great.

Installer crashes, probably not the fault of Remastersys but might have something to do with it being a mini install.   (Also it could be that ubiquity is not yet compatible with 12.04)

Attaching log if you care to review it.

---

### Post by Fragadelic on 2011-11-04
> **cbowman57 said:**
> Ok, tried dist mode on 12.04 minimal installation with Gnome only.

Live session works great.

Installer crashes, probably not the fault of Remastersys but might have something to do with it being a mini install.  

Attaching log if you care to review it.

Everything in the log looks ok.  Can you run the installer from a terminal window on the live and see what messages come up?  Seems that sometimes not all of the deps are in the installer packages as there is an assumption at times about what is installed.  If you find out you are missing a package, let me know which one it is and I'll put it as a dep for remastersys so it doesn't happen again.

---

### Post by cbowman57 on 2011-11-04
Here's an image of the error as reported by ubiquity.

[ATTACH]206308[/ATTACH]

---

### Post by Fragadelic on 2011-11-04
> **cbowman57 said:**
> Here's an image of the error as reported by ubiquity.

[ATTACH]206308[/ATTACH]

Hmmm...  thats a partitioning issue.  Can you post your package list.

Can you do the following and attach the file here:

sudo dpkg --get-selections > cbowmanpkglst.txt

---

### Post by cbowman57 on 2011-11-04
It occurs right after I select the partitioner, nautilus pops open & it starts scanning every partition, then it craps out.

You want that information from within the live session or the installation I built it from?

---

### Post by Fragadelic on 2011-11-04
> **cbowman57 said:**
> It occurs right after I select the partitioner, nautilus pops open & it starts scanning every partition, then it craps out.

You want that information from within the live session or the installation I built it from?

No.  From your original system.  I need to know what is installed.  It looks like maybe libparted or something is not installed and that will show me your package list.

---

### Post by cbowman57 on 2011-11-04
Here it is.

---

### Post by Fragadelic on 2011-11-04
> **cbowman57 said:**
> Here it is.

That appears to have everything it needs for ubiquity and partitioning.

At this point I think I need to see the terminal output when running the installer from the live session - launched from the terminal so all the output shows up.  This usually shows more than the small amount of info in that dialog.

Also try to see if there are files in /var/lib/installer/ after it crashes and post those too.

If we can figure out exactly what is causing the crash then we can start to fix it.

---

### Post by cbowman57 on 2011-11-04
Sure, pardon what may seem to be a stupid question but exactly what command (for the installer) should I use to execute from the terminal?

I tried just using "ubiquity" earlier and it just launched, there was no terminal output.

thanks.

---

### Post by Fragadelic on 2011-11-04
> **cbowman57 said:**
> Sure, pardon what may seem to be a stupid question but exactly what command (for the installer) should I use to execute from the terminal?

I tried just using "ubiquity" earlier and it just launched, there was no terminal output.

thanks.

ubiquity gtk_ui

Should work.  It normally does provide more info in the terminal window.

---

### Post by cbowman57 on 2011-11-04
> **Fragadelic said:**
> ubiquity gtk_ui

Should work.  It normally does provide more info in the terminal window.

Nothing more is displayed.  I'm feeling like a real bonehead. :)

Going to try installing from the splash menu, see if I get different results.  Could be a gnome shell quirk.
* Results the same, should have expected that.  Have a couple other things to check out.

---

### Post by inameiname on 2011-11-04
> **Fragadelic said:**
> I just went through the usb-creator-gtk code and it imposes a minimum of 1024MB

/usr/share/pyshared/usbcreator/misc.py
```
# The minimum size, in megabytes a persistence file can be.
MIN_PERSISTENCE = 1024
MAX_PERSISTENCE = 4096 # VFAT maximum file size.
# Padding for the kernel and initramfs, in megabytes
PADDING = 30
(CAN_USE,     # Obvious.
 CANNOT_USE,  # The partition or disk is too small for the source image.
 NEED_SPACE,  # There is not enough free space, but there could be.
 NEED_FORMAT, # The device has the wrong filesystem type, or the source is a
              # disk image.
) = range(4)

```So you will need a usb key at least 1GB larger than your iso file in order for the persistent option to show up.

Hmm, thanks for finding that bit of info on the startup disk creator. It makes sense. Though, I don't know why that would be the 'minimum'. If all you are doing is a little saving here and there in a live session, a couple hundred megs is more than enough.

I guess the reason why it is always greyed out as an option for me is the fact that I use partitions. Even though a use fairly large usb keys, 4GB+, and always have more than 1GB more in room, I often just have one partition of 2GB for my custom iso, 1.5GB being for my backup, and ideally 500MB for my persistence.

Thanks again for letting us know! I wonder if there would be any harm in simply lowering that number.

---

### Post by Fragadelic on 2011-11-04
> **inameiname said:**
> Hmm, thanks for finding that bit of info on the startup disk creator. It makes sense. Though, I don't know why that would be the 'minimum'. If all you are doing is a little saving here and there in a live session, a couple hundred megs is more than enough.

I guess the reason why it is always greyed out as an option for me is the fact that I use partitions. Even though a use fairly large usb keys, 4GB+, and always have more than 1GB more in room, I often just have one partition of 2GB for my custom iso, 1.5GB being for my backup, and ideally 500MB for my persistence.

Thanks again for letting us know! I wonder if there would be any harm in simply lowering that number.

You can try and see if it works for you.  Not sure about the reasoning.

---

### Post by Fragadelic on 2011-11-04
> **cbowman57 said:**
> Nothing more is displayed.  I'm feeling like a real bonehead. :)

Going to try installing from the splash menu, see if I get different results.  Could be a gnome shell quirk.
* Results the same, should have expected that.  Have a couple other things to check out.

If you can get a regular xsession with xterm up instead of gnome shell or launch xterm and run the command from there.

---

### Post by cbowman57 on 2011-11-04
> **Fragadelic said:**
> If you can get a regular xsession with xterm up instead of gnome shell or launch xterm and run the command from there.

No difference, I did try a couple things though.

Ran it from the nearly identical setup but built on 11.10, nautilus did it's auto-open thing but the installation went perfectly.

Major differences between the two attempts:

I had not activated the skel option in 11.10, I used it in 12.04.

Thought maybe some mounted & bind partitions might have had a part in the failure but removed those entries in 12.04, no change, left them intact on the 11.10 version install and it was successful anyway.

Think I'll just monitor progress & see if anyone else is successful with the 12.04 desktop iso or not.

:)

---

### Post by zer010 on 2011-11-04
It's awesome that you're working on Remastersys again! An absolutely awesome tool. Been using it since 9.04. 
I'd have to agree with ezsit though,
> **ezsit said:**
> ...BTW, I would not bother with increasing the compression at the possible cost of boot time, especially on older computers, since burning to DVD is easy, cheap and USB sticks are cheap and readily available. The size of the CD should not be the determining factor. Anyhow, a DVD reader/writer can be added to an older computer a lot cheaper and easier than making an older computer fast enough to decompress a highly compressed CD for booting purposes. Just a thought.

Insofar, I only have a single core.  Also, I've been a little dismayed with the .iso size limit of ~4GB.  Since DL-DVD-RW and BlueRay-RW are available, not to mention fairly large capacity USB flash drives, it seems kinda strange to limit the size of the resulting DIST .iso...

---

### Post by Fragadelic on 2011-11-04
> **zer010 said:**
> It's awesome that you're working on Remastersys again! An absolutely awesome tool. Been using it since 9.04. 
I'd have to agree with ezsit though,


Insofar, I only have a single core.  Also, I've been a little dismayed with the .iso size limit of ~4GB.  Since DL-DVD-RW and BlueRay-RW are available, not to mention fairly large capacity USB flash drives, it seems kinda strange to limit the size of the resulting DIST .iso...
Thats the beauty of the SQUASHFSOPTS in the config file.  You can decide to use it or not but the option is there for people.

As for the genisoimage issue, it is starting to become somewhat of a broken record issue.  Genisoimage limits the maximum file size for a single file on an iso to be 4GB.  That means the entire filesystem.squashfs must be less than 4GB.  The original mkisofs tool does not have the limitation but it is not available in Ubuntu or Debian.  I have enabled iso level 3 on the iso in the version of remastersys folks are testing right now but haven't heard back from anyone on it.  I remove the message about the 4GB limit.  Hopefully the iso level 3 option allows the iso to be created.

---

### Post by zer010 on 2011-11-05
My apologies for reiterating such a discussed issue, but I was unaware of such things. I do appreciate your feedback though. ^_^d

---

### Post by Fragadelic on 2011-11-05
> **zer010 said:**
> My apologies for reiterating such a discussed issue, but I was unaware of such things. I do appreciate your feedback though. ^_^d
Its no trouble at all.  I end up having to post something about it quite a bit.  I hope that genisoimage using level 3 gets by the limitation but no feedback yet so far and I haven't had a chance to try it out myself either.

Don't worry, I'll be the first to make sure the word is spread if it works as that is basically the only hurdle left.

Folks also think that just because you can get 8gb or larger usb keys for cheap that they will work with larger files but the truth is that fat32 has a file size limit of 4GB as well so that doesn't help anyway.

---

### Post by cbowman57 on 2011-11-05
Ok guys, making an appeal for feedback from anyone that has tried this on 12.04, just so I can rule that out as part of my problem.

@Fragadelic, I used the skel option earlier, are there any basic things it changed on my system other than copying files to /etc/skel ?  Maybe I can revert whatever that option did & have another go at it.

---

### Post by Fragadelic on 2011-11-05
> **cbowman57 said:**
> Ok guys, making an appeal for feedback from anyone that has tried this on 12.04, just so I can rule that out as part of my problem.

@Fragadelic, I used the skel option earlier, are there any basic things it changed on my system other than copying files to /etc/skel ?  Maybe I can revert whatever that option did & have another go at it.
All the skel copy does is to copy the normal config files from that users home folder to /etc/skel and then it goes through the files in /etc/skel and removes ones that are user specific.

If you want, you can see the remove commands from the gui and issue them to restore /etc/skel to its original form.

grep "rm -rf /etc/skel" /usr/bin/remastersys-gui

This will print out all the rm commands I use prior to copying those settings over.  You can then copy those from the terminal and paste them back to execute them but you will need to be root.

FYI though, if the copy to skel is bad, it will not even properly boot the live since it won't be able to create the live user.  This is wat happens if you blindly copy all of your settings into /etc/skel and don't change or remove references to username it was copied from which include the original home folder name.

---

### Post by cbowman57 on 2011-11-05
Makes me think there must be something about 12.04, at least the way mine was installed, that is preventing success.

On 11.10, built the same way, it seems to work rather well already.

Have you had any other reports yet of it working on 12.04?

---

### Post by Fragadelic on 2011-11-05
> **cbowman57 said:**
> Makes me think there must be something about 12.04, at least the way mine was installed, that is preventing success.

On 11.10, built the same way, it seems to work rather well already.

Have you had any other reports yet of it working on 12.04?

No but lkjoel and I were chatting yesterday while he was trying to install it and he was having some issues as well.  I think its too early on and they still have a lot to do with it.  If I get a chance I'll download it and try it out myself as I can do a lot of troubleshooting while its in live mode.

Give me a link to the one you downloaded and I'll start from the same place you did.  I have your package list so I can duplicate your setup.

---

### Post by cbowman57 on 2011-11-05
Ok, I installed the core with 11.10 mini [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/mini.iso)

Edited the sources.list to precise and added the shell.

```
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted

deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
```

---

### Post by Fragadelic on 2011-11-05
> **cbowman57 said:**
> Ok, I installed the core with 11.10 mini [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/mini.iso)

Edited the sources.list to precise and added the shell.

```
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted

deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
```
That may be your problem.  It is not a pure 12.04 install and there wasn't an upgrade path made yet.  I thought you installed one of the 12.04 daily builds and worked from there.

---

### Post by cbowman57 on 2011-11-05
> **Fragadelic said:**
> That may be your problem.  It is not a pure 12.04 install and there wasn't an upgrade path made yet.  I thought you installed one of the 12.04 daily builds and worked from there.


LOL!! No, I thought I'd mentioned that in post 1 or 2. :)

I like to install from the minimal.iso, that's why I was curious to find out if it had worked for anyone using  a precse-daily yet, that would have pretty well confirmed that it was due to this being built from the mini.

Don't worry about it though, and whatever is preventing it from working now will probably be fixed by the time there is a 12.04 mini.iso

---

### Post by inobe on 2011-11-05
> **Fragadelic said:**
> Have you tried remastersys?

It takes your install and makes a live iso out of it that isn't tied to your hardware.  If your system dies, you just use the dvd iso to put it back like a normal Ubuntu live cd except that it has all your personalized stuff including whatever apps you installed.

This, I believe, is better than anything else since you can run your backed up iso just like your install and if you have it on a usb key with persistence you will even be able to save your settings.

It accomplishes what you mention but in an easy and complete way.  The only issue is the limit imposed by genisomage of 4GB per file on an iso.  genisoimage does have an iso level 3 setting which is what I set as default for this version which may be able to ignore that limit so it can build a larger backup.

Colin Watson and I spoke quite a while back about the ability to have multiple squashfs files and it does work but install will not due to the fact that only the first squashfs file gets remounted to /rofs and/rofs is the source for the install.  I have to sign up to the mailing list again and continue the discussion with him.  I have all the code in the new remastersys to handle this but it is commented out right now.  If in the future Colin can get it to use more than 1 squashfs file in /rofs then I will enable it and it will allow for much larger backups.  I tried changing casper to link all of the squashfs files under /rofs but it wouldn't work.  If I manually did it while in live it worked but for some strange reason it wouldn't during bootup.  The live uses dash and busybox and I used the commands on them fine but it just wouldn't work during boot.

i stand by what was stated, it is sufficient to accomplish a backup.

the limitation can be fixed if the actual backup was separate from the app that restored it.

if i'm not talking out of my head, wouldn't that make sense?

---

### Post by cbowman57 on 2011-11-06
Well, I just dicovered this thread [http://ubuntuforums.org/showthread.php?t=1874553](http://ubuntuforums.org/showthread.php?t=1874553)

Apparently there is a bug in ubiquity for 12.04, which is probably what was afflicting my testing. :)

---

### Post by vagrale13 on 2011-11-07
I test remastersys with the follwing versions:

1) Ubuntu 11.04 (with 3 users)
2) Ubuntu 11.10 (with gnome-shell) tested with change background grub image
3) Ubuntu 11.10
4) Ubuntu 11.10 (with Mate desktop)
5) Ubuntu 12.04

all systems *32bit*

the results:
1) Works fine without problem
2) Works fine without problem
3) Works fine without problem
4) After login i had problem, and i had just a blank desktop.
but i' m not sure that the problem is in remastersys
5) Works fine without problem

All finished iso tested on virtualbox.

---

### Post by Fragadelic on 2011-11-07
> **vagrale13 said:**
> I test remastersys with the follwing versions:

1) Ubuntu 11.04 (with 3 users)
2) Ubuntu 11.10 (with gnome-shell) tested with change background grub image
3) Ubuntu 11.10
4) Ubuntu 11.10 (with Mate desktop)
5) Ubuntu 12.04

all systems *32bit*

the results:
1) Works fine without problem
2) Works fine without problem
3) Works fine without problem
4) After login i had problem, and i had just a blank desktop.
but i' m not sure that the problem is in remastersys
5) Works fine without problem

All finished iso tested on virtualbox.

With mate desktop, can you tell me what config folders it uses in your home folder?  I have a feeling it uses .mate or something like that.  If it does, please let me know or post the output of "ls -a" from your home folder.  I only include the regular gnome, kde and .config folders for the skel copy and will need to add any other folders mate desktop uses.

---

### Post by Fragadelic on 2011-11-07
> **cbowman57 said:**
> Well, I just dicovered this thread [http://ubuntuforums.org/showthread.php?t=1874553](http://ubuntuforums.org/showthread.php?t=1874553)

Apparently there is a bug in ubiquity for 12.04, which is probably what was afflicting my testing. :)

That makes perfect sense.

---

### Post by Fragadelic on 2011-11-07
> **inobe said:**
> i stand by what was stated, it is sufficient to accomplish a backup.

the limitation can be fixed if the actual backup was separate from the app that restored it.

if i'm not talking out of my head, wouldn't that make sense?

I've been thinking about adding an additional step for large backups that would tar up the home folder huge files onto a separate area that can be restored after install.  Not sure that this will make it in 3.0.0 but may make it for 3.0.1.  This would get by the 4GB limit as it would chunk the tarred backup into 1GB hunks that could be put anywhere.

---

### Post by Fragadelic on 2011-11-07
If anyone uses any other window managers that use a different config folder in the $HOME directory, please let me know which folders they use and I'll add them to the skel copy portion of the gui.

---

### Post by vagrale13 on 2011-11-07
> **Fragadelic said:**
> With mate desktop, can you tell me what config folders it uses in your home folder?  I have a feeling it uses .mate or something like that.  If it does, please let me know or post the output of "ls -a" from your home folder.  I only include the regular gnome, kde and .config folders for the skel copy and will need to add any other folders mate desktop uses.
Here is the output

```
:~$ ls -a
.                 .gnupg                .ssh
..                .gstreamer-0.10       .sudo_as_admin_successful
.aptitude         .gtk-bookmarks        .systemclean
.bash_history     .gvfs                 .themes
.bash_logout      .ICEauthority         .thumbnails
.bashrc           .icons                .vboxclient-clipboard.pid
.cache            .libreoffice          .vboxclient-display.pid
.caja             .local                .vboxclient-seamless.pid
.config           .mate2                .Xauthority
.dbus             .mateconf             .xsession-errors
debs              .mateconfd            &#914;&#943;&#957;&#964;&#949;&#959;
Desktop           Mate-Extra            &#916;&#951;&#956;&#972;&#963;&#953;&#945;
.dmrc             .mission-control      &#904;&#947;&#947;&#961;&#945;&#966;&#945;
.esd_auth         .mozilla              &#917;&#953;&#954;&#972;&#957;&#949;&#962;
examples.desktop  .onboard              &#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
.fontconfig       .profile              &#923;&#942;&#968;&#949;&#953;&#962;
.gconf            .pulse                &#924;&#959;&#965;&#963;&#953;&#954;&#942;
.gksu.lock        .pulse-cookie         &#928;&#961;&#972;&#964;&#965;&#960;&#945;
.gnome2           sensors-applet-2.2.7
.gnome2_private   .shotwell

```

---

### Post by cbowman57 on 2011-11-07
Ok, after applying this workaround: ```
change  #! /bin/sh to #! /bin/bash in /lib/partman/choose_partition/60partition_tree/do_option
``` that I found in this [post]("http://ubuntuforums.org/showpost.php?p=11433232&postcount=6") I was able to do a dist mode installation built from my 12.04 gnome built from the mini.iso.

That's a relief.

Would be nice to include ~/.themes & ~/.icons for gnome shell installations, and possibly others.

I did find an annoyance caused by installing from the shell though, there is an autorun when mounted option that is active by Gnome default, it causes the spawning of a few nautilus windows when ubiquity scans the partitions in preparation for partitioning.

If I find the correct gsettings command line to disable that before ubiquity begins to run is it possible that you could include it in your installation script?

---

### Post by Fragadelic on 2011-11-07
> **cbowman57 said:**
> Ok, after applying this workaround: ```
change  #! /bin/sh to #! /bin/bash in /lib/partman/choose_partition/60partition_tree/do_option
``` that I found in this [post]("http://ubuntuforums.org/showpost.php?p=11433232&postcount=6") I was able to do a dist mode installation built from my 12.04 gnome built from the mini.iso.

That's a relief.

Would be nice to include ~/.themes & ~/.icons for gnome shell installations, and possibly others.

I did find an annoyance caused by installing from the shell though, there is an autorun when mounted option that is active by Gnome default, it causes the spawning of a few nautilus windows when ubiquity scans the partitions in preparation for partitioning.

If I find the correct gsettings command line to disable that before ubiquity begins to run is it possible that you could include it in your installation script?
Themes and Icons become quite large.  What I might do is make an option to move those into the proper global folders.  Having too much in the /etc/skel directory will result in the live user not being created on systems with less RAM since everything in the live users home folder is held in RAM.

I think the spawning windows issue should go away as I haven't seen that on any versions so far.  If you do find something, let me know and I'll see what I can do.

My general rule is to limit what I do to the actual system so it stays as pristine as possible and reduces the likeliness that remastersys causes any adverse effects.  I have worked really hard to ensure that the really big changes only happen on files I move to my dummysys temp folder prior to remastering so that the real files are left as is.  This makes remastersys safe to use and also lets me assure users that do have things change, that it wasn't changed by remastersys.

---

### Post by Fragadelic on 2011-11-07
I've mostly setup my launchpad account to be able to setup a PPA for remastersys and have had the remastersys project that was created by someone else handed over to me on it.

I will hopefully be releasing 3.0.0 via the launchpad ppa for remastersys.

This will make it much easier for folks to add remastersys to ubuntu and debian since I am too lazy to create and maintain my own signed repository.  My current repository is a quick and dirty unsigned repo and some folks have issues with that.

---

### Post by cbowman57 on 2011-11-07
That all makes sense, thanks for explaining the negative impact.  Something to keep in mind if I get a huge collection of themes & icons under /usr/share.

---

### Post by inameiname on 2011-11-07
After finally testing out Remastersys, beta version 3.0, I am afraid it did not work for me in making a proper ISO in Backup Mode for me for my 11.10 Oneiric machine.

It installed just fine, and seemed to work just fine too (ie, it created a Backup Mode ISO just fine). Unfortunately, when I tried to copy that ISO onto a flash drive via the Startup Disc Creator, just as I always have done, it did not work. More specifically, it ran the process extremely slow, and then would not complete. What normally took a matter of minutes took nearly a half and hour to reach 99%, only to freeze there, and not finish. 

To note, this was an attempt to backup a fresh install of Ubuntu Oneiric 11.10, (well a previous Remastersys 2.0.18 backup of one of my machine that worked just fine before). No special hardware, or software that would conflict with making a Remastersys backup. 

Also, after this one failed to copy the ISO to a flash drive, I downgraded Remastersys back to the working version, and it backed my machine up just as before, as well as copying it successfully to a flash drive. 

Therefore, I do not know what is the cause/difference between why it worked with the latter version, but not the former version of Remastersys.

---

### Post by Fragadelic on 2011-11-08
> **inameiname said:**
> After finally testing out Remastersys, beta version 3.0, I am afraid it did not work for me in making a proper ISO in Backup Mode for me for my 11.10 Oneiric machine.

It installed just fine, and seemed to work just fine too (ie, it created a Backup Mode ISO just fine). Unfortunately, when I tried to copy that ISO onto a flash drive via the Startup Disc Creator, just as I always have done, it did not work. More specifically, it ran the process extremely slow, and then would not complete. What normally took a matter of minutes took nearly a half and hour to reach 99%, only to freeze there, and not finish. 

To note, this was an attempt to backup a fresh install of Ubuntu Oneiric 11.10, (well a previous Remastersys 2.0.18 backup of one of my machine that worked just fine before). No special hardware, or software that would conflict with making a Remastersys backup. 

Also, after this one failed to copy the ISO to a flash drive, I downgraded Remastersys back to the working version, and it backed my machine up just as before, as well as copying it successfully to a flash drive. 

Therefore, I do not know what is the cause/difference between why it worked with the latter version, but not the former version of Remastersys.

Try taking out the -comp xz option from the SQUASHFSOPTS.

---

### Post by inameiname on 2011-11-08
> **Fragadelic said:**
> Try taking out the -comp xz option from the SQUASHFSOPTS.

Thanks for the suggestion, however it wasn't there in the first place. I used the defaults:

```

# Here you can change the mksquashfs options
#SQUASHFSOPTS="-no-recovery -always-use-fragments -comp xz -b 1M -no-duplicates"
SQUASHFSOPTS="-no-recovery -always-use-fragments -b 1M -no-duplicates"

```

---

### Post by foxhead128 on 2011-11-08
Wonderful!

---

### Post by Fragadelic on 2011-11-08
> **inameiname said:**
> Thanks for the suggestion, however it wasn't there in the first place. I used the defaults:

```

# Here you can change the mksquashfs options
#SQUASHFSOPTS="-no-recovery -always-use-fragments -comp xz -b 1M -no-duplicates"
SQUASHFSOPTS="-no-recovery -always-use-fragments -b 1M -no-duplicates"

```

How big was your iso and what size usb key are you using?

Can you post the remastersys.log?

---

### Post by inameiname on 2011-11-08
> **Fragadelic said:**
> How big was your iso and what size usb key are you using?

Can you post the remastersys.log?

The resulting size of the custom.iso made was 1.7GB, which comprises a total filesystem of 5.1GB (approximately 220MB is my total size of my home folder), and I tried to copy that custom.iso onto a 4GB usb key, which has two partitions, a 2GB NTFS one (I use for storage), and a 2GB FAT32 one (the one I use to put the ISO on).

And as to the remastersys.log, I am afraid I do not have that anymore. This was a few days ago, and I have cleaned and restored my whole computer three times since then using a Remastersys 2.0.18 custombackup.iso, both Natty and Oneiric ones. So my apologies for not remembering to keep that file; it was time to do my usual updating and making a new updated-ISO, which is why I just downgraded to the stable Remastersys and went from there.

But now that I have a recent image of my computer via custombackup.iso, I guess I will try to recreate the error when I get a few extra moments and then I will post that log.


UPDATE:

Well.....after re-testing Remastersys 3.0.0 it seems to be working now. Isn't that always how it is...one way or the other? :P 

Using first my custombackup.iso from Natty, made with Remastersys 2.0.18, I restored my computer from scratch, only to immediately back it up after that after changing one thing, installing Remastersys 3.0.0. And it successfully created the ISO AND backed that up onto the flash drive. 

I then did the very same thing using my custombackup.iso from Oneiric, and unlike the last time I tried it, this time it not only created a successful ISO but also it backed up just fine onto the flash drive. Strange. It is the exact same computer as before, with the addition of it all having been backed up in Backup Mode via Remastersys 2.0.18 one more time before since I had tried it with 3.0.0 prior.

So I guess the issue fixed itself. Regardless, I'll post the remasterys.log files for both just because:

---

### Post by cbanakis on 2011-11-08
I just want to say thank you.
The idea of being able to tweak and customize everything till its just right, then easily be able to create your own custom distro with just a few clicks is amazing.

I just stumbled on your software a few days ago, and still have not quite figured it out yet.
Been getting an error about - "The 'grup-pc' package failed to install into /taget/."

No worries though, I'll figure it out.

I look forward to tinkering with your next release.
Glad to know your back on it.

Are you accepting donations?
I'd be glad to help out, but since I'm still pretty new to linux, I cant to much.
But I could spare a little money, if that helps get us all great software.

---

### Post by mrjoeyman on 2011-11-10
I would like to remaster my fedora 15 install, as it is finally PERFECT! :)  I dont want to have to go through all that I did if something happens. Can I use remastersys for Fedora? Thanks.

Joel

---

### Post by Fragadelic on 2011-11-10
> **mrjoeyman said:**
> I would like to remaster my fedora 15 install, as it is finally PERFECT! :)  I dont want to have to go through all that I did if something happens. Can I use remastersys for Fedora? Thanks.

Joel

No.  Remastersys is only for Debian, Ubuntu and the variants that don't change the live boot process.

I had plans to add fedora but I haven't had the time to look into it.

---

### Post by lkjoel on 2011-11-10
Relinux 0.5 or 0.6 will have out-of-the-box Fedora support.

---

### Post by mrjoeyman on 2011-11-10
Well I eagerly await! How soon?

---

### Post by lkjoel on 2011-11-10
For which? The fedora support for relinux will come after 0.4, which will mean in a few weeks (if everything goes well), or in a month.
FYI, Fedora support will come in relinux 0.5.

---

### Post by mrjoeyman on 2011-11-10
Im running Fedora 15. Hope I can get relinux to save my system just as it is when it is ready :)

---

### Post by Archangelos on 2011-11-10
> **Fragadelic said:**
> Due to the number of emails I received I have decided to make time to continue to develop remastersys.

I am planning to include options for distributions to make it easier.  I already have some scripts that I have personally been using for distribution mode remasters and will be including them in the main remastersys package.  As a result I will need dedicated testers for the different variants to help me out in testing.

Please post here, PM me, or email me if you can help out.

 This is actually the coolest linux-anything news I've heard in a long time. Gnome 3--annoying. Unity--meaningless.  But remastersys 3? Now that's interesting. ;-)  In fact that is so interesting, I'd be willing to slap down a 20 YUAN donation for that one.

---

### Post by lkjoel on 2011-11-10
> **Archangelos said:**
> This is actually the coolest linux-anything news I've heard in a long time. Gnome 3--annoying. Unity--meaningless.  But remastersys 3? Now that's interesting. ;-)  In fact that is so interesting, I'd be willing to slap down a 20 YUAN donation for that one.
Unity is Meaningless?? Unity is great! It's just that you've got to get used to it.
It's different, but it's much simpler than any other environment I've seen.

---

### Post by Fragadelic on 2011-11-11
I looked into Fedora livecd-tools to see how they do it and in some ways it is easier but it is less flexible than ubuntu's method.

It requires copying the entire system over to a standard file that is formatted with ext3.  What this means is that you will have to have at least 2 times the free space as your install occupies.

eg. If your fedora install takes up 6GB then you will need to have 12GB free.

6GB for ext3 filesystem file
approx 2GB for the squashfs file
approx 2GB+ for the iso

---

### Post by cwklinuxguy on 2011-11-11
[Fragadelic]("http://ubuntuforums.org/member.php?u=386921")

Nice to hear you're continuing development of Remastersys! It so happens I am trying to make an Ubuntu variant as we speak, info on the project is [here]("http://paradiseos.wordpress.com")

I've noticed on your website that the only difference between Dist and Backup (essentially) is that Backup includes the data of the home folder. I have installed Mate Desktop Environment (the fork of Gnome 2) in Ubuntu 11.10, and it has been compiled in my home folder. As far as I know, that is where is supposed to be. That's kind of weird, but that is where it is and the instructions on the Mate wiki don't tell me to but it anywhere else. So my question is, can the Dist mode be FORCED to include a particular subdirectory of ~? I don't want it to be a full backup, but I do want Mate DE included. Any ideas as to how I can accomplish this? Thanks.

---

### Post by lkjoel on 2011-11-11
> **cwklinuxguy said:**
> [Fragadelic]("http://ubuntuforums.org/member.php?u=386921")

Nice to hear you're continuing development of Remastersys! It so happens I am trying to make an Ubuntu variant as we speak, info on the project is [here]("http://paradiseos.wordpress.com")

I've noticed on your website that the only difference between Dist and Backup (essentially) is that Backup includes the data of the home folder. I have installed Mate Desktop Environment (the fork of Gnome 2) in Ubuntu 11.10, and it has been compiled in my home folder. As far as I know, that is where is supposed to be. That's kind of weird, but that is where it is and the instructions on the Mate wiki don't tell me to but it anywhere else. So my question is, can the Dist mode be FORCED to include a particular subdirectory of ~? I don't want it to be a full backup, but I do want Mate DE included. Any ideas as to how I can accomplish this? Thanks.
No, you are not forced to have it in the home directory.
Follow this guide: [http://ubuntuforums.org/showthread.php?p=11333073](http://ubuntuforums.org/showthread.php?p=11333073)
Once all of the debs are installed, simply run remastersys or relinux and it should work.

---

### Post by Fragadelic on 2011-11-11
> **cwklinuxguy said:**
> [Fragadelic]("http://ubuntuforums.org/member.php?u=386921")

Nice to hear you're continuing development of Remastersys! It so happens I am trying to make an Ubuntu variant as we speak, info on the project is [here]("http://paradiseos.wordpress.com")

I've noticed on your website that the only difference between Dist and Backup (essentially) is that Backup includes the data of the home folder. I have installed Mate Desktop Environment (the fork of Gnome 2) in Ubuntu 11.10, and it has been compiled in my home folder. As far as I know, that is where is supposed to be. That's kind of weird, but that is where it is and the instructions on the Mate wiki don't tell me to but it anywhere else. So my question is, can the Dist mode be FORCED to include a particular subdirectory of ~? I don't want it to be a full backup, but I do want Mate DE included. Any ideas as to how I can accomplish this? Thanks.

You will need to install it globally or nobody else will be able to use it.

Anything in the /home/user folders is only for that user.  No other users will be able to access it.

When you did make install it should have installed it in /usr or /usr/local and the subdirectories under that.

---

### Post by mrjoeyman on 2011-11-11
> **lkjoel said:**
> Unity is Meaningless?? Unity is great! It's just that you've got to get used to it.
It's different, but it's much simpler than any other environment I've seen.

I personally didn't get much out of Unity but Gnome3's Fedora Desktop is very intuitive once you get the hang of it. It probably would be the same with Unity if I had given it more time, so you are probably spot on.

---

### Post by mrjoeyman on 2011-11-11
> **Fragadelic said:**
> I looked into Fedora livecd-tools to see how they do it and in some ways it is easier but it is less flexible than ubuntu's method.

It requires copying the entire system over to a standard file that is formatted with ext3.  What this means is that you will have to have at least 2 times the free space as your install occupies.

eg. If your fedora install takes up 6GB then you will need to have 12GB free.

6GB for ext3 filesystem file
approx 2GB for the squashfs file
approx 2GB+ for the iso

Wow quite a difference there!

---

### Post by Thad E Ginathom on 2011-11-12
Only just now stumbled on the good news: Delighted to know that Remastersys is alive and growing again.

---

### Post by cwklinuxguy on 2011-11-12
> **Fragadelic said:**
> 
When you did make install it should have installed it in /usr or /usr/local and the subdirectories under that.

Oh, okay. I am new to this sort of thing (I'm no developer by ANY stretch of the imagination), so I was not aware of that. I'll take a look-see and check. I ran the "sudo make install" command on all of them, so I assume it should be fine then.

---

### Post by Fragadelic on 2011-11-15
> **cwklinuxguy said:**
> Oh, okay. I am new to this sort of thing (I'm no developer by ANY stretch of the imagination), so I was not aware of that. I'll take a look-see and check. I ran the "sudo make install" command on all of them, so I assume it should be fine then.

It should be.  If you want to check where the binary is, issue "which appname"  where appname is one of the binaries and you should see where it is.  If it is under /usr somewhere then you are fine.

---

### Post by mrjoeyman on 2011-11-20
Just wanted to drop a line and say thanks for the program! I got the new Linux Mint "Lisa" with Gnome3 to a point of my satisfaction (Great Distribution!) and downloaded Remastersys to back it up to a live CD. It took all of ten minutes for me to get the result! I tried it out and all was perfect. Thanks again!

:popcorn:

---

### Post by Fragadelic on 2011-11-21
You're welcome.

I am just about to receive the final 3.0.0 version as the nice gui is ready.  Just some final tweaks and it will be ready to release.

---

### Post by philinux on 2011-11-21
> **Fragadelic said:**
> You're welcome.

I am just about to receive the final 3.0.0 version as the nice gui is ready.  Just some final tweaks and it will be ready to release.

Excellent, well done. :KS

---

### Post by cbowman57 on 2011-11-21
Great news, thanks for breathing life back into this project.

---

### Post by inashdeen on 2011-11-22
hi, i am having a major porb. very bad one. i am building a custom Ubuntu 11.10, to share it with friends. i didnt tweak outside.i just changed the plymouth (manually before i installed remastersys), and grub theme (using the tool you created in remastersys3. eveything woks fine, except... it didnt leave the plymouth on the live cd.it boot, i choose boot live cd, it goes into plymouth, and stuck there. sometimes it gives stdin error.  i thought it is a problem with lightdm, so i changed to gdm, but the problem persist. help

---

### Post by Fragadelic on 2011-11-22
> **inashdeen said:**
> hi, i am having a major porb. very bad one. i am building a custom Ubuntu 11.10, to share it with friends. i didnt tweak outside.i just changed the plymouth (manually before i installed remastersys), and grub theme (using the tool you created in remastersys3. eveything woks fine, except... it didnt leave the plymouth on the live cd.it boot, i choose boot live cd, it goes into plymouth, and stuck there. sometimes it gives stdin error.  i thought it is a problem with lightdm, so i changed to gdm, but the problem persist. help

Check your plymouth theme.

---

### Post by inashdeen on 2011-11-22
what to check ???

---

### Post by BC59 on 2011-11-22
@Fragadelic

After the new thread you started, I used Remastesys for the first time to test it.

1. I used Remastersys on Ubuntu 11.10 fresh install and after some apps installed and removed but more interestingly, with AMD Radeon proprietary drivers activated. I used the first option, to backup everything and Voila! Now I have my personal 11.10 working like a charm. I used it to another computer with a different video card and it gave me the time to uninstall AMD and install NVIDIA drivers without crash.

2. Then installed Wine with MSOffice 2010 and my Dropbox folder.
Trying to backup everything, Remastersys gave up, because of the huge .iso file created.

So now the catch is to create an option of what exactly to include to the backup. Something to give you the option to select between different folders on Home.

---

### Post by ezsit on 2011-11-22
> So now the catch is to create an option of what exactly to include to the backup. Something to give you the option to select between different folders on Home.

Why not create a folder and call it "Not_Saved", then put everything you do not want saved into this folder. When you run Remastersys, use the exclude folders option to exclude your "Not_Saved" folder. This should quite easily accomplish what you want.

Then again, if you install Office 2010 in Wine, your .wine folder is probably over 500MB in and of itself. Why do you need that in the backup? Just reinstall Office when you reinstall the backup.

---

### Post by Fragadelic on 2011-11-23
Got the remastersys-gtk.py gui from Krasimir Stefanov.  Modified it a bit and branched out the skelcopy to a bash script so further updates don't disrupt the translations.  Package has been sent back to him to finalise the translations files and then I will be providing the package to you all for a short period of time and then it will be up on launchpad with instructions to follow.

Thanks very much to Krasimir for his very nice gui.

This is going to be the default gui for remastersys moving forward and we will be providing a single package "remastersys" that includes remastersys-gtk.

---

### Post by Fragadelic on 2011-11-26
OK - Krasimir is done with the gui and I have finished updating remastersys as well.  Between the 2 of us we came up with a gui better than the original and also better than the old remastersys-gtk.  No more xterm for the gui.  I suggested to Krasimir that I would like to see vte embedded and he implemented it.  I made a small tweak to the call and I think we are ready.  Sent the package back to him for testing and if he is ok with it I will put it up on launchpad for you all to try.

I'm really proud of this release.  Lots of updates, improvements, and tweaks.

Thanks to Krasimir Stefanov for the gui and a code suggestion for vesamenu.c32.

Thanks to Joel Leclerc - lkjoel here on the forum for finally explaining his suggestion about getting rid of the install icon from the system.

Thanks to Tony Lovasco for helping point me in the right direction for the rescue boot problem on a remastersys created installed system.

Thanks also to everyone here that tested it out and gave me feedback.

It should be released in the next day or so.

---

### Post by Fragadelic on 2011-11-27
I have put up what will become the final 3.0.0 version of remastersys for Ubuntu Lucid and newer.

[http://www.remastersys.com/repository/ubuntu-testing/](http://www.remastersys.com/repository/ubuntu-testing/)

If you previously tested the other one, please download and try this one which has a date stamp of today November 27th.

This includes the new Gui written in pygtk by Krasimir Stefanov and slightly modified by me.

I removed a lot of the messages that showed some sort of error when it wasn't critical.  I also have it remove the frontend after remastering and after install so it doesn't show up in the users menu anymore.

I will post a full changelog once it is released or you can check the changelog in the package.

Please post feedback in this thread.

---

### Post by dhayfule on 2011-11-30
Its a sigh of relief that its back....

I was shocked today when one of my colleague told me that the project is stopped. Glad to see it back.

BTW it would be great if there are options for customizing splash images and default icons.

---

### Post by Fragadelic on 2011-11-30
> **dhayfule said:**
> Its a sigh of relief that its back....

I was shocked today when one of my colleague told me that the project is stopped. Glad to see it back.

BTW it would be great if there are options for customizing splash images and default icons.

I've included a tool to set the splash image of the live menu as well as for grub.  I've also included a tool to copy your user settings so they are the default which means I think what you are asking is already included in the new 3.0.0 version.

---

### Post by EngineersGarage on 2011-12-01
can i use the 3.0 on ubuntu10.10?

---

### Post by Basher101 on 2011-12-01
I tried some backup software, but none ever worked as great as remastersys. Great regards for creating such a significant piece of backup-software. The only thing i would really love to see is to be able to back up more than ~ 20 GB, in other words exceeding the 4 GB limitation so i could make a >4GB iso that i install on my external USB HDD. I dunno if it is possible, but this would be really awesome. Also if not possible, i keep all my user files somewhere else and keep Ubuntu itself quite small (around 10GB).

thanks again for this! There is no other backup out there that is BOOTABLE.

---

### Post by EngineersGarage on 2011-12-01
I would love to make use of this programe if I knew that it works with my OS, ubuntu 10.10.

---

### Post by lkjoel on 2011-12-02
@Basher101, I think he'll implement this feature later. He doesn't have a timeline, so I'm not sure when. This will be included in relinux 0.4 though.

@EngineersGarage, It should work. I've used remastersys before on 10.10, and it worked flawlessly.

---

### Post by Fragadelic on 2011-12-02
> **Basher101 said:**
> I tried some backup software, but none ever worked as great as remastersys. Great regards for creating such a significant piece of backup-software. The only thing i would really love to see is to be able to back up more than ~ 20 GB, in other words exceeding the 4 GB limitation so i could make a >4GB iso that i install on my external USB HDD. I dunno if it is possible, but this would be really awesome. Also if not possible, i keep all my user files somewhere else and keep Ubuntu itself quite small (around 10GB).

thanks again for this! There is no other backup out there that is BOOTABLE.
I can make an iso larger than 4GB and it will boot but the problem is that it won't be installable due to ubiquity and how it does the install.

The 4GB limitation is due to the fork of original cdrecord tool.  The old spec was limited by the iso9660 spec of having a maximum single file size of 4GB on the iso.  The newer spec surpasses this but unfortunately the genisoimage tool that replaced cdrecord is unable to do this.

With that said, I will try to talk to Colin Ward and the others devs of the live and ubiquity to see if anything can be done.  I had to patch casper in order to get the multiple squashfs files to boot properly but ubiquity still only looks in one place for files to install and I was unable to get all of them to appear in the same directory.

It is true that I don't have any timelines.  I just try to make it work with what we have and I am trying to stay away from having to patch casper or ubiquity as that adds another layer of possible failure for those tools.  I think they work great for Ubuntu and making distributions but they are limiting when trying to do a backup.

I also have another plan in the works to get by this limitation using a 2 step process that I already have the basics of figured out but once I release 3.0.0 for ubuntu I have to work on updating the debian version of remastersys as well before I can get to this.

One way or another I will break the 4GB barrier that we are limited by right now.

---

### Post by duffydack on 2011-12-03
Any idea how I can fix the time/date issue with a custom made ubuntu 11.10?  The clock just says "Time" and I can't get it to say anything else, even setting it manually.  Tried your version 3 beta but that doesn't boot.

Thanks.

---

### Post by trogbot on 2011-12-03
Glad to hear Remastersys is back in dev.  Used it quite often to perform backup of my Ubuntu 10.10 system, until about 3 days ago.  I had installed Samba SWAT (Web Interface) & ***_xinitd_***; after which I wanted to backup my sys.  Remastersys ran, but produced #,s of directoryies in Remastersys directory, but without any iso.:confused:  By chance; by me going to ***_xinitd_*** have adverse effects on Remastersys?  If so, would making Remastersys work with ***_xinetd_ *** be possible?  Any info/help would be greatly appreciated.

---

### Post by Basher101 on 2011-12-03
> **Fragadelic said:**
> I can make an iso larger than 4GB and it will boot but the problem is that it won't be installable due to ubiquity and how it does the install.

The 4GB limitation is due to the fork of original cdrecord tool.  The old spec was limited by the iso9660 spec of having a maximum single file size of 4GB on the iso.  The newer spec surpasses this but unfortunately the genisoimage tool that replaced cdrecord is unable to do this.

With that said, I will try to talk to Colin Ward and the others devs of the live and ubiquity to see if anything can be done.  I had to patch casper in order to get the multiple squashfs files to boot properly but ubiquity still only looks in one place for files to install and I was unable to get all of them to appear in the same directory.

It is true that I don't have any timelines.  I just try to make it work with what we have and I am trying to stay away from having to patch casper or ubiquity as that adds another layer of possible failure for those tools.  I think they work great for Ubuntu and making distributions but they are limiting when trying to do a backup.

I also have another plan in the works to get by this limitation using a 2 step process that I already have the basics of figured out but once I release 3.0.0 for ubuntu I have to work on updating the debian version of remastersys as well before I can get to this.

One way or another I will break the 4GB barrier that we are limited by right now.

I would help you right away!...that is if i actually had any knowledge..i haven't come far but installing, changing themes and icons and pretty much everything a normal user does...too bad i won't have the time to learn it since school sits in my neck :/ but keep it going! I am really looking forward to it!

Kudos

---

### Post by aimwin on 2011-12-03
Please also update your
[http://sourceforge.net/projects/remastersys/](http://sourceforge.net/projects/remastersys/)

I am very sad to read that today.

And I am very happy to see you pop up in Ubuntuforums saying you will be back?

Please keep up your great work, Fragadelic .

Canonical and Mark Sh. should have sponsor you and make remastersys as one key program in the system tool menu,
the same as usb-creator.

Please keep up your great work.

---

### Post by duffydack on 2011-12-04
Wait, What?  You have stopped again already?  That's sad to hear, this is a bloody great app.  Canonical need to look at this and think what I am thinking... Ms has sysprep, ubuntu should have this.

---

### Post by Basher101 on 2011-12-04
> **duffydack said:**
> Wait, What?  You have stopped again already?  That's sad to hear, this is a bloody great app.  Canonical need to look at this and think what I am thinking... Ms has sysprep, ubuntu should have this.

Microsofts backup tools are okay, but they are not a STANDALONE and BOOTABLE image. 

Remastersys > Windows backup&restore

---

### Post by lkjoel on 2011-12-04
> **aimwin said:**
> Please also update your
[http://sourceforge.net/projects/remastersys/](http://sourceforge.net/projects/remastersys/)

I am very sad to read that today.

And I am very happy to see you pop up in Ubuntuforums saying you will be back?

Please keep up your great work, Fragadelic .

Canonical and Mark Sh. should have sponsor you and make remastersys as one key program in the system tool menu,
the same as usb-creator.

Please keep up your great work.
No, I think that it's just because he forgot to update it. He told me a week ago that he would continue developing it as much as possible, so I really doubt that he's stopping it.
Anyhow, just take a look at [http://www.remastersys.com/]("http://www.remastersys.com/").

---

### Post by C.S.Cameron on 2011-12-05
Thanks Tony:
Your Remastersys is a great tool.

---

### Post by 1roxtar on 2011-12-05
Remastersys is an invaluable tool for me.  I am a computer tech and I install Ubuntu on a lot of customer computers.  Seeing it in active development again is great news.  I can now, once again, create a custom LiveDVD that is tweaked like I want it and has all the needed codecs.  Now whenever I do a fresh install, all I have to do is a quick update and Voila! I have a machine with everything working out-of-the-box.  Thank you and keep up the great work.

:guitar:

---

### Post by Fragadelic on 2011-12-11
For those having issues with Ubuntu 11.10 not logging into the live desktop automatically.  This is due to lightdm not being setup on the system properly.

Ok I found this on my 11.10 remaster.  Lightdm is trying to run /usr/share/xsessions/ubuntu.desktop which isn't there.

I am running xfce on this remaster so I did the following that fixed the auto login issue.

sudo /usr/lib/lightdm/lightdm-set-defaults -s xfce

which created the /etc/lightdm/lightdm.conf file with the following information:

```
[SeatDefaults]
user-session=xfce
```

After this remastering produced a live system that logged automatically into my xfce session.

---

### Post by Fragadelic on 2011-12-12
I have uploaded a new version that should work better with 11.10 and 12.04 while still being compatible with 10.04.

For those having issues with lightdm and not logging in automatically, please see my previous post for what you need to do on your system.

There are other small fixes to exclude more things and fixed up some wording, etc.

If nothing comes up from this, this will end up being the final Remastersys 3.0.0-1 that I release as stable.

Please test it and report back.

[http://www.geekconnection.org/remastersys/repository/ubuntu-testing/](http://www.geekconnection.org/remastersys/repository/ubuntu-testing/)

---

### Post by Fragadelic on 2011-12-12
> **duffydack said:**
> Wait, What?  You have stopped again already?  That's sad to hear, this is a bloody great app.  Canonical need to look at this and think what I am thinking... Ms has sysprep, ubuntu should have this.

I forgot to update sourceforge.  I am just about to release my best version ever 3.0.0-1 that supports 10.04 and up.

---

### Post by BrokenKingpin on 2011-12-15
I look forward to the new version. Will you have documentation that will go along with this release? I am interested in creating a Ubuntu or Debian spin, and instructions would be very helpful, especially if there are any manual steps that need to be done.

---

### Post by Fragadelic on 2011-12-15
> **BrokenKingpin said:**
> I look forward to the new version. Will you have documentation that will go along with this release? I am interested in creating a Ubuntu or Debian spin, and instructions would be very helpful, especially if there are any manual steps that need to be done.

I've added most things that folks would need to do on the gui so you shouldn't have to do much manually anymore.

Things like settings the grub background, setting the background for the live menu, creating a new plymouth theme, and copying your settings to /etc/skel are now all included in the gui and are a simple click away.

The package that is up there is pretty much the final but I haven't officially released it yet as I'm trying to get my ppa setup for it.

---

### Post by BrokenKingpin on 2011-12-16
> **Fragadelic said:**
> I've added most things that folks would need to do on the gui so you shouldn't have to do much manually anymore.

Things like settings the grub background, setting the background for the live menu, creating a new plymouth theme, and copying your settings to /etc/skel are now all included in the gui and are a simple click away.

The package that is up there is pretty much the final but I haven't officially released it yet as I'm trying to get my ppa setup for it.
That sounds awesome... I look forward to giving it a try.

---

### Post by frodowiz on 2011-12-19
i use this tool to understand these processes and i have introduced 4 people to ubuntu who are still using it as their only os because of this tool.. you have done mighty fine work..

i read how you were surprised how many people use it because all you ever heard  were the complaints.. wasnt it once said "the squeaky wheel gets the grease"?  only a very small percentage of folks complain about anything so i use it as a gauge..

 the more whiners, the more finer the product..

i think ill stick to learning and leave the sayings to those more capable :)

---

### Post by obscur156 on 2012-02-04
Wow,what a great news for me today.
Remastersys living again.
That was something i was really missing.

Thanks Fragadelic for sharing your hard work with all of us.
I appreciate it very much .

Best regards and have a nice day budy. ):P

---

### Post by Fragadelic on 2012-02-04
Thanks.

I have actually already released the second version since continuing.

I am currently working on updating the debian version of remastersys and a new qt gui for remastersys for ubuntu.  Once I finish with it I will split remastersys off into 3 packages.  The base cli package, the gtk frontend, and the qt frontend.  The debian version will end up using these new frontends as well.

---

### Post by vagrale13 on 2012-02-18
How easy is add to *remastersys*, other graphical interface like *Mate, Cinnamon*.

---

### Post by Fragadelic on 2012-02-18
> **vagrale13 said:**
> How easy is add to *remastersys*, other graphical interface like *Mate, Cinnamon*.

I've already added mate but need info on where Cinnamon stores config files and can put that in too.  Will be in the next version 3.0.2 of remastersys.

---

### Post by vagrale13 on 2012-02-19
> **Fragadelic said:**
> I've already added mate but need info on where Cinnamon stores config files and can put that in too.  Will be in the next version 3.0.2 of remastersys.
That would be very nice!:)
See some info

```
:~$ sudo find / -name cinnamon

/usr/share/cinnamon
/usr/share/themes/WoodnTux/cinnamon
/usr/share/themes/Dark-Glass/cinnamon
/usr/share/themes/Minty/cinnamon
/usr/share/themes/Eleganse/cinnamon
/usr/share/themes/ChocoLatte/cinnamon
/usr/share/themes/Trans-Blues/cinnamon
/usr/share/themes/ElementaryOS/cinnamon
/usr/share/themes/New-Elements/cinnamon
/usr/share/doc/cinnamon
/usr/share/lintian/overrides/cinnamon
/usr/bin/cinnamon
/usr/lib/cinnamon
/home/vagrale13/.local/share/cinnamon
```

---

### Post by Fragadelic on 2012-02-19
If it is .local then it is already included.  You should be all set for both if you use 3.0.1.

---

### Post by vagrale13 on 2012-02-24
I test with newer version *remastersys 3.0.1-1* on *Ubuntu 11.10*
and **Mate** works fine. :)
**Cinnamon** doesn' t work, after login returns to classic Ubuntu.:confused:

---

### Post by Fragadelic on 2012-02-24
You need to make sure cinnamon is set as the default desktop environment on your system.  If you are going into unity then that is the default.

---

### Post by bsad on 2012-03-05
Are there any known issues with Lucid 10.04.4 (Desktop) and Remastersys? I have been able to create an ISO but when I boot the LiveCD there is no install icon on the Gnome desktop or menu.

Any way to invoke the installer via command?

Works fine with older Lucid releases (from 2010). Running the latest version from the PPA 3.0.1-1. Having the same problem with Lubuntu and the 10.04 or 11.10 releases.

---

### Post by Fragadelic on 2012-03-05
I have been using 11.10 for quite some time now with remasters of kde, gnome3, unity, lxde and xfce without issue.  Try installing the ubiquity-frontend-gtk prior to remastering.

---

### Post by nm_geo on 2012-03-09
Fragadelic thanks for your information.

I will be working on building a LiveCD of the Lubuntu 12.04 precise-desktop-i386 using the non-pae kernel as soon as we near the release day or slightly after.

---

### Post by Fragadelic on 2012-03-09
No problem.  Just let me know if you need any other info.

---

### Post by Fragadelic on 2012-03-10
Here is some information for folks that are just installing remastersys for the first time.

In newer versions of ubuntu you will need to install ubiquity-frontend-debconf prior to installing remastersys.

If you don't, it will try to install everything for both the kde and gtk frontends as ubiquity requires either ubiquity-frontend-debconf, ubiquity-frontend-gtk or ubiquity-frontend-kde and if the debconf(cli version) isn't installed first it will install all of them.

The other negative effect is that remastersys will be uninstalled as well when the ubiquity-frontend-gtk or ubiquity-frontend-kde are removed if the debconf frontend isn't installed.

I will be fixing this in the next package which should be released in less than 1 week and it will also have support for 12.04 as I have started to test with it today.

---

### Post by nm_geo on 2012-03-10
> **Fragadelic said:**
> Here is some information for folks that are just installing remastersys for the first time.

In newer versions of ubuntu you will need to install ubiquity-frontend-debconf prior to installing remastersys.

If you don't, it will try to install everything for both the kde and gtk frontends as ubiquity requires either ubiquity-frontend-debconf, ubiquity-frontend-gtk or ubiquity-frontend-kde and if the debconf(cli version) isn't installed first it will install all of them.

The other negative effect is that remastersys will be uninstalled as well when the ubiquity-frontend-gtk or ubiquity-frontend-kde are removed if the debconf frontend isn't installed.

I will be fixing this in the next package which should be released in less than 1 week and it will also have support for 12.04 as I have started to test with it today.

Fragadelic you are the man.. BINGO

I am typing this from a remastersys of Lubuntu precise 12.04 i386 non-pae install. I built the mini.iso of Lubuntu-core and installed it earlier updated to lubunut-desktop and added to many other things :P

Anyway I decided to get the latest remastersys and give it the old college try good news is I have the custom.iso installed and I am using it.

I have way to many versions on this laptop and the grub install just did it to MBR when I wanted to use the partition that I installed to, but I can fix that easily.

Cool... Cool.. cool thanks dude.. 

We will be able to help those non-pae hardware people if they need it..

I did install the LXDE stuff that I will clear out in the next run Here is a screen shot ..

---

### Post by Fragadelic on 2012-03-10
My preferred desktop is XFCE these days and I just remastered Xubuntu 12.04 daily build for my needs with the regular kernel.  It requires installing the regular kernel and then uninstalling the pae kernel.  I'm glad you mentioned this to me about the pae as I hadn't looked at it prior to your PM to me.

I also found another little bug which I mentioned in mt last post on this thread.  I'm going to do some more testing and then get an updated remastersys as I already have some tweaks from 11.10 that I have implemented but not released yet.

---

### Post by nm_geo on 2012-03-10
> **Fragadelic said:**
> My preferred desktop is XFCE these days and I just remastered Xubuntu 12.04 daily build for my needs with the regular kernel.  It requires installing the regular kernel and then uninstalling the pae kernel.  I'm glad you mentioned this to me about the pae as I hadn't looked at it prior to your PM to me.

I also found another little bug which I mentioned in mt last post on this thread.  I'm going to do some more testing and then get an updated remastersys as I already have some tweaks from 11.10 that I have implemented but not released yet.

Well you have done really well.  I am glad you have revived Remastersys it is an excellent resource.. Thanks..

My next thing will be to hack the regular install and change the selected kernel in extract-cd casper??.. and add the non-pae kernel to modules . That way maybe we can get a more normal smaller liveCD for Lubuntu.

---

### Post by Fragadelic on 2012-03-12
Install works fine without any extra changes.  I remastersys Xubuntu 12.04 with only the regular non pae kernel and it installed just fine.

---

### Post by dhayfule on 2012-04-25
> **Fragadelic said:**
> I've included a tool to set the splash image of the live menu as well as for grub.  I've also included a tool to copy your user settings so they are the default which means I think what you are asking is already included in the new 3.0.0 version.
Thats great to see.

Thanks. I just saw the new version last night and going to give it a try.

Regards

---

### Post by dhayfule on 2012-04-25
> **aimwin said:**
> Please also update your
Canonical and Mark Sh. should have sponsor you and make remastersys as one key program in the system tool menu,
the same as usb-creator.


This is not just a suggestion, but a need of time. It's strange why isn't it added on standard repositories of Ubuntu yet? It will be really helpful if one can directly download it from software center without having the need to add custom lines in the source list.

---

### Post by Ariane98 on 2012-05-13
Hi
I have a "total noob" question
I like Xubuntu but there are a few things I added to feel "at home" (vlc, skype...)
I wanted also to have 3 keyboard layouts pre selected and available from the menu bar
Now I want to make a liveCD with these settings. I had heard of mastersys, but when I try
 sudo su
remastersys dist

xubuntu says "command not found"

what is wrong ?

[another noob question : is it possible to make a live usb of xubuntu with the persistance feature ? Which tool would you recommand ?]

Thanx to those who will take some time to help a poor noob... :)

---

### Post by cbowman57 on 2012-05-13
I can answer your second question.

For an Ubuntu stick either Startup Disk Creator or Unetbootin should do it with an option for persistence.

---

### Post by Fragadelic on 2012-05-13
Check my website under the ubuntu section for details on how to install remastersys.  It isn't included in the default Ubuntu repositories.

As for persistence, be very careful as there is a current bug with running persistence and then trying to install it afterwards as you will have issues.  If you simply want to keep it as a persistent usb setup then that is fine but if you plan to install it, do not use persistence.

---

