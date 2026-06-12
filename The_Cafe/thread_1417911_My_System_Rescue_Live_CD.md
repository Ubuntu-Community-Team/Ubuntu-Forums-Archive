---
title: "My System Rescue Live CD"
date: 2010-02-27
forum: The Cafe
---

### Post by nerdopolis on 2010-02-27
Hi. I have been working on creating a live cd that you can use to configure and rescue Ubuntu systems that you cant get a GUI with. (whether it will be because of a broken X-server or something). I could not find any CD that does this for Ubuntu.

I have the script that I use to make the live CD attached. It uses remastersys to make the ISO.
 
I had an thread in the 'General help' section in August, when I did not have much of one here: [http://ubuntuforums.org/showthread.php?t=1254973](http://ubuntuforums.org/showthread.php?t=1254973) . I  moved the discussion to the community cafe, because I felt that its more fitting here now.

A few notes: while it can detect linux/ubuntu systems installed normaly, it will not detect installs on Wubi, and I don't think it can find encrypted ones either. It currently is in english only, and x86 only. (I cant test x64, because I have no x64 processors...). 

Another thing: as  Live CD, chroots into the chosen system, and it starts graphical programs within a nested xserver, Its also supposed to pull in some programs so that the chroot *thinks *that the programs are permanently installed, when they are really not (I found out a way to do that). These programs are to aid in configuring the system, programs like bootup-manager. The thing is, are there any other programs like that? 

I don't have an ISO anywhere, as I don't know who would accept a 350MB file, and I don't know how to put the source code with the ISO, as I build the ISO with a script that calls  debootstrap, chroot, and apt-get, and edits a few files with echo cat sed awk and grep, that doesn't touch any source.

EDIT: I have a newer script in this thread, which adds more features to the live cd later in this thread. The one attached in this post is outdated

---

### Post by nerdopolis on 2010-03-01
...bump...?

---

### Post by nerdopolis on 2010-03-02
... ... bump?... ...

---

### Post by fatality_uk on 2010-03-02
Just in case you didn't know:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

And there are a few others.

---

### Post by nerdopolis on 2010-03-02
Thanks for the reply, but those seem to be straight out data recovery cd's backups, partition management, and data restoration. While I might considersome  of those for inclusion, I'm looking for system config tools, for editing configs and stuff. 

Maybe if I put it this way: I'm looking for(preferably graphical)  tools that you could use to configure your system to start again, but would need your system to be started to use them. (as my live cd can let you use them, once I know of them, and include them.)

---

### Post by nerdopolis on 2010-03-03
So... Did anybody try to build the Live CD to try it out? 

its as simple as extracting the script, making it executable, and running it in a terminal, pressing enter in the terminal twice, and waiting for it to finish.

What did you think about it?

---

### Post by nerdopolis on 2010-03-04
I guess no one tried it yet?

---

### Post by MooPi on 2010-03-04
Why not install to a flash drive and use it as a system recovery.  The cd drive will be  available for usage and the flash is much more responsive than a live CD. I'm currently using a flash drive as my root or install drive. You could customize the install easier than a remaster of Ubuntu.

---

### Post by nerdopolis on 2010-03-04
well... its intended (If I find a good place to put 400MB files) to be a simple ISO that one can download, and burn to a disk, and use when their x server wont load or something like that. Not many people know how to make a flash drive bootable, or have an extra one to just toformat, and not all BIOSes support it. (and I already have a script customizing a live cd attached in my first post...)

Think of it as almost a version of this ( [http://en.wikipedia.org/wiki/Windows_Recovery_Environment](http://en.wikipedia.org/wiki/Windows_Recovery_Environment) )for Ubuntu (and possibly other Linux systems)

---

### Post by nerdopolis on 2010-03-05
Anyone know of a place I can put the ~350 MB .iso file for people to download?

---

### Post by nerdopolis on 2010-03-07
No one knows of a good open-source centric server/website to place a 350MB file?

---

### Post by nerdopolis on 2010-03-08
... bump? ...

---

### Post by MooPi on 2010-03-08
Dropbox ? I don't know what the file size limits are. You can pay for a larger dropbox if need be but the standard is free.

---

### Post by nerdopolis on 2010-03-09
I took a look at dropbox, and it seems like the max size is 300MB.  Thats a little too close. Are there any others?

---

### Post by nerdopolis on 2010-03-10
bump?

---

### Post by nerdopolis on 2010-04-13
Hi. I made a few changes to the script that will make the resulting Live CD a little more usable. its attached. I did a few tweaks so you can copy and paste between the main X display, and the display within the Xephyr window, and now you can use arrow keys in the Xephyr window. 

I also added a user editor, and a login prompt so you can log into a specified user instead of being root if needed.


I plan to add more utilities as I find them, as well as some interactive scripts to allow users to do common fixes for common problems without typing them. (like sudo dpkg-reconfigure -phigh xserver-xorg).

Anyone know of any relevant tools that I can also include onto my Live CD?

Thanks

---

### Post by nerdopolis on 2010-04-14
... bump... ?

---

### Post by nerdopolis on 2010-04-15
...bump...? Did anybody give this a try?

---

### Post by Dayofswords on 2010-04-15
you could set up a torrent of your own build
(i cant since i'm on windows at school =p)



Also:
"LiveDiskCreAtedFromLiveDiskCreAtionScript_English_x86.iso"
is the final name of the iso, i found it in the script. bit long winded lol

---

### Post by Dayofswords on 2010-04-16
i'll attempt a build in a clean virtualbox

EDIT: failed, said it could not find remastersys

---

### Post by nerdopolis on 2010-04-16
Does it say ```
Unable to access the Remastersys Archive site. Please test your connectivity to the Internet If you belive you are connected, the Remastersys Archive Site may be down. The script needs Remastersys' Archive Site in order to succede. Exiting.
``` I know that your network connection to virtual box is fine because it actually tests Ubuntu's archive site first, and if it cant reach it Ubuntu's site, it aborts before it gets to test Remastersys's.

Or a little while after you run it, or does it run a bit, say that remastersys can not be found, and dump a bunch of errors? Did you notice any output from aptitude?

I tried it here, and it seems to be working here. That does happen to me sometimes where remastersys' site is not found, and it must have been something up with the Remastersys server. I would try again...

BTW: I make that long winded file name to be (almost) absoultly sure that I am not overwriting anything. I doubt normal people have file names like that so thats why I chose it. :lolflag:

---

### Post by nerdopolis on 2010-04-18
**Dayofswords**: did you get to retry the live CD build?

Did anybody else also try my live CD as well?

---

### Post by nerdopolis on 2010-04-19
no one had any success?

---

### Post by nerdopolis on 2010-04-21
I guess not?

---

### Post by nerdopolis on 2010-04-22
Bump... I included a screen shot to show what this live cd does. I think it summarizes what it does... 

EDIT: it doesn't only do terminal things, it can run GUI tools under your install. 

I tried uploading the CD onto a torrent site with no luck... I did not see any data transfer for the upload...

---

### Post by nerdopolis on 2010-04-24
... bump? ...

---

### Post by nerdopolis on 2010-04-25
... ... bump? ... ...

---

### Post by nerdopolis on 2010-04-26
I noticed a few views on my scripts and my screenshot. Any thoughts?

---

### Post by nerdopolis on 2010-04-27
bump?

---

### Post by nerdopolis on 2010-04-29
... ... ... bump ... .... ...?

---

### Post by nerdopolis on 2010-04-30
... ... ... ... bump? ... ... ... ...

---

### Post by nerdopolis on 2010-05-29
Bump?

---

### Post by Phrea on 2010-05-29
I don't think a lot of people are interested... :\
You keep bumping, users keep ignoring it. :\

---

### Post by Shining Arcanine on 2010-05-29
There are already tools for system recovery and they work quite well with any operating system. It would probably be best to focus on using those and then submitting improvements to them should you make any. If the available system recovery tools become too numerous, the quality of all of them will decline due to a lack of use.

---

### Post by nerdopolis on 2010-05-29
Maybe I need to be a little more clear?

The Live CD is more or less a Linux equivalent for WinRE, or the older ERD disk for Windows. Its supposed to be used for when you can't boot, your system, or load X or something. 

I could not find any live CD's like this after searching on Google. All I could find out there was many *data* recovery CD's, for pulling data off an accidentally formatted partition, like TestDisk.

(I admit, I think the Ubuntu DVD's offer an option to get a bash prompt for an unbootable system, but this one gives you a **GUI**)

It's going to recovery tools *on* it, (it has a few, but not enough). If you know of any good ones please do tell, so I can throw them on the Live CD so they can be used.

---

### Post by Shining Arcanine on 2010-05-29
Try System Rescue CD:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

It includes a GUI environment and Firefox. All you need to do is execute startx.

---

### Post by nerdopolis on 2010-05-29
SystemRescueCD seems to offer a different functionality then mine...

SystemRescueCD seems to have more partition and filesystem related tools on it, as this CD here basically mounts a filesystem of an existing system, and chroots into it, automatically.

EDIT: I have a screenshot of what it does on Page 3

---

### Post by Phrea on 2010-05-29
I know I'm out of my place here.. ..but, sir, you are spamming.

Apparently people aren't interested, so stop bumping your own thread.

---

### Post by nerdopolis on 2010-05-29
:confused:  You did mention that already. (my last post was in reply for **Shining  Arcanine**, not a bump... )

Please understand, I put a lot into making this  script, so its kind of hard for me to let this thread sink, forever  forgotten. I thought it would be useful for the Ubuntu/Linux community,  and I felt Ubuntu/Linux had been missing something like this for a long  time. I'm not expecting fame on Phoronix, or the H or anything, I'm just  looking for feedback on what I have.

---

### Post by Shining Arcanine on 2010-05-30
> **nerdopolis said:**
> SystemRescueCD seems to offer a different functionality then mine...

SystemRescueCD seems to have more partition and filesystem related tools on it, as this CD here basically mounts a filesystem of an existing system, and chroots into it, automatically.

EDIT: I have a screenshot of what it does on Page 3

As far as I can tell, System Rescue CD has all of the functionality that your attempt at a Rescue CD has. If you cannot see that, then I think you are not looking hard enough.

I mount and chroot drives all the time when I use System Rescue CD. I will say that it does not do that automatically, but at the same time, System Rescue CD would be less functional if it did that automatically, because there are commands that you cannot do after you have chrooted into a system, such as parted.

---

### Post by nerdopolis on 2010-05-30
> **Shining Arcanine said:**
> As far as I can tell, System Rescue CD  has all of the functionality that your attempt at a Rescue CD has. If  you cannot see that, then I think you are not looking hard enough.

I mount and chroot drives all the time when I use System Rescue CD. I  will say that it does not do that automatically, but at the same time,  System Rescue CD would be less functional if it did that automatically,  because there are commands that you cannot do after you have chrooted  into a system, such as parted.

Maybe I should have said it targets a different skill level, rather  then having a different functionality?#-o  This live CD is more people who don't know what chroot is, and don't  know how to work around running a graphical application in a chroot.

SystemRescueCD IMHO seems to be for users that have more experience.

---

### Post by Shining Arcanine on 2010-05-30
> **nerdopolis said:**
> Maybe I should have said it targets a different skill level, rather  then having a different functionality?#-o  This live CD is more people who don't know what chroot is, and don't  know how to work around running a graphical application in a chroot.

SystemRescueCD IMHO seems to be for users that have more experience.
In that case, the issue is that users need to learn. These sorts of tools for users can only become so easy to use before the only thing left to improve is users' knowledge of how they work. You cannot fix something without understanding how it works.

---

### Post by nerdopolis on 2010-05-30
I try to look at this from the perspective of a beginner, as we were all once one at some point. 

As a beginner, it can be very stressful when your system suddenly becomes unbootable/unusable and your data unaccessible, and to know how to fix it you have to suddenly learn all these new things like chroot, and xhost +LOCAL:... Its a little harder then popping in a disk that automatically does that chroot stuff for you, and gives you graphical tools and automated scripts to help you get running again. 

IMHO, I don't think we should force users to learn all that stuff, at such an inconvenient time. When your system is down, all you want to do is get it running again.

---

### Post by Shining Arcanine on 2010-05-30
> **nerdopolis said:**
> I try to look at this from the perspective of a beginner, as we were all once one at some point. 

As a beginner, it can be very stressful when your system suddenly becomes unbootable/unusable and your data unaccessible, and to know how to fix it you have to suddenly learn all these new things like chroot, and xhost +LOCAL:... Its a little harder then popping in a disk that automatically does that chroot stuff for you, and gives you graphical tools and automated scripts to help you get running again. 

IMHO, I don't think we should force users to learn all that stuff, at such an inconvenient time. When your system is down, all you want to do is get it running again.

I do not think we have a choice whether or not to force users to learn those things, because understanding them is necessary to be able to fix things. If understanding them is too much of a chore for them, then they should either not be using computers or be paying someone else to fix things for them.

Unless you can write a computer program that can think like a computer technician, you will not succeed in writing a tool that automates the task of fixing a computer. You would have a much easier time designing a computer that does not break in the first place.

---

### Post by nerdopolis on 2010-05-30
**Shining Arcanine**: You are correct, its impossible to create an  all-knowing recovery program that automatically finds the problem in the  system, and fix it without any user intervention and knowledge at all,  but IMHO that doesn't mean that there can be front ends on the live cd  for editing Grub configs and init scripts, or provide scripts that you  can double click on that are labeled  "attempt to reconfigure xserver"  that pops up a dialog that describes what its going to do, and then run  "sudo dpkg-reconfigure -phigh xserver-xorg" if you hit next, to at least try to simplify the process?

IMHO,  just because a person doesn't know what chroot is, or how to fix the x  server, or finds it all confusing, doesn't mean they shouldn't be using  Linux, or a computer at all...

---

### Post by nerdopolis on 2010-07-14
Well. OK. After finding out SourceForge does support large files, I created a sourceforge .
project.

You can download the ISO here now: [http://sourceforge.net/downloads/linuxrcd/LinuxRescueCD/LiveDiskCreAtedFromLiveDiskCreAtionScript_English_x86.iso/](http://sourceforge.net/downloads/linuxrcd/LinuxRescueCD/LiveDiskCreAtedFromLiveDiskCreAtionScript_English_x86.iso/)

Be aware that it is in a pre-alphaish testing sort of state right now, so be careful!

---

### Post by tds04 on 2010-11-29
Thanks for this.  im going to give it a shot.

---

