---
title: "Suspend doesn't work proppely - 8.04, Darter Ultra (daru2)"
date: 2008-04-24
forum: System76 Support
---

### Post by laserline on 2008-04-24
Hello,

I would like to report that Suspend doesn't work propperly in the Ubuntu 8.04 (stable).

I've installed both versions, 32BIT first, then 64BIT and I have the same results.

The installation procedure on both was to wipe my drive (not upgrading from Gutsy 7.10), then I added System76 Repos and installed the latest driver (2.18), then I started the System76 application. Went to "Install Driver" --> "Install". Then, I rebooted.
I didn't choose "Restore System" because I already put the repositores manually.

When I suspend the system, all is good, the power button and indicator led blink. I tried waking the system by pressing P1, P2 buttons, the WIFI/BT button, move the mouse, press all keys on the keyboard, the cdrom eject button - nothing worked.

When I press the power button, the system tries to resume, it looks OK for a second, but then while the screen is still blank, the system Shuts Down (un-cleanly I might add) -- As I said before, this happens on 32BIT and 64BIT of Ubuntu Hardy 8.04 (Stable).

Is there something to do with this ?
Hibernation works OK.

Thanks in advance,
Idan Mashaal

---

### Post by laserline on 2008-04-24
UPDATE:
I've upgraded System76 driver to 2.20 and did a full Restore and reboot - that didn't help.
Instead it installed GnuCash, so I started reading the source to see what it does, and something is weird. 
I traced all the things that are supposed to be going on in Ubuntu 8.04 with 'daru2' and for some reason, I don't see any ACPI fixes (although the batter works after installing the driver. (driverscontrol.py line 78 sound.alsa4() )

I also found out that it adds sources, installs GnuCash (and docs), overwrites the driver and GSynaptics.
About GSynaptics, it doesn't fix the SHMConfig "true" in xorg.conf (so why install it?) -- lines 80-82 in base_system.py

In adition to all that, I can't find a thing about ACPI with the daru2...

Is the driver really ready for Ubuntu 8.04 ?

Thanks,
Idan

---

### Post by AusIV4 on 2008-04-24
I suspect the driver will get this fixed fairly soon, but in the mean time, can you show us your /etc/default/acip-support file?

---

### Post by laserline on 2008-04-24
Sure, the files is attached.

I just noticed that the battery monitor got screwed also (I even rebooted)

Idan.

---

### Post by reh4c on 2008-04-24
I still have the same battery indicator problem (wacky readings) with 8.04 64-bit.  There's a bug open on launchpad, just search for PR200 (same OEM laptop as Daru2/MSI-1221).  Needless to say, suspend doesn't work on mine either...same problem as you.  The only other issue that I've confirmed is with Cheese and the webcam.  Cheese now functions very poorly (i.e. freezing, video in window lags when dragging, etc.)  Please let us know if you're having the same problems with that as well.

---

### Post by laserline on 2008-04-25
Hi, just installed Cheese from Ubuntu's repos, and I'm experienceing the same issues as you. Slow FPS, video lagging when dragging.

Taking a picture works.
Shooting a video, makes the app stall and stop responing when pressing "Stop Recording"

The system-76 driver assumes the stock Ubuntu one is ok, but I guess it needs some tweaking.

I really do hope they will be able to fix/resolve issues with Hardy and Daru2. ( I'm kinda disappointed :confused: )

Thanks,
Idan.

---

### Post by AusIV4 on 2008-04-26
Line 10 of your acpi-support file reads:
```
ACPI_SLEEP_MODE=mem
```
Try setting it to:
```
ACPI_SLEEP_MODE=standby
```

---

### Post by laserline on 2008-04-26
I'll try that and post later on.

Isn't that something the driver should handle (or a custom modification) ?
I guess it's not specific to my machine only but to all daru2's out  there, as I did a clean installation.

Thanks,
Idan

---

### Post by laserline on 2008-04-26
Hi AusIV4,

I've made the change, rebooted and afterwards tried to suspend my daru2.
The system went to suspend mode (power button and the power led blinking) but waking up, from the power button (the only one that got the system to respond) caused the system to wake up but shutdown - uncleanly.

What log holds these events, maybe the answer is there ??

Thanks,
Idan.

---

### Post by laserline on 2008-04-26
Hello again,

I've found something quite disturbing...Something I overlooked before.
The findings I've found are the same with i.e, ACPI_SLEEP_MODE=mem and ACPI_SLEEP_MODE=standby    (I've reverted back to the defaults "mem")

Here goes:

When I try to wake my daru2 (by pressing the power button) it looks alive and after a few seconds shutdown (screen is blank), then I've waited for another 3-4 seconds and the system came back ON (by itself -- the power button and power led were OFF!) all the leds were up and running, fans whistling, HD working, Screen Blank. I've waited something like 30 seconds and there was no response except from the fans working (hard), I tried pressing all the buttons I can find, nothing worked. I pressed the power button, and it ignored me. I pushed and hold the power button for 10 seconds and nothing happend. Then I felt HOT air from my fan (HOT as in the system is doing something, but there was no sign).
I've finally shut it down by taking the battery out :( :(

I had a dual-boot with XP on the system and I never had something like this, I frankly use suspend really often.

I might add that the battery readings are way off... and  the battery seems to get lost from the graph. Even when charging, and I know that after 2 hours the battery led should turn off, when Ubuntu 8.04 is running, the battery never gets off, and every charge cycle the Power Manager's graph shows a new cycle (I hope it's not hosing my battery).

Any ideas what can be causing this ??

Thanks,
Idan.

---

### Post by badbull on 2008-04-27
i have the same suspend problems in hardy as i had in gutsy. the suspend to ram don't work.
in gutsy i changed the ACPI_SLEEP_MODE to standby and it worked (but not with blinking lights)
but i think this don't work in hardy. i changed the option but it goes on memory sleep and crash on wakeup, like you described above.

---

### Post by tuebinger on 2008-04-29
I'm having the same problems with the suspend feature.  I hope it gets fixed soon, as I'm having to shut down every time I use the computer.  And I was just beginning to enjoy the suspend feature working properly under 7.10!:(

---

### Post by thomasaaron on 2008-04-29
We *think* we've got the answer, and it involves rolling a custom kernel.
It will be a few days, but we are hard at work on it.

---

### Post by maartenlameris on 2008-05-16
Is there any progress in the fix for this problem?
Or a alpha version we can test?

---

### Post by thomasaaron on 2008-05-16
Not quite yet. R&D is still working on it. It's a tough one.

---

### Post by laserline on 2008-05-18
Can't we just diff both stable ubuntu kernels and see what has changed and why...

Not talking about diff the whole source, but the appropriate modules/drivers..

Idan.

---

### Post by thomasaaron on 2008-05-19
That behavior is typical.

Right now, suspend (S1 and S3) only work in 64-bit Gutsy. They are defunct in Hardy because of a regression of some type in the Kernel, which we are still trying to locate and fix. (Hibernate does work fine in Hardy, though.)

If you really need suspend, you will have to revert to Gutsy 64-bit and install/run the System76 driver (which will fix the battery monitor problem as well).

If you do not want to revert to Gutsy 64-bit, but you do want the battery monitor fixed, you will need to add...

acpi=noirq

...as a kernel option in your /boot/grub/menu.lst. This will mess up your brightness function keys, though. But it's the best fix we have at the moment.

---

### Post by Cogito² on 2008-05-30
Just to clarify, is hibernate working (in general)? Because it doesn't work on my laptop (Compaq V2000). It stops in the middle of booting up and nothing happens. Suspend also doesn't work, but as I've gathered I shouldn't expect it to...

---

### Post by greg_g on 2008-05-31
Cogito, just so you know, this thread is about a specific laptop, namely the System76 Darter Ultra.  If your laptop (a Compaq) is not performing suspend and/or hibernate correctly, it would be best to search [http://www.launchpad.net](http://www.launchpad.net) for issues about it, or check this link for more information/hints/tips: [https://wiki.ubuntu.com/LaptopTestingTeam/Compaq](https://wiki.ubuntu.com/LaptopTestingTeam/Compaq)

But to answer your question, there are many laptops that do perform suspend and hibernate flawlessly.  The main factor is if your laptop manufacturer uses components that are not made by companies which hate supporting anything but Windows. </mini_rant>

Best,

Greg

---

### Post by Cogito² on 2008-05-31
> **greg_g said:**
> Cogito, just so you know, this thread is about a specific laptop, namely the System76 Darter Ultra.  If your laptop (a Compaq) is not performing suspend and/or hibernate correctly, it would be best to search [http://www.launchpad.net](http://www.launchpad.net) for issues about it, or check this link for more information/hints/tips: [https://wiki.ubuntu.com/LaptopTestingTeam/Compaq](https://wiki.ubuntu.com/LaptopTestingTeam/Compaq)

But to answer your question, there are many laptops that do perform suspend and hibernate flawlessly.  The main factor is if your laptop manufacturer uses components that are not made by companies which hate supporting anything but Windows. </mini_rant>

Best,

Greg

Haha well that explains what "Darter Ultra" means...I wasn't quite sure and upon my scan of this thread I didn't quite figure it out (nor realize it was of importance). I'll look into those links. Thanks for the info.

---

### Post by digitalbenji on 2008-05-31
I have a Darter 1 (white darter).  Out of the box, 32 bit Hardy suspend and hibernate worked fine.  The last Kernel update (-17) nerfed both suspend and hibernate for me.  It looks like someone submitted a bug on this, [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/236272](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/236272)

For now, I will be using the -16 kernel.  What version are you having your problem with?  You can determine this by typing ```
uname -a
```

Thanks,

---

### Post by thomasaaron on 2008-06-02
Actually, this post is not for the white Darter (daru1), it is for the newer Darter (DarU2). The source of the problems are radically different.

With the white Darter is probably just a configuration issue. We can do some testing on it.

---

### Post by laserline on 2008-06-02
Hi Tom,

Where are we standing in the development of the fix ?

Idan.

---

### Post by walkeraj on 2008-06-11
I have tried everything at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279) and I have had no luck with this problem.  I have also installed the 2.6.24-19-image package from hardy-proposed.  That also did not work.

The inability to suspend is very frustrating and, frankly, compromises the usability of the notebook somewhat.  I'd be very interested to know the status on this problem too.

I was informed at one point that a notebook had been sent to a kernel developer (which is a really good idea).  Did anything come of that?

---

### Post by thomasaaron on 2008-06-11
It is still with the developer. They're continuing to work on it. We're not giving up on it.

---

### Post by MarkID on 2008-06-11
Hmmm.  A few days ago I tried suspend on my Daru1 and lo and behold, suspend started to work, where it hadn't after the Hardy upgrade.  I can even get my wifi back after coming out or suspend.  Maybe it was one of the system updates, or maybe it's just magic.  (Also, the dimming problem seems to have solved itself.)

---

### Post by thomasaaron on 2008-06-11
Right. But this thread pertains to the DarU2. It is a completely different set of issues.

---

### Post by maartenlameris on 2008-06-18
Is there any progress made on this issue I would like to upgrade to 8.04 but need my suspend to work.

If needed i'm happy to do some testing in this matter.

---

### Post by arch_o_median on 2008-06-22
Hi there!   I'm running a gazelle performance gazp3.   I also haven't been able to suspend/hibernate since I upgraded to Hardy 8.04.  I was able to suspend/hibernate in gutsy 7.10.
  When I hibernate via the keyboard Fn->F1 key combination the screen blanks, the disc light blinks and then the system goes completely off as desired.  When I try to reactivate it, the screen never displays anything, the fan comes on and runs until I hold down the power button.

---

### Post by arch_o_median on 2008-06-22
My system info is my sig.

---

### Post by thomasaaron on 2008-06-23
Please post that in a separate thread.

Suspend/Hibernate issues are a little different for each of these models. This thread was dedicated to the DarU2, and the fix will not be anything similar to the GazV3.

Also, let us know what processor you are using so we can set up tests in-house.

---

### Post by walkeraj on 2008-06-24
Is there any kind of blog or something we can go to to see the status on this as it develops?  While I'm sure the work is ongoing, it would definitely help to know how it's developing so we don't all keep poking our heads in here asking for a timetable.

As a developer, I have learned that a major premise of good UI is some kind of visual indicator of activity, even if it just says "reticulating splines" or somesuch nonsense.  You know?

---

### Post by thomasaaron on 2008-06-25
I'm going to talk to Carl about starting an email list or something so that we can provide updates to interested folks.

---

### Post by walkeraj on 2008-06-25
Sweet.  I'll friggin' make the whole company fresh gingerbread if you can fix this in the next two months.

---

### Post by damphoud on 2008-07-03
Have you guys been able to figure it out? I have a 1221 as well, and I'm unable to suspend. I don't expect any trouble shooting, as my laptop is not system76.

---

### Post by maartenlameris on 2008-07-14
Is there any progress on this problem?

---

### Post by Nuno Bettencourt on 2008-07-16
Hi, even though i don't own a Darter Ultra, i have a Tsunami Traveller 1275R which is also a rebrand of the MSI-PR200 and I'm having all the difficulties described above running Hardy 64bits kernel 2.6.24-19.

My resume after suspend wakes up the computer and after 2-3 seconds shuts it down. After 3-5 seconds  wakes it up again, can ear fans, hdd, see lights coming up, but the screen is blank.

My hibernate mode seems to do it's job.

My battery readings, after enabling acpi=noirq also works, but as said, brightness controls FN+F4 and FN+F5 stopped working. Regarding this, a few days ago i had a Fedora 9 live cd which i tested only for a couple of minutes, and i don't think the problem with AC and battery ocurred. I'll try to post some more info about this.

---

### Post by gaussian on 2008-07-16
I have Darter 2 and I haven't updated to Hardy mostly because of the suspend problems mentioned in this thread. This is going to be slightly off topic, but I went and downloaded "Daily Live CD" images for next version (8.10). Note that this is not even yet in the Alpha stage (or more precisely in the current alpha releases there are no live-CD's).

Some good news: using yesterdays (7/15) daily live-CD's under both 32-bit and 64-bit one of the suspend modes worked perfectly. This means that
$sudo -s
$echo "standby" >/sys/power/state
resulted computer being frozen up like it should be and then returning after hitting the power button. This is the light sleep mode (no blinking lights).

Then the bad news: 
$sudo -s
$echo "mem" >/sys/power/state
resulted computer going to "deep sleep" properly, but not returning from there like it seems to do under hardy. 

It looks like I am going to stick to Gutsy until 8.10 comes out.

P.S. 64-bit live-cd worked really well otherwise (battery indicator seemed to behave, no screen brightness cycling etc), 32-bit had some bad video/starting X issues. I also could not get wireless to work under either on of them but I am really not worried about that.

---

### Post by vacula on 2008-07-17
I've tried Fedora 9 Live CD few weeks ago - problem with hibernate, battery and touchpad still occured there and I'm pretty sure the root of this all is invalid acpi on ms1221 :(

---

### Post by walkeraj on 2008-07-20
> **gaussian said:**
> Some good news: using yesterdays (7/15) daily live-CD's under both 32-bit and 64-bit one of the suspend modes worked perfectly. This means that
$sudo -s
$echo "standby" >/sys/power/state
resulted computer being frozen up like it should be and then returning after hitting the power button. This is the light sleep mode (no blinking lights).

Then the bad news: 
$sudo -s
$echo "mem" >/sys/power/state
resulted computer going to "deep sleep" properly, but not returning from there like it seems to do under hardy.

This is hardly a change, I'm afraid.  As far as I know, regular standby has been working.  Unfortunately, this doesn't do a heck of a lot for laptops as most of the board still remains powered.

> It looks like I am going to stick to Gutsy until 8.10 comes out.

Unfortunately, I don't think a new version number is going to make any difference unless this problem is fixed in the kernel between now and then.  Given the fact that this problem hasn't received a lot of attention from kernel developers and has been ongoing for months with no visible progress whatsoever, I wouldn't hold your breath for 8.10.

Speaking of this ongoing problem, has there been any progress?  What happened to that status report and feedback you were going to try and give to us?  It's been three weeks and nary a peep.

---

### Post by williumbillium on 2008-07-20
> **walkeraj said:**
> This is hardly a change, I'm afraid.  As far as I know, regular standby has been working.  Unfortunately, this doesn't do a heck of a lot for laptops as most of the board still remains powered.

I thought the issues with Hardy are the exact opposite of gaussian's ibex testing results.  According to the first post in this thread, hibernate (to hard disk) works, but suspend (to ram) does not.

> **walkeraj said:**
> Unfortunately, I don't think a new version number is going to make any difference unless this problem is fixed in the kernel between now and then.  Given the fact that this problem hasn't received a lot of attention from kernel developers and has been ongoing for months with no visible progress whatsoever, I wouldn't hold your breath for 8.10.

Speaking of this ongoing problem, has there been any progress?  What happened to that status report and feedback you were going to try and give to us?  It's been three weeks and nary a peep.

Agreed, I'd like to hear more updates too.  Not being able to upgrade is really starting to get frustrating, especially since I bought my Daru2 only a few weeks before Hardy came out :(

Edit:  Also, I am subscribed to several bugs in launchpad.  Perhaps if more people subscribed to them they'd get more attention.  They don't have many subscribers right now...

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/215033](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/215033)
[https://bugs.launchpad.net/system76/+bug/225347](https://bugs.launchpad.net/system76/+bug/225347)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/139701/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/139701/)

Not sure if this one is directly related to the Daru2 issues, perhaps someone knows?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279)

---

### Post by Nuno Bettencourt on 2008-07-21
> **williumbillium said:**
> Edit:  Also, I am subscribed to several bugs in launchpad.  Perhaps if more people subscribed to them they'd get more attention.  They don't have many subscribers right now...


Great idea, even though I've got a MSI pr200 clone, I subscribed to those threads that made sense to me and reflected my problems. Maybe this way it will have some more impact.

---

### Post by gaussian on 2008-07-21
> **williumbillium said:**
> I thought the issues with Hardy are the exact opposite of gaussian's ibex testing results.  According to the first post in this thread, hibernate (to hard disk) works, but suspend (to ram) does not.



Actually, my very limited testing had nothing to do with hibernate. It was between S1 and S3 sleep. S3 sleep is what we want (power/state=mem), S1 is what we have working (power/state=standby). I claim no expertise on this, see:
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Global_states]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Global_states")

Has anyone (System 76?) tried going through the procedure explained here: [https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend") ?

---

### Post by thomasaaron on 2008-07-21
Not sure. I'll pass that link on to R&D.

---

### Post by williumbillium on 2008-07-21
> **gaussian said:**
> Actually, my very limited testing had nothing to do with hibernate. It was between S1 and S3 sleep. S3 sleep is what we want (power/state=mem), S1 is what we have working (power/state=standby). I claim no expertise on this, see:
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Global_states]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Global_states")

Got it.  Looks like I was a little ignorant to the different states.  Thanks for the wp link.

---

### Post by thinman1189 on 2008-07-21
Not sure if this has been said already or not but I just got my serval performance today and suspend won't work.

---

### Post by thomasaaron on 2008-07-22
Might be a good idea to start a new thread dealing with suspend on servals. The DarU2 is a completely different issue.

Be sure to give more detail in the thread about the symptoms.

---

### Post by thinman1189 on 2008-07-23
Okay, I don't have time now but I'll try to suspend again tomorrow and post the error.

---

### Post by williumbillium on 2008-07-30
I noticed that the bug for this issue in the System76 launchpad has priority:undecided.  Shouldn't this be upped?  This is a showstopper for me.

[https://bugs.launchpad.net/system76/+bug/225347](https://bugs.launchpad.net/system76/+bug/225347)

---

### Post by walkeraj on 2008-07-30
Yeah, that's what prompted my comments about attention and progress, frankly.  It honestly appears from outside that no one really cares about this bug...:(

---

### Post by williumbillium on 2008-07-30
> **walkeraj said:**
> Sweet.  I'll friggin' make the whole company fresh gingerbread if you can fix this in the next two months.

I think it's also worth noting that we're now 1 month into the "fresh gingerbread if you can fix this in the next two months" period.  I'm going to up the ante by saying that if this is fixed in the next month, I'll bake brownies for the whole company too :)

---

### Post by walkeraj on 2008-07-30
> **williumbillium said:**
> I think it's also worth noting that we're now 1 month into the "fresh gingerbread if you can fix this in the next two months" period.  I'm going to up the ante by saying that if this is fixed in the next month, I'll bake brownies for the whole company too :)

I say draft that up and have it notarized.  Let's make this official.

---

### Post by williumbillium on 2008-08-04
Perhaps the Ubuntu kernel team meeting, this tuesday,

[http://blog.phunnypharm.org/2008/08/ubuntu-kernel-team-irc-meeting.html]("http://blog.phunnypharm.org/2008/08/ubuntu-kernel-team-irc-meeting.html")

would be a good opportunity to raise this issue with the Ubuntu kernel team?

---

### Post by walkeraj on 2008-08-13
Three weeks now.  I'm determined not to let this thread leave the first page until we hear SOMETHING about SOME kind of progress.

---

### Post by thomasaaron on 2008-08-13
I appreciate your tenaciousness. However, the guys in R&D and the devs looking into this one probably do not see this post.

This is a very tough one, and we are still working on it. I promise.

---

### Post by arch_o_median on 2008-08-13
I've been running: 

sudo /etc/acpi/hibernate.sh

  It works about 70% of the time....

---

### Post by walkeraj on 2008-08-13
> **arch_o_median said:**
> I've been running: 

sudo /etc/acpi/hibernate.sh

  It works about 70% of the time....

That's probably because, like your signature says, you're running a gazelle and not a Darter Ultra 2, which is what this thread is about.  I appreciate you trying to be helpful, but, in the future, try and read the thread a bit more before you post.

Edit: This is, in fact, the [second time]("http://ubuntuforums.org/showpost.php?p=5239497&postcount=29") you've incorrectly commented on this same thread about this same issue.

---

### Post by gaussian on 2008-08-13
An aside: Overall when it comes to hibernating with my Darter, I have found that using s2disk (part of uswsusp or suspend package, depending on the version of Ubuntu) works more reliably than using the standard (pmi) hibernate.

Back to regularly scheduled programming: Suspending (S1) Darter...

---

### Post by laserline on 2008-08-18
Hi Tom,

I found this thread [http://ubuntuforums.org/showthread.php?t=810222&highlight=suspend](http://ubuntuforums.org/showthread.php?t=810222&highlight=suspend)

Apparently, the daru2 isn't alone at all.
Dell, Compaq and other laptops suffer from the same problem.

Is this problem Ubuntu specific or Linux specific ?

I wonder if Fedora / Mandriva have the same problems. Did R&D try installing a diffrent distro ?

Thanks,
Idan.

---

### Post by thomasaaron on 2008-08-18
> Apparently, the daru2 isn't alone at all.
Dell, Compaq and other laptops suffer from the same problem.


> Is this problem Ubuntu specific or Linux specific ?


I wonder if Fedora / Mandriva have the same problems. Did R&D try installing a diffrent distro ?

Thanks,
Idan.

---

### Post by thomasaaron on 2008-08-18
> Apparently, the daru2 isn't alone at all.
Dell, Compaq and other laptops suffer from the same problem.

Honestly, I'm not sure if the problem with Dell and Compaq are the exact same issue. As far as I know, it is pretty unique to the DarU2 and it deals with some conflicts between Ubuntu's tickless kernel and the DarU2's hardware.

> Is this problem Ubuntu specific or Linux specific ?

I wonder if Fedora / Mandriva have the same problems. Did R&D try installing a diffrent distro ?

I know it exists under Fedora. I believe some customers have tried other distros without success.

---

### Post by gaussian on 2008-08-18
> **thomasaaron said:**
> Honestly, I'm not sure if the problem with Dell and Compaq are the exact same issue. As far as I know, it is pretty unique to the DarU2 and it deals with some conflicts between Ubuntu's tickless kernel and the DarU2's hardware.



I know it exists under Fedora. I believe some customers have tried other distros without success.

Can confirm this under Mandriva (2008.1 Live-CD, 32 bit) and Open-Suse (Live-CD, I think it was 64 bit).

---

### Post by glacialfury on 2008-08-22
As far as I've seen, it's more a Hardy problem; resuming from suspend apparently worked well in Gutsy.  Many users across many different hardware sources are having this problem.

Several have fixed it using "quirks".  I don't profess to understand it all, but perhaps those more knowledgeable would look into:

[http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html)

---

### Post by walkeraj on 2008-08-26
Nope.  It is not just a hardy problem, it is everywhere.  It's the new kernel that came with Hardy.  If you downgrade your kernel in Hardy, suspend/hibernate revert to the way they were before (albeit with a host of other problems).

These "quirks", are basically different methods of hardware-specific suspend stored in hal-info, and should already be up-to-date on all of these systems.  I'll give a few of them a try and post any successful results here.

---

### Post by luckytwitch on 2008-08-27
So, I'm a new Ubuntu user, but after cruising through these forums and following lots of links, I found something that works for my system (Kubuntu 8.04 and KDE on my Sony Vaio VGN-CR123E).  I'm not quite sure what it actually does, but my suspend works now.  
Here's the link that I found, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279"), and the following is the code that I used to make suspend work:```
echo "SUSPEND_MODULES=ehci-hcd" > /tmp/unload_modules
chmod +x /tmp/unload_modules
sudo mv /tmp/unload_modules /etc/pm/config.d
```
If anyone can explain what this actually does, it'd be cool, thanks

---

### Post by walkeraj on 2008-08-27
(from [wikipedia]("http://http://en.wikipedia.org/wiki/Host_controller_interface")):

> A host controller interface (HCI) is a register level interface which allows a host controller for USB or FireWire to communicate with the operating system of a personal computer.

On the expansion card or motherboard controller, this involves much custom logic, with digital logic engines in FPGAs plus analog circuitry managing the high speed differential signals. On the software side, it requires a device driver (called a Host Controller Driver, or HCD).

Enhanced Host Controller Interface (EHCI) is a high speed controller standard which is publicly specified.

So, what's happening is that, on your particular laptop (which is totally different from the one being discussed here), either the usb chipset itself or the driver is causing problems with suspend.  By adding
```
SUSPEND_MODULES=ehci-hcd
```

to **/etc/pm/config.d**, you are telling linux to unload this module from the kernel before it suspends and reload it when it returns.  By having the kernel explicitly unload this module, it ensures that it is not loaded when the actual suspend occurs, and ensures that it is cleanly removed and re-inserted into the running kernel when you come back from suspend.  This is a general way to avoid modules that cause problems with suspend.  Unfortunately, as I mentioned above, this is a TOTALLY different laptop.  Which modules cause these problems (and indeed whether it is a module that causes it or not) is very hardware dependent and will differ greatly between even laptops of the same general make from the same manufacturer.

In the case of this laptop, it definitely appears to be something more than a simple SUSPEND_MODULES directive.

Thanks for trying to help, though.

---

### Post by walkeraj on 2008-10-02
I've honestly given up on expecting a solution to this, but is there anything new to say about it?

---

### Post by thomasaaron on 2008-10-02
Well, it worked with Gutsy 64-bit. Then died in Hardy.

I'm trying to figure out what changed:

I downgraded HAL, Gnome Power Manager, acpid and several other things.
I even installed Hardy's realtime kernel (as Gutsy 64-bit was a realtime kernel). No dice.

If you guys have any other ideas on this, I'd love to try them.

So, we're still working on it.

---

### Post by walkeraj on 2008-10-02
Did someone mention that hibernate was working in the latest Intrepid builds?  I'm trying to recall if I saw that somewhere.

---

### Post by thomasaaron on 2008-10-02
I think I heard that too. But we're just now gearing up to start testing intrepid.

---

### Post by gaussian on 2008-10-02
> **walkeraj said:**
> Did someone mention that hibernate was working in the latest Intrepid builds?  I'm trying to recall if I saw that somewhere.

Yes. It is still working (at least was couple days ago, at least using s2disk, but last time I checked it worked with pm-hibernate too). 

Intrepid is actually getting to be quite reliable by now (huge change over the last month), the only big thing for my home usage is Flash 10 not being quite compatible/or horrible slow with lot of important websites (webkinz, soccernet-live scores, shining stars...:D) This could be easily fixed by installing manually Flash 9.

---

### Post by freduardo on 2008-10-09
I don't know if this is going to be very useful to most you, but at the very least it is another bump on this thread:

I'm using Arch Linux (64b) on my MSI PR200 at the moment, with their stock 2.6.26 kernel.

- The alsa issue is pretty much solved (using gnome-alsamixer and muting 'front' when on headphones).

- Battery state is reported correct abut 99% of the time. The only time it seems to fail is when the battery is fully charged but still plugged in on AC.
When I issue: 
```
dmesg | grep EC
``` I get:
```
ACPI: EC: driver started in poll mode
```
at the end.

- Overall battery performance seems to have improved in comparison with Ubuntu Gutsy. Note though that I'm using a far lighter setup (Openbox) than Gutsy's full blown Gnome desktop.

- Hibernate seems to work fine with pm-hibernate. Although I've only tested it once, the laptop did 'revive' correctly.


- Suspend unfortunately doesn't work. I get the same 'revival' behaviour most of you described here.


Again, this might not be that interesting to most of you, but if anyone wants more info (e.g. wants me to look something up on my Arch setup) to compare with their Ubuntu stuff, don't hesitate to ask.

---

### Post by freduardo on 2008-10-09
Sorry, double posted.

---

### Post by laserline on 2008-10-10
Hi Tom/Crichell

As this thread is open for almost 6 months w/o resolution I expect  System76 to give us Daru2 users a detailed update about where this issue stand.

In this update I expect the following information:
[LIST=1]
[*]What caused the problem/breakage from Ubuntu 7.10
[*]What is currently been done/investigated.
[*]Who is working on this bug.
[*]What is the problem or atleast you think the problem is (kernel/apci tools etc...)
[*]A roadmap for a resolution of this bug (so we'll know what's going on)
[*]Any other information you think we should know.
[/LIST]

On a side note, I just tried Mandriva 2009 that uses the 2.6.27 kernel and I find the same issues: Suspend and Battery monitor loosing the battery.
In addition, I tried the latest Ubuntu 8.10 and that has the same issues also (Suspend and Battery monitor loosing the battery).

I thank you in advance, and expect a quick and thorough reply asap.

Idan.

---

### Post by val67 on 2008-10-10
This is ridiculous... what bug takes 6 mths to be solved ??!!

---

### Post by jdb on 2008-10-10
> **val67 said:**
> This is ridiculous... what bug takes 6 mths to be solved ??!!

This one :)

If it was easy, it would be fixed, it's not & it's not.
Nothing ridiculous about that.

jdb

---

### Post by gaussian on 2008-10-10
> **jdb said:**
> This one :)

If it was easy, it would be fixed, it's not & it's not.
Nothing ridiculous about that.

jdb
Also note that this bug seems to affect every distribution having a newer Kernel (>2.6.24 I think), so it is not a little tweak that Ubuntu made that broke things. 

And by every I mean everyone I tested and every report in these forums from users trying out other distros.

---

### Post by gaussian on 2008-10-10
> **laserline said:**
> 
In addition, I tried the latest Ubuntu 8.10 and that has the same issues also (Suspend and Battery monitor loosing the battery).


I have been using 8.10 for months now as a testing laboratory, and I haven't seen any Battery monitor issues. Suspend certainly does not work.

---

### Post by val67 on 2008-10-10
AFAIK the Dell ubuntu laptops suspend just fine with Hardy.

---

### Post by jdb on 2008-10-10
> **val67 said:**
> AFAIK the Dell ubuntu laptops suspend just fine with Hardy.

The Dell has different hardware/bios, it's a hardware/bios/kernel compatibility problem.

jdb

---

### Post by val67 on 2008-10-10
Right, so the solution to the problem is to buy a dell machine instead of one from system76, right? or else we have to wait till when? 'cause i don't see any progress from the system76 front ...

---

### Post by gaussian on 2008-10-10
> **val67 said:**
> Right, so the solution to the problem is to buy a dell machine instead of one from system76, right? or else we have to wait till when? 'cause i don't see any progress from the system76 front ...


Have fun calling Dell Tech Support, or even their sales :) At least for me support from System 76 has been well worth the inconvenience of not having functioning Suspend.

Seriously, I would also appreciate an update on this. But I understand that it is not necessarily something that is easy to solve. I would also really appreciate if System 76 would be little more transparent on what works and does not work with their different models under different versions of Ubuntu.

Edit: Just checked again, under Intrepid S1 sleep works (i.e. "sudo -s, echo "standby" >/sys/power/state") works.

---

### Post by laserline on 2008-10-11
> **gaussian said:**
> 
Edit: Just checked again, under Intrepid S1 sleep works (i.e. "sudo -s, echo "standby" >/sys/power/state") works.

Well, This sounds promising.
Can anyone else confirm this ?

I'll try it now on Hardy and post my results.

If that works on Intrepid, I guess System76 could add it to the driver to change the default behavior of the suspend.

Idan.


**EDIT1:** I just did that from the terminal in Gnome on Hardy and the system did suspend, but the Screen was still lit and I could see the screen as it is.
Is there a way to cause this method to shutdown the monitor ?

**EDIT2:** I've changed the defaults in ```
/etc/default/acpi-support
``` to ```
ACPI_SLEEP_MODE=standby
```
And then hacked the /etc/acpi/sleep.sh script so it won't exit if gnome is running (commented out lines 15,16,17) and executed the sleep.sh script as root. The system went to sleep, including monitor shutting down. The CPU still works (as it's only to RAM) but the system did come back (!) - That's on Hardy.

Now what I need to figure out is how to tell Gnome's power management to use "standby" instead of "ram" and that will do the trick.

Anyone knows where Gnome holds that setting ?

---

### Post by jhp-dk on 2008-10-11
I havent read the whole thread, but mine ubuntu hardy dont return from suspend, if i use the suspend button from the 'quit'-menu.

then i tried looking in the repos for hibernate, and i think theres a package with this name. I installed it and now my suspend to ram work with the command ```
sudo hibernate-ram --f
```
i have to force it because my nvidia nvs140 cant unload :S  but i dont care as long as it works.. :)

---

### Post by laserline on 2008-10-11
If you edit the acpi-support file and change it like my previous post, then the 'sleep.sh' script should work.

I'm looking for a way to change the behaiviour of the 'Logout' button in Gnome. So it'll use 'standby' instead of 'ram'

Does anyone know how this can be changed (if at all)

Idan.

---

### Post by williumbillium on 2008-10-12
The fact that S1 suspend/standby is working in Hardy has been known about for a while.  It's just not really very useful as it still consumes a fair amount of power.

Also, jhp-dk, this thread is specifically for the System76 Daru2 model laptop.  It sounds like you have something else.

---

### Post by walkeraj on 2008-10-14
> **jhp-dk said:**
> I havent read the whole thread, but

Ach, then *don't reply to it.*.  Please.  This issue is bad enough as it is without someone popping in every couple of pages to say "Suspend doesn't work on my dell/compaq/macbook".  There are a great many helpful threads out there that probably have to do with your laptop.  Search for them, read them and be well.

As for everyone talking about how S1 works: ***We know.*** We've known for months.  We've known even a few pages earlier in this very thread, but the point remains: the laptop is still largely powered on.  This does bupkis for any practical purposes.  What we need are S3 and S4 working like any good laptop should.

---

### Post by Modax42 on 2008-10-16
Well, for what it's worth, suspend works pretty well on my new Darter.  It does refuse to resume once in a while--I'd say once every five times--but I'd say that's pretty comparable to my friend's vista laptop, which often crashes on resume

---

### Post by walkeraj on 2008-10-16
> **Modax42 said:**
> Well, for what it's worth, suspend works pretty well on my new Darter.

Agh, you're killing me.

As in the Darter 3?  As in *not this laptop*?  I don't mean to be rude, but I really don't understand posts like this.  Are you trying to be helpful, or are you posting just to post?  After all, you are, in essence, saying:

"Yeah, I know this thread is about a totally different laptop, but, hey, mine works if it means anything to you."

When you look at it like that, does it make sense?

I mean, even if your brand new darter is the same model as ours, you didn't even provide any information or speculation on what might be different with your laptop or any kind of informed information on this thread at all.

So, I feel fairly comfortable saying that "what it's worth" is precisely zero.

---

### Post by djekz on 2008-10-16
> **Modax42 said:**
> Well, for what it's worth, suspend works pretty well on my new Darter.  It does refuse to resume once in a while--I'd say once every five times--but I'd say that's pretty comparable to my friend's vista laptop, which often crashes on resume


Wow, that input was really not useful to this thread at all.  Please refrain from adding various random messages that have no pertaining value to a thread, it adds unnecessary extra reading for those interested in finding a solution.

---

### Post by thomasaaron on 2008-10-16
C'mon, guys. Let's not pound the poster too hard. A lot of new System76 customers don't realize that a) there are different versions of the various models (DarU1, DarU2, DarU3); and b) there are huge hardware differences between each version.

If you haven't been following System76 for a while, this is an easy mistake to make.

Maybe this would be a good point to clarify in a sticky. I'll talk to Carl about it.

---

### Post by gaussian on 2008-10-16
> **walkeraj said:**
> Agh, you're killing me.

As in the Darter 3?  As in *not this laptop*?  I don't mean to be rude, but I really don't understand posts like this.  Are you trying to be helpful, or are you posting just to post?  After all, you are, in essence, saying:

"Yeah, I know this thread is about a totally different laptop, but, hey, mine works if it means anything to you."

When you look at it like that, does it make sense?

I mean, even if your brand new darter is the same model as ours, you didn't even provide any information or speculation on what might be different with your laptop or any kind of informed information on this thread at all.

So, I feel fairly comfortable saying that "what it's worth" is precisely zero.

Really, who died and made you the post police? This is an open internet forum. Like it or not, you will get some post containing irrelevant noise here. While they might irritate you, please show some common courtesy in your responses. And your post complaining about the noise will just add noise. As will this post. Lighten up.

---

### Post by walkeraj on 2008-10-16
Absolutely.  Open is the name of the game, yes, but because they're open sometimes they need to be self-regulating.  We're all the post police.  Occasionally, people need to be told to RTFM (or... I suppose it would be RTFT).  Not one of us can claim that we haven't been told the same before.

Were a person to do so with that with this thread, they would not only see the specifics mentioned numerous times, but would also see examples of other people mistakenly entering the thread without reading it and being gently informed of the specifics.

As I said, even if it was relevant to this model, "works for me" just isn't very helpful, especially when some of us have been trying to solve this issue for six months now with no progress.  It's frustrating when someone comes in and says "hey, well, my new laptop works".

I may have been a bit harsh, and, if I hurt anyone's feelings, *mea maxima culpa*.

---

### Post by elusivespoon on 2009-04-26
So hoping against hope, is there any chance suspend will work if I do a dist upgrade to Jaunty?

---

### Post by thomasaaron on 2009-04-27
No, but it seems the power monitoring is fixed.

---

### Post by williumbillium on 2009-05-04
> **thomasaaron said:**
> No, but it seems the power monitoring is fixed.

Really?  Power management was still wonky for me until I applied the patch from Timo Tretter's PPA.

---

### Post by elusivespoon on 2009-05-07
> **thomasaaron said:**
> No, but it seems the power monitoring is fixed.

Really? Right now the power monitor is showing as not charged and no power, and CPU temp at 295F (both of which aren't true). Do I still need to have 'acpi=noirq' in the boot options?

---

### Post by thomasaaron on 2009-05-07
Evidently, I was mistaken. I thought I'd read in a different thread that it was working better. But that person must have used the aforementioned ppa. Sorry about that, guys.

---

### Post by jdb on 2009-05-07
> **elusivespoon said:**
> Really? Right now the power monitor is showing as not charged and no power, and CPU temp at 295F (both of which aren't true). Do I still need to have 'acpi=noirq' in the boot options?

I've kind of lost track of which release has what kernel, but I'm thinking it might not be fixed in the kernel 8.04 uses.

Anyone out there know???

jdb

---

### Post by williumbillium on 2009-05-07
> **jdb said:**
> I've kind of lost track of which release has what kernel, but I'm thinking it might not be fixed in the kernel 8.04 uses.

Anyone out there know???

jdb

According to [this]("http://bugzilla.kernel.org/show_bug.cgi?id=12011#c116") the patch was applied to 2.6.29.  Jaunty uses 2.6.28.  I can't find any mention of "ACPI: EC: Add delay for slow MSI controller" with regards to 2.6.28.

Although I only booted up Jaunty once without using Timo Tretter's patch, I definitely experienced the usual symptoms of broken power management in that case.

---

### Post by jdb on 2009-05-07
> **williumbillium said:**
> According to [this]("http://bugzilla.kernel.org/show_bug.cgi?id=12011#c116") the patch was applied to 2.6.29.  Jaunty uses 2.6.28.  I can't find any mention of "ACPI: EC: Add delay for slow MSI controller" with regards to 2.6.28.

Although I only booted up Jaunty once without using Timo Tretter's patch, I definitely experienced the usual symptoms of broken power management in that case.

That sounds about right.

I've been running 2.6.29 on Archlinux for a while & the problem is
definitely gone in that version.

The latest Ubuntu I'm running is Ibex on 2.6.24 but it is in Virtualbox so I think that's hiding the problem, I'm not sure
though because I've never let it run long enough to tell.

jdb

---

### Post by williumbillium on 2009-05-07
> **elusivespoon said:**
> Really? Right now the power monitor is showing as not charged and no power, and CPU temp at 295F (both of which aren't true). Do I still need to have 'acpi=noirq' in the boot options?

A fellow daru2 owner has a PPA with patched versions of the Ubuntu kernel that will fix this problem.  The instructions to use it are here:

[http://ubuntuforums.org/showpost.php?p=6717607&postcount=21](http://ubuntuforums.org/showpost.php?p=6717607&postcount=21)

You'll just need to switch out references to "intrepid" to "jaunty"

BTW, AFAIK, the extra kernel parameters won't help in Jaunty and are not needed if you do use the above PPA.

---

### Post by williumbillium on 2009-08-14
There's a report on the bug for the daru2 suspend issue that suspend is working with Karmic:

[https://bugs.launchpad.net/system76/+bug/225347/comments/2](https://bugs.launchpad.net/system76/+bug/225347/comments/2)

I'm not going to have time to test this for the next week or two as I'll be travelling.

Anyone else able to confirm this is true?

---

### Post by j.c.sackett on 2009-11-06
I tried suspend in karmic and it still fails.

However, I am not testing on a clean install. Anyone care to try that and post results?

---

### Post by thomasaaron on 2009-11-06
Yeah, I can't find the person who left that comment in our database. That doesn't mean he doesn't have a daru2, but...

---

