---
title: "LiveCD/DVD/USB Customization Discussion"
date: 2008-11-26
forum: The Cafe
---

### Post by red_team316 on 2008-11-26
This thread is for the discussion of practices of how to customize a LiveCD/DVD , InstallCD/DVD, LiveUSB, yet focused on how to make certain portions of it easier or even feasible for a non-technical user as well as coming up with new ideas on how to improve any process that may be required for the creation. 

There are several customization programs out there to help with this such as reconstructor, UCK, remastersys, revisor, and several others. Many of the items that will be discussed in this thread have been used in said programs. If you possess the knowledge, you can do everything you need manually. Hopefully the knowledge shared here will contribute to better software provided to the end user. Hopefully someday there will be a unified program that is capable of creating/customizing/remastering a linux distro regardless of brand.

Some useful resources for anyone interested:
This list is in no particular order, I may clean it up later...
[LiveCD Customization - Ubuntu Help Page](https://help.ubuntu.com/community/LiveCDCustomization)
[LiveCD Customization From Scratch - Ubuntu Help Page](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
[InstallCD Customization - Ubuntu Help Page](https://help.ubuntu.com/community/InstallCDCustomization)
[LiveCD Creator - Ubuntu Wiki](https://wiki.ubuntu.com/LiveCDCreator)
[Customised Iso Image Tools - Ubuntu Wiki](https://wiki.ubuntu.com/CustomisedIsoImageTools)
[Customize Live Initrd - Ubuntu Wiki](https://wiki.ubuntu.com/CustomizeLiveInitrd)
[DebootstrapChroot - Ubuntu Wiki](https://wiki.ubuntu.com/DebootstrapChroot)
[x86, x86_64, PPC, IA64 mkisofs commands - UCK Launchpad Answers](https://answers.launchpad.net/uck/+question/3069)
[ Apt-Get How To - Ubuntu Help Page](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto)
[How to boot several CD iso files in a DVD - JustLinux Forums](http://www.justlinux.com/forum/showthread.php?t=150078)
[Chroot Guide - Gentoo Wiki](http://www.gentoo.org/proj/en/base/amd64/howtos/index.xml?part=1&chap=2)
[How To Autostart Programs - Gentoo Wiki](http://www.gentoo-wiki.info/HOWTO_Autostart_Programs)
[Isolinux HowTo for newbies](http://members.chello.at/bobby100/ILpart1.htm)
[How To Create a WINE LiveCD - Reconstructor Forums](http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=44&func=view&id=1044&catid=3)

**Nested X11 Environments:**
[Nested X11 environment session - Zebardast Blog](http://zebardast.wordpress.com/2008/04/07/nested-x11-environment-session/)
[How To Xephyr - UbuntuForums Thread](http://ubuntuforums.org/showthread.php?t=620003)

**Chrooting:**
[32-bit Chroot Guide - Gentoo Wiki](http://www.gentoo.org/proj/en/base/x86/chroot.xml)
[32/64-bit Chroot Guide - Gentoo Wiki](http://www.gentoo.org/proj/en/base/amd64/howtos/index.xml?part=1&chap=2)

**LiveCD Customization/Remastering Programs:**
[Reconstructor - Customize Ubuntu Based LiveCD's](http://www.reconstructor.aperantis.com/)
[UCK (Ubuntu Customization Kit)](http://uck.sourceforge.net/)
[Remastersys - a backup utility for Klikit-Linux, Ubuntu and derivatives](http://www.remastersys.klikit-linux.com/)
[Revisor - Customize Fedora](http://revisor.fedoraunity.org/)

**LiveUSB Links:**
[LiveUSB - Creates Ubuntu Based LiveUSB's](http://klik.atekon.de/liveusb/)
[Unetbootin - Creates LiveUSB's](http://unetbootin.sourceforge.net/)
[LUBI - Creates Ubuntu Based LiveUSB's](http://sourceforge.net/projects/lubi/)
[PenDriveLinux - Tons of ways to create LiveUSB's](http://www.pendrivelinux.com/)

---

### Post by ingo on 2008-12-11
Hi red_team,

sorry for not replying earlier but I've been away AND very busy.

I am very interested in your usplash experiences (and no, I do not know C :(). Have you written a how to or anything like that? Mind, my programming experience is very, very limited, i.e. bash scripting :oops:

We were talking about Xnest in the other thread and you mentioned Xephyr - I am afraid I have not yet messed with Xephyr - should I?

fwiw - I have written a couple of how tos on the kubuntu forum ([http://kubuntuforums.net/forums/index.php?topic=3099957.0](http://kubuntuforums.net/forums/index.php?topic=3099957.0) and [http://kubuntuforums.net/forums/index.php?topic=3099749.0](http://kubuntuforums.net/forums/index.php?topic=3099749.0)) and am planning a third one everything one can do in the chroot environment.

On a different note - what would be cool to incorporate into uck/reconstructor would be USB stick creation. If you check the second link above you will notice that I successfully used usb-creator (sure takes the grind out of making the stick yourself!).

Cheers!

---

### Post by red_team316 on 2008-12-12
> **ingo said:**
> Hi red_team,

sorry for not replying earlier but I've been away AND very busy.

I am very interested in your usplash experiences (and no, I do not know C :(). Have you written a how to or anything like that? Mind, my programming experience is very, very limited, i.e. bash scripting :oops:

We were talking about Xnest in the other thread and you mentioned Xephyr - I am afraid I have not yet messed with Xephyr - should I?

fwiw - I have written a couple of how tos on the kubuntu forum ([http://kubuntuforums.net/forums/index.php?topic=3099957.0](http://kubuntuforums.net/forums/index.php?topic=3099957.0) and [http://kubuntuforums.net/forums/index.php?topic=3099749.0](http://kubuntuforums.net/forums/index.php?topic=3099749.0)) and am planning a third one everything one can do in the chroot environment.

On a different note - what would be cool to incorporate into uck/reconstructor would be USB stick creation. If you check the second link above you will notice that I successfully used usb-creator (sure takes the grind out of making the stick yourself!).

Cheers!

I've given help here and there on several forums about usplash but have yet to make a how-to/tutorial. I have been planning on one for quite some time as all the other how-to's on the subject I have found are fairly simple and I don't really think they do justice. I have been working on stuff for a usplash-creator for ages with TheeMahn from UE. [TUM 1.04](http://forumubuntusoftware.info/viewtopic.php?f=23&t=1767) does a decent job of creating standard usplashes, but won't handle anything thats complex-code like my parallax usplash. I've been following the "Replace usplash with splashy" thread for awhile and now everybody is getting excited about KVM and Plymouth, so more people are getting interested in the bootsplash process :) Anyway, my how-to will be pretty detailed, but if someone doesn't know programming, then that shouldn't stop them. If they do know how to program, then they would definitely get the meat and potatoes of how to really customize one. I guess I'll try to whip up something over the holiday season.


Xephyr to me is like Xnest on steroids. Not sure about how your experience will be, but try using Xnest, and then try using Xephyr. Xephyr seems to run much smoother, faster, and has more options. The only thing I'm kind of bummed about is that it doesn't look like there is an option to name the Window as there is in Xnest. Definitely not a reason to use Xnest instead as the window title really has nothing to do with a nested X anyway, but I would like to see it added someday(or someone tell me "hey, you can do it, you're just not doing it the right way/etc...").
Take a look at this, it's one of the links in the first post that relates to Xephyr. [http://zebardast.wordpress.com/2008/04/07/nested-x11-environment-session/](http://zebardast.wordpress.com/2008/04/07/nested-x11-environment-session/)

I'm definitely interested in chroot capabilities. I'll look forward to your how-to :) There are so many things you can do and it's a pretty steep learning curve but way worth it once you've done it for awhile.

It appears your how-to(hard way) is missing the md5sum calculation. I think thats pretty important. If you don't, you'll end up with a LiveCD that fails the integrity check even if your LiveCD works fine. This is also a bug in reconstructor I fixed recently because it finally bugged me enough to finally squash it. I finally figured it out by analyzing the md5sum.txt's of several ubuntu releases and by looking at Petr Pudlak's script on the LiveCDCustomization page. 
Python Code:
```

# exclude isolinux directory or else when checking disc integrity it will say there are errors
                os.popen('(cd \"' + os.path.join(self.customDir, "remaster/") + '\"; ' + 'find . -type f -not -name md5sum.txt -not -path \'*/isolinux/*\' -print0 | xargs -0 md5sum > md5sum.txt)')

```
Which translates to this as the terminal command:
```

cd yourremasterdirectory; find . -type f -not -name md5sum.txt -not -path '*/isolinux/*' -print0 | xargs -0 md5sum > md5sum.txt

```

Yea, I've looked into USB creation, but usb-creator as well as Unetbootin don't quite satisfy me. Ubuntu's usb-creator is still in it's infancy and I haven't had any luck with it yet, although I've read a few of the releases have bugs in them so that may have affected me. I'm sure it will get better with time. usb-creator as well as Unetbootin are practically useless without commandline options to load a custom iso and do all of the creation from the terminal. LiveUSB on the other hand(by Simon Peter) reads /cdrom so all you have to do is mount a custom ISO there first. Although yet again, it could be developed more. I submitted a patch to him some time back because it won't handle DVD sized ISO's but have yet to see him integrate it into his launchpad branch :/ Personally, I think the guy at [www.pendrivelinux.com](www.pendrivelinux.com) has the most straight forward information, how-to's on USB creation. Then again, every way I've stated above makes the USB slightly differently and they all have their strengths and weaknesses. UCK/Reconstructor/etc in my opinion need to step back and use one or more of said programs like a plugin rather than recreating the wheel. Thats probably the main reason why there isn't that functionality yet. 


isolinux customization has been something I've been looking at for a long time. Specifically, so LiveCD could be created with other apps similar to the Ultimate Boot CD and/or Multi-Distro DVD's. As far as the Multi-Distro DVD idea, there is a very good how-to on the justlinux forums by saikee on how to do this with GRUB. [http://www.justlinux.com/forum/showthread.php?t=150078](http://www.justlinux.com/forum/showthread.php?t=150078) .Again in the first post :)


I recognized your avatar from the kubuntu forums but hadn't put 2 and 2 together since the username is different ;) Shakespearean?


Cleaned up the list in first post and added a few links.

---

### Post by ingo on 2008-12-12
Wow, you've done some research on the subject I see - nice links!

Have yet to try your usplash (personally, I like to see what is happening on screen during boot up, so usplash is one of the first things that gets the boot on a new install :)).

You are right with the MD5 sum - thanks for pointing that out. I've never ever had to use it - call me lucky. Ought to look into it.

usb-creator may be brand new but has so far been used successfully by a number of people over at [www.kubuntuforums.net]("http://www.kubuntuforums.net") - agreed that it cannot do fancy things like house multiple isos but the persisent feature is nice. I've tried pendrive linux a number of times and it never worked due to faulty code - am not the only one there :( So far I've been doing it myself using Qqmike's how to over at [www.kubuntuforums.net]("http://www.kubuntuforums.net"). Will study that link you provided!

As for the last "bit in the middle" how to on what to do in chroot - at the mo I cannot see it being more than a list of tips & tricks such as using Xnest/Xephyr, a link to the KDE Admin pages which have some info on theming and ways of saving space and bog standard stuff such as adding repos. I'm sure the list will grow but that is a start. Unfortunately it seems that the [www.kubuntuforums.net](www.kubuntuforums.net) community is not so much into remastering, am pretty much on my own there :(

And finally - yep, the name toad had been taken on this forum, what a bummer! And the avatar is Catweazle (of UK book and TV series fame), a magician from the Dark Ages who actually managed to transport himself to the present time (an accident, of course!). That explains the somewhat confused look on his face. Top that with the fact that we actually look quite similar and there was no way round it :D

---

### Post by Lampi on 2009-03-29
hello friends of Ubuntu!

I think this is the right place to ask about **squashfs** device **labeling**:

If you create a squashfs device using *mksquashfs <sourcetree> /dev/<device name>* you'll get a single device with a squashed filesystem in it. This one can be easily mounted using the **block device** as source reference, but it has neither a UUID nor a LABEL assigend to. Since I use this squash device as my filesystem root on a usb stick, I should *never* use block device names, since they can easily change on bootup detection.

ext2/3 filesystems have e2label, if you've forgotten about disk labeling while you created the fs, what's available for squashfs?? I checked the manpage (man mksquashfs) and tried to google it up but no results so far :(

Thanks for any kind of help on this matter!

---

### Post by DouglasAWh on 2009-06-02
I realize this is Ubuntu Forums, but I was wondering if someone could tell me if there's a UCK (Ubuntu Customization Kit) for Fedora.  Revisor isn't nearly as good as UCK as far as I'm concerned.  The main thing is bandwidth, pulling all those packages.  I guess I could make a local repository, but that's even more work!  I want to be able to very easily incrementally build these things.  We might get a suggestion for one different package from a user.  We think it's a good idea and with revisor we're stuck forever waiting for stuff to build.  With UCK we are done in a minute.

An aside: the reason we are interested in moving from Ubuntu to Fedora is because of Spacewalk.  It will be nice with spacewalk can do .deb, but I don't think we want to wait for that.

Thoughts?

---

