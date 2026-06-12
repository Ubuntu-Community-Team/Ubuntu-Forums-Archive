---
title: "Daru2 and Latest Update"
date: 2009-01-30
forum: System76 Support
---

### Post by laserline on 2009-01-30
Hello,

I've just updated my Ubuntu 8.10 installation on the Daru2 I own and found that the ACPI is broken...

I'm always booting the Daru2 with the kernel option "acpi=noirq".

After the update I rebooted, and after a few minutes my Battery was lost (even running in command line showed it's lost).

I thought, let's try booting w/o the "acpi=noirq" option  but that too, after a few minutes it was lost.

I also noticed, that when the ACPI gets crazy, the ACPI sensor shows the CPU is at 146 degrees Celsius (just thought I should mention that).

Does anyone else have the same problem ?

Where can I find the logs about the EC thingy or anything that relates to this old old problem (not to mention my ancient suspend thread).

Thanks,
Idan.

---

### Post by thomasaaron on 2009-01-30
First, if that CPU temp is correct, it is VERY hot. I'm not sure that it is accurate. But you should make sure you don't have a dust bunny living in your cpu fan or something. Also make sure you're not obstructing the vents when you use it.

Second, are you running proposed updates? Go to System > Admin > Software Sources to find out. If so, you probably should not. You should probably disable them and go back to the previous kernel until the kernel is officially released.

After you check out #1 and #2, please post the output of...

```
uname -r
```

---

### Post by gaussian on 2009-01-30
I can attest to ACPI thermal problems. I am sure it is not the real CPU temperature (146 Celsius), since the laptop itself it is not getting hot at all.

As a temporary fix, I am booting to an older Kernel (I think it is .9.xxx instead of .11.xxx version).

---

### Post by laserline on 2009-01-30
Hi Tom,

[LIST=1]
[*]When ACPI is crazy the temp states by default 146 Celsius. When it works, the temp is correct. Now it works and my temp is 52 Celsius.
[*]I'm not using proposed.
[*]The output of 'uname -r' is: 2.6.27-11-generic
[/LIST]

I've just rebooted, and uptime is about 26 minutes - ACPI didn't go crazy yet.


Idan.

---

### Post by thomasaaron on 2009-01-30
> 1. When ACPI is crazy the temp states by default 146 Celsius. When it works, the temp is correct. Now it works and my temp is 52 Celsius.

OK, then it probably isn't accurate.

> 2. I'm not using proposed.

See what happens in the *-9 kernel (per gaussian)
   
> 3. The output of 'uname -r' is: 2.6.27-11-generic

There's a bug report already at launchpad.net/system76 on the DarU2 power management problems. Please add this info to that bug, and I'll start to figure out what's changed in the kernel options.

---

### Post by jdb on 2009-01-30
> **thomasaaron said:**
> OK, then it probably isn't accurate.



See what happens in the *-9 kernel (per gaussian)
   


There's a bug report already at launchpad.net/system76 on the DarU2 power management problems. Please add this info to that bug, and I'll start to figure out what's changed in the kernel options.

I noticed that when Archlinux upgraded the kernel in December.

[http://ubuntuforums.org/showthread.php?t=772722&page=13z&#122](http://ubuntuforums.org/showthread.php?t=772722&page=13z&#122)


jdb

---

### Post by williumbillium on 2009-02-04
This appears to be the relevant bug report at kernel.org.  They don't seem to be using acpi=noirq but the symptoms are very similar and are all MSI machines.

[http://bugzilla.kernel.org/show_bug.cgi?id=12011](http://bugzilla.kernel.org/show_bug.cgi?id=12011)

BTW, the acpi=noirq fix works in 2.6.27-9

*Wild guess* that this is the patch that caused the regression:

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-11/msg01302.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-11/msg01302.html)

---

### Post by jdb on 2009-02-04
> **williumbillium said:**
> This appears to be the relevant bug report at kernel.org.  They don't seem to be using acpi=noirq but the symptoms are very similar and are all MSI machines.

[http://bugzilla.kernel.org/show_bug.cgi?id=12011](http://bugzilla.kernel.org/show_bug.cgi?id=12011)

BTW, the acpi=noirq fix works in 2.6.27-9

*Wild guess* that this is the patch that caused the regression:

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-11/msg01302.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-11/msg01302.html)

I'm on 2.6.28-1 in Archlinux & the acpi=noirq option seems to be doing something again.
It disables the Fn-F4 & Fn-F5 keys, it had stopped doing that in previous releases.
I looked at the ec.c code & a lot has changed since the msg01302 patch.

The power readout hasn't glitched yet, but I won't feel real good about it
until I see it go many more hours with no problems :rolleyes:

jdb

---

### Post by jdb on 2009-02-04
> **jdb said:**
> I'm on 2.6.28-1 in Archlinux & the acpi=noirq option seems to be doing something again.
It disables the Fn-F4 & Fn-F5 keys, it had stopped doing that in previous releases.
I looked at the ec.c code & a lot has changed since the msg01302 patch.

The power readout hasn't glitched yet, but I won't feel real good about it
until I see it go many more hours with no problems :rolleyes:

jdb

It took 6 hours, but it broke.
Ah well :(

jdb

---

### Post by badbull on 2009-02-05
i had the same problems, just with my self compiled kernel wich works only in acpi poll mode.
but i made some good experience with some changes mentioned in this bug report [http://bugzilla.kernel.org/process_bug.cgi](http://bugzilla.kernel.org/process_bug.cgi)
I changed ACPI_EC_UDELAY from 100 to 500 and add some udelay(ACPI_EC_UDELAY); lines to the acpi_ec_transaction_unlocked() function. 
I'll do some more testing and report my experiences the next days.

---

### Post by impact on 2009-02-07
So if I understand this right, acpi=noirq doesn't do anything right now (other than disabling the brightness control)?

On a semirelated note, they are testing yet another patch at that kernel.org bug report.

---

### Post by jdb on 2009-02-07
> **impact said:**
> So if I understand this right, acpi=noirq doesn't do anything right now (other than disabling the brightness control)?

On a semirelated note, they are testing yet another patch at that kernel.org bug report.

That's what I'm seeing :(
I hope the new patch works :D


jdb

---

### Post by badbull on 2009-02-10
i've created a new patch here: [http://bugzilla.kernel.org/show_bug.cgi?id=12011](http://bugzilla.kernel.org/show_bug.cgi?id=12011)
this works for me without any kernel option.
i'm testing kernel 2.6.28 from Ubuntu Jaunty and 2.6.29-rc3.

I try to create a ppa for the kernel, but i get errors every time ;-)

---

### Post by jdb on 2009-02-10
> **badbull said:**
> i had the same problems, just with my self compiled kernel wich works only in acpi poll mode.
but i made some good experience with some changes mentioned in this bug report [http://bugzilla.kernel.org/process_bug.cgi](http://bugzilla.kernel.org/process_bug.cgi)
I changed ACPI_EC_UDELAY from 100 to 500 and add some udelay(ACPI_EC_UDELAY); lines to the acpi_ec_transaction_unlocked() function. 
I'll do some more testing and report my experiences the next days.

Thanks BadBull,

I loaded your patch & will let you know what happens.


jdb

---

### Post by thomasaaron on 2009-02-10
JDB,

If that patch works for you, could I bother you to post instructions for how to apply it?

---

### Post by jdb on 2009-02-10
> **thomasaaron said:**
> JDB,

If that patch works for you, could I bother you to post instructions for how to apply it?

It's still looking good but sometimes it takes a while to break.

If it's still looking good in the Morning I'll post some instructions.
It's not too bad, but it's probably more than a lot of folks want to do every time the kernel is upgraded.

If this works it would really be nice if the developers would make the affected parameters available
as kernel options so we could just put the changes in menu.lst & be done with it.

jdb

---

### Post by williumbillium on 2009-02-10
With a bit of work I think we can get the patch in the linux kernel but it requires some more testing.  See latest comments at:

[http://bugzilla.kernel.org/show_bug.cgi?id=12011](http://bugzilla.kernel.org/show_bug.cgi?id=12011)

jdb, if you post instructions tomorrow I'll see if I can patch my kernel and do some testing.

---

### Post by jdb on 2009-02-11
> **williumbillium said:**
> With a bit of work I think we can get the patch in the linux kernel but it requires some more testing.  See latest comments at:

[http://bugzilla.kernel.org/show_bug.cgi?id=12011](http://bugzilla.kernel.org/show_bug.cgi?id=12011)

jdb, if you post instructions tomorrow I'll see if I can patch my kernel and do some testing.

It's been up over 20 hours & everything looks good.

I'll post a method for patching an Ibex kernel this afternoon.

jdb

---

### Post by badbull on 2009-02-11
> **jdb said:**
> It's been up over 20 hours & everything looks good.

I'll post a method for patching an Ibex kernel this afternoon.

jdb

I'm working on a ppa for the intrepid kernel. this should be ready in a few hours. for the kernel patch i need some testers.
I'll post the url for the ppa when it's ready.

---

### Post by jdb on 2009-02-11
> **badbull said:**
> I'm working on a ppa for the intrepid kernel. this should be ready in a few hours. for the kernel patch i need some testers.
I'll post the url for the ppa when it's ready.

Cool, that's much better than a patch!

I just loaded a pristine Ibex & was about to patch it to check out my instructions.
I'm going to hold off on that & will load your ppa when it's ready.

jdb

---

### Post by badbull on 2009-02-11
you can find the ppa at [https://launchpad.net/~timo-tretter/+archive/ppa/](https://launchpad.net/~timo-tretter/+archive/ppa/)

for installing the kernel from this ppa add
```

deb http://ppa.launchpad.net/timo-tretter/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/timo-tretter/ppa/ubuntu intrepid main

``` to your /etc/apt/sources.list file and update your apt with
```

sudo apt-get update
sudo apt-get upgrade

```

to avoid the error that the server is not signed add the repository key with
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com  0C177666C5D9696595765DC22CC852C735B96AB3

```

ps: i386 is not ready now...but it shout be in a few minutes. i cannot test it now, hope it will start ;-)

---

### Post by jdb on 2009-02-11
> **badbull said:**
> you can find the ppa at [https://launchpad.net/~timo-tretter/+archive/ppa/](https://launchpad.net/~timo-tretter/+archive/ppa/)

for installing the kernel from this ppa add
```

deb http://ppa.launchpad.net/timo-tretter/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/timo-tretter/ppa/ubuntu intrepid main

``` to your /etc/apt/sources.list file and update your apt with
```

sudo apt-get update
sudo apt-get upgrade

```

to avoid the error that the server is not signed add the repository key with
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com  0C177666C5D9696595765DC22CC852C735B96AB3

```

ps: i386 is not ready now...but it shout be in a few minutes. i cannot test it now, hope it will start ;-)

I followed the above instructions & it worked like a charm for i686.

I'm going to let it run all night & will let you know the results.

How does this affect future kernel updates??

Will Ubuntu upgrades overwrite this or will the kernel be upgraded when this ppa is??

Thanks,

jdb

---

### Post by badbull on 2009-02-11
> **jdb said:**
> 
How does this affect future kernel updates??

Will Ubuntu upgrades overwrite this or will the kernel be upgraded when this ppa is??

jdb

i just increase the version number...so it will be overwritten if a new kernel comes out.

we hope to get this patch into the kernel so it will be fixed in the next kernel version. hopefully the ubuntu maintainers add this to the jaunty kernel.

---

### Post by jdb on 2009-02-11
> **badbull said:**
> i just increase the version number...so it will be overwritten if a new kernel comes out.

we hope to get this patch into the kernel so it will be fixed in the next kernel version. hopefully the ubuntu maintainers add this to the jaunty kernel.

I see now, you bumped it from 2.6.27-11.27 to 2.6.27-11.28
I like the way that works.
If Ubuntu upgrades to something like 2.6.27-1X.YZ then you can make a 2.6.27-1X.YZ+1

Yeah, if Ubuntu puts it in their jaunty kernel that will be great.
With any luck it will make it to the kernel.org kernel eventually.

jdb

---

### Post by jdb on 2009-02-12
BadBull, it ran all night with no problems, I think you've got it!!

jdb

---

### Post by williumbillium on 2009-02-12
Hi Badbull, the patch from your PPA has been running fine for me all night too, without acpi=noirq.

How many delays does the patch from the PPA have?  Do we need to test with fewer delays as well?

---

### Post by jdb on 2009-02-12
> **williumbillium said:**
> Hi Badbull, the patch from your PPA has been running fine for me all night too, without acpi=noirq.

How many delays does the patch from the PPA have?  Do we need to test with fewer delays as well?

He changed ACPI_EC_UDELAY from 100 to 500 and then added the delay to many additional spots in the code.
I'm a little nervous about adding all that delay especially inside a spin_lock, they are only supposed to last for a few instructions.
Keep an eye out for anything strange.

If you still want directions on patching the kernel let me know.

Here is BadBull's patch:

```
--- a/drivers/acpi/ec.c	2009-01-28 19:49:30.000000000 +0100
+++ b/drivers/acpi/ec.c	2009-02-05 09:48:32.000000000 +0100
@@ -67,7 +67,7 @@
 
 #define ACPI_EC_DELAY		500	/* Wait 500ms max. during EC ops */
 #define ACPI_EC_UDELAY_GLK	1000	/* Wait 1ms max. to get global lock */
-#define ACPI_EC_UDELAY		100	/* Wait 100us before polling EC again */
+#define ACPI_EC_UDELAY		500	/* Wait 100us before polling EC again */
 
 #define ACPI_EC_STORM_THRESHOLD 8	/* number of false interrupts
 					   per one transaction */
@@ -255,27 +255,36 @@
 	int ret = 0;
 	pr_debug(PREFIX "transaction start\n");
 	/* disable GPE during transaction if storm is detected */
+	udelay(ACPI_EC_UDELAY);
 	if (test_bit(EC_FLAGS_GPE_STORM, &ec->flags)) {
 		clear_bit(EC_FLAGS_GPE_MODE, &ec->flags);
 		acpi_disable_gpe(NULL, ec->gpe);
 	}
 	/* start transaction */
+	udelay(ACPI_EC_UDELAY);
 	spin_lock_irqsave(&ec->curr_lock, tmp);
 	/* following two actions should be kept atomic */
+	udelay(ACPI_EC_UDELAY);
 	ec->curr = t;
+	udelay(ACPI_EC_UDELAY);
 	start_transaction(ec);
+	udelay(ACPI_EC_UDELAY);
 	if (ec->curr->command == ACPI_EC_COMMAND_QUERY)
 		clear_bit(EC_FLAGS_QUERY_PENDING, &ec->flags);
 	spin_unlock_irqrestore(&ec->curr_lock, tmp);
+	udelay(ACPI_EC_UDELAY);
 	/* if we selected poll mode or failed in GPE-mode do a poll loop */
 	if (force_poll ||
 	    !test_bit(EC_FLAGS_GPE_MODE, &ec->flags) ||
 	    acpi_ec_wait(ec))
 		ret = ec_poll(ec);
+	udelay(ACPI_EC_UDELAY);
 	pr_debug(PREFIX "transaction end\n");
 	spin_lock_irqsave(&ec->curr_lock, tmp);
 	ec->curr = NULL;
+	udelay(ACPI_EC_UDELAY);
 	spin_unlock_irqrestore(&ec->curr_lock, tmp);
+	udelay(ACPI_EC_UDELAY);
 	if (test_bit(EC_FLAGS_GPE_STORM, &ec->flags)) {
 		/* check if we received SCI during transaction */
 		ec_check_sci(ec, acpi_ec_read_status(ec));
```

---

### Post by jdb on 2009-02-12
> **jdb said:**
> He changed ACPI_EC_UDELAY from 100 to 500 and then added the delay to many additional spots in the code.
I'm a little nervous about adding all that delay especially inside a spin_lock, they are only supposed to last for a few instructions.
Keep an eye out for anything strange.



After loading BadBull's ppa you can get his source by:

apt-get install linux-source-2.6.27

There aren't near as many delays as in the original patch and no delays in a spin_lock.

This is looking very good!!!

jdb

---

### Post by badbull on 2009-02-12
the patch from the ppa has only one delay...
for me it works, but at the kernel bug site is a commend from a user who had a problem with it.
I'm a bit confused now, i reverted all patches and build a new image, but it works as well.
please test the ppa kernel as much as you can, so we get a good feedback if the changes really work.

---

### Post by jdb on 2009-02-12
> **badbull said:**
> the patch from the ppa has only one delay...
for me it works, but at the kernel bug site is a commend from a user who had a problem with it.
I'm a bit confused now, i reverted all patches and build a new image, but it works as well.
please test the ppa kernel as much as you can, so we get a good feedback if the changes really work.

So far, so good.

I'm looking at your diff file 
linux_2.6.28-6.17-1_2.6.28-7.21.diff
and noticed there are no changes for ec.c but there are changes for battey.c

Does that also fix the problem??
Is that the patch that will probably make it into jaunty??

Thanks,

jdb

---

### Post by badbull on 2009-02-12
the ppa patch should include changes in the ec.c
i didn't change any other thing...
i'll take a look to see if i did something wrong

UPDATE: the diff from the ppa include my changes. it also include many changes from the ubuntu maintainers so its kind of hard to find where the changes are

UPDATE 2: the jaunty kernel version is 2.6.28-**7**.21
this include the first patch with all the delays also in the spinlock.

---

### Post by jdb on 2009-02-12
> **badbull said:**
> the ppa patch should include changes in the ec.c
i didn't change any other thing...
i'll take a look to see if i did something wrong

UPDATE: the diff from the ppa include my changes. it also include many changes from the ubuntu maintainers so its kind of hard to find where the changes are

UPDATE 2: the jaunty kernel version is 2.6.28-**7**.21
this include the first patch with all the delays also in the spinlock.

I also patched my 2.6.28-ARCH (archlinux) kernel with just the one delay and it too is working good without acpi=noirq.
It sure is nice to have Fn-F4 & fn-F5 working. 

jdb

---

### Post by thomasaaron on 2009-02-13
Thanks for your help on this badbull and jdb.

---

### Post by thomasaaron on 2009-02-13
Badbull,

Is there a chance we could solicit your help on this bug...
[https://bugs.launchpad.net/system76/+bug/225347](https://bugs.launchpad.net/system76/+bug/225347)

Initially the suspend and battery monitor issue (which you just solved) were lumped into one bug, as you can tell from this report...
[https://bugs.launchpad.net/system76/+bug/225350](https://bugs.launchpad.net/system76/+bug/225350)

Essentially, our DarU1 (which is an ms-1221 or pr200) shuts down when you try to resume from suspend. I can supply you with all the info you want on it. We've sent this thing off to devs, but nobody's been able to get it fixed.

---

### Post by jdb on 2009-02-13
> **thomasaaron said:**
> Badbull,

Is there a chance we could solicit your help on this bug...
[https://bugs.launchpad.net/system76/+bug/225347](https://bugs.launchpad.net/system76/+bug/225347)

Initially the suspend and battery monitor issue (which you just solved) were lumped into one bug, as you can tell from this report...
[https://bugs.launchpad.net/system76/+bug/225350](https://bugs.launchpad.net/system76/+bug/225350)

Essentially, our DarU1 (which is an ms-1221 or pr200) shuts down when you try to resume from suspend. I can supply you with all the info you want on it. We've sent this thing off to devs, but nobody's been able to get it fixed.

Does anyone know what the last kernel was that Daru2 suspend worked???

Thanks

jdb

---

### Post by thomasaaron on 2009-02-14
Yes, the ONLY kernel it ever worked on was Gutsy 64-bit. This was Ubuntu's first 64-bit real-time kernel. The one before and after was *not* realtime.

I've tried our current real-time kerenls, but they do not work.

And maybe the real-time think is a red herring.

---

### Post by jdb on 2009-02-14
> **thomasaaron said:**
> Yes, the ONLY kernel it ever worked on was Gutsy 64-bit. This was Ubuntu's first 64-bit real-time kernel. The one before and after was *not* realtime.

I've tried our current real-time kerenls, but they do not work.

And maybe the real-time think is a red herring.

Thanks Tom.

I'm not real optimistic, but I'm downloading 7.10 right now.
I need something else to drive (keep) me nuts :lolflag:

jdb

---

### Post by gaussian on 2009-02-14
Little test results here:

I have been now running the PPA-version of the kernel for few days (**32-bit version**):
```

$ apt-cache policy linux-image-2.6.27-11-generic 
linux-image-2.6.27-11-generic:
  Installed: 2.6.27-11.28
  Candidate: 2.6.27-11.28
  Version table:
 *** 2.6.27-11.28 0
        500 http://ppa.launchpad.net intrepid/main Packages
        100 /var/lib/dpkg/status
     2.6.27-11.27 0
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages
        500 http://security.ubuntu.com intrepid-security/main Packages
$ uname -r
2.6.27-11-generic


```

Unfortunately this morning all the bad things are back: my CPU-temperature readings are showing 146C, battery is not found etc. I hope this is either fluke or just a 32-bit problem.

---

### Post by jdb on 2009-02-14
> **gaussian said:**
> Little test results here:

I have been now running the PPA-version of the kernel for few days (**32-bit version**):
```

$ apt-cache policy linux-image-2.6.27-11-generic 
linux-image-2.6.27-11-generic:
  Installed: 2.6.27-11.28
  Candidate: 2.6.27-11.28
  Version table:
 *** 2.6.27-11.28 0
        500 http://ppa.launchpad.net intrepid/main Packages
        100 /var/lib/dpkg/status
     2.6.27-11.27 0
        500 http://us.archive.ubuntu.com intrepid-updates/main Packages
        500 http://security.ubuntu.com intrepid-security/main Packages
$ uname -r
2.6.27-11-generic


```

Unfortunately this morning all the bad things are back: my CPU-temperature readings are showing 146C, battery is not found etc. I hope this is either fluke or just a 32-bit problem.

I don't really know what the additional delay does, but I suspect it just makes some combination of events less probable.

Hopefully the probability is very low :confused:

I doubt this will ever be 100% fixed until someone discovers that elusive combination of events.

jdb

BTW: I'm running 32 bit also

---

### Post by badbull on 2009-02-15
I'm running the jaunty kernel under intrepid (you can just add the jaunty ppa to your sources list). for me the patch works well. i didn't get any wrong value. on the old it just happend everytime.

maybe the patch doesn't work 100% but just 90%. so its better than nothing ;-)

@Tom: finding out a delay fix the problem was just a fluke. I don't see any chance to get a fix for the suspend thing.

---

### Post by badbull on 2009-02-24
the patch will be included in the next kernel version 2.6.29. hopefully it will also be added to the next ubuntu kernel.

---

### Post by jdb on 2009-02-24
> **badbull said:**
> the patch will be included in the next kernel version 2.6.29. hopefully it will also be added to the next ubuntu kernel.

Cool!!!! :popcorn:

---

### Post by laserline on 2009-02-24
Hi,

So I guess that means we'll probably see it on 9.10

What are the odds this will be in 9.04's kernel as an ubuntu patch ?

Idan.

---

### Post by ackey on 2009-03-18
After not being on my Daru2 for a while, I wanted to catch up with the party and install the fix.

One problem: I can't figure out how to.  I've added the ppa, added the key, did the update/upgrade.  Now what?  It didn't look like it was included in the packages gotten on the upgrade.  I can't seem to "find" something called linux - 2.6.27-11.27 anywhere via synaptic or aptitude.  

So can someone hold my hand through this?  What does an unknowledgeable end-user need to do to get this working?

Thanks!

Edit: Currently using 2.6.27-9-generic, Intrepid Ubuntu

---

### Post by badbull on 2009-03-18
hm, i can't test, because my notebook is away for repairing.
you could install the deb file manually.
download [http://ppa.launchpad.net/timo-tretter/ppa/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.27~ppa0_i386.deb](http://ppa.launchpad.net/timo-tretter/ppa/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.27~ppa0_i386.deb) for i386 or [http://ppa.launchpad.net/timo-tretter/ppa/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.27~ppa0_amd64.deb](http://ppa.launchpad.net/timo-tretter/ppa/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.27~ppa0_amd64.deb) for amd64 and install it.

edit: you are using 2.6.27-9 the latest intrepid kernel is 2.6.29-11. maybe just install the latest kernel with ```
 sudo apt-get instal linux-image-2.6.27-11-generic
``` fix the problem

---

### Post by badbull on 2009-03-18
> **laserline said:**
> Hi,

So I guess that means we'll probably see it on 9.10

What are the odds this will be in 9.04's kernel as an ubuntu patch ?

Idan.

if ubuntu 9.04 will not include the patch i'll update the ppa for every kernel update. otherwise you can install the vanilla kernel as deb package from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
these packages are build from the original source without any patches from ubuntu. all versions from 2.6.29-rc5 should include the patch.

---

### Post by ackey on 2009-03-19
Thanks badbull, I had to both update menu.lst and force your version in synaptic.  I think I'm running on the right kernel now.

However, I'm still having the no-battery/high temp bug in acpi.  This *may* have fixed glitches I was seeing with my touchpad.  I see that other users have still had problems with acpi after applying this patch on 32bit Intrepid.  Will upgrading to Jaunty (and installing patch) work better?

---

### Post by badbull on 2009-03-20
> **ackey said:**
> Thanks badbull, I had to both update menu.lst and force your version in synaptic.  I think I'm running on the right kernel now.

However, I'm still having the no-battery/high temp bug in acpi.  This *may* have fixed glitches I was seeing with my touchpad.  I see that other users have still had problems with acpi after applying this patch on 32bit Intrepid.  Will upgrading to Jaunty (and installing patch) work better?

are you sure you running the right kernel? on other users the problems appears only after dates. please print the output of ```
uname -r
```

---

### Post by ackey on 2009-03-24
uname -r provides 2.6.27-11-generic and I have that version locked (in Synaptic) to the ppa0 version, which I think is yours.

I haven't had the power management issue reoccur since the first day, but my touchpad is acting up again today.  I know these problems are hard to diagnose when it is a day-by-day issue.

I've been trying to watch dmesg for things that might be a hint into what appears to be a acpi/mouse issue.  In the following snippet, are either of the first two lines indicative of anything?

```
[  411.980220] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 1241.408087] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1660.805258] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[ 1660.805273] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[ 1660.806170] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[ 1660.806176] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[ 4262.862999] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
[ 4262.863013] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[ 4262.864036] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
[ 4262.864044] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[ 4263.385589] CPU0 attaching NULL sched-domain.
[ 4263.385597] CPU1 attaching NULL sched-domain.
[ 4263.388145] CPU0 attaching sched-domain:
[ 4263.388152]  domain 0: span 0-1 level MC
[ 4263.388157]   groups: 0 1
[ 4263.388166] CPU1 attaching sched-domain:
[ 4263.388170]  domain 0: span 0-1 level MC
[ 4263.388173]   groups: 1 0
[ 4263.624056] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[ 4263.624063] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[ 4263.624980] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[ 4263.624983] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[ 4899.452081] CE: hpet increasing min_delta_ns to 22500 nsec

```

When I saw the touchpad error today:
```
[20418.056616] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[20418.057434] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[20418.058368] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[20418.059317] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[20418.060280] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[20418.060289] psmouse.c: issuing reconnect request
[20418.490396] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[20419.310531] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[20419.342515] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10

```

I realize that the touchpad issue, the power management work-around, and the CE and ACPI: EC lines might all be unrelated, but if any of these printouts are unique to me, I figure they might be related to the problem.

---

### Post by thomasaaron on 2009-03-25
ackey,

Does your touchpad ever quite working?

---

### Post by ackey on 2009-03-25
So far it hasn't stop responding permanently, but it is still glitching - not responding for a second, usually my music skips too.  In the past (previous touchpad, Ubuntu versions, kernels...) glitching would eventually lead to constant fake signals to mouse and keyboard - my computer would look possessed.  The glitching used to be accompanied by ACPI failures (battery and temp) and a spike in my CPU usage chart.  Now (with this kernal modification) I don't seem to be getting those now.

My dmesg for this morning:
```
[  291.985027] ACPI: EC: missing confirmations, switch off interrupt mode.
[  477.072059] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1769.039289] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 1769.040184] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1769.041113] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1769.042088] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1769.043028] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1769.043040] psmouse.c: issuing reconnect request
[ 1769.828990] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[ 1769.863993] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[ 1770.328600] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1770.329562] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1770.330466] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1770.331416] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1770.332349] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1770.332356] psmouse.c: issuing reconnect request
[ 1771.073842] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[ 1771.104607] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[ 1915.062112] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1915.062950] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1915.063875] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1915.064815] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1915.065754] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1915.065760] psmouse.c: issuing reconnect request
[ 1916.095424] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[ 1916.126455] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[ 2109.276986] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2109.277939] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2109.278846] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2109.279824] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2109.280729] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2109.280736] psmouse.c: issuing reconnect request
[ 2110.122163] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[ 2110.164312] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input12
[ 2112.715682] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2112.716500] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2112.717465] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2112.718411] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2112.719370] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2112.719376] psmouse.c: issuing reconnect request
[ 2113.549617] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[ 2113.581316] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input13
[ 2137.910468] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 2137.911301] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2137.912238] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2137.913186] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2137.914153] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 2137.914160] psmouse.c: issuing reconnect request
[ 2138.633755] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 2138.989506] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[ 2139.817500] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[ 2139.850039] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input14

```  

But the mouse is "losing sync" a few times a minute sometimes, which makes use difficult.  I've found that if I use Fn-F3 to disable the touchpad and use an external mouse I don't see these issues.

---

### Post by thomasaaron on 2009-03-25
The last few times I've seen these errors on a DarU2, the touchpad was on its way out.

Does anybody else using the kernel patch see these messages?

---

### Post by jdb on 2009-03-25
> **badbull said:**
> if ubuntu 9.04 will not include the patch i'll update the ppa for every kernel update. otherwise you can install the vanilla kernel as deb package from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
these packages are build from the original source without any patches from ubuntu. all versions from 2.6.29-rc5 should include the patch.

I just loaded loaded kernel 2.26.29 & got:

15:24:38 ~ dmesg | grep "ACPI: EC"
ACPI: EC: Enabling special treatment for EC from MSI.
ACPI: EC: Look up EC in DSDT
ACPI: EC: non-query interrupt received, switching to interrupt mode
ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
ACPI: EC: driver started in interrupt mode


Notice the "special treatment for EC from MSI" line.

:guitar:

jdb

---

### Post by laserline on 2009-05-13
Hi Badbull,

I've installed the patched kernel from the ppa.
I'm running the latest Intrepid kernel from there

uname -r states: 2.6.27-14-generic

In Grub I removed the ACPI=NOIRQ line and The battery is disabled + temp off the charts (146c)

Should it be enabled with the patch ?

How do I make sure that the patch works ?

dmesg gives this:
```

[    0.492808] ACPI: EC: Look up EC in DSDT
[    0.516241] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.520214] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.520214] ACPI: EC: driver started in interrupt mode

```

I tried installing the Jaunty kernel on my Intrepid laptop, but dependencies aren't resolved.

Thnaks,
Idan.

---

### Post by badbull on 2009-05-24
hi idan,

sorry for my absence. MSI sucks on repairing the webcam...

first you should try ```
dmesg | grep "ACPI: EC"
```
if you get something like "Enabling special treatment for EC from MSI." the patch is in the kernel.

because i'm not on intrepid anymore, the intrepid package of the ppa is may outdated (mine is 2.6.27-11).
I'll update this in the next weeks.
otherwise you can install the mainline kernel (unpatched vanilla kernel as deb package).
it will include the patch since 2.6.29
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
take 2.6.29.4

---

### Post by laserline on 2009-05-24
Hi,

Thanks for your response, I already got the mainline kernel (2.6.29.3) - I will update to 2.6.29.4
The patch works, and it's good to have the battery monitor back :)
Does the 2.6.29 kernel fix the sqlite issue ?

Thanks,
Idan

---

### Post by ackey on 2009-06-07
> **badbull said:**
> 
first you should try ```
dmesg | grep "ACPI: EC"
```
if you get something like "Enabling special treatment for EC from MSI." the patch is in the kernel.


I just upgraded to jaunty (hoping all of my problems would be fixed) and was still seeing power management issues.  I tried the mainline 2.6.29 kernel, but I'm not seeing the message above.  I haven't seen any strange behavior for the 15 minutes since starting with the new kernel, so perhaps it is working.

If this does start failing, what is the best known method for dealing with ACPI on Daru2 running jaunty?

---

### Post by ackey on 2009-06-08
Ok - I'm still on the mainline 2.26.29 kernel and I've lost the battery monitor.  So where do I get the kernel with the MSI fix from?

---

### Post by jdb on 2009-06-08
> **ackey said:**
> Ok - I'm still on the mainline 2.26.29 kernel and I've lost the battery monitor.  So where do I get the kernel with the MSI fix from?

I'm running the 2.6.29 kernel with Arch Linux on a Daru2, power management works correctly & I get the "... EC from MSI" message.
I've also tried the vanilla kernel from kernel.org and get the same results.

I once installed a 2.6.29 kernel in Ubuntu & it worked correctly also.
I once installed BadBull's patch & it worked good too.
Sometimes patches break with new releases, I haven't tried it recently.

I'm not familiar with "mainline 2.26.29 kernel", how did you install it???

jdb

---

### Post by ackey on 2009-06-08
I got the kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).  It just intalled with dkpg, which I can handle.  I hadn't realized there was a difference (as there apparently is) so I had gone for the one that seemed simpler.

I started trying to compile the kernel from kernel.org, but I have absolutely no clue what I am doing.  Is there an easy way to figure out the answers to the config questions?  I was just using the default ones, but there isn't a default for the RCU configuring.

---

### Post by jdb on 2009-06-08
> **ackey said:**
> I got the kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).  It just intalled with dkpg, which I can handle.  I hadn't realized there was a difference (as there apparently is) so I had gone for the one that seemed simpler.

I started trying to compile the kernel from kernel.org, but I have absolutely no clue what I am doing.  Is there an easy way to figure out the answers to the config questions?  I was just using the default ones, but there isn't a default for the RCU configuring.


That's a cool directory, I didn't know about it.

I just downloaded linux-source-2.6.29_2.6.29-020629_all.deb and untarred the source code.
The following is from that source so it looks like the patch made it into code OK.

```
14:40:05 acpi grep MSI ec.c
static int EC_FLAGS_MSI; /* Out-of-spec MSI controller */
	if (EC_FLAGS_MSI)
		pr_info(PREFIX "Enabling special treatment for EC from MSI.\n");
		EC_FLAGS_MSI = 1;
```

You might double check that you loaded the kernel itself & not just the headers.
You can check what you are running with:

```
uname -a
```


jdb

---

### Post by ackey on 2009-06-08
I downloaded linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb and I see with uname -r that I'm running 2.6.29-020629-generic, so I think I'm on the right kernel.  I definitely don't see the line in my dmesg - should I be looking in a different log?

---

### Post by jdb on 2009-06-08
> **ackey said:**
> I downloaded linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb and I see with uname -r that I'm running 2.6.29-020629-generic, so I think I'm on the right kernel.  I definitely don't see the line in my dmesg - should I be looking in a different log?

It should be in the dmesg output, this is what I get:

```
15:25:38 ~ dmesg | grep "EC from MSI"
ACPI: EC: Enabling special treatment for EC from MSI.
```

I haven't compiled the mainline kenel so I can't say for sure, but the code is definately in the source.

This code will only be activated on computer like the Daru2 with MSI bios.
Have you reflashed your bios??

jdb

---

### Post by ackey on 2009-06-08
I've certainly never tried to reflash my bios (I doubt it is something I can accidentally do through stupidity).  I see it is determining the EC_FLAGS_MSI by

```

        if (dmi_name_in_vendors("Micro-Star") ||
	    dmi_name_in_vendors("Notebook")) {

```

Is there a way for me to check how this is specified in my machine?

---

### Post by ackey on 2009-06-08
I restarted and looked through the BIOS to see if there was anything of note.  I found:
BIOS Build A1221IG6 Ver 3.47 12/19/2008

I've had the computer since 2007, so the BIOS was updated at some point.

---

### Post by jdb on 2009-06-08
> **ackey said:**
> I restarted and looked through the BIOS to see if there was anything of note.  I found:
BIOS Build A1221IG6 Ver 3.47 12/19/2008

I've had the computer since 2007, so the BIOS was updated at some point.

That's odd!

How did you look through the BIOS???

I'll take a look at mine & see what it says.


jdb

---

### Post by ackey on 2009-06-08
Ah, by looking through the BIOS, I just mean the configuration menu available on startup.

I asked my partner (who also has a DarU2) to check his and he found:
BIOS Build A1221IG6 V1.10 5/28/07

So the A1221IG6 isn't particularly identifying, but somehow we have very different versions and dates.  He got his computer 6 months or so after I did, but I sent mine in to System76 for some maintenance in Jan of 2009.  So perhaps they loaded a new BIOS version?  

I know my partner claims to have no problem with power management.

---

### Post by jdb on 2009-06-08
> **ackey said:**
> Ah, by looking through the BIOS, I just mean the configuration menu available on startup.

I asked my partner (who also has a DarU2) to check his and he found:
BIOS Build A1221IG6 V1.10 5/28/07

So the A1221IG6 isn't particularly identifying, but somehow we have very different versions and dates.  He got his computer 6 months or so after I did, but I sent mine in to System76 for some maintenance in Jan of 2009.  So perhaps they loaded a new BIOS version?  

I know my partner claims to have no problem with power management.

HA HA that's easier than I was thinking.

My BIOS matches your partners exactly.
I think you've gotten to the root of the problem but I don't know the fix.
You could hack the ec.c code to load the fix unconditionally but that would be a pain every time there was a kernel update.

I wonder if there's any way to flash the BIOS to what it was originally??
Maybe Tom Aaron knows.

jdb

---

### Post by thomasaaron on 2009-06-09
It's hard to say for sure what the BIOS was originally. Probably when we sent your machine in for the touchpad problem they flashed the BIOS to bring it up to date.

Your partner's BIOS, version 1.10 was definitely one of the first versions, though. I remember there were some imaging problems with it, so we started updating to the next version... (1.2**, I think).

I find it curious your partner has no power management problems with version 1.10, though.

---

### Post by ackey on 2009-06-09
So this new BIOS means I can't use the existing patches for power management?  

I wouldn't mind hacking the ec.c code, but compiling the kernel terrifies me.  What other options might there be?

---

### Post by jdb on 2009-06-09
> **ackey said:**
> So this new BIOS means I can't use the existing patches for power management?  

I wouldn't mind hacking the ec.c code, but compiling the kernel terrifies me.  What other options might there be?

Maybe Tom can fix you up with the 1.2 version if they still have a copy.
It might work.

jdb

---

### Post by thomasaaron on 2009-06-09
Yeah, contact me via email (support(at)system76(dot)com) and I'll see what I can dig up....

---

### Post by williumbillium on 2009-06-28
Just a quick note to those Daru2 users using Timo's PPA that they might want to stick with 2.6.28-11 until Timo adds a patched 2.6.28-13 kernel to his repository.

---

### Post by werewolves on 2009-08-11
> **williumbillium said:**
> Just a quick note to those Daru2 users using Timo's PPA that they might want to stick with 2.6.28-11 until Timo add's a patched 2.6.28-13 kernel to his repository.
Anyone have an idea when this might happen? ;)  Perhaps System76 should officially take this over!!

---

### Post by werewolves on 2009-10-08
> **werewolves said:**
> Anyone have an idea when this might happen? ;)  Perhaps System76 should officially take this over!!

So.... any ideas System 76 folks?  Any chance you guys can take this patch over?  Would like my suspend to work on the latest kernel.

---

### Post by williumbillium on 2009-10-08
> **werewolves said:**
> So.... any ideas System 76 folks?  Any chance you guys can take this patch over?  Would like my suspend to work on the latest kernel.

First of all, this bug (the power management bug) and the suspend bug are separate.  Fixing this one doesn't solve suspend.

Second, I wouldn't expect System 76 to start providing this patch at this point.  It was fixed in the mainline kernel and will finally be included in the Karmic kernel (only a few weeks away from release now), at which point a patch will no longer be needed.

That said, I'm pretty disappointed that System 76 never provided this patch in the driver.  I haven't been able to update my kernel in over 3 months now and before that I was relying on a 3rd party PPA for updates.  Surely this is the kind of thing System 76 should be taking care of?

---

### Post by werewolves on 2009-10-09
> **williumbillium said:**
> First of all, this bug (the power management bug) and the suspend bug are separate.  Fixing this one doesn't solve suspend.

Second, I wouldn't expect System 76 to start providing this patch at this point.  It was fixed in the mainline kernel and will finally be included in the Karmic kernel (only a few weeks away from release now), at which point a patch will no longer be needed.

That said, I'm pretty disappointed that System 76 never provided this patch in the driver.  I haven't been able to update my kernel in over 3 months now and before that I was relying on a 3rd party PPA for updates.  Surely this is the kind of thing System 76 should be taking care of?

I fully agree.  Disappointing.

I didn't realize that it was fixed in Karmic, that's good news.  Thanks for the heads up.

---

