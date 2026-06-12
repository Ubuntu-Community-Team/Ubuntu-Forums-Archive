---
title: "Dell Poweredge 700 Freezing"
date: 2005-05-30
forum: Server Platforms
---

### Post by sjpwong on 2005-05-30
I'm trying to run a Dell poweredge 700 as an Apache2 Web server, however, I am getting frequent system freezes.

I have disabled all 3D/dri capabilites so I'm confident that GDM is not locking things up.

I have tried "noapic nolapic" on the boot parameters but that has not worked, it just locked up again this morning after several days.

Does anyone have any other pointers?

It's running Apache2, SSHD and MaxDB.  There are 3 NICS but only one is active (I have disabled the other kernel modules).

---

### Post by David Cartwright on 2005-06-01
[QUOTE=sjpwong]I'm trying to run a Dell poweredge 700 as an Apache2 Web server, however, I am getting frequent system freezes.

I have disabled all 3D/dri capabilites so I'm confident that GDM is not locking things up..[/QUOTE]

Since you are running with Xorg rather than a console install, I would not be surprised that Xorg is the problem.

Some suggested steps:

1. Open a console and run **top**. Leave it open and running.
2. When the server freezes, you'll be able to have a pretty good idea what tasks were running at the time of the freeze.
3. You'll probably find Xorg at the top of the list..

You should reload Ubuntu and choose the server option and just run from console. If you want a 24x7 server, this is the option you will need to choose. Then become friends with **nano**, it's a great little console text editor that ships standard with 5.04.

If you must run a graphical environment, I'll assume you don't have to have 24x7 operation, therefore a possible work-around is to setup a cron job to run once a day that reboots the machine, for example, at 1:30am every day.

So a crontab entry such as:

30 01 * * * /sbin/reboot

will cause the machine to reboot at 1:30am every day.

It's not elegant, but if Xorg is causing a lock-up every couple of days, this should at least allow you to have 99%+ uptime. Oh and make sure you never leave a CD in the CDROM drive.

---

### Post by sjpwong on 2005-06-01
I have since discovered a "Logical Processor" setting in the BIOS setup that I have disabled.  This has at least removed the false enumeration of a second processor that was happening.

The machine has been up for just under 2 days so I'm keeping an eye on it.

[QUOTE=David Cartwright]Since you are running with Xorg rather than a console install, I would not be surprised that Xorg is the problem.

Some suggested steps:

1. Open a console and run **top**. Leave it open and running.
2. When the server freezes, you'll be able to have a pretty good idea what tasks were running at the time of the freeze.
3. You'll probably find Xorg at the top of the list..[/QUOTE]

Each time I've seen it the console is actually blank so I haven't been able to see anything.

I'm trying what you suggest via screen on another machine.

[QUOTE=David Cartwright]
You should reload Ubuntu and choose the server option and just run from console. If you want a 24x7 server, this is the option you will need to choose. Then become friends with **nano**, it's a great little console text editor that ships standard with 5.04.[/QUOTE]

I was previously running Debian without X and using VNC Xservers for the users.  I may have to try that again.  I'm not sure what the state of that "Logical Processor" BIOS setting was previously as it's been back to Dell for a new HDD in between :-(

[QUOTE=David Cartwright]
If you must run a graphical environment, I'll assume you don't have to have 24x7 operation, therefore a possible work-around is to setup a cron job to run once a day that reboots the machine, for example, at 1:30am every day.

So a crontab entry such as:

30 01 * * * /sbin/reboot

will cause the machine to reboot at 1:30am every day.

It's not elegant, but if Xorg is causing a lock-up every couple of days, this should at least allow you to have 99%+ uptime. Oh and make sure you never leave a CD in the CDROM drive.[/QUOTE]

Possible but I really want to avoid this!  Doesn't make Linux look real good :-(

Thanks for your comments.

---

### Post by sjpwong on 2005-06-28
After several more frustrating freezes of this systm I decide to revert to the 386 kernel version.

I think this says it all  :) 

$ uptime
 16:13:26 up 20 days,  1:40,  1 user,  load average: 0.00, 0.00, 0.00

---

### Post by LordHunter317 on 2005-06-28
[QUOTE=David Cartwright]Since you are running with Xorg rather than a console install, I would not be surprised that Xorg is the problem.[/quote]I would.

> 3. You'll probably find Xorg at the top of the list..Which means nothing.

> You should reload Ubuntu and choose the server option and just run from console. If you want a 24x7 server, this is the option you will need to choose.You can run a 24x7 server with X.

> If you must run a graphical environment, I'll assume you don't have to have 24x7 operation, therefore a possible work-around is to setup a cron job to run once a day that reboots the machine, for example, at 1:30am every day.

So a crontab entry such as:

30 01 * * * /sbin/reboot

will cause the machine to reboot at 1:30am every day.This is some of the worse production advice I've seen given, ever.  


[quote=sjpwong]I have since discovered a "Logical Processor" setting in the BIOS setup that I have disabled. This has at least removed the false enumeration of a second processor that was happening.[/quote]Is the processor HyperThreaded?  If so, that's the second processor you were seeing.  It's not false.

Your problem sounds suspicially like flakey hardware to me.  What kernel were you running before?

---

### Post by sjpwong on 2005-06-28
Yeah, I have to agree with your comments.

Yes, it was a P4 with HT.  I was looking for something like that to disable but ended up only finding the "Logical Processor" which I have left disabled.

I was using the 686 version of the current Hoary kernel at the time.  I believe that the package would have been linux-image-2.6.10-5-686 but not sure which version exactly.

The machine had a disk failure at which point I ran the Dell diagnostics several times and didn't find any other problems.  After it was returned I installed Ubuntu instead of Debian and started to have all these problems.  Making we question my decision :-(

Do you suggest I try and take it down and run the Dell diags again?

---

### Post by sjpwong on 2005-06-28
[QUOTE=sjpwong]Yeah, I have to agree with your comments.

Yes, it was a P4 with HT.  I was looking for something like that to disable but ended up only finding the "Logical Processor" which I have left disabled.

I was using the 686 version of the current Hoary kernel at the time.  I believe that the package would have been linux-image-2.6.10-5-686 but not sure which version exactly.

The machine had a disk failure at which point I ran the Dell diagnostics several times and didn't find any other problems.  After it was returned I installed Ubuntu instead of Debian and started to have all these problems.  Making we question my decision :-(

Do you suggest I try and take it down and run the Dell diags again?[/QUOTE]
 The version installed was 2.6.10-5-686-34.1 and the running version is 2.6.10-5-386-34.1.

I'm just upgrading them to the latest version (34.3) now but will keep running the 386 version for now.

---

### Post by David Cartwright on 2005-06-30
[QUOTE=LordHunter317]Which means nothing.[/QUOTE]
Maybe yes, maybe no. We searching for clues to find a solution. I don't think it is appropriate to dismiss a clue until it is certain that it is false.

[QUOTE=LordHunter317]You can run a 24x7 server with X.[/QUOTE]
Absolutely. However, I have experienced exactly the same problems as sjpwong on 3 IBM servers that were running Ubuntu with X.org. They were locking up every 2 to 3 days. Now operating in console mode, they have been running for weeks without a hitch. Therefore I think it is very appropriate to be suspicious of a problem with X.org ... not X in general, but the latest version of X.org in Hoary.

[QUOTE=LordHunter317]This is some of the worse production advice I've seen given, ever.[/QUOTE]
It was my mistake to not make it clear the suggestion was a temporary work-around to give time to track down the problem.

However, what is not sustainable is to have users coming in of a morning and unable to work because a server has locked-up.

In circumstances where you need time to track down the problem, what do you propose as an alternative? Unless sjpwong has capabilities to remotely cycle the power to the offending server, the only other alternative I am aware of involves getting to the site every day before anyone needs to access the server. That can quickly become tiresome!

[QUOTE=LordHunter317]Your problem sounds suspicially like flakey hardware to me.  What kernel were you running before?[/QUOTE]

As I mentioned earlier, I saw exactly the same problem on 3 different servers, hence my problem was certainly not flakey hardware. Albeit, it could relate to a specific type of hardware in the servers since they are all the same model. However,, given that sjpwong has been experiencing the same problem on a different server .. then maybe the problem is software.

My suggestion is that we are searching for clues to a problem. I suggested some clues based on my experiences along with a temporary workaround to assist the smooth running of a real-world business.

If anyone else has experienced lock-up problems please jump in and contribute.

---

### Post by sjpwong on 2005-06-30
[QUOTE=David Cartwright]Absolutely. However, I have experienced exactly the same problems as sjpwong on 3 IBM servers that were running Ubuntu with X.org. They were locking up every 2 to 3 days. Now operating in console mode, they have been running for weeks without a hitch. Therefore I think it is very appropriate to be suspicious of a problem with X.org ... not X in general, but the latest version of X.org in Hoary.[/QUOTE]

Unfortunately, I was still experiencing the problem *after* I disabled GDM (and X) so I have no reason to suspect that is the source of the problem here.

As mentioned before, it has been running without a problem for >22 days now running the 386 kernel flavour?!

I find it hard to believe, but at least it has restored some faith in Linux for my customer and let me move forward.

[QUOTE=David Cartwright]It was my mistake to not make it clear the suggestion was a temporary work-around to give time to track down the problem.[/QUOTE]

My only problem with it is that it does not give me any guarantee to stop it happening within that 24hr period.  I don't suspect that it is a problem related to elapsed time.

Any way, thanks for everyone's comments.  Just hope my workaround is a sane work around for others.

---

### Post by LordHunter317 on 2005-07-01
[QUOTE=David Cartwright]Maybe yes, maybe no.[/quote]No, certainly no.

The first listed process in top(1) doesn't mean thing when the system panics.  It might not even be the process that hung the box, depending on where top was in it's monitoring cycle.

It doesn't tell you a thing.

> In circumstances where you need time to track down the problem, what do you propose as an alternative? Unless sjpwong has capabilities to remotely cycle the power to the offending server, the only other alternative I am aware of involves getting to the site every day before anyone needs to access the server. That can quickly become tiresome!It also motiviates you to get it fixed a lot faster, or at least figure out what's wrong to get it fixed.  It's also not a reliable way to avoid a problem like this.  It might work.  The box might also be hung when you get in.  Haven't actually really done anything.

The i386 kernel thing interests me.    It's possible Ubuntu has an option enabled that's causing issues, that's not enabled on the 386 kernel.  It's also possible that recent of a kernel has a bug, or two, or three.

Try booting with ACPI off.  Also, run memtest86 on the box overnight if you get a chance to ensure the memory is 100% OK.

While running a 386 kernel is an OK solution, it can be rather slow.

---

### Post by sjpwong on 2005-07-02
[QUOTE=LordHunter317]The i386 kernel thing interests me.    It's possible Ubuntu has an option enabled that's causing issues, that's not enabled on the 386 kernel.  It's also possible that recent of a kernel has a bug, or two, or three.[/QUOTE]

Bad news!  About 3 hours after my last post the &^!&@ thing froze again :-(  I think it just cracked the 23 day mark though.

[QUOTE=LordHunter317]Try booting with ACPI off.  Also, run memtest86 on the box overnight if you get a chance to ensure the memory is 100% OK.[/QUOTE]

I've run memtest86 for a couple of hours and no problems found.

I've run the Dell diagnostics a few times with nothing found.

I have just updated the BIOS to the latest version (A01->A04).

I think I'll run for a while with the BIOS update before switching off ACPI to see if that sorts it out.

[QUOTE=LordHunter317]While running a 386 kernel is an OK solution, it can be rather slow.[/QUOTE]

Well, I'd be happy with that if it had stayed running!

Thanks.

---

### Post by sjpwong on 2005-07-04
The source of the problem may have manifested itself...

Yesterday, mid-afternoon while doing a compare with a complete system backup (with Mondo) I started to get CD read errors.  I thought there must have been a problem with the CD I burnt so I burnt another...same problem.

Now, I thought it unlikely to be a problem with the actual iso created so I tried to boot the diagnostic CD...no dice!  It would not boot off the CD.  Just sat there for ages before booting into the HDD.

Now, the drive fails to reset at all.

Perhaps, that's what the source of the problems has been?!

Tonight, I'll check the cables etc.

---

### Post by LordHunter317 on 2005-07-04
Doubtful that would cause a hung kernel, but it's sounding suspicuously to me like you have a failing motherboard.

You're not running this machine too hot, are you?

---

### Post by sjpwong on 2005-07-07
[QUOTE=LordHunter317]Doubtful that would cause a hung kernel, but it's sounding suspicuously to me like you have a failing motherboard.

You're not running this machine too hot, are you?[/QUOTE]

I wasn't sure whether there might have been some low level problems freezing the IDE bus?!

It's winter here now and the room is cool so I don't think it's running hot.

I've disabled the drive in the BIOS until Dell can replace it.

---

### Post by sjpwong on 2006-02-14
Well, to bring this sad tale to a close it looks like it was my fault why the machine was locking up :-(

I had stopped the ACPI daemon from running (I understand a lot more now than I did then) as I thought it was just for power management and didn't think I needed it!

Everything is OK now.

Thanks for everyone's help.

---

### Post by sjpwong on 2007-01-21
This actually still an ongoing problem with this machine.  Random locks about every 5 days or so but quite variable time periods of running.

It makes this particular client very wary of using Linux on Dell because he likes buying Dell because hardware is cheap to get a hold of.

Shame, I wish I had some real data to add...

---

### Post by mrweirdo on 2007-02-02
I too have a Dell Poweredge however mine is a 1400 with dual p3 800mhz chips. 
I have dual nics in the system as its used for router and samba server.  

Whats interesting is the lockups happen when I transfer large amounts of data eather to or from the server as it hardly freezes otherwise. Thinking it was the intel nics I disabled the motherboards built in one and replaced both with pci cards from dlink with the same results.
I also have noticed that using gigabit nics seem to make the lock ups happen more frequently then using slower 100meg nics.

I have tried both ubuntu versions from hoary on and fedora core 3 and it still crashes randomly. Also I have tried running windows on the same box without issues.  So I'm beginning to think there is some linux / dell hardware incompatibility going on.

---

### Post by Hans Kurppa on 2007-02-05
> **mrweirdo said:**
> So I'm beginning to think there is some linux / dell hardware incompatibility going on.
Must be.

I have PowerEdge 860 *(Dual-Core Xeon+SAS drives)*, and it freezes after 30min~1hour (on idle, no work load, it's not in production use yet).

So far I've tried CentOS 4, Ubuntu 6.06 and 6.10, FC6, and SUSE Linux Enterprise Server 10 *(Dell supports SLES10 so I'm really wondering why that freezes too)*. Same kind of lock up/freeze in all, with or without X.

All kernels have been the default ones (x64, haven't tried x86(386) yet). Also tried various kernel params with no luck: cpu_exclusive=0, noapic, nolapic, acpi=off etc... Ran Memtest on it, didn't report any errors.

---

### Post by Hans Kurppa on 2007-02-10
Reinstalled SLES10, this time with the Server Assistant System Setup (previous installations were done straight from the OS install DVD). It's been up now for 2+ days, no freezes so far.

Maybe the System Setup program does some configs that are missing when installing straight from OS install DVD/CD (too bad it accepts only RHEL and SLES as linux installation).

Also the server didn't have the utility partition when I did the previous OS installations, though I really doubt that could be an issue here.

---

### Post by mrweirdo on 2007-02-12
configs or possibly even custom drivers. Unfortunately I don't have the Server assistant disk on hand or I'd give it a try as well. Its probably on dells website hidden some place although it still doesn't allow me to run what i prefer being ubuntu ;)

A friend of mine who also has a poweredge server suggested trying out mandriva(mandrake) linux so I'll probably give that a go when i get home this afternoon to see if that solves the random freezes although I highly doubt it will.

I wonder if it would not be posible to take the install cd and modify it to work with something like fedora then go from there to ubuntu. I have noticed when looking for drivers on dells site most of the linux ones come in the form of rpms which ubuntu doesn't use.

---

### Post by mrweirdo on 2007-02-13
So far so good with mandriva after installing it from downloadable iso's and running it for over a day and constantly bombarding it with network traffic without lockups.

Now what I'd like to figure out is why it can run without hiccups but Ubuntu cannot.

I'm thinking the crashing is in some way related to the Adaptec onboard AIC-7899P SCSI controller so after looking through the dell manuals I found out how to disable that and I'm now using an LSI PCI-X card instead.

I believe you hit <ctrl><a> then select buss a then advanced scsi settings and you can disable  the control from there.

Anyways I'll post back later if it worked.

---

### Post by mrweirdo on 2007-02-13
nope that didn't seem to do any good as it crashed almost instantly after hitting it with network data over samba.

As much I prefer ubuntu it sadden me i might have to switch distros :( as now I am completly out of ideas.

---

