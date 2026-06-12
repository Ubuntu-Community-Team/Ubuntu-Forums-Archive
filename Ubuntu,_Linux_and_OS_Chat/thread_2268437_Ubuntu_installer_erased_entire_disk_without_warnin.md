---
title: "Ubuntu installer erased entire disk without warning"
date: 2015-03-08
forum: Ubuntu, Linux and OS Chat
---

### Post by alice7 on 2015-03-08
Sadly, this thread is not a joke. I booted into a live Ubuntu 14.04.2 usb, clicked install. My disk had an arch linux partition and a Fedora 21 LVM partition. The menu options available were "something else", and "erase disk and install ubuntu", with a sub-option for "use LVM". I initially missed that "use LVM" was a sub-option for "erase entire disk," so I selected that and pressed continue. But, of course, it wasn't going to erase the disk without double checking with me! A window popped up that said something like "are you sure you want to write these changes to disk." I clicked "no." It did it anyway. I tried exiting the whole installer and booting up again, but there was nothing left on my disk to boot. Going back to the ubuntu installer on the live usb showed my whole disk as free space. 

Maybe there was some way to recover the data, but I didn't have time to mess around with it and didn't have that much important data on the other partitions anyway, so I ended up just installing ubuntu on the whole disk. Honestly I'm shocked, and I don't think I can continue using ubuntu after a bug as catastrophic as this. What I did was slightly dumb, but the installer should offer at least some protection from accidents like that.

---

### Post by Bucky Ball on 2015-03-09
*Thread moved to **Ubuntu, Linux and OS Chat**.*

That is bad news, but not a support thread. I always use 'Something Else' and backup anything I don't want to lose before installing. 

Hope things go better for you in future.

---

### Post by sudodus on 2015-03-09
I'm sorry that your drive was wiped without your intention.

Installing operating systems is always risky. All editing of the partition table is risky. I agree with Bucky Ball, it is important to backup everything you don't want to lose before such operations.

---

### Post by buzzingrobot on 2015-03-09
> **alice7 said:**
> ...A window popped up that said something like "are you sure you want to write these changes to disk." I clicked "no." It did it anyway.


If you can repeat and verify that, it sounds worth reporting as a bug.

 > I tried exiting the whole installer and booting up again, but there was nothing left on my disk to boot. Going back to the ubuntu installer on the live usb showed my whole disk as free space. 


Every Linux installer I've used, with one exception, begins drive partitioning and formatting as soon the user gives the OK. The partitioning takes a split second and the formatting generally runs in the background as the installer moves on to the next matter.

The exception is the Anaconda installer used in Fedora and the Red Hat family. Individual install functions are grouped in a central hub.  The user may re-execute and alter each component as often as necessary. Changes to the drives do not begin until an explicit "Begin Installation" button is clicked.

---

### Post by cmcginty on 2015-10-04
> **buzzingrobot said:**
> If you can repeat and verify that, it sounds worth reporting as a bug.



Hey this just happened to me too. I backed out when it said "are you sure". Rebooted and now my LVM volume group is gone, replaced with the installer version. Has this been reported as an official bug yet? This just really ruined my day. I'm going to try and see if I can rebuild the LVM info, but i've never tried to recover something like this before.

---

### Post by RichardET on 2015-10-04
> **alice7 said:**
> Sadly, this thread is not a joke. I booted into a live Ubuntu 14.04.2 usb, clicked install. My disk had an arch linux partition and a Fedora 21 LVM partition. The menu options available were "something else", and "erase disk and install ubuntu", with a sub-option for "use LVM". I initially missed that "use LVM" was a sub-option for "erase entire disk," so I selected that and pressed continue. But, of course, it wasn't going to erase the disk without double checking with me! A window popped up that said something like "are you sure you want to write these changes to disk." I clicked "no." It did it anyway. I tried exiting the whole installer and booting up again, but there was nothing left on my disk to boot. Going back to the ubuntu installer on the live usb showed my whole disk as free space. 

Maybe there was some way to recover the data, but I didn't have time to mess around with it and didn't have that much important data on the other partitions anyway, so I ended up just installing ubuntu on the whole disk. Honestly I'm shocked, and I don't think I can continue using ubuntu after a bug as catastrophic as this. What I did was slightly dumb, but the installer should offer at least some protection from accidents like that.

maybe your drive was partitioned incorrectly;  I doubt it's a "bug."  Reminds me of someone I knew who always claimed SAS had a bug;  no, it could never be her program!

---

### Post by ian-weisser on 2015-10-04
> **cmcginty said:**
> Hey this just happened to me too.

Well, I don't see a bug report from the OP, so if you can reproduce the problem then please file a bug report against the partman-lvm package. And if you discover anyone else suffering from this specific problem, please refer them to the bug report so they can confirm your problem and subscribe to the report.



> **RichardET said:**
> maybe your drive was partitioned incorrectly;  I doubt it's a "bug."

Maybe it's a bug and maybe it's not. But cmcginty is describing unexpected behavior and data loss. Nobody wants that!
If cmcginty can reproduce the problem of a cancel dialog that doesn't cancel, then escalating the issue to the bug tracker seems appropriate.

---

### Post by RichardET on 2015-10-05
> **ian-weisser said:**
> Well, I don't see a bug report from the OP, so if you can reproduce the problem then please file a bug report against the partman-lvm package. And if you discover anyone else suffering from this specific problem, please refer them to the bug report so they can conform your problem and subscribe to the report.





Maybe it's a bug and maybe it's not. But cmcginty is describing unexpected behavior and data loss. Nobody wants that!
If cmcginty can reproduce the problem of a cancel dialog that doesn't cancel, then escalating the issue to the bug tracker seems appropriate.

I dont see any value in mixing OS's on one drive, and in the OpenBSD world, for instance, its strongly discouraged.
Thus, I cant rate this problem as a true bug.

---

### Post by buzzingrobot on 2015-10-05
The installer needs to be abundantly clear in telling the user that the existing boot sector and file systems, if any, on the drive(s) will be deleted if he or she proceeds beyond that point.

In other words, the user needs to be required to take a specific, obvious, and clearly labeled action to commit that step. If the user backs out before making that choice, then, obviously, the drives should not be touched.

I'm not so sure that the current installer is, in all sections of its partitioner, that obvious. A button that says "Go Back" paired with a button that says "Next" is insufficient if clicking "Next" triggers the repartitioning and/or reformatting. It only takes a split second to kill a partition table.

Ubuntu's installer takes a linear approach: one step after another.  So, the step after choosing a partitioning scheme is to create that scheme and format the drives.

That particular step should be called out for the attention of the user and require a separate action by the user. If the user says "No", the installer should return to the beginning of the partitioning section.

Work on a new installer design is under way, I see.

---

### Post by QIII on 2015-10-05
> **RichardET said:**
> I dont see any value in mixing OS's on one drive, and in the OpenBSD world, for instance, its strongly discouraged.
Thus, I cant rate this problem as a true bug.

What you think should be the case with regard to miltiple OSes on one disk and what the OpenBSD community recommends are entirely immaterial.  The OP has a problem.  Unless you would care to help the OP or help to guide in reporting this as a bug and letting the developers look at it, *this* community would probably prefer that you refrain from comment.

---

### Post by QIII on 2015-10-05
@ alice7:

That the Ubuntu installer is unclear about this and does not appear to sufficiently warn new users about what is about to happen is a known frustration that has been brought up quite often.  However, it is not considered a bug because it is performing as designed.  Personally, I think that is terrible design and Canonical needs to rethink it.

What most certainly would be a bug is if you are given a chance to say "No" but something bad happens anyway.

Please report this as a bug.

---

### Post by RichardET on 2015-10-06
There is this web article from August, 2014:

[http://www.omgubuntu.co.uk/2014/08/ubuntu-installer-bug-wipes-partitions](http://www.omgubuntu.co.uk/2014/08/ubuntu-installer-bug-wipes-partitions)

and then this:

[http://askubuntu.com/questions/485968/ubuntu-install-erased-windows](http://askubuntu.com/questions/485968/ubuntu-install-erased-windows)

The main complaint was this:
"When trying to install Ubuntu I selected the default checked "Erase  hardrive" option and checked the second box below it (below an option to  encrypt which I didn't select) which had to do with installing tools to  make partitioning easier. There was a small warning in red text around  the Erase hard drive option that said it would delete all my files, but I  clicked Continue anyway because I assumed I'd be given an option to  Revert or some kind of warning if this really would mess up my system.  Instead though, it sent me to the Choose Your Location screen within the  applet and the back button became grayed and unusable, which is when I  worried that it may have messed up my partitions. (It technically has no  valid OS I can boot from now...)"


I personally have never experienced this bug with any Linux I have tried, mainly Fedora, Centos, OpenSUSE, and Ubuntu, (GNOME, XFCE, UNITY), but, I have never used a USB stick, always a CD version.    

It would be useful to post the dmesg, and other details.

---

### Post by buzzingrobot on 2015-10-06
> **RichardET said:**
> 
I personally have never experienced this bug with any Linux I have tried, mainly Fedora, Centos, OpenSUSE, and Ubuntu, (GNOME, XFCE, UNITY), but, I have never used a USB stick, always a CD version.    



It's the same installer, USB or DVD/CD. 

I recall reports like this from some time ago which, I think, were identified as caused by wording in the installer that might be misconstrued by users. I couldn't turn up a bug report, though.

Fedora's current installer, also used in RHEL 7/CentOS 7, does not follow a step-by-step linear path. The user returns to a "hub" to configure and reconfigure different aspects of the install, in whatever order.  Nothing is touched on the drives until the user clicks, "Begin Installation", and that is made clear to the user. The installer took a lot of heat when it was introduced, but I think the clear separation between configuration and actual installation is smart.

---

### Post by kansasnoob on 2015-10-06
> **RichardET said:**
> There is this web article from August, 2014:

[http://www.omgubuntu.co.uk/2014/08/ubuntu-installer-bug-wipes-partitions](http://www.omgubuntu.co.uk/2014/08/ubuntu-installer-bug-wipes-partitions)

and then this:

[http://askubuntu.com/questions/485968/ubuntu-install-erased-windows](http://askubuntu.com/questions/485968/ubuntu-install-erased-windows)

The main complaint was this:
"When trying to install Ubuntu I selected the default checked "Erase  hardrive" option and checked the second box below it (below an option to  encrypt which I didn't select) which had to do with installing tools to  make partitioning easier. There was a small warning in red text around  the Erase hard drive option that said it would delete all my files, but I  clicked Continue anyway because I assumed I'd be given an option to  Revert or some kind of warning if this really would mess up my system.  Instead though, it sent me to the Choose Your Location screen within the  applet and the back button became grayed and unusable, which is when I  worried that it may have messed up my partitions. (It technically has no  valid OS I can boot from now...)"


I personally have never experienced this bug with any Linux I have tried, mainly Fedora, Centos, OpenSUSE, and Ubuntu, (GNOME, XFCE, UNITY), but, I have never used a USB stick, always a CD version.    

It would be useful to post the dmesg, and other details.

Actually the bug you mention has been fixed:

[https://launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

What's being described here is different:

> **[COLOR="#FF0000"]There was a small warning in red text around  the Erase hard drive option that said it would delete all my files, but I  clicked Continue anyway[/COLOR]**

That's purely operator error, but going back to the original post this is concerning:

> **[COLOR="#FF0000"]A window popped up that said something like "are you sure you want to write these changes to disk." I clicked "no." It did it anyway.[/COLOR]**

If the installer did in fact continue after clicking no that would be a new bug. I'll be performing some test installations with Wily in the very near future so I'll see if I can duplicate that behavior. BTW that new dialogue window was added as one part of the fix for the aforementioned bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/comments/134](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/comments/134)

> Always show a confirmation dialog before committing partitioning. I've
    read considerably more reports of users having their data destroyed by
    some misunderstanding or other of the partitioner than I'm comfortable
    with; if a slightly ugly confirmation even when we think things are
    clear saves some people from that, then it's worth it, and it adds
    another layer of defence against bugs.

I honestly never checked to see if the "quit" or "no" buttons worked on that window :oops:

So I'll have a look ASAP and report the problem on the QA Tracker if I can reproduce it.

---

### Post by cmcginty on 2015-10-07
I decided I didn't need my recovered system drive anyway, so I went ahead and tried to reproduce the issue.

[COLOR="#FF0000"]**I confirmed this is a real bug and was able to reproduce it.**[/COLOR]

I have no doubt in my mind that it was the installer that wiped my data. The steps to reproduce are:
1) At the first desktop selection screen choose "Try Ubuntu Live Image"
2) After booting click the "Install" icon on the desktop
3) Continue first screen with English install
4) Enabled third party licensed software, continue
5) Select an "LVM Enabled" install
6) Select "Install" or "Next" (forget exactly what the button name was) *[[NOTE: You might think, "Why click INSTALL idiot when it says your drive will be modified". Well what got me was that the "install" button is in the exact same location as the "Continue" button from the previous screen. When dialogue box changed, my mouse cursors was still directly over the "Install" button. My **over sensitive** touchpad registered a mouse click the second I touched it to move the cursor and it clicked "Install". **Whoops, bye bye drive and all my data.** ]]*
7) At this point all the drive icons in the left dock disappear and window pops up ... Warning, your disk is about the be erased.... Go Back or Continue. I hit Go Back

8) At this point I opened  a terminal to check the LVM info on the disk. It had all been erased and replaced with the installer's version. My partition info was also modified, but when I dumped that I was getting a warning about being out of sync. I don't know if that really was written to the drive or not.

So doing all this I was going to try and get the logs off the box, but not having a valid drive, I tried to install SSH. Long story short, the machine froze up before I could get SSH working. :-(
[U]
**I'm 100% sure if you test this in a virtual machine you will get the same results.**[/U] If you still can not reproduce this I will setup my own VM and maybe post a Youtube video or something.

Last thought. I know you say maybe it was fixed in development already (or not), but until Canonical pulls down the 14.04.3 LTS ISO or (at the very least) put up a visible warning, _users are going to continue losing their personal data with the Ubuntu Live ISO_.

---

### Post by kansasnoob on 2015-10-07
> Last thought. I know you say maybe it was fixed in development already (or not), but until Canonical pulls down the 14.04.3 LTS ISO or (at the very least) put up a visible warning, users are going to continue losing their personal data with the Ubuntu Live ISO. 

I was only saying that specific bug was fixed. It specifically involved the installer not recognizing existing operating systems and/or partitions which resulted in wiping partitions that the installer didn't even see as existing, particularly doing an upgrade via live DVD/USB.

I'll have a look at this sometime within the next 2 or 3 days. I test on bare metal rather than in a VM. I do know that entire disc/LVM installs are just that - it uses the entire disc - PERIOD. What else could "entire disc" mean?

Something I've found problematic ever since the installer (ubiquity) was rebuilt during the Maverick dev cycle is that it fails to recognize multiple physical drives in what I'd consider a sensible manner. So it's not safe to perform any entire disc install (with or without LVM) on a machine that has more than one physical drive.

---

### Post by kansasnoob on 2015-10-07
> **buzzingrobot said:**
> The installer needs to be abundantly clear in telling the user that the existing boot sector and file systems, if any, on the drive(s) will be deleted if he or she proceeds beyond that point.

In other words, the user needs to be required to take a specific, obvious, and clearly labeled action to commit that step. If the user backs out before making that choice, then, obviously, the drives should not be touched.

I'm not so sure that the current installer is, in all sections of its partitioner, that obvious. A button that says "Go Back" paired with a button that says "Next" is insufficient if clicking "Next" triggers the repartitioning and/or reformatting. It only takes a split second to kill a partition table.

Ubuntu's installer takes a linear approach: one step after another.  So, the step after choosing a partitioning scheme is to create that scheme and format the drives.

That particular step should be called out for the attention of the user and require a separate action by the user. If the user says "No", the installer should return to the beginning of the partitioning section.

Work on a new installer design is under way, I see.

About this:

> Work on a new installer design is under way, I see.

Where did you find that info? I'd love to see some major changes because they really messed up when they performed the last major rebuild during the Maverick dev cycle. One of my biggest gripes was their choice to eliminate the "Use largest continuous free space" option.

---

### Post by kansasnoob on 2015-10-07
I really don't see a problem. I tested both a Wily daily image and a 14.04.3 image, and both show the same warning:

[ATTACH=CONFIG]264851[/ATTACH]

**[COLOR="#FF0000"]Warning[/COLOR]: This will delete all .....................................................**

So what would be reasonable to expect if you select that option and click on Continue?

I personally chose the Something else option because I didn't want to wipe everything on this box, but I'm sure clicking on Continue will wipe the drive, then you'll see another screen saying what new partitions will be created ................... but the wiping has already been done - POOF!

A red warning that says all will be deleted means all will be deleted!

---

### Post by oldfred on 2015-10-07
But the encryption and the LVM install do not mention that. 
The issue often is "easier" partitioning, so they select LVM.
And full drive to most Windows users is there c: drive, but they want to keep there d: drive on the same physical drive. Or most Windows users do not know a Windows drive is really just a partition.

---

### Post by sudodus on 2015-10-08
> **kansasnoob said:**
> I really don't see a problem. I tested both a Wily daily image and a 14.04.3 image, and both show the same warning:

[ATTACH=CONFIG]264851[/ATTACH]

**[COLOR="#FF0000"]Warning[/COLOR]: This will delete all .....................................................**

So what would be reasonable to expect if you select that option and click on Continue?

I personally chose the Something else option because I didn't want to wipe everything on this box, but I'm sure clicking on Continue will wipe the drive, then you'll see another screen saying what new partitions will be created ................... but the wiping has already been done - POOF!

A red warning that says all will be deleted means all will be deleted!

Yes, it this is true.

> **oldfred said:**
> But the encryption and the LVM install do not mention that. 
The issue often is "easier" partitioning, so they select LVM.
And full drive to most Windows users is there c: drive, but they want to keep there d: drive on the same physical drive. Or most Windows users do not know a Windows drive is really just a partition.

Yes, this is also true.

-o-

It is easy to click once by mistake. A extra final big read checkpoint before overwrite would save some people, but others are too trigger-happy, and would click past that checkpoint too :-/

---

### Post by RichardET on 2015-10-08
I think the installer should only do what a user intends it to do, assuming that the user understands what he's doing with the installer, but, if mistakes by the user are made, because the user does not understand drive partitioning, and how the drive is currently partitioned, resulting in some lesson learned, that's also good.  My rule is simple - if you don't want your drive touched, don't touch it;  it's that simple.  And if you must play, use a VM.

One rule I have with Ubuntu,, after experimenting many times, is to ignore the home drive encryption option, and also the total install encryption option.  The latter gets very old after a couple of reboots, and the former does not seem to work correctly;  it always causes a boot-up to hang and its not clear to me if the mounting process is working properly, with home drive encryption, anyone else notice this behavior?

---

### Post by buzzingrobot on 2015-10-08
> **RichardET said:**
> ...if mistakes by the user are made, because the user does not understand drive partitioning...

Yes, it's the partitioning itself that's the real issue. It's unrealistic to expect people to understand them, and even more so when you toss in GPT vs MBR, primary and secondary, Secure Boot, BIOS vs UEFI, bootloaders, etc.

Every installer I've every used, on any PC platform, takes the same approach to mitigating this:  They want the user to allow the installer to assume there's only one drive in the machine and to take control of it and partition it as it wishes.

As soon as an installer gives the user actual access to a partitioner, as Ubuntu does via the "Something Else..." option, then it loses control and must rely on the user, flagging only choices that are impossible to implement.

Windows and OS X take this approach, as well. 

(Fedora's installer will rather easily default to automagically creating an LVM scheme spanning multiple drives. It's labeled as "LVM", though, and so assumes users know what that means.)

Phones and tablets hide partitioning altogether, so it will be interesting to see the impact this has on traditional PC's as users bring their small device habits and expectations to that platform.

---

### Post by monkeybrain20122 on 2015-10-08
I don't know, I find Ubuntu's installer easier to use than Fedora's at least for new users(I dualboot) With Fedora it is kind of confusing for the uninitiated (the menu is kind of like a maze and it is not quite clear what your action will do and the messages are cryptic, at least that was my first impression) On the other hand Ubuntu's is a lot more straight forward. Mind you, I always use the advanced option ("something else") since I like to have a separate /home partition so there may be some issues with the automatic options that I am not aware of (I heard that it automatically creates a /boot partition for no reason and it will turn out to be too small after a few kernel updates)
I think there may be some problem with Fedora's automatic option as well (I never used it though, also do things manually there) 

Dualbooting/multibooting is always a bit tricky so I always use the manual option instead of something like "install along" regardless of distro. The installers make assumptions about the drive layout which may not be what one wants. 

Edited: OpenSuse has the worst installer IMO. Very confusing and I was afraid to proceed in case it wiped out Ubuntu and fedora. So I use it only in VM.

---

### Post by buzzingrobot on 2015-10-08
> **monkeybrain20122 said:**
> I don't know, I find Ubuntu's installer easier to use than Fedora's at least for new users(I dualboot) With Fedora it is kind of confusing for the uninitiated 

Oh, yeah.  Fedora's installer is not for the uninitiated. It doesn't have an "automagic" option, and even savvy users complain they can't figure out how to delete, create, and assign mount points to partitions within the installer. It has a "free up space" function that is confusing.  I don't mind the hub-and-spoke approach but it clearly annoys some folks. I think the ability to re-do your configuration and needing to explicitly trigger the action that touches the drives ihs value.

I agree Ubuntu's installer is the best, and probably, the safest for newbies and non-experts, meaning anyone with one drive with no interest in creating any particular partitioning scheme. Beyond that point, installers can only do so much to protect us from ourselves. If I was writing one for ordinary folks, I think I'd try to keep it as visual as possible, trying to disguise the existence of partitions as much as possible, maybe using sliders, like gparted, to size different named partitions (but calling them "sections" or some other less hostile euphemism.)

---

### Post by sammiev on 2015-10-08
> **monkeybrain20122 said:**
> I don't know, I find Ubuntu's installer easier to use than Fedora's at least for new users(I dualboot) With Fedora it is kind of confusing for the uninitiated (the menu is kind of like a maze and it is not quite clear what your action will do and the messages are cryptic, at least that was my first impression) On the other hand Ubuntu's is a lot more straight forward. Mind you, I always use the advanced option ("something else") since I like to have a separate /home partition so there may be some issues with the automatic options that I am not aware of (I heard that it automatically creates a /boot partition for no reason and it will turn out to be too small after a few kernel updates)
I think there may be some problem with Fedora's automatic option as well (I never used it though, also do things manually there) 

Dualbooting/multibooting is always a bit tricky so I always use the manual option instead of something like "install along" regardless of distro. The installers make assumptions about the drive layout which may not be what one wants. 

Edited: OpenSuse has the worst installer IMO. Very confusing and I was afraid to proceed in case it wiped out Ubuntu and fedora. So I use it only in VM.

I agree with the whole post and I do enjoy OpenSuse, you raise an excellent point however.

---

### Post by kansasnoob on 2015-10-09
> **oldfred said:**
> But the encryption and the LVM install do not mention that. 
The issue often is "easier" partitioning, so they select LVM.
And full drive to most Windows users is there c: drive, but they want to keep there d: drive on the same physical drive. Or most Windows users do not know a Windows drive is really just a partition.

But the LVM option is only available when the Entire disk option is selected. If any other option is selected the LVM and Encrypted options are grayed out:

[ATTACH=CONFIG]264869[/ATTACH]

[ATTACH=CONFIG]264870[/ATTACH]

Of course LVM can be performed with or without encryption:

[ATTACH=CONFIG]264871[/ATTACH]

When ubiquity was rebuilt during the Maverick dev cycle I did fight for a warning to be added at the very beginning of the installation process. Basically I think the first screen you see after launching ubiquity should be a warning to the effect that any and all partitioning, installation, etc can result in data loss and requires some basic knowledge of the Linux/Ubuntu drive & partition designations, etc, etc. Then a link should be provided to some rather detailed info including links to the forums and Ask Ubuntu, etc. But the idea was shot down.

---

### Post by cmcginty on 2015-10-14
> **buzzingrobot said:**
> 
I agree Ubuntu's installer is the best, and probably, the safest for newbies and non-experts, meaning anyone with one drive with no interest in creating any particular partitioning scheme. 

Actually the Mint installer is much clearer about how it presents the install actions to the user. The dialogue box design is similar but the is clearly an improvement over Ubuntu.

---

### Post by cmcginty on 2015-10-14
> **kansasnoob said:**
> But the LVM option is only available when the Entire disk option is selected. If any other option is selected the LVM and Encrypted options are grayed out:

[ATTACH=CONFIG]264869[/ATTACH]

[ATTACH=CONFIG]264870[/ATTACH]

Of course LVM can be performed with or without encryption:

[ATTACH=CONFIG]264871[/ATTACH]



These screen shots are not from 14.04.2 and 14.04.3 release which is what this thread is about.

---

