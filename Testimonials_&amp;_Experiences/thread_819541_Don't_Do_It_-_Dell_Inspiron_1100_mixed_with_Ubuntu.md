---
title: "Don't Do It - Dell Inspiron 1100 mixed with Ubuntu 8.04 = Nasty Hang-over"
date: 2008-06-05
forum: Testimonials &amp; Experiences
---

### Post by steppedup on 2008-06-05
Let me plainly say this - if you have an Inspiron 1100, do NOT install Ubuntu 8.04 Hardy Heron.  Let me repeat - do not install it as of the date of this posting - 6/03/2008.

[INDENT][B][I]
Edit as of 6/12/2008:  [http://ubuntuforums.org/showthread.php?t=822192](http://ubuntuforums.org/showthread.php?t=822192) - is a complete A to Z of how to install Ubuntu 7.10 on a Dell Inspiron 1100....successfully and happily.  Back to the post as originally written....
[/I][/B][/INDENT]

**I do not use these words lightly **- Hardy Heron sucks.  Ubuntu 8.04 sucks.  Kubuntu blows (yes, tried that variety as well - all same issues).  **Before you flame on, Johnny**, - hear me out.  



The good news - I'm in the process of finishing a very quick installation of Gutsy Gibbon 7.10.  Successfully and happily. 

The background - I'm a relative newbie at Linux (understand the general format/ packaging system/ etc - but don't have the command lines memorized).

This was on my fiancee's laptop.  She keeps borking her Windows XP box with MyViralSpace.  She only uses her laptop to plug in USB devices (camera, usb flash stick), check the internet, and check email.  

A perfect candidate for ole Mr. Hardy Heron.  

Um, no.  


Problems:  graphics drivers that don't work, no USB unplug and replay, and inadequate wireless support.  So - can't see anything on the screen, can't access usb memory repeatedly - and no internet access.  


**The graphics** for the Inspiron 1100 video card do not work (after reboot, Grub runs - and then presto - David Blaine has made the operating system disappear!)  And yes - I upgraded to the A32 bios, set memory to 8 MB, and did all of the other work-arounds (disable splash screen, etc) that every other poor Inspiron 1100 owner has attempted and uploaded to this thing we call the internet.  

Every time I rebooted, I would be presented with a black screen.  Computer's on - but no one's home.  

I would run reboot and hit ESC at Grub - and then run Xfix.  It would run, and I'd be able to continue the reboot - with the screen working.  Until I rebooted. Every single time.  Over and over. 

Kind of like a very nasty 'Ground Hogs Day' with Bill Murray playing myself offing himself repeatedly with an Ubuntued Dell Inspiron 1100.  

[INDENT]Drop Inspiron 1100 into bathtub with him - check.  
[/INDENT]
[INDENT]Eat screws from disassembled Inspiron 1100 - check. [/INDENT] 

[INDENT]Cut Ubuntu install CDs into Chinese throwing stars, spend all day training the old drunk on the side of the road how to have Ninja-like throwing ability, and then try to take away his MadDog 20/20 - check.  [/INDENT] 


Let's move onto **USB problems **with Ubuntu 8.04 (Hardy Heron).

Ok - if Steve Jobs or Bill Gates stuck their tongue in your ear, and then wouldn't pull it out, would that be disturbing?  

[INDENT](By the way, you're welcome for the Jobs and Gates' mental picture above.  Consider it penance for the hours I spent on the Hardy "the Hard to Use" Heron system (TM)."[/INDENT]

Because that's what it felt like being unable to unmount multiple USB flash drives.  And then to find out that's officially a 'bug.'

Come on folks - that's not a bug.  That's the Ebola Virus!  

Hardy Heron is supposed to be the Linux that's easy to use.  It's supposed to be the One!  

But USB - that everpresent, ubiquitious technology that has brought massive photo collections of kegger hand-stands to the masses doesn't work?

And yes, again, I did all the work-arounds.  Mount -o force, blah, blah, blah.

Being able to not use USB memory with all of our collective memories embedded on them is a slightly negative Factor along the Fiancee Continuum - which drives the secondary computer market in my household.


**Moving onto dis-connectivity.**  

Why the heck wouldn't they put ndiswrapper onto the install CD of Hardy Heron?  Especially with USB not working reliably? And you know that you don't have good wireless drivers because (and here I quote all of you misbegotten fan boys) 'linux is locked out from the propietary drivers by the mean, evil hardware manufacturer's!'

Get over it!  Include ndiswrapper and set that to be the default for all wireless networking!  Easy solution!

But I digress....  So the default drivers for the WPC54G wireless card aren't working.

The work-around involves either getting the ndiswrapper or the b43 chipset package to your computer.  But with no connectivity and no USB, how to do that?  Sure, wired works - assuming you have an RJ-45 cable that hasn't disappeared into the darkest depths of the garage.

And sure you can burn the files to CD - but by the time you realize all of that - it's 1 AM.  And unlike you're soon-to-be-flaming-my-a$$'s city, Bremerton, Washington does not carry CD's that you can write data to at 7'11's.

I know.  I actually went and looked in a last chance of desperation.  I found they also don't sell RJ-45.

**But they do sell Coors Light!!!  (You may mock, but it's always the first beer that's gone at a party!)**

Perhaps the Coors Light did not assist in my subsequent troubleshooting.  But it sure felt good.


**And in a moment of slightly inebriated genius**, I downloaded the alt-install of Gutsy Gibbon.

Burned it to CD.  Installed it.

It's online right now happily updating all of the security updates.

So, with the Dell Inspiron 1100 (and pretty much any other computer that uses wireless or USB), gut it out with Gutsy Gibbons - Ubuntu 7.10.


[INDENT]*TM:  Hardy "the-Hard-To-Use" Heron System is a trademark of SteppedOnIt Productions, Incorporated.  All infringements on this trademark will be considered as fully allowable only within the non-existent state of Daenmark.  All rights incorporated within the nebulous regions of the ether between frontal and suborbital regions.  Any disagreements shall be handled by small men with big sticks.*[/INDENT]

---

### Post by gumpish on 2008-06-10
Heh.

Yes, I also have tried 8.04 with an Inspiron 1100, and I also had the blank screen after installation.

Also if I suspend from the live CD when the system comes back up, it's blank again, and you can't even get to the other TTYs. (In comparison, Debian 4 and Xfce4 are able to resume from suspend properly on this same machine.)

Looks like this model is being left behind by Ubuntu. I think I'll see how Gutsy does.

---

### Post by stairwayoflight on 2008-06-11
Linux distributors have to make a choice about where they stand in terms of new features, drivers, and other software. Distributions such as Debian tend to be more conservative in their choices. But it also means that if support for new hardware has been released, it will appear in the stable version much later than eg. Ubuntu.

Ubuntu's philosophy is to try and support newer software a little sooner. However, there are edge cases where support for hardware may break. But understand, laptop vendors will extensively test hardware and drivers for windows (or in Apple's case, Mac OS), while Linux developers working hard (often for no money!) to support hardware they don't have in the first place.

Please show a little respect for these people. For Linux to have come this far is a miracle. Do something useful, like researching the actual nature of the problem, and filing bug reports. Maybe donate or lend the hardware in question to a developer. But please, if you can't contribute in any way then at least be patient. Your hardware support will in all likelihood be fixed soon.

---

### Post by pcjason on 2008-06-11
I had a very similar experience with my Inspiron 1100.  I enjoyed using 7.10 on it, but 8.04 was just painful.  I made the decision to move on to a different distribution for the time being.  I enjoy messing around in linux, but at the end of the day I just want a stable distribution.  I have been using Mandriva One and have found it very enjoyable.  Good luck with with whatever you choose!

---

### Post by Aeroangel on 2008-06-12
My father also owns a Dell Inspiron 1100, and was unable to install ubuntu 8.04. I understand that it is a lot of hard work to make an operating system, but I was disappointed. I didn't know that the dell inspiron 1100 would be able to run 7.10, so I will try that out next- thanks for the info.

---

### Post by steppedup on 2008-06-12
Stairwayofdarkness:

I have tons of respect for the Ubuntu community, and much patience.  Development does take time.

I don't have patience for people who flame in posts - and definitely don't have patience for software releases that break previous functionality. 

To wit:

[INDENT]> Linux distributors have to make a choice about where they stand in terms of new features, drivers, and other software.    [/INDENT]

Um - what is new about a Dell Inspiron 1100?  What is new about USB support?

[INDENT]> Do something useful, like researching the actual nature of the problem, and filing bug reports. [/INDENT]

How many bug reports need to be filled out for the same issue?  Like I pointed out in my post, it's a known bug:

[INDENT]> Because that's what it felt like being unable to unmount multiple USB flash drives. And then to find out that's **officially a 'bug.'**

Come on folks - that's not a bug. That's the Ebola Virus! [/INDENT]

Finally, regarding your condescending tone.  Specifically:
[INDENT]> But please, if you can't contribute in any way then at least be patient.[/INDENT]

If you had taken the time to look me up, you would have seen I've made a total of 4 posts.  Unlike your 106 posts - like Ali G says - "Respect."

But...my 4 posts make it very easy to see the very first post that pops up.  [  A post in which I provided a complete compilation of how to install Ubuntu 7.10 on a Dell Inspiron 1100. ]("http://ubuntuforums.org/showthread.php?p=5139418#post5139418")   A post that took more than a few hours to compile after fully testing everything in the post.

Instead of wasting all of our time with the condenscending tone, why not put your time to good use?  

Since you're taking requests, **can we get a complete A to Z guide on installing Ubuntu 8.04 on a Dell Inspiron 1100?**  Like I provided for 7.10?

Because I would definitely read that post - otherwise don't waste my time any further.

Think I'll have some popcorn while waiting....:popcorn:

---

### Post by mimada on 2008-06-15
I just installed Hardy on my wife's Inspiron 1100 yesterday. Everything seemed okay until I tried to update Hardy (via NIC). It kept freezing until I booted as root in recovery mode and completed the update in terminal mode. When I rebooted, I got the blank black screen.

I was able to recover video by replacing the xorg.conf file (/etc/X11) with the one posted [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/179503") by Carl Hoffman. I suspect I may have been able to restore video by using one of the backed up xorg.conf files I found in the X11 directory, post update, but I haven't tested this.

My wife's Inspiron doesn't have built in wireless so I bought her a Linksys PCMCIA card a while ago. I got it to work after tooling around with it for a bit. The rest of the installation was a bunch of tweaks to get everything looking good.

---

### Post by msrinath80 on 2008-06-15
I would recommend that folks with the Inspiron 1100 try Fedora 9. It might be worth a try.

---

### Post by ron4x4 on 2008-06-16
After installing 8.04 on my Inspiron 1100 the USB completely died. I have looked and looked. I think I am going to rebuild,it from scratch and put 7.10 back on it and Just remember not do any update until there is a viable Fix or the Lappy Dies. I really don't understand that the USB drivers are a bug. As a rule from my years of coding, you always make drivers backward compatable. Maybe I'll try to build or find a fix before I rebuild. I really prefer to be up to-date.

---

### Post by carljm on 2008-07-23
I just installed Hardy on a Dell Inspiron 1100 upgraded to A32 BIOS.  I had the blank screen problem initially, but I fixed that by booting into recovery mode.  First I dropped to a root prompt and edited /boot/grub/menu.lst to remove "quiet splash" from the end of the boot options.  Then I rebooted, went back into recovery mode, and chose the option to "fix xorg configuration" (don't remember exactly how it was labeled).  It did a bit of autodetection of my video hardware, then I chose "resume normal boot" and it booted up just great.  It's sitting here now updating 236 packages, we'll see if things are still OK after the upgrade...

Not having any trouble with USB drives.

Wireless, of course, all depends on your choice of PCMCIA card, since the 1100 doesn't have internal wireless.

---

### Post by phytech222 on 2008-08-05
hardy installed fine no screen or usb probs, well i still can't get my wireless card to work, just shaky movies until i started using gnome mplayer

---

### Post by reebnek on 2008-08-19
Have tested and confirmed use of Hardy 8.04 on an Inspiron 1100.  I followed oilgeek's direction from this link.
[http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/dell-inspiron-1100-which-distro-604288/](http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/dell-inspiron-1100-which-distro-604288/)
STEPS:
1 upgrade the 1100 bios to A32
2 change the video shared memory in the bios from 1 to 8 meg
3 do Ubuntu 7.10 install in "video safe mode" - will use VESA driver
4 perform all updated and patches
5 add the video card info found in this reply in /etc/X11/xorg.conf
6 add the screen info found in this reply in /etc/X11/xorg.conf
7 sudo aptitude install 915resolution
8 reboot and rock out with Ubuntu 7.10! :) Now 8.04!

---

### Post by syg00 on 2008-10-14
And if you are planning on going to 8.10, make sure you keep a copy of xorg.conf.
PITA if you don't.

Works o.k.(-ish); had to turn off effects before I could get to read anything on a message box, or use the terminal.

---

### Post by sparvik on 2008-10-14
I installed 8.04. something on my 1100 with the A32 bios.  Upon first reboot after install I had a blank screen but I restarted X (ctrl+alt+bckspc) and it has loaded fine ever since. Well X has ran fine that is. It didn't recongnize my wacom Graphire 2, but I am sure that I could fix that ease enough. But the real anoying thing is the S-Video out.  I have had to rewrite my xorg.conf file probaly 20 times. I have followed directions from 15+ forums but I can't even get it to recongnize that my video card even has a S-Video out. Finaly I down graded to 7. something and I couldn't even get the display on the laptop to work. I love everything else about Ubuntu but I can't ditch the XP until I get Video out working.

Oh yeah on a after thought, the version of Hardy I downloaded has had no problems with USB and came with nsdiwrapper installed by default.
(ubuntu-8.04.1-desktop-i386.iso)

---

### Post by Sef on 2008-10-14
Moved to Testimonials and Experiences.

---

### Post by spawn. on 2008-10-14
Dell is horrible.

---

### Post by armandh on 2008-10-14
some hardware presents no problems
some hardware just sucks

Ubuntu is built on previous experience.
Given yours,
I am happy the only problem with my wife's laptop......
is the dreaded BCM43xx wlan.

---

### Post by jbrax on 2008-10-20
Ubuntu-8.04 works fine with Dell Inspiron 1100

[B]A to Z guide on installing Ubuntu 8.04 on a Dell Inspiron 1100 is here!
There are three sources of errors that you have to fix: BIOS, splash-screen and X11-configuration.[/B] 

1. Upgrade your laptops bios to A32
   HOWTO do it with bootable ISO without Windows: 
   [http://www.geocities.com/randomnumbergenerator2001/](http://www.geocities.com/randomnumbergenerator2001/)

2. Go to BIOS and change the video memory setting from 1MB to 8MB

3. Install Ubuntu-8.04 in text mode (I used Ubuntu-8.04 DVD but any installation media should work)

4. After installation press Esc when booting and select recovery option to get into root terminal
   Edit two files: /boot/grub/menu.lst and /etc/X11/xorg.conf
   In menu.lst change default from splash to nosplash. Do not uncomment the line. This fixes the "blank screen after reboot" error.  
   In xorg.conf add sync and resolution info. This fixes "only 800x600 resolution" error. 

```
   Edit line 89 in file: /boot/grub/menu.lst
   vim +89 /boot/grub/menu.lst
   Change 
   # defoptions=quiet splash
   to read: 
   # defoptions=vga=773 quiet nosplash
   Do not remove the #-marks!
   When modified here this change persists after kernel upgrades!
```

   Edix xorg.conf 
   vim /etc/X11/xorg.conf
   after Section InputDevice change the rest of the file into this:

```
Section "Device"
        Identifier "Intel 82845G/GL"
        Driver "i810"
        BusID "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier "Internal monitor"
        Option "DPMS"
        HorizSync 28-80
        VertRefresh 43-60
EndSection

Section "Monitor"
        Identifier "External Monitor"
        Option "DPMS"
        HorizSync 28-80
        VertRefresh 43-60
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device "Intel 82845G/GL"
        Monitor "Internal monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth 16
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection
```

   Exit and continue booting

5. Update ja upgrade the system

If you have already installed Ubuntu-8.04 and just want to fix the issues here's how to edit 

1. Open Terminal
2. Type: gksudo gedit /boot/grub/menu.lst Do the editing, save and quit.
3. Type: gksudo gedit /etc/X11/xorg.conf Do the editing, save and quit.

---

### Post by lowbot on 2008-11-23
How were you guys able to install the new version of the Dell bios after linux is installed? It looks like the package they offer at dell.com is strictly win32. Do I have to install windows on here just to update the bios?

---

### Post by jbrax on 2008-11-24
> **lowbot said:**
> How were you guys able to install the new version of the Dell bios after linux is installed? It looks like the package they offer at dell.com is strictly win32. Do I have to install windows on here just to update the bios?

You don't need windows to update the bios. These instructions are copied from the URL mentioned above [http://www.geocities.com/randomnumbergenerator2001/]("http://www.geocities.com/randomnumbergenerator2001/") 

1. Download the supplied [CD Image]("http://www.geocities.com/randomnumbergenerator2001/bootcd_A32_1100.zip") and unzip it.
2. Burn to CD (as an image file!) using your favourite CD burning program. You can easily use cdrecord like this with a 2.6 kernel:

    cdrecord --dev=/dev/hda /path/to/image/bootcd_A32_1100.iso

Or like this for a 2.4 kernel:

    cdrecord --dev=0,0,0 /path/to/image/bootcd_A32_1100.iso

3. Reboot, press F12 at the start of the boot process and select CD boot. At the "a:\>" prompt, enter:

    I1100A32

The BIOS update will start and do the work for you.

---

### Post by -=mad-dog=- on 2008-12-06
I know this is thread is a bit old but I wanted to put my two cents in. I installed 8.04 back when it first came out from a fresh install. I of coarse had to make sure my bios was up to date, already done before hand, and set the video memory to 8mb, done before as well. Install was a bit fed up, woot 800x600. Other than that, it ran GREAT!!! Installed the 915 drivers and usb worked out of the box and so did my wireless card. I have since then had to go back to xp because of school but I am now trying to get 8.10 installed and im loving it....yea right. However, with all due respect to all of you who have posted your hard times, the blam can not be placed entirely on Ubuntu or the devs that work on it. Dell is a lot to blame here for making a ;)WONDERFULL;) bios. To be honest, I wish I could just take their bios and !!!FIX!!! it. However, I don't exactly know how to decompile the bios bin and the recompile it.

---

### Post by swindelltyler on 2008-12-09
I do not know what I am doing wrong here but I used that code in my xorg.conf and it loads in low graphics mode saying EE: no device detected, or something like that, now changing the word i810 to vesa will make it load, except it is vesa then. I am getting tired of this vesa crap, it is real slow and evertime I scroll in Firefox, it makes my music skip. Please help me figure out why it is doing this. Yes I have an inspiron 1100.



I am using Ubuntu 8.10 gnome, switching to KDE as soon as I can.

---

### Post by sidral on 2008-12-26
I had the same problems you described when trying to install 8.04 and 8.10 in my old 1100... Tried all but nothing worked... 

But aynway, I will try with 7.04.

After all, congratulations for your amazing and ironic post.

---

### Post by wolfen69 on 2008-12-26
> **sidral said:**
> I had the same problems you described when trying to install 8.04 and 8.10 in my old 1100... Tried all but nothing worked... 

But aynway, I will try with 7.04.

After all, congratulations for your amazing and ironic post.

why not try a different distro instead of ubuntu 7.04 that is not even supported any more? ubuntu is not the only good distro. a learned a while ago that being stubborn about which OS i want will get you nowhere. some computers just require a different approach.

---

### Post by marcf3998 on 2008-12-26
Being new to Linux and Ubuntu this post made my day, you see I have a 1100! I thought it was just my laptop trying to die or my lack of knowledge. My 1100 has survived a violent car wreck that blew the battery and DVD out of the body :( after if flew from the back seat and took a chunk out of the dash. I put it all back together and it works but I expect it to die someday. I admit it sold me on Dell, d@mn its a tough little bugger.

I have 8.04 and get the hang time when its booting sometimes, crtl alt backspace usually pops it onto the log in. Sadly I have tried several flavors of Linux and like Ubuntu best so far, Xubuntu needs tinkering every time to keep running on my 1100. Puppy Linux starts everytime but has a 800x640 screen max.

Thanks to all for the information in this forum, it has been loads of help.

---

### Post by stalkingwolf on 2008-12-28
I recently sold a Dell C400 with basically the same specs with 8.04
installed and working fine  on it.  I have a Toshiba Tecra 8200
that also has 8.04 running on it.  I had to configure gtk to get the resolution I wanted but thats it ( I dont have the commands and procedures at hand just now.  I will post them this afternoon.)

I have yet to have a system that with a little work would not work with Ubuntu.

If you need a little more incentive to make it work, try this:

[http://yro.slashdot.org/article.pl?sid=08%2F12%2F27%2F2010244&from=rss]("http://yro.slashdot.org/article.pl?sid=08%2F12%2F27%2F2010244&from=rss")

---

### Post by conolo on 2009-05-24
I succeded, but only after adding a small change.
 The contribution from jbrax is enormously valuable. Thank you and many kudos to you, jbrax.
 

 I did everything jbrax said to do, but I would still get a blank screen on startup. But by luck I hit upon a another place where "no" had to be inserted in front of "splash".
 

 In /boot/grub/menu.lst you'll find a section that resembles this one, which I copied  from my Ubuntu 6.06 install on my desk top computer. Again, yours will be different, so don't simply paste mine into your file.
 

 

 title		Ubuntu, kernel 2.6.15-53-386
 root		(hd0,2)
 kernel		/boot/vmlinuz-2.6.15-53-386 root=/dev/hda3 ro quiet splash
 initrd		/boot/initrd.img-2.6.15-53-386
 savedefault
 boot
 [COLOR=Black]
[/COLOR] 
 [COLOR=Black]In the 8.04 menu.lst, I had to change the line which is similar to this line:[/COLOR]
 [COLOR=Blue]kernel		/boot/vmlinuz-2.6.15-53-386 root=/dev/hda3 ro quiet splash[/COLOR]
 to one which is similar to this one:
 [COLOR=Blue]kernel		/boot/vmlinuz-2.6.15-53-386 root=/dev/hda3 ro quiet nosplash[/COLOR]
 by adding the letters "[COLOR=Blue]no[/COLOR]"
 Again, yours will be different, so don't simply paste mine into your file.
  My apologies for not providing the exact text that you'll see on an Ubuntu 8.04 install on a Dell Inspiron 1100 laptop. That's my father's computer and I may not have access to it for a while. I figured  that the immediate needs of others overides my desire to be more precise.

---

### Post by conolo on 2009-05-24
Many thanks jbrax !


I also had to make an additional change to /boot/grub/menu.lst.



In the 8.04 menu.lst file, I had to change the line which is similar to this line:
 kernel		/boot/vmlinuz-2.6.15-53-386 root=/dev/hda3 ro quiet splash


 to one which is similar to this one:
 kernel		/boot/vmlinuz-2.6.15-53-386 root=/dev/hda3 ro quiet nosplash
 by adding the letters"no" before "splash"

Apologies for not having the exact line. After fixing the line in my father's laptop, I no longer have access to it. So I had to use the lines from my Ubuntu 6.06 install as examples for the lines in 8.04..

---

### Post by johanzebin on 2011-01-30
Thanks for the thread, and especially to jbrax!

I just installed Xubuntu 10.4 LTS on an Inspiron 1100 with 15" monitor, which first had the "random freezing" problem.
After updating the BIOS to A32, the automatic process of xorg-configuration failed miserably and only showed a black screen after bootup.

I then edited one line in **/etc/default/grub** to:
```
GRUB_CMDLINE_LINUX_DEFAULT="nosplash i915.modeset=1"
```

It now seems to work without any problems ):P.

---

