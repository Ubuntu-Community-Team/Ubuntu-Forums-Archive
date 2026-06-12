---
title: "Is it possible to run Mac software on Ubuntu/Linux?"
date: 2007-05-11
forum: The Cafe
---

### Post by bash on 2007-05-11
Now that most of the new programs for Macs come out both for the PPC platform as well as the x86 I was wondering if it was possible to run Mac software in Ubuntu.

Does something similar to VMWare or Virtualbox exist for Mac software? Or even better, since Mac OS X is  by quite a big part also based on the UNIX(-like) system envirement. So maybe is there a kernel module/patch/deamon or whatever with which you can achieve to run Mac software more or less nativly in Ubuntu.

Hope someone will be able to find an answer to this other than just (hopefully not) no.

---

### Post by Compucore on 2007-05-11
From what I have read up on MAC OSX it was based on freebsd if memory serves me coreectly over here. I could be wrong as well. Which is another distro of the linux environment. Not to put the OSX down or anything like that. But I think they structured the OS from BSD to look slightly different. So on th back side I don't know if the software itself that runs under OSX will actually work on linux based or Under specifically ubuntu linux. As far as I know freebsd is just another distro of linux itself.

Compucore

---

### Post by GrueTamer on 2007-05-11
FreeBSD is not linux at all, it is in fact a free version of BSD.  BSD is a fork of Unix, just as Linux is.  While BSD and Linux are similar in ways, such as how they can both run Gnome and KDE and stuff, they are very different under the hood.

---

### Post by Rhox on 2007-05-11
> **GrueTamer said:**
> FreeBSD is not linux at all, it is in fact a free version of BSD.  BSD is a fork of Unix, just as Linux is.  While BSD and Linux are similar in ways, such as how they can both run Gnome and KDE and stuff, they are very different under the hood.

Linux is not a fork of Unix. Linux was a clone of Minix. FreeBSD was a fork of 386BSD but its code doesn't really resemble 386BSD.

---

### Post by diskotek on 2007-05-11
this discussion making to try freeBSD. i'm curious n00bster now

---

### Post by saphil on 2007-05-11
What software are you wanting to run?  
Maybe you can get the source-code and compile it for your Linux box.  
If you have source-code, the sky's the limit!!

---

### Post by akxiii on 2008-04-11
This is what I would like to see a version of for linux:
[http://www.splasm.com/audiobookbuilder/index.html](http://www.splasm.com/audiobookbuilder/index.html)
it is an Audiobook Builder that lets you piece together a bunch of audiobook files in a nice little way for the ipod.
-ak

---

### Post by buried on 2008-04-11
Unless the source code is open, it is not possible at the moment..patience..

---

### Post by chucky chuckaluck on 2008-04-11
osx is based on freebsd, but it's combined with the mach kernel, too. i think that probably means there's no way to use their stuff in linux, or a bsd. i think some of their software was developed, or at least started, in opendarwin (i'm not sure that would be any help to you).

---

### Post by elmer_42 on 2008-04-11
I don't even think it's possible to emulate the Mac like Windows is emulated, because Apple has a bunch of proprietary stuff like Cocoa or whatever it is called.

---

### Post by aeiah on 2008-04-11
if its open source, yes, you may be able to compile it (providing there arent any dependencies that cant be met) otherwise you cant. the only way you can do it without buying a mac is to acquire a version of mac os x that you can run in a virtual machine.

---

### Post by aeiah on 2008-04-11
you might want to look here, although it seems rather outdated and unreliable: [http://ubuntuforums.org/showthread.php?t=180073](http://ubuntuforums.org/showthread.php?t=180073)

or google around for 'mp3 to m4b linux'

---

### Post by swoll1980 on 2008-04-11
> **aeiah said:**
> if its open source, yes, you may be able to compile it (providing there arent any dependencies that cant be met) otherwise you cant. the only way you can do it without buying a mac is to acquire a version of mac os x that you can run in a virtual machine.

You can't install osx on a pc though so you can't use virtualbox or vmware you have to use a special vm that emulates a mac computer I forget what the name of the popular choice is

---

### Post by popch on 2008-04-11
The license agreement for Mac OS X explicitly forbids running the OS on any machine. Excepting Apple computers, of course.

AFAIK Darwin runs the same kernel and is both open and free. That would be a bit like the Max OS X without the GUI, I suppose.

That might still not be so useful when the object is to run MAC OS applications, as they are bound to need services provided by the parts of Mac OS X which is not in Darwin.

---

### Post by roaldz on 2008-04-11
You can run Mac OS X Leopard on a Virtual computer, and on a normal computer. I know this, because i´ve got it running on my laptop.
Mac software is built for aqua and quartz. I don´t know much about it, but it´s not GTK and Xorg:)
You can get opendarwin to run apple´s bsd-like os.
Look on wikipedia for a unix/bsd history diagram, its VERY interesting!:)

Roald

---

### Post by 3rdalbum on 2008-04-11
Sorry to continue a megabump, but the fact that the Mac OS X kernel bears a passing resemblence to another Unix isn't going to help in writing a compatibility layer :-)  Just like with Windows and Wine, the real problem is reverse-engineering and reimplementing the core OS X libraries. They are not present in Darwin so they cannot be studied. The presence of undocumented OS X APIs is well known, and unfortunately Apple's own programs depend on them.

So yeah, something like Wine could be developed for running OS X programs, but the challenges would be no less great than with Wine.

---

### Post by boomtisk on 2008-04-11
Isn't running Mac programs on Non-Apple hardware illegal according to Apple's EULA?

---

### Post by roaldz on 2008-04-11
> **boomtisk said:**
> Isn't running Mac programs on Non-Apple hardware illegal according to Apple's EULA?

Yes, just like running osx on non-apple hardware, or unlicensed copy´s of windows. Just like driving through a red light:)
Just like smoking weed in amsterdam:P

---

### Post by Dixon Bainbridge on 2008-04-11
> **boomtisk said:**
> Isn't running Mac programs on Non-Apple hardware illegal according to Apple's EULA?

Does anyone actually read the EULA, let alone adhere to it? :)

---

### Post by Speed Demon on 2009-01-18
> **Dixon Bainbridge said:**
> Does anyone actually read the EULA, let alone adhere to it? :)

:lol: Thats a good point. I always just SAY I accept it unless it is Windows. Then I make sure I can get a refund if I dont accept it :popcorn::P

---

### Post by turfreijer on 2009-05-03
smoking weed in amsterdam is not illegal....hahaha ;-)

---

### Post by lvleph on 2009-05-03
But it is not legal either. lol

---

### Post by merkourio on 2009-05-03
Veeeeeeeeeeeeeeeeeeryyyyy interesting point....
What about making "Champagne" guys??? :popcorn:

---

### Post by ssam on 2009-05-27
[http://ubuntuforums.org/showthread.php?t=475328](http://ubuntuforums.org/showthread.php?t=475328)
[http://ubuntuforums.org/showthread.php?t=1097789](http://ubuntuforums.org/showthread.php?t=1097789)

i am not a lawyer, but i read groklaw.

i don't think EULAs has much to do with it, just like wine is unaffected by the windows EULA. if a particular program had the 'only on apple branded computers' clause then it may have an effect, but i'm not even sure if apple's own apps have this (safari accidentally had the clause on one release, but it was removed [http://news.cnet.com/8301-10784_3-9904445-7.html](http://news.cnet.com/8301-10784_3-9904445-7.html) , if you look at the new version it does not mention apple branded computers at all.)

also no one is even sure if the clause is valid for Mac OS X.

---

### Post by FLMKane on 2009-05-27
> **Rhox said:**
> Linux is not a fork of Unix. Linux was a clone of Minix. FreeBSD was a fork of 386BSD but its code doesn't really resemble 386BSD.

Linux is nothing like Minix, aside from the fact that they are both Unix-like

---

### Post by MaxIBoy on 2009-05-27
[LIST]
[*]FreeBSD is binary compatible with XNU, which is the kernel in OS X.
[*]DarwinBSD is a BSD built around the XNU kernel. OS X is built around Darwin.
[*]Both Darwin and XNU are open source.
[*]However, OS X uses a different toolkit for widgets. In Linux, we have GTk+, Qt, and WxWidgets. OS X uses Cocoa. Cocoa is proprietary.
[*]So, you can use command-line tools for DarwinBSD, and they'll run on FreeBSD and they're easy to port to other Unix-like operating systems, but you can't use graphical programs for OS X, because the graphics toolkits are proprietary and exist only for OS X.
[/LIST]

---

### Post by DeadSuperHero on 2009-05-27
> **swoll1980 said:**
> You can't install osx on a pc though so you can't use virtualbox or vmware you have to use a special vm that emulates a mac computer I forget what the name of the popular choice is

Technically, you can with osx86.

---

### Post by 3rdalbum on 2009-05-27
> **MaxIBoy said:**
> [LIST]
[*]However, OS X uses a different toolkit for widgets. In Linux, we have GTk+, Qt, and WxWidgets. OS X uses Cocoa. Cocoa is proprietary.
[*]So, you can use command-line tools for DarwinBSD, and they'll run on FreeBSD and they're easy to port to other Unix-like operating systems, but you can't use graphical programs for OS X, because the graphics toolkits are proprietary and exist only for OS X.
[/LIST]

Forget graphical toolkits; Mac OS X uses completely different APIs to what we use on Linux. The underlying userspace tools are completely different, too; try doing anything on the command-line on Mac OS X and you'll find it completely different.

Making a compatibility environment for OS X would be just as difficult and time-consuming as it was to make Wine.

---

### Post by MaxIBoy on 2009-05-27
I have done things on the command line in OS X. Bash shell, GNU coreutils, lp printer tools, and our favorite "remove recursive force" command worked without a hitch.

---

### Post by hanzomon4 on 2009-05-27
The CLI is not really different some apps are directly related to apple's own closed software but I haven't run across many, diskutil is one. And sometimes os X just uses different FOSS apps like curl instead of wget by default

---

### Post by Dark Aspect on 2009-05-27
You can hack a Mac OSX iso and load it on virtualbox and even native Intel based cores but I don't think the process is legal. Sadly AMD cores are not supported in this loop hole and its hardware support once you load Mac OSX is very limited.

---

### Post by 3rdalbum on 2009-05-27
> **MaxIBoy said:**
> I have done things on the command line in OS X. Bash shell, GNU coreutils, lp printer tools, and our favorite "remove recursive force" command worked without a hitch.

Ever tried to add or modify a user account?

---

### Post by hanzomon4 on 2009-05-27
add_user?

---

### Post by schauerlich on 2009-05-28
> **MaxIBoy said:**
> I have done things on the command line in OS X. Bash shell, GNU coreutils, lp printer tools, and our favorite "remove recursive force" command worked without a hitch.

Mac OS X does use GNU bash, but I'm pretty sure the coreutils is made up of BSD equivalents.

---

### Post by dstempfley on 2009-05-28
What an interesting thread to get tangled in.

As to the original question, I haven't tried it (my osx runs happily on my mac), but a quick look at the osx86 project implies it can probably be done.  [http://wiki.osx86project.org/](http://wiki.osx86project.org/)

It sounds like an exercise in futility to get anything more than basic commands to work natively.  It may be possible, but other then the wow factor, why would you want to?
  
As for BSD being a "fork" of Unix.  Many die hard Unix guys will say that BSD IS Unix.

While Linux may be nothing like Minix now, it's well documented that Linus developed the Linux kernel as a free replacement for the Minix operating system, which I had to pay $100 for for as part of a CS class.  The first version even used Minix user space tools.  It stands to reason then, that at least the early versions of Linux were something like Minix, even if that's no longer the case.  

My 2 cents.

/Dion

---

### Post by lykwydchykyn on 2009-05-28
> **dstempfley said:**
> 
  
As for BSD being a "fork" of Unix.  Many die hard Unix guys will say that BSD IS Unix.

I think many people don't realize that Unix is not a single OS.  It is a classification of OS's that adhere to POSIX and SUS and have been certified by The Open Group as a Unix.

Linux is not certified as Unix, but it aims to comply with both POSIX and SUS and I doubt anyone could tell me any specific way in which it doesn't comply.  I suspect it is only not certified because nobody cares enough to pay for certification.

> 
While Linux may be nothing like Minix now, it's well documented that Linus developed the Linux kernel as a free replacement for the Minix operating system, which I had to pay $100 for for as part of a CS class.  The first version even used Minix user space tools.  It stands to reason then, that at least the early versions of Linux were something like Minix, even if that's no longer the case.  


The ironic thing is that one of the first big flame wars (which still comes up today) of the Linux community centers around its fundamental DIFFERENCE from Minix -- macrokernel vs. microkernel architecture.  So I find it kind of funny that people would say Linux is based on Minix.

Otherwise, though, you have a good point.

When it comes to the Unix thing, though, people tend to split hairs over something that is really quite nebulous.  I'm not a Unix expert, but from what little I have seen of AIX, Solaris, HP-UX, SCO, OSX, and BSD (all officially Unix), Linux doesn't seem any more different from them as they are from one another.

---

### Post by dstempfley on 2009-05-28
> **lykwydchykyn said:**
> 
When it comes to the Unix thing, though, people tend to split hairs over something that is really quite nebulous.  I'm not a Unix expert, but from what little I have seen of AIX, Solaris, HP-UX, SCO, OSX, and BSD (all officially Unix), Linux doesn't seem any more different from them as they are from one another.

AFAIK anymore, the difference is only important to those uberdorks (he says with the utmost respect) that speak kernel code as a second language.

---

### Post by dstempfley on 2009-05-28
> **3rdalbum said:**
> Ever tried to add or modify a user account?

It's slightly reminiscent of using the nis+ commands to manage namespace information.  It's not pretty but looks something like:

dscl . -create /Users/testuser
dscl . -create /Users/testuser UserShell /bin/bash
dscl . -create /Users/testuser RealName “Test User”
dscl . -create /Users/testuser UniqueID 502 
dscl . -create /Users/testuser PrimaryGroupID 80
dscl . -create /Users/testuser NFSHomeDirectory /Users/testuser
dscl . -passwd /Users/testuser PASSWORD
dscl . -append /Groups/admin GroupMembership testuser

/usr/sbin/inituser testuser

I suppose you could wrapper that with a useradd script.
But I fear we digress way too far.

---

### Post by MikeTheC on 2009-05-28
Well, the OSx86 Project is alive and well, I can tell you that much.

Any more than that I'm not sayin' in a public forum, but what I will say is I'm not exactly in Luna, Aero, XFCE, KDE or Gnome as I type this.

---

### Post by schauerlich on 2009-05-28
> **MikeTheC said:**
> Well, the OSx86 Project is alive and well, I can tell you that much.

Any more than that I'm not sayin' in a public forum, but what I will say is I'm not exactly in Luna, Aero, XFCE, KDE or Gnome as I type this.

I like wmii too.

---

### Post by hanzomon4 on 2009-05-28
> **dstempfley said:**
> It's slightly reminiscent of using the nis+ commands to manage namespace information.  It's not pretty but looks something like:

dscl . -create /Users/testuser
dscl . -create /Users/testuser UserShell /bin/bash
dscl . -create /Users/testuser RealName “Test User”
dscl . -create /Users/testuser UniqueID 502 
dscl . -create /Users/testuser PrimaryGroupID 80
dscl . -create /Users/testuser NFSHomeDirectory /Users/testuser
dscl . -passwd /Users/testuser PASSWORD
dscl . -append /Groups/admin GroupMembership testuser

/usr/sbin/inituser testuser

I suppose you could wrapper that with a useradd script.
But I fear we digress way too far.

Um add_user```
add_user(7)            Mac OS X Darwin ZSH customization           add_user(7)

NAME
       add_user  - Add a user to the Directory Service database and create the
       user's account

SYNOPSIS
       add_user username fullname uid account_type

       where

       username is a one-word short username that becomes the username of  the
       account

       fullname  can  be a multi-word full name such as "Joseph P. Docus" pro-
       vided the double-quotes are present.

       uid is an (unused) numerical user id integer (Mac OS X starts numbering
       users consecutively from 501 but any larger integers may be used)

       account_type must be either "staff" or "admin".

       All  four  arguments  are  compulsory and must be supplied in the order given above.

DESCRIPTION
       add_user Consider using the System Preferences  >  Accounts  preference
       pane to do this instead.

       The add_user command must be invoked by an admin user.

       Takes  the  user's username (i.e., account name, short name), fullname,
       uid, and staff|admin and creates:

       a new user in NetInfo passwd

       a new /Users/username home directory

SEE ALSO
       add_user(7),     addgroup(7),     delete_user(7),      delete_group(7),
       remove_user_from_group(7), adduser2group(7)




```

---

### Post by dstempfley on 2009-05-28
> **hanzomon4 said:**
> Um add_user ... 

I hadn't seen that.  It's not native on any OS X but it does keep you from having to write it yourself.  It's from a collection of zsh template scripts to assist with administration.  [zsh-templates-osx]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fcode.google.com%2Fp%2Fzsh-templates-osx%2F&ei=mqUeSsTLC92rtgfSufHrAw&usg=AFQjCNEIjqTMUvG2X-dMt74JUXLHAWKaOQ")  In the script it uses dscl to do the work.

---

### Post by DCK on 2009-05-28
I'm quite unfamiliar with the libraries needed to implement to get OS X working. I've heard that, with OS X being Unix-like it should  and their Cocoa API being based on OpenStep that there's already some code in the right direction in the GNUStep.

If an OS X compatibility layer is any more easy to complete than Wine, it should have serious consideration. There are a lot of propietary killer apps that won't come close to a Linux release like:
- Adobe Creative Suite (including Photoshop, InDesign, Illustrator etc.)
- Microsoft Office:mac
- iTunes
- Various CAD applications
- Maya3D

OS X excels in production applications, and Linux/BSD is severely lacking in that respect to the other two major OSes. Most users use Wine, but it is lacking - maybe an OS X layer would be able to be more efficient?

---

### Post by dspari1 on 2009-05-28
> **lykwydchykyn said:**
> I think many people don't realize that Unix is not a single OS.  It is a classification of OS's that adhere to POSIX and SUS and have been certified by The Open Group as a Unix.

Linux is not certified as Unix, but it aims to comply with both POSIX and SUS and I doubt anyone could tell me any specific way in which it doesn't comply.  I suspect it is only not certified because nobody cares enough to pay for certification.



The ironic thing is that one of the first big flame wars (which still comes up today) of the Linux community centers around its fundamental DIFFERENCE from Minix -- macrokernel vs. microkernel architecture.  So I find it kind of funny that people would say Linux is based on Minix.

Otherwise, though, you have a good point.

When it comes to the Unix thing, though, people tend to split hairs over something that is really quite nebulous.  I'm not a Unix expert, but from what little I have seen of AIX, Solaris, HP-UX, SCO, OSX, and BSD (all officially Unix), Linux doesn't seem any more different from them as they are from one another.

BSD variants haven't been certified to be UNIX either:
[http://www.netbsd.org/about/call-it-a-duck.html](http://www.netbsd.org/about/call-it-a-duck.html)
[http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

> The following are not officially certified as POSIX compatible, but they conform in large part.

    * Nucleus RTOS
    * RTEMS - POSIX API support designed to IEEE Std. 1003.13-2003 PSE52
    * FreeBSD[11]
    * GNU/Linux (most distributions &#8212; see LSB)
    * NetBSD
    * BeOS
    * OpenBSD
    * Sanos
    * SkyOS
    * Syllable
    * VSTa

Furthermore, since Debian is not rpm complaint, it isn't Linux complaint. I don't agree with it, but it is what it is.

[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)

> Choice of RPM package format

For example, the LSB specifies that software packages should either be delivered as an LSB compliant installer, or (preferably) be delivered in a restricted form of the RPM format. Debian however uses its own format, the deb package format, which predates rpm. Debian developers argue their format is superior to RPM, and that further changing the underlying package format of a distribution to satisfy the LSB is fairly unrealistic. Most packages can be converted between .rpm and .deb with alien or other package conversion program, but each format has capabilities the other lacks, so this operation doesn't work every time and is impossible to use with some packages.

To address this, the standard does not dictate what package format the software system must use for its own packages, merely that RPM must be supported to allow packages from third-party distributors to be installed on a conforming system.

Since Debian already includes optional support for the LSB (at version 1.1 in "woody" and 2.0 in "sarge"), this issue evaporates under closer scrutiny (i.e. the end user just needs to use Debian's alien program to transform and install the foreign RPM packages in the native package format). This is part of the reason the specified RPM format is a restricted subset&#8212;to block usage of untranslatable RPM features. By using alien, Debian is LSB-compatible to all intents and purposes, but according to the description of the lsb-package, the presence of the lsb-package "does not imply that we believe that Debian fully complies with the Linux Standard Base, and should not be construed as a statement that Debian is LSB-compliant." This theoretical possibility of Debian's non-compliance to LSB might be considered a valid criticism, however slight.

---

### Post by lykwydchykyn on 2009-05-28
> **dspari1 said:**
> BSD variants haven't been certified to be UNIX either:
[http://www.netbsd.org/about/call-it-a-duck.html](http://www.netbsd.org/about/call-it-a-duck.html)
[http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

I stand corrected.  Still, it reinforces my point, since BSD is constantly referred to as Unix.  I doubt very many of the people who go about saying "Linux is not Unix" could actually go in to technical reasons why it's any less Unix than BSD.

---

### Post by afrodeity on 2009-06-09
I was playing with a friends macbook the other night and comparing it to my humble tower running Ubuntu Hardy 8.04. Not a lot different, except for the fact that her machine has some really amazing software. Isn't this the issue - porting some of the Mac applications over to Ubuntu? Or finding some way to create a MacOS compatibility layer like WINE? I suspect the system is converging, and the difference is more like the difference between a DEB and RPM than a Windows EXE.

---

### Post by mrebanza on 2010-01-29
wow ... what an interesting thread . . .  I just learned over 30 years of computer technology history in under 10 minutes!!!!


PS - If Porting the Mac OSX API's into the Unix Roots is Do-able....and from the sounds of this discussion it definitely is.... than it definitely should be done!!!!;)

---

### Post by AllRadioisDead on 2010-01-29
If a project is ever to be started, I propose the name **Mace**.

---

### Post by DiegoDeEscocia on 2010-01-29
Talk about an exciting potential project! I do hope this comes to fruition.

What would MACE stand for? I trust you know Wine isn't simply meant to be Win with an 'E' on the end of it....

It's a recursive acronym - WINE - *Wine* Is Not an Emulator

MACE - Macintosh Application/API Compatability Extension ?

Anyway very exciting point guys. Hope it's possible it would be increadible if it were!

(sounds easier than Wine though I'm sure my ignorance may simply make it seem so :-D )


Also what about MINE?

*MINE* Is Not an Emulator? ;-)


Also is this link of any help to anyone: [http://www.maconlinux.org](http://www.maconlinux.org)

Presently seems to be for powerpcs only.....But seems to profess to run some Mac progs under linux....

---

### Post by phrostbyte on 2010-01-29
[http://www.gnustep.org/](http://www.gnustep.org/) allows you to run some applications that were originally designed for the Mac on Linux. One of it's goal is to eventually be something like a Wine for Mac OS X.

---

### Post by schauerlich on 2010-01-29
> **phrostbyte said:**
> [http://www.gnustep.org/](http://www.gnustep.org/) allows you to run some applications that were originally designed for the Mac on Linux. One of it's goal is to eventually be something like a Wine for Mac OS X.

GNUstep is an implementation of the OpenStep specification. It's not supposed to emulate Cocoa.

---

### Post by dolphinaura on 2010-01-29
> **bash said:**
> Now that most of the new programs for Macs come out both for the PPC platform as well as the x86 I was wondering if it was possible to run Mac software in Ubuntu.

Does something similar to VMWare or Virtualbox exist for Mac software? Or even better, since Mac OS X is  by quite a big part also based on the UNIX(-like) system envirement. So maybe is there a kernel module/patch/deamon or whatever with which you can achieve to run Mac software more or less nativly in Ubuntu.

Hope someone will be able to find an answer to this other than just (hopefully not) no.
due to the fact that ubuntu does not run cocoa, which is needed to use mac apps, it is currently not possible to do so.

and according to the Apple EULA, emulating / running mac osx in any hardware than its own (this includes virtual machines) is illegal.
Although im typing from one of these right now, its against the forum TOS to talk about the emulation section, so im going to leave out that part.

---

### Post by afrodeity on 2010-02-17
I can't find any reference in the Code of Conduct about not talking about emulation! Where is the relevent section? [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

---

### Post by t0p on 2010-02-17
> **afrodeity said:**
> I can't find any reference in the Code of Conduct about not talking about emulation! Where is the relevent section? [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Emulating a Mac environment is illegal (due to the DMCA).  And it's against the CoC to discuss how to break the law.  That's what dolphinaura meant, I think.

---

### Post by forrestcupp on 2010-02-17
> **saphil said:**
> What software are you wanting to run?  
Maybe you can get the source-code and compile it for your Linux box.  
If you have source-code, the sky's the limit!!I realize that this is a very old post, but I just had to laugh.  I can give you some source code of something programmed using the win32 api.  Let's see if you can just "compile it for your Linux box."  You'd pretty much have to rewrite the whole thing. ;)

> **dolphinaura said:**
> 
and according to the Apple EULA, emulating / running mac osx in any hardware than its own (this includes virtual machines) is illegal.
There is some debate over whether or not EULAs would hold up in a court of law.  But even assuming they would, you have to accept a EULA to be bound by it.  You wouldn't have to accept MacOSx's EULA to run an emulator of it.

---

### Post by afrodeity on 2010-02-17
Should we be talking about the Mac-Linux compatibility layer as opposed to outright emulation? Emulation usually refers to interaction with a particular type of processor which strictly speaking no longer applies. Macintosh moved from PowerPC to Intel and there is nothing to stop us from calling instructions to and from an Intel compatible CPU. 

There is also nothing illegal as far as I can see, with wanting to be compatable with a propietory OS in order to run free software, otherwise, files created on Linux would not be able to be opened on Windows because of the legality and vice versa.

I also suggest we stop talking about Cocoa and move forward to Carob and [Etoile.]("http://etoileos.com/")

---

### Post by schauerlich on 2010-02-17
> **afrodeity said:**
> Should we be talking about the Mac-Linux compatibility layer as opposed to outright emulation? 

That's like recreating Wine for OS X. We'd have a small head start with GNUstep, but really, Cocoa is so much more that it would take years of work for any reasonable amount of functionality.

---

### Post by afrodeity on 2010-02-19
Well get cracking then. Must be a way to work around the problem so that we have a wholewheat version of Carob.

---

### Post by murderslastcrow on 2010-02-19
Not to be a downer, because I think it would be AMAZING to be able to run OS X software in Linux (it would basically void the whole reason of getting a Mac in the first place, of course), but I think there's a more feasible form of action. Most OS X software is also available for Linux, except for perhaps 200 titles or so. The reason for this is that people who port programs to OS X are also likely to port it to Linux, and there are very few programs for OS X that are not available elsewhere.

Wouldn't it be a better idea to spend the time and energy and man-hours asking these developers to release code for GTK/QT/WxWidget compatible interfaces, or even learn some programming and try to get on with them in porting the applications? There aren't that many, so there shouldn't be too much sweat about it- the biggest ones are Adobe CS and Final Cut (and iLife, which we know will probably never come to Linux).

Which brings me to my next point, another alternative means of getting these applications is to create open source implementations of the same technology, or helping to add format compatibility with these programs to open source projects that already exist.

Something tells me those three actions- petitioning, helping developers with work in porting, and creating/modifying open source software to do the same job- would take less time and effort than emulating the OSX APIs.

Of course, if there are dedicated people who are willing to do this, it would be awesome. However, I predict that by the time they're done, free software Operating Systems will be so commonplace no one will even care. Just think about how far computing has come in the past 15 years. Wine has been around that long and still isn't quite perfect. What will have changed in 15 years.

I know I'm being a downer, because theoretically it's a very cool idea, but unless we do it the dirty way by getting someone in Apple to port the code, I'm afraid it may be a very stressful experiment to carry out.

By all means, continue to discuss how we could make this possible. I'm still interested.

---

### Post by hobo14 on 2010-02-19
> **t0p said:**
> Emulating a Mac environment is illegal (due to the DMCA).  And it's against the CoC to discuss how to break the law.  That's what dolphinaura meant, I think.
 I'm fairly certain emulation is not illegal.  There may be something else in there that's necessary that IS illegal, but not the actual act of emulation. 

Also, of course, the DCMA is only relevant in the countries that created it: Canada and the US (but I assume UF's servers are based in the US?)

EDIT: Forgot to add also that US law contains safe harbour laws that prevent a website being held responsible for the content created by users.

---

### Post by jayg1169 on 2010-02-19
This has to be one of the most interesting threads ive read on this forum in a long time.:D

---

### Post by afrodeity on 2010-02-19
Fresh Carob Project -- we find alternatives to Cocoa by canvassing all of the above in order to get the best software running on U8untu

---

### Post by conbot on 2011-05-16
PearPC: pearpc.sourceforge.net
SheepShaver: sheepshaver.cebix.net/emaculation.com
Basilisk II: basilisk.cebix.net/emaculation.com


If you are running ubuntu on your mac: maconlinux.org

---

### Post by uRock on 2011-05-16
If the thread is over a year old, then closed for necromancy.

Thread Closed

---

