---
title: "Power management (daru2)"
date: 2008-04-28
forum: System76 Support
---

### Post by nowanfoo on 2008-04-28
The old thread on this subject seems to be gone.

The problem is that power management goes haywire on the daru2: the screen dims and brightens, the battery status (both whether it's on AC, and the charge level) is horribly confused.  Setting the brightness control not to dim when on battery helps make the system usable when this happens.

This is with gutsy and kernel 2.6.22-14.  Setting ec_intr=0 in the boot helps, but even with that the system can frequently get into a state where the battery status goes haywire.  Typically this is after the laptop has been off an on a bit without being on AC between power-ups.

If anyone knows where this is being discussed now, can you post it in a follow-up?

---

### Post by freduardo on 2008-04-28
The old thread:
[http://ubuntuforums.org/showthread.php?t=609722]("http://ubuntuforums.org/showthread.php?t=609722")
was moved to Ubuntu Forums > The Ubuntu Forum Community  > Forum Archive  > Main Support Categories  > System76 Support

Another thread:
[http://ubuntuforums.org/showthread.php?t=764970]("http://ubuntuforums.org/showthread.php?t=764970")
on the suspend problems.

---

### Post by badbull on 2008-04-28
as you might read the ec_intr kernel option has been removed in the newer kernel. this option activate/deactivate the sending of acpi interrupts. the daru2 sends worng acpi interrupts so we use the polling mode in gutsy.(ec_intr=0)
in the new kernel the acpi embedded controler (drivers/acpi/ec.c) trys to set the mode to interrupt, if this fails it goes back to poll mode. you can't control this via boot option.
at the moment i'm compiling a hardy kernel with a modified ec.c. i'll post my experience on this later...maybe we have luck and get a kernel patch from ubuntu or system76.

---

### Post by laserline on 2008-04-29
If it supposed to fallback to polling automatically but doesn't actually do that, then that affects much more systems (I own a daru2).

I guess there should be a kernel update to fix that bug. not just a fix for system76 systems.

Although I won't mind this being fixed ASAP :)

Please see this post: [http://ubuntuforums.org/showthread.php?t=764970](http://ubuntuforums.org/showthread.php?t=764970)

Idan.

---

### Post by badbull on 2008-04-29
i had installed my selfbuild kernel with a default polling mode. it seems to work right, but i didn't test it much.
you can download it from ....

[edit] sorry, doesn't work...just for 3 hours then it goes crazy...

---

### Post by thomasaaron on 2008-04-29
We too are rolling a custom kernel that should set things straight.
It will probably take a few days.

---

### Post by jdb on 2008-04-29
I really like the acpi=noirq boot option.
It never goes crazy.
For me the lack of a screen brightness control has become a non issue because I like it full bright all the time anyway.

I still think I'm going to write a little progam with a brightness slider but it may be a while.  I'm trying to learn lisp & decided to make that my first project after the tutorial stuff I'm doing.  I'm an old vi guy & I'm having a heck of a time with emacs, much less the dang lisp :)

jdb

---

### Post by laserline on 2008-04-29
If you need any testing, please let me know.

Idan.

---

### Post by laserline on 2008-04-29
> **jdb said:**
> I really like the acpi=noirq boot option.
It never goes crazy.
For me the lack of a screen brightness control has become a non issue because I like it full bright all the time anyway.

I still think I'm going to write a little progam with a brightness slider but it may be a while.  I'm trying to learn lisp & decided to make that my first project after the tutorial stuff I'm doing.  I'm an old vi guy & I'm having a heck of a time with emacs, much less the dang lisp :)

jdb

You can meanwhile use the brightness gnome applet. It works great.

---

### Post by zombiepig on 2008-04-30
is it possible that we are seeing the same problem (with different hardware) over here?
[http://ubuntuforums.org/showthread.php?t=765213](http://ubuntuforums.org/showthread.php?t=765213)
Or am I way off track? :P

---

### Post by badbull on 2008-04-30
did you use the ec_intr=0 option in gutsy (2.6.22 kernel)?

maybe the new implementation of the embedded controler raise more problems...

---

### Post by jdb on 2008-04-30
> **laserline said:**
> You can meanwhile use the brightness gnome applet. It works great.
Thanks but I run xubuntu.
I've never figured out how to use those gnome applets without a gnome desktop.
xfce4 has a lot of good applets, but I can't find one that controls the brightness.

jdb

---

### Post by 22bsti on 2008-04-30
I'm with you jdb xfce or obenbox for me. Gnome is too slow feels like windows.

---

### Post by thomasaaron on 2008-04-30
Well, that would be the *first* time I've heard gnome compared to Windows!:lolflag:

Generally, people are saying KDE feels like windows.

---

### Post by jdb on 2008-04-30
I don't know how it is now, but back awhile I had a lot of trouble with nautilus & HUGE directries, it would take forever to list all the files.

I tried thunar & it was downright snappy.
I removed nautilus & that removed the whole gnome desktop.
What was left was xfce but no "desktop".
That's when I loaded xubuntu to get an nice, tested, integrated xfce desktop.

Xubuntu has everything I need but it's a leaner system than gnome.

jdb

---

### Post by impact on 2008-05-01
> **zombiepig said:**
> is it possible that we are seeing the same problem (with different hardware) over here?
[http://ubuntuforums.org/showthread.php?t=765213](http://ubuntuforums.org/showthread.php?t=765213)
Or am I way off track? :P

With the MSI laptops it's the same problem (MSI doesn't support linux on most laptops and their BIOS is broken).

---

### Post by laserline on 2008-05-01
The daru2 is an MSI laptop.
OEM: MS-1221.
MSI Branded: MSI PR200

Idan.

---

### Post by thomasaaron on 2008-05-01
The MS-1221 had excellent support under Gutsy64 bit.
There has been a kernel change in Hardy we're dealing with. Carl has made some good progress though towards fixing it.

---

### Post by laserline on 2008-05-01
A couple of questions:

1. Is this change a kernel module or a custom kernel ?
2. What is to be done, so that future versions of the Ubuntu / Kernel won't break this fix ?
3. Are you working with the Ubuntu developers on streamlining these fixes ?

Thanks,

Idan

---

### Post by thomasaaron on 2008-05-01
> 1. Is this change a kernel module or a custom kernel ?
Not sure yet. Carl is holed up in his laboratory with a Do Not Disturb sign up until he gets it fixed. I'll report back when I know for sure. :guitar:


> 2. What is to be done, so that future versions of the Ubuntu / Kernel won't break this fix ?
3. Are you working with the Ubuntu developers on streamlining these fixes ?

Yes. Hopefully we can get the fix moved up to Ubuntu to prevent it from happening again.

---

### Post by laserline on 2008-05-01
Thanks for keeping us posted.

---

### Post by laserline on 2008-05-06
Hi Tom,

Any news on this issue ?

Thanks,

Idan.

---

### Post by thomasaaron on 2008-05-06
It's proving difficult to figure out exactly where the suspend problem is occurring in the new kernel. We've sent a DarU2 to an Ubuntu developer who should be able to help us find the problem.

As for the battery management issue, look at the last post by Carl here...
[http://ubuntuforums.org/showthread.php?t=609722&page=15](http://ubuntuforums.org/showthread.php?t=609722&page=15)

Adding the acpi=noirq kernel option fixes it, but with some minor side effects. It's still worth it though. Carl gives directions for inserting this option in the aforementioned thread.

---

### Post by TheBuzzSaw on 2008-05-06
Where do I go to set "acpi=noirq"? I've never tweaked these settings before. :/

---

### Post by windtracekimo on 2008-05-06
edit the file /boot/grub/menu.lst with root previlege (or sudo).
Usually these boot scripts are listed at the bottom of the file. (like the following, each boot image is defined and started by "title")

title       Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel      /boot/vmlinuz-2.6.24-16-generic root=UUID=3fd94c09-430d-4fa8-b1a2-e242bb7a9ba8 ro quiet splash
initrd      /boot/initrd.img-2.6.24-16-generic
quiet

First, find out which kernel image you are using by looking at the "default=". If is "default=0", then you are currently using the first image listed as above.
Then add "acpi=noirq" at the end of the "kernel" line. The "ro" "quiet" "splash" are all options for booting the kernel.
Then save it and reboot.

---

### Post by bkloppenborg on 2008-05-28
Does anyone know the status on this problem?  Has the Ubuntu developer came up with any (permanent) fixes?  Thank you.

---

### Post by thomasaaron on 2008-05-29
Unfortunately, not yet. But we still have a several things left to try.
I'll keep you posted on it.

---

### Post by ceminino on 2008-06-18
Is anyone having shutdowns because of heat? It happens either in Poll of interrupt mode of the EC when the cpu is on high load. This is really annoying. I have the T7300 cpu. The worst is that just watching some stuff in flash can cause this overheating. Any solutions? I have ubuntu 8.04 32 bit.

---

### Post by badbull on 2008-06-20
i can confirm this issue. while compiling a kernel the temperature gets up to 90°. my msi pr200 had shut down two times because of heat.
but i can't confirm this on watching flash videos. maybe take a look at the temperatur ```
cat /proc/acpi/thermal_zone/THRM/temperature
```
and how much is the cpu load on while watching flash videos
```
top
```
btw. ensure the laptop gets fresh air from the bottom.

---

### Post by ceminino on 2008-06-20
The critical temperature for shutdown seems to be just above 90 degrees. 

and exemple of flash video is here 
[http://www.storyofstuff.com/](http://www.storyofstuff.com/)
it's about 20 minutes, no way to watch it :S

Fresh air from the bottom, how? I just put the laptop on a table.

I know that this laptop is not meant for computing (even if I test some mpi codes for short times) but still this is really annoying!

---

### Post by jdb on 2008-06-20
> **badbull said:**
> i can confirm this issue. while compiling a kernel the temperature gets up to 90°. my msi pr200 had shut down two times because of heat.
but i can't confirm this on watching flash videos. maybe take a look at the temperatur ```
cat /proc/acpi/thermal_zone/THRM/temperature
```
and how much is the cpu load on while watching flash videos
```
top
```
btw. ensure the laptop gets fresh air from the bottom.

I've never had my daru2 shut down but I do see the high 80s when I compile a kernel or make a coding mistake & get it stuck in a loop.
I've probably been a few degree's away from it.
When I run sensors to check the temp it says the critical temp is 100.

jdb

---

### Post by ceminino on 2008-06-20
do you have 32 bit or 64 bit ubuntu?

---

### Post by jdb on 2008-06-20
> **ceminino said:**
> do you have 32 bit or 64 bit ubuntu?

I've got 32 bit loaded.

jdb

---

### Post by williumbillium on 2008-08-28
The following was just posted on this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/139701/]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/139701/") in launchpad:

> The Ubuntu Kernel Team is planning to move to the 2.6.27 kernel for the upcoming Intrepid Ibex 8.10 release. As a result, the kernel team would appreciate it if you could please test this newer 2.6.27 Ubuntu kernel. There are one of two ways you should be able to test:

1) If you are comfortable installing packages on your own, the linux-image-2.6.27-* package is currently available for you to install and test.

--or--

2) The upcoming Alpha5 for Intrepid Ibex 8.10 will contain this newer 2.6.27 Ubuntu kernel. Alpha5 is set to be released Thursday Sept 4. Please watch [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing) for Alpha5 to be announced. You should then be able to test via a LiveCD.

Please let us know immediately if this newer 2.6.27 kernel resolves the bug reported here or if the issue remains. More importantly, please open a new bug report for each new bug/regression introduced by the 2.6.27 kernel and tag the bug report with 'linux-2.6.27'. Also, please specifically note if the issue does or does not appear in the 2.6.26 kernel. Thanks again, we really appreicate your help and feedback.

Anyone have an intrepid install to test with?

It seems there is at least a little bit of hope that the problem has been fixed in kernel 2.6.27:

 [http://bugzilla.kernel.org/show_bug.cgi?id=9823#c53](http://bugzilla.kernel.org/show_bug.cgi?id=9823#c53)

That bug is related to a different msi model but seems similar (at least in my very limited understanding) to the daru2 problems.  I don't know if that patch is actually in the ubuntu kernel yet though (nor how to check if it is).

---

### Post by badbull on 2008-08-29
the power management problem (wrong battery/display dimming) is fixed in 2.6.27. the kernel will automatic use poll mode for acpi.
suspend is still not working.

---

### Post by williumbillium on 2008-08-29
That's good news.  I've got to admit that I was hoping it would fix suspend too though.

---

### Post by laserline on 2008-08-29
> **williumbillium said:**
> That's good news.  I've got to admit that I was hoping it would fix suspend too though.

Yeah,

I was hoping suspend would be fixed too.

Does hibernate work as expected ?

Idan.

---

### Post by gaussian on 2008-08-29
> **laserline said:**
> Yeah,

I was hoping suspend would be fixed too.

Does hibernate work as expected ?

Idan.

Works on a 32-bit at least with s2disk (I always use that). I can try the regular (pm-hibernate) later tonight, if I remember correctly I had some problems with it with an earlier kernel (I might be wrong).

---

### Post by laserline on 2008-08-29
How do you use s2disk instead of pm-hibernate ?

Idan.

---

### Post by gaussian on 2008-08-29
> **laserline said:**
> How do you use s2disk instead of pm-hibernate ?

Idan.

Install uswsusp package. After that you can try if its works from command line by trying 
```

sudo s2disk

```

If it works, you can make it functional in GUI by editing manually the script
```

/usr/lib/hal/scripts/linux/hal-system-power-hibernate

```

There might be less hacky ways of making it the default hibernating program, but I am not aware of them.

---

### Post by gaussian on 2008-08-29
Can confirm now that hibernate works in Intrepid with pm-hibernate.

---

### Post by Aggrocrag on 2008-09-10
I'm a little confused;
What have people gotten to work using intrepid?
Please include which versions (32 or 64 bit) you're using, and any modifications you did.
I am considering upgrading to ibex, so I'm trying to get a feel for how smooth it went for people, thanks.

---

### Post by gaussian on 2008-09-10
> **Aggrocrag said:**
> I'm a little confused;
What have people gotten to work using intrepid?
Please include which versions (32 or 64 bit) you're using, and any modifications you did.
I am considering upgrading to ibex, so I'm trying to get a feel for how smooth it went for people, thanks.

32-bit Intrepid (not a clean install, updated from Feisty-Gutsy-Hardy-Intrepid):

Hibernate works, with no modifications
Suspend does not --> If I remember correcly with modifications you can get the not-quite-suspending (standby-mode) to work, I am not using that


Couple annoying bugs still interfering with a smooth 32-bit Daru2 intrepid experience:

1. Touchpad settings get reset randomly. Does not happen in 64-bit Gutsy (my main installation), so unlikely to be a hardware problem
2. Virtual terminals disappear after restarting X. 

I am sure there are more. Generally after each update Intrepid seems to be getting more solid.

---

### Post by williumbillium on 2008-10-13
Another regression in the 2.6.27-7 kernel that breaks power management is being reported here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147560](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147560)  (scroll to the bottom)

---

### Post by laserline on 2008-10-13
> **williumbillium said:**
> Another regression in the 2.6.27-7 kernel that breaks power management is being reported here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147560](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147560)  (scroll to the bottom)


That guy just reported everything is OK after a bios upgrade:
> interestingly, after a BIOS upgrade, it works fine again

might just have been a fluke

---

### Post by williumbillium on 2008-10-14
> **laserline said:**
> That guy just reported everything is OK after a bios upgrade:

Well that's good at least.  So I guess the question is, was this a fluke or are we all going to have perform bios upgrades?

---

### Post by gaussian on 2008-10-14
Ok, tell me if I am being completely clueless here.

I have been using Intrepid 32-bit version quite a lot. Never had any problems with Battery not being detected. The clueless part: looking at the BIOS setup at the startup it looks like my BIOS version is 2.61. Incidentally, the MSI website has no BIOS versions starting with 2 (just 1 and 3). This is a Darter Ultra where I have never updated the BIOS.

Edit: ```
 sudo dmidecode -s bios-version
``` reports A1221IG6 V1.1.

---

### Post by williumbillium on 2008-10-14
> **gaussian said:**
> Ok, tell me if I am being completely clueless here.

I have been using Intrepid 32-bit version quite a lot. Never had any problems with Battery not being detected.

What kernel are you using gaussian?  I was using a live cd of intrepid alpha 5 that was running smoothly for me on the power management front too.

However, I have a feeling that it is 2.6.27-7.10 that would cause the regression.  I'm maybe getting out of my depth here, but the first item in [this changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.27-7.10/changelog)) is  [this patch]("http://www.uwsg.iu.edu/hypermail/linux/kernel/0810.1/1373.html").  It was only from a few days ago and I'd hazard a guess that it has implications for polling mode.  Perhaps someone with more knowledge could look at it.

---

### Post by gaussian on 2008-10-14
> **williumbillium said:**
> What kernel are you using gaussian?  I was using a live cd of intrepid alpha 5 that was running smoothly for me on the power management front too.

However, I have a feeling that it is 2.6.27-7.10 that would cause the regression.  I'm maybe getting out of my depth here, but the first item in [this changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.27-7.10/changelog)) is  [this patch]("http://www.uwsg.iu.edu/hypermail/linux/kernel/0810.1/1373.html").  It was only from a few days ago and I'd hazard a guess that it has implications for polling mode.  Perhaps someone with more knowledge could look at it.

Using  2.6.27.7.8, not seeing 2.6.27-10 anywhere yet. Will report back when I get it.

---

### Post by gaussian on 2008-10-14
Ok, now I am definitely running 2.6.27-7.10

And I am sad to report that the battery indicator is indicating 0% for the battery that should be about full. It looks like 2.6.27-7.11 is coming down the pipeline.

Edit: With new Kernel version (7.11) seems to be working. But I think it is 
a) too early to tell
b) the previous problem could have been just a fluke

---

### Post by thomasaaron on 2008-10-15
We've not tested the DarU2 with 8.10 yet. There will probably be a kernel option that needs to be added for the power management to work correctly. I'll post back when I know.

---

### Post by gaussian on 2008-10-16
> **gaussian said:**
> Ok, now I am definitely running 2.6.27-7.10

And I am sad to report that the battery indicator is indicating 0% for the battery that should be about full. It looks like 2.6.27-7.11 is coming down the pipeline.

Edit: With new Kernel version (7.11) seems to be working. But I think it is 
a) too early to tell
b) the previous problem could have been just a fluke

Replying my own post here: Now I am ready to confirm that it was not a fluke and that with both 7.10 and 7.11 version Battery Indicator looses the battery stochastically (and reboot seems to be only cure). Also stochastically I get nonsensical CPU-temperature readings: If my CPU really was at 146 Celsius right now (294.8 Fahrenheit) my Jeans would be burning:)

---

### Post by badbull on 2008-10-17
i think the new problem is caused by a "fix" from here: [http://bugzilla.kernel.org/show_bug.cgi?id=10724](http://bugzilla.kernel.org/show_bug.cgi?id=10724)

on some notebook some wrong irq was detected and the ec switched to poll mode although it isn't necessary. but it's enables the interrupt mode on daru2/msi pr200.

---

### Post by williumbillium on 2008-10-17
OK, so how should we proceed with this?  At least from looking at that particular patch, it doesn't seem there is a new kernel parameter to apply.  Where would one look to see any new parameters in this kernel?

Is there any chance at all of approaching MSI to fix the bios?  From my limited understanding, this problem seems to stem from the computer sending the wrong interrupt codes so the kernel then has to make workarounds (by switch to polling mode) for it.  Wouldn't it be better to look at this problem from the source so we don't keep getting these regressions?

A few months ago a big fuss was kicked up with the bios that Foxconn provided with some of their motherboards and they ended up fixing it:

[http://ubuntuforums.org/showthread.php?t=869249](http://ubuntuforums.org/showthread.php?t=869249)

Interestingly the Daru2 bios comes from the same company, American Megatrends.  The issue that is raised in the first post in the above thread about the dsdt tables is very similar to the A1221IG6 V3.3
 bios on my daru2.

---

### Post by badbull on 2008-10-17
there is a newer bios from msi ([http://global.msi.com.tw/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1208](http://global.msi.com.tw/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1208)). i can't test it because i don't have a windows system to update.

an other and maybe better option is to get back the "ec_init=0" kernel parameter. i've tested some parameters described here [http://bugzilla.kernel.org/show_bug.cgi?id=10724](http://bugzilla.kernel.org/show_bug.cgi?id=10724) but nothing works for me.

---

### Post by jdb on 2008-10-17
> **badbull said:**
> there is a newer bios from msi ([http://global.msi.com.tw/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1208](http://global.msi.com.tw/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1208)). i can't test it because i don't have a windows system to update.

an other and maybe better option is to get back the "ec_init=0" kernel parameter. i've tested some parameters described here [http://bugzilla.kernel.org/show_bug.cgi?id=10724](http://bugzilla.kernel.org/show_bug.cgi?id=10724) but nothing works for me.

I can't test it because I'm running kernel 2.6.26 which doesn't have a problem, but the parameter that fixed it in 2.6.24 was acpi=noirq.

I haven't downloaded 2.6.27 source, but if someone has, the valid kernel parameters will be lested in /usr/src/linux-source-2.6.27/Documentation/kernel-parameters.txt

jdb

---

### Post by williumbillium on 2008-10-17
> **badbull said:**
> there is a newer bios from msi ([http://global.msi.com.tw/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1208](http://global.msi.com.tw/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1208)). i can't test it because i don't have a windows system to update.

It is being reported [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147560/comments/58") (part of [this bug ticket]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147560")) that bios v3.43 does not fix the kernel regression.

---

### Post by badbull on 2008-10-18
> **jdb said:**
> I can't test it because I'm running kernel 2.6.26 which doesn't have a problem, but the parameter that fixed it in 2.6.24 was acpi=noirq.

I haven't downloaded 2.6.27 source, but if someone has, the valid kernel parameters will be lested in /usr/src/linux-source-2.6.27/Documentation/kernel-parameters.txt

jdb

acpi=noirq is still a kernel option and it starts the driver in poll mode. but it's still disable the brightness hotkeys.
we need a kernel option witch just start the ec in poll mode but does not affect any other funktions.

---

### Post by jdb on 2008-10-18
> **badbull said:**
> acpi=noirq is still a kernel option and it starts the driver in poll mode. but it's still disable the brightness hotkeys.
we need a kernel option witch just start the ec in poll mode but does not affect any other funktions.

I know this isn't going to help you in Ubuntu, but just an FYI:

In the ARCH OS they just released 2.6.27-ARCH kernel & I loaded it last night.
They use pretty much the the kernel straight form kernel.org, not much in the way of patches.
ACPI works perfectly & so do the brightness keys.

jdb

---

### Post by badbull on 2008-10-18
the ubuntu kernel works fine until 2.6.27-7.
i found a patch witch add the old ec_intr option to the ec driver.
[http://bugzilla.kernel.org/attachment.cgi?id=17355](http://bugzilla.kernel.org/attachment.cgi?id=17355)
don't know if this still works with the last ubuntu kernel

---

### Post by williumbillium on 2008-10-18
> **jdb said:**
> In the ARCH OS they just released 2.6.27-ARCH kernel & I loaded it last night.
They use pretty much the the kernel straight form kernel.org, not much in the way of patches.
ACPI works perfectly & so do the brightness keys.

jdb

This might just be because the arch kernel doesn't have the latest patches.  The patch in question (that puts the daru 2 in interrupt mode) was only from a week ago.

---

### Post by badbull on 2008-10-18
a patch for the driver/acpi/ec.c could look like this...
it adds the old ec_intr=0 kernel option
```

119a120,121
> int acpi_ec_intr = 1; /* Default is interrupt mode */
> 
293a296,299
> 	if (acpi_ec_intr == 0) {
> 		pr_debug(PREFIX "GPE storm detected\n");
> 		set_bit(EC_FLAGS_GPE_STORM, &ec->flags);
> 	}
1026a1033,1044
> static int __init acpi_ec_set_intr_mode(char *str)
> {
> 	if (!get_option(&str, &acpi_ec_intr)) {
> 		acpi_ec_intr = 0;
> 		return 0;
> 	}
> 	return 1;
> }
> 
> __setup("ec_intr=", acpi_ec_set_intr_mode);
> 
> 
```

---

### Post by jdb on 2008-10-18
> **williumbillium said:**
> This might just be because the arch kernel doesn't have the latest patches.  The patch in question (that puts the daru 2 in interrupt mode) was only from a week ago.

Does that patch come from Ubuntu or from kernel.org?

I'm not sure but I think the Ubuntu folks ( Canonical ???) write a lot of those patches.

I've always been curious about how that works, can anyone shed some light?

jdb

---

### Post by thomasaaron on 2008-10-18
williumbillium, 

Does suspend work with that kernel?

---

### Post by badbull on 2008-10-19
> **jdb said:**
> Does that patch come from Ubuntu or from kernel.org?

I'm not sure but I think the Ubuntu folks ( Canonical ???) write a lot of those patches.

I've always been curious about how that works, can anyone shed some light?

jdb

the bad patch was from kernel.org. some people mentioned that their system is unstable the ec poll mode.
i think we have to open a new bug in lauchpad or at the kernel bugtracker and hope we get back the ec_intr=0 option.

---

### Post by jdb on 2008-10-19
> **badbull said:**
> the bad patch was from kernel.org. some people mentioned that their system is unstable the ec poll mode.
i think we have to open a new bug in lauchpad or at the kernel bugtracker and hope we get back the ec_intr=0 option.

Thanks,

I think 2.6.27.2 was just released the other day so I,m guessing it's the first one, 2.6.27.1.
I'm going to be sure not to load it :)

I read through ChangeLog-2.6.27.1 & ChangeLog-2.6.27.2 but didn't see anything that seemed relevant to this issue.
I looked through the patches too. I didn't see anything, but I could have looked right at it & not recognized it.

These are the files affected:

16:16:28 Desktop grep "diff --git" < patch-2.6.27.1
diff --git a/Makefile b/Makefile
diff --git a/kernel/trace/Kconfig b/kernel/trace/Kconfig

16:16:55 Desktop grep "diff --git" < patch-2.6.27.2
diff --git a/Makefile b/Makefile
diff --git a/arch/x86/kernel/alternative.c b/arch/x86/kernel/alternative.c
diff --git a/arch/x86/kernel/early-quirks.c b/arch/x86/kernel/early-quirks.c
diff --git a/arch/x86/kernel/io_apic_32.c b/arch/x86/kernel/io_apic_32.c
diff --git a/arch/x86/mm/ioremap.c b/arch/x86/mm/ioremap.c
diff --git a/drivers/char/tty_io.c b/drivers/char/tty_io.c
diff --git a/drivers/net/atl1e/atl1e_main.c b/drivers/net/atl1e/atl1e_main.c
diff --git a/drivers/net/sky2.c b/drivers/net/sky2.c
diff --git a/drivers/net/wireless/b43legacy/xmit.c b/drivers/net/wireless/b43legacy/xmit.c
diff --git a/drivers/net/wireless/libertas/main.c b/drivers/net/wireless/libertas/main.c
diff --git a/fs/cifs/cifsglob.h b/fs/cifs/cifsglob.h
diff --git a/fs/cifs/cifssmb.c b/fs/cifs/cifssmb.c
diff --git a/fs/cifs/readdir.c b/fs/cifs/readdir.c
diff --git a/fs/xfs/linux-2.6/xfs_buf.c b/fs/xfs/linux-2.6/xfs_buf.c
diff --git a/fs/xfs/linux-2.6/xfs_buf.h b/fs/xfs/linux-2.6/xfs_buf.h
diff --git a/fs/xfs/xfs_log.c b/fs/xfs/xfs_log.c
diff --git a/kernel/sched_rt.c b/kernel/sched_rt.c
diff --git a/kernel/trace/Kconfig b/kernel/trace/Kconfig
diff --git a/net/mac80211/debugfs_netdev.c b/net/mac80211/debugfs_netdev.c
diff --git a/net/rfkill/rfkill.c b/net/rfkill/rfkill.c


That's why I was wondering if it might be something that Ubuntu did.

EDIT:

I patched to 2.6.27.1 & recompiled my kernel, so far so good, but its hard to tell until it soaks awhile.
I'm going to patch to 2.6.27.2 later today & give it a try.


jdb

---

### Post by badbull on 2008-10-20
try ```
dmesg | grep poll
``` to see if the ec driver is started in poll mode.
if you see something like this ```
[    0.860258] ACPI: EC: driver started in poll mode
```
everything is great.

---

### Post by jdb on 2008-10-20
> **badbull said:**
> try ```
dmesg | grep poll
``` to see if the ec driver is started in poll mode.
if you see something like this ```
[    0.860258] ACPI: EC: driver started in poll mode
```
everything is great.

This is 2.6.27.1

12:18:09 ~ dmesg | grep poll
ACPI: EC: driver started in poll mode
13:43:55 ~ 

I'm going to try 2.6.27.2 later today

jdb

---

### Post by badbull on 2008-10-20
i've tested 2.6.27.2 vanilla kernel. it also starts the the driver in poll mode. the bug seams to be only in the ubuntu kernel.

---

### Post by williumbillium on 2008-10-21
> **thomasaaron said:**
> williumbillium, 

Does suspend work with that kernel?

I haven't tried the latest Arch kernel.  The most recent ubuntu kernel I've used is the one with intrepid alpha 6.  Suspend did not work.

Also, if confirmation that the bad patch came from Ubuntu is still needed, does this help confirm?

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008342.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008342.html)

Wouldn't the patch be listed in upstream kernel changes if it came from kernel.org?

---

### Post by freduardo on 2008-10-21
For what it's worth, I jst did a pacman -Syu on my PR200, installed a new stock Arch64 kernel, and rebooted with it.

I believe it's 2.6.27.1-1 (so not *.2 ?).

Still in poll mode :)

EDIT: pm-suspend doesn't work though.

---

### Post by badbull on 2008-10-21
i think i'm sure now. the bad patch comes from here [http://bugzilla.kernel.org/show_bug.cgi?id=10724](http://bugzilla.kernel.org/show_bug.cgi?id=10724) (the patch [http://bugzilla.kernel.org/attachment.cgi?id=18044&action=edit](http://bugzilla.kernel.org/attachment.cgi?id=18044&action=edit))

this patch is applied to the ubuntu kernel but not to the vanilla kernel 2.6.27.2

launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/270017](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/270017)

---

### Post by jdb on 2008-10-21
> **badbull said:**
> i think i'm sure now. the bad patch comes from here [http://bugzilla.kernel.org/show_bug.cgi?id=10724](http://bugzilla.kernel.org/show_bug.cgi?id=10724) (the patch [http://bugzilla.kernel.org/attachment.cgi?id=18044&action=edit](http://bugzilla.kernel.org/attachment.cgi?id=18044&action=edit))

this patch is applied to the ubuntu kernel but not to the vanilla kernel 2.6.27.2

launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/270017](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/270017)

I looked at the launchpad bug and Timo Tretter posted two comments:

>I've got the problem the other way arround. I need the ACPI polling mode
>because my notebook (MSI-PR200/System 76 Daru2) send wrong battery status interrupts.
>The 2.6.27-7 does not enable the polling mode, 2.6.27-6 does.

>This is not fixed for me because the "fix" cause the old problem. On my
>laptop the EC driver needs to be started in poll mode to show the correct
>values for battery and ac adapter. The 2.6.27-7 kernel starts the driver
>in interrupt mode.

It's sounds like they fixed a problem is some other laptops but broke ours  :(

jdb

---

### Post by badbull on 2008-10-21
> **jdb said:**
> I looked at the launchpad bug and Timo Tretter posted two comments:

to clarify, these comments are mine.
i created a new bug in launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287093). maybe someone from ubuntu take a look at this problem.

---

### Post by gaussian on 2008-10-21
> **badbull said:**
> to clarify, these comments are mine.
i created a new bug in launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287093). maybe someone from ubuntu take a look at this problem.

I suggest that as many as possible subscribe to this bug to get it on to the radar screen of Ubuntu Devs.

---

### Post by williumbillium on 2008-10-21
> **gaussian said:**
> I suggest that as many as possible subscribe to this bug to get it on to the radar screen of Ubuntu Devs.

There is also [a somewhat new feature]("https://blueprints.launchpad.net/malone/+spec/malone-me-too") in launchpad so you can mark a bug as affecting you.  It's probably worth doing that too.   See the text directly below the title of the bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287093)

---

### Post by badbull on 2008-10-25
i've tested some vanilla kernel. 2.6.27.x works with ec in poll mode.
kernel 2.6.28-rc1 starts ec in interrupt mode, but the battery shows right values.

i think ubuntu will not change the kernel major version, so maybe they will fix the problem or we have to build our own kernel.

---

### Post by jdb on 2008-10-25
> **badbull said:**
> i've tested some vanilla kernel. 2.6.27.x works with ec in poll mode.
kernel 2.6.28-rc1 starts ec in interrupt mode, but the battery shows right values.

i think ubuntu will not change the kernel major version, so maybe they will fix the problem or we have to build our own kernel.

I'm running 2.6.27.2 & it puts it in the interrupt mode when it sees an interrupt but then switches to polling when it detects a storm:

ACPI: EC: Look up EC in DSDT
ACPI: EC: non-query interrupt received, switching to interrupt mode
ACPI: EC: GPE storm detected, disabling EC GPE
ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
ACPI: EC: driver started in poll mode

I think that Ubuntu removed the storm detection, I'm not sure why.

jdb

---

### Post by badbull on 2008-10-25
oh, i was wrong... 2.6.28-rc1 still starts in poll mode, just like 2.6.27.3.

---

### Post by badbull on 2008-10-27
the bad patch is committed to 2.6.28-rc2
it starts the driver in interrupt mode with the same problems like the ubuntu kernel.

---

### Post by jdb on 2008-10-28
> **badbull said:**
> the bad patch is committed to 2.6.28-rc2
it starts the driver in interrupt mode with the same problems like the ubuntu kernel.

Your right.

I just loaded 2.6.28-rc2 & this is the result:

23:57:32 ~ dmesg | grep "ACPI: EC:"
ACPI: EC: Look up EC in DSDT
ACPI: EC: non-query interrupt received, switching to interrupt mode
ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
ACPI: EC: driver started in interrupt mode

So far power is reporting correctly but I'm going to leave it on tonight & see what it looks like in the morning.

jdb

---

### Post by jdb on 2008-10-28
> **jdb said:**
> Your right.

I just loaded 2.6.28-rc2 & this is the result:

23:57:32 ~ dmesg | grep "ACPI: EC:"
ACPI: EC: Look up EC in DSDT
ACPI: EC: non-query interrupt received, switching to interrupt mode
ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
ACPI: EC: driver started in interrupt mode

So far power is reporting correctly but I'm going to leave it on tonight & see what it looks like in the morning.

jdb

It's morning & power reporting has gone bonkers.

The part of the patch for ec.c is 663 lines long & it's
not clear to me exactly which lines cause our problem.

I did find this snippet of code in a long if-else block in ec.c:
...
if (printk_ratelimit())
 pr_info(PREFIX "missing confirmations, " "switch off interrupt mode.\n");
 clear_bit(EC_FLAGS_GPE_MODE, &ec->flags);
...

I think I might insert the line:
clear_bit(EC_FLAGS_GPE_MODE, &ec->flags);

right after the if-else block & see what happens.

jdb

---

### Post by jdb on 2008-10-28
This is my patch:

```
diff -ur linux-2.6.28-rc2/drivers/acpi/ec.c linux-2.6.28-dads/drivers/acpi/ec.c
--- linux-2.6.28-rc2/drivers/acpi/ec.c	2008-10-27 20:52:59.000000000 -0400
+++ linux-2.6.28-dads/drivers/acpi/ec.c	2008-10-28 11:33:14.000000000 -0400
@@ -256,6 +256,7 @@
 	unsigned long tmp;
 	int ret = 0;
 	pr_debug(PREFIX "transaction start\n");
+	set_bit(EC_FLAGS_GPE_STORM, &ec->flags);
 	/* disable GPE during transaction if storm is detected */
 	if (test_bit(EC_FLAGS_GPE_STORM, &ec->flags)) {
 		clear_bit(EC_FLAGS_GPE_MODE, &ec->flags);


```

And this is the result:

13:20:02 ~ dmesg | grep "ACPI: EC: "
ACPI: EC: Look up EC in DSDT
ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
ACPI: EC: driver started in poll mode

jdb

---

### Post by gaussian on 2008-10-28
> **jdb said:**
> This is my patch:

```
diff -ur linux-2.6.28-rc2/drivers/acpi/ec.c linux-2.6.28-dads/drivers/acpi/ec.c
--- linux-2.6.28-rc2/drivers/acpi/ec.c	2008-10-27 20:52:59.000000000 -0400
+++ linux-2.6.28-dads/drivers/acpi/ec.c	2008-10-28 11:33:14.000000000 -0400
@@ -256,6 +256,7 @@
 	unsigned long tmp;
 	int ret = 0;
 	pr_debug(PREFIX "transaction start\n");
+	set_bit(EC_FLAGS_GPE_STORM, &ec->flags);
 	/* disable GPE during transaction if storm is detected */
 	if (test_bit(EC_FLAGS_GPE_STORM, &ec->flags)) {
 		clear_bit(EC_FLAGS_GPE_MODE, &ec->flags);


```

And this is the result:

13:20:02 ~ dmesg | grep "ACPI: EC: "
ACPI: EC: Look up EC in DSDT
ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
ACPI: EC: driver started in poll mode

jdb

jdb,

I have very little experience on building Kernel modules (the only exception is building wacom-modules for my Bamboo Fun drawing tablet). Is this something I could build without building the whole kernel and just replace the module (like I do with wacom) or is it something that requires compiling the whole kernel?

---

### Post by jdb on 2008-10-28
> **gaussian said:**
> jdb,

I have very little experience on building Kernel modules (the only exception is building wacom-modules for my Bamboo Fun drawing tablet). Is this something I could build without building the whole kernel and just replace the module (like I do with wacom) or is it something that requires compiling the whole kernel?

The kernel needs to be rebuilt but the modules don't.

This patch is against 2.6.28 which is only out there as a testing patch to 2.6.27.

I haven't looked, but I imagine the broken code in later versions of 2.6.27 looks about the same.

Here in a nut shell is a quick & dirty way to patch an Ubuntu kernel.

1) Use synaptic to install linux-source

2) Open a terminal in /usr/src/linux...

3) gedit Makefile
chnage the EXTRAVERSION as in the example below so it matches the end of the folder name in /lib/modules

	VERSION = 2
	PATCHLEVEL = 6
	SUBLEVEL = 24
	#EXTRAVERSION = .3
	EXTRAVERSION = -19-generic
	#the new files are named *-2.6.24-19-generic
	NAME = Err Metey! A Heury Beelge-a Ret!

3) make whatever changes desired in the source code, i.e., drivers/acpi/ec.c

3.5) (thanks to gaussian) make oldconfig

4) make bzImage

5) Go to the /boot directory.
Rename the kernel
If things go bad you can boot to another partition or a live cd, delete the new kernel you are about to install & rename the old kernel back again.
The kernel will have a name such as vmlinuz-2.6.24-19-generic

You could also make a new grub entry that would reload the old kernel using it's new name.

Don't worry about the initrd.img file, the original one will work fine, you don't need a new one to go with your new kernel.

6) Copy the new kernel to the boot directory as in the example below:
cp arch/x86/boot/bzImage /boot/vmlinuz-2.6.24-19-generic
Use the name of the original kernel you just renamed.

Since no modules have changed and you have modified the Makefile to make a kernel that matches the existing ones, you don't have to do anything with modules.
This is good because there are some custom ones installed that don't come with the kernel source.

If an update that supplies a new kernel comes along, you will have to apply the patch again.

jdb

---

### Post by gaussian on 2008-10-28
> **jdb said:**
> The kernel needs to be rebuilt but the modules don't.

This patch is against 2.6.28 which is only out there as a testing patch to 2.6.27.

I haven't looked, but I imagine the broken code in later versions of 2.6.27 looks about the same.

Here in a nut shell is a quick & dirty way to patch an Ubuntu kernel.

1) Use synaptic to install linux-source

2) Open a terminal in /usr/src/linux...

3) gedit Makefile
chnage the EXTRAVERSION as in the example below so it matches the end of the folder name in /lib/modules

	VERSION = 2
	PATCHLEVEL = 6
	SUBLEVEL = 24
	#EXTRAVERSION = .3
	EXTRAVERSION = -19-generic
	#the new files are named *-2.6.24-19-generic
	NAME = Err Metey! A Heury Beelge-a Ret!

3) make whatever changes desired in the source code, i.e., drivers/acpi/ec.c

4) make bzImage

5) Go to the /boot directory.
Rename the kernel
If things go bad you can boot to another partition or a live cd, delete the new kernel you are about to install & rename the old kernel back again.
The kernel will have a name such as vmlinuz-2.6.24-19-generic

You could also make a new grub entry that would reload the old kernel using it's new name.

Don't worry about the initrd.img file, the original one will work fine, you don't need a new one to go with your new kernel.

6) Copy the new kernel to the boot directory as in the example below:
cp arch/x86/boot/bzImage /boot/vmlinuz-2.6.24-19-generic
Use the name of the original kernel you just renamed.

Since no modules have changed and you have modified the Makefile to make a kernel that matches the existing ones, you don't have to do anything with modules.
This is good because there are some custom ones installed that don't come with the kernel source.

If an update that supplies a new kernel comes along, you will have to apply the patch again.

jdb


Great. I will try this tomorrow and report back if it helps with Intrepid 2.6.27 32-bit kernel.

---

### Post by gaussian on 2008-10-28
Unfortunately it seems that the patch does not work here. *Read on to end of post containing new information*

First very small addition to build instructions: I think one needs
```

make oldconfig

```
as 3.5)


I did apply the patch, I hope I did it correctly:
```

mymachine$ diff -ur /usr/src/linux-source-2.6.27/drivers/acpi/ec.c /usr/src/linux-source-2.6.27-own/drivers/acpi/ec.c
--- /usr/src/linux-source-2.6.27/drivers/acpi/ec.c	2008-10-24 01:35:21.000000000 -0500
+++ /usr/src/linux-source-2.6.27-own/drivers/acpi/ec.c	2008-10-28 20:08:55.000000000 -0500
@@ -259,6 +259,7 @@
 				     .irq_count = 0};
 	int ret = 0;
 	pr_debug(PREFIX "transaction start\n");
+	set_bit(EC_FLAGS_GPE_STORM, &ec->flags);
 	/* disable GPE during transaction if storm is detected */
 	if (test_bit(EC_FLAGS_GPE_STORM, &ec->flags)) {
 		clear_bit(EC_FLAGS_GPE_MODE, &ec->flags);


```

Unfortunately here is the results of dmesg:
```

mymachine$ dmesg | grep -i "acpi: ec"
[    0.765606] ACPI: EC: Look up EC in DSDT
[    0.896254] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.896254] ACPI: EC: driver started in poll mode
[   25.292033] ACPI: EC: non-query interrupt received, switching to interrupt mode

```

Am I correct to assume that the 25.292033 line here is bad news? This is using 2.6.27-generic under 32-bit. Also should I be passing any parameters to kernel? Currently my relevant menu.lst line is:
```

kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/ubuntu-root ro  

```


*New info: Maybe I misunderstood the patch. It now seems that after an hour of using the patched kernel my dmesg has 15 events "ACPI: EC: non-query interrupt received, switching to interrupt mode", but both the battery indicator and thermal sensor still behave sensibly. So there is hope, I'll report back tomorrow morning.*

---

### Post by badbull on 2008-10-29
maybe it's better to use this howto to compile a new kernel
[https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way)

this will create a new deb package

---

### Post by jdb on 2008-10-29
> **gaussian said:**
> Unfortunately it seems that the patch does not work here. *Read on to end of post containing new information*

First very small addition to build instructions: I think one needs
```

make oldconfig

```
as 3.5)


I did apply the patch, I hope I did it correctly:
```

mymachine$ diff -ur /usr/src/linux-source-2.6.27/drivers/acpi/ec.c /usr/src/linux-source-2.6.27-own/drivers/acpi/ec.c
--- /usr/src/linux-source-2.6.27/drivers/acpi/ec.c	2008-10-24 01:35:21.000000000 -0500
+++ /usr/src/linux-source-2.6.27-own/drivers/acpi/ec.c	2008-10-28 20:08:55.000000000 -0500
@@ -259,6 +259,7 @@
 				     .irq_count = 0};
 	int ret = 0;
 	pr_debug(PREFIX "transaction start\n");
+	set_bit(EC_FLAGS_GPE_STORM, &ec->flags);
 	/* disable GPE during transaction if storm is detected */
 	if (test_bit(EC_FLAGS_GPE_STORM, &ec->flags)) {
 		clear_bit(EC_FLAGS_GPE_MODE, &ec->flags);


```

Unfortunately here is the results of dmesg:
```

mymachine$ dmesg | grep -i "acpi: ec"
[    0.765606] ACPI: EC: Look up EC in DSDT
[    0.896254] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.896254] ACPI: EC: driver started in poll mode
[   25.292033] ACPI: EC: non-query interrupt received, switching to interrupt mode

```

Am I correct to assume that the 25.292033 line here is bad news? This is using 2.6.27-generic under 32-bit. Also should I be passing any parameters to kernel? Currently my relevant menu.lst line is:
```

kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/ubuntu-root ro  

```


*New info: Maybe I misunderstood the patch. It now seems that after an hour of using the patched kernel my dmesg has 15 events "ACPI: EC: non-query interrupt received, switching to interrupt mode", but both the battery indicator and thermal sensor still behave sensibly. So there is hope, I'll report back tomorrow morning.*

It looks like the patch went in OK & the kernel worked, the trouble is that the patch didn't do it's job.

I think the 25.202033 is 1/2 second intervals, so about 12 seconds after it started in the poll mode it received a non-query interrupt and went back in the interrupt mode.

Mine didn't do that, but I'm not running exactly the same kernel as you are.
Also, the patch wasn't all that well thought out, it was more of a cut & try effort.

I'm kind of busy on a few other things at the moment, but in a few days or so I think I'm going to look into this a little deeper.

With any luck maybe a real developer will take an interest :)

jdb

---

### Post by gaussian on 2008-10-29
jdb,


So far it seems to be working. Great work!

---

### Post by gaussian on 2008-10-29
> **jdb said:**
> It looks like the patch went in OK & the kernel worked, the trouble is that the patch didn't do it's job.

I think the 25.202033 is 1/2 second intervals, so about 12 seconds after it started in the poll mode it received a non-query interrupt and went back in the interrupt mode.

Mine didn't do that, but I'm not running exactly the same kernel as you are.
Also, the patch wasn't all that well thought out, it was more of a cut & try effort.

I'm kind of busy on a few other things at the moment, but in a few days or so I think I'm going to look into this a little deeper.

With any luck maybe a real developer will take an interest :)

jdb

I am happy to test anything, unfortunately I don't have the required knowledge to help with the coding (economics professor, not a kernel hacker). Anyhow, like I said in the post that I wrote exactly at the same time as your post quoted here, it seems that the patch might still be working. Even though dmesg reports switching to interrupt mode  both thermal monitors and battery indicator are still behaving after 10 hours of uptime. This would have not happened without the patch with the new kernel, so I'll keep my fingers crossed.

---

### Post by thomasaaron on 2008-10-29
We're testing Intrepid on the DarU2 today. 

I've added acpi=noirq as a kernel option. This seems to stop the flakey power management, but it is giving us a really slow response time. For example, if the ac adapter is unplugged, the applet will switch to battery power after about 20 seconds. 

Are you guys getting this as well?

---

### Post by gaussian on 2008-10-29
> **thomasaaron said:**
> We're testing Intrepid on the DarU2 today. 

I've added acpi=noirq as a kernel option. This seems to stop the flakey power management, but it is giving us a really slow response time. For example, if the ac adapter is unplugged, the applet will switch to battery power after about 20 seconds. 

Are you guys getting this as well?

Thomas,

I'll test this tonight with the patch (and without acpi=noirq). My DARU is at home.

---

### Post by gaussian on 2008-10-29
> **thomasaaron said:**
> We're testing Intrepid on the DarU2 today. 

I've added acpi=noirq as a kernel option. This seems to stop the flakey power management, but it is giving us a really slow response time. For example, if the ac adapter is unplugged, the applet will switch to battery power after about 20 seconds. 

Are you guys getting this as well?

With jdb's patch I am getting exactly same "slowness". So I guess it does the same thing as acpi=noirq, pretty much.

---

### Post by jdb on 2008-10-29
> **gaussian said:**
> With jdb's patch I am getting exactly same "slowness". So I guess it does the same thing as acpi=noirq, pretty much.

Has it been on all day?
Is power reporting still sane?

Just curious.

Do your Fn F3 & Fn F4 keys dim/undim the screen ?

Thanks,

jdb

---

### Post by gaussian on 2008-10-29
> **jdb said:**
> Has it been on all day?
Is power reporting still sane?

Just curious.

Do your Fn F3 & Fn F4 keys dim/undim the screen ?

Thanks,

jdb

Yes. It has been. And it is sane.

And I just realized that the "ACPI: EC switching to..." messages were generated by me using Fn F3 & Fn F4. And they work. So everything is absolutely perfect.

Thomas: Does acpi=noirq under regular Kernel disable dim/undim?

---

### Post by thomasaaron on 2008-10-29
> Thomas: Does acpi=noirq under regular Kernel disable dim/undim?

Yes, it does.

---

### Post by jdb on 2008-10-29
> **gaussian said:**
> Yes. It has been. And it is sane.

And I just realized that the "ACPI: EC switching to..." messages were generated by me using Fn F3 & Fn F4. And they work. So everything is absolutely perfect.

Thomas: Does acpi=noirq under regular Kernel disable dim/undim?

Thanks.

BTW, with a handle like gaussian I was guessing a math professor :)
It sure is an interesting time for your profession.

Be careful, applying patches & compiling kernels is the start of the slippery slope towards hacking, LOL.

jdb

---

### Post by gaussian on 2008-10-30
> **jdb said:**
> Thanks.

BTW, with a handle like gaussian I was guessing a math professor :)
It sure is an interesting time for your profession.

Be careful, applying patches & compiling kernels is the start of the slippery slope towards hacking, LOL.

jdb

This is off-topic, but I have been down that road many years ago: I did enjoy reading Kerningham & Ritchie, trying to learn Z80-assembler and play with VAX/VMS computers when I was much younger. And CP/M was pretty cool too. 

As for the name Gaussian, it comes from my Statistics background: Gaussian=Normal was a wordplay that I found amusing.

And now back to topic: so given my experience and Thomas' answer there seems to be a very small advantage for this patch over plain acpi=noirq option under intrepid: dim/undim keys work.

---

### Post by laserline on 2008-10-30
> **thomasaaron said:**
> We're testing Intrepid on the DarU2 today. 

I've added acpi=noirq as a kernel option. This seems to stop the flakey power management, but it is giving us a really slow response time. For example, if the ac adapter is unplugged, the applet will switch to battery power after about 20 seconds. 

Are you guys getting this as well?

Hi Tom,

Yes, I experience lag until the applet is updated when switching power sources.

Idan.

---

### Post by thomasaaron on 2008-10-30
OK, thank you.

---

### Post by ceminino on 2008-11-04
still no news of a permanent fix for the battery status? And especially for the standby!!?

---

### Post by Adriweb on 2008-11-04
Could we please get a developer's help with this? Lots of people seem to be having trouble with Ibex's power management. 

I have an HP 530 which, with Hardy, would sleep properly when I closed the lid. Ibex does not seem to respond at all to the lid closing. If i chose shutdown then Sleep, it will sleep but if I just close the lid, nothing happens. 

The power management applet is exhibiting problems too: sometimes it shows the options for AC power, Battery power and General. Sometimes only AC Power and General. Sometimes it shows the screen brightness slider on the AC power pane and sometimes not. 

I am not using a Beta Ibex version, I'm using the release.

---

### Post by thomasaaron on 2008-11-04
> I have an HP 530 

This forum is for the support of System76 computers. We have no HP computers to test with.

> which, with Hardy, would sleep properly when I closed the lid. 

Then your problem is not at all related to the one being discussed in this particular thread. So, the solution that comes for this particular computer probably won't impact your HP.

> Ibex does not seem to respond at all to the lid closing.

Make sure you're running the latest Intrepid. Not the beta or alpha versions. And make sure you're fully updated. Also, a fix for this probably will be coming down via an update soon.

> The power management applet is exhibiting problems too: sometimes it shows the options for AC power, Battery power and General. Sometimes only AC Power and General. Sometimes it shows the screen brightness slider on the AC power pane and sometimes not.

We've not encountered that problem on any System76 computers, so I'm not sure what it is. If you remove your battery, I don't think it will show the battery tab. But if you have ac and battery connected and it doesn't show all the tabs, you have some sort of acpi or hardware detection issue. Try adding "acpi=noirq" as a kernel option in /boot/grub/menu.lst.
That worked for the DarU2, but then your problem is not one I've seen on the DarU2.

---

### Post by walkeraj on 2008-11-14
Okay, I'm just now jumping into this thread, and I've given the last few pages a quick review.  So, let me see if I have it right: 

Power management is working perfectly in Intrepid, but requires a kernel patch, or does it still require the insidious acpi=noirq?

---

### Post by thomasaaron on 2008-11-14
Still requires acpi=noirq

With that kernel option, we've found batter/ac detection is slower than it used to be. However, it works.

Suspend still does not work.

---

### Post by val67 on 2008-11-14
> **thomasaaron said:**
> Still requires acpi=noirq

With that kernel option, we've found batter/ac detection is slower than it used to be. However, it works.

Suspend still does not work.

Hi,

So what is the next step to fix this 6 months old problem?

Val.

---

### Post by jdb on 2008-11-14
> **val67 said:**
> Hi,

So what is the next step to fix this 6 months old problem?

Val.

I don't think anything short of a change in the kernel is going to fix it.

That would have to come from Ubuntu, going to kernel.org probably wouldn't help.
They accepted the change from Ubuntu that broke it in the first place.

A few of us have posted here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287093)

Adding your name to the list couldn't hurt.

jdb

---

### Post by val67 on 2008-11-14
> **jdb said:**
> I don't think anything short of a change in the kernel is going to fix it.

That would have to come from Ubuntu, going to kernel.org probably wouldn't help.
They accepted the change from Ubuntu that broke it in the first place.

A few of us have posted here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287093)

Adding your name to the list couldn't hurt.

jdb

Thanks jdb,

Sorry if I sound frustrated, but it is really annoying to see that something used to work, then it got broken, and now nobody is fixing it after so much time !!!

---

### Post by jdb on 2008-11-14
> **val67 said:**
> Thanks jdb,

Sorry if I sound frustrated, but it is really annoying to see that something used to work, then it got broken, and now nobody is fixing it after so much time !!!

I know the feeling :(

jdb

---

### Post by walkeraj on 2008-11-14
> **jdb said:**
> I know the feeling :(

jdb

We *all* know the feeling, and I'm going to be honest and say that this whole debacle has lowered my faith in both the company and the community a little.

Sure, the support is stellar (and Tom really should get like 30 medals), but that's only half the story.  You'd think that, after this much time, someone would have made *some* progress, but as near as I can tell the System76 R&D team either doesn't exist, or is more concerned with finding the next new thing or fixing problems on other models.  Seriously, has *anyone* from System76 other than Tom chimed in on this?  Because, I've not seen it.

You could say I'm not being fair to System 76 in this assessment, and perhaps I'm not.  Perhaps the R&D team doesn't employ anyone experienced in kernel development.  Even still, shouldn't the "research" part of "research and development" have seen that HDMI and suspend didn't work and that power management was flakey?  

Even looking past that, you'd think that a company-OEM relationship could have gotten some cooperation from the OEM in information that could have helped SOMEONE write a patch to this problem.  We bought these things with the understanding that they would work as laptops, after all, and what good is a laptop without suspend or power management?  I guess this is why the Darter3 isn't MSI.

Someone will probably come back at me and tell me to write a patch for it myself.  Had someone said that when this problem started, I would have come back and said I didn't know the kernel that well and would need 6 months to a year to get up to speed, and would have laughed, thinking that someone would probably fix it three times over in that time period, but this is where the kernel team starts to look not-so-good.  How long have these bugs been open?  I know, it's entirely volunteer, and I appreciate that.  I work with and contribute to open source, too, but... didn't a kernel developer get a loaner unit to develop on?  What happened with that?

It would all be terribly frustrating if it hadn't been like this for so long.  As it is, it just kind of :(

---

### Post by ceminino on 2008-11-14
The worst is that when you buy a laptop is basically for two years, and if it isn't fixed after one year you're really fu**ed! I don't blame System 76 about the problem, since it's a kernel problem, I'm just annoyed that they recommend a laptop which has those problem as a start.

---

### Post by val67 on 2008-11-14
> **ceminino said:**
> The worst is that when you buy a laptop is basically for two years, and if it isn't fixed after one year you're really fu**ed! I don't blame System 76 about the problem, since it's a kernel problem, I'm just annoyed that they recommend a laptop which has those problem as a start.

Definitely it's System 76 fault here because they haven't tested Daru2 properly.

Here is a bigger problem, in my opinion:

With this rush to keep up with the 6 month release of Ubuntu, I am afraid that there is not enough time to sort out the outstanding bugs before moving to the next release.

To me it seemed that S76 has waited hoping that Ibex would "magically" solve the problem, which didn't happen.

Instead, S76 should have kept Hardy (LTS) and make it rock solid !

System76 should have supported Hardy LTS

---

### Post by jdb on 2008-11-14
I'm not so sure 76 is the one to blame.

It worked great with ec_intr=0, then the kernel changed.

It's not hard to patch the kernel to make it work but 76 would have a hard time deploying a kernel patch.

It would get blown away every time Ubuntu pushed new kernel code & they do that all the time.

I don't use Ubuntu anymore, I use Archlinux but it has the same problem.

I just don't load every new kernel update that's available & when I do load one, I patch it.

jdb

---

### Post by walkeraj on 2008-11-15
> **jdb said:**
> I'm not so sure 76 is the one to blame.


Yeah, it's just hard to know what to think when there was never a time when it worked completely.  The day I got it, I think it was hibernate that was broken, but I was cool with that, I could still suspend, and hibernate support was coming.  Soon enough, hibernate worked, which was useful, but suspend didn't and power management was broken... and it's remained that way.

>  It worked great with ec_intr=0, then the kernel changed.

It's not hard to patch the kernel to make it work

From what I was reading, it's still slow to respond to power events, and I remember when it was like that before and it was still kind of broken.

> 
but 76 would have a hard time deploying a kernel patch.

It would get blown away every time Ubuntu pushed new kernel code & they do that all the time.


True enough, so why can't we get a kernel level fix in place?  How long has this been a known issue?  It's quite frustrating.

I don't load every new kernel that comes down the pipe either and I'm certainly no stranger to patching my own, but I mean... I could have done that on another system for less money.

I work with open source a lot, and I'm a very big advocate of it, especially such a well-known and shining example as Ubuntu.  Indeed, just the other day my friend's laptop with Vista on it decided to randomly delete a few essential system files and she didn't have a recovery disk, so I installed Ubuntu on it for her and it works perfectly, which felt kind of ironic.

---

### Post by ceminino on 2008-11-15
> **jdb said:**
> I'm not so sure 76 is the one to blame.

It worked great with ec_intr=0, then the kernel changed.



It never worked great, we never had standby working. I'm ashamed to say it but because of that I use windows at home, and linux just for work.

---

### Post by jdb on 2008-11-15
> **ceminino said:**
> It never worked great, we never had standby working. I'm ashamed to say it but because of that I use windows at home, and linux just for work.

I agree on the hibernate/suspend never working right.

76 should have checked the hardware out better before using it.

jdb

---

### Post by gaussian on 2008-11-15
> **jdb said:**
> I agree on the hibernate/suspend never working right.

76 should have checked the hardware out better before using it.

jdb


If my memory serves me correctly everything works almost perfectly with 64-bit Gutsy. The two caveats:

1) I think hibernate needs s2disk (uswsusp)
2) Using suspend will make computer hang on power down just when it is supposed to power down

I have to admit that I was little disappointed when I got my Daru with 32-bit Feisty and real suspend did not work (standby did). However for my personal use in the end really does not matter, Daru2 is my desktop replacement at home. My laptop nowadays is a Asus EEE 1000: in the end I decided Daru is too heavy to be hauled around. Can you tell I like light computers? I never understood people with 14 or 17 inch laptops. But then again, I don't play games, do video-editing or anything like that.

As a summary: Tom's support on things that matter have been so great that regardless of this I will probably buy my next computer from System 76.

---

### Post by jdb on 2008-11-15
> **gaussian said:**
> 
As a summary: Tom's support on things that matter have been so great that regardless of this I will probably buy my next computer from System 76.

I agree with what you say.

For me the Daru2 is great, if I'm not using it I just power down.
I like a clean boot once in a while anyway, with Archlinux & fluxbox it only takes about 40 seconds from power button to desktop.

But ..., I do understand that suspend is important to some laptop users.

jdb

---

### Post by williumbillium on 2008-11-15
:(

---

### Post by bkloppenborg on 2008-11-16
Although it was posted above, this bug has the following ticket:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/147560]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/147560")

A kernel patch was applied that worked fine up to 2.6.27-6 but was broken by another kernel patch in 2.6.27-7.

---

### Post by jdb on 2008-12-25
I just upgraded to 2.6.27-10 in Archlinux and acpi=noirq no longer fixes the power management problem.
Ibex is currently on 2.6.27-9 so this is something to look out for on the next kernel upgrade.

jdb

---

### Post by ceminino on 2008-12-30
> **jdb said:**
> I've never had my daru2 shut down but I do see the high 80s when I compile a kernel or make a coding mistake & get it stuck in a loop.
I've probably been a few degree's away from it.
When I run sensors to check the temp it says the critical temp is 100.

jdb

sorry to bring back this long forgotten issue of the heating, but I thought I'd just drop a line since I understood what was the problem. Actually it's just dust stuck around the fan... blowing a bit air inside is enough...
I'm testing a parallel job on both cores for 1 hour and the temperature is just 83 degrees... simple solutions to simple problems :)

---

### Post by pavel_987 on 2009-01-15
So is it safe to say that suspend will never get fixed? Or probably on the date we decided to get a new laptop. :(

On the bright side I'm trying to 2.6.29-rc1 from git, and it looks like they fixed the power management regression in recent kernels. But I may be speaking too soon.

---

### Post by val67 on 2009-01-15
i am still stupefied that the s76 R&D team could not have found a fix for this in more than 6 months, and include it in the s76 driver.

---

### Post by walkeraj on 2009-01-15
> **val67 said:**
> i am still stupefied that the s76 R&D team could not have found a fix for this in more than 6 months, and include it in the s76 driver.

This model has been the black sheep for awhile now.  Even System76 has gone with a different OEM for the Daru3 because of all the problems.

I pretty much gave up awhile back, put Windows on the Daru2 using the included driver disk and sold it on Craigslist.  I  Now I have a Thinkpad that hibernates and suspends and am finally happy with a Linux laptop.

---

### Post by gbuntu55 on 2009-01-15
I'll admit it. As a daru2 user for a little over a year now, I probably would not have gone this route if I'd known all the hacks I'd be having to do to keep some semblance of a useful system/laptop going. Along with a buggy Gnome install and problems with python scripts after the upgrade from Feisty to Gutsy and the power management problem, I have twice had to conduct major surgery on my laptop LCD screen to fix a broken/worn cable connection that runs tightly through the left hinge.

A few months ago I did a clean install of Kbuntu (Hardy) and decided *not* to use the System76 drivers. Since then I have had fewer problems but maybe I'm just getting used to the occasionally flaky nature of the system and the Ubuntu distro.

One particularly annoying problem that crops up at random every few weeks is the complete inability to properly shut down the system. This usually starts with a few icons disappearing from the menus (I'll go to shut down and notice that some of the logout/suspend icons are just missing). This is when I know I'm in trouble.

I try to shutdown and the system will go to a terminal with a login prompt. When I try to login, it just stalls for a moment and then the login prompt appears again. From this point there is no easy way to issue any commands (I have even tried ssh'ing to the laptop from another PC to no avail). ATL-ALT-DEL doesn't work and shutting down through the power button ends up scrambling the disk and then I have to run fsck and cross my fingers!

I can't count how many times I've come back from one of these problems with all my desktop reset and strange behavior from some apps until files are cleaned up.

A few weeks ago I found that using alt-sysrq S, U, B, or may just B is 
one way to reboot when in this situation. More info here:
[http://www.linuxhowtos.org/Tips%20and%20Tricks/sysrq.htm](http://www.linuxhowtos.org/Tips%20and%20Tricks/sysrq.htm)

Has anyone else encountered these issues?

Oh, one last thing about daru2. Some of the keys are beginning to get a little shall we say, "shaky". The down arrow key feels like it might give out any day now. Also, the left mouse button stopped clicking a long time a go. It still works but it's pretty "spongey".

Sorry to ramble on and take this somewhat off topic but that's my experience with the daru2 from System76. I'm thinking new laptop this year. Question is, is it time for a Mac?

---

### Post by val67 on 2009-01-16
> **gbuntu55 said:**
> Sorry to ramble on and take this somewhat off topic but that's my experience with the daru2 from System76. I'm thinking new laptop this year. Question is, is it time for a Mac?

I am leaning towards Mac as well. I think it's wrong to be forced to upgrad e every 6 months your OS to a new Ubuntu version that proves to need some other months to iron out the major bugs. By the time one finally (after months) has a functional desktop, a new Ubuntu version comes out which breaks many things.

I had hoped that the S76 driver could solve this problems, but unfortunately  this is not the case.

---

### Post by val67 on 2009-01-16
> **walkeraj said:**
>   Now I have a Thinkpad that hibernates and suspends and am finally happy with a Linux laptop.

Can you please share the specs of your Thinkpad?

Thx,

---

### Post by jdb on 2009-01-16
> **val67 said:**
> I am leaning towards Mac as well. I think it's wrong to be forced to upgrad e every 6 months your OS to a new Ubuntu version that proves to need some other months to iron out the major bugs. By the time one finally (after months) has a functional desktop, a new Ubuntu version comes out which breaks many things.

I had hoped that the S76 driver could solve this problems, but unfortunately  this is not the case.

Ubuntu is not the only linux distro out there.

Also, you don't have to upgrade Ubuntu every 6 months.
Hardy Heron, Ubuntu 8.04 LTS Desktop Edition, is supported for 3 years.
The LTS stands for Long Term Support.

After three years all the major bugs will be gone & it should work fine for another year or so after that.
By then the next LTS should be pretty well bug free.

jdb

---

### Post by val67 on 2009-01-16
> **jdb said:**
> Ubuntu is not the only linux distro out there.

Also, you don't have to upgrade Ubuntu every 6 months.
Hardy Heron, Ubuntu 8.04 LTS Desktop Edition, is supported for 3 years.
The LTS stands for Long Term Support.

After three years all the major bugs will be gone & it should work fine for another year or so after that.
By then the next LTS should be pretty well bug free.

jdb

I know about the LTS releases. Problem is that if I buy a S76 laptop today, it does not come with a LTS installed. So I would have to do it all manually ... and w/out the help of the s76 driver

---

### Post by jdb on 2009-01-16
> **val67 said:**
> I know about the LTS releases. Problem is that if I buy a S76 laptop today, it does not come with a LTS installed. So I would have to do it all manually ... and w/out the help of the s76 driver

The 76 drivers work just fine in Hardy.

jdb

---

### Post by val67 on 2009-01-16
> **jdb said:**
> The 76 drivers work just fine in Hardy.

jdb

Does it fix the Daru2 suspend/resume issue?

---

### Post by val67 on 2009-01-16
> **jdb said:**
> The 76 drivers work just fine in Hardy.

jdb

Ok, if I buy today a a76 laptop, it will come with ibex.

Assuming I have to manually reinstall hardy LTS, how can I then install the s67 driver?

---

### Post by jdb on 2009-01-16
> **val67 said:**
> Ok, if I buy today a a76 laptop, it will come with ibex.

Assuming I have to manually reinstall hardy LTS, how can I then install the s67 driver?

```
sudo echo 'deb http://planet76.com/repositories/ ./' > /etc/apt/sources.list.d/system76.list
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install system76-driver

```

run system76-driver and select "Install Drivers" -> "Install"

The 76 drivers won't do anything for Daru2 power management.

jdb

---

### Post by val67 on 2009-01-16
Thanks, jdb. It's good to know that Hardy is still supported, even though not installed by default.

---

### Post by gbuntu55 on 2009-01-17
> 

The 76 drivers won't do anything for Daru2 power management.

jdb

What exactly do the s76 drivers do then? Like I said I've not used the s76 drivers since a clean install of Kubuntu Hardy LTS and I'm using kernel version 2.6.24-23-generic after a recent package upgrade. I don't use hibernate/suspend b/c of past issues but I don't seem to be having any problems with going from AC to battery power like we used to see with the screen brightness/apci issues.

So, what would the sys76 drivers do for my daru2 in its current config?

---

### Post by williumbillium on 2009-01-17
> **gbuntu55 said:**
> What exactly do the s76 drivers do then? Like I said I've not used the s76 drivers since a clean install of Kubuntu Hardy LTS and I'm using kernel version 2.6.24-23-generic after a recent package upgrade. I don't use hibernate/suspend b/c of past issues but I don't seem to be having any problems with going from AC to battery power like we used to see with the screen brightness/apci issues.

So, what would the sys76 drivers do for my daru2 in its current config?

According to the [System76 driver page in the wiki]("http://knowledge76.com/index.php/System76_Driver"), in Hardy on the Daru2, support for the following items is added:

Restore, Sound, Wireless LED

The workaround for power management has to be added manually AFAIK.

---

### Post by williumbillium on 2009-01-17
> **jdb said:**
> Also, you don't have to upgrade Ubuntu every 6 months.
Hardy Heron, Ubuntu 8.04 LTS Desktop Edition, is supported for 3 years.
The LTS stands for Long Term Support.

After three years all the major bugs will be gone & it should work fine for another year or so after that.
By then the next LTS should be pretty well bug free.

The problem is that the latest release to fully work on the Daru2 is Gutsy which will no longer be supported in 3 months time.  So I am effectively, a year after purchasing my computer, being forced to "upgrade" to a release that has worse support for it.  If I don't upgrade, I no longer receive security updates which is not an option.  Of course, I don't really blame Ubuntu for this, but it is the situation I am facing none the less.

Also, the LTS releases are supported for 3 years.  It is my understanding that, after that time period, they no longer receive security updates so I wouldn't recommend continuing to use them after that time.  Can someone confirm that is the case?

---

### Post by gbuntu55 on 2009-01-17
> According to the System76 driver page in the wiki, in Hardy on the Daru2, support for the following items is added:

Restore, Sound, Wireless LED

The workaround for power management has to be added manually AFAIK.

That's what so strange. I don't seem to have any sound or wireless LED problems and I'm not using the the driver. 

If it ain't broke...I don't see why I should install the s76 driver?

---

### Post by jdb on 2009-01-17
> **gbuntu55 said:**
> That's what so strange. I don't seem to have any sound or wireless LED problems and I'm not using the the driver. 

If it ain't broke...I don't see why I should install the s76 driver?

The main thing it fixes is the internal & external microphones.
With the latest Ubuntu they might not need fixing anymore.
I think I remember them working without the driver but they might have been low on gain.

I'm on the latest kernel in Archlinux right now & they don't work at all with it.
I need to take a look at the 76 driver & see what the fix is.

jdb

---

### Post by walkeraj on 2009-01-17
From what I've seen, the System 76 "drivers" are not actually drivers, per se, but rather a series of python scripts that detect and apply certain platform-specific fixes.  A lot of the time, certain machines, especially laptops, require a bit of fiddling to get certain things like hotkeys and microphones and embedded webcams to work.  Sometimes you might need to insert a module or change the hotkey masking or have certain troublesome services disabled at suspend time or something like that when the autodetection doesn't quite do it for you.

Gradually, whatever failings keep hardware from "just working" are fixed, and tweaks aren't necessary anymore, which is almost certainly why later distributions don't have some problems, and don't require the "Drivers".

---

