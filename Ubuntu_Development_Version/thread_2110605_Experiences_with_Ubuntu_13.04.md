---
title: "Experiences with Ubuntu 13.04"
date: 2013-01-30
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-01-30
Actually, last night...the installation went fine...i must say that so far it is running very well, and feels pretty stable for a "testing distro"...

And all the "pluses" i noted on the live session that are improvements on my hardware over the 12.10 version are also present in the hard installed version... :D

In 12.10 i had this bug where when i did a shut down, the computer would shut down and then turn itself back on after about 5 seconds..

In 13.04 that bug is gone...normal shutdown

In 12.10, even though i set my screen to go black after 30 minutes, it would always turn off after 10 minutes (the default setting) unless i came out of suspend first...

In 13.04, that bug is also gone for me! 

Also, power management and performance is definitely improved over 12.10 on my new Toshiba Laptop w/intel....

Problems encountered on 13.04:

1) When installing ubuntu restricted extras, the microsoft fonts license agreement did not come up...everything else got installed except for those fonts...ended up having to do it in the terminal where the agreement DID come up...

2) When going to itunes movie trailers website, i noticed that the Quicktime Videos are "tearing" they keep going from normal to distorted...This does not happen on my ubuntu 12.10 (which i am dual booting with)...

3) When i go to System Settings and adjust the mousepad settings, 
the default on pointer speed is about in the middle, and i like to lower it down to the lowest setting...
    
Once i do that, if i leave the System Settings, the Pointer Speed goes right back to the default setting...only way i can keep it set (for the session) is to leave it open....

Has anyone else working with 13.04 noticed any of these particular bugs?  Especially #3?

How can i find out if these bugs have been reported...also: how do i go about filing or adding to bug reports for 13.04?

Otherwise, i am very glad i installed it and certainly, it runs quite well...I had updates for it yesterday and today and didn't see any smoke coming out of my laptop (LOL) so...so far, so good...

---

### Post by screaminj3sus on 2013-01-30
pointer speed settings has been totally broken for me since ubuntu 12.04

---

### Post by mcellius on 2013-01-30
I've seen your bug #1, but it might not be the bug you think it is.  I eventually found the EULA window behind the Software Center, on the screen but hidden.  The download I was attempting - Ubuntu-Restricted-Extras - just hung there for a long time.  I thought it had crashed, but instead it was awaiting my input.

---

### Post by craig10x on 2013-01-30
> **mcellius said:**
> I've seen your bug #1, but it might not be the bug you think it is.  I eventually found the EULA window behind the Software Center, on the screen but hidden.  The download I was attempting - Ubuntu-Restricted-Extras - just hung there for a long time.  I thought it had crashed, but instead it was awaiting my input.

yeah, actually i did notice it under the software center eventually, but by that point i no longer had the option of installing the fonts and it just finished installing the rest...
It was take too long to finish and that is when i discovered that... That's why i ended up doing it in the terminal instead...

---

### Post by craig10x on 2013-01-30
> **screaminj3sus said:**
> pointer speed settings has been totally broken for me since ubuntu 12.04

They have been kind of troublesome for the last few editions...it is changed again for 13.04 (looks different then it was in 12.04 and 12.10) and i guess ubuntu gets that program from gnome itself, so perhaps it is a bug from their side...

How would one check to see if this bug in 13.04 has been reported?
Also, wondering if anyone else using 13.04 has experienced it too, or am i the only "lucky one"...

---

### Post by mc4man on 2013-01-30
as far as 3 - 
using a laptop/touchpad though don't think much different than mouse
The settings 'pointer speed' scales from 1.0, (far left), to 10.0 (far right. 
After changing, closing & re-opening it always goes back to near middle (about 5.75), but does not affect the previous setting.
This can be confirmed (or not) in dconf (dconf-editor > screen show for touchpad
At least here 10.0 is  too slow so up to 136.0 in dconf, when opening the settings panel it shows near middle but is actually what I set in dconf..

---

### Post by screaminj3sus on 2013-01-30
> **craig10x said:**
> They have been kind of troublesome for the last few editions...it is changed again for 13.04 (looks different then it was in 12.04 and 12.10) and i guess ubuntu gets that program from gnome itself, so perhaps it is a bug from their side...

How would one check to see if this bug in 13.04 has been reported?
Also, wondering if anyone else using 13.04 has experienced it too, or am i the only "lucky one"...

I usually just google the problem the best I can, and if I don't come across any bug reports for it then I report it, if you do end up reporting a duplicate the most that happens is someone marks it as a duplicate of the very bug you were looking for :)

As a side note I've just installed 13.04 as well. 12.10 has been so unstable and problematic for me I thought I might as well be on the bleeding edge :D. 13.04 actually seems smoother sailing so far, I have high hopes for this release, only crash I had was dconf-service crashing on the live cd, no other crashes after getting it installed and updating. Also my brightness keys finally work out of the box on my lemur ultra without needing to use the system76 driver :)

---

### Post by Curtis6767 on 2013-01-30
I upgraded from 12.10 today and now my screen doesn't turn off after 10mins of inactivity. I would never have considered jumping into 12.10 early but this new kernel makes my system run smooth and fast. Also seems to be very stable.

Hope the next update doesn't bork it.

GL

---

### Post by craig10x on 2013-01-30
Interesting mc4man...so are you saying that when i set that pointer speed to the lowest setting, it is actually retaining that setting when i close the systems settings programs, even though if i open it again, it give the appearance that it has returned to the default again?  

Just wanted to clarify...i was assuming that if it shows it went back to the default, that in fact, it was actually changing me back again...

I'll have to try to see if i can find a bug report on this...apparently, others are experiencing it too..by the way, i am using the touchpad on my laptop also...not any external mouse...

@ Curtis6767:  in my 12.10 the screen goes off after the 10 min default but when i change to any other listed time, it still stays at going off in 10 minutes!
Apparently the Screensaver feature had weird quirks in 12.10...are you saying that you upgraded to 13.04? And you got the problem with your latest update? If so, that could well get straightened out by final release...or by doing a "clean install" as sometimes problems do develop upon doing an upgrade...

@ nJ3sus: That is great to hear! And that is my experience too so far...12.10 was a bit buggy for me too (some of the problems i had i noted in my first post) and they are gone with 13.04 and this isn't even finalized yet...so it looks like it is going to be a much better experience then 12.10 and i have also noted some nice improvements in power management and performance, thanks to the 3.8 kernel it has...

---

### Post by Curtis6767 on 2013-01-31
Craig10, from the moment I upgraded from 12.04 to 12.10, my screen would turn off after 10mins of inactivity. I have always set the time to "Never" but this did not work in 12.10. It was annoying but I didn't know it was a bug. 

Up until I saw your post yesterday, I had been playing around with 13.04 in VB. I was waiting for a time when Rhythm Box would start working and when I could also get Netfilx Desktop to work, as well. That all came together with this past Tuesday's upgrades.

Then I saw your post stating that when you installed 13.04 the screen bug went away. I was hoping that an upgrade to 13.04 would eliminate this problem but, as I mentioned above, I didn't realize this was a bug until I read your original post. Now I can walk away from the computer and come back later and the screen is still on, which is as it should be, if desired.

Also, I upgraded my 12.10 system, which is dual booted with Windows, using the instructions that grahmmechanical provided in another thread in this sub forum.

FYI I'm just a casual user, not a tester, nor do I have any programming skills and because I run a program that requires NetFramework I'm not using Ubuntu as much as I was 6 months ago and if this install gets borked I won't lose anything critical.

GL

---

### Post by dino99 on 2013-01-31
Since last WE on i386 logged as gnome-classic:
- shutdown is still hanging about 5 seconds on modem-manager
- and got that new issue: if i logout, i only get a black screen with a blinking cursor. Need to hard shutdown (reset does not work)

its with nvidia activated.

---

### Post by fantab on 2013-01-31
Raring Ringtail is already so much better than the final 12.10. I hope it gets even more better... the only downside is nautilus 3.6 the earlier edition was so much better.... I guess this is the reason why LinuxMint forked it as Nemo. I installed Nemo with Raring and side by side Nemo is very efficient. 

But the flip side of installing Nemo is that it only comes with cinnamon... Well I got cinnamon too.

---

### Post by craig10x on 2013-01-31
> **fantab said:**
> Raring Ringtail is already so much better than the final 12.10. I hope it gets even more better... the only downside is nautilus 3.6 the earlier edition was so much better.... I guess this is the reason why LinuxMint forked it as Nemo. I installed Nemo with Raring and side by side Nemo is very efficient. 

But the flip side of installing Nemo is that it only comes with cinnamon... Well I got cinnamon too.

Agree :D
13.04 is still 3 months away from final release and it's already much better then 12.10 final...

Yeah, i do miss the old version of nautilus but find i can manage pretty well with it...reminds me a bit of dolphin file manager in kde where one tends to need to use "right click" more often...but i think i can "live with it" (lol)... ;)

Cinnamon desktop is a great option, as well as "cairo dock session" but i like unity (now that i got use to it) so i just use the "stock" set-up as it were...

I just hope that little "buggy" with the touchpad setting that i have gets straightened out by final release but it's a minor bug compared to the SEVERAL big ones i had in 12.10...

---

### Post by screaminj3sus on 2013-01-31
> **fantab said:**
> Raring Ringtail is already so much better than the final 12.10. I hope it gets even more better... the only downside is nautilus 3.6 the earlier edition was so much better.... I guess this is the reason why LinuxMint forked it as Nemo. I installed Nemo with Raring and side by side Nemo is very efficient. 

But the flip side of installing Nemo is that it only comes with cinnamon... Well I got cinnamon too.

I thought I would dislike nautilus 3.6, but IMO its actually a big improvement. For example I actually loved that they replaced type-to-find with search. At first I thought I would hate this, because the search in nautilus 3.4 never worked for some of my use cases (I have a samba share with a lot of videos, ctrl + f search would never work on that, it would just freeze forever), and type-to-find had its own issues (for example lets say you have a folder names noodles, but are looking for noodles.mkv, with type to find it will go to the folder but no way to go to the file so I have to scroll). with nautilus 3.6 I just start typing and it shows me all the relevant results instantly, even over the network share! The only problem atm is the lack of recursion (which is already fixed in nautilus 3.7 afiak). The only other problem I had with it is that by default the new document template is missing, but thats easy to fix.

It also looks a lot less ugly than nautilus 3.4 did with the ambiance theme, and the symbolic icons look really nice.

---

### Post by fantab on 2013-01-31
yes, the recurssive search is fixed in 3.7 so by next stable release nautilus would have improved...

I have been using 3.6 in Arch (gnome-shell) and the only thing I dearly miss is 'recursive search'... I am using 'gnome-search-tool' to hunt down my files... catfish too is an option... Not a huge issue but I wanted to try 'Nemo' and cinnamon is impressive too...

---

### Post by mc4man on 2013-01-31
> **fantab said:**
> yes, the recurssive search is fixed in 3.7 so by next stable release nautilus would have improved...

recursive search was added back right after 3.6.1 release, Ubuntu could easily enable in nautilus-3.6.x, so far they've chosen not to..

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1077415](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1077415)

---

### Post by Cavsfan on 2013-02-01
When I tried to boot into Raring today, the login screen came up, I entered my password and then it seemed to be starting up.
Then a few seconds later I am looking at the login screen again. This happened over and over.
I got into safemode first choosing network and then root shell. Then I got a bunch of updates and the 8.0-3 kernel but, it still would not boot.

I am going to get another daily iso, disconnect my 1TB USB drive and re-install. Haven't been able to install with the USB drive connected in 3 attempts now.

But, hey we're having fun. :D

---

### Post by craig10x on 2013-02-01
Well, so far 4 days of updates (including 2 kernel updates) and still no smoke coming out of the laptop :D

Actually, so far each time i updated it seems to only help things not make them worse...so i am keeping my fingers crossed...
I hope to make it to the final on April 25th at which time i am going to wipe the dual boot i have with 12.10 and just install 13.04, fresh...

The only bugs i still have is the touchpad pointer speed going back to default (even though i lower it) every time i close that program, so i have to leave it open while in session...

And the other is "tears in video" on quicktime videos at the itune's movie trailer website...no problems with normal flash videos at all...

Hope they get corrected for me by final release...All the "pluses" i outlined in my first post, are a real pleasure with 13.04 over my 12.10 experience...And it's running amazingly stable for a release that is still 3 months away yet...

---

### Post by Cavsfan on 2013-02-02
With my USB drive off Raring 64bit desktop installed pretty fast this time around.

During the installation it still said Ubuntu 12.10 at the lower left.
It seems to be a bit more stable than it was previously.
Installed the “xorg crack pushers” team PPA and installed Nvidia driver version 313.18 and it seems to work well.

When did Gnome Classic become Gnome Fallback?

IMO anything you can do in a terminal is the better choice.
I installed ubuntu-restricted-extras via terminal and the EULA popped up and all went well.
Also got the 3.8.0-4 kernel a day after getting the 3.8.0-3 kernel.
The 3.8.0-3 kernel came on yesterday's daily iso.

---

### Post by screaminj3sus on 2013-02-03
yay I've noticed that another problem that I had with 12.10 doesn't seem to exist in 13.04 :) in 12.10 smplayer was no longer able to inhibit the screensaver for some reason, but somehow it works in 13.04 with the same version of smplayer.

---

### Post by VinDSL on 2013-02-03
> **craig10x said:**
> I hope to make it to the final on April 25th at which time i am going to wipe the dual boot i have with 12.10 and just install 13.04, fresh...
Heh!  I need to do a fresh install, one of these days.  :)

```
vindsl@Zuul:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
**[COLOR="Blue"]Oct 13 2011[/COLOR]**

```

Dern thing just keeps working...

---

### Post by craig10x on 2013-02-04
I probably wouldn't bother, except that at that point (final release) i was figuring on wiping out my dual boot and it would be an easy way to do it (having the installer do it) rather then trying to re-size the partition and deleting the extra version (12.10) from the grub menu...

Also, i recall (from one time i had installed ubuntu while still in beta) that a certain bug i had on it, which got corrected in updates i received, didn't fix the bug on my beta, but when i clean re-installed it, the bug was fixed...

So that does seem to happen sometimes...and since i do have those 2 bugs (touchpad not remembering the setting i change it to and the tearing of quicktime videos) if they do get corrected, i may not get the benefit of it unless i clean install...

---

### Post by tdockery97 on 2013-02-05
So far I'm having a great experience with 13.04.  I don't normally watch quicktime videos, but after reading the post above by craig10x regarding quicktime video tearing I thought I'd give that a test.  I've now tried several with no issues whatsoever.  I'm running the AMD ATI Radeon 6310 graphics using the proprietary driver installed through additional drivers.

---

### Post by craig10x on 2013-02-05
> **tdockery97 said:**
> So far I'm having a great experience with 13.04.  I don't normally watch quicktime videos, but after reading the post above by craig10x regarding quicktime video tearing I thought I'd give that a test.  I've now tried several with no issues whatsoever.  I'm running the AMD ATI Radeon 6310 graphics using the proprietary driver installed through additional drivers.

Thanks for checking that...it could be just on my particular hardware...though interestingly enough, on live session of 13.04 the quicktime videos played fine...perhaps i got some kind of corruption in that while it was being installed...another reason i will clean install when the final comes out...I have an I3 Core Intel processor with Intel Graphics...never had a problem with quicktime on ubuntu with this computer before...

In the case of intel, there are no proprietary drivers offered because the open source and proprietary are the same (intel is very linux friendly in that regard)...

Just curious, could you check the "touchpad" bug i am having to see if you get that too?  When i go to the mouse settings and lower the pointer speed, if i close that window, it appears to go back to the default position...

Have to say, that otherwise, my experience with 13.04 has been great also...and i have noted a LOT of improvements over my 12.10 install... :)

---

### Post by tdockery97 on 2013-02-05
Just tried changing the pointer speed in the touchpad settings, and it doesn't appear to stick after closing the settings.

Thanks for having me do that craig10x.  I didn't realize that there is an option in system settings to turn the touchpad off.  I had been using a startup script to do that.

---

### Post by craig10x on 2013-02-05
You are very welcome...also nice seeing you over here at the ubuntu forums ):P

That little bug in the touchpad seems to be experienced by others here as well, so i guess it is a common bug...hopefully, it will get fixed by the final...

My "work around" for now is to just leave that window open while i am in session...each morning when i boot up, i just slide it down to the place i like it...

---

### Post by tdockery97 on 2013-02-05
I only use my laptop at home with a mouse, so it doesn't really affect me.  I do hope that they get it fixed as most laptop users probably use their touchpads.

By the way craig10x, I don't know if it is something you do or would use, but the dodge windows app that was written for 12.04/12.10 also works in 13.04.

---

### Post by jerrylamos on 2013-02-05
> **tdockery97 said:**
> I only use my laptop at home with a mouse, so it doesn't really affect me.  I do hope that they get it fixed as most laptop users probably use their touchpads.

I touch type mostly, so my hands are all over the keyboard.  The "touchpads" are forever firing off and screwing things up, so I use wireless mice on my notebooks & netbook.  The "touchpad" is tuned off.

Now on my tablets, not much choice, use screen fingerprints instead of mice, and do have keyboard attached much of the time.

---

### Post by MarcoDePollo on 2013-02-06
I've running kubuntu-raring since early January, primarily as a test to begin with but I was so impressed it quickly turned out to be my primary OS.

Sound is working beautifully. Previously I had to wait at least five minutes or so, before the sounddrivers decided to initialize the hardware. Now, it is up and running by the time KDE loads.

Graphics is another area that has been bothering me. Being blessed with both integrated graphics and discrete graphics, this has been quite problematic for me, since fglrx had trouble recognizing the discrete Radeon-chip so I had to stick with the Intel graphics. Now, some how my Intel graphics are disabled by the kernel and fglrx install and run without problems.

---

### Post by OrangeCrate on 2013-02-06
Though I used to be involved in the development cycles, for the past few releases, I really haven't had much time. However, I downloaded and installed today's daily for Xubuntu to take a look.

I set it up to my preferences, and ran it through it's paces, to note what I needed to keep an eye on. Imagine my surprise, that everything worked. I know that will change, but, at least for today, I'm really impressed.

---

### Post by OrangeCrate on 2013-02-06
> **jerrylamos said:**
> I touch type mostly, so my hands are all over the keyboard.  **The "touchpads" are forever firing off and screwing things up, so I use wireless mice on my notebooks & netbook.  The "touchpad" is tuned off.**

Now on my tablets, not much choice, use screen fingerprints instead of mice, and do have keyboard attached much of the time.

Just thinking out loud...

I use Thinkpads, and I also use a mini-mouse most of the time. Like you, I turn off the touchpad (but I leave the TrackPoint live). It would be a worthless poll, and a waste of bandwidth, but, I wonder how many people actually turn off their touchpads, and use a mouse on their laptops. My experience with touchpads leads me to believe that many more do, than one might think.

---

### Post by Cavsfan on 2013-02-06
Just made a blood test appointment and printed out the document on my HP Printer. It printed out well. ;)

---

### Post by mcellius on 2013-02-06
> ... I wonder how many people actually turn off their touchpads, and use a  mouse on their laptops. My experience with touchpads leads me to believe  that many more do, than one might think.

Yep, that's exactly what I do.  Especially when the laptop is sitting on my lap, it's too easy to accidentally hit the touchpad when I'm typing so I prefer to keep it off.  I'm with you in thinking that lots of people do this.

---

### Post by craig10x on 2013-02-07
I filed a "bug report" on launchpad about the problem i mentioned in my initial post about the touchpad pointer speed not locking in when you change it from the default...anyone else who has observed it, is welcome to add to my report....seems odd that no else has appeared to have reported it to them...

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1118719](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1118719)

I would really appreciate others who have observed this bug to report it on my bug report at launchpad, i think it would look better if more would mention it to them...

Thanks...

---

### Post by Rob Sayer on 2013-03-10
I installed kubuntu raring a few days ago on my acer netbook because it has the notorious cedarview gpu archtecture, and I read on phoronix that the 3.7 kernel incorporated the drivers.  Had single boot ubuntu based mint 13 kde on it because mint uses a 6 month old ubuntu 12.04 version and comes with kernel 3.2xx.  You don't have to manually compile an older kernel/header version and hold it.  Synaptic does that for you.

However, that meant other problems.  The kernel version doesn't work properly with the HDd controller.  It only gets 13-14Mb/s transfer at most with a usb HD.

I was prepared to live with that until the official release, but then I started to suspect the wireless controller was having odd problems too.  So I figured what the hell.  

One thing I'll tell you.  I'd *never* install alpha Windows.  Not in a million years.

I didn't use a daily build, I just installed with the live DVD version from usb stick.  That was pretty clunky until I updated it.  But so far it runs well.  Probably better than 12,04 based mint with limited update capability.  Touch wood.  The video is definitely faster.  Not by an order of magnitude but it's quite noticeable.

Of course, it's kubuntu, and I've found kde to be the most stable of all 5 desktop shells I've tried.  I suspect that helps.

---

### Post by jerrylamos on 2013-03-11
> **mcellius said:**
> Yep, that's exactly what I do.  Especially when the laptop is sitting on my lap, it's too easy to accidentally hit the touchpad when I'm typing so I prefer to keep it off.  I'm with you in thinking that lots of people do this.
Touchpad off.  On netbook, notebook.  I touch type with some misses on keypresses and the touchpad makes the screen go nuts.  A wireless USB mouse works just fine, thanks.  Oh, when I use the touchpad on my son or daughters Apple it's pretty clumsy.

---

### Post by Kehribar on 2013-04-01
I have been using Ubuntu on my Fujitsu Siemens Amilo Pi 1505 for the last 3.5 years.  Yesterday I upgraded to 13.04 and the system seems to be smoother than 12.10.  As a pleasant surprise, there seems to be some improvement in battery consumption as well.  Once in a while a popup message indicates an internal error, and it is reported to the center.  Other than that, and so far ( :P ) there don't seem to be any major problems.  I am certainly pleased to see improvements in Ubuntu, and I would like to see software companies taking linux more seriously and not giving linux users the hind tit.

---

### Post by Redalien0304 on 2013-04-02
Installed Ubuntu 13.04 Raring, a few Bumps but nothing to bad. 1st tried cinnamon stable, just hangs on log screen into cinnamon desktop. Solved by Installing Cinnamon Daily for 13.04. Also the Kernel 3.8.0-16 hangs halfway through install. Rebooted, installed via terminal sudo apt-get update, sudo apt-get upgrade.

---

### Post by monkeybrain2012 on 2013-04-02
> **craig10x said:**
> 

1) When installing ubuntu restricted extras, the microsoft fonts license agreement did not come up...everything else got installed except for those fonts...ended up having to do it in the terminal where the agreement DID come up...


I wish this is the expected behaviour. I never understood why they need to put Microsoft's fonts in restricted extras in the first place. Since it requires agreeing to MS's EULA it should be separate from restricted extras. I don't want it so I always skip the EULA once I became more experienced, but when I started out with Ubuntu I thought the installation of restricted extras would stop if I didn't agree to the EULA and always ended up having to remove it later.

---

### Post by jerrylamos on 2013-04-06
> **OrangeCrate said:**
> Just thinking out loud...

I use Thinkpads, and I also use a mini-mouse most of the time. Like you, I turn off the touchpad (but I leave the TrackPoint live). It would be a worthless poll, and a waste of bandwidth, but, I wonder how many people actually turn off their touchpads, and use a mouse on their laptops. My experience with touchpads leads me to believe that many more do, than one might think.
Just got an Acer C7 Chromebook with touchpad.  One finger, two finger scroll, tap or hold, etc.  Don't like the touchpad at all. Slow compared to a mouse so I plugged in a wireless mouse.  Only disconcerting thing, the display is so fast scrolling the whole screen jumps in time with the slight detents on the mouse scroll wheel.

The touchpad is slightly recessed so I don't accidentally bump it very often as I use the mouse and touch type.

---

### Post by Sylslay on 2013-04-07
Pionter speed - usb mouse is not working ok (change speed every day and is very lagy after 3-5min from boot).
Xubuntu 13.04, 64 bit , 
Samsung R730 (windows 7 and xface fedora 18 works ok , with full speed mouse),

No work around found,,,, sa far. (4 weeks on 13.04)
Waitning for great upgrade (turned of fiew services at startr or turned on full performance on cpu, nothing helps , very slow, but when I liesten some music or video in backround - os is faster and not that lagy)

Apart form slow mouse anything elese is working ok in Xubuntut 13.04 - 64 bit

Seems to be better on latest kernel, no perfect yet (or normal).
3.8.0-17-generic #27-Ubuntu SMP Sun Apr 7 19:39:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Sorry to everyone.
Found tha slow mause was HARDWERE ISSUE.
WRONG CONFIG OF RAM , OR LOOSE CONNECTION OR SOME THING WITH DUAL CHANNEL ASYNCHRON... (ON FEDORA AFTER WHILE FOUND THE SAME PROBLEM),
WONDER WHY WINDOSE-MOUSE WAS OK, MEABY WINDOWS IS SLOW ANYWAY,
JUST GOT THIS SECOND HAND LAPOTOP FOR FIEW WEEKS, AND I DID DEEP CLEANING - CHECKED ALL SCREWS...

---

### Post by JonPaul on 2013-04-08
Hey @jerrylamos - do you wear that helmet cos you get so many crashes!!! :lolflag:

---

### Post by craig10x on 2013-04-08
also @jerrylamos are you telling me that because i have been running 13.04 development for 2 months now, i have a FAT UBUNTU?
what am i suppose to do, put it on a "diet" ???? :lolflag:

---

### Post by ubume2 on 2013-04-08
Installed Beta 2 on my Desktop today.  Runs better than 12.10. Launcher hides and reveals properly  as it does in 12.04.  Seems to be snappier, faster than 12.10. So far so good.  Hope updates don't undo these improvements. I am avoiding installing any of those tweak tools.

---

### Post by jerrylamos on 2013-04-09
> **JonPaul said:**
> Hey @jerrylamos - do you wear that helmet cos you get so many crashes!!! :lolflag:

Good point.  Actually it's a bicycle helmet on a trip to Australia, we live in the U.S.  And yes I crash bicycling and skiing.

Latest crash was update from 3.8.0-16 to 3.8.0-17.  After the update, still running, screen kept greying out.  Then  would not boot again.  At all.  So I re-installed.

Presently have Raring amd64 running O.K. (for a Beta) on 10" netbook with 20" external screen, a 15" notebook, and raring i386 on a tower.

Having some problems booting USB hard drive on the notebook.  I don't know if it is a hard drive problem, a USB case problem, a Raring problem, or me.

---

### Post by Sylslay on 2013-04-10
Hi Jerrylamos , did You try plop boot manager??? (workaround)

---

### Post by jerrylamos on 2013-04-11
> **Sylslay said:**
> Hi Jerrylamos , did You try plop boot manager??? (workaround)
Nope, don't know that one.  Any pointers other than google?

---

### Post by rsrocha on 2013-04-12
I installed yesterdays daily build and it feels solid and stable. Unity feels slower than 12.04 and 12.10. The only thing i need getting used to is the new replacement for gwibber.

Also i dont have any twitter account option in online accounts.

---

### Post by moenderman on 2013-04-18
Hi there, 
I also moved on to 13.04 yesterday hoping that my Wifi issues will be fixed with the new kernel. Unfortunately I have the same issue: My Wifi connection first gets perfectly established and works fine. Then after a random period of time the connection simply gets lost. I then do restart Wifi via the Wifi button on my notebook and everything is working properly. 

I have already read something about that problem in 12.04 and 12.10. The Wifi adapter falls into some "deep sleep" and does not wake up again. I would like to bring that issue to some developer so they might fix it until the release candidate will be published. As Wifi is one of the most important items I guess this bug should be highly prioritized, shouldn't it?

Can someone tell me what I can do to shed some light on my system. The description on the ubunut bug reporting sites are honestly way to flamboyant I think. 

Or does maybe anyone knows an easy fix?

Thanks a lot!

---

### Post by VinDSL on 2013-04-18
> **moenderman said:**
> My Wifi connection first gets perfectly established and works fine. Then after a random period of time the connection simply gets lost[...]

Can someone tell me what I can do to shed some light on my system.
Well...

The only "connection" problems I've experienced, over the years, has always been because of NM (network mangler).

Tricks n' tips:  You cannot install/run 2 network managers at the same time. ;)

Every time I've had enough of it --  deleted NM -- and installed WiCD -- WiCD has fixed the problem(s).

Of course, we're supposed to be testing NM, not WiCD.  So, I try NM every week or so, and eventually it works again (only to fail again later).

It's a teeter-totter game we play, here in +1...  LoL!  :D

---

### Post by IdoSC on 2013-04-19
I love the dash in this version, works so much better and faster than 12.10. But Nautilus 3.6 is atrocious...I can't even use the backspace button to go up one level.

---

### Post by tdockery97 on 2013-04-19
YouTube blogger quidsup has a fix for that in this video:  [https://www.youtube.com/watch?v=2Birudyo3fs](https://www.youtube.com/watch?v=2Birudyo3fs)

---

