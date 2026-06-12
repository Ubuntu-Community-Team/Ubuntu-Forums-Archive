---
title: "Is it generally better to wait for the official release of 10.10 on home computers?"
date: 2010-09-19
forum: The Cafe
---

### Post by Artemis Fowl on 2010-09-19
I really like ubuntu, and I really want to try 10.10, but is it better to wait for the offical release?

---

### Post by Phrea on 2010-09-19
Yes.

You can run it as a virtual machine or live cd which, I think, most people do.
As a rule of thumb: stick to stable releases if that's your only computer/os.

On a personal note, I'm really really not excited about Meerkat tho.

---

### Post by Artemis Fowl on 2010-09-19
Thanks for the advice. In reply to your personal note, why are you not very excited?

---

### Post by hessiess on 2010-09-19
You can set up a system with two OS's and a shared data (not /home) partition. Have the bleeding edge OS on one partition and a stable OS on the other. then if something breaks in the bleeding edge os, just reboot.

On the shared data partition, I personally have a large ext3 part which is mounted in /home/user/ALL/. Doing this alows data to be shared transparently without the risk of conflicting config files. Just make sure the user ID on both OS's is the same, or you will run into permission errors.

BTW, after a few times, reinstalling the OS every 6 mouths gets extremely tedious and new releases only feature minor differences.

---

### Post by Artemis Fowl on 2010-09-19
> **hessiess said:**
> You can set up a system with two OS's and a shared data (not /home) partition. Have the bleeding edge OS on one partition and a stable OS on the other. then if something breaks in the bleeding edge os, just reboot.

On the shared data partition, I personally have a large ext3 part which is mounted in /home/user/ALL/. Doing this alows data to be shared transparently without the risk of conflicting config files.


I'm sorry, but I don't quite understand a lot of that. I've heard ext3 and ext4 talked about, but I do not know what they are. The second paragraph doesn't really make any sense to me, but thanks.

---

### Post by phrostbyte on 2010-09-19
Yes! But don't let that stop you from playing around with the Beta.

---

### Post by hessiess on 2010-09-19
> **Artemis Fowl said:**
> I'm sorry, but I don't quite understand a lot of that. I've heard ext3 and ext4 talked about, but I do not know what they are. The second paragraph doesn't really make any sense to me, but thanks.

Hard drives can be spilt into multiple low level ``files'' called partitions, each partition can be formatted with a file system (ext3/4 etc).

On DOS/Windows, different partitions are identified using drive letters. *NIX does not do that, instead it allows different partitions to be mounted *absolutely anywhere* in the file system.

For example you could have one partition that stores the root of the file system, analogous to c:/. Then have a completely different partition mounted *within* the root partition for storing user data (/home).

Once you understand this, it is immensely powerful but it is hard to grasp to start with. If you want to learn, try experimenting with partitioning under VirtualBox.

---

### Post by Artemis Fowl on 2010-09-19
Thank you, but again (I'm really sorry) I don't quite understand about having a partition mounted in the root partition.

---

### Post by The Cog on 2010-09-19
In windows, different partitions show up as C:, D: etc. Unix/Linux is different. One partition is mounted as / (called the root partition) and you can optionally mount other partitions that then show up as folders somewhere inside the directory tree. In windows, it is common to use C: for the system and D: for user data. The equivalent in *nix is to have the system mounted as /, but to mount a separate partition at /home so that all the users data is on the second partition. In both cases, you can reinstall the OS on the system partition without overwriting the user data on the other partition.

A further trick with Linux is to have two or more system partitions. You boot up whichever system partition you want to run as /, but both of them can use the user partition as /home so the same user files appear in the same place on both systems.

As for trying Maverick - I tried it a couple of weeks ago and gave up after a few days, moving back to Lucid. Too much didn't work. I hope that's just because it's a beta.

---

### Post by lovinglinux on 2010-09-19
> **The Cog said:**
> As for trying Maverick - I tried it a couple of weeks ago and gave up after a few days, moving back to Lucid. Too much didn't work. I hope that's just because it's a beta.

I'm on the same situation. To be honest, I don't think I will upgrade Ubuntu this time. Although I usually upgrade when a new beta is available, Maverick didn't work well for me. Basically Dolphin was unusable due to dbus issues, the Update Manager crashed all the time, nvidia driver wasn't that good, the plasma monitors were messed  and I didn't see anything that would make me stick with it. I'm on KDE tho.

When I tried to fix the dbus issue, the system stopped recognizing devices like sound card and DVD drives. So I installed Lucid again. Lucid is working fine and is a LTS release, so I think this time I will pass the upgrade. Already installed the OS 3 times this month and don't want to do it again.

---

### Post by Frogs Hair on 2010-09-19
I will wait for the finished product. I haven't seen much written about 10.10 here in the Cafe , maybe because it's not LTS . There seemed to be a lot more of a buzz prior to the Lucid release.

---

### Post by chriswyatt on 2010-09-19
Depends whether you live life on the edge or not.  And also how willing you are to fix problems should they come about.

I've always used Ubuntu beta releases and have generally gotten on OK with them.  Had the occasional time where I haven't been able to boot up or the odd crash here and there, but that's to be expected.

---

### Post by NightwishFan on 2010-09-19
I would wait as was said use Live CD or Virtualbox.

As for Maverick, the upstream 2.6.35 kernel has LOADS of issues on my hardware and I am spinning in circles figuring out why. As much as new stuff works (my touch-pad yay) other stuff does not. Such as the frame-buffer, Intel Graphics Performance.. Alsa..

Mavericks configuration works quite well, but not well enough. That is why I test though.

---

### Post by 2cute4u on 2010-09-19
Maverick has tons of problems running in a vmware virtual machine.  The indicator applets crash all the time, and menus leave ghosts.

---

### Post by Linye on 2010-09-19
Lol

---

### Post by andrewabc on 2010-09-20
> **Frogs Hair said:**
> I will wait for the finished product. I haven't seen much written about 10.10 here in the Cafe , maybe because it's not LTS . There seemed to be a lot more of a buzz prior to the Lucid release.

That is because there is a forum specifically for that.
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

I had some issues with testing 10.10, although for all I know it was due to a faulty keyboard. I assume they fixed all the apps that were randomly/constantly crashing (such as update manager and screenshot app).

I'm excited about it due to new kernel, drivers, and updated software. I skipped 10.04, so for me 9.10 is getting out of date and I want to use newer ubuntu version that supports SSD.

I would wait to test with the RC September 30 if you don't test often. Liveusb works best for testing.

---

### Post by ubunterooster on 2010-09-21
I've been using 10.10 for a while. It works well. I usually jump in on the beta but think it is probably safer to wait till the RC, which has come out, I believe.

---

### Post by DeadlyWolf on 2010-09-21
September 30th for RC, I believe.


[https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule)

---

### Post by grahammechanical on 2010-09-21
If you are still having a problem understanding what a partition is, then, think of them as pretend additional hard discs. Like a hard disc they can be formatted separately. So, if you have a partition for testing Beta editions then if things go wrong it will not affect your working installation which is on another partition. Deleting or over-writing the faulty Beta will not wipe out your data.

I have 4 partitions. One for 10:4 with a mount point of /, another mounted as /home, which "Places" sees as Home Folder. Both partitions are treated as one space by the OS. There are two other partitions. In one I have an installation of Mythbuntu, which does not even load (must make better use of this wasted space). In the other I install the latest version of Ubuntu to try it out before I install it on the  working OS partition.

regards. 

regards.

---

### Post by A_Nonny_Moose on 2010-09-21
I have two internal and two external hard disks.  Of the two internal, I use one for production, and it is loaded with 10.04.1 LTS.  I use the other disk as a test bed, and it currently has 10.10 beta.  There is a problem with my video driver, and I cannot get up in high-res graphics.  So, I can't really test this with Xwindows running, so I am waiting for a fix.

---

### Post by Mark Phelps on 2010-09-21
To answer the original question ... unless you're really into experiencing the bleeding edge of Ubuntu development, quite adept at diagnosing and fixing problems, and have some way to restore (or return to) your previous stable environment should some major problem occur ... then yes, it generally better to wait.

If some day, Canonical would finally get around to providing some kind of roll-back feature such that an "upgrade" to a pre-release version first saved off the current system stuff, then upgrading and running a beta, or even an alpha, would be relatively risk-free.

But, given the frequency of "I upgraded to the Alpha/Beta/RC and now my PC won't boot -- help me!!" posts we get, since these same folks often make no attempt to backup their stable version, as a general rule, it is better to wait.

---

### Post by forrestcupp on 2010-09-21
> **Artemis Fowl said:**
> I'm sorry, but I don't quite understand a lot of that. I've heard ext3 and ext4 talked about, but I do not know what they are. The second paragraph doesn't really make any sense to me, but thanks.

> **Artemis Fowl said:**
> Thank you, but again (I'm really sorry) I don't quite understand about having a partition mounted in the root partition.

Judging by some of your responses, I'd say that you, personally, need to stay far, far away from using any form of Alpha or Beta software.  You need to learn a lot about how things work before you start using unstable software, or you'll just give yourself and all the nice helpers here *a lot* of headaches.

No offense meant.  There will come a time when you're more knowledgeable, and at that time, you'll be installing alphas and betas with ease.

---

### Post by Random_Dude on 2010-09-21
Why not wait two weeks or so until it comes out?

It's probably not worth some headaches just so you can try it earlier. ;)

---

