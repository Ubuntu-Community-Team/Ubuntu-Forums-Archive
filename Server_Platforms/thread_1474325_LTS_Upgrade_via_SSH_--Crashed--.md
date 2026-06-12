---
title: "LTS Upgrade via SSH --Crashed--"
date: 2010-05-05
forum: Server Platforms
---

### Post by zenon212 on 2010-05-05
I have looked around a bit but I can't even get my head around what to do next.

I attempted to upgrade my headless Ubuntu server from 8.4 LTS to 10.4 LTS last night.  I used **screen** so that I could reconnect because the update said that although SSH may crash, I should be able to get back on via port 9004.  When I tried to get back on this morning I could not SSH in via port 22 or 9004, so I did the only thing that I felt that I had left--I rebooted.  I have since had to dig out an old monitor and keyboard and put a head on it to try and get this problem resolved.

When I boot the computer, GRUB gives me the option of **kernel 2.6.32-21-generic-pae**, but when I pick that I get the following error and the Caps and Scroll lights on the keyboard just blink.

[INDENT]Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)[/INDENT]

I next have the option of **kernel 2.6.32-21-generic-pae (recovery mode)**, but when I choose that option I get a screen full of time dated lines that do not make any sens to me and that same previous error message somewhere in the middle of it all.

If I try to boot to any of the old kernels, then I get a screen full of error messages and get dropped to an **ash** shell, BusyBox v1.13.3

Obviously the computer was in the middle of asking me something very important when I rebooted, but without being able to log in, I was never going to find out what that was.  I guess I assumed that it wasn't a big deal because all of this was probably sorted out already as a possible chain of events on a headless server upgrade.

The bottom line is that my server no longer works and I do not have a clue as to how to get it up and going.  If you have ever experienced this situation and have gotten through it or you actually do know something about this situation, please help me out.

My server is no longer headless, but I am now definitely clueless.

Thanks,
Brad

---

### Post by byStanderone on 2010-05-05
...some say that an upgrade of an lts to an lts is possible, but haven't seen a clear cut info if it really works, and there are threads that say that it could not be done, tho haven't tried it personally, logically i'd say it can not be done.

---

### Post by zenon212 on 2010-05-06
I guess I just assumed this was what you were supposed to do with an LTS system.  But it IS starting to feel like you are correct.

---

### Post by TheFuturian on 2010-05-06
It could have been the grub update that caused your headache, sometimes the option of "root (0,0)" isn't accurate. Depending on your harddrive configuration this may need to be "root (0,1)", "root (0,2)", etc etc. You can drop to a command shell within the Grub menu and use commands like [find]("http://www.gnu.org/software/grub/manual/html_node/find.html#find") to try and work out the correct option.

Attempting the dist-upgrade locally was unfortunately just as awkward. Thankfully I had the option of cancelling the process as I'd took a snapshot first. I got no less then 10-15 prompts about configuration files that the package maintainer wanted to replace, all of which I had heavily customised. I also got a few erroneous errors as attached. For me it looks like it's gonna be a matter of setting up a new 10.04 server and migrating each service on my 8.04 server across one by one :-S. Not as quick, but at least I can be sure that all goes smoothly before turning off the old box.

---

### Post by zenon212 on 2010-05-06
Grub doesn't seem to be the answer because the boot entry seems to be set to the proper drive location.

**find /boot/grub/stage1** returns **(hd0,0)** and that is what **root** is set to in all of my boot entries.

That was a very informative path to follow, though.

Do you have any more ideas?

---

### Post by zenon212 on 2010-05-07
Still no takers?  Is there no one that has experienced this before?

---

### Post by arrrghhh on 2010-05-07
> **zenon212 said:**
> Still no takers?  Is there no one that has experienced this before?

I'm not very well-versed in recovering Ubuntu or even Linux systems in this type of a state... I hate to say it, but you may be in for a rebuild.  I had to rebuild mine for 10.04, but that was mostly my doing :D

After reading over this thread again, have you tried reinstalling GRUB to the MBR?  I know you don't *think* it's GRUB, but it seems like something is definitely messed up in relation to GRUB.  Perhaps it was trying to update to grub2, was waiting for your input, and on the reboot failed?

---

### Post by zenon212 on 2010-05-07
Is Ubuntu still so unstable that we can't actually fix problems?  Are we still in the stone age era with Linux?  Is a wipe and reinstall still the best solution?

---

### Post by arrrghhh on 2010-05-07
> **zenon212 said:**
> Is Ubuntu still so unstable that we can't actually fix problems?  Are we still in the stone age era with Linux?  Is a wipe and reinstall still the best solution?

No, I'm just saying I'm by no means an expert, and from the sounds of it you upgraded your system by skipping a couple of releases... without monitoring it... which is not recommended.

Perhaps someone smarter with Linux than I, can help.  I'm just saying from the sounds of it, YOU hosed YOUR system.  No blaming Ubuntu here.

---

### Post by zenon212 on 2010-05-07
arrrghhh,

I am not ruling out GRUB as a possibility.  I just have no idea how to resolve the issue because, as I originally stated "I can't even get my head around what to do next."  I suspect that GRUB is the issue, my expertise just does not lie in the Linux booting process.  I am more than willing to learn and this is a great opportunity to learn more about the boot process, but all I have ever done with GRUB was purely on a newb level.

And I get that you were suggesting that I hosed my system, but I am not sure what I did wrong. It was a headless system and I could not get into it.  I didn't want to reboot, but I don't see what other option I had.  I appreciate your need to step up your point one more level because it appeared that I wasn't getting it, but I was more or less trying to taunt someone else into jumping in on my problem.  I thought maybe questioning the stability of Ubuntu would draw some guru into the mix so that he/she could point out how simple the solution was, thereby actually giving me some sort of direction.

You see, I have a big fear on these forums that once a post has been responded to then others feel like it is a done thread and move on.  There are people out there looking for ways to help and when they see the RE: on a post, then they figure it is being worked on.  That may not be true, but that is my fear.

Anyway, I may be too clueless to figure this out.  In fact, I may be too clueless to even have a server, although it has served me well these last two years. Or maybe there really is a legitimate solution to this without having to wipe the drive and reinstall the server and have to fight back through configuring all of my services to the way that I had them.  I have crossed those hurdles, now I want to try to figure out how to get over this one.

What are your thoughts, arrrghhh?

---

### Post by TheFuturian on 2010-05-08
Whenever I've been completely caught out I've "chrooted" into the environment to see if there's anything I can see/do. I believe a reinstall of grub can also be attempted by using this technique. Before Ubuntu I was a Gentoo newbie, from this experience I had used the "Mounting the /proc and /dev filesystems" and the "Entering the new Environment" stages of the [handbook]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=6").

I appreciate the link may not be the most welcome in this forum, however as you rightly point out there is no simple guidance to the situation. You'll need to boot from an Ubuntu CD and get to a terminal in order to accomplish this, also don't forget to mount your root filesystems first:-

```
mkdir /mnt/ubuntu
mount /dev/***sdax*** /mnt/ubuntu

mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev

chroot /mnt/ubuntu /bin/bash
env-update
*>> Regenerating /etc/ld.so.cache...*
source /etc/profile
export PS1="(chroot) $PS1"
```

---

### Post by arrrghhh on 2010-05-10
My thoughts unfortunately have run out... You can certainly try to boot from a LiveCD and see what you can see.  If reinstalling GRUB doesn't fix it, I'm not sure what the issue could be.  Unfortunately my Ubuntu-fu is not that great...

---

### Post by zenon212 on 2010-05-15
I could not find any way to recover from my crash.  After a week or so of searching and pondering, I wiped my drive and installed 10.4 from the CD.  I am glad that I had my /home folder on a separate partition.

I guess Ubuntu is not ready for headless just yet.  Maybe some day it will rise to that level.

---

### Post by jerome1232 on 2010-05-15
Just wanted to chip in to say my little headless server upgraded from 8.04 to 10.04.

I ended up wiping it out anyways because I wanted to switch to ext4. Reconfiguring it wasn't an issue since it's just a mumble server.

But you shut the thing down in the middle of an upgrade and you expected it to recover? Isn't this the reason to keep backups of a server?

just my 2cents.

---

### Post by lavinog on 2010-05-16
> **zenon212 said:**
> 
I guess Ubuntu is not ready for headless just yet.  Maybe some day it will rise to that level.

It can always be handy to have a monitor handy just in case.
A $30 kvm switch could be a good investment too.

---

### Post by zenon212 on 2010-05-16
Hey, jerome1232, I thought I already stated the obvious, but thanks for the redundancy.  So what would you have done in that situation?  Of course, you could suggest that you would not have gotten into that situation, but that doesn't really take brains.  So if you were in that situation what would you have done?

Also, I do have backups of my server, you just can't really reinstall over a crash.  I guess that I could reinstall the old 8.04 and then restore, but of course I want to go forward, not back.

---

### Post by jerome1232 on 2010-05-16
I didn't mean to come off as blunt, I think I tend to do that sometimes.

My point was the release upgrades can, should, and have worked (for me at  least) via ssh.

You just came off as "omg server died when it got powered off in the middle of a release upgrade, this is so unstable!" to me.

I would have at least hooked up the monitor and keyboard *before* rebooting the thing when it was possibly in the middle of a release upgrade.

I think it's easier to just reinstall and restore configurations from backups than to go for an indepth attempt to recover an install that is quite possibly borked beyond my ability to recover.

Then again hooking up a monitor is not an option for servers that truly are remote, but usually data centers will reinstall the os for you if it comes to that. You can then use your backups to get your configurations back to where they were before the server catastrophically blew up. I know Ubuntu isn't a limelight server distro but I also understand it is used in the real world for that purpose.

---

### Post by zenon212 on 2010-05-16
This was a very frustrating ordeal for me.  I probably would not have even tried to do it headlessly if it hadn't told me that I could recover it on a different port.  Once I let time go by, I came to terms with the extent of the situation.  Ultimately it just means that I have to re-figure out everything that I fought to figure out the last few years.  For a lot of this stuff, you delve into it long enough to get the way you want it and then you move on.  I do have backups and once I figure out how to extract single files from in nested folders via command line, I will be much happier.

Maybe my expectations were off in the first place, but I suspect that most people that try to use Ubuntu headlessly and make sure that there is a path for recovery if there is a problem and then find out that it just doesn't work that way would question the stability of the distro.  Maybe most of them would not voice that here, but that doesn't mean that the questioning process does not happen.  But note, that I did say that I only made that statement in order to draw someone in who may actually know something about the situation.  Which is what I requested in the first place.

Often times, people think that they are helping by chiming in when they really do not know how to help.  If no experts posted fixes I would eventually figured out through googling that no one had a clue how to resolve the issue.  But sometimes when you haven't fully given up on getting a solution someone comes on and points out that your situation is hopeless.  Even if they offer a little helpful advice in the process, it does much more to demoralize someone that is stressed out than it could ever help.

I appreciate any actual help that anyone gives me and I am sorry if I came off as flippant, but no one wants to hear that they should just give up and no one wants to hear that they should have just done it differently in the first place.  In fact, two years from now when I go through this again, I will probably have completely forgotten all of this.  Let's hope not, but I probably will.

I love Linux and I love Ubuntu far better than any other distro that I have ever tried.  But there is so much to know that no one, not even Linus himself, can know it all or even come close.  That doesn't mean we can't have fun trying.  Well, there will be times like these, but most of it is really fun.

---

### Post by zazuge on 2010-11-06
your story with a bad and sad ending made me stop of wanting to upgrade via ssh the two servers at the company
well because the head of IT departement doesn't tolerate downtime on dayworktime
since the time i migrated from Fedora2 and Redhat 9 shriek to Ubuntu 9.04 
(because of the diference in implice default values of in samba config file)
i had only one option and that to upgrade past wortime hours at night via ssh
but if that will break the system like that then i better test it with my computer at home (i plan to connect to my PC via ssh from my laptop) 
well the lesson i learned from your experience is to never go the easy way (to wipe it out clean) because that you'll never learn from the mistakes and the problems
i found a link witch my help future attempt to migrate (but hadn't test it yet)
[http://library.linode.com/troubleshooting/upgrade-ubuntu-10.04](http://library.linode.com/troubleshooting/upgrade-ubuntu-10.04)
hope that help because this thread didn't solve the problem (no solution was posted nor the problem was pointed at with certainty )

---

### Post by CharlesA on 2010-11-06
If you are going to do an upgrade over SSH, at least make sure there is a monitor and keyboard connected to the machine and use screen, so that everything is still running in case you get disconnected.

Oh, and make sure you have a good backup before even attempting to upgrade, in case something goes wrong.

---

