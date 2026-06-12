---
title: "System76 Drivers on Mint"
date: 2008-05-21
forum: System76 Support
---

### Post by einnar on 2008-05-21
Will the System76 drivers work in Mint?
If not, can someone smarter than me figure out how to make it work?

Thanks! :)

---

### Post by thomasaaron on 2008-05-21
They will not work in Mint.

You might be able to make them work with a little python hacking and experimentation.

That said, I have no way of knowing if the fixes applied by the driver will be compatible with Mint.

---

### Post by einnar on 2008-05-21
Thanks Thomas!

In that case, I'm looking for someone that knows Python, and is smarter than me. :)

Can anyone assist?

---

### Post by matthekc on 2008-06-23
I bought a serval performance and the first thing I did was throw mint on it.  My video card is good, audio is fine, and the webcam works. This is all without any special drivers. I only have minor gotcha's like if the monitor powers down I can only get it back sometimes, or not all the special keys work.  I think the problems we're so minor I don't think I'll even go out of my way to fix them.

Your mileage my vary but I love mint and this machine together.

---

### Post by doubledown11 on 2009-06-08
Just installed Mint 7 on my Gazu1.  Webcam is out of commission but other than that everything seems to be running perfectly.  I was having lots of flaky issues with wireless that seem to be resolved now.  Not sure if it is Mint that fixed it or just the fresh install.

Like Thomasaaron said, the System76 Driver Utility will not run on this distro.

---

### Post by thomasaaron on 2009-06-09
The packages for installing the web cam drivers are in the System76 driver. you can pop it open, extract and install them. There's a few special considerations for the GazU1, though. Let me know via email if you need further help with this.

---

### Post by Scotty Bones on 2009-06-13
Actually...This can be done! Albeit, with some hacking.

Mint is really nothing more than an "enhanced" Ubuntu. So...with a little work, you can get Mint to report itself as Ubuntu.

The main culprit here is _mint-system_, This package checks to make sure the OS is branded as Mint at startup, and if it is not, it makes it so.  It is also used by several mint tools for identification purposes and is a required dependency, so don't even think about just removing it.


[B][SIZE="3"][COLOR="Red"]HOWTO: INSTALL S76 DRIVERS IN MINT
[/COLOR][/SIZE]
[/B][COLOR="Red"]**Warning: Create backups of config files before editing them.  You have been warned.  Attempt at your own risk!**[/COLOR]


I.  The first file that needs editing is:  [COLOR="RoyalBlue"]/usr/lib64/linuxmint/mintSystem/python/mint-adjust.py[/COLOR]

This file will show you what is being modified by _mint-system_ and how. Under the "# Restore LSB information" heading. Four lines down, you should see a line that reads: 
"[COLOR="SeaGreen"]lsbfile.writelines("DISTRIB_ID=[COLOR="Red"]Mint[/COLOR]\n")[/COLOR]"
Change Mint to Ubuntu.



II.  The second file to be edited is:  [COLOR="RoyalBlue"]/etc/lsb-release
[/COLOR]
It should be modified to look something like this:
```

[COLOR="Red"]DISTRIB_ID=Ubuntu[/COLOR]
[COLOR="Red"]DISTRIB_RELEASE=9.04[/COLOR]
RELEASE_NOTES_URL=http://www.linuxmint.com/rel_gloria.php
[COLOR="Red"]DISTRIB_CODENAME=jaunty[/COLOR]
[COLOR="Red"]DISTRIB_DESCRIPTION="Ubuntu 9.04"[/COLOR]

```



III.  The third file is: [COLOR="RoyalBlue"]/etc/linuxmint/info[/COLOR]

```

[COLOR="Red"]RELEASE=9.04[/COLOR]
[COLOR="Red"]CODENAME=jaunty[/COLOR]
EDITION="Main Edition"
[COLOR="Red"]DESCRIPTION="Ubuntu 9.04"[/COLOR]
DESKTOP=Gnome
TOOLKIT=GTK
NEW_FEATURES_URL=http://www.linuxmint.com/rel_gloria_whatsnew.php
RELEASE_NOTES_URL=http://www.linuxmint.com/rel_gloria.php
USER_GUIDE_URL=http://ftp.heanet.ie/pub/linuxmint.com/stable/7/user-guide/english.pdf
[COLOR="Red"]GRUB_TITLE=Ubuntu 9.04[/COLOR]

```

[COLOR="Red"]Notice that in 2 and 3, I have only changed the pertinent lines.[/COLOR]



IV.  The last two to edit are:  [COLOR="RoyalBlue"]/etc/issue[/COLOR]

```

[COLOR="Red"]Ubuntu 9.04[/COLOR] \n \l

```

and [COLOR="RoyalBlue"]/etc/issue.net[/COLOR]

```

[COLOR="Red"]Ubuntu 9.04[/COLOR]

```



V.  Give your system a reboot. If I haven't missed anything here, your system should now identify itself as Ubuntu 9.04.  Don't forget to restore your backups after you have completed the System 76 driver install.



Your welcome :)

If anyone can find any easier way (and i'm sure there is), please let us know.

---

### Post by Scotty Bones on 2009-06-14
If anyone has tried the above howto, please let me know if it works for you.  I got this working almost a month ago, when I first got my new Pangolin.  It was a lot of trial and error, making documentation difficult.
So...just let me know how it turned out for you, good or bad.

---

### Post by Cadeyrn on 2009-08-15
Worked great for me. Thanks! But, when you said that /usr/lib64/linuxmint/mintSystem/python/mint-adjust.py had the red name as Mint, I don't know if that's true for any random Linux Mint distro, but I do know my x64 Gloria says LinuxMint and not Mint. A simple, insignificant mistake, but who knows? Fixing that could prove helpful.

And also, maybe you should include what the text of the original files looks like too? Because I forgot to back a few of them up and certain pieces of text were lost forever. I just barely remembered them, but the next person to make that mistake might not remember.

Lastly, after the post-driver-installation reboot I was faced with a broken NVidia driver and Ubuntu asking if I wanted to run the session in low graphics mode, so first I navigated that menu to reset my graphics configuration to default, and then went to jockey to find the NVidia driver was deactivated, since I set the display config back to default. Reactivating that driver seems to be working. If I never edit this post again, then it worked. Otherwise, I may be screwed.

---

### Post by Scotty Bones on 2009-08-16
> **Cadeyrn said:**
> Worked great for me. Thanks! But, when you said that /usr/lib64/linuxmint/mintSystem/python/mint-adjust.py had the red name as Mint, I don't know if that's true for any random Linux Mint distro, but I do know my x64 Gloria says LinuxMint and not Mint. A simple, insignificant mistake, but who knows? Fixing that could prove helpful.

I'm glad to hear the process worked well enough for you.
The difference in text of the python script might be because of a difference in the version of mintSystem. I tend to pull from the newer repos, ie. those for Helena, so that might be the cause in difference there.

> And also, maybe you should include what the text of the original files looks like too? Because I forgot to back a few of them up and certain pieces of text were lost forever. I just barely remembered them, but the next person to make that mistake might not remember.

If necessary, the original config files can always be pulled from the live cd. I wasn't sure how much demand or interest this would be to others. But I could clean this up and expand it for the Helena/Karmic release, If there is interest. It may also be possible to script the process, but that is a bit out of my league.

> Lastly, after the post-driver-installation reboot I was faced with a broken NVidia driver and Ubuntu asking if I wanted to run the session in low graphics mode, so first I navigated that menu to reset my graphics configuration to default, and then went to jockey to find the NVidia driver was deactivated, since I set the display config back to default. Reactivating that driver seems to be working. If I never edit this post again, then it worked. Otherwise, I may be screwed.

This wasn't an issue I ran into; but since I tend to pull in newer nVidia drivers from the PPA's, this is usually the last thing I install. If I redo this howto for the next release (Clem may change things that affect this how-to). I will be sure to make a note about the breakage. And suggest that nVidia install be held off until after the S76 driver install.

---

### Post by Cadeyrn on 2009-08-24
Well, I found out the cause--the System76 Driver automatically downloaded the newest kernel and I didn't notice that kernel had become the default one to boot from, and everyone knows the newest Ubuntu kernel almost never works with the NVidia drivers. Simply setting the kernel I always use back to the default in GRUB's menu.lst fixed it. Also, the items in menu.lst were overwritten from the driver install--I had to re-enter the Windows boot line.

---

### Post by thomasaaron on 2009-08-25
You're right, nVidia tends to lag slightly behind the newest kernel -- particularly if you are running proposed updates (see System > Administration > Software Sources).

However, just to clarify, the System76 Driver has nothing to do with kernel updates. Those come down the pipe via Update Manager, which is an Ubuntu program for monitoring the availability of new updates.

---

### Post by luptinpitman on 2009-12-23
Running Mint Linux "Helena" on a Starling Netbook.  Followed the how-to using version 9.10 and karmic in place of 9.04 and jaunty respectively.  Made the necessary changes to the files listed (after backing them up) then was able to run/install system76 driver successfully without rebooting.  After install of system76 payload I restored all backed up files and rebooted.  No errors and no issues of any kind.

---

### Post by Futurian on 2010-05-22
Has anyone tried Scotty Bones' procedure on System76 with Linux Mint 9 Isadora? If so, how did it go?

Thanks.

---

### Post by Mr_Shifty on 2010-05-23
I'm running Mint 9 on my DARU3, but I haven't tried that procedure.  I'm not having any issues however, otherwise.  I haven't tried using the webcam (I don't typically use it anyway) but I have full 3D acceleration and Compiz seems to be functioning nicely.

Is there anything else the System76 driver does that I'm missing?  Because otherwise, at least on this laptop, Mint 9 works really well so far.

---

### Post by Scotty Bones on 2010-05-24
> **Futurian said:**
> Has anyone tried Scotty Bones' procedure on System76 with Linux Mint 9 Isadora? If so, how did it go?

Thanks.

Since I no longer run Mint myself, I can not attest to the continued effectiveness of my original how-to. However, after a quick review of the files involved in this new release via VirtualBox, the only thing that seems to have changed is the location of the mint-adjust.py file in step I from:

/usr/lib64/linuxmint/mintSystem/python/
to
/usr/lib64/linuxmint/mintSystem/

Given what I see, I believe it should still work properly.

---

### Post by bill516 on 2010-05-25
For the record I have installed and run 64 bit Mint 8 on my older PanP4-Nvidia 9300M graphics with no problems at all.  Everything worked.  I have burned a Livecd of Mint 9.  It seems to access both wireless and webcam without issues.  No full install yet but I would be very surprised if there were problems with it.  

I cannot speak to the present machines of course, but my PanP4 seems hospitable to a wide variety of other distributions.  Mandriva, the newest PCLOS, sidux and Mepis all have run nicely on this machine. Knoppix runs well from its live DVD.

So the System 76 driver would not seem to be necessary on this particular system.  But a small company like System 76 certainly would not develop it if it were not necessary elsewhere!  E.G., I'll bet (without knowing!) that ATI cards pose a problem without that driver.

Mint is quite nice but in the end it makes no compelling case for me as against Ubuntu 10.4 which is running very well.  But I can appreciate that others might prefer Mint.

So Ubuntu stays on and it remains my "go to" distribution.  It really is a very good operating system/desktop environment on a solid, well-supported system.  Yes, I did put those buttons back on the top right side where they "belong".  :P

---

### Post by gruntlips_ on 2010-05-25
Hmmm... does pulseaudio work correctly in mint? Because it sure doesn't in 10.04.

---

### Post by Scotty Bones on 2010-05-27
> **gruntlips_ said:**
> Hmmm... does pulseaudio work correctly in mint? Because it sure doesn't in 10.04.

I can't speak for Mint, but PA w/ 10.04 on my Panp5 works wonderfully. Whether its on board, HDMI or my bluetooth headphones; I just works.

---

### Post by bro brian on 2010-12-29
System76 should be looking closely at Linux Mint. I don't know why they aren't. I really think that they should create a system76 driver for Mint. Ubuntu and Mint go hand-in-hand. Why they aren't moving on this is beyond me. I would think that it would be to their advantage to offer a mint driver to their loyal following.

  Of course, maybe they are looking at it closely. Wild guess (not an informed guess), but maybe they haven't any reason to believe that Mint is stable enough for their approval at this time.

---

### Post by isantop on 2010-12-30
We've built up a brand identity with Ubuntu. Many people think of us as the Ubuntu computer company, and Ubuntu is a large part of who we are as a company. Switching from Ubuntu to Mint would for us be almost as drastic as Apple switching from Mac OS to Ubuntu. 

I'm not ruling out the possibility of a Mint version of the System76 Driver, however, I wouldn't hold my breath. Doing that means we need to test and QC on an entirely different distribution, and Mint and Ubuntu are only going to drift further and further apart as time goes on. We'll see a big split in April with Unity.

---

### Post by bro brian on 2010-12-30
Understood. I thought that there may be a specific reason why it might not be such a practical move for system76. It's an ethics issue, I suppose. No big deal.
  I, personally, am very happy with the native Ubuntu of my system76 laptop. I did install Mint on my old Compaq Presario briefly, but It seemed to bog it down quite a bit - don't know why. So I replaced it with the Ubuntu Lucid using their i386 architecture (32 bit) cd download.
  Thanks for the explanation & insight.

---

### Post by macpj on 2011-01-13
I haven't seen any postings in regards to Mint being installed on a machine in several months. Was wondering if anyone has done a recent install or upgrade to Mint in the last few months, if there were any issues on their System76 machine. :-?

---

### Post by bro brian on 2011-01-13
> **macpj said:**
> I haven't seen any postings in regards to Mint being installed on a machine in several months. Was wondering if anyone has done a recent install or upgrade to Mint in the last few months, if there were any issues on their System76 machine. :-?
I never did install it on my Pan5 laptop, so I'm not really sure what would happen. I am still curious myself, however, and I wonder if you couldn't just install system76's driver onto it after installing Mint. Why couldn't you? Mint is merely the Ubuntu os with a few tweaks. It loads up using the Ubuntu protocol and everything.

---

### Post by isantop on 2011-01-13
You could, but it wouldn't run, since Mint identifies as Mint, not as Ubuntu. There is a thread somewhere on hacking mint to work with the driver though.

---

### Post by bro brian on 2011-01-13
Go here:
[http://ubuntuforums.org/showthread.php?t=802181&highlight=system76+driver+Mint](http://ubuntuforums.org/showthread.php?t=802181&highlight=system76+driver+Mint)

---

### Post by jml on 2011-01-13
Maybe my needs are less demanding than most, but I find that Debian works very well with my System 76 laptops.  I have been running Debian testing (squeeze) on my DARU1, and Debian stable (Lenny) on m DARU3.  I would be running Debian on my STAR1 but I ran into the poor wireless performance issue that was present with standard Ubuntu.  I need the System 76 driver to get good wireless performance.  I plan to sell my Star1 and buy a current Starling as I feel that it should run Debian without the wireless problems.

Joe

---

### Post by jdb on 2011-01-14
> **jml said:**
> Maybe my needs are less demanding than most, but I find that Debian works very well with my System 76 laptops.  I have been running Debian testing (squeeze) on my DARU1, and Debian stable (Lenny) on m DARU3.  I would be running Debian on my STAR1 but I ran into the poor wireless performance issue that was present with standard Ubuntu.  I need the System 76 driver to get good wireless performance.  I plan to sell my Star1 and buy a current Starling as I feel that it should run Debian without the wireless problems.

Joe

Just to round out the DARU line, I'm running Debian squeeze on my DARU2.

jdb

---

### Post by tlroche on 2011-01-26
Getting meta on the thread:

First,

> **isantop said:**
> There is a thread somewhere on hacking mint to work with the driver though.

> **bro brian said:**
> Go here:
[http://ubuntuforums.org/showthread.php?t=802181&highlight=system76+driver+Mint](http://ubuntuforums.org/showthread.php?t=802181&highlight=system76+driver+Mint)

... don't do that: that just points back to this thread, in which currently (unless I'm completely blind or careless) there is no pointer to the Mint-hacking thread. Second,

> **Futurian said:**
> Has anyone tried Scotty Bones' procedure on System76 with Linux Mint 9 Isadora?

> **Scotty Bones said:**
> I can not attest to the continued effectiveness of my original how-to. However, after a quick review of the files involved in this new release via VirtualBox, the only thing that seems to have changed is the location of the mint-adjust.py file in step I from:

/usr/lib64/linuxmint/mintSystem/python/
to
/usr/lib64/linuxmint/mintSystem/


Can someone point to Scotty Bones' howto? I searched this forum but found nothing.

---

### Post by macabrem on 2011-01-26
> **jml said:**
> Maybe my needs are less demanding than most, but I find that Debian works very well with my System 76 laptops.  I have been running Debian testing (squeeze) on my DARU1, and Debian stable (Lenny) on m DARU3.  I would be running Debian on my STAR1 but I ran into the poor wireless performance issue that was present with standard Ubuntu.  I need the System 76 driver to get good wireless performance.  I plan to sell my Star1 and buy a current Starling as I feel that it should run Debian without the wireless problems.

Joe

Joe,
   On the Star 1, I got my wireless working well with a Debian based distro (crunchbang) by downloading the "bleeding edge" package of Compat Wireless from:  [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

Then just followed the directions to build the driver for the Star 1.  It was pretty easy, and I consider myself more intermediate than advanced with linux.

I've been trying to get the word out about that great program after I got the suggestion from somebody else.

I don't think it will make a difference, but I'm running the Liquorix Kernel.  I'm pretty sure the driver still worked okay when I booted into the standard Debian kernel.

---

### Post by henrydubb on 2011-02-05
I am posting this on Mint Debian via Virtualbox. I also have the Mint Menu installed in 10.10. 

For me Mint was the Mint Menu. I love how you have total system access via a menu. When i use other menus they feel buggy because I can't edit, remove, install, or search for programs.

But again LMDE runs without no issue in Virtual Box. It can run full screen or seamless like another program. Have also noticed the jumping cursor issue is no more.

I have come to the conclusion that having 10.10 with 76 drivers and other distros running in VB is the best of both worlds. This will become more important for me after the Unity Disaster. 



> **macpj said:**
> I haven't seen any postings in regards to Mint being installed on a machine in several months. Was wondering if anyone has done a recent install or upgrade to Mint in the last few months, if there were any issues on their System76 machine. :-?

---

### Post by jml on 2011-02-06
Thanks for the link, macabrem.  Unfortunately, I have already given my STAR1 to one of my friends.  I will however, forward this link to him.  He is a big fan of Mint, and is toying with Mint-Debian edition.

Joe

---

### Post by isantop on 2011-02-07
> **henrydubb said:**
> I am posting this on Mint Debian via Virtualbox. I also have the Mint Menu installed in 10.10. 

For me Mint was the Mint Menu. I love how you have total system access via a menu. When i use other menus they feel buggy because I can't edit, remove, install, or search for programs.

But again LMDE runs without no issue in Virtual Box. It can run full screen or seamless like another program. Have also noticed the jumping cursor issue is no more.

I have come to the conclusion that having 10.10 with 76 drivers and other distros running in VB is the best of both worlds. This will become more important for me after the Unity Disaster.

Good to hear you've found an acceptable solution. I see where you're coming from with Unity, but I should point out that even in this early state, Natty's Unity is already much faster and more stable than Unity in 10.10. I'm confident they'll get all the bugs worked out in time for 11.04.

---

### Post by henrydubb on 2011-02-10
For those that want Mint but don't want to lose System76 Ubuntu supported drivers, try the Mint Repo

 [http://packages.linuxmint.com/list.php?release=Julia](http://packages.linuxmint.com/list.php?release=Julia)

I ended up installing mintsystem and everything seems to work fine. Wireless seems to work better but I have had wireless issues as of late so it might be working better for non mint reason.

The only issue is cheese can't do videos, can't remember if it did previously.

---

### Post by chasashmore on 2011-06-07
Just to let Scotty Bones and others know: the instructions he gives for installing the System76 drivers under LinuxMint still work: I just installed the drivers following the instructions on my Gazelle Ultra (Gazu1) under LinuxMint 10 KDE (Julia). Of course, I found the file mint-adjust.py under /usr/lib64/linuxmint/mintSystem as noted in a later post, and there was a minor difference I found in one or two files from what he listed, but it was rather obvious what adjustment to make. Many thanks for the instructions. :D

---

### Post by tlroche on 2011-08-21
> **chasashmore said:**
> Just to let Scotty Bones and others know: the instructions he gives for installing the System76 drivers under LinuxMint

[here]("http://ubuntuforums.org/showpost.php?p=7449131&postcount=7")

> **chasashmore said:**
> still work: I just installed the drivers following the instructions on my Gazelle Ultra (Gazu1) under LinuxMint 10 KDE (Julia).

And I used them to put [LMDE]("http://blog.linuxmint.com/?p=1604") on my PanP5. Rolling updates! and I'm swapping a lot less than under Natty.

> **chasashmore said:**
> Many thanks for the instructions.

Ditto!

---

### Post by silvaire on 2012-09-02
I recently got a gazp7.  I didn't realize that System76 was so closely tied to Ubuntu, and don't give information on how to configure other distros. I was quite explicit at purchase time that I'd be reformatting the disk and running RHEL6 and other distros, and not Ubuntu, so I'm a bit disappointed.

Anyway, for Linux Mint 13:

To get the screen brightness keys (Fn-F8 and Fn-F9) to work, I added this line to /etc/default/grub:

GRUB_CMDLINE_LINUX="acpi_os_name=Linux acpi_osi="

(reboot)

-----------------------

To get the SD card reader to work, I used this:
wget [https://bugs.launchpad.net/bugs/971876/+attachment/2991730/+files/rts_bpp.tar.bz2](https://bugs.launchpad.net/bugs/971876/+attachment/2991730/+files/rts_bpp.tar.bz2)
tar xjf rts_bpp.tar.bz2
cd rts_bpp
make
sudo -s     # become root
  make install
  modprobe rts_bpp
  depmod -a
(no reboot required)

-----------------------

Suspend/Resume is working fine.

-----------------------

---

### Post by ImperfectlyInformed on 2012-10-19
I switched my (lemu2) Lemur UltraThin purchased 02/26/2011 to Mint. No problems, webcam works fine as well.

Ubuntu is terrible with the new Gnome and Unity type of stuff. Mint is actually working a nice desktop interface called Cinnamon.

I'm very happy to be done with Ubuntu. Even tho the switch went fine, to avoid problems in the future I may go with someone else such as ZaReason for my next laptop since they ship with various different distros, including Mint.

---

### Post by GeneSalamin on 2012-10-19
It is actually possible to stay with Ubuntu and yet have the good old Gnome desktop.  Install Gnome Shell, and then choose Gnome Classic as a desktop.  See how to here.

[https://www.ibm.com/developerworks/mydeveloperworks/blogs/netcooltips/entry/how_to_return_to_classic_gnome_in_ubuntu_12_04_precise12?lang=en](https://www.ibm.com/developerworks/mydeveloperworks/blogs/netcooltips/entry/how_to_return_to_classic_gnome_in_ubuntu_12_04_precise12?lang=en)

---

### Post by bro brian on 2012-10-19
I quite like Linux Mint 13 XFCE. I'm thinking about installing it on some computer at some point. It comes with certain codecs pre-installed, which is good, and the XFCE interface reminds me much of the old Gnome look.
I do run OzUnity3  - BlackOpal64 on my desktop that I built myself. The BlackOpal64 is a respin of Ubuntu 12.04 (Precise), and I can log into it in Gnome Classic. It is wonderful!
At the moment, I'm still running Ubuntu 10.04 Lucid on my Sys76 lappy, but will eventually re-install an newer os onto it. I will probably go with Xubuntu (Ubuntu with the XFCE desktop environment). I can always add certain codecs myself, and the Sys76 driver should install in Xubuntu.
ZaReason is certainly an option for purchasing a computer with a Linux distro factory loaded onto it, however I would certainly question their customer support. Sys76 support is by far the best I have ever experienced.

---

### Post by oakhilltop on 2012-10-19
Just adding my .02 to Sys 76 marketing. Support for Mint would've be a plus for me. And, I am thinking of making the move.

To those who have installed Mint, does the laptop boot directly to the login screen or does it install grub? I like the quick boot of my Lemur with SSD. It gets to the login screen in no time.

I have been very happy with my Lemur, but am skeptical about the upcoming Ubuntu. I had been using Mint for a couple of years prior to purchasing the Lemur

---

### Post by bro brian on 2012-10-20
> **oakhilltop said:**
> [COLOR=Red]Just adding my .02 to Sys 76 marketing. Support for Mint would've be a plus for me. And, I am thinking of making the move.

To those who have installed Mint, does the laptop boot directly to the login screen or does it install grub? I like the quick boot of my Lemur with SSD. It gets to the login screen in no time.[/COLOR] [COLOR=Red]

I have been very happy with my Lemur, but am skeptical about the upcoming Ubuntu. I had been using Mint for a couple of years prior to purchasing the Lemur[/COLOR] 

For the sole purpose of attempting to answer your question, I installed Linux Mint XFCE on Virtualbox.  Upon reboot after install, there was only a black screen for a moment, and no grub menu appeared. It went straight to the login screen.
So I suppose that (with a solid state hard drive), Linux Mint would boot fairly quickly.

---

