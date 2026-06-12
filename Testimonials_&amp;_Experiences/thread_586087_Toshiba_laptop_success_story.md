---
title: "Toshiba laptop success story"
date: 2007-10-21
forum: Testimonials &amp; Experiences
---

### Post by lyndaj70 on 2007-10-21
Hello, all,

I have been playing with Linux for years, but on this particular laptop doubted that I would be able to transition gracefully....

However, I really liked Feisty, and decided to give it a try...

Dual-booted with XP for a while...  to test whether I could do everything I needed.  My goal was to have a linux laptop where I could safely go in the field and use in my work of computer repair without having fear of having to wipe/reinstall all the time....  And as this laptop is also used by my 8-year-old to occasionally watch movies and play games in the field when it isn't needed, it HAS to be versatile and easy to use...

I managed to install successfully, ran Automatix2 to get my needed codecs, now plays DVD's for the kid.

Since I have a few Windows apps that I am unable to part with at present, I decided to create a VirtualBox machine of Win2k.  Why 2k?  All that came with this stupid thing was a restore disk, which "won't" work in the virtual machine.  So I took an old copy of Win2k and used it instead.  It does what I want so I'm not concerned about how old it is.. It won't be going online anyway.....

Had to edit the new usbfs file (/etc/udev/rules.d/40-permissions.rule) as root to enable my usb to serial controller, and now I can use it in VirtualBox in my multimeter program until I can locate a linux substitute.  You can find the instructions here [http://ubuntuforums.org/archive/index.php/t-393582.html]("http://ubuntuforums.org/archive/index.php/t-393582.html").

So now I run Quickbooks99 (I know I can use gnucash but I'm happy where I'm at), my WatchTower Library (got WT Reader to work in Wine but it was unstable), and my multimeter program.  They "just work" and so I'm happy..

Plan on creating another VM to use if I end up needing it to hook up contaminated Windows drives to disinfect spyware, but am hoping that clamAV will work for the antivirus scans....  I want to have the virtual machine I use when I need to, and one I can easily restore after hooking up anything to it to protect myself from the nasties out there....

I was unable to get the on-board modem to work but wireless worked out of the box.   Sound required me to let Ubuntu download the updates and restart the system...  On-board ethernet works fine.. usb mouse works fine... was unsuccessful in getting one usb keyboard to work, it came off a Dell so maybe that's why (old proprietary hardware).  I have another one to try but it's hooked up to my desktop and I don't feel like fighting the dust bunnies right now (grin)...

With the USB-to-serial controller (purchased at Radio Shack) my external serial modem works like a charm.

Video is fine but can't enable the special effects.  Don't want them slowing me down, anyway....

Tried installing 7.10 but had video problems, as well as a bug about allocating resources, so I put 7.04 back.  It worked once it booted, but booting took forever, the username/pasword were HUGE in that little box you typed it, and the video had to reset itself to normal size from garguantuan every time you rebooted.  I'll wait a while and perhaps test it on VirtualBox until some more updates are available.  I have 7.10 with scads of Debian Jr. games and stuff installed in a virtual machine on my Vista pc.  Once I get the kinks worked out of the lappie plan to start on it, with the eventual goal of installing Ubuntu as primary OS, and Vista in a virtual machine to use as needed or desired.  The kid likes Purple Place, I'm afraid (sigh).  It's pretty, but a bit resource-hungry IMHO, but then again, Linux spoiled me on that, particularly Damn Small and Puppy.

Decided to use Opera as both main browser and email client, and am uninstalling Evolution.  Just too much program for what I need.  Now all I need is a simple calendar program that will sync with my google calendar, and I'll be set.

For those who are considering Linux, I strongly suggest downloading VirtualBox and trying it in a Virtual Machine first, to get a feel for it.... Play with it, then resize your partitions, or get another hard disk, and try a dual-boot config.  Just a little at a time -- don't do like I did back in the 1990's and wipe everything without trying the merchandise first.  

I installed Suse back when I didn't really have a clue about Linux and learned the hard way about certain cheap hardware some of these OEM's put in their systems, and when I went to wipe/reinstall Windows, my restore disk didn't see my hard disk... After having a heart attack thinking I had trashed my machine I learned how to repartition manually, and got it back up and running, but I learned to go slow and easy on my next try.

Linux is worth the extra work.  I have security, and the freedom of choice.  I'm not tied to license fees and I can try what I want without fear of breaking the bank... If I like it, I can install it on my buddies' computer, again and again and again and no one is going to come knocking to take me away for license infringement.....

I don't have to be as concerned about viruses, I have more tools to work with computers, I don't have to be as concerned about hackers, or my fiancee hacking into my personal files while I'm not looking...

I don't have to ban my daughter from the computer, because despite the fact that my kids have all managed to innocently trash multiple Windows installations, they haven't managed to faze Linux the least little bit.  

And Ubuntu has Debian Jr, available in synaptic, full of games and educational stuff for kids... As well as edubuntu, and scads of other things kids like to use... like gimp and tuxpaint... 

Yeah, I'm lookiing forward to getting the desktop set up.  Figure I'll try my luck at setting up a NFS network.. should add to the security side of things.....

Wish me luck! :)

---

### Post by lyndaj70 on 2007-10-22
:KS[SIZE="4"]***Keyboard Update***[/SIZE]:KS

Well, I couldn't resist the temptation, and so this morning I detached my Microsoft Natural USB keyboard from my desktop and hooked it up to this lappie.

IT JUST WORKED.

In fact, I'm typing on it now.  The system didn't take any longer to boot, and I was able to use this keyboard to even log in.

On Windows, my general expeience has been that you hook it up and then wait, having a standard ps/2 keyboard/mouse already installed and working to use to install the usb versions......

No such issues with Ubuntu.

I want to thank Mark Shuttleworth and the nice folks who work so hard on Linux in general and Ubuntu in particular.  Thanks you you all, I now have a laptop that I can work and play with in safety and security.  

I found a multimeter program, now all I have to do is configure my ports so that it can see my multimeter on the usb to serial converter cable..  And for a modem, I have an external serial using the same converter cable that works like a charm.  In this particular system, the only thing I could not get to work was the modem, everything else works great.....  I can deal with that, though later on I may research linmodems and see what I can come up with.  If I'm successful, I will let everyone know.

Take care!
~Lynda :guitar:

---

