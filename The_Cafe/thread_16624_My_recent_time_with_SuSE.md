---
title: "My recent time with SuSE"
date: 2005-02-22
forum: The Cafe
---

### Post by jdong on 2005-02-22
Yep, watch out: Distro junkie attack again!

Recently, to play with it some more, I've installed SuSE on my laptop (Celeron 340, 768MB RAM, i865 integrated graphics).

I'm not going to review SuSE -- I personally feel reviews are worth CRAP to people wanting to try distros. Why? It provides ONE person's opinion/experience on a distro, and further uses that ONE opinion to generalize about EVERYONE's experience with the product. Obviously far too few people have statistical background. (p.s., kudos to those reviewers who try and detail installations on 5 or 10 different systems -- You can ignore this last paragraph -- I, and most reviewers I've read, do not have the time/resources/time/time/time to do this!)

Well, basic experience:

1. Very nice install -- tells you in an overview EXACTLY EVERYTHING it's gonna do ahead of time, instead of making you work step-by-step, realizing that you made a mistake too late to correct it!

2. reiserfs is default. Has been that way since like 6.4. SuSE's reiserfs seems VERY matured -- I've done quite a number of hard resets (EVIL) but haven't been able to corrupt the FS yet. I'm impressed. P.S., Reiser4 is also built into the kernel (modprobe reiser4 ;-) ). I've yet to test it. Right now, I **value my stability**.

3. KDE -- GO KDE!! Still my favorite DE, primarily because of the kioslaves implementation. (Can Nautilus let me use ssh:/// to edit a textfile with Openoffice.org, then save it back? Err, not really.)... SuSE has definitely modified their KDE quite a bit. Switch User is enabled by default, pretty cool theme (can't complain yet), and nice set of applets in tray. They definitely changed the icon size proportions from default KDE Plastik, because I find myself clicking on wrong buttons much less often.

4. Power Management. Go find yourself some screenshots of YAST Powersave. Very nicely integrated -- grabs its events from acpid, but forwards it to the little tray applet. Events on lid close, sleep button, powerbutton, etc, can be controlled through the GUI. Suspend-to-disk works out-of-the-box. Suspendto RAM doesn't work -- hasn't worked on any other distro, either (black screen on resume).

5. Openoffice.org KDE integration -- much nicer than GTK+ OO.o... Again, Kioslaves rules -- being able to type in an http:// address into the Open dialog in Openoffice, saving to samba shares on-the-fly. P.S. Hoary is missing OOo KDE integration altogether... That ticks me off!

6. APT -- Get apt4rpm. It unlocks the entire SuSE archive -- RPMs for everything from FreeNX to wine, all quite up-to-date. (K3b 0.11.20cvs, Wine 20050211, KDE 3.2.3, X.org 6.8.2 late RC, Firefox 1.0 + IDN spoof fix, ...). Don't use YOU, use APT.

7. Init scripts -- *nicely* polished -- Initrd intelligently waits (idle-loops) for the root device to appear, allowing installation to USB hard drives that love to register 5 seconds too late! Network scripts background DHCP, but if another init script requires network access and mandatory devices aren't activated yet, it will pause for 15 seconds for DHCP to finish. The Hotplug scripts shows nice progress in *'s of what it's doing. Bootup is quite fast and comparable to Hoary -- unheard of in an RPM distro! Definitely we should hack some of these neat tricks to work with Hoary.

8. Yast -- very mature administration tool. Administers everything including the kitchen sync (j/k).

9. FAUmachine -- a GUI, vmware clone that uses a modified implementation of UML. It makes setting up virtual Linux machines as easy as apt-get install FAUMachine.

10. Kernel -- Diffed it against 2.6.8 -- about 10MB's worth of TEXT PATCHES! Goes into the HEAVILY PATCHED category, but definitely doesn't feel "weighed down" at all. Binary NVidia/ATI drivers are also prepackaged, but need to be fetched through YAST -- not too much different from Ubuntu.



This definitely seem like a great OS for me to settle on. I can tell you, the discovery of apt4rpm in SuSE made all the difference -- they provide stable "backports" of latest software (GAIM is at 1.1.3, just to say!) through APT, but not through YAST.

FAUmachine is also a big player. For the backports work (textmode compiling on an Athlon64), I can take the performance hit -- just give me a fickin virtual environment without 6 hours of manual reading and kernel patching!


I definitely want to switch my desktop over to SuSE.

---

### Post by mark on 2005-02-22
I installed SuZE 9.2 on my scratch drive a while back...even when selecting Gnome as the default DE, the "KDE"-ness of the distro still came through.  That's not good or bad - that's choice.  Same thing with the latest MEPIS (I think it's 3.3) - even though it now offers Gnome or KDE, you can really tell the primary orientation.

Again, one of the things that really hooked me on Ubuntu was the fact that it was Debian-based and the primary (only!) orientation was Gnome.  But SuZE does have a lot to reccomend it - I can't see that Novell's ownership has hurt it a bit.

---

### Post by poofyhairguy on 2005-02-22
[QUOTE=jdong]
5. Openoffice.org KDE integration -- much nicer than GTK+ OO.o... Again, Kioslaves rules -- being able to type in an http:// address into the Open dialog in Openoffice, saving to samba shares on-the-fly. P.S. Hoary is missing OOo KDE integration altogether... That ticks me off!
[/QUOTE]

Well...the universe OO2 has it. And 2 seems stable to me.

---

### Post by KiwiNZ on 2005-02-23
I just got the latest edition of  Linux Format and the cover DVD features full version of Suse 9.2 . 
I am really tempted to give it a go. I haven't tired Suse since version 9.00

---

### Post by defkewl on 2005-02-23
How do you update your software? Does SuSE use up2date like Redhat too or else?

---

### Post by nocturn on 2005-02-23
I've always liked SuSE.  It was the distro I used for the longest period and I still have it on a server at work.

But they went down the road of nonfree licenses (YaST) and I didn't like UnitedLinux.

Otherwise, they are still great.

---

### Post by rufius on 2005-02-23
The last SuSE I tried was 8.2 and I had (to say the least) a terrible experience with it. Hardware was detected incorrectly or not at all and it was just bogged down and slow. I've been tempted to try SuSE 9.2 on my test box but haven't had time to get the ftp cd or bother to get a harddrive for the test box.

---

### Post by jdong on 2005-02-23
SuSE updates, usually, through their YAST online update (YOU) program. I have it going through APT. They have a little tray applet for monitoring for updates.

As far as YAST, it _IS_ GPL'd after Novell took over, but few distros have started to take advantage.

---

### Post by jdong on 2005-02-23
BTW, OO.o 2 sucks right now. Half of the times, clicking File->Open will crash the whole thing.

---

### Post by MaZiNgA on 2005-02-23
SuSE is actually great distro! I've been using SuSE 9.1 for quite a long time but installing apt4rpm gave some crashes and glitches on my system so I had to switch to Debian.

Yast2 is a great Configuration tool (mind I'm not saying Add/Remove Software tool) and...GPL'd??? I didn't know that! Why aren't we using it in Ubuntu? Is there some way for me to use it? Is there a .deb around??? :eager:

---

### Post by cacofonix on 2005-02-23
[QUOTE=jdong]BTW, OO.o 2 sucks right now. Half of the times, clicking File->Open will crash the whole thing.[/QUOTE]

How did you get a copy? I have tried getting the iso using wget and it has trouble finishing it off if you restart the download.


cacofonix

---

### Post by eldrich_rebello on 2005-02-23
i've had a decent time with suse 9.1.it's ok but gnome doesn't function properly if you login as anyone else except root.it's also way slower than ubuntu and debian.kde is a bit overwhelming for me.that's why i've stuck with ubuntu though i still have suse

---

### Post by ember on 2005-02-23
I went away from SuSE with version 8.1, which was, to my mind, the last usable distro they sold. 9.0 and 9.1. were quite unstable on the machine of a friend, yet at least that brought me to Ubuntu ;)

And additionally I have to state, that Fedora Core just really, really sucks if it comes to bringing up a smooth and productive working enviroment. Unfortunately the Planet CCRMA archives are reasonably more up to date than DeMuDi.

---

### Post by poofyhairguy on 2005-02-23
[QUOTE=MaZiNgA]Why aren't we using it in Ubuntu? [/QUOTE]

Because.....its a QT app. Made for KDE from the start.

---

### Post by poofyhairguy on 2005-02-23
[QUOTE=jdong]
I definitely want to switch my desktop over to SuSE.[/QUOTE]

As much as you like KDE you should. I mean...that is a nice KDE.

Of course, I must ask- have you tried MEPIS? If you haven't put that next on your "got to try" list. I personally think its a better KDE desktop, if only because Yast doesn't get in your way (such as with wireless).

I always have fun reading about jdong's newest flavor of the month.

---

### Post by TravisNewman on 2005-02-23
So j- do you think you'll be back to Ubuntu this time or do you think it might be permanent?

---

### Post by Quest-Master on 2005-02-23
I used SUSE as my first distro, but the small bugs which annoyed me just a little in the beginning killed it all for me. I was forced back onto Windows, but later made it to the light.

Ubuntu. \m/

---

### Post by poofyhairguy on 2005-02-23
[QUOTE=cacofonix]How did you get a copy? I have tried getting the iso using wget and it has trouble finishing it off if you restart the download.


cacofonix[/QUOTE]


Its in the Hoary Universe.

---

### Post by cacofonix on 2005-02-23
[QUOTE=poofyhairguy]Its in the Hoary Universe.[/QUOTE]

Whoops I used the wrong quote #-o :-\". I want to get the suse dvd iso but wget seems to have trouble with them has anyone been able to get wget to download them properly?


cacofonix

---

### Post by TravisNewman on 2005-02-23
are you talking about the livedvd or the trial version of Suse?

EDIT: on that topic, do the mini-install cd and install dvd from suse's ftp run out after a certain time or nag you or what? They're called "evaluation"

---

### Post by jdong on 2005-02-24
The FTP DVD and mini-install are both FULL VERSIONS of SuSE, like the boxed version. They've ,however, been stripped of the commercial applications

---

### Post by TravisNewman on 2005-02-24
OK YAST sucks for package management-- but it's really freakin awesome for an installation, and not too bad for general system configuration, though sometimes it's pretty lacking.
 
For my weekend project that I posted about earlier, I was using a very old version of it just to test it out, so this is very new to me still.

There are a few things about SuSE I don't like, but overall it's very slick. Gnome even feels nicer and more polished, and they don't even put much emphasis on it. But the fonts are freakin' HUGE by default-- though they do look nicer than in Fedora, and even in Ubuntu with the fonts.conf trick.

Things seem to be quite quick. I don't know if there's prelinking or not, haven't gotten into any in-depth stuff yet.

I LOVE the grub that it installs. It's the same grub as the Ubuntu LiveCD-- why isn't this more common, it's just beautiful.

So yes, I may be getting won over by an RPM based distro, for some things, but Debian is just too amazing at some things. They both have their places in my Linuxing now I think. I'm definitely going to stay in SuSE for a few days though and learn my way around.

First thing-- I gotta figure out how to install apt4rpm

---

### Post by jdong on 2005-02-24
Urg, still can't cope with Fedora.

Running Ubuntu under GNOME right now -- I give up on KDE for now... :(. Am running a risky setup though, 5x40GB IDE RAID0 w/ reiserfs. Sure fast as hell -- installed to GNOME in 5 minutes!


I've had enough distro junkiness for now -- doing useful stuff with my time. Currently, working on a Python port of the WAIH: [http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/trunk/README.whatis](http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/trunk/README.whatis)

Hopefully that'll solve our Java installing problems, once I'm done :) (IF I'm done!)

---

### Post by TravisNewman on 2005-02-24
So question j-- you said that installing apt4rpm gave you more possibilities of software to install than YAST. But when I did it, it seems to have LIMITED what I can install. And yes, I've checked the sources.list

---

### Post by jdong on 2005-02-24
Did you get the sources.list from the examples/ folder on the FTP? That one has like 20 or so sections -- packman, suser, suse-projects all provide lots of packages in addition to stable, the SuSE collection.

---

### Post by KiwiNZ on 2005-02-25
I tried Suse 9.2 for a few days , I didn't like it . Hard to put my finger on why , it just seemed like someone with a crayola set had been to work on it.

This evening I blew it away and installed Fedora Core 3 . Just messing around with it now.

---

### Post by jdong on 2005-02-25
btw, python RULES as a programming language! :D

---

### Post by A-star on 2005-02-25
[QUOTE=jdong]Did you get the sources.list from the examples/ folder on the FTP? That one has like 20 or so sections -- packman, suser, suse-projects all provide lots of packages in addition to stable, the SuSE collection.[/QUOTE]

I would like to have  look at this list, can you give the full link or copy/past it here?

---

### Post by jdong on 2005-02-25
```

jdong@omega:~$ sudo hdparm -tT /dev/md0
Password:

/dev/md0:
 Timing cached reads:   2264 MB in  2.00 seconds = 1131.61 MB/sec
 Timing buffered disk reads:  258 MB in  3.01 seconds =  85.71 MB/sec
jdong@omega:~$

```

```

jdong@omega:~$ cat /proc/mdstat
Personalities : [linear] [raid0] [raid1] [raid5] [multipath] [raid6] [raid10]
md0 : active raid0 sdb1[4] sda1[3] hdd2[2] hdb2[1] hda2[0]
      194177024 blocks 32k chunks

unused devices: <none>

```

```

jdong@omega:~$ mount
/dev/md0 on / type reiser4 (rw,noatime,nodiratime)

```

```

jdong@omega:~$ uname -a
Linux omega 2.6.10-ck6 #3 Fri Feb 25 16:06:52 EST 2005 i686 GNU/Linux

```

```

jdong@omega:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 4
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 8
cpu MHz         : 801.360
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 pni syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 1569.58

```

The **ULTIMATE** Ubuntu speed demon setup! Yeah!

---

### Post by TravisNewman on 2005-02-25
[QUOTE=A-star]I would like to have  look at this list, can you give the full link or copy/past it here?[/QUOTE]
 Yeah I'm with him! I didn't actually find apt on the suse servers, but I did apt4rpm suse on google and installed the rpms from the first site that came up. I didn't see any sources.list or even an examples folder.

---

### Post by wallijonn on 2005-02-26
[QUOTE=jdong]

The **ULTIMATE** Ubuntu speed demon setup! Yeah![/QUOTE]

So, you're running an i686 kernel instead of the K7 kernel? hmmm.

---

### Post by CowPie on 2005-02-26
[QUOTE=jdong]The FTP DVD and mini-install are both FULL VERSIONS of SuSE, like the boxed version. They've ,however, been stripped of the commercial applications[/QUOTE]
 Suse was hell to install, unless you buy it.

I always hated the YOU, and the package manager interface was crap.

EDIT:  Cool!  We get dots now..I should visit here more often!

---

### Post by jdong on 2005-02-26
[QUOTE=wallijonn]So, you're running an i686 kernel instead of the K7 kernel? hmmm.[/QUOTE]

I'm actually running a K8 (Athlon64) kernel. I config'ed it myself. It's a ck6 +reiser4+evms+PATA sata_promise patch kernel.

---

### Post by TravisNewman on 2005-02-27
What kind of dots are you talking about?

---

