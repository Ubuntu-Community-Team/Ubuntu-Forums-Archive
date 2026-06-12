---
title: "Sys76 thoughts on Lucid Lynx Alpha 3"
date: 2010-03-08
forum: System76 Support
---

### Post by samalex on 2010-03-08
This is to the System76 folks or anyone else who's test driven Ubuntu 10.04 on a Sys76 system (excluding VirtualBox, VmWare, etc).

I'm planning on doing a clean install of Lucid Lynx when it's released next month, but I'm curious to see if System76 has tried it on their systems and when it's released if they'll have driver support for the PanP5.  Also any thoughts on it thus far?  

I love the new Light theme and I'm really anxious to try out the Ubuntu One Music Store.  Also I've read articles saying it boots in 10 seconds or less on some systems, which would be nice to see.  

For me I hope it allows the HDMI port to work and possibly the modem, though I'm not holding my breath on that one.  Also I've found some minor bugs with Gnome that I hope will be fixed on 10.04.

Anyway, just curious... Take care,

Sam

---

### Post by HotShotDJ on 2010-03-08
Hi, Sam --

I've tried Alpha 3 -- I installed it on a 40 GIG "testing" partition.

[LIST=1]
[*]Power Management is STILL broken -- and it is worse than in Karmic. gnome-power-manager has been rendered completely useless.  I'll attempt a custom compiled Kernel in the near future and see if it is the same issue as before (ACPI_AC not compiled as a module in the stock Kernel).
[*]Suspend is broken -- I didn't try hibernation.
[*]Cannot turn on the built-in blue-tooth (thankfully, my bluetooth dongle works just fine)
[*]Cannot turn off WiFi
[/LIST]
I THINK that #2, #3, and #4 are related... I suspect something to do with Kernel level changes in APCI.  I have the same problems when using the 2.6.32 Kernel in Karmic.  I may get a bit more serious with testing Lucid and start filing/contributing to bug reports.  Hopefully these problems will get worked out before final release.

(The reason that I use 2.6.32 in Karmic is because the 2.6.31 Kernel in Ubuntu has rendered VirtualBox unusable.  At least for me, Karmic will be forever known as Ubuntu ME.)

---

### Post by miniyak on 2010-03-08
wait... hdmi isn't working for you Sam? Or are you referring to sound over hdmi?

I have seen the hdmi on the panp5 fail to work with older tvs. My suspicion here is specification inconsistencies... In which case i would assume no update is ever going get it working... because the problems with tv (or rather the people whom felt that are av cables need to be updatable).

However hdmi works perfectly on my new 21" 1080p dell monitor using twin view. (at least they sell good monitors) Best investment I've made in a while. The extra screen real estate (3600*1080) helps when im working on projects. Wish i had got a screen like this with the pangolin right off the bat.

....lucid right... just a couple of comments

yes the default brown theme was bad... but they went with purple instead? Lot of hubbub over something most people (who were upset w/brown) would change anyhow. 

I'm definitely waiting till May to even think of upgrading.. ive been burned too many times with trigger happy early installs... (though i would have an extra drive this time...)
Would love to hear more developments though.. so keep the info coming.

---

### Post by samalex on 2010-03-09
> **miniyak said:**
> wait... hdmi isn't working for you Sam? Or are you referring to sound over hdmi?

I have seen the hdmi on the panp5 fail to work with older tvs. My suspicion here is specification inconsistencies... In which case i would assume no update is ever going get it working... because the problems with tv (or rather the people whom felt that are av cables need to be updatable).

However hdmi works perfectly on my new 21" 1080p dell monitor using twin view. (at least they sell good monitors) Best investment I've made in a while. The extra screen real estate (3600*1080) helps when im working on projects. Wish i had got a screen like this with the pangolin right off the bat.

....lucid right... just a couple of comments

yes the default brown theme was bad... but they went with purple instead? Lot of hubbub over something most people (who were upset w/brown) would change anyhow. 

I'm definitely waiting till May to even think of upgrading.. ive been burned too many times with trigger happy early installs... (though i would have an extra drive this time...)
Would love to hear more developments though.. so keep the info coming.

I've never been able to get HDMI to work on my PanP5 running 9.04, but from what others have posed it's fixed in 9.10 (and hopefully 10.04).  I do get Video, though it's pixelated, but no audio.  VGA works fine, but it'll be nice to plug in one cable instead of two when connecting my laptop to the TV, which is only about 18 months old so I suspect it's not a compatibility problem.

As for being an early adopter, I'm generally not... so I may wait a week or two to let others 'beta test' 10.04 when it hits the streets.  And I agree about 9.10 being equated to Windows ME...  that's why I still run 9.04.

As for the theme, yeah I do change the stock theme outta the box, but if Ubuntu ran with a decent stock theme I might keep it around for a while.  I love Apple's theme, which it looks like Ubuntu is trying to mimic, so I'm glad to see the change.  I keep equating this to when RH7 rolled out Bluecurve around 2002 or 2003.  It was just an aesthetic change, but it was refreshing to see.

Take care,

Sam

---

### Post by miniyak on 2010-03-09
hmm... i had hdmi working in 9.04. sort of had similar problem,.. though I never really tested using hdmi the way i do now using twin view vs. that god awful "screen switch" fn-f7 combo.

And i say god awful because today i went to turn the volume up and accidentally hit while in twin view. long story short, the only way to fix the resulting issue is to restart. Laptops should have dedicated sound keys is the moral to the story.

---

### Post by wrender on 2010-03-10
I was really hoping that the ac adaptor would be recognized when it is plugged in with My Serp5 with Lucid.... sigh.

---

### Post by samalex on 2010-03-10
I've been playing with Lucid Alpha 3 in VirtualBox, and that thing is full of bugs.  Granted it's an alpha version, but hopefully they get most of these ironed out before April 29th.

Sam

---

### Post by samh785 on 2010-03-12
I used alpha 3 in virtual box, and then installed alpha 3 on my panp6. The virtual box install had far more software crashes than did the actual install. For me, it's actually running very stable (I've only had a few *tiny* problems that have resolved themselves. If I were you, I would wait until the first beta at the latest because in my current experience it's only a wee bit less stable than 9.10

---

### Post by HotShotDJ on 2010-03-13
> **HotShotDJ said:**
> 
[LIST=1]
[*]Power Management is STILL broken -- and it is worse than in Karmic. gnome-power-manager has been rendered completely useless.  I'll attempt a custom compiled Kernel in the near future and see if it is the same issue as before (ACPI_AC not compiled as a module in the stock Kernel).
[*]Suspend is broken -- I didn't try hibernation.
[*]Cannot turn on the built-in blue-tooth (thankfully, my bluetooth dongle works just fine)
[*]Cannot turn off WiFi
[/LIST]
I THINK that #2, #3, and #4 are related... I suspect something to do with Kernel level changes in APCI.Surprisingly, I guessed that one right.  It was kernel level changes in ACPI (still haven't debugged #1)

Through a VERY convoluted route, I found [Bug 14667 -  bisected 2.6.32 EC regression - Temperatures not correctly detected after suspend]("http://bugzilla.kernel.org/show_bug.cgi?id=14667") -- I know it doesn't seem to make sense, but trust me on this one.  I applied the fix suggested in comment #11 of that bug, recompiled, *et voila*, Suspend works (what was broken was detection  of the lid "button") built-in blue-tooth works (Fn + F12) and I can again turn off wireless card (Fn + F11).

This is an upstream bug... Ubuntu developers did not introduce it.  It is patched (will be patched?) in 2.6.33 at some point if I'm reading the bug report correctly.  I'm not sure if it will be fixed in 2.6.32, which is what Lucid is using.

Tom:  This is something that System76 may want to get involved in now, before Lucid development gets too far along.  It is a VERY easily corrected problem -- but once Lucid hits RC phase, I'm afraid they will not be interested in fixing it.  I don't know how many of your products this will effect, but it definitely will cause pain and suffering for PanP5 and probably PanP6 owners if the bug ends up in Lucid final.

---

### Post by thomasaaron on 2010-03-15
Thanks, HotShotDJ. Passing this one on.

---

### Post by samh785 on 2010-03-15
It should also be noted that (on panp6) that the touchpad cannot be disabled.

---

### Post by thomasaaron on 2010-03-15
The function key combination for disabling it doesn't work?

Try running your System76 Driver and rebooting. Did that fix it. If not, we'll look into it.

sudo modprobe -r psmouse 

...will disable it

---

### Post by marshmallow1304 on 2010-03-17
Is there a way to force the S76 Driver to run on Lucid?

Edit:  I got it.  It's not difficult.  Just edit /etc/lsb-release from
> I don't know whether it's necessary to edit both lines.  I can't be bothered to experiment with it right now.
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"

to
> 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"

Then install the driver, reboot and restore the file.  ([Source]("http://ubuntuforums.org/showpost.php?p=7449131"))


I can confirm that the function keys for touchpad, wireless, webcam, and Bluetooth don't work, even with the driver installed.  On a related note, what is the preferred method of reporting hardware-related bugs on S76 hardware?  Is launchpad.net/system76 in active use?

---

### Post by thomasaaron on 2010-03-17
You can report bugs at...
[http://launcpad.net/system76](http://launcpad.net/system76)

However, please don't start reporting bugs in Lucid yet. We've not even started testing with it yet.

We'll begin testing next week, and, chances are, we'll have most of the bugs squashed anyway by the time Lucid is officially released. No sense reporting bugs before then.

---

### Post by samh785 on 2010-03-17
> **thomasaaron said:**
> The function key combination for disabling it doesn't work?

Try running your System76 Driver and rebooting. Did that fix it. If not, we'll look into it.

sudo modprobe -r psmouse 

...will disable it
What's the command to re-enable it?  :)

---

### Post by jdb on 2010-03-17
> **samh785 said:**
> What's the command to re-enable it?  :)

sudo modprobe psmouse 

jdb

---

### Post by samh785 on 2010-03-17
> **jdb said:**
> sudo modprobe psmouse 

jdb
Thank you so much! :D

---

### Post by HotShotDJ on 2010-03-18
> **marshmallow1304 said:**
> I can confirm that the function keys for touchpad, wireless, webcam, and Bluetooth don't work, even with the driver installed.This is consistent with problems that I talk about in [post #9]("http://ubuntuforums.org/showpost.php?p=8963415&postcount=9").  There really isn't much to do except for wait.

---

### Post by samh785 on 2010-03-18
> **thomasaaron said:**
> You can report bugs at...
[http://launchpad.net/system76]("http://www.launchpad.net/system76")
fixed the url for you :D

---

### Post by HotShotDJ on 2010-03-20
> **thomasaaron said:**
> Thanks, HotShotDJ. Passing this one on.
Hi, Tom --

This bug is also in Launchpad:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524956](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524956)

I've added a comment regarding the PanP5 to that one.  Perhaps it would be helpful for System76 to chime in as well as you test Lucid Beta on your shop machines.  Developers are probably more likely to listen to you than to me. :)

---

### Post by Vrekk on 2010-03-21
My starling is running the beta1 great :D, just the top panel is a little messed up :popcorn: Can't wait to see this get released

EDIT: Gnome panel fixed its self so never mind on that :D

---

### Post by samalex on 2010-03-22
> **Vrekk said:**
> My starling is running the beta1 great :D, just the top panel is a little messed up :popcorn: Can't wait to see this get released

EDIT: Gnome panel fixed its self so never mind on that :D

I installed Beta 1 in VBox this weekend, and it installed great!  I only had one or two crashes while trying to setup the VBox video card, which I never could get any higher then 800x600.  From reading more into this, the VirtualBox tools that get installed use the HAL, which isn't used with Ubuntu 10.04, so I'm not sure there is a work around :-/ 

But from what I've seen I like the theme and new apps.  I can't wait for the Music store to be available.  It just says Coming Soon in RhythmBox.

For anyone interested here are some screenshots I posted on our LUG forum:
[http://bbs.hotlug.org/viewtopic.php?f=3&t=1021](http://bbs.hotlug.org/viewtopic.php?f=3&t=1021)

Take care --

Sam

---

### Post by smulloni on 2010-03-22
I upgraded my Darter to Lucid Beta 1 without incident -- except that I had to remove openoffice.org-filter-binfilter due to a circular dependency issue.   Compiz, which never worked before on this machine, now works, and the hard drive, which used to sound like a rat eating Grape Nuts, is now pleasingly silent.  Suspend never worked on this machine and still doesn't.  My volume control disappeared and I can't find a way to get it back -- but otherwise, the water is fine, come on in.

---

### Post by Vrekk on 2010-03-22
> **smulloni said:**
> I upgraded my Darter to Lucid Beta 1 without incident -- except that I had to remove openoffice.org-filter-binfilter due to a circular dependency issue.   Compiz, which never worked before on this machine, now works, and the hard drive, which used to sound like a rat eating Grape Nuts, is now pleasingly silent.  Suspend never worked on this machine and still doesn't.  My volume control disappeared and I can't find a way to get it back -- but otherwise, the water is fine, come on in.

Did you try running the system76 driver again? That fixed almost all of my problems when I upgraded my netbook (well not wireless but that's a known issue)

---

### Post by samh785 on 2010-03-25
> **samalex said:**
> 
But from what I've seen I like the theme and new apps.  I can't wait for the Music store to be available.  It just says Coming Soon in RhythmBox.
It's in public beta now and works well for me :)

---

### Post by ranch hand on 2010-04-01
I have not tried 10.04 on my wifes pangolin.

I am testing it on my desktop.

Most of you are probably running 9.10 and I can tell you that, as a surviver of 9.10-testing, 10.04-testing is boring by comparison.  This bugger is more stable than 9.10 at RC.

It will be on the wifes S76 box.  It is just nicer than 9.10.

The buttons on the left side, by the way are easy to fix in gconf-editor>apps>metacity>general>button layout.  If you want the same order and placement that you are used to you want to edit that to read   :minimize,maximize,close

Gconf-editor can be added to your menu under whatever name you want and under command put
gconf-editor

That command will also, of coarse, pull it up in terminal for you.

They even seem to be getting plymouth under control.

The thing does boot fast but the 10 second or less target is for something running the atom processor and using a SDD.  For most folks on more standard hardware the speed seems to vary from the high teens to about 40 seconds when everything is working right (it is a beta1).

---

### Post by ranch hand on 2010-04-01
Now, as to what I popped over here from the 10.04 forum for, how in flinderation is the testing on the S76 driver for 10.04 going and do you need another pangolin running it?

---

### Post by thomasaaron on 2010-04-01
It's going pretty well. Still a lot of work to do, though. A System76 Driver that supports 10.04 won't be released, though, until after the official release of Lucid.

---

### Post by ranch hand on 2010-04-01
> **thomasaaron said:**
> It's going pretty well. Still a lot of work to do, though. A System76 Driver that supports 10.04 won't be released, though, until after the official release of Lucid.
All right.

If you need testing help just holler over on the testing forum.  There are several Sys76 boxes on it now.

I would put it on the wifes but I am trying to be good and leave it alone.

She loves the thing by the way.

---

### Post by riseringseeker on 2010-04-01
> **ranch hand said:**
> 
Gconf-editor can be added to your menu under whatever name you want and under command put
gconf-editor


The easiest way would be to open System->Preferences->Main Menu then click on "System Tools".  Check mark "Configuration Editor"

---

### Post by ranch hand on 2010-04-01
> **riseringseeker said:**
> The easiest way would be to open System->Preferences->Main Menu then click on "System Tools".  Check mark "Configuration Editor"
The reason I mentioned that is because it is not in the menu on most of my installs of 10.04.  I am not sure why not and some folks may not know how to get it there.

The only install I have of 10.04 with it in  the menu is actually one upgraded9.04>9.10>10.04.

Why such a handy tool would not be default on the menu is beyond me.

---

### Post by Flyers2391 on 2010-04-01
> **ranch hand said:**
> The reason I mentioned that is because it is not in the menu on most of my installs of 10.04.  I am not sure why not and some folks may not know how to get it there.

The only install I have of 10.04 with it in  the menu is actually one upgraded9.04>9.10>10.04.

Why such a handy tool would not be default on the menu is beyond me.

I've never actually gone to the system > preferences menu to edit the menu, I've always just right clicked and selected "edit menus"

those buttons being on the left side in the wrong order are going to be really annoying ... if I wanted my system be a pain to use I'd get a mac

---

### Post by ranch hand on 2010-04-01
> **Flyers2391 said:**
> I've never actually gone to the system > preferences menu to edit the menu, I've always just right clicked and selected "edit menus"

those buttons being on the left side in the wrong order are going to be really annoying ... if I wanted my system be a pain to use I'd get a mac
+1

Why they do not have a system tools menu by default is beyond me.  The buttons on the left are easy to change.  But why on the left?  Most folks are right handed.  The cursor is therefore on the right half of the screen most of the time.

They seem to have "exciting" plans for the right side of the screen.  I can't wait.  Hopefully it can be turned off, whatever it is.

---

### Post by jpv on 2010-04-02
> **ranch hand said:**
> +1
They seem to have "exciting" plans for the right side of the screen.  I can't wait.  Hopefully it can be turned off, whatever it is.

Fix Window buttons in Ubuntu 10.04:
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"

Only problem is, due to the new theme and the button icons, the correct order will look a little goofy.  I'll live with that instead of being massively inconvenienced by this stupid move.

See also: [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633)
[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

---

### Post by riseringseeker on 2010-04-02
> **ranch hand said:**
> The reason I mentioned that is because it is not in the menu on most of my installs of 10.04.  I am not sure why not and some folks may not know how to get it there.

The only install I have of 10.04 with it in  the menu is actually one upgraded9.04>9.10>10.04.

Why such a handy tool would not be default on the menu is beyond me.

It is on the System Tools menu by default, but just not **active** by default.  I have a 10.4 on a usb and two installs of 9.10 currently running.  Neither release have it active by default, but it is indeed on the System Tools menu in both.

To be honest, I added it on the "Other" menu list before I found it to already be available, but unchecked on the System Tools menu in both 10.4 and 9.10.

Not sure how often I would use it once the install is complete, but I do use it on every installation I do.  (I install 1 or 2 a month on co-workers boxes).  

The first thing I do is get rid of the count time timer for log-out/shutdown, then revert the updates behavior to giving an icon announcing updates are available.  I may use it for more in Lucid, time will tell.

That said, I agree that it should be enabled, not just available to be enabled by default.  I think there is a large percentage of people who have been around Ubuntu that do at least what I mentioned above on a new install.

---

### Post by ranch hand on 2010-04-02
I just did a clean install of the B1 and it sure was there if you put the system tools menu in.  Wasn't a while back so I have just been adding it and the menu.  Now it is there and I am HAPPY about that.

I was afraid they were going to leave use with out it as a default part of the system tools menu.  Glad that is not true.

Wonder what the reason for leaving the system tools menu inactive by default is.  Gconf-editor, for instance, is not hard to use but may be hard to find for a new user this way.

---

### Post by samalex on 2010-04-02
I've been running with Beta 1 in VirtualBox since it came out, and though it's slick, I get Crash Alerts pretty regularly so I guess it still has some rough edges to go.  

I'm planning on moving up to 10.04 pretty quickly after it's released, so I'm just curious if the System76 guys will have drivers available for the PanP5 laptop when 10.04 is released later this month.

Thanks -

Sam

---

### Post by NightwishFan on 2010-04-02
I wish I could buy a System76. I think I might actually tone down on my spending and save up for one. I could use my current laptop as a squid proxy or donate it. Any recommended models? The low power desktops are awesome but I need something portable. Raw machine is not really a factor as I only have modest needs.

Also, running in Virtualbox is different from bare hardware. Some bugs might be limited to only there. ;)

---

### Post by ranch hand on 2010-04-02
> **NightwishFan said:**
> I wish I could buy a System76. I think I might actually tone down on my spending and save up for one. I could use my current laptop as a squid proxy or donate it. Any recommended models? The low power desktops are awesome but I need something portable. Raw machine is not really a factor as I only have modest needs.

Also, running in Virtualbox is different from bare hardware. Some bugs might be limited to only there. ;)
The Pangolin that I bought my wife with 9.10 installed works great and is about the same power as the desktop in my sig.

The battery life is not that great but we use it plugged in over 99% of the time so we do not care.

I got some extra ram and a 7200rpm 320Gb HDD with it as the only non standard stuff.

It seems like a very robust box built to stand up well to moving around.  Great hinges.

Wife hauls it to work and back quite a bit.

She loves the bugger.

---

### Post by NightwishFan on 2010-04-02
Excellent, thank you. I will browse around the page. Battery life is a major importance to me though.

---

### Post by ranch hand on 2010-04-02
Well 1.5 hours will probably not cut it then.

This is too bad as it is a very powerful, fast box.

I have the idea that all their boxes are pretty good stuff.

---

### Post by HotShotDJ on 2010-04-03
I went ahead and "backported" the fix for the ACPI issues that are currently being tested for 2.6.34 (I'm not certain if it is part of the 2.6.33 git tree).  Surprisingly, the patch I created worked.  I've uploaded it to launchpad.  I guess it is in the hands of the developers.  If anybody here needs the patch for 2.6.32, I'll be happy to post it... however, I have only tested it on my PanP5, only 64 bit, and only with the 2.6.32-19.28 kernel.  It SHOULD work just fine when compiled for a 32 bit system, but I can't vouch for that.

---

### Post by riseringseeker on 2010-04-03
> **Flyers2391 said:**
> I've never actually gone to the system > preferences menu to edit the menu, I've always just right clicked and selected "edit menus"


Thanks for that, learned something new.  Makes sense though, most things in Ubuntu have some sort of menu with a right click.

---

### Post by riseringseeker on 2010-04-03
> **ranch hand said:**
> I just did a clean install of the B1 and it sure was there if you put the system tools menu in.  Wasn't a while back so I have just been adding it and the menu.  Now it is there and I am HAPPY about that.

I was afraid they were going to leave use with out it as a default part of the system tools menu.  Glad that is not true.

Wonder what the reason for leaving the system tools menu inactive by default is.  Gconf-editor, for instance, is not hard to use but may be hard to find for a new user this way.

I guess mine was there on both installs after I added fusion-icon and backintime, hadn't looked at the menus before that.  Both show up when installed in the System Tools menu.

---

### Post by ranch hand on 2010-04-03
> **riseringseeker said:**
> I guess mine was there on both installs after I added fusion-icon and backintime, hadn't looked at the menus before that.  Both show up when installed in the System Tools menu.
I have a single 320Gb drive in an external enclosure that I loan to folks that want to try Ubuntu out.  I am just redoing the whole thing.  Have all the partitions made and am installing a little at a time.  It will have 9.04-32, 9.10-32, 10.04-32, 9.04-64, 9.10-64 and 10.04-64 on it in that order.

I have installed and set up 9.10-32 and 10.04-32.  I had to download the 32bit images as I just run 64 bit.  The 10.04-32 was installed from a Live CD ISO.

No system tools menu.  Went to enable it and it was empty.  Had to add gconf-editor again.

Must be going to be there by default but not making it on all images yet.

---

### Post by Noah0504 on 2010-04-05
I'm really hoping a lot of these issues are cleared up quite soon.  Some of the new features in Lucid really make it great, but I'm going to be sticking with Karmic if it's going to basically break my system.

---

### Post by thomasaaron on 2010-04-05
Honestly, unless your interested in testing Lucid on your own computer just for the fun of it -- or to provide feedback to Ubuntu developers -- there's really no use in worrying about it. 

At this stage of the game, it's under HEAVY, fast-paced development. Lots of bugs are being squashed. It's performance level now really isn't indicative of what it will be by the end of the month.

---

### Post by Noah0504 on 2010-04-05
I've been using Ubuntu long enough to know how many bugs get fixed in even the last two weeks before a release, but I also hate to say I've seen plenty of releases break a machine that ran wonderfully one release prior.  Don't take this as a complaint, just an observation.  :P  Either way, I still look forward to the release of Lucid.  I'm thinking about going ahead and loading the beta to help bug test and see how many issues get resolved.

EDIT:  The BT issues would be a pretty big deal though while I was testing the beta until it gets resolved.

---

### Post by ranch hand on 2010-04-05
I would not recommend to install the B1 ISO and update to current.  There is a problem for some doing so.  If you et the current daily build you should have no trouble.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

If you wait until Thursday the B2 ISO should be released.

Of coarse if you install from the daily and keep it updated you will have the B2 without having to fight the crowd that will swamp the servers Thursday.

---

### Post by Noah0504 on 2010-04-05
> **ranch hand said:**
> I would not recommend to install the B1 ISO and update to current.  There is a problem for some doing so.  If you et the current daily build you should have no trouble.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

If you wait until Thursday the B2 ISO should be released.

Of coarse if you install from the daily and keep it updated you will have the B2 without having to fight the crowd that will swamp the servers Thursday.

Yeah, I plan on getting the daily-live build.  Does anyone know if any of the more serious issues have been corrected yet?  For instance, not being able to turn on BT or turn off wireless.

---

### Post by ranch hand on 2010-04-05
I know nothing about either one of those things, don't have wireless on this box and have never heard of the other.

The best place to ask about that type of thing would be;

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Please use the forum search before posting.  There are way too many threads on the same topics.

---

### Post by riseringseeker on 2010-04-05
> **ranch hand said:**
> 
No system tools menu.  Went to enable it and it was empty.  Had to add gconf-editor again.

Must be going to be there by default but not making it on all images yet.

What I was trying to say is it may indeed not have had the System Tools menu before I installed backintime, and/or fusion-icon.  I never looked, but from what you're saying it probably wasn't active until **after** I installed one or the other, since they live in the System Tools menu.
 and are added there when installed.

You should be able to just open the menu edit, highlight Applications, then check the System Tools menu over "show" column on the to make it active.  Inside the System Tools menu (and most others), I have several additional options that are not currently active I can add with a mouse click.

---

### Post by riseringseeker on 2010-04-05
> **thomasaaron said:**
> Honestly, unless your interested in testing Lucid on your own computer just for the fun of it -- or to provide feedback to Ubuntu developers -- there's really no use in worrying about it. 

At this stage of the game, it's under HEAVY, fast-paced development. Lots of bugs are being squashed. It's performance level now really isn't indicative of what it will be by the end of the month.

Agreed.  The install I have on the USB drive I have gotten updates as many as three times a day (I run update manually), and each time there have been literally dozens to install.

It's a nice interface and everything is working for me on my Daru1.  I am, for the time being at least, leaving the buttons on the left side to give it a fair chance.  It's not like I use a windows machine very often at all.

I am just playing with it to get a feel for the changes so I am not totally surprised when I go to install it on all my machines next month.

---

### Post by thomasaaron on 2010-04-15
OK, here are some of my preliminary thoughts on Lucid...

[http://thomasaaron.wordpress.com](http://thomasaaron.wordpress.com)

...enjoy.

---

### Post by Noah0504 on 2010-04-17
> **thomasaaron said:**
> OK, here are some of my preliminary thoughts on Lucid...

[http://thomasaaron.wordpress.com](http://thomasaaron.wordpress.com)

...enjoy.
So, I have to be pushy and ask.  :P  How is testing going on the different System76 machines?  I know everything is working flawlessly on my PanP6 except for the bug posted earlier in this thread about not being able to enable BT and turn off WIFI.  I also think the battery applet is partially broke again for now... Right now I'm using the computer on battery power, but Ubuntu has no idea.  :P

Anyway, I'm hoping these issues get resolved before the actual release.  I also hope the System76 driver is coming along nicely for Lucid.

---

### Post by Noah0504 on 2010-04-17
> **HotShotDJ said:**
> I went ahead and "backported" the fix for the ACPI issues that are currently being tested for 2.6.34 (I'm not certain if it is part of the 2.6.33 git tree).  Surprisingly, the patch I created worked.  I've uploaded it to launchpad.  I guess it is in the hands of the developers.  If anybody here needs the patch for 2.6.32, I'll be happy to post it... however, I have only tested it on my PanP5, only 64 bit, and only with the 2.6.32-19.28 kernel.  It SHOULD work just fine when compiled for a 32 bit system, but I can't vouch for that.
I'd be interested in trying out that patch on my PanP6.

---

### Post by ranch hand on 2010-04-17
> **HotShotDJ said:**
> I went ahead and "backported" the fix for the ACPI issues that are currently being tested for 2.6.34 (I'm not certain if it is part of the 2.6.33 git tree).  Surprisingly, the patch I created worked.  I've uploaded it to launchpad.  I guess it is in the hands of the developers.  If anybody here needs the patch for 2.6.32, I'll be happy to post it... however, I have only tested it on my PanP5, only 64 bit, and only with the 2.6.32-19.28 kernel.  It SHOULD work just fine when compiled for a 32 bit system, but I can't vouch for that.
I would be interested in this patch mayself.  It should fit the wifes pang very well and I have a pair of partitions ready for the RC.

I am assuming this is still a problem.

---

### Post by Noah0504 on 2010-04-18
> **ranch hand said:**
> I would be interested in this patch mayself.  It should fit the wifes pang very well and I have a pair of partitions ready for the RC.

I am assuming this is still a problem.
Yes, it's still a problem.  Here is the bug report for the kernel issue: [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/526354](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/526354)

And here is the sad news: [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/526354/comments/39](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/526354/comments/39)

The window for kernel updates has already been closed, so I guess those affected will have to wait until a update is released later.  It's a real killer for a lot of users, but oh well.  I guess I can stick with 9.10 or just apply the fix.  There are some instruction on how to do so in that bug report.  Maybe I will just do that and see how smooth it runs.

---

### Post by ranch hand on 2010-04-18
Well, thanks a bunch for this further information.

I am trying to be good and not mess with the wifes box.  If it was mine I would go for it.

It looks as if they intend to release the bugger after 10.04 launches though so it shouldn't be long.  There seems to be a lot of models effected so I am sure it will be high on the priority list.

---

### Post by ranjan_mg on 2010-04-20
I tried the latest live cd on panp6. 
1) I could not get it to suspend closing the laptop lid - the power options are set correctly
2) Internal microphone not recognised.

---

### Post by ranch hand on 2010-04-20
I would wait for the RC on Thursday.

---

### Post by Noah0504 on 2010-04-21
> **ranjan_mg said:**
> I tried the latest live cd on panp6. 
1) I could not get it to suspend closing the laptop lid - the power options are set correctly
2) Internal microphone not recognised.
Suspend isn't going to work due to a bug that also affects the BT, WiFi and oddly enough, the trackpad enable/disable key.  This bug requires a fix in the kernel that will not be released until after Ubuntu 10.4 final.  Hopefully it won't take long.

And I don't think I have had a problem with the microphone, but I will double check when I get home.

---

### Post by ranjan_mg on 2010-04-21
I think the microphone is working. In 9.10, I would see microphone1 and microphone2 listed where as 10.04 does not. So, I thought it was not working.
 
For suspend and resume, is there a launchpad bug ? I did not see any. Oddly, suspend and resume work fine with the function keys.
Yes, could not get bluetooth either.

---

### Post by HotShotDJ on 2010-04-21
> **ranjan_mg said:**
>  I did not see any. Oddly, suspend and resume work fine with the function keys.
Yes, could not get bluetooth either.Yes, there is a launchpad bug (although the title of the bug doesn't seem to have anything to do with the problems we're seeing on PanP5 and 6) The issue is within ACPI, wich is why you are able to suspend and resume using the methods OTHER than the lid (lid button creates an ACPI event, as do the Bluetooth and WiFi function keys). [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/526354](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/526354)

(And before you say that this bug doesn't have anything to do with your problems... I PROMISE you that it is the cause of the PanP5 & 6 woes).

---

### Post by samalex on 2010-04-21
> **HotShotDJ said:**
> Yes, there is a launchpad bug (although the title of the bug doesn't seem to have anything to do with the problems we're seeing on PanP5 and 6) The issue is within ACPI, wich is why you are able to suspend and resume using the methods OTHER than the lid (lid button creates an ACPI event, as do the Bluetooth and WiFi function keys). [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/526354](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/526354)

(And before you say that this bug doesn't have anything to do with your problems... I PROMISE you that it is the cause of the PanP5 & 6 woes).

I hoped to install Lucid when it's released next week on my PanP5, but unless they have the ACPI problems fixed by then I'll probably hold off.  But can wifi and bluetooth be togged through the menus or is it just through the function keys that doesn't work?  I use wifi daily and bluetooth probably weekly, so if there's no other way to toggle these then that is indeed a problem.

As for suspend, I can live without that for a while.

Sam

---

### Post by HotShotDJ on 2010-04-21
> **samalex said:**
> But can wifi and bluetooth be togged through the menus or is it just through the function keys that doesn't work?  I use wifi daily and bluetooth probably weekly, so if there's no other way to toggle these then that is indeed a problem.Hi, Sam... the only way to toggle on/off both the wifi and bluetooth is through the function keys.  It looks like the developers will be releasing the third version of Ubuntu in a row that doesn't work without major tweaking (at least for me).  And this is with computers that I bought for the specific purpose of running Linux.

Needless to say, I'm very disappointed.  How will [Bug #1]("https://launchpad.net/ubuntu/+bug/1") ever be closed like this?

EDIT: PS -- using the proprietary (3D) drivers for NVidia has now completely borked my Lucid install... it has been rendered unbootable.  Will it be fixed for release?  Your guess is as good as mine.

---

### Post by ranch hand on 2010-04-21
> **HotShotDJ said:**
> Hi, Sam... the only way to toggle on/off both the wifi and bluetooth is through the function keys.  It looks like the developers will be releasing the third version of Ubuntu in a row that doesn't work without major tweaking (at least for me).  And this is with computers that I bought for the specific purpose of running Linux.

Needless to say, I'm very disappointed.  How will [Bug #1]("https://launchpad.net/ubuntu/+bug/1") ever be closed like this?

EDIT: PS -- using the proprietary (3D) drivers for NVidia has now completely borked my Lucid install... it has been rendered unbootable.  Will it be fixed for release?  Your guess is as good as mine.
Bug 1, to me is fun but silly.  That should not be a concern.

Building an OS that works is what is needed.

The only way to get a large market share is to dumb down the system to the point that idiots can use it.  Yes that is harsh.

How is most malware introduced to computers.  Idiots install it on their very own computers and then complain about it.

Linux, in general, is suited to be a "grown up" OS.  I think a very good market share can be had if the effort is concentrated on distros that actually work and do serious work.

They also need to do things like have switching that works for everyone.

---

### Post by Noah0504 on 2010-04-22
> **HotShotDJ said:**
> Hi, Sam... the only way to toggle on/off both the wifi and bluetooth is through the function keys.  It looks like the developers will be releasing the third version of Ubuntu in a row that doesn't work without major tweaking (at least for me).  And this is with computers that I bought for the specific purpose of running Linux.

Needless to say, I'm very disappointed.  How will [Bug #1]("https://launchpad.net/ubuntu/+bug/1") ever be closed like this?

EDIT: PS -- using the proprietary (3D) drivers for NVidia has now completely borked my Lucid install... it has been rendered unbootable.  Will it be fixed for release?  Your guess is as good as mine.

I know the reasoning behind not releasing the fix before the release, but I think there needs to be an exception to that rule.  This breaks systems for MANY people.  I've been running Lucid for the reasons of curiosity and trying to help build a better release with bug reports.  What good does it do to help acknowledge a big problem that will be fixed AFTER release?  I guess late is better than never?

I haven't had a problem with the nVidia drivers.  Everything seems to be running fine aside from the obvious bug we've been running into with out PanP5s and PanP6s.

---

### Post by HotShotDJ on 2010-04-22
> **Noah0504 said:**
> I've been running Lucid for the reasons of curiosity and trying to help build a better release with bug reports.  What good does it do to help acknowledge a big problem that will be fixed AFTER release?  I guess late is better than never?This is exactly why I've been testing Lucid (fortunately, on its own partition so that my production system isn't effected). But my experience is that "late = never" with Ubuntu.  In other words, if there is a bug that has not been fixed by the second Beta, the bug will be present in the final release (unless it is one of the "special" projects on their list, like Plymouth for Lucid).

Karmic was released with major problems for many people. (I often refer to Karmic as "Ubuntu ME"). None of them were corrected after the release.  I can only hope that Lucid, as a LTS release, will be better.  So far, the evidence is against that hope, with the developers more worried about deadlines than coming out with a solid release.  This was NOT always the case.  They delayed the release of Dapper Drake by two months -- it was scheduled as 6.04-LTS, but was held back for two months and finally released as 6.06-LTS.

Anyway, we will see what happens.  I'm starting to test Lucid RC.  I am SO hoping that I am wrong about this.

---

### Post by Noah0504 on 2010-04-22
> **HotShotDJ said:**
> This is exactly why I've been testing Lucid (fortunately, on its own partition so that my production system isn't effected). But my experience is that "late = never" with Ubuntu.  In other words, if there is a bug that has not been fixed by the second Beta, the bug will be present in the final release (unless it is one of the "special" projects on their list, like Plymouth for Lucid).

Karmic was released with major problems for many people. (I often refer to Karmic as "Ubuntu ME"). None of them were corrected after the release.  I can only hope that Lucid, as a LTS release, will be better.  So far, the evidence is against that hope, with the developers more worried about deadlines than coming out with a solid release.  This was NOT always the case.  They delayed the release of Dapper Drake by two months -- it was scheduled as 6.04-LTS, but was held back for two months and finally released as 6.06-LTS.

Anyway, we will see what happens.  I'm starting to test Lucid RC.  I am SO hoping that I am wrong about this.

Ubuntu is starting to have the same practice of "release now, fix later" that major software companies often seem to use.  I see that a fix has been committed in the bug report, but I'm not sure exactly what this means.  Does it mean we will see the bug fixed on or shortly after release.  I wish it would at least make it into the proposed repository so it could be tested... or has it already made it there?

---

### Post by samalex on 2010-04-22
> **HotShotDJ said:**
> This is exactly why I've been testing Lucid (fortunately, on its own partition so that my production system isn't effected). But my experience is that "late = never" with Ubuntu.  In other words, if there is a bug that has not been fixed by the second Beta, the bug will be present in the final release (unless it is one of the "special" projects on their list, like Plymouth for Lucid).

Karmic was released with major problems for many people. (I often refer to Karmic as "Ubuntu ME"). None of them were corrected after the release.  I can only hope that Lucid, as a LTS release, will be better.  So far, the evidence is against that hope, with the developers more worried about deadlines than coming out with a solid release.  This was NOT always the case.  They delayed the release of Dapper Drake by two months -- it was scheduled as 6.04-LTS, but was held back for two months and finally released as 6.06-LTS.

Anyway, we will see what happens.  I'm starting to test Lucid RC.  I am SO hoping that I am wrong about this.

HotShotDJ,

Definitely please post your updates as you see problems or things that are resolved in Lucid on the PanP5.  I still would like to try Lucid when it's released next week, but with Jaunty running so well I'm not sure how eager I am to move to a buggy OS if Lucid is riddled with problems outta the gate.  I didn't move to Karmic for this same reason.

Sam

---

### Post by HotShotDJ on 2010-04-22
> **Noah0504 said:**
> Ubuntu is starting to have the same practice of "release now, fix later" that major software companies often seem to use.I could live with that (with some annoyance, of course) IF they got to the "fix later" part.> **Noah0504 said:**
> I see that a fix has been committed in the bug report, but I'm not sure exactly what this means.I'm not sure what it means at this point.  I've asked about it in the bug-report.  Also, I'm investigating it as I type this (waiting to finish getting the latest Ubuntu kernel git tree).  As soon as I know something, I'll let you know.

---

### Post by Noah0504 on 2010-04-22
> **HotShotDJ said:**
> I could live with that (with some annoyance, of course) IF they got to the "fix later" part.I'm not sure what it means at this point.  I've asked about it in the bug-report.  Also, I'm investigating it as I type this (waiting to finish getting the latest Ubuntu kernel git tree).  As soon as I know something, I'll let you know.

You wouldn't happen to be William Davis, would you?  :P

---

### Post by HotShotDJ on 2010-04-22
> **Noah0504 said:**
> You wouldn't happen to be William Davis, would you?  :PShhhhhhhh.  ;)

---

### Post by HotShotDJ on 2010-04-22
OK... the ACPI fix is in the latest git tree.  From what I can tell, it should be in 2.6.32-22.33, BUT, I'm not positive, since that version is still in development. I'm hoping that it lands in lucid-proposed sooner rather than later.

---

### Post by Noah0504 on 2010-04-29
It looks like the ACPI fix is now in the linux-proposed repository.  If it's not showing up for you, take a look at the bug report.  There is a comment showing where to find the kernel build.  When I get home today, I'm going to try it out.  Looks like I don't have to worry about upgrading!

---

### Post by thomasaaron on 2010-04-30
OK, I'm getting word from customers that enabling the proposed and backports repos and running updates fixed bluetooth.

---

### Post by Noah0504 on 2010-04-30
> **thomasaaron said:**
> OK, I'm getting word from customers that enabling the proposed and backports repos and running updates fixed bluetooth.
It fixed every issue I've had so far (suspend, WiFi, BT and a few other quirks).  Although, I think I still need to text the internal microphone.  I heard someone mention that wasn't working for them.  Other than that, it looks like 10.4 is working PERFECTLY!

---

