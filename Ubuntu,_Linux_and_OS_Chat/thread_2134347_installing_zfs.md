---
title: "installing zfs"
date: 2013-04-10
forum: Ubuntu, Linux and OS Chat
---

### Post by bgeek12 on 2013-04-10
Let me preface by saying that I've been a unix administrator off and on for decades.  I haven't spent much time with ubuntu.  Perhaps that was the problem.

I've been running solaris 10 and 11 on some servers solely to support some zfs filesystems at home for various archives.  I'm kinda tired of solaris and it's implementation of smb, so I wanted to move to something "easier" and newer.  So I read a bit on linux with zfs and toss my hat into the ubuntu crowd.

I was totally unprepared for the adventure.


I installed the desktop OS.  Where's the dang terminal app?  Can't find it.  Spent a couple minutes searching.  Found out how to start up a terminal session.  Could it be more difficult to start a terminal window?  Maybe.  Why make it so hard?


I punted the desktop and installed the server OS.  Terminal is easy to find.  Nice.

I read the ubuntu zfs page  [https://launchpad.net/~zfs-native/+archive/stable](https://launchpad.net/~zfs-native/+archive/stable) and tried to see which build of zfs I need.  I'm running Ubuntu 12.  So I'm looking for the build for ubuntu 12.  Nowhere during the download or install have I seen these names in the drop-down to select my release: "Raring, Quantal, Precise,.." until now.  WTH are those?  I'm looking for 12.  How hard is it to say "10, 11, 12"...?  Couple minutes more trying to figure out what those words mean.  Finally figure out that I need Quantal.  Ok.  I select Quantal.  I feel like I'm getting somewhere.  
On [https://launchpad.net/~zfs-native/+archive/stable?field.series_filter=quantal](https://launchpad.net/~zfs-native/+archive/stable?field.series_filter=quantal) I see "You can update your system with unsupported packages from this untrusted PPA by adding **ppa:zfs-native/stable**  to your system's Software Sources.  ([Read about installing]("http://ubuntuforums.org/+help-soyuz/ppa-sources-list.html"))"

Ok, lemme see how to do that...

This page says use deb to install the package:  I dutifully use deb:

[EMAIL="brad@ubuntu:~$"]brad@ubuntu:~$[/EMAIL] sudo deb [http://ppa.launchpad.net/zfs-native/stable/ubuntu](http://ppa.launchpad.net/zfs-native/stable/ubuntu)
sudo: deb: command not found
[EMAIL="brad@ubuntu:~$"]brad@ubuntu:~$[/EMAIL] sudo find / -name deb 2>/dev/null
[EMAIL="brad@ubuntu:~$"]brad@ubuntu:~$[/EMAIL]

no deb.

hrm.

Another hint:
[h=2]Adding this PPA to your system[/h]You can update your system with unsupported packages from this untrusted PPA by adding **ppa:zfs-native/stable** to your system's Software Sources. ([Read about installing]("http://ubuntuforums.org/+help-soyuz/ppa-sources-list.html"))


I get sent here:  [https://launchpad.net/+help-soyuz/ppa-sources-list.html](https://launchpad.net/+help-soyuz/ppa-sources-list.html)

It says:  **Step 2:** Open a terminal and enter: 
sudo add-apt-repository ppa:user/ppa-name 
Replace ppa:user/ppa-name with the PPA's location that you noted above. 

I dutifully enter "sudo add-apt-repository  [http://ppa.launchpad.net/zfs-native/stable/ubuntu](http://ppa.launchpad.net/zfs-native/stable/ubuntu)"

sudo: add-apt-repository: command not found

Where's add-apt-repository?

[EMAIL="brad@ubuntu:~$"]brad@ubuntu:~$[/EMAIL] find / -name add-apt-repository 2>/dev/null
[EMAIL="brad@ubuntu:~$"]brad@ubuntu:~$[/EMAIL]

no add-apt-repository

hrm.


Searching, I find:

[http://ubuntuforums.org/showthread.php?t=1971357](http://ubuntuforums.org/showthread.php?t=1971357)

I need to install add-apt-repository

sudo apt-get install software-properties-common

then...

sudo apt-get install python-software-properties

ok, now I have add-apt-repositories!

A little more fumbling around figuring out that I now need to run:

[EMAIL="brad@ubuntu:~$"]brad@ubuntu:~$[/EMAIL] sudo apt-get install ubuntu-zfs

Nowhere in any documentation on how to install zfs for ubuntu 12 do I find any mention of "apt-get install"

Quite the twisty maze of passages to decipher all of this.

let's see how this goes.  The kernel is still building.



Let me just say that the people that bust it to get this software working are awesome.  The time spent and the problems solved is quite impressive.  But...  Every time I dip my toes into open software, it's like herding cats.  Every release, something major changes, rendering 90% of the "how-to" blogs obsolete.  Just basic sysadmin tasks change so often, it's like you need an encylopedia to install patches.  "Red hat do this.  Ubuntu do this.  CENTOS do this.   and on and on."

Linux is kicking some microsoft and apple butt.  These types of experiences push a lot of people away.  I want a toaster.  Plug it in.  Push the button.  Toast comes out.  That's what my Mac is like: It's for editing video and sequencing music.

hopefully some day the compexity will become so great that things become quite simple.

regards

YAY this is getting somewhere...

[EMAIL="brad@ubuntu:~$"]brad@ubuntu:~$[/EMAIL] sudo zpool create -f galaxy raidz2 /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh /dev/sdi
[EMAIL="brad@ubuntu:~$"]brad@ubuntu:~$[/EMAIL] sudo zpool status
  pool: galaxy
 state: ONLINE
  scan: none requested
config:
        NAME        STATE     READ WRITE CKSUM
        galaxy      ONLINE       0     0     0
          raidz2-0  ONLINE       0     0     0
            sdb     ONLINE       0     0     0
            sdc     ONLINE       0     0     0
            sdd     ONLINE       0     0     0
            sde     ONLINE       0     0     0
            sdf     ONLINE       0     0     0
            sdg     ONLINE       0     0     0
            sdh     ONLINE       0     0     0
            sdi     ONLINE       0     0     0
errors: No known data errors
[EMAIL="brad@ubuntu:~$"]brad@ubuntu:~$[/EMAIL] df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root   28G  1.5G   25G   6% /
udev                     989M  4.0K  989M   1% /dev
tmpfs                    400M  484K  399M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     999M     0  999M   0% /run/shm
/dev/sda1                228M   27M  190M  13% /boot
galaxy                   8.1T     0  8.1T   0% /galaxy
[EMAIL="brad@ubuntu:~$"]brad@ubuntu:~$[/EMAIL]

success.  Now for some testing and smb...

---

### Post by grahammechanical on 2013-04-11
> [COLOR=#000000] I want a toaster. Plug it in. Push the button. Toast comes out.[/COLOR]

That is Ubuntu but you did not want the simple toaster, did you? Be honest. You wanted to experiment to see if the toaster would work on gas.

There is a reason why some file systems are not available when we install Ubuntu. There is a reason why there is a default file system in Ubuntu. It is for people who really do want the plug in the toaster way of installing an operating system

Regards.

---

### Post by bs27975 on 2013-04-12
> **grahammechanical said:**
> That is Ubuntu but you did not want the simple toaster, did you? Be honest. You wanted to experiment to see if the toaster would work on gas.

There is a reason why some file systems are not available when we install Ubuntu. There is a reason why there is a default file system in Ubuntu. It is for people who really do want the plug in the toaster way of installing an operating system

Regards.

+1

As soon as he said he uses a Mac, your comment applies.

Play with k/ubuntu for a while, get happy / comfortable, before going on.

Any reasonable amount of familiarity would reveal terminal or konsole, and the basic division of Debian / Fedora in distros. Of course, instead of just installing server, pressing Ctrl-Alt-F1 ...

There's a reason it's free vs why you pay so much for Mac, let alone Microsoft. For those, you pay up front, for Linux/Unix you pay as you go. (Perpetually, but that's another story.)

Note that zfs was on Solaris, not Mac, and that some unhappiness with Solaris exists.

Unrealistic expectations, searching for a magic wand ...

---

### Post by bgeek12 on 2013-04-12
Lemme see if I can respond...

The intent of my post was to lament the ongoing state of documentation  and rapid changes of basic components in open source resulting in slower-than-you-may-want  adoption.  I don't dip my toes into the open source world often, but when I do, it's painful only for these reasons and reminds me that "The nice thing about standards is that there are so many to choose from!"

You're so right about the "pay as you go" with linux.  I'd rather spend the time doing other things.

ctl-alt-f<n> is klunky in a VM and I really hated the desktop.

One or two glitches or difficulties along the path of getting ZFS working would have not prompted the post.  But... it was so much harder than it needed to be with all the misinformation and assumed tribal knowledge.

I understand why zfs isn't available when you install Ubuntu.  It's hard to miss that it's a licensing conflict.

On the upside, I can say that Ubuntu is looking pretty much like a ZFS toaster now that it's working.  I can clone this VM and tuck it away in case I break something major, or repeat the install on hardware for other ZFS toasters.

Comparing Solaris to Ubuntu on this ZFS Toaster project:
   Solaris points:
       ZFS is baked in
       docs are accurate and useful
   Ubuntu pros:
       samba is dead simple to configure
       it's not a dead platform
   Winner: Ubuntu provisionally after some validation

FWIW:  I rely on raidz2 for it's resilience and ability to recover reliably from drive failures in a large array.  It's either ZFS or RAID 10, but that costs more in hardware.  I'll do some recovery testing and try ZFS on a few more Linux distros.

my Mac?  I paid $150 for a late-gen G5 PowerMac, $120 for Final Cut Studio 2,  then dropped in a 1T drive that needed a home.  It works great and my  music sequencer software runs just fine on it.  It's turned off unless it's performing one of those "toaster" style functions.  Final Cut Studio 2 and my music apps dictate the platform, nothing else.  I tend to pick the app and find a platform to run it on.  So the Mac comment - I'm unsure whether that was intended to be a knock against me.

all the best

---

### Post by bs27975 on 2013-04-13
> **bgeek12 said:**
> Lemme see if I can respond...

I have done you a disservice too, and for that I apologize.

I should also have separately replied to your post directly. Wherein I would have said, and below ...

THANK YOU FOR YOUR POST!

Through your excellent description of what you went through with zfs, the google search term that led me to your post, I conclude what you have said ... zfs is not ready for prime time kubuntu.

I am about to add a 4GB drive to one system to replace a 2GB, and add that 2GB to another 2GB on another system, making 4GB, to receive replicated backups. So was searching for the how to on zfs, after someone pointed it out to me.

Through your post, largely, I'll forgo zfs (0.61?), and just get on with LVM.

Like your post notes, and like I feel about my cell / PIM - zfs / disks have to just work. And your post points out that that's not true for zfs, so I'll move on.

But I wouldn't have known to move on nearly as fast without your excellent post.

Thank you, VERY MUCH, for having taken the time to do so.


> **bgeek12 said:**
> The intent of my post was to lament the ongoing state of documentation  and rapid changes of basic components in open source resulting in slower-than-you-may-want  adoption.  I don't dip my toes into the open source world often, but when I do, it's painful only for these reasons and reminds me that "The nice thing about standards is that there are so many to choose from!"

There are four basic mistakes with this paragraph:

1. (Largely) open source is developed for free by developers in their spare time, working on fiddly bits that interest them. If the world paid for open source / documentation the way they do for commercial products, the documentation would be there. People get what they pay for. It is the lack of these 'filling out bits' (delivering 'user experience', if you will), in my opinion, that is the large barrier preventing larger adoption - witness the linux desktop dearth - nothing else. (However, 'sufficient' filling out bits exist server / console [cmd line] side] that linux servers have taken over the world.)

2. The rapid change is largely evolution (not to say there aren't mis-steps, a direction tried not working out). This is a double edged sword. I take your point, and don't disagree with it, but I also not only take the benefit and quicker evolution made possible by the open source development ecosystem over the commercial one, I also have to accept the speedbumps that that quicker evolution brings. It is what it is / nature of the beast. Which one learns to accept and live with. (I get that you're not there yet.)

3. Open source / how it does things, set and are the de facto standards, often becoming the documented standards. You are misusing 'standards' here. The issue with standards is that commercial software won't adhere to them, what they do adhere to remains undocumented, and even what they do document they don't necessarily or completely follow. (If it were documented and followed, you would be MUCH happier and have a much better experience with open source - the guessing and reverse engineering waste of resource consumption would cease.) It is not that open source is not adhering to standards, it is that commercial software isn't.

4. If we paid for open source the way we do for commercial software ... well, we wouldn't be having this conversation. We'd be too busy getting on with using the hammer, rather than talking about the hammer's nature.

> **bgeek12 said:**
>  You're so right about the "pay as you go" with linux.  I'd rather spend the time doing other things.

Yep, but that's not open sources fault. It bugs my **** that I have to re-learn how to do what I've been doing for 30 years. However, I eventually concluded ... unlike commercial software, once I learn the open source one, the learning curve is done. The next service pack or 'OS' isn't going to put me back on the learning curve treadmill of ... ok, so what are they calling it NOW!!! Once I've grokked the open source hammer on a particular beastie, forever onwards I get on with using the hammer. With each commercial service pack or OS, I have to relearn how to use the hammer. I choose to no longer be on that treadmill.

So, and I get that it's not intuitive, eventually one comes to understand ... learn it only once (more) ... and you're done. So I'll put the annoying re-effort to learn it just once more. And then move on.

> **bgeek12 said:**
> ctl-alt-f<n> is klunky in a VM and I really hated the desktop.

Yep, but again, that's not open sources fault - those keystrokes existed long before the vm software. In the mean time ... Alt-F2 (== start/run), 'konsole' or 'terminal', done.

> **bgeek12 said:**
> One or two glitches or difficulties along the path of getting ZFS working would have not prompted the post.  But... it was so much harder than it needed to be with all the misinformation and assumed tribal knowledge.

I understand why zfs isn't available when you install Ubuntu.

Agreed (so much harder), and wouldn't have known that if you had not 'open sourced' yourself and written your message. Thank you again.


> **bgeek12 said:**
>  It's hard to miss that it's a licensing conflict.

That's largely a misstatement - as I understand it, two bits of code, different licensing agreements, so can't bundle together, but can coincide. The issue is the conflict means it can't directly go in the kernel (currently). Nothing says it can't be installed at the same time as the OS, if they chose to do so, and if it were ready for prime time. Certainly lots of other software is installed at the same time, often I expect, under different licensing models. Just, beside each other, not within. Apache particularly comes to mind. 

> **bgeek12 said:**
> On the upside, I can say that Ubuntu is looking pretty much like a ZFS toaster now that it's working.  I can clone this VM and tuck it away in case I break something major, or repeat the install on hardware for other ZFS toasters.

That's still just weird (in a vm), but I sure get the figure it out and make the mistakes in a vm rather than in real hardware.

But then, real hardware would also eliminate your keystroke in a vm issue. (-:

> **bgeek12 said:**
> Comparing Solaris to Ubuntu on this ZFS Toaster project:
   Solaris points:
       ZFS is baked in
       docs are accurate and useful
   Ubuntu pros:
       samba is dead simple to configure
       it's not a dead platform
   Winner: Ubuntu provisionally after some validation

I'm not so sure I agree with you. I need my disks to 'just work' just like I do my cell. I'm not sure in your place I wouldn't want a solaris zfs toaster, since, as you say, it's baked in.

But I'm sure glad to have been able to read what your mileage was.

> **bgeek12 said:**
> FWIW:  I rely on raidz2 for it's resilience and ability to recover reliably from drive failures in a large array.  It's either ZFS or RAID 10, but that costs more in hardware.  I'll do some recovery testing and try ZFS on a few more Linux distros.

You're not going to be happy no matter what you do, learning curve wise - two real flavours out there, both with their own learning curve - debian (like k/ubuntu) based and fedora (red hat) based. deb vs rpm. Then you have hybrids like SuSe, which use yum but are still debian based. I think for what you are talking I would head over to CentOS and stick there. But would also say SuSe (maybe, over kubuntu, given canonical's drop of it) for desktop. And each of these have their own (so much for only learn once) peculiarities. Aside from continuing to type 'cmd' occasionally from a command prompt ... eventually you keep each straight. Not without that pay as you go drain I mentioned.

Care to talk about video change, if you want to talk about annoying re-learning? Beta, VHS, CD, DVD, PVR, cable, standard def, high def, dvi, hdcp, netflix, hulu ... I just want to sit down and be entertained for an hour people! On my schedule, not the network's!

Guess it's not just computers, and we may as well just learn to live with it. (Agreed, sadly.)

> **bgeek12 said:**
> ... RAID 10 ..

10-4! For me, determined some years ago, it makes more sense to duplicate systems, replicate nightly, and gain so much more redundancy than just disks. YMMV. (Home, not commercial environment. In commercial, such duplication not cost reasonable, and probably dealing with blades / fibre channel raid'ed disk arrays ... and zfs doesn't even come into the equation. That's the disk array vendors problem.)

With the replicas, re-link to the other replica at failure, finish what I'm in the middle of, THEN deal with the hardware issue. No more, stop the world if a MB, or any other piece of hardware fails, not just a disk.


> **bgeek12 said:**
> my Mac?  I paid $150 for a late-gen G5 PowerMac, $120 for Final Cut Studio 2,  then dropped in a 1T drive that needed a home.  It works great and my  music sequencer software runs just fine on it.  It's turned off unless it's performing one of those "toaster" style functions.  Final Cut Studio 2 and my music apps dictate the platform, nothing else.  I tend to pick the app and find a platform to run it on.  So the Mac comment - I'm unsure whether that was intended to be a knock against me.

It has been my experience that people with Macs want toasters. And that's no bad thing. Mac hangs together and 'just works'. People get on with doing. But only what Mac lets you.

However, as soon as you say solaris, or open source, or kubuntu ... you become almost diametrically opposed to 'Mac'. So, in general, if you like a Mac, you're not going to be happy as soon as you go anywhere else. Nothing else has the dollar inflow to provide all the filling bits that make the Mac experience so excellent. So ... if consumers put the same money into open source that they do into commercial software ... loop back to top of message.

One comment I have heard and tend to think is probably true ... once you want to go beyond that with a Mac, you're in to a level of difficulty and complexity that is just as 'bad' as any other OS. As soon as you want to go there, people have lost the very advantage for which they (usually) bought Macs, and become unhappy. (Discovered, too late.)

> **bgeek12 said:**
> all the best

And to you to. And thanks for taking the time to respond to my bad.

---

### Post by bgeek12 on 2013-04-15
I don't think your reply was "bad" but I would say it was easy to  interpret it that way.  1st time I read it, I misunderstood.

All valid points you make above.

However, I would add:

I misspoke.  It's REALLY EASY to get zfs working on Ubuntu 12.  It's just takes a small amount of tribal knowledge to know how, or some sleuthing to figure out how.

Since I don't mess with open source much lately, I don't keep up with the tribal knowledge.  Ubuntu has this image of "easy Linux" in my mind.  That is true until the GUI lacks what you need.  Then its down into the shell.  So "bad me" for trying to take the easy linux image to the lower levels.  I'm comfortable in the shell.  I spent many years delivering C and ksh code.  I just don't go there any more for the fun of it

I agree with what you say about open source.  Developers and people who give free time to open source do so, I think, because they like to build code and build cool stuff.  Delivering documentation isn't as fun.  But... I still lament that the documentation, being what it is, holds a lot of the audience at arm's length.  I believe that the open source community wants broader adoption.  Better documentation would help a lot in that regard.  But it is what it is.

You mentioned Relearning!  You nailed it there.  For example: "OMG what's the flipping package installer / updater called now?"  That's so annoying.  That alone drives me nuts.  Not only because it was probably completely unnecessary, when you find good blog "how-to" posts, chances are they're obsolete and don't call out the release they're good for.

Actually, I am happy with what I have.  I want a large storage array that has reasonable performance and is resilient to drive failures.  Any data considered important, I keep in a minimum of two places - replicate - as you do.  I don't mind digging in a bit to learn ZFS because I need to be familiar with it when I have to replace a drive.  Plus, it has this "cool factor".  I've had one drive fail, and two go offline on the 1st array before I had a replica.  Scary, but I didn't lose any data.  I replicated everything when the two went offline before I tried a repair.  Both repairs were flawless.  Kudos to ZFS for being solid.

Solaris provided me with this type of platform two boxes until samba stopped working on one of them.  After spending 3 hours trying to get samba working again, I started looking for something on Linux.  Linux has a rep for "easy mode" samba.  I had heard that some Linux variants were supporting ZFS.  Ubuntu came to mind.  Here we are.

And.... after running this for a while I am beginning to question the value of raidz2.  Time to re-examine - thanks for the prodding.  Once I started replicating, the value of raidz2 went down a bit.

BTW: I can still read my 5.25" floppies if I need to.  The DOS ones, not the TRS-DOS ones (I think I tossed those).

You're so right about "getting on with doing."  I don't want to fiddle with the OS on a video editor or when I'm messing with music.  But I do dive into the command-line to get selective backups of my critical data replicated out to the storage farm.

Oh, and...

Why do I run one of these arrays in a VM?  For all the reasons anyone would run a VM.  The later hypervisors let the VM have access to the physical drives easily, so performance is plenty high.  I run a few more VMs on the same box.  Why have all that CPU and RAM sitting idle 98% of the time?

cheers

---

