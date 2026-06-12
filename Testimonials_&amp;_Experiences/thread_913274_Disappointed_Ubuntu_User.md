---
title: "Disappointed Ubuntu User"
date: 2008-09-07
forum: Testimonials &amp; Experiences
---

### Post by _Fred_ on 2008-09-07
Well, it is with great regret that I post this message here. I sincerely hope that those who make decisions in the direction of this distro hear what I am saying.

It is a great service U has done for the world by making an easy distro based on a good distro.

I have to say though, it has been taken a bit too far.

I've been using Linux for a LONG time and Debian for almost as long (mostly "unstable") until wednesday when my hdd died (again).

Installation was pretty good, though I had to do it in two phases, first resizing an ntfs block and then manually splitting up the disk.

Why is there no root password setup stage? I had to sudo su and run passwd...

Problems :

runlevels/display managers and a lack of inittab
what causes the funny log to run on ctrl alt f8? how do i move that to f10 so i can have 8 tty terms and f9 being xorg? how do i change the runlevel to a text only boot up so i can run startx ONLY when *I* need to?

automounting of usb disks and a lack of front end tool to comprehensively turn it off (gnome volume manager no longer has a tab for this, and the gnome config thing only turns it off in gnome. gconf2 can turn it off properly, however that is a bit obscure. the file to adjust is in /etc/hal/.... at first i was happy that i had found it. Then I read the comments. As a software dev myself I care a great deal about the quality of the work I produce. Especially when it is FOSS work. The comments in that file are broken english. I would like to blame it on someone from sweden or some other non english country as that would be understandable, but my gut feeling based on observations on the internet and IRL of various cultures english skills tells me that the author was a yank :

> The following shows how to put sync and noatime on for devices smaller then 1Gb and off for device larger then that. Note that the sync option can wear out device faster then you'd like too.

This is second rate at best.

so, I move on to trying to get a decent fstab setup and again find uuid numbers making a hash of things. No problem. I fix it up more or less and add the devices I know I will need until I run across references to update grub and find out that it blows away manual config in menu.lst. This is FAR from cool and has been a bug for 2 years now.

How can I apt-get remove all of the ubuntu front end stuff (ie gnome)? I only need xfwm4 (the ONLY fully functional raw wm available, all major and some obscure ones tested...) so it would be nice to ditch everything that is gnome.

There were more things, but I've lost track

I understand that the system need to be easy as pie for every noob that is now installing this thing, but when you make it so damn difficult to build a solid static system based on it, you are shooting yourself in the foot.

Probably the best approach would have been to install ubuntu server instead and add in the gui stuff that I need rather than fighting with the stuff I don't want.

I'm at the point of dropping it for Gentoo and giving a source based setup a whirl. I'm a bit stunned at that proposition as 2 days ago you couldn't have convinced me that I would stop using debian no matter how hard you tried. Now after less than 48 hours on unbuntu I'm seriously considering no more .debs, a sad day for me at least after using deb for such a long time.

deb stable - too old
deb testing - updates for broken stuff too slow
deb unstable - great, but can't keep it fully up to date and trying to will result in issues and admin time
ubuntu - broken in some ways and difficult to normalise back to a unix like environment in others.

can i really not win? :-(

All advice and information more than welcome, teach the old dog some new tricks if you can. I really don't want to do another install now. Making this one function reasonably would be far more desirable.

Sincerely,

Fred.

---

### Post by mikewhatever on 2008-09-07
> Probably the best approach would have been to install ubuntu server instead and add in the gui stuff that I need rather than fighting with the stuff I don't want.

Well, why didn't you? You probably won't need instructions on doing it, yet, perhaps some other 'disappointed user' will.

[http://psychocats.net/ubuntu/minimal#barebones](http://psychocats.net/ubuntu/minimal#barebones)

I've noticed you said not another install, <sudo rm ubuntu-desktop> should remove all of gnome with apps and stuff.

---

### Post by photonian on 2008-09-07
:)
dito

---

### Post by _Fred_ on 2008-09-07
> **mikewhatever said:**
> Well, why didn't you?
Good question, fast download of most common variant in the knowledge that it's *only* a config change away is probably the answer.

[http://psychocats.net/ubuntu/minimal#barebones](http://psychocats.net/ubuntu/minimal#barebones)

Thanks for the link :-)

> I've noticed you said not another install, <sudo rm ubuntu-desktop> should remove all of gnome with apps and stuff.

Thanks, I'll give that a whirl.

To be honest, the gui aspect is the least of my worries. The fstab and inittab stuff is seriously concerning. It's like they've taken a calf and grown it into a prize bull and then broken all four ankles with a baseball bat...

I have no problem with guis etc being all automated and hands off as they are easy enough to swap out. When the system underneath starts to be nonconfigurable because some dev knows better than the rest of us... well... that's another story isn't it!

I was using windowmaker until I bought a new monitor and needed xrandr. I tested 12 window managers or so and xfwm4 was the only one that behaved more or less properly. metacity was broken, kdes one was broken, sawfish, broken, ice, blackbox, ion etc all broken or not usable for my purpose.

I'm comfortable doing all that stuff and much more, I built a new 2.6 kernel for each kernel.org release when they first came out and loved it. To do that at the time meant swapping all the tools from the old way to the new way (i forget what changed, but something would only work with the right version kernel about then).

If I can't do 

apt-get install grub

and not break my system and/or config though... how can i have confidence in the thing?

any tips for /etc/event.d/ stuff? I have no idea about that at all.

Thanks for your input, love the sig btw.

Fred.

---

### Post by ByteJuggler on 2008-09-07
> **_Fred_ said:**
> Well, it is with great regret that I post this message here. I sincerely hope that those who make decisions in the direction of this distro hear what I am saying.

It is a great service U has done for the world by making an easy distro based on a good distro.

I have to say though, it has been taken a bit too far.

I've been using Linux for a LONG time and Debian for almost as long (mostly "unstable") until wednesday when my hdd died (again).

I'm presuming you're just mentioning this (hdd breaking) conversationally and not saying that Ubuntu has had anything to do with this?  BTW if you want your comments to be heard by the dev's/ubuntu teams, it would be better to (also) post them on Launchpad rather than on the *community* forums, which this is.  

> **_Fred_ said:**
> 
Installation was pretty good, though I had to do it in two phases, first resizing an ntfs block and then manually splitting up the disk.

Why is there no root password setup stage? I had to sudo su and run passwd...

Because Ubuntu's security model disables the root account to close down a common attack vector.  (How long have you been an Ubuntu user?) If you had asked about this and/or searched the community documentation this would've become abundantly clear.  See _[here]("http://ubuntuforums.org/showthread.php?t=765414")_, and _[here]("https://help.ubuntu.com/community/RootSudo")_.  **You should almost never enable the root account on Ubuntu.**

> **_Fred_ said:**
> 
runlevels/display managers and a lack of inittab
what causes the funny log to run on ctrl alt f8? how do i move that to f10 so i can have 8 tty terms and f9 being xorg? how do i change the runlevel to a text only boot up so i can run startx ONLY when *I* need to?

OK, since you've been using Linux for a long time you should know that the runlevels are stored in /etc/rcx.d folders, where x is the runlevel number.  A little bit of digging (like 2 minutes worth, since I just found this out myself) reveals that Ubuntu (and Fedora 9, and Debian Experimental) has replaced the venerable SysV init with [_Upstart_]("http://upstart.ubuntu.com/"), an event driven init daemon.  There is however a "telinit" command that works with Upstart to emulate the old style init behaviour, but obviously there are differences, one of which is that by default there's no inittab, and by default the default runlevel is therefore runlevel 2.  (See /etc/event.d/rc-default.)  You can override the runlevel 2 default by creating an inittab, or by editing /etc/event.d/rc-default.

As for your tty question, that also lies tied up with Upstart:  Have a look in /etc/event.d at the files "tty1" - "tty6".  It contains the definitions for each default tty.  To add a new tty, create a new file called e.g. "tty7" and modify as required.

As for X, or rather "gdm", the Gnome display manager (which you should be familiar with) is still started via a conventional rc.d script, in particular it's "/etc/rc2.d/S13gdm" on my gutsy server. To disable X starting in runlevel 2, rename that link (to for example _S13gdm) or remove it.  Alternatively, use the "update-rc.d" to modify init style startup scripts via a command.  Try "man update-rc.d" to get more (but you should know to do that  given your longtime Linux usage.)

> **_Fred_ said:**
> 
automounting of usb disks and a lack of front end tool to comprehensively turn it off (gnome volume manager no longer has a tab for this, and the gnome config thing only turns it off in gnome. gconf2 can turn it off properly, however that is a bit obscure. the file to adjust is in /etc/hal/.... at first i was happy that i had found it.

Perhaps it'd be a good idea to request/suggest it (GUI for this) as a feature on Launchpad.  But, at least you seem to have a solution.

> **_Fred_ said:**
> 
Then I read the comments. As a software dev myself I care a great deal about the quality of the work I produce. Especially when it is FOSS work. The comments in that file are broken english. I would like to blame it on someone from sweden or some other non English country as that would be understandable, but my gut feeling based on observations on the internet and IRL of various cultures English skills tells me that the author was a yank : This is second rate at best.

I'm not really sure what you're complaining about here -- sure the English could be better, but does that have anything to do with your auto-mounting problem as such?  The quality of a person's English (whether American or not) does not necessarily imply anything about the quality of their software work.  In any case, I'll also just note that gconftool-2 and preferences.fdi is not exclusively part of Ubuntu.  I suggest you submit a patch for this to the Gnome project (or just email the project.)  Also, don't you think it's a bit harsh to judge the entire Gnome project as poor quality due to poor English grammar in a config file?  Or am I reading you/inferring incorrectly?

> **_Fred_ said:**
> 
so, I move on to trying to get a decent fstab setup and again find uuid numbers making a hash of things. No problem. I fix it up more or less and add the devices I know I will need until I run across references to update grub and find out that it blows away manual config in menu.lst. This is FAR from cool and has been a bug for 2 years now.


I'm not sure what you mean here -- "update-grub" is a script which is **meant to overwrite the existing menu.lst**.  See "man update-grub" where its purpose is explained.  The script file itself also clearly states:

> ## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below


Entries below the "AUTOMAGIC KERNELS LIST" are however left alone, but obviously any edits between the markers (to the autogenerated menu entries) are blown away on running update-grub, as the menu.lst warns.  That is however expected behaviour and not a bug.  

Or am I misunderstanding you?  

> **_Fred_ said:**
> 
How can I apt-get remove all of the ubuntu front end stuff (ie gnome)? I only need xfwm4 (the ONLY fully functional raw wm available, all major and some obscure ones tested...) so it would be nice to ditch everything that is gnome.


There are commands to do that, but really I'd actually recommend you rather install the server edition of Ubuntu which does not include any GUI stuff, and then install xfwm4 on top of that afterwards. If you actually want to do this I'll help you find the answers.  (Or, see _[here]("http://ubuntuforums.org/showthread.php?t=186556")_ which leads _[here]("http://ubuntuforums.org/showpost.php?p=1106946&postcount=2")_.  Look into "debfoster".)

> **_Fred_ said:**
> 
There were more things, but I've lost track

I understand that the system need to be easy as pie for every noob that is now installing this thing, but when you make it so damn difficult to build a solid static system based on it, you are shooting yourself in the foot.

Well, for what it's worth, my Ubuntu desktop based server is really rather stable and on 24/7.  It frequently has uptimes of over a month, after which I usually upgrade/install patches and reboot if neccesary (and deal with any upgrade problems e.g. VMWare kernel modules needing recompiling or whatever.) So it's certainly possible to have a very stable setup, whether or not you have a GUI installed. (I use the server to host services as well as to do some remote desktop/terminal services style work with NX.) 

> **_Fred_ said:**
> 
Probably the best approach would have been to install ubuntu server instead and add in the gui stuff that I need rather than fighting with the stuff I don't want.


Yep. Can you not do this anymore? 

> **_Fred_ said:**
> 
I'm at the point of dropping it for Gentoo and giving a source based setup a whirl. I'm a bit stunned at that proposition as 2 days ago you couldn't have convinced me that I would stop using debian no matter how hard you tried. Now after less than 48 hours on unbuntu I'm seriously considering no more .debs, a sad day for me at least after using deb for such a long time.


By all means give Gentoo (and any other distro you like) a whirl.  But don't expect "the perfect" distro to exist.  Maybe you find one more to your liking, I hope you do.  But I must say (if I may say so), for someone that's used Linux for as long as you have, you seem to give up very quickly.  I've answered half your questions in this post, not having directly known most of the answers beforehand but having known more or less where to look and so on (which is probably partly due to me also using Linux off and on for quite a long time now, similar to yourself.)  This makes it appear to me that your problems are perhaps not as big in reality as you experience them to be and that with a little patience you might actually get everything sorted out to your satisfaction?  :confused:

> **_Fred_ said:**
> 
All advice and information more than welcome, teach the old dog some new tricks if you can. I really don't want to do another install now. Making this one function reasonably would be far more desirable.

Well, I hope I've helped you in that goal.  Perhaps you can post separate threads on each of the issues you're having and see if people help you.  And as I say be patient, sometimes a little persistence is required.  Also, you might ask questions on _[Launchpad]("https://launchpad.net/ubuntu")_, particularly the appropriate projects themselves if appropriate, sometimes you'll get answers from developers involved with the projects etc.

---

### Post by _Fred_ on 2008-09-08
My god your post is huge.

You've made a lot of assumptions and read

__________________________________________

between the lines
__________________________________________

a lot also.

The only thing I'll say now is that I've been using linux not on and off, but solidly 12 hours a day for many years and admining some solaris boxes at work etc etc etc too.

My question about the tty stuff was to find out what was running the logging tty and how could i be certain to relocate that explicitly to a new F key. adding my extra two ttys was already done when i posted. I don't just want to cross my fingers when I make a change, I want to understand all the implications and I can't for the life of me find what that screen is called or what is running it and how it ends up on that key combo.

I've gotta get some shut eye before another long day so I can't afford the time to write a fully detailed response to your post right now.

I will say though, thank you for putting in the effort there. I do appreciate it even if it was a bit misguided in places :-)

Fred.

---

### Post by ByteJuggler on 2008-09-08
> **_Fred_ said:**
> My god your post is huge.
You've made a lot of assumptions and read
between the lines
a lot also.

I try to be thorough, and your post was long as well. Clearly I was not thorough enough though as I didn't answer your kernel logging question below. :-)  Anyway, I'm sorry if I misread you but remember that people respond both to the tone of and the content of a post.  

> **_Fred_ said:**
> 
The only thing I'll say now is that I've been using linux not on and off, but solidly 12 hours a day for many years and admining some solaris boxes at work etc etc etc too.
Your point being?  Let me just say that I'm really trying to ignore/move the conversation away from the issue of who's got what experience as I think that's largely irrelevant (hence my non commital description.)  But suffice it to say that I can just as well describe my experience as you did yours above. 

> **_Fred_ said:**
> 
My question about the tty stuff was to find out what was running the logging tty and how could i be certain to relocate that explicitly to a new F key. adding my extra two ttys was already done when i posted. I don't just want to cross my fingers when I make a change, I want to understand all the implications and I can't for the life of me find what that screen is called or what is running it and how it ends up on that key combo.

Sorry that sort of got lost in the noise - I did try to answer all your questions but that one slipped the net.   

Anyway, are you talking about the kernel debug/output console, which normally goes to tty8? (alt-f8 )  If so see the "console=" **_[kernel boot paramter]("http://www.kernel.org/hg/index.cgi/linux-2.6/file/fc7ca9955988/Documentation/kernel-parameters.txt")_**.  Add (for example) "console=tty16" to the kernel parameters to make kernel output go to tty16.

> **_Fred_ said:**
> 
I've gotta get some shut eye before another long day so I can't afford the time to write a fully detailed response to your post right now.

I will say though, thank you for putting in the effort there. I do appreciate it even if it was a bit misguided in places :-)

I'm sorry if it was misguided in places.  It's just that it was late and I get slightly frustrated with posts that on the one hand asks for help while simultaneously complaining and making out like some problems are huge big issues when experience of many years reflects differently, and then on the other hand the poster makes claims as to their experience etc. which seems incongruous with the questions and complaints.  No offence intended.  I shall try be more careful in future. :)

---

### Post by _Fred_ on 2008-09-09
I'm still out of time at this stage, so no complete detailed reply again... I feel so slack...

ULTRA brief summary :

root : thank you for the links, you answered the question though I don't agree with quite a bit of what they have said. It's a bunch of excuses to keep support load down. That is fine. I was just wondering why, it took 0.5 seconds to enable it for console use and I don't want a gui root account though I have used them in the past for very good reasons at specific times very carefully. If they are going to disable the root account via setting no password they should also disallow console root logins which they appear not to have done. A little inconsistent unless I'm confused which is possible.

kernel console mode : you learn something every day, thanks!

while we are on a roll here does anyone know how to remove those time stamps from the bootup text output? it's ugly as sin and heavily reduces readability. I'm hoping it's configurable and not hard compiled into the kernel...

You were right to give me a bit of stick back btw. There was and still is "tone" in my post(s) due to feeling a bit shafted (by my own doing). I've got only about 1.5 hours net time a day as of last week when I became un-un-employed and a lot of responsibilities to deal with in that time. I was counting on my machine for dev time on the train and I haven't had it. My FOSS projects schedule has been pushed back about 2 weeks due to the dead hdd (not blamed on ubuntu, that would just be silly to say) and the choice of ubuntu over a more familiar setup.

The lesson to be learned here is that ubuntu is definitely a fork not a child and given the fork was about 3 years ago or so the divergence has been fairly significant.

Thanks again,

Fred.

---

### Post by _Fred_ on 2008-09-09
I just noticed that you are a bloody POHM, where abouts are you roughly, maybe I could spare 30 seconds to buy you a beer in London some time before I jump on a Jet back to NZ.

---

### Post by ByteJuggler on 2008-09-09
> **_Fred_ said:**
> I'm still out of time at this stage, so no complete detailed reply again... I feel so slack...

No worries, there's only 24h in a day - I some days wish there were 48, tbh. :(

> **_Fred_ said:**
> 
root : thank you for the links, you answered the question though I don't agree with quite a bit of what they have said. It's a bunch of excuses to keep support load down. That is fine. I was just wondering why, it took 0.5 seconds to enable it for console use and I don't want a gui root account though I have used them in the past for very good reasons at specific times very carefully. If they are going to disable the root account via setting no password they should also disallow console root logins which they appear not to have done. A little inconsistent unless I'm confused which is possible.


Ok, my ultra brief response:  If the root account has no password (meaning it's locked so that it cannot log in at all, not meaning that you can login without a password), then it's by definition _not crackable_, it's that simple.  It means that a cracker then must find both a valid username on a system and then the password to that username to get into the system, if gaining access by conventional means.  

If however the root account has some password, then you only need to find the password to it to gain *root* access to the system.  And unfortunately, most casual crackers targetting the password system expects Unix/Linux systems to have a root account with a password.  Now, you can imagine, with end users picking and setting passwords for root, this opens a big potential attack vector since many people will pick and set weak root passwords which may be brute force crackable by miscreants and script kiddies.  So, to completely eliminate this attack vector, Ubuntu removes the root password and locks the root account and instead provides "sudo", which still gives users access to "root" privileges when needed.  Thus, sudo avoids the common "root" account attack vector by completely locking the root account, and instead, granting only certain users "sudo" permissions.  Thus requiring hackers to firstly identify user accounts on a system (which can be more tricky than it sounds) and then also cracking it/them.  It's by no means perfect or a silver bullet (but then, what is??) but it does add to the security model and removes a common attack vector, and for that reason alone I think it's worthwhile.

In any case, you can obtain a root shell (which is usually what most people *really *want when they say they want to enable the root account) by using e.g. "sudo -i" or "sudo -s".  In practice there's very little difference between logging in as root and doing either "sudo -i" or "sudo -s" after you've gained root privileges, hence why "sudo" is the preferred option.  (OK, so that wasn't exactly ultra brief...) :P

As for root logins, let me reiterate that root logins are disabled, full stop, in all normal run-levels.  **Hence, normally, you should not be able to logon directly (by entering a password) as root on Ubuntu, period.**  If you can, then the root account's been unlocked, and you should then lock it again with "passwd -l root".   (The only exception is if you boot up with the "recovery mode" (or a suitable LiveCD), which drops you to a root shell directly, however that implies physical access to the machine, in which case generally all bets are off anyway.)

> **_Fred_ said:**
> 
kernel console mode : you learn something every day, thanks!


OK glad that helped.  :-)  As an aside: If there's one thing that's both a blessing and a curse about this industry, it's exactly that - you learn something new every single day, and there's _always_ more stuff to be learnt...

> **_Fred_ said:**
> 
while we are on a roll here does anyone know how to remove those time stamps from the bootup text output? it's ugly as sin and heavily reduces readability. I'm hoping it's configurable and not hard compiled into the kernel...

As far as I know it's just kernel debug info, hence not meant to be particularly pretty.  However, it (particularly the timestamps) does follow a very distinct pattern (encodable into a regexp), so one can easily strip them out or reformat (or remove) them with a bit of awk, perl or python.  If you feel strongly enough about it I'll try to help you write a filter script to remove/reformat them. Alternatively, if you feel adventurous, it's probably not *that* hard to hunt down the relevant code in the kernel and build your own custom kernel with that stripped out... ;)

Anyway, let me/us know if there's anything else, I'll try to help.  (Feel free to PM me if you want.  This has been an interesting exchange. :) )

---

### Post by ByteJuggler on 2008-09-09
> **_Fred_ said:**
> I just noticed that you are a bloody POHM, where abouts are you roughly, maybe I could spare 30 seconds to buy you a beer in London some time before I jump on a Jet back to NZ.

You're a kiwi then?  That explains a few things! :popcorn: Congrats on the rugby recently by the way.  (Mutter... mutter...)  Good luck against the Aussies next Saturday.  (Aside, as you can see from my profile, I'm not a native POHM, I'm actually also a South African, and so a fellow southern hemispherian as well... :) )

Anyway, I'd probably have taken you up on the offer of a free beverage even though we're close to Leicester (not London), except, I'm off on 3 weeks holiday to the States tomorrow...

---

### Post by _Fred_ on 2008-09-11
LOL, not a POHM, but a Yarpy instead! :-) I have to ask, English decent, or Afrikans? Have a good time in either case!

I'm not jumping on that Jet for about 11 months ( :-( and you thought I whinged about ubuntu a lot! ) so there is time for a beer if/when you are down that way.

I'm going to try to get a bunch of stuff installed and downloaded tonight, I may even try my first reboot, uptime currently at :

fred@rwdlsd:~/Desktop$ uptime
 10:34:02 up 5 days,  5:50, 19 users,  load average: 0.06, 0.21, 0.23

I have a funny little blue thing telling me i need a restart, bizzare, I only ever restart for kernels, I guess I must have updated the kernel package then ;-)

Fred.

---

### Post by HousieMousie2 on 2008-09-15
Thank you gentlemen, this has been a very interesting and informative thread to read.  As a newbie, I don't pretend to understand much of what was exchanged, but I am grateful for those things I did manage to absorb.  I must commend you both for rising above 'tonal issues' that so often derail the to true objectives of this site.

---

### Post by _Fred_ on 2008-09-15
I've dug and I've dug and I am now certain that I'm going back to good old deb. The list of things to "fix" got sooooo long. Various apps have been modified to interact with the desktop creating the situation where an ubuntu official (popular) app package behaves differently to a functionally identical one that you build yourself from source. I found many many aspects of that totally unacceptable.

I will be back to tidy up the loose ends in this thread at some point, and to buy that SAFA a beer or two, but only once I have an OS that doesn't get in my way while trying to help out noobs.

The thing that grates me most is that the noobiness could have been done without breaking things for non noobs. But it hasn't. Which makes me sad.

This article and it's sister also make me sad. So sad I shed a few tears over it the other night.

[http://ianmurdock.com/2005/04/11/cant-we-all-just-get-along/](http://ianmurdock.com/2005/04/11/cant-we-all-just-get-along/)

On the one hand ubuntu "big brothering" the debian into ubuntu has undoubtedly brought MANY users away from windoze, which is a VERY good thing, but on the other hand it seems like the reason that ubuntu can even exist is almost being forgotten and left out in the cold. No where on the front page of the main site does it say "we take deb unstable and tidy it up 6 monthly" or similar euphemised version. It's like ubuntu is what it is because of it. Whereas the truth is it is what it is because it polished a gui and some tools in a certain way and slapped them on top of debian.

Peace!

Fred.

---

### Post by _Fred_ on 2008-09-21
I'm back on debian unstable and although I have some different issues of various technical types I'm happier because the issues aren't "features" they are "bugs" and thus they will get fixed (by me or someone else). It's hard to get a dev to remove a feature, but it's easy to get a dev to fix a bug.

One thing I noticed is that on deb unstable with grub2 installed the config has a do not use UUID option. That is how it should be in ubuntu too. It's not cool that the update grub script over writes the users configuration in a part of the file where it should be safe.

On a side note, deb unstable is literally twice as fast to boot as ubuntu is. 30 seconds vs 60 seconds. Also, cpu usage and ram usage during X use is a bunch lower too. Not that I care about that, but interesting to note never the less.

Fred.

---

### Post by steveneddy on 2008-09-21
> **ByteJuggler said:**
> I'm presuming you're just mentioning this (hdd breaking) conversationally and not saying that Ubuntu has had anything to do with this?  BTW if you want your comments to be heard by the dev's/ubuntu teams, it would be better to (also) post them on Launchpad rather than on the *community* forums, which this is.  


Because Ubuntu's security model disables the root account to close down a common attack vector.  (How long have you been an Ubuntu user?) If you had asked about this and/or searched the community documentation this would've become abundantly clear.  See _[here]("http://ubuntuforums.org/showthread.php?t=765414")_, and _[here]("https://help.ubuntu.com/community/RootSudo")_.  **You should almost never enable the root account on Ubuntu.**


OK, since you've been using Linux for a long time you should know that the runlevels are stored in /etc/rcx.d folders, where x is the runlevel number.  A little bit of digging (like 2 minutes worth, since I just found this out myself) reveals that Ubuntu (and Fedora 9, and Debian Experimental) has replaced the venerable SysV init with [_Upstart_]("http://upstart.ubuntu.com/"), an event driven init daemon.  There is however a "telinit" command that works with Upstart to emulate the old style init behaviour, but obviously there are differences, one of which is that by default there's no inittab, and by default the default runlevel is therefore runlevel 2.  (See /etc/event.d/rc-default.)  You can override the runlevel 2 default by creating an inittab, or by editing /etc/event.d/rc-default.

As for your tty question, that also lies tied up with Upstart:  Have a look in /etc/event.d at the files "tty1" - "tty6".  It contains the definitions for each default tty.  To add a new tty, create a new file called e.g. "tty7" and modify as required.

As for X, or rather "gdm", the Gnome display manager (which you should be familiar with) is still started via a conventional rc.d script, in particular it's "/etc/rc2.d/S13gdm" on my gutsy server. To disable X starting in runlevel 2, rename that link (to for example _S13gdm) or remove it.  Alternatively, use the "update-rc.d" to modify init style startup scripts via a command.  Try "man update-rc.d" to get more (but you should know to do that  given your longtime Linux usage.)


Perhaps it'd be a good idea to request/suggest it (GUI for this) as a feature on Launchpad.  But, at least you seem to have a solution.


I'm not really sure what you're complaining about here -- sure the English could be better, but does that have anything to do with your auto-mounting problem as such?  The quality of a person's English (whether American or not) does not necessarily imply anything about the quality of their software work.  In any case, I'll also just note that gconftool-2 and preferences.fdi is not exclusively part of Ubuntu.  I suggest you submit a patch for this to the Gnome project (or just email the project.)  Also, don't you think it's a bit harsh to judge the entire Gnome project as poor quality due to poor English grammar in a config file?  Or am I reading you/inferring incorrectly?



I'm not sure what you mean here -- "update-grub" is a script which is **meant to overwrite the existing menu.lst**.  See "man update-grub" where its purpose is explained.  The script file itself also clearly states:



Entries below the "AUTOMAGIC KERNELS LIST" are however left alone, but obviously any edits between the markers (to the autogenerated menu entries) are blown away on running update-grub, as the menu.lst warns.  That is however expected behaviour and not a bug.  

Or am I misunderstanding you?  



There are commands to do that, but really I'd actually recommend you rather install the server edition of Ubuntu which does not include any GUI stuff, and then install xfwm4 on top of that afterwards. If you actually want to do this I'll help you find the answers.  (Or, see _[here]("http://ubuntuforums.org/showthread.php?t=186556")_ which leads _[here]("http://ubuntuforums.org/showpost.php?p=1106946&postcount=2")_.  Look into "debfoster".)


Well, for what it's worth, my Ubuntu desktop based server is really rather stable and on 24/7.  It frequently has uptimes of over a month, after which I usually upgrade/install patches and reboot if neccesary (and deal with any upgrade problems e.g. VMWare kernel modules needing recompiling or whatever.) So it's certainly possible to have a very stable setup, whether or not you have a GUI installed. (I use the server to host services as well as to do some remote desktop/terminal services style work with NX.) 



Yep. Can you not do this anymore? 



By all means give Gentoo (and any other distro you like) a whirl.  But don't expect "the perfect" distro to exist.  Maybe you find one more to your liking, I hope you do.  But I must say (if I may say so), for someone that's used Linux for as long as you have, you seem to give up very quickly.  I've answered half your questions in this post, not having directly known most of the answers beforehand but having known more or less where to look and so on (which is probably partly due to me also using Linux off and on for quite a long time now, similar to yourself.)  This makes it appear to me that your problems are perhaps not as big in reality as you experience them to be and that with a little patience you might actually get everything sorted out to your satisfaction?  :confused:



Well, I hope I've helped you in that goal.  Perhaps you can post separate threads on each of the issues you're having and see if people help you.  And as I say be patient, sometimes a little persistence is required.  Also, you might ask questions on _[Launchpad]("https://launchpad.net/ubuntu")_, particularly the appropriate projects themselves if appropriate, sometimes you'll get answers from developers involved with the projects etc.

Yeah - what he said.

:popcorn:

---

### Post by _Fred_ on 2008-09-21
About the HDD, timeline :

hdd breaks > install ubuntu > cry a lot > install debian again

About root...

Saying you should never enable root on ubuntu is like saying that you should never enable root on linux which is a fundamentally flawed statement. There are many good reasons to do it, though that is a separate thing to discuss than whether it is ok to describe how to circumvent ubuntu policies on this forum. When I asked about that I purely wanted to understand why it wasn't part of the install. The two links answered those questions even if some of the content is misleading and innaccurate.

About "the rest" you'll have to wait a bit longer :-)

Fred.

---

### Post by karellen on 2008-09-21
well, have fun you two :). for those wanting a thoroughly Linux experience, there's always Gentoo, Arch, LFS and god knows what else. for us, the rest of the mortals, distros like Distrowatch's top 5 are just fine ;)

---

### Post by _Fred_ on 2008-09-21
Why not the top 6??? :-p

It's saying something seriously strong when from the top 6 4 are debian based.

BTW, if I were anything but mortal, perhaps I could have configured ubuntu to my liking.

I've heard "ubuntu is an ancient african word for "can't configure debian"" I think it would be fair to say the opposite is also true, ie, "debian is an ancient american word for "can't configure ubuntu"" :-)

The way it has been userfriendlied has broken many things if you dare to strip off the clothes... way too much for a mortal like me to make work how I want it to (as opposed to how shuttleworth thinks it should work).

Fred.

---

### Post by karellen on 2008-09-21
> **_Fred_ said:**
> Why not the top 6??? :-p

It's saying something seriously strong when from the top 6 4 are debian based.

BTW, if I were anything but mortal, perhaps I could have configured ubuntu to my liking.

I've heard "ubuntu is an ancient african word for "can't configure debian"" I think it would be fair to say the opposite is also true, ie, "debian is an ancient american word for "can't configure ubuntu"" :-)

The way it has been userfriendlied has broken many things if you dare to strip off the clothes... way too much for a mortal like me to make work how I want it to (as opposed to how shuttleworth thinks it should work).

Fred.

:) well if you ask me (which I currently dual boot Mandriva and Vista) I'd say Distrowatch's top ten ;). I used Debian and it didn't seem to different from Ubuntu.
but again, I'm not the type of user that fiddles too much with the intricacies of his OS :D

---

### Post by pdq on 2008-09-21
Fred,
It sounds like you want to tweak Ubuntu to make it work like another distro.  Why would you do that instead of just using the distro that works how you want it to work?

I'm a total noob, but this is just a common sense question rather than a technical one.

If I was buying a vehicle I would just buy the one that works the way I want as opposed to buying some other vehicle and modifying it to work like the one I should have bought.

Furthermore, if you are changing to another distro wouldn't you expect it to operate differently?  Otherwise, there would be no point to having a zillion distros.

---

### Post by hellokitty1001 on 2008-09-21
try thisss..

[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by _Fred_ on 2008-09-22
Hi,

> **pdq said:**
> I'm a total noob, but this is just a common sense question rather than a technical one.

I'll be gentle then :-)

I've said it before and I'll say it again, Ubuntu is GREAT for guys like you, new guys that want to ditch wondoze but need a helping hand to get you started. It works REALLY well for that :-)

However, what they have done could have been done in a more modular fashion such that pieces could be removed without breaking other pieces.

Things like runlevels could have been setup properly when replaced with upstart instead of just hacked in to only work for a normal desktop user.

etc. (it's a long list of things broken by friendly-for-noob mods)

> **pdq said:**
> It sounds like you want to tweak Ubuntu to make it work like another distro.  Why would you do that instead of just using the distro that works how you want it to work?

I think your understanding of what a "distro" is is a bit lacking. A distro is a large group of lots of different bits of software. 30,000 or so. I typically use about 1000 - 4000 of these, you might use a different 1000 - 4000 or less or more. With apt, each has a set of dependencies that get pulled in with the program you are after. Every program in a distro should work perfectly when installed using apt which pulls in its dependencies. If they don't, the distro is considered broken because it's dependency tree does not reflect reality. 

What ubuntu have done is polish a very narrow subset of components so they work well together ONLY and not setup the dependencies properly, and add dependencies which shouldn't exist. This isn't one, but it illustrates the point :

firefox depends on pidgin

Such deps or program mods that cause them are flawed in a fundamental way.

> **pdq said:**
> If I was buying a vehicle I would just buy the one that works the way I want as opposed to buying some other vehicle and modifying it to work like the one I should have bought.

And I would do this :

[http://www.diyefi.org/forum/viewtopic.php?f=3&t=16](http://www.diyefi.org/forum/viewtopic.php?f=3&t=16)

ie turn a $1000 truck into a weapon capable of destroying all but the most exotic sports cars on a race track for about us $5k or less.

Did mazda make it so that if i removed the engine the steering wheel had to come out too? no.

> **pdq said:**
> Furthermore, if you are changing to another distro wouldn't you expect it to operate differently?  Otherwise, there would be no point to having a zillion distros.

I would expect that all packages have sensible dependencies and are configurable in a reasonable way without breakage when deviating from the default.

Basically, to answer your main question/statement :

There is no "distro that works how I want it to" I have to adjust any of them because I am fussy and I care. This is the same for a lot of people.

In my case, I want xfwm and xfdesktop and xfsession without xfpanel and hal and dbus and christ only knows what else.

I want pidgin to run without vomitting messages onto my console complaining that something it doesn't depend on isn't there.

etc.

Perhaps this clears up why I think it's poor form?

In the process of making a noob friendly distro, they have broken the base in multiple ways if you dare to step outside the narrow box that is defined as "using ubuntu".

Regards,

Fred.

---

### Post by wolfen69 on 2008-09-22
> **_Fred_ said:**
> Well, it is with great regret that I post this message here. I sincerely hope that those who make decisions in the direction of this distro hear what I am saying.





after doing over 25 successful installs on varying hardware, i've come to this conclusion: ubuntu is great. the people that come here must have the 1 out of a hundred that wont play nice. get over it and move on. 

are you trying to get people to not use ubuntu? some people just don't get it. if something does not work for me, i don't complain, i move on. you have wasted your own time as well as my own and others. 

i'm sure mark shuttleworth will "get right on it" as far as making ubuntu work on *your* computer. while your at it, hit up the windows and mac message boards and complain there too. :rolleyes:

---

### Post by wolfen69 on 2008-09-22
> **_Fred_ said:**
> Ubuntu is GREAT for guys like you, new guys that want to ditch wondoze but need a helping hand to get you started. It works REALLY well for that :-)



i am far from a noob and have my own computer repair business. ubuntu does what it does, and does it well. what gives you the right to talk down to people? wow. it's people like you that give linux a bad name. obviously, if you were in charge of ubuntu, things would be perfect. please, don't respond to this, as you are annoying enough to make me want to slit my wrist. i would rather read something bill gates wrote than your useless "know it all" rant.

---

### Post by wolfen69 on 2008-09-22
> **pdq said:**
> Fred,
It sounds like you want to tweak Ubuntu to make it work like another distro.  Why would you do that instead of just using the distro that works how you want it to work?



because people like him want every distro to be the way *he* wants. it would make too much sense for him to use what works for him and not complain. instead of filing bug reports, or better yet starting his own distro, he has chosen to belittle himself. he believes he has the power to change millions of users minds. how sad. i hope a mod closes this sad, sad thread.

---

### Post by _Fred_ on 2008-09-22
Clearly you didn't read the last post that explained in detail why it isn't really finished/complete/stable/high quality etc.

> you are annoying enough to make me want to slit my wrist.

Please do.

At 25 years you've obviously lost the ability to care about what you use. Thus you've settled for "good enough" which is fine.

This was a request for help in sorting the issues. Once I realised that it was not going to happen because there are too many hacks/mods/patches it changed tack. Now it's a good place to discuss exactly what those things are.

Now that it's in this section, I believe I have as much right to share with people my negative experience as you have to share your positive "I didn't change anything and (of course) it still worked" experience.

Fred.

---

### Post by wolfen69 on 2008-09-22
> **_Fred_ said:**
> 


Please do.

At 25 years you've obviously lost the ability to care about what you use. Thus you've settled for "good enough" which is fine.



1. you have been reported.

2. i do care about what i use and have tried every OS under the sun. that's why i use ubuntu.

3. this is my last response.

---

### Post by _Fred_ on 2008-09-22
Reported for what? It was your suggestion :-)

Fred.

---

### Post by karellen on 2008-09-22
come on guys, there's no point in arguing over Ubuntu. there are so many choices in the FOSS world, distros for every possible taste and even easy ways to create your own distro...in the end everyone uses what suits his needs :)

---

### Post by _Fred_ on 2008-09-23
Exactly. I just had really high expectations of ubuntu. In my mind, pre trying it, it was "debian on steriods" now I'm thinking more like "debian on crack" ;-) It has it's place, but not with me.

---

### Post by karellen on 2008-09-23
> **_Fred_ said:**
> Exactly. I just had really high expectations of ubuntu. In my mind, pre trying it, it was "debian on steriods" now I'm thinking more like "debian on crack" ;-) It has it's place, but not with me.

that's fine. if it doesn't suit your needs, use other distro or make your own one

---

### Post by _Fred_ on 2008-09-23
> **karellen said:**
> that's fine. if it doesn't suit your needs, use other distro or make your own one

That is exactly what I'm doing :-)

That doesn't mean I can't post my thoughts on WHY I decided to go that way though does it?

When I get time I'll follow up the other messages in this thread that I haven't yet answered.

Fred.

---

