---
title: "Pangolian 5 CPU and Xorg issue"
date: 2011-07-06
forum: System76 Support
---

### Post by gamerchick02 on 2011-07-06
I'm running a Pangolian version 5 with the GeForce 105M graphics card and 64-bit Ubuntu (4 gig of RAM).

When I run the proprietary driver from nVidia (with a second monitor) after about a half hour, I get CPU spikes attributed to Xorg (from running the command "top") and my fan doesn't ever shut off.

I'm only running a few programs: Xchat, gwibber, firefox or chromium, empathy, libreoffice.

My laptop essentially slows down to a crawl and it's almost unusable. 

I haven't changed any of the settings in the nVidia settings manager except for the one that sets up my second monitor.

Is there a way to troubleshoot this?

I've been using the open-source drivers for awhile (since the Natty beta) but I'd really like to use the binary drivers, because I think I get better performance.

Well, except when it completely slows down and becomes unusable, that is.

I can't track down what's causing the spike in Xorg usage.  Right now (after a reboot) it's running just fine, but a couple of minutes ago I was having massive slowdowns and it was almost impossible to type.

Also, are any other PanP5 users running into this?

Thanks,

Amy

---

### Post by gamerchick02 on 2011-07-06
I've cleaned my fan out, and that has helped a great deal.  I'm not going to call it solved til I'm sure the fan-cleaning fixed my problem.

Amy

---

### Post by gamerchick02 on 2011-07-07
UPDATE!!!

I've updated my drivers manually and it seems to be taking care of the problem.

I also switched to a DVI to HDMI cable on the monitor and everything was detected and is currently running swell.

Does anyone know why the newest driver was not updated for Natty?  Natty was running a very old driver that only seemed to work well in Maverick.

Amy

---

### Post by gamerchick02 on 2011-07-07
I just disabled sync to vblank and allow flipping.

Xorg seems to be behaving itself right this second coming in on top at 3% of my CPU, compiz at 6%.

I'll update this again if something changes.

Is anyone else with this laptop and GPU having the same issue that I am with the binary drivers and Natty?

Also, I'd be welcome to suggestions from System76 on this one.

Amy

---

### Post by gamerchick02 on 2011-07-08
Xorg chomped on my CPU after about 2.5 to 3 hours while using the binary drivers.

I switched back to the open-source nouveau ones.

Anyone have an idea why this is happening?

Anyone having the same issue as I am?

Amy

---

### Post by isantop on 2011-07-11
Hi Amy.

Sorry for the very slow response. I was out of the office on vacation last week, and things fell a bit behind here. I just closed up shop her, but I'll be sure and get things caught up here tomorrow.

---

### Post by gamerchick02 on 2011-07-11
> **isantop said:**
> Hi Amy.

Sorry for the very slow response. I was out of the office on vacation last week, and things fell a bit behind here. I just closed up shop her, but I'll be sure and get things caught up here tomorrow.

Thanks for getting back with me.

I figured you were on vacation.  :)

Amy

---

### Post by isantop on 2011-07-12
What problems come up with the default proprietary drivers available through the Additional Drivers utility? Can you try reinstalling those to rule out the possibility of a bad download the first time you tried them?

---

### Post by gamerchick02 on 2011-07-12
> **isantop said:**
> What problems come up with the default proprietary drivers available through the Additional Drivers utility? Can you try reinstalling those to rule out the possibility of a bad download the first time you tried them?

The additional drivers utility installs the binary drivers from nVidia.  I enable them, reboot, and start running basic stuff (browser, music app, gwibber, empathy, irc, etc) and sometimes as quickly as 10 minutes in, Xorg starts eating my CPU for lunch.  Sometimes Compiz gets in on the action.  It'll jump from a decent 3-8% to 50-98%.  This causes a major slowdown and the computer is pretty much unusable.

I upgraded to the 275.09.07 binary drivers from the edgers ppa (I didn't install the ppa, just the packages from [here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/760632/comments/95").

This increased the time I could use the computer without a massive slowdown (compare about 10 minutes to an hour to 2 to 3 hours).

I think the issue is in the nVidia binary drivers that are packaged for Natty.  This happened when I installed the beta, and has been hanging around through reinstalls (and I did a full reinstall, wiping my /home and then bringing it back after reinstall).

Any thoughts?

Amy

---

### Post by isantop on 2011-07-13
We'll have to do some testing with the driver and natty to see if that's what's causing the interaction. We haven't gotten any other reports of this, though, and since it's persisting across reinstalls, this is starting to sound like you may have a hardware problem.

---

### Post by gamerchick02 on 2011-07-13
> **isantop said:**
> We'll have to do some testing with the driver and natty to see if that's what's causing the interaction. We haven't gotten any other reports of this, though, and since it's persisting across reinstalls, this is starting to sound like you may have a hardware problem.

Hrm.

Ok.

I'm out of warranty, so unless this can be taken care of with software, I'm kind of stuck.

I have full hardware acceleration under Windows 7, if this helps anything.

Amy

---

### Post by gamerchick02 on 2011-07-15
Also!

I run a dual-monitor setup with a Westinghouse 1280x1024 LCD panel.

Just something I thought of that I didn't add before.

Amy

---

### Post by HotShotDJ on 2011-07-16
> **isantop said:**
> We haven't gotten any other reports of this, though, and since it's persisting across reinstalls, this is starting to sound like you may have a hardware problem.I'm just chiming in here so that Amy doesn't feel like she's going crazy. :)  While I haven't experienced the xorg instability that she is reporting, I have had an issue with the NVidia binary drivers + dual monitor (both Ubuntu and OpenSuSE... manually installed and repository installs).  For your convenience, I'll quote [what I said in another thread]("http://ubuntuforums.org/showpost.php?p=11042883&postcount=6") here:> NVidia "Feature" with Dual-Monitor Set Up: Be warned -- GPU Scaling does not work with NVidia chip-sets with an external monitor attached and both monitors turned on. The GPU remains at its highest setting at all times. This can be an issue with laptops, since it will create a lot of heat. At best, it creates a noisy laptop with the fans running on high all the time. At worse, it can over-heat your laptop causing system instability and even system failure. (see: [http://www.nvnews.net/vbulletin/show...96#post2027196](http://www.nvnews.net/vbulletin/show...96#post2027196)). NOTE: If you turn off the internal monitor and use only the external monitor, this should not be an issue.
Please note also that this has not always been the case with NVidia's proprietary drivers.  As discussed in the referenced linked in the above quote, this appears to have begun with the 180.60 driver.

I believe that this behavior can be controlled using "dword" controls within /etc/X11/xorg.conf, but I haven't tried that method and it could have other unintended consequences.  It has been quite some time since I've messed with dwords and my knowledge on how to use them is quite dated.  I will spend some time this weekend updating my knowledge to find out if there is a way to safely override this behavior.

Amy:  Might I recommend that you install the sensors package and begin monitoring your temps.  What I'd like you to look for is any correlation between the temps and the behavior of xorg (CPU spikes, slow performance, etc.).  Also, as I suggested yesterday, you might want clean out your chassis (paying special attention to the fan and heat-exchanger assembly) to make sure that there are no obstructions to the air-flow.

Since I, too, rely on a dual-monitor set up with my PanP5 and the issue is not confined to Ubuntu, I'm quite motivated to see this issue resolved.

---

### Post by HotShotDJ on 2011-07-16
> **HotShotDJ said:**
> I believe that this behavior can be controlled using "dword" controls within /etc/X11/xorg.conf, but I haven't tried that method and it could have other unintended consequences.  It has been quite some time since I've messed with dwords and my knowledge on how to use them is quite dated.  I will spend some time this weekend updating my knowledge to find out if there is a way to safely override this behavior.Ok... I've done some research and some testing on my own PanP5. It seems that [http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/) remains the authoritative source regarding Dwords in Linux.  So far, I've found nothing describing other options.

Adding the following to the "Device" section of /etc/X11/xorg.conf has solved the problem for me without a huge impact on my 3d performance.```
Option         "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x2; PowerMizerDefaultAC=0x2"
```You'll need to restart X after making this change -- but you can reboot just to be sure.  What this will do is lock the "Performance Level" to a medium setting.  At least on my system, this is sufficient to drive the external monitor, and give adequate 3d performance (I tested with Google Earth and GLXGears).  I tried to test using the lowest performance level, but it didn't have any effect... the graphics card continued running on the medium setting.

Please let me know if it helps your situation.

UPDATE:  Further testing: I've been monitoring the GPU temperature.  With the above settings, it is pretty much staying at a reasonable 64 C without the chassis fan running at full blast. However, when I run GLXGears, the GPU temp jumps up to 69 - 70 C and the chassis fan runs at full blast.  After stopping GLXGears, the GPU temp decreases very quickly.  It does take several minutes before the chassis fan slows down (it happens once the GPU temp gets down to about 61 C) and again, the temperature stabilizes at 64 C with the chassis fan running slow and quiet.

QUIET MODE (The "M" Button).  Within 1 minute, the GPU was at 75 C (and climbing) whilst running GLXGears.  At that point, I lost my nerve at took my laptop out of quiet mode and the GPU cooled down as previously described.  I recommend against using Quite Mode when running your PanP5 in dual-monitor mode... even with the graphics card dialed back.

**NOTE** This has been tested by me on a System76 PanP5 running OpenSuSE 11.4, Gnome 3.0, Kernel version 2.6.39.3, NVidia binary driver version 275.09.07.  This advise is offered "As-Is."  Always backup your important files before messing around with system configurations and settings.  My liability is limited to the amount you paid me for this advise.  :)

---

### Post by gamerchick02 on 2011-07-16
HotShotDJ,

Thanks for your advice.  Also, thank you for confirming that I'm not going crazy; this issue WAS NOT in Maverick.  Maybe I shouldn't have upgraded...

Anyway.

I'm running the nouveau drivers right now and they're working *crosses fingers*.

I think I'm going to stick with the nouveau drivers and revisit the binary ones every so often.  Buying a laptop made for Linux was supposed to mitigate these issues.

I cleaned my fan out the other day and noticed improved performance overall, but I still get the xorg cpu issue with the binary drivers; it just takes longer to slow down.  Heh.

I was using top to figure out what was going on, but that sensors package is a good idea too.

So, this isn't a hardware issue; it's a software issue.  This is good to know.

I really did think I was going crazy...  Heh.

Thanks again, I really appreciate it!

Amy

---

### Post by HotShotDJ on 2011-07-16
> **gamerchick02 said:**
> Buying a laptop made for Linux was supposed to mitigate these issues.In fairness... the good folks at NVidia made sure that their Windows drivers behave the same way, so you would likely be having an overheating issue in Microsoft land as well.

---

### Post by gamerchick02 on 2011-07-16
That's the funny thing.

I'm not having overheating or slowdowns in Windows 7.

Strange.

Amy

---

### Post by HotShotDJ on 2011-07-16
> **gamerchick02 said:**
> That's the funny thing.

I'm not having overheating or slowdowns in Windows 7.

Strange.

AmyThat IS interesting.  Do you use the fancy Aero effects in Windows 7?  Perhaps your configuration of Windows 7 isn't relying heavily on 3d graphics.  I really can't tell you. :)  It WOULD be interesting to test, but I only run Windows 7 in VirtualBox and I refuse to install it directly to the hardware.  I like to keep Microsoft products safely sand-boxed in a virtual machine where the damage they can do is limited.

BTW:  I still have my external monitor connected with the xorg.conf modifications I mentioned above and I've not had any problems.  At least for me, the issue is resolved, albeit imperfectly.  As it always has been and always will be, with laptops, one must look for satisfactory, if not perfect, compromises between performance, power-usage, and heat.  If you don't need 3d performance, your solution of using nouveau is that satisfactory compromise.  But it would drive me insane, since I love Gnome 3, and Gnome Shell requires 3d graphics.

---

### Post by gamerchick02 on 2011-07-16
I'm not using "fancy-fancy" Aero graphics... I think my card and everything comes out to a 3.5 or something on 7's "suitability index".  I have clear bars and Aero effects, if that's what you mean.  Windows 7 isn't so bad, and I have a partition for it.

The funny thing is that Unity works just fine with the nouveau drivers.  And I thought it required 3D?  Or am I mistaken?

I haven't tried Gnome3 shell.  OT but do you like it?  I kind of like Unity.

Amy

---

### Post by HotShotDJ on 2011-07-16
> **gamerchick02 said:**
> The funny thing is that Unity works just fine with the nouveau drivers.  And I thought it required 3D?  Or am I mistaken?

I haven't tried Gnome3 shell.  OT but do you like it?  I kind of like Unity.

AmyI also thought Unity required 3d.  I wonder if Ubuntu is installing the experimental 3d drivers for nouveau.  You can check in Synaptic Package Manager and search for nouveau to find out.

(OPINION MODE)
I absolutely despise Unity.  To me, it seems very clunky and poorly designed.  It takes ideas from both Gnome Shell (the "dashboard") and OSX (the integrated menu bar) and then mangles them.  It was pushed out in a hurry, and it shows.  In fairness, I DO like the integrated menu bar.  I just didn't like the fact that if my mouse cursor passed over another window on my way to the menu bar, the menu bar changed to the window I passed over -- another example of a good idea poorly implemented.  Perhaps they've fixed that?

Gnome 3, on the other hand, feels much more polished.  It its very smooth and is easy use.  This is not to suggest that it is perfect.  Like Unity, the configuration options are limited, but that is changing.  Gnome 3 has a robust architecture for adding extensions, and little by little, developers are taking advantage of it.  Also, the Gnome developers are actually listening to their users and many of the complaints about Gnome 3.0 are being resolved for Gnome 3.2.  I've spent some time playing with the Gnome Shell extensions, and I'm VERY happy with the results.  A GUI to install these extensions is already available, although I haven't installed and used it yet.
(END OPINION MODE)

I hope that answered your questions.

---

### Post by gamerchick02 on 2011-07-16
> **HotShotDJ said:**
> I also thought Unity required 3d.  I wonder if Ubuntu is installing the experimental 3d drivers for nouveau.  You can check in Synaptic Package Manager and search for nouveau to find out.

(OPINION MODE)
I absolutely despise Unity.  To me, it seems very clunky and poorly designed.  It takes ideas from both Gnome Shell (the "dashboard") and OSX (the integrated menu bar) and then mangles them.  It was pushed out in a hurry, and it shows.  In fairness, I DO like the integrated menu bar.  I just didn't like the fact that if my mouse cursor passed over another window on my way to the menu bar, the menu bar changed to the window I passed over -- another example of a good idea poorly implemented.  Perhaps they've fixed that?

Gnome 3, on the other hand, feels much more polished.  It its very smooth and is easy use.  This is not to suggest that it is perfect.  Like Unity, the configuration options are limited, but that is changing.  Gnome 3 has a robust architecture for adding extensions, and little by little, developers are taking advantage of it.  Also, the Gnome developers are actually listening to their users and many of the complaints about Gnome 3.0 are being resolved for Gnome 3.2.  I've spent some time playing with the Gnome Shell extensions, and I'm VERY happy with the results.  A GUI to install these extensions is already available, although I haven't installed and used it yet.
(END OPINION MODE)

I hope that answered your questions.

Come to think of it, I'm running the experimental drivers.  The 2D ones are the "nv" drivers; I'm running nouveau.

We'll see if Ubuntu spins a Gnome3 version.  I wouldn't mind trying it out; Gnome3 looks pretty nice.  It's default now in Fedora 15 and Fab from Linux Outlaws has been using it all the time; he likes it.

We'll see where Unity goes.  If there's a lot of push-back from people (and people are switching over to Gnome3) they may just use Gnome3.  I know that 11.10 will have Gnome3 as a base, which I'm actually looking forward to.

I've gotten used to Unity.  I'm not waving cheer poms about it, but I find that it works for me (granted, I've gotten used to a lot too).

I agree that it was put out in a hurry.  The whole thing felt mashed when I first tried it; I'm hoping it will mature a bunch more by 11.10.  Right now, it seems pretty stable for me, especially with the nouveau drivers.

Amy

---

### Post by HotShotDJ on 2011-07-17
> **gamerchick02 said:**
> Come to think of it, I'm running the experimental drivers.  The 2D ones are the "nv" drivers; I'm running nouveau.

We'll see if Ubuntu spins a Gnome3 version.  I wouldn't mind trying it out; Gnome3 looks pretty nice.  It's default now in Fedora 15 and Fab from Linux Outlaws has been using it all the time; he likes it.I would definitely encourage you to take Gnome 3 out for a test drive.  You can run it from CD using one of [THESE]("http://gnome3.org/tryit.html").  I recommend the one based on OpenSuSE, since that is the Linux distribution that I'm currently suggesting to most people (we can discuss why in another thread if you're interested.  For now, suffice it to say that I have been discouraged by the direction that Ubuntu has been going over the last several releases).

If you like Unity, I suspect that you'll love Gnome 3. BUT, to each his-or-her own.  One of the advantages of Linux are the choices.  If you don't like one distribution, you can use another.  If you prefer a particular desktop environment, you can usually install it on your current system.  And with the ubiquity of "Live CD" distributions, it is so easy to "try before you buy." 

Now, I'd like to get back to this thread's topic for a moment. :D  Would you mind installing the binary NVidia drivers and then make the adjustments to xorg.conf that I mentioned earlier in this thread.  The reason I ask you to do this is that right now, all I have to go on is a single case (my own) with no external verification.  Also, you were experiencing more severe symptoms than I was, so it would be helpful to find out if my idea solves your problem with the binary drivers.  If we can verify that it works for you, a "how-to" for using twin-view on laptops with NVidia cards could be written.

I hope to talk to you again soon!

---

### Post by gamerchick02 on 2011-07-17
> **HotShotDJ said:**
> Ok... I've done some research and some testing on my own PanP5. It seems that [http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/) remains the authoritative source regarding Dwords in Linux.  So far, I've found nothing describing other options.

Adding the following to the "Device" section of /etc/X11/xorg.conf has solved the problem for me without a huge impact on my 3d performance.```
Option         "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x2; PowerMizerDefaultAC=0x2"
```You'll need to restart X after making this change -- but you can reboot just to be sure.  What this will do is lock the "Performance Level" to a medium setting.  At least on my system, this is sufficient to drive the external monitor, and give adequate 3d performance (I tested with Google Earth and GLXGears).  I tried to test using the lowest performance level, but it didn't have any effect... the graphics card continued running on the medium setting.

Please let me know if it helps your situation.

UPDATE:  Further testing: I've been monitoring the GPU temperature.  With the above settings, it is pretty much staying at a reasonable 64 C without the chassis fan running at full blast. However, when I run GLXGears, the GPU temp jumps up to 69 - 70 C and the chassis fan runs at full blast.  After stopping GLXGears, the GPU temp decreases very quickly.  It does take several minutes before the chassis fan slows down (it happens once the GPU temp gets down to about 61 C) and again, the temperature stabilizes at 64 C with the chassis fan running slow and quiet.

QUIET MODE (The "M" Button).  Within 1 minute, the GPU was at 75 C (and climbing) whilst running GLXGears.  At that point, I lost my nerve at took my laptop out of quiet mode and the GPU cooled down as previously described.  I recommend against using Quite Mode when running your PanP5 in dual-monitor mode... even with the graphics card dialed back.

**NOTE** This has been tested by me on a System76 PanP5 running OpenSuSE 11.4, Gnome 3.0, Kernel version 2.6.39.3, NVidia binary driver version 275.09.07.  This advise is offered "As-Is."  Always backup your important files before messing around with system configurations and settings.  My liability is limited to the amount you paid me for this advise.  :)

Ok.

I've done all the modifications like you suggested, including the xorg change, and I ran glxgears for a couple of minutes... I'm not ever in Quiet Mode (why would someone use that?) and my GPU didn't go up over 70C.  It went up to about 67C, which is fine.  Now I'm at 65C and just running Firefox and the nVidia control panel.

Wow, my computer is quieter than ever with this change.  We'll see how well it does after running for several hours, but right now, all seems well.

I've been documenting all of this nvidia stuff over on my [blog]("http://gamerchick02.posterous.com"), and I will do a write up with this information.  It's not anything official or anything, but any bit of documentation helps.

I was actually going to just go down to the regular laptop display (today, even) and saw your updates in my email.  I decided to give it a go. Now I have a quiet computer running my nVidia GPU the way it's supposed to be.

Thanks.  I'll run the computer "regularly" (browsing, Office, youtube, podcasts, banshee, etc etc) and see if I get slowdowns after 3 hours like I was before.

So, that xorg mod locks the GPU on the "medium" setting, right?  So that will keep the temperature from going up, the performance from degrading, and the CPU from going crazy?  (I'm computer literate, I swear, it's just some of this stuff I don't get...)

Thanks again, HotShotDJ for your help.  It feels good to have the computer running well again.

Amy

---

### Post by HotShotDJ on 2011-07-17
> **gamerchick02 said:**
> So, that xorg mod locks the GPU on the "medium" setting, right?  So that will keep the temperature from going up, the performance from degrading, and the CPU from going crazy?  (I'm computer literate, I swear, it's just some of this stuff I don't get...)Yes... at least that is the hope.  Remember, we are operating under the hypothesis that 1) Running in Twinview mode using NVidia's drivers locks the GPU to its highest setting, creating a lot of heat; 2) Your laptop (and most laptops) have a difficult time dissipating that much heat; 3) the heat is causing your system to become unstable.

Now, we know that 1 and 2 are true.  Now we are checking to see if 3 is true.  It is possible that some other interaction is causing 3, but everything you've described in this thread strongly suggest a problem with heat.

Keep in mind that one of the side effects of locking your GPU on "medium" is that some applications that use heavy 3d effects (Google Earth comes to mind and some Compiz effects) may not perform as well in this mode -- but it should be considerably better than with the nouveau drivers.  And also, when you want to "go portable" with your laptop, you'll probably want to go back to the normal xorg.conf settings.  I can script that for you so that you can just run a simple CLI command, then log out and back in, to switch back and forth between "normal" and twinview mode (PS -- OpenSuSE has a feature that allows me to choose this at boot up or to switch via GUI "on-the-fly" -- not that I would EVER boast or brag... LOL).

-- Actually, I'll bet you could script it yourself. :)

I'll keep my eye on your blog and this thread to see how things work out!

(Oh dear.... I do hope that our friends at System76 don't mind that we did this without them... LOL)

PS:  I read more of your blog.  Nicely done, Amy!  I've added you to my bookmarks.

---

### Post by isantop on 2011-07-18
Oh I don't mind a bit! :D

It's good to hear you guys are getting this solved. I wish I could be more help, but these seemed pretty isolated. I hadn't thought to test with an external monitor. I'll definitely keep this fix in mind for future customers in case we see this problem again.

(As an off-topic aside, I think I saw Amy on Google+. If that was you, congrats on getting in!)

---

### Post by gamerchick02 on 2011-07-18
> **HotShotDJ said:**
> Yes... at least that is the hope.  Remember, we are operating under the hypothesis that 1) Running in Twinview mode using NVidia's drivers locks the GPU to its highest setting, creating a lot of heat; 2) Your laptop (and most laptops) have a difficult time dissipating that much heat; 3) the heat is causing your system to become unstable.

Now, we know that 1 and 2 are true.  Now we are checking to see if 3 is true.  It is possible that some other interaction is causing 3, but everything you've described in this thread strongly suggest a problem with heat.

Keep in mind that one of the side effects of locking your GPU on "medium" is that some applications that use heavy 3d effects (Google Earth comes to mind and some Compiz effects) may not perform as well in this mode -- but it should be considerably better than with the nouveau drivers.  And also, when you want to "go portable" with your laptop, you'll probably want to go back to the normal xorg.conf settings.  I can script that for you so that you can just run a simple CLI command, then log out and back in, to switch back and forth between "normal" and twinview mode (PS -- OpenSuSE has a feature that allows me to choose this at boot up or to switch via GUI "on-the-fly" -- not that I would EVER boast or brag... LOL).

-- Actually, I'll bet you could script it yourself. :)

I'll keep my eye on your blog and this thread to see how things work out!

(Oh dear.... I do hope that our friends at System76 don't mind that we did this without them... LOL)

PS:  I read more of your blog.  Nicely done, Amy!  I've added you to my bookmarks.

I know now it's the second monitor that's causing all of my issues.  I've removed the monitor and now things are working just fine.  But, things are running a little hotter because it's... hotter here.  I hate 90F weather and my computer hates it too.

I just need to write up what we did and tag it properly so people can find it easier.  :)

And thanks for the note about my blog.  It's nice to see a new reader.

Amy

---

### Post by gamerchick02 on 2011-07-18
> **isantop said:**
> Oh I don't mind a bit! :D

It's good to hear you guys are getting this solved. I wish I could be more help, but these seemed pretty isolated. I hadn't thought to test with an external monitor. I'll definitely keep this fix in mind for future customers in case we see this problem again.

(As an off-topic aside, I think I saw Amy on Google+. If that was you, congrats on getting in!)

I thought I was a regular use case with the extra monitor.  I guess not now.

I've removed it in the hopes of keeping the heat down.  

And yes, I'm on G+.  I don't know exactly what I'm doing with it right now, but I have it.  If any of you want an invite, DM me your email and I'll add you.

Amy

---

### Post by isantop on 2011-07-19
Nope, I'm already on as well. +Ian Santopietro

---

### Post by HotShotDJ on 2011-07-19
> **gamerchick02 said:**
> I know now it's the second monitor that's causing all of my issues.  I've removed the monitor and now things are working just fine.  But, things are running a little hotter because it's... hotter here.  I hate 90F weather and my computer hates it too.I've also reduced the frequency and duration of my dual-headed computing. Heat is the arch-enemy of laptops. There are just times when I REALLY need the expanded desktop... usually writing a report while reading journal articles while looking at a spreadsheet full of fun statistics.  At some point, I'd probably be better off getting a full desktop system (with 4 monitors!!!) for my home office.  But when I purchased my PanP5, the goal was to get something that I wouldn't have to replace while I was in grad school.  My little Pangolin has more than fulfilled that goal.  I suspect it will be quite awhile before I need to replace it -- although if anybody felt like buying me [THIS]("http://www.system76.com/product_info.php?cPath=28&products_id=114") (with all the cool upgrades, of course) as a gift, I certainly would not complain. ;)

I'm curious how well the xorg mods controlled your heating problem.  Were you able to eliminate the instability and CPU spikes with the external monitor running?

PS:  Its hot here in Connecticut too!  By the end of the week it is supposed to be be near 100 F.  UGH.  I'm about to loose my resolve not to run the air-conditioning.  I'm all for reducing my carbon footprint, but... I mean REALLY!?!?!  100 F?  In CONNECTICUT?  Even the dalai lama has his limits!

---

### Post by gamerchick02 on 2011-07-19
> **HotShotDJ said:**
> I've also reduced the frequency and duration of my dual-headed computing. Heat is the arch-enemy of laptops. There are just times when I REALLY need the expanded desktop... usually writing a report while reading journal articles while looking at a spreadsheet full of fun statistics.  At some point, I'd probably be better off getting a full desktop system (with 4 monitors!!!) for my home office.  But when I purchased my PanP5, the goal was to get something that I wouldn't have to replace while I was in grad school.  My little Pangolin has more than fulfilled that goal.  I suspect it will be quite awhile before I need to replace it -- although if anybody felt like buying me [THIS]("http://www.system76.com/product_info.php?cPath=28&products_id=114") (with all the cool upgrades, of course) as a gift, I certainly would not complain. ;)

I'm curious how well the xorg mods controlled your heating problem.  Were you able to eliminate the instability and CPU spikes with the external monitor running?

PS:  Its hot here in Connecticut too!  By the end of the week it is supposed to be be near 100 F.  UGH.  I'm about to loose my resolve not to run the air-conditioning.  I'm all for reducing my carbon footprint, but... I mean REALLY!?!?!  100 F?  In CONNECTICUT?  Even the dalai lama has his limits!

It controlled my heat issue pretty well.  I just decided to increase my desk space (you know the thing my laptop sits on, hah!) by getting rid of the second monitor.  I'm actually doing well with just the one panel.  I like having a second monitor, but I'll stick with just the one if I can keep my heat down.

That's a beautiful system.  I wouldn't be opposed to a gift either.  Hah!

I'm a wuss when it comes to the heat.  I hate it, and we're having 90+ temps with very high humidity right now.  Not only is it bad for my computer, it's bad for me, because I sweat horribly.  We've been running the air off and on since May; we got some hot weather then too.

I'm waiting for October and November when things will be nice.  September can still be hot around here, and it's unbearable.  I prefer sweaters and jeans to shorts and t-shirts anyway.

Amy

---

### Post by gamerchick02 on 2011-09-02
Let me resurrect this thread.  (Oh noez, it's the ZOMBIE THREAD come to eat your brains... *NOM NOM NOM*)

I had the runaway Xorg issue AGAIN with the nVidia binary drivers, like I was getting when I had a dual-head setup.

Turns out I was going through my programs and services running, and a little something called "seti" and "einstein_at_home" were mucking about with my CPU.  I wasn't running Boinc, but these processes were running anyway.

It also turns out that the most recent client and service aren't in the repositories.  6.10.x is in the repos, and 6.12 is the current [release]("http://boinc.berkeley.edu/download.php").

I'm going to try the newest version of the software and see if that helps my situation.  I think the program wasn't paying attention to my settings (something like "only use 60% of the CPU) and it was using as much as it could, so it would peg my CPU up to insane levels and force my fan to sound like a 747 taking off.

So, if you run Seti, with a similar setup, it might behoove you to try the newest version of the Boinc client to avoid CPU issues.

Amy (who is glad to have tracked down her issue)

---

