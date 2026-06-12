---
title: "Power Management Problem"
date: 2007-11-11
forum: System76 Support
---

### Post by gamx on 2007-11-11
I just got my Darter Ultra and I am happy with it. However, there is a problem that it is quite annoying. If I am running the laptop with AC power and the battery plugged in, the computer keeps changing the brightness of the screen from normal to "dim" (every minute or so). At the same time, the icon for power management (I configured to show up even if it is not charging) changes from "charging" to "empty." The system seems to be running with the battery during these "dim" periods...

I think it has to do somehow with the power management, because if I run the laptop with AC power and without the battery the brightness is fine.

Anybody has had this problem?

---

### Post by nowanfoo on 2007-11-11
I'm having a very similar problem.  The screen dims and brightens frequently, displaying the gnome brightness-adjustment icon while it does so.  The gnome power-management icon switches from displaying the plug (indicating AC power) and not displaying it as well.  This is all while the AC is plugged in.  The degree of charge of the battery seems to make no difference (even when the batter is fully charged), nor does replacing the battery with a different one.

Also, /proc/acpi/battery/BAT1/state seems confused as well.  For example:

present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      unknown
present voltage:         10000 mV

This is while AC is in and the green battery-charging light on the front has gone off.  A few seconds later, after the screen brightens, but with the green battery-charging light still off:

present:                 yes
capacity state:          ok
charging state:          charging
present rate:            2304 mA
remaining capacity:      18 mAh
present voltage:         53313 mV

I'm running gusty on my darter ultra, model MS1221.  Until recently I was not using gnome (I was using ion).  I switched to gnome to try to get power management working, since it was completely disabled before.  Now power management is enabled, but I'm not sure the cure is worth it, as the flickers are frequent and disturbing.  Often the screen blanks for a second or so as well.

---

### Post by nowanfoo on 2007-11-11
It would seem this is the same problem as here:

[http://ubuntuforums.org/showthread.php?t=587276]("http://ubuntuforums.org/showthread.php?t=587276")

---

### Post by gamx on 2007-11-11
Yes. That is exactly my problem. Let's hope they find a fix soon... Thanks for the tip.

Gamx

---

### Post by palintheus on 2007-11-11
the dimming/blanking just showed up in Gutsy, but the power applet has been an issue since release of the daru2, the dsdt tables are the issue there, they are working on them according to the previous threads on this issue.

---

### Post by thomasaaron on 2007-11-12
The dimming issue has now been fixed. It will be coming down in the next System 76 driver. Should be within the week.

---

### Post by gamx on 2007-11-12
That is great news! thanks!

---

### Post by nowanfoo on 2007-11-20
Any word yet on when the new system76 driver will be available?

---

### Post by thomasaaron on 2007-11-20
Probably mid-week next week.

---

### Post by pavel_987 on 2007-11-26
by "The dimming issue has now been fixed" do you mean the dsdt tables are in order? Or is it more of a workaround dealing with the dimming.

My question is: after the update, would I be able to monitor my cpu temperature and battery through acpi without it going haywire every few minutes?
Right now I have the updated DSDT without the compiled errors, maybe it helps. But my acpi sensors still go haywire. :sad:

---

### Post by thomasaaron on 2007-11-26
The DSDT tables have been re-compiled and work much better. There is still more work to do on them, but you should be able to monitor your battery fine.

---

### Post by werewolves on 2007-11-30
> **thomasaaron said:**
> Probably mid-week next week.

Any updates on the release of this?

---

### Post by thomasaaron on 2007-12-03
I know I've said this before, and I'm not trying to be evasive, but VERY soon. The fix is in place, but the driver is getting a face-lift. It should be done by the end of the week.

---

### Post by nowanfoo on 2007-12-07
Can anyone point to a discussion of this issue elsewhere -- some way to fix it other than waiting on the new driver?

---

### Post by palintheus on 2007-12-07
It has to do with the dsdt tables being re-compiled so its not common, also this laptop is pretty new so I don't think their is a solution for it outside System76. I have searched before and found nothing on the subject other than these forums.

---

### Post by pavel_987 on 2007-12-11
I would like to inquire if this is issue will still be worked on. I have the new 2.1.3 system76 driver and I can't say that I see much results. I haven't taken empirical measurements but I think the record for correctly reporting battery charge is 3 min. 

Pre-emptive answer: Yes, I have the new DSDT. 100% sure.

---

### Post by muzcuk on 2007-12-11
Same thing here... The 0 0 1 0 2 0 3 0... thing has been solved with this driver but battery indicator still sucks.. Also the screen dimming problem continues, that is unless I disable screen dimming while on battery power...

---

### Post by thomasaaron on 2007-12-11
Just want to verify that you RAN the driver. System > Administration > System 76.
Sorry. I've got to ask.

---

### Post by muzcuk on 2007-12-11
Not only the driver but I ran the system restore and then the driver. I am quite sure it worked because as I said, 0 0 1 0 2 0 3 0 4 0 thing has been solved instantaneously but nothing else..

---

### Post by pavel_987 on 2007-12-11
Not only did I run the driver, I (cat)'ed the dsdt from /proc/acpi/dsdt , decompiled it with the  intel ASL compiler, then (diff)'ed it with the previous dsdt from your driver. You made ~14 changes with most of them being LEqual to LGreaterEqual. 

Sometimes I'm PEBKAC and ask tech support stupid questions. But this issue is very important to me. Half of my laptop use is mobile.

---

### Post by nowanfoo on 2007-12-11
Same here; downloaded the driver, ran it, did the driver install to be sure, and rebooted.  Battery status is still haywire more often than not, and the screen dimming/brightening issue persists.

---

### Post by thomasaaron on 2007-12-11
OK. I'll be testing a Darter today. Let me have a look.

---

### Post by saxamo on 2007-12-11
I've downloaded the driver and restored, and I must say that it looks like power management is working allright for me. Allright meaning, MUCH less buggy than before.

Edit: I spoke too soon. Can't read battery information, it only recognizes if the AC is plugged in or not.

---

### Post by muzcuk on 2007-12-11
Lucky guy.. Mine doesn't even do that..

---

### Post by gamx on 2007-12-11
The latest driver hasn't solved my problem either. It still says the battery is empty when it is not and the like...

---

### Post by werewolves on 2007-12-11
Same here.  Battery monitor still shows wrong state.  Screen dimming is still wonky.  If I can provide any info, please let me know.

---

### Post by GregCwx1 on 2007-12-12
I've been following this thread with interest for awhile since I experienced the same issues early on with my Daru2 and gutsy (7.10) ubuntu upgrade.

I have been running the laptop in battery mode for almost three hours this evening (supposedly I have 5 minutes left). I can report a considerable improvement in the power management after installing the latest system76 patch/driver. I have had no intermittent screen dimming. I even set the screen to a lower setting to see if it would switch back and forth like before. No change. The sensor just came on and told me I have 4 minutes left. I'll see if it gos into hibernate mode as it is supposed to.

Anyway, the fixes seem to be working on my system. Thanks for keeping on top of the situation system76 and I hope the other's with problems can get to the bottom of the issue.

Good luck!

---

### Post by vacula on 2007-12-13
Good time, everyone!

I also experience similar troubles with my laptom MSI PR200. It's also based on MS-1221, and ACPI there sucks even with syntax fix and recompilation :(

I'm trying zen-sources kernel, and the only thing I asked maintener to add there is early Embedded Controller table initialization - so I have battery present, but it after some minutes goes crazy.

I'm using custom linux, and I'm very interested in getting modified dsdt or any related patches, so will appreciate any links. Where is it possible to download drivers you are talking about here not using ubuntu updater?

---

### Post by muzcuk on 2007-12-13
The driver comes from system76 repository for ubuntu, I am not sure how you would download it for another distro. The driver will recognize your PR200 as daru2 and will work perfectly fine (that is of course if you can install it). It solves many issues but power management is not one of them (it gets slightly better, though). The driver is basically a bunch of scripts to recognize your computer and modify configuration files etc. according to your system. Your best bet for another distro would be downloading the source code and modifying and re-compiling it to work on your distro, or you can understand what it does and apply the modifications manually to your system (you'd have to keep up with the updates in that case)..

Where can you get the source? I don't know. I also needed it at some point and couldn't find it. But one of the system76 people will probably help you out.. They are good. 

My system is called DATRON MS12 but it is same as MSI PR200 or system76 darter ultra 2, I am running gutsy 32 bit with system76 drivers. I intend to switch to gentoo (64 bit) to maximise performance at some point but power management (and other stuff) does not work properly even with the system76 drivers so I wouldn't really trust gentoo on that. In a couple of months, hopefully all of the issues will be solved (card reader (MS), HDMI out, fingerprint reader and power management, also the compiz thing with intel 965 ) and then I will migrate to gentoo, applying fixes one by one manually. This is the drawback of having a system so good, it is not supported well, not in linux.

---

### Post by vacula on 2007-12-13
thanks a lot, muzcuk!

Actually, currently I'm running gentoo x86_64, so +1 pair of hands and one head to your efforts to get linux work properly on MS-1221.

One more thing, could you post here System 76 Support deb repository?

---

### Post by muzcuk on 2007-12-13
[http://planet76.com/repositories/](http://planet76.com/repositories/)

cool..

could you share your make.conf ? I really couldn't decide which flags to use.. 

I know how to handle portage but I never had a santa rosa processor before..

plus, what do you have in your kernel?

---

### Post by thomasaaron on 2007-12-13
Crack open the driver and look at sound.py. You'll see how we compile it.

---

### Post by pavel_987 on 2007-12-13
+1 Gentoo x86_64 here

So far Gentoo supports everything Ubuntu does. At least on this laptop. You just have to get the System76 drivers and backport it to Gentoo. So don't worry about switching, the power management problems are just as bad on Ubuntu as they are on Gentoo. I keep a partition with Ubuntu on it for compatibility purposes (which my friend finds funny because most people do that with windows).

Considering this is a power management forum subject: Anyone out there feels like tinkering with the DSDT? I had a quick look but don't have the time to actually sit don't and figure stuff out. It'd be great if one of you hobbyists would improve the DSDT then submit a patch to System76.

---

### Post by ryjo on 2007-12-15
Hello,

I just got a Darter with Gutsy.  This power management problem remains after having run the System 76 driver today (12/15),  Thanks for news/advice.

---

### Post by thomasaaron on 2007-12-17
Could you please confirm that 1) your system is completely updated, and 
2) you are running 2.1.3 version of the driver (System > Admin > Sys76Driver > About.

---

### Post by nowanfoo on 2007-12-17
Is this directed specifically at the previous poster, or at the rest of us that are having this problem as well?  In my case I am running 2.1.3, and my system is completely up to date.

---

### Post by thomasaaron on 2007-12-17
Sorry. It was directed to ryjo.

---

### Post by ryjo on 2007-12-17
Yes. The system is completely updated, I am running version 2.1.3 of the System76 Driver, and I installed the System 76 drivers after the system was completely updated.  With this software status and with AC plugged in, the current primary symptom is that power management bounces between thinking it is on AC with highly variable estimates of battery state, and thinking it is on battery and unable to determine battery state.

> **thomasaaron said:**
> Could you please confirm that 1) your system is completely updated, and 
2) you are running 2.1.3 version of the driver (System > Admin > Sys76Driver > About.

---

### Post by sonmez on 2007-12-17
I noticed that I am having the same problem. I have Daru2 with up to date Gutsy and system76 driver.

Peneus

---

### Post by ackey on 2007-12-19
It seems to be better than it has been before, but the power manager does not always function properly.  I have run the driver (both install and restore) and restarted the system.  The DSDT.aml file shows a modification date of Dec. 13th, so presumably the driver "worked".

Is there a specific configuration of HAL/ACPI/etc that should be running for this to work?  I had problems with HAL after my gutsy upgrade and had to do some fiddling, so it may not be in the expected state.

---

### Post by thomasaaron on 2007-12-19
The driver should have definitely fixed the issue with using the function keys to brighten and dim the lcd.

As for the rest of it, we are back to work on it. It seems that some progress was made, but the problems are definitely still there.

---

### Post by werewolves on 2007-12-23
> **thomasaaron said:**
> The driver should have definitely fixed the issue with using the function keys to brighten and dim the lcd.

Not in my case at least.  Installed the driver as soon as it came out, but if I dim my screen, after a few seconds, it will brighten back to full.

---

### Post by thomasaaron on 2007-12-24
Could you please send me an email with what you just said. Include model#, etc...
I'll test as soon as I get back to the office on the 31st.

---

### Post by palintheus on 2008-01-03
This is a new one to me, it happened when unplugging my daru2 from the AC adapter
[IMG]http://img510.imageshack.us/img510/3037/screenshotkg2.png[/IMG]

also any updates on progress?

---

### Post by thomasaaron on 2008-01-04
I've NEVER seen that one before. Any ideas on how I can duplicate it. (If it's KDE, nevermind.)

---

### Post by palintheus on 2008-01-04
Its GNOME, and all I did was unplug my AC adapter....

---

### Post by thomasaaron on 2008-01-04
I'm trying duplicate that.

---

### Post by palintheus on 2008-01-04
Good luck!

---

### Post by thomasaaron on 2008-01-04
That's got to be a fluke.

But I know how you can work around it: Don't do that anymore! :lolflag:

---

### Post by saxamo on 2008-01-04
> **palintheus said:**
> This is a new one to me, it happened when unplugging my daru2 from the AC adapter
[IMG]http://img510.imageshack.us/img510/3037/screenshotkg2.png[/IMG]

also any updates on progress?

I too have seen this same message a few times, I haven't thought much of it but I definitely have gotten it before. Usually when I unplug my AC adapter.

---

### Post by nowanfoo on 2008-01-06
> **thomasaaron said:**
> I've NEVER seen that one before. Any ideas on how I can duplicate it. (If it's KDE, nevermind.)
I get that message sometimes when I push the power button to shut down -- I presume that it's because gnome has noticed that the battery state has changed (eroneously, of course).  If so, could it be that this happens when the AC is unplugged as well -- i.e., if the AC is unplugged directly after gnome has noticed a battery state change?

---

### Post by gamx on 2008-01-16
Going back to the original posts of this threat... Are there any news on when the problem with power management will be definitely fixed?
Thanks.

---

### Post by pavel_987 on 2008-01-16
When I was purchasing the laptop I was looking at the system features and the laptop pictures. I notices that the fingerprint scanner and hdmi port weren't listed in the features. Realized that those aren't supported therefore not listed. I can understand that, support for those is sort of hard and system76 didn't mislead it's customers by stating there's a working fingerprint scanner and hdmi port.

But I do wish for system76 to put a disclaimer on their website about this laptop. Power management is something that I assume to be working when I see a laptop being sold in such a way. The currently stated information is not complete.

---

### Post by gamx on 2008-01-19
Unfortunately, I couldn't agree more. This problem has been going on for quite a long time and it is a showstopper for most of us...

---

### Post by nowanfoo on 2008-01-22
> **gamx said:**
> Unfortunately, I couldn't agree more. This problem has been going on for quite a long time and it is a showstopper for most of us...
As annoying as I find the problem, I suspect that calling it a showstopper is going too far in most cases.  It's not as if the battery doesn't work, after all, it's that the system's efforts to extend and monitor battery life are miss-firing.  Disable these efforts and the annoyances go away (with the exception of not being sure what your battery life is), and you still have a perfectly respectable battery life.  Even if you push it to the extreme edge (which I've done a time or two) the occasions when the battery reports are accurate are frequent enough that you'll be warned to shut down.

As for System76, I've no complaints about the level of support.  This has been taking time, but these things do take time, after all.

---

### Post by theologian aaron on 2008-01-22
I am rarely if ever warned to shut down when the power is low.  I am a student, and am constantly using my machine on the go.  I have lost data because the computer has cut out with no warning at all.  

I would have to say that it is a dealbreaker, and that I would not have bought this thing had I known about it.  Also, I cannot recommend others to buy it until this issue has been fixed.

---

### Post by badbull on 2008-01-25
hi, i've this acpi problem with my msi pr200, too. I compiled the new linux kernel 2.6.24 by hand, but unfortunately this didn't fix the problem, Is there a kernel patch or some other solutions?

---

### Post by thomasaaron on 2008-01-25
It is a problem with your DSDT tables. We've tried changing the DSDT tables with only a small amount of success. We are working closely with Canonical to ensure that Hardy (the next version of Ubuntu) is compatible with those tables.

---

### Post by 6174 on 2008-01-25
> **thomasaaron said:**
> It is a problem with your DSDT tables. We've tried changing the DSDT tables with only a small amount of success. We are working closely with Canonical to ensure that Hardy (the next version of Ubuntu) is compatible with those tables.

Just to clarify, does this imply that moving to Hardy would improve the situation? Or is the issue still being worked on for Hardy with the expectation that it will be resolved prior to Hardy's release?

---

### Post by badbull on 2008-01-26
well, i think with the new kernel something changed. the problem appears not that often like it does with the old kernel.
so we have to wait for the stable release of hardy and hope there is a fix in it.

---

### Post by impact on 2008-01-29
Another MSI owner here with the same problem. I tried Hardy alpha and the issue is still there.

There are however some bugs filled at the kernel bugzilla about malfunctioning battery and power management, hopefully this ca be fixed.

[http://bugzilla.kernel.org/show_bug.cgi?id=9341](http://bugzilla.kernel.org/show_bug.cgi?id=9341)
[http://bugzilla.kernel.org/show_bug.cgi?id=9823](http://bugzilla.kernel.org/show_bug.cgi?id=9823)

---

### Post by badbull on 2008-01-30
thanks for the links...i tried the patch from the first link.
i get a little improvement of the problem. the battery capacity returns often still wrong values, but "acpi -V" mostly returns right AC Adapter values. (but still not all the time)

btw: the system76 driver don't work for me with the new kernel. the problem with the brightness/darkness while using the fn keys returns.

UPDATE: It works for some hours...but now its going to be mad again. it seems like all fixes still don't work.

UPDATE2: oops, should be better to boot the new kernel ;-)
ok, the patch displays either the right values or 
" Thermal 1: ok, 146.0 degrees C
  AC Adapter 1: off-line". 
so its gonna be a game of luck if its notice that the ac adapter is pluged in or not.

---

### Post by palintheus on 2008-01-30
Here is another bug report related to this issue. It is assigned to the Ubuntu Kernel Team and marked Confirmed, it has no Importance listed however.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147560](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/147560)

---

### Post by alberto.ceccherini on 2008-02-03
hi...
i'm quite new in ubuntu, i've tried to read all the previous posts on this thread, and I'm still not sure this is the right place to report my experience.

I'm using Gutsy on my old toshiba satellite and i haven't had problems with power management until 2 o3 weeks ago.

Since then (i don't remember if due to an update) my power management seems to go crazy. When AC is plugged in the system seems to recognize it and message says the battery is charging... but after some times the system goes down without any message and when I get it on again I can see the battery is completely  low.

So it seems not to charging even if display the contrary. I've also windows on my laptop.. (even if I haven't started it for a long period :-) ) and it works fine...  

Any Idea on how to solve it ... or someone to ask for suggestions?
Thanks very much
Alberto

---

### Post by impact on 2008-02-03
This is not the best place to ask, you might want to try [http://ubuntuforums.org/forumdisplay.php?f=135](http://ubuntuforums.org/forumdisplay.php?f=135) or [https://bugs.launchpad.net/](https://bugs.launchpad.net/) .

---

### Post by ryjo on 2008-02-03
To follow up on my original post on this issue (Gutsy on new Darter):
(1) I am getting messages that my battery has low capacity and may be bad.  Since this is a new machine, I am thinking that this is likely due to the faulty power management software, rather than the battery.
(2) As previously noted in this thread, I too have encountered sudden shut-down while I have been in the middle of working with others on what should be ample battery power.  This has resulted in loss of work-in-progress.
(3) I don't know if this is power mgt related, but if I close the lid and return to the computer later to resume work (plugged in to AC the whole time), my screen will go black for about a second at a time...pretty disruptive.

> **ryjo said:**
> Yes. The system is completely updated, I am running version 2.1.3 of the System76 Driver, and I installed the System 76 drivers after the system was completely updated.  With this software status and with AC plugged in, the current primary symptom is that power management bounces between thinking it is on AC with highly variable estimates of battery state, and thinking it is on battery and unable to determine battery state.

---

### Post by impact on 2008-02-03
3) sounds extremely familiar to me. I had to set "do nothing when the lid is closed" in gnome power manager otherwise I'd experience the same thing.

---

### Post by jdb on 2008-02-03
I've been using Ubuntu for years but just got my first laptop, a darter, last month.
I've been having all the problems noted here, blinking screen etc.
Under Systems->Preferences->Power Management I set screen brightness to 100% for AC power & 0% dimming for battery power.
That at least stopped the changes in screen intensity.

I noticed something else strange.
If you right click on the battery icon in the upper panel there is an
option for power history.
You can select graphs of several parameters.
The histories are bizarre, but what is strange is that sometimes they change to reasonable values, not only the present values, but the past values too.
The "history" changes.
It's like the data is randomly gathered from different places.

I know nothing about ACPI or DSDT tables but have started reading up on them.  I sure hope someone finds something before I do because it looks like it's going to take a while to come up to speed.

John Bowman

---

### Post by badbull on 2008-02-06
is the problem fixed in fedora? i tried the fedora 8 liveCD for about an hour and had no problems so far. (the live cd runs with kernel 2.6.23)
have someone tested an fedora installation?

---

### Post by reh4c on 2008-02-07
Hello.  Darter2 power management seems to work much better with Fedora 8.  Also, desktop effects work "out of the box" with a simple click of the mouse.  I'd have to lean towards F8 over Ubuntu in most ways on the Daru2.  I tried F9 alpha last night, but it's certainly unstable...as would be expected.  It will be an exciting period over the next few months with Ubunut 8.04 and Fedora 9 coming out in April.

---

### Post by jdb on 2008-02-08
I'm using the script below to keep an eye on things:

one=`cat /proc/acpi/battery/BAT1/info | grep "design capacity:"`
two="design capacity:         4800 mAh"
if [ "$one" !=  "$two" ]
   then
   cat /proc/acpi/battery/BAT1/info
   cat /proc/acpi/battery/BAT1/state
   acpi -V
fi

When things go haywire the design capacity changes to random values, that should never happen.

I've tried  /etc/init.d/acpid restart 
   and
/etc/init.d/acpi-support stop  /etc/init.d/acpi-support start

That worked once but hasn't on subsequent tries.

The only thing I've found that consistently squares things up is going into & out of suspend.
After the suspend a "cat /proc/acpi/battery/BAT1/..." can take up to 30 seconds to complete but acpi is stable.

Go to
[http://h1.ripway.com/jdbowman/acpi/index.html]("http://h1.ripway.com/jdbowman/acpi/index.html")
to see a snapshot of the voltage history, the battery was on charger the whole time, the on/off charge events are false.
It normalizes after going in & out of suspend.

I compiled the 2.6.24 kernel & tried booting to that.
I lost wifi, sound & video but wanted to see how acpi worked.
It was a lot more stable, it only went bananas for several minutes during a 2 hour period and then corrected itself.

In 2.6.22 it usually goes crazy after about a half hour & almost never corrects itself.

I am trying to figure out what going in & out of suspend does to correct it but haven't gotten too far yet.

John Bowman

---

### Post by jdb on 2008-02-15
I loaded 64 bit Ubuntu & it looks like it's back to square one.
Suspend works well, but it no longer fixes the acpi problem.

On 32 bit Ubuntu going into & out of suspend would cause access to /proc/acpi/battery/BAT1/info & /proc/acpi/battery/BAT1/state to become very sluggish, but they would then return good results until the next reboot.

On 64 bit Ubuntu nothing changes when going into & out of suspend.

Once acpi starts malfunctioning I get results like this:
######################
cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         53266 mAh
last full capacity:      49170 mAh
battery technology:      rechargeable
design voltage:          31545 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            MS-1221

serial number:           

battery type:            LION

OEM info:                MSI Corp.
##################
cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      unknown
present voltage:         10000 mV
##############
acpi -V
    Battery 1: charging, 0%, 21:20:00 until charged
    Thermal 1: ok, 210.0 degrees C
  AC Adapter 1: off-line
###################

These results would indicate that:
the battery has a design capacity of 53 Amp Hours (I wish)
the battery has a design voltage of 31 Volts (really 14.8 )
the present voltage is 10 volts (really fully charged)
the temperature is 210 C (410 F, I don't think so)
the AC Adaptor is off-line (it isn't)

All this doesn't hurt anything because the actual battery charging is handled by a processor built into the battery pack.
It does make it awfully hard to know when to shut down when I'm running on batteries.

I'm still trying to figure out what going into & out of suspend did on the 32 bit Ubuntu but have not made much headway yet.

John Bowman

---

### Post by badbull on 2008-02-22
some bugs seems to be fixed in the last ubuntu 8.04 version. it detects the ac adapter right and the battery state looks good too. but the "design capacity" and "last full capacity" are still wrong. is there a way to set them manualy? 
the gnome-power-manager also do some wrong things but i don't know why.

---

### Post by leptons on 2008-02-22
I have been having some related issue ever since i got this laptop (darter2)

Whenever I have my battery and AC power plugin at the same time, when the gnome-power-manager misread the current status, the screen would just turn blank (as if the lid is closed). I had to use alt-ctrl-backspace to log out and then back to fix it. So, has there been a solution to this problem other than turning off blanking screen when the lid is closed?

---

### Post by thomasaaron on 2008-02-22
Not yet. We have sent the computer to an engineer at Canonical. They are helping us figure out a) how to fix it; and b) how to implement that change into Hardy.

---

### Post by jdb on 2008-02-23
I've been looking for how /proc/acpi/battery gets populated & guessed it might be from the sbs (smart battery system) module.
I peppered it with printk statements & noticed it got loaded & initialized but never did anything else.
It looks liked the timer should be calling it but I guess not.

I blacklisted sbs & rebooted and acpi is working much better now.
It did go crazy once, but going in & out of suspend fixed it.
Other than that it's been running about 6 hours with no problems.
It never made it much more than a half hour before.

I still haven't found what populates /proc/acpi/battery.

Probably as soon as I post this things will go nuts again.

#### update #####

It didn't go nuts as soon as I posted, but it did after a few more hours.
Suspend didn't fix it, this is so random it's hard to tell what affects it.

I blacklisted the battery module & rebooted.
There were no entries in /proc/acpi/battery so 'battery' is probably  the module that builds it.
I'm going to spend some time analyzing that module but don't know if it will get me anywhere.

I sure hope that engineer from Canonical can get to the bottom of this.

#### another update #####

When I boot with the battery module blacklisted, the "Power Manager 2.20.0" comes up in  the desktop mode.
When I modpobe battery to start it manually the "Power Manager 2.20.0" stays in the desktop mode but the /proc/acpi/battery files get built & are updated.
So far there have been no discrepancies in the /proc/acpi/battery files, but until it runs clean for at least 12 hours I won't be sure.
If it continues to run clean I'm thinking there may be something in "Power Manager 2.20.0" that is causing problems.

John Bowman

---

### Post by impact on 2008-02-24
JDB: try using ec_intr=0 as a boot option. It seems to solve the power management problems for me.

---

### Post by jdb on 2008-02-24
impact, it seems to solve the problem for me also.

Thanks,

John Bowman

---

### Post by gaussian on 2008-02-25
> **jdb said:**
> impact, it seems to solve the problem for me also.

Thanks,

John Bowman

+1  (on a 32-bit Gutsy on a DARU2)

---

### Post by badbull on 2008-02-25
looks like this don't work for me. I added it to the grub default options but still getting wrong data from the battery.
maybe it is caused by my newer kernel. i'll try the older one, hope it works with it.

[update]
the old kernel works better...

---

### Post by theologian aaron on 2008-02-25
adding ec_intr=0 did seem to do the trick for me.
 My darter actually displayed the power status all the way until it warned me and shut itself down.  Fantastic!

Now, can you explain why this is?

---

### Post by ackey on 2008-02-25
I tried it, but it did not improve things.  Can someone clarify what else is required with this boot option?  I'm using kubuntu, so I'm not using the gnome power manager.  Does that matter?

---

### Post by jdb on 2008-02-25
ackey:

This was my /boot/grub/menu.lst entry before:

kernel	/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet

This was after the change:

kernel	/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ec_intr=0 ro quiet

The root=  entry will probably be different on yours, don't change that, just add ec_intr=0
If you make any typos in ec_intr=0 it won't complain, but it won't fix the problem either.


theologin:

I'm not sure what this does but I'm guessing it disables interrupts from the battery.

Maybe impact can shed some light.

jdb

---

### Post by badbull on 2008-02-26
better add it to the default option line in the menu.lst
it should look like this. 
```
# defoptions=quiet splash ec_intr=0
``` (the # is required)

this will keep the setting after a grub/kernel update.
after adding run ```
sudo update-grub
```

---

### Post by thomasaaron on 2008-02-26
For those of you who have had success with the ec_intr=0 kernel option,
are you using 32-bit or 64-bit Ubuntu?

---

### Post by gaussian on 2008-02-26
> **thomasaaron said:**
> For those of you who have had success with the ec_intr=0 kernel option,
are you using 32-bit or 64-bit Ubuntu?

32-bit here and no power management problems so far with ec_intr=0.

---

### Post by jdb on 2008-02-26
64 bit and it hasn't even hiccuped since  since I set the boot option.

Everything works as it should & I get a low battery warning when it's low.

I've tried it in both gnome & xfce4 desktops.

John

---

### Post by theologian aaron on 2008-02-26
it was working for awhile, but I've now started having issues again.

EDIT:

Scratch that.  It seems that ec_intr=0 had removed itself from the bootloader while I was sleeping.  I replaced it and am back on track.  Does anyone know a reason why it would have been removed?

Edit2:

I've added it to menu.lst as badbull has suggested and we'll see what happens.  (Note:  to do that I did "sudo gedit /boot/grub/menu.lst" and changed the offending line)

---

### Post by thomasaaron on 2008-02-26
OK. I've got it running on the shop DarU2.

I'll let you know if it's still ticking tomorrow.

---

### Post by thomasaaron on 2008-02-27
Well, that fix is working flawlessly for 64-bit Ubuntu.
I let it run all night. It just won't die!

---

### Post by thomasaaron on 2008-02-27
ackey,

I'm pretty confident the fix will work for you. Please post the output of...

cat /boot/grub/menu.lst

...after you enter the kernel option.

---

### Post by impact on 2008-02-27
I found some explanation on the MSI megawiki:

[http://megawiki.org/wiki/MSILaptopDriver](http://megawiki.org/wiki/MSILaptopDriver)

[i]It's like this: communication with the ACPI embedded controller can be
done either interrupt-based or polling-based. The embedded controller
is responsible for all that small housekeeping stuff that needs to be
done on a laptop: battery management, fan management, brightness
management, power plug management and other stuff. Since 2.6.18 the
interrupt-based mode is the default (same as passing
ec_intr=1). Before that the polling mode was used by
default. Interrupt-based mode is cleaner in some way. However, for
those special commands the MSI EC knows that we use for brightness
control it doesn't trigger interrupts. Thus, when issueing those
commands we have to temporarily switch to polling mode and than back
to interrupt mode. 
[/i]

I guess it's the same with battery status - the embedded controller doesn't trigger interrupts. In short - the BIOS in MSI laptops is less than perfect. ec_intr=0 is a workaround that disables interrupt-based mode.

Meanwhile, kernel developers have come to the same conclusion;

[http://bugzilla.kernel.org/show_bug.cgi?id=9823](http://bugzilla.kernel.org/show_bug.cgi?id=9823)

   [i]According to the above analysis it seems that the bug is related with EC and
there are two possible reasons .
   a. the broken EC firmware ( related with BIOS).
   b. Uncorrect EC I/O access (related with EC driver)
   Maybe a is the mainly root cause.
[/i]


Some MSI owners are now trying to alert MSI and hopefully get them to figure it out and release a fixed BIOS, but it's really hard, because MSI isn't System76 and seem to not care much about Linux, because "it works in Windows".

---

### Post by pavel_987 on 2008-02-27
On the site posted by impact ([http://megawiki.org/wiki/MSILaptopDriver](http://megawiki.org/wiki/MSILaptopDriver)) the last line reads "f you are running kernel 2.6.20 or 2.6.21, this is resolved by passing ec_intr=0 kernel parameter. This bug is reportedly fixed in kernel 2.6.22." Aren't we all running 2.6.22, shouldn't this have no effect?

Also, what's the success of people running with this boot option on newer kernels? I think I read that badbull had some problems. I'm a fan of 2.6.24 and it's built-in iwlwifi driver.

---

### Post by theologian aaron on 2008-02-27
I'm running 2.6.22-14 with the fix (done in menu.lst) and have only had some minor problems, mostly when going to and from battery power.

---

### Post by vacula on 2008-02-28
I'm running 2.6.24 on latest gentoo, I'm using custom acpi from here - [http://planet76.com/repositories/system76-driver-2.1.3.deb](http://planet76.com/repositories/system76-driver-2.1.3.deb) and I'm booting with ec_intr=0 param.

Still no success, no suspend2ram at all - laptop just hangs in some undefined state, and hibernate works just one time. No possibility to hibernate two or more times one by one. Battery still goes crazy in few minutes.

---

### Post by badbull on 2008-02-28
@pavel_987: i had problems with my selfbuild kernel...maybe i did some mistakes on configuration. I'm now testing ubuntu 8.04 and it looks like it  works with the fix, too.
I haven't test it for a long time, but i think it also works with the newer kernel. I'm going to test it for a longer time.

---

### Post by gaussian on 2008-02-28
> **vacula said:**
> I'm running 2.6.24 on latest gentoo, I'm using custom acpi from here - [http://planet76.com/repositories/system76-driver-2.1.3.deb](http://planet76.com/repositories/system76-driver-2.1.3.deb) and I'm booting with ec_intr=0 param.

Still no success, no suspend2ram at all - laptop just hangs in some undefined state, and hibernate works just one time. No possibility to hibernate two or more times one by one. Battery still goes crazy in few minutes.

I don't think anyone is claiming that this fixes waking up from suspend2ram, just the battery monitor situation. From other threads I gather there is hope for suspend2ram in 8.04, at least in 64-bit side and hopefully in 32-bit (I don't want to reinstall, just apt-get dist-upgrade). Someone who knows more, please fill in.

---

### Post by jdb on 2008-02-28
I booted Ubuntu on a 2.6.24 kernel this morning.
ec_intr=0 does NOT fix the acpi problem in 2.6.24.

jdb

---

### Post by thomasaaron on 2008-02-28
jdb,

I've been running my shop daru2 all day on Hardy with the ec_intr=0 option and it is not acting up.

The battery monitor applet doesn't look right. It LOOKS like it is on A/C when it is on battery and vice versa. But when you place your cursor over it, it reports a/c or battery power correctly. However, it gives incorrect readings.

That said, I've been running it for hours  and hours and it hasn't really flaked out and started dimming the screen, etc...

What results are you getting?

---

### Post by jdb on 2008-02-28
I just loaded HardyHeron & have been running on it for about an hour.
So far it's worked great, no acpi problems!!

I'm really impressed by the font rendering in Hardy, it really looks good!

jdb

---

### Post by impact on 2008-02-28
> **pavel_987 said:**
> On the site posted by impact ([http://megawiki.org/wiki/MSILaptopDriver](http://megawiki.org/wiki/MSILaptopDriver)) the last line reads "f you are running kernel 2.6.20 or 2.6.21, this is resolved by passing ec_intr=0 kernel parameter. This bug is reportedly fixed in kernel 2.6.22." Aren't we all running 2.6.22, shouldn't this have no effect?




The bug mentioned on that page is related to something else (brightness control on MSI laptops and some other stuff). I just linked it because it explains what the ec_intr=0 parameter does. 

Also, ec_intr=0 is in no way related to suspend or hibernate problems and likely won't have any effect on them.

---

### Post by thomasaaron on 2008-02-28
Our shop DarU2 suspends fine with the ec_intr=0 option.

---

### Post by gaussian on 2008-02-28
> **thomasaaron said:**
> Our shop DarU2 suspends fine with the ec_intr=0 option.

But this is "standby" as opposed to "mem"? Or does something (64-bit and/or Hardy) fix the S3 resume problem?

---

### Post by thomasaaron on 2008-02-28
S1 uses the "mem" designation and it suspends to ram (blinking lights, et al.).
S3 uses the "standby" designation and suspends to disk (more like hibernate; shuts all the way down).

Both work fine with Ubuntu 64-bit on the DarU2. S1 is the preferred method.

Has nothing to do with the ec_intr=0 option. That just fixes the flakey power management.

---

### Post by vacula on 2008-02-28
> **thomasaaron said:**
> 
Both work fine with Ubuntu 64-bit on the DarU2. S1 is the preferred method.

Has nothing to do with the ec_intr=0 option. That just fixes the flakey power management.

Could you please share what changes/patches were applied? i.e. some kernel patches or whatever? Could you please share yours /proc/acpi/dsdt ?

---

### Post by pavel_987 on 2008-02-28
> **thomasaaron said:**
> S1 uses the "mem" designation and it suspends to ram (blinking lights, et al.).
S3 uses the "standby" designation and suspends to disk (more like hibernate; shuts all the way down).

Both work fine with Ubuntu 64-bit on the DarU2. S1 is the preferred method.

Has nothing to do with the ec_intr=0 option. That just fixes the flakey power management.

I thought that S3 was the "suspend to ram", and is the one preferred.
And S4 is hibernate, writes to disk.
S1 just stops the CPU, no blinking lights. But that's just my understanding of it.
([http://en.wikipedia.org/wiki/Acpi](http://en.wikipedia.org/wiki/Acpi))

@vacula, I asked for that once before. That would be really nice of them. In the end I decompiled the DSDT myself using the intel ASL compiler. Here's a guide for Gentoo, [http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems) . It shouldn't be too hard to adopt it to your own distro.

---

### Post by vacula on 2008-02-28
> **pavel_987 said:**
> 
@vacula, I asked for that once before. That would be really nice of them. In the end I decompiled the DSDT myself using the intel ASL compiler. Here's a guide for Gentoo, [http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems) . It shouldn't be too hard to adopt it to your own distro.

Thanks for quick reply, but I already have integrated custom dsdt into mine kernel from this package: [http://planet76.com/repositories/system76-driver-2.1.3.deb](http://planet76.com/repositories/system76-driver-2.1.3.deb) - it's latest available drivers pack I was able to find. My acpi contain no syntax errors as well as warnings. So, I guess, probably Hardy contain some custom patches/acpi which is not at system76 repository. I will appreciate if anyone will share /proc/acpi/dsdt from Hardy here.

---

### Post by lippman on 2008-02-29
I'm using a Darter Ultra running gutsy.  Using the ec_intr=0 option seems to fix everything for me.  The battery monitor icon is right and the battery readings behave well.

Thanks to everyone writing in this post!  This fix really increases my confidence in the battery life- I'm no longer paranoid about working in the coffee shop.

---

### Post by 6174 on 2008-03-01
I've got a daru2 and the ec_intr=0 does not seem to be a complete fix. For a while it did seem to make everything work, but I had my laptop doing a long background task so I just left it on and plugged into the wall. Now uptime is saying the system has been running about 2.5 days and the screen flashing and incorrect reporting on power status is back.


For reference this is on 64-bit Gutsy with kernel 2.6.22-14 with only ec_intr=0 as a kernel parameter (I removed quiet and splash). I've got version 2.1.3 of the System 76 driver and my system is fully up to date package update wise.

---

### Post by thomasaaron on 2008-03-03
Did the computer suspend?

Also, make sure the kernel option is actually still there? (Do I recall a kernel update coming down the pike? If so, it could've updated menu.lst.)

---

### Post by 6174 on 2008-03-03
> **thomasaaron said:**
> Did the computer suspend?

Also, make sure the kernel option is actually still there? (Do I recall a kernel update coming down the pike? If so, it could've updated menu.lst.)

It shouldn't have suspended, all I did was close the lid and let it keep running. I also did verify that the kernel option is still in the menu.lst

I'm now sitting on about 50 hours of uptime and the problem hasn't resurfaced. I'm not sure what caused it previously but from what I've seen I'm not convinced the ec_intr=0 is a complete fix. It certainly makes things much better and may be a 95% fix but there might still be something else (which unfortunately I can't pin down to any helpful degree).

---

### Post by thomasaaron on 2008-03-04
OK. Well that's good.

You might want to go to System > Preferences > Power Management and make sure it isn't set to suspend when the lid is closed.

---

### Post by 6174 on 2008-03-05
> **thomasaaron said:**
> OK. Well that's good.

You might want to go to System > Preferences > Power Management and make sure it isn't set to suspend when the lid is closed.

It was (and is) set to blank screen. After thinking about it for a while, I'm pretty sure it didn't suspend because I had an active network connection the entire time (IRC). I'm not positive but I'm under the impression that suspend would have cut the wireless network connection if it had actually suspended.

Either way, I still haven't been able to replicate the problem so I don't know how it got into that weird state a few days ago.

---

### Post by thomasaaron on 2008-03-05
OK.

Also, you're right. By default, the wireless modules is unloaded in suspend and hibernate. By default, that is.

---

### Post by reh4c on 2008-04-11
Fix doesn't work on Hardy beta 64-bit with kernel 2.6.24-15.  Same wacky battery meter readings.

---

### Post by thomasaaron on 2008-04-11
Yeah, we're looking at that now.
I guess in Gutsy, the 64-bit kernel was NOT a tickless kernel.
In Hardy it is a tickless kernel. We're thinking that might be the issue.

---

### Post by reh4c on 2008-04-11
> **thomasaaron said:**
> Yeah, we're looking at that now.
I guess in Gutsy, the 64-bit kernel was NOT a tickless kernel.
In Hardy it is a tickless kernel. We're thinking that might be the issue.
Good point.  It's tough to have it all :)

---

### Post by pavel_987 on 2008-04-20
Hey guys. Has anyone been able to solve this problem on Hardy? Or is it still up in the air?

Although on a different system, I played around with the tickless kernel. Disabling and enabling the option. It had no effect on the power management. So I doubt that's the problem. But I could be wrong.

I did notice a few interesting things in dmesg though. I currently don't have a gutsy install, but I was wondering if someone could run ```
dmesg | grep EC
``` for me and tell me their output.

When I run that command on Hardy beta I get
```

[   18.485839] ACPI: EC: Look up EC in DSDT
[   18.494065] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   18.500907] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   18.500911] ACPI: EC: driver started in interrupt mode

```

This suggests that the 'ec_intr' option is ignored and contact with ACPI remains interrupt based instead of polling based. I believe that in the recent kernel versions (.23 to .25 maybe?) they removed the ec_intr option and made it automatic detection. But I'm not sure. When I get more time I'll peek into the source to see what's being done.
Check out:
[http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg09437.html](http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg09437.html)

---

### Post by pavel_987 on 2008-04-20
Sorry for the double post. But I was correct.
ec_intr is no longer a kernel parameter as of 2.6.24

Check out [http://kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fv2.6%2Fpatch-2.6.24.bz2;z=3301](http://kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fv2.6%2Fpatch-2.6.24.bz2;z=3301)

---

### Post by crichell on 2008-04-21
pavel - can you try "force_poll=1" boot parameter. This appears to be the replacement for "ec_intr=0".

---

### Post by jdb on 2008-04-21
[QUOTE=pavel_987;4755650]Sorry for the double post. But I was correct.
ec_intr is no longer a kernel parameter as of 2.6.24

acpi=noirq will put it in the poll mode but it has the side effect of disabling the screen brightness controls.

jdb

---

### Post by pavel_987 on 2008-04-22
The force_poll=1 parameter didn't work for me. Has it worked for anyone else? I dug around the kernel source and didn't really see it as an option. 

Thanks for the suggestion JDB, but I prefer not to loose the screen dimming.

In the end thankfully I did manage to fix the problem, but I'd prefer to do it in a nicer way like a kernel parameter.

Also, does S3 suspend work with Hardy for you guys? I haven't been able to get that to work. The laptop goes to sleep, but fails to come back up.

---

### Post by crichell on 2008-04-22
I'm also experiencing the S3 regression in Hardy.

This [link]("http://lkml.org/lkml/2007/5/4/191") led me to force_poll=1; however, I'm still having the funky battery issue with the option as well.

---

### Post by jdb on 2008-04-22
I just tried suspend & got the same bad results you did.
I normaly just shut my computer down when I'm not using it, a boot does it good every so often :)

If you apt-get or synaptic linux-source-2.6.24 you will get:
/use/src/linux-source-2.6.24.tar.bz2

If you tar xf linux-source-2.6.24.tar.bz2 or double click (or single click if you've set your options like I have) & select extract you will get:
linux-source-2.6.24/Documentation/kernel-parameters.txt

force_poll isn't mentioned but that's where I discovered the acpi boot option.
Except for not being able to dim the screen, power managment works good with the acpi=noirq boot option.

Screen blanking works when the lid is closed or the prerequisite idle time
is reached.
The Power History charts work good also, no erratic bogus values.

jdb

---

### Post by badbull on 2008-04-22
i think the acpi=noirq option works for me, but it disables my brightness control keys. (the option in the gnome-power-manager disappeard a while ago)
is there a workaroud to get the keys working again?

---

### Post by jdb on 2008-04-23
> **badbull said:**
> i think the acpi=noirq option works for me, but it disables my brightness control keys. (the option in the gnome-power-manager disappeard a while ago)
is there a workaroud to get the keys working again?
I found a quick & dirty way of adjusting the brightness, I might play around with this and try to write something a little more eloquent.

To get the current brightness:
cat  /sys/devices/virtual/backlight/acpi_video0/brightness

To change it to something else, 4 for example:
sudo su
echo 4 >  /sys/devices/virtual/backlight/acpi_video0/brightness
exit

jdb

---

### Post by jdb on 2008-04-23
I found one more thing acpi=noirq affects, the "power critically low" interupt is ignored.
The battery just shuts down when the charge gets too low & the laptop goes down like a ton of bricks.

On the other hand, things aren't much better when interupts are enabled.
I have the option set to hibernate since suspend doesn't work.
When the "power critically low" interupt fires, there isn't time for the hibernate  to complete before the battery shuts down.

At least with acpi=noirq set I get an accurate % of charge reading from the battery meter & after 3 hours or so I can start keeping an eye on it.

jdb

---

### Post by badbull on 2008-04-26
the acpi=noirq disables all acpi events. the states in /sys/class/power_supply/ADP1 seems to be wrong or do not change. the states in /proc/acpi/... seems to be right.
the /etc/acpi/video_brighnessdown.sh and /etc/acpi/video_brighnessup.sh don't work. it looks like the only way to change the brighness is to rewrite the /sys/devices/virtual/backlight/acpi_video0/brightness or /sys/class/backlight/acpi_video0/brightness file.
a workaround is maybe usind a script like this to increase
```
#!/bin/bash
value=`cat /sys/class/backlight/acpi_video0/brightness`
let "value += 1"
echo $value
echo $value > /sys/class/backlight/acpi_video0/brightness
```

but i didn't figure out how to start a script by using the fn keys. does someone know how to do this?

---

### Post by jdb on 2008-04-26
> **badbull said:**
> the acpi=noirq disables all acpi events. the states in /sys/class/power_supply/ADP1 seems to be wrong or do not change. the states in /proc/acpi/... seems to be right.
the /etc/acpi/video_brighnessdown.sh and /etc/acpi/video_brighnessup.sh don't work. it looks like the only way to change the brighness is to rewrite the /sys/devices/virtual/backlight/acpi_video0/brightness or /sys/class/backlight/acpi_video0/brightness file.
a workaround is maybe usind a script like this to increase
```
#!/bin/bash
value=`cat /sys/class/backlight/acpi_video0/brightness`
let "value += 1"
echo $value
echo $value > /sys/class/backlight/acpi_video0/brightness
```

but i didn't figure out how to start a script by using the fn keys. does someone know how to do this?
Unfortunately it looks like those keys are handled by acpi, with acpi interupts disabled they don't get handled.
I think I'm going to write a small gtk program with a brightness slider.
I don't want to have to be root to use it so it can't be a script because it will need the suid bit set.

Like you, I'd also like to figure out how to capture those keys but I'm kind of busy on other stuff right now.

If nothing is fixed in a few weeks or so I might spend some time on it.

jdb

---

### Post by badbull on 2008-04-26
could you try "acpi_irq_balance" as boot option? i tryed it for about an hour and everything were fine.

Update: ok, it's going wrong after a reboot...

---

### Post by jdb on 2008-04-26
> **badbull said:**
> could you try "acpi_irq_balance" as boot option? i tryed it for about an hour and everything were fine.
Thanks badbull I'll try that.

BTW, the forum has moved to:

[http://ubuntuforums.org/forumdisplay.php?f=341](http://ubuntuforums.org/forumdisplay.php?f=341)

this is an archive now.

I just discovered it a short time ago.

Very strange.

jdb

---

### Post by jdb on 2008-04-26
I tried the acpi_irq_balance option & I thought it was going to be OK
but then it went crazy again.

It's hard to tell when this problem is fixed because sometimes it goes crazy right away and sometimes it works great for hours before it goes crazy.

I've never seen it go crazy with acpi=noirq, we just need to find a good way to address the brightness control problem.

jdb

---

### Post by laserline on 2008-04-27
Hi Guys,

Because the forum was archived, I posted a couple ago a new Suspend problem in with Daru2 and Hardy.

Please take a look here and tell see if you experience the same (look at my last post with the laptop reviving itself automagically - wierd): [http://ubuntuforums.org/showthread.php?t=764970](http://ubuntuforums.org/showthread.php?t=764970)

Maybe we could consolidate both threads as this one is in the Archives.

Thanks,
Idan.

---

### Post by badbull on 2008-04-27
i think the suspend problem is caused by another error as the power management problem.
but maybe we should open a new tread for the power management problem in hardy.

at the moment i trying some kernel boot options. but without much success :-(

---

### Post by badbull on 2008-04-27
hat no luck with the kernel options...

but i fugure out, that the acpi still blocks the fn key bindings. xev gives no output and programms like xbindkeys can't handle the key press.
maybe not the biggest problem, you can set it to F4 and F5 without using the Fn key.

as a workaround you can make the brighness control file human writeable
add this in the /etc/rc.local
```
chmod 666 /sys/class/backlight/acpi_video0/brightness
```
install xbindkeys

create up and down scripts as i described before

create a ~/.xbindkeysrc like this (change the path to the scripts)
```
# brighness down = F4
"<down script>"
    m:0x0 + c:70
    F4
#brighness up = F5
"<up srcipt>"
    m:0x0 + c:71
    F5
```
and add xbindkeys to gnome startup

for brighness changing on plug/unplug the ac adapter you can use a python script like this
```

#!/usr/bin/evn python
import time, os

laststate = ""

while True:
	f = open("/proc/acpi/ac_adapter/ADP1/state")
	state = f.readline()
	if state.find("off-line") == -1 and laststate != "up":
		print "Power Up"
		os.system("echo 8 > /sys/devices/virtual/backlight/acpi_video0/brightness")
		laststate = "up"
	if state.find("on-line") == -1 and laststate != "down":
		print "Power Down"
		os.system("echo 0 > /sys/devices/virtual/backlight/acpi_video0/brightness")
		laststate = "down"
	f.close()
	time.sleep(10)

```

but all these is mostly untested ;-)

---

### Post by laserline on 2008-04-27
Hi Badbull,

I searched the forums and there is more breakage to suspend and acpi caused by hardy.
I even read the changelogs from 2.6.22 to 2.6.25 and searched for the ec_intr and force_poll parameters and only found something about it on 2.6.22

What are the odds that this problem is kernel related and an updated kernel (2.6.24-17) should be released.

Better yet, what are the odds of System76 releasing a driver that will make the daru2 usable with Hardy. In addition, I saw they are selling daru2's pre-installed with Hardy, and was wondering why there isn't an official message from them.

Meanwhile, I'm seriously thinking about downgrading (as in clean install) to Gutsy... (that would be unpleasant because I've already customized Hardy).

Idan.

---

### Post by badbull on 2008-04-27
i read something about kernel options these days and looked in the source code of the acpi/ec.c file. but i think there is nothing that replace the ec_intr funktion of the 2.6.22 kernel.
currently i'm using gutsy and hardy as dualboot, but hardy is still for testing. i have also another problem im hardy. on battery power my harddisk is going to sleep and wakes up neary every second. have someone of you the same problem?

---

### Post by laserline on 2008-04-27
Hi Badbull

1. Please tell me what you are doing to test this, and I'll post my results.

2. Dualboot as in 2 root / partitions and one grub in MBR ?

Idan.

---

### Post by badbull on 2008-04-27
yes to root partitions in one grub.
i didn't test much on the harddisk bug, a change of the spinoff time with hdparm didn't work. maybe it's just a bug (or wrong config entry) on my system. if you don't hear the harddisk starting very often or typing something in the firefox address line takes a while you don't have that bug.

---

### Post by laserline on 2008-04-27
I'll keep an eye (ear) on it  ;)

---

### Post by crichell on 2008-04-29
One of Ubuntu's ACPI developers has the daru2 in hand and we're working on a solution that doesn't effect hot keys. We're also working on S3 suspend and hope to have a solution soon.

"acpi=noirq" is a good temporary fix. This option fixes battery indication; however, it does disable the brightness hot keys.

To apply the workaround open a terminal and paste in the following command:

```
sudo gedit /boot/grub/menu.lst
```

At the end of the file you will see "## ## End Default Options ##". Add "acpi=noirq" to the next kernel line so that the line looks like this:

```
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=14724fbc-a01a-436a-82a3-93a6a0c1e1c8 ro quiet splash acpi=noirq
```

Save and close the file then Reboot.

I'll keep you posted as we work on a permanent fix.

---

### Post by laserline on 2008-04-29
Thanks a lot.

[Edit:] Suspend doesn't work with the temporary fix, right ?

Idan.

---

### Post by pavel_987 on 2008-04-30
Suspend is a different problem. It does not work with or without the fix on hardy. My educated guess is that suspend not working was a kernel regression starting from 2.6.23. 2.6.22 works, 2.6.23, 2.6.24, 2.6.25 don't. Yes I've tested all of them. But not quite done yet, maybe I'll find the culprit.

What I did for power management was directly edited the kernel source and fixed the issue. You just need to make sure that EC starts in poll mode instead of interrupt mode. I'm working with 2.6.25. So I went into [kernel source]/drivers/acpi/ec.c and commented out lines 542-545 that read ```
		if (printk_ratelimit())
			pr_info(PREFIX "non-query interrupt received,"
				" switching to interrupt mode\n");
		set_bit(EC_FLAGS_GPE_MODE, &ec->flags);
``` in function acpi_ec_gpe_handler 
and added ```
test_bit(EC_FLAGS_GPE_MODE, &ec->flags);
``` on line 804 between ```
pr_info(PREFIX "GPE = 0x%lx, I/O: command/status = 0x%lx, data = 0x%lx\n",
			  ec->gpe, ec->command_addr, ec->data_addr);
	pr_info(PREFIX "driver started in %s mode\n",
		(test_bit(EC_FLAGS_GPE_MODE, &ec->flags))?"interrupt":"poll");
``` in function acpi_ec_add

Then you can just recompile and run the new kernel. To verify that it works ```
 dmesg | grep EC 
``` will tell you that the EC has started in Poll mode.

In fear of people messing up their computer, I do NOT recommend doing this. Do it at your own discretion.

---

### Post by zzottt on 2008-04-30
Thanks :KS crichell!

I think the acpi=noirq flag might have fixed my Suspend problems
I will try this for a while and see if that is truly the case

:popcorn:

---

### Post by laserline on 2008-05-01
```
acpi=noirq
``` doesn't fix the Suspend problem on the daru2.

Idan

---

### Post by badbull on 2008-05-01
right, there is still no fix for the suspend problem, but maybe for the battery bug.
i made the adjustments pavel_987 post before and build a .deb package. it looks like it works for me. if someone want to test it please send me a personal message.

---

### Post by nealmcb on 2008-05-01
Carl, I don't see a ## ## End Default Options ## in menu.lst.  I'll try putting it on the # defoptions= line like we did with ec_intr.

---

### Post by ceminino on 2008-06-12
still no news on a way to have stand by?

---

### Post by ceminino on 2008-06-17
Is anyone having shutdowns because of heat? It happens either in Poll of interrupt mode of the EC when the cpu is on high load. This is really annoying. I have the T7300 cpu. The worst is that just watching some stuff in flash can cause this overheating. Any solutions?

---

### Post by nealmcb on 2008-06-17
Ceminino, how would we know if it was heat-related?

---

### Post by ceminino on 2008-06-17
Because when monitoring the temperature of the cpu, it comes around 90 degrees, at that point the hardware failsafe comes in action and shutdowns the computer.

---

### Post by jdb on 2008-06-20
> **ceminino said:**
> Because when monitoring the temperature of the cpu, it comes around 90 degrees, at that point the hardware failsafe comes in action and shutdowns the computer.

My daru2 has never shut down but I have seen temps in the 80s when it's doing something like compiling the kernel.
I've never used mine in a room warmer than about 25, what is the room temp when yours overheats ????

jdb

---

### Post by nealmcb on 2008-06-20
I'll add that at least one way to get cpu temperatures is to "apt-get install lm-sensors sensors-applet"
and run that "hardware sensors module" in the panel.

.... which I just did because the timing of your question is uncanny.  My fan was blowing like crazy this morning, then the power suddenly cut out.  So mine likely overheated when I was playing with compiz and enabled "cube gears", on top of all the firefox stuff I had running....

This happened to me once before, back in the fall when the acpi was totally broken, and I had hoped that the problem was just that some interrupt was being lost.  But I'm running a daru2 with hardy 64 and acpi=noirq and it still happened.

What can we do to fix this?  Is there some better fan management, or some cpu auto-scaling that can kick in when the temp gets really high?

I don't see any access to the fan statistics on the daru2 - are they available?

---

### Post by jdb on 2008-06-20
> **nealmcb said:**
> I'll add that at least one way to get cpu temperatures is to "apt-get install lm-sensors sensors-applet"
and run that "hardware sensors module" in the panel.

.... which I just did because the timing of your question is uncanny.  My fan was blowing like crazy this morning, then the power suddenly cut out.  So mine likely overheated when I was playing with compiz and enabled "cube gears", on top of all the firefox stuff I had running....

This happened to me once before, back in the fall when the acpi was totally broken, and I had hoped that the problem was just that some interrupt was being lost.  But I'm running a daru2 with hardy 64 and acpi=noirq and it still happened.

What can we do to fix this?  Is there some better fan management, or some cpu auto-scaling that can kick in when the temp gets really high?

I don't see any access to the fan statistics on the daru2 - are they available?

When the fan is blowing hard and the CPU is heating up it's because it is really working hard :)
Most applications don't work it anywhere near hard enough to do that.
Large compiles, like compiling the kernel will heat it up.
Another common thing that heats it up is a program bug that results in an unintended continuous loop in the code.
That is what most likely happened in compiz.
I had the 64 bit flash player get caught in a loop like that a couple times, it might be fixed now, but that's one of the reasons I went back to 32 bit.

jdb

---

### Post by nealmcb on 2008-06-24
I think a properly working system must have ways to avoid shutting down just because some application goes into a loop.  So something needs fixing here.

I installed the "sensord" program to log temperatures.  And I did a "sudo modprobe coretemp" to load a module used by sensord.

This leads me to see various other possible pieces to the puzzle.  One thing is a surprising difference between what temperature acpi reports at

  /proc/acpi/thermal_zone/THRM/temperature

and what the coretemp module says for the two cores (these are in millidegrees, so divide by 1000):

 /sys/devices/platform/coretemp.0/temp1_input
 /sys/devices/platform/coretemp.1/temp1_input

They are different by between 8 and 11 degrees C.  E.g.:  

$ cat /sys/devices/platform/coretemp.0/temp1_input  /sys/devices/platform/coretemp.1/temp1_input /proc/acpi/thermal_zone/THRM/temperature
49000
51000
temperature:             61 C

Somehow it seems that even if they are measuring different things, the cores would hotter than other parts of the cpu.  Is there a bug in the calibration or calculations?

A possible approach to resolving this would be to change the trip point.  But I know very little about such things, other than noticing this:

$ more /proc/acpi/thermal_zone/THRM/trip_points 
critical (S5):           100 C

For those that are willing to push the limits, below is a simple way to max out the cpu.
Of course this may crash your system, or melt down your computer and destroy your only copy of your new great American novel.   But don't blame me if it does - you have been warned....  But again, I expect my computers to be able to do this sort of thing safely - people max out their CPUs by encoding video and trying to break crypto keys all the time....

In a terminal pipe an endless stream of "y" lines into the sha1 hash calculator:

 $ yes | sha1sum

Doing that in two terminals uses both cpus....
Use cntl-c to kill them.

At any rate, some more informed info on all of this would be welcomed.

---

### Post by jdb on 2008-06-24
I just ran both processors on my Daru2 up to 100% & they only got to 70 degrees centagrade.
I stated previously that the got into the eighties but I was going from memory then & doing a mental conversion from Fahrenheit, I usually run sensors with the -f option.
I have never had it shut down on me.

Here is a screen shot:

[temperature of CPUs @ 100%]("http://h1.ripway.com/jdbowman/acpi/index.html")

jdb

---

### Post by jdb on 2008-06-24
The updater just pushed me a new kernel image (2.6.24-19.34 headers).
When they send a new one I always recompile my kernel & modules to include a couple of hacks.
I just did that & the highest core temp I saw was 79 centigrade during the kernel compile and
86 centigrade during the module compile.
It stayed around 80 centigrade plus or minus a few degrees for most of both compiles.
I guess compiling is harder work than a do nothing loop :)
The kernel compile took 6 minutes 42 seconds, the module compile took 35 minutes 34 seconds.
The air blowing out of the right hand vent was pretty warm.

jdb

---

### Post by nealmcb on 2008-06-24
Thanks, jdb - seems like mine is running a lot hotter than yours.  But what temps do you see in

 /proc/acpi/thermal_zone/THRM/temperature

compared to the output of "sensors"?

And what do others see?  Tom?

---

### Post by jdb on 2008-06-24
> **nealmcb said:**
> Thanks, jdb - seems like mine is running a lot hotter than yours.  But what temps do you see in

 /proc/acpi/thermal_zone/THRM/temperature

compared to the output of "sensors"?

And what do others see?  Tom?

************** Idle:

18:15:14 /proc/acpi/thermal_zone/THRM cat temperature 
temperature:             53 C

18:15:21 /proc/acpi/thermal_zone/THRM sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48.0°C  (crit = +100.0°C)                  


************* A do nothing loop on each processor:

18:19:43 /proc/acpi/thermal_zone/THRM cat temperature 
temperature:             75 C

18:20:32 /proc/acpi/thermal_zone/THRM sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +72.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +74.0°C  (crit = +100.0°C)                  


jdb

---

### Post by leptons on 2008-06-28
Just wondering... what's the news on the temporary fix for the battery problem? what about the lid-closing-screen-blanking problem (the computer keeps thinking the lid is closed while it isn't) in daru2? does the temporary fix fixes the lid problem?

---

### Post by jdb on 2008-06-28
> **leptons said:**
> Just wondering... what's the news on the temporary fix for the battery problem? what about the lid-closing-screen-blanking problem (the computer keeps thinking the lid is closed while it isn't) in daru2? does the temporary fix fixes the lid problem?

I've don't remember ever seeing the lid closing problem.
I'm running 32 bit Hardy & xubuntu on a Daru2.

If you use the kernel option acpi=noirq all the battery problems go away.
It may even fix the lid closing problem.
It does cause the fn-f4 & fn-f5 keys not to control the screen brightness but you can use xbacklight instead.

jdb

---

### Post by bkloppenborg on 2008-07-08
I'm on a MSI MS-1719 that is afflicted by the same problem as the Daru2.  Today I tried to use my external monitor using the FN+F2 key combination but it didn't work.  Could this be due to the acpi=noirq option I added to my kernel's parameter list?  Anyone have an idea for a workaround?  I use nvidia-glx-new drivers.

---

