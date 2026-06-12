---
title: "Anyone running 10.04 on PanP5?"
date: 2010-04-20
forum: System76 Support
---

### Post by samalex on 2010-04-20
Hi,

I'm just curious if anyone is running 64-bit 10.04 Desktop on a PanP5 system.  I'm still running 9.04, but I'm really eager to do a clean install of 64-bit 10.04 when it's released in a few weeks.

Also for the System76 guys, do you know if there'll be driver support for the PanP5 when 10.04 is released?

I've been running 32-bit 10.04 in VirtualBox for a while and am sold, but I'm more curious about the hardware support on the PanP5 since 9.04 supported about 100% of the hardware (except the modem) when I got the laptop from System76 last summer.  Also I'm still running the stock version of Ubuntu that was pre-loaded, so I have to admit I'm nervous moving to another version given I've had such good luck with 9.04 thus far.  But I LOVE the bells and whistles of 10.04 plus the Ubuntu One Music Store -- I've already bought a few songs through it.

Thanks and take care --

Sam

---

### Post by thomasaaron on 2010-04-20
> Also for the System76 guys, do you know if there'll be driver support for the PanP5 when 10.04 is released?

Probably for the fingerprint reader. Maybe for power management. Not exactly sure yet.

---

### Post by gamerchick02 on 2010-04-20
> **samalex said:**
> Hi,

I'm just curious if anyone is running 64-bit 10.04 Desktop on a PanP5 system.  I'm still running 9.04, but I'm really eager to do a clean install of 64-bit 10.04 when it's released in a few weeks.

Also for the System76 guys, do you know if there'll be driver support for the PanP5 when 10.04 is released?

I've been running 32-bit 10.04 in VirtualBox for a while and am sold, but I'm more curious about the hardware support on the PanP5 since 9.04 supported about 100% of the hardware (except the modem) when I got the laptop from System76 last summer.  Also I'm still running the stock version of Ubuntu that was pre-loaded, so I have to admit I'm nervous moving to another version given I've had such good luck with 9.04 thus far.  But I LOVE the bells and whistles of 10.04 plus the Ubuntu One Music Store -- I've already bought a few songs through it.

Thanks and take care --

Sam

I am, and it's running well.  I get the odd "Program X has crashed" message, but it seems to be rather harmless.

Everything works really well... I'm really pleased with this upgrade.  I'll be more pleased when Lucid is released and the driver software works, so I can get better fingerprint reader functionality.

Enjoy Lucid. I love it on both my netbook and laptop and I'd recommend this upgrade.

Amy

---

### Post by samalex on 2010-04-21
> **gamerchick02 said:**
> I am, and it's running well.  I get the odd "Program X has crashed" message, but it seems to be rather harmless.

Everything works really well... I'm really pleased with this upgrade.  I'll be more pleased when Lucid is released and the driver software works, so I can get better fingerprint reader functionality.

Enjoy Lucid. I love it on both my netbook and laptop and I'd recommend this upgrade.

Amy

Amy,

Thanks for the reply..  Can you verify that Wifi and Bluetooth work? Someone posted that this isn't working well in Lucid, so just curious.  Also what about HDMI output with audio and video.  That's something my panP5 can't do under 9.04, but I read it was fixed in 9.10 and hopefully in 10.04 as well.  

But I'm loving it in VirtualBox, and it's VERY fast there so hopefully it runs just as fast when installed.

Take care --

Sam

---

### Post by marshmallow1304 on 2010-04-21
I could not get bluetooth or wifi to activate.  I suspect this is because the keyboard shortcuts aren't working, not necessarily because the hardware itself doesn't work because Fn+F1 to turn off the touch pad doesn't work either.

---

### Post by HotShotDJ on 2010-04-21
Hi, Sam --

Unfortunately, the PanP5 will not work "out-of-the-box" with Lucid.  There is a chance that the major problem (ACPI) will be fixed sometime after the release date.  Also, power management issues that were introduced in Karmic for the PanP5 persist and will not likely ever be corrected (some simple configuration changes in the kernel fix it up perfectly, but developers are not interested in it).

Having said that, I'm still happy with my PanP5... but it is not an Ubuntu friendly laptop ... at least not any more.  I'm back to the old days of tweaking, patching and recompiling kernels to get Linux runnning on my hardware -- something I was trying to avoid by purchasing a Linux computer.  Oh well... live and learn.

---

### Post by samalex on 2010-04-22
> **HotShotDJ said:**
> Hi, Sam --

Unfortunately, the PanP5 will not work "out-of-the-box" with Lucid.  There is a chance that the major problem (ACPI) will be fixed sometime after the release date.  Also, power management issues that were introduced in Karmic for the PanP5 persist and will not likely ever be corrected (some simple configuration changes in the kernel fix it up perfectly, but developers are not interested in it).

Having said that, I'm still happy with my PanP5... but it is not an Ubuntu friendly laptop ... at least not any more.  I'm back to the old days of tweaking, patching and recompiling kernels to get Linux runnning on my hardware -- something I was trying to avoid by purchasing a Linux computer.  Oh well... live and learn.

That sucks ...  I bought the PanP5 because it was Ubuntu friendly, so blah if it's no longer that way given it's not even a year old yet.  I know it's not the fault of System76 since they just run with the Canonical punches, but whether from you or System76 I'd love to see some how-tos or info on how to get the PanP5 and Lucid working happily together once Lucid is released -- given the problems you guys are reporting are still present.

Take care --

Sam

---

### Post by HotShotDJ on 2010-04-22
> **samalex said:**
> but whether from you or System76 I'd love to see some how-tos or info on how to get the PanP5 and Lucid working happily together once Lucid is releasedI have every intention of getting Lucid working properly on my PanP5.  I'm carefully documenting what I do and will be more than happy to publish an How-To once I get it right. (I'm stubborn, so it will be "when" and not "if"  LOL)

P.S.  I agree with your assessment that this is not the fault of System76.  Ubuntu developers are screwing the small hardware vendors who WANT to offer Ubuntu, but are unable to promise compatibility for longer than 6 months.  I know that System76 has tried to get the fixes to the Starling wireless card into Ubuntu without success.  Having said that, I would purchase from System76 again in a heartbeat -- Their quality is high, their prices are very competitive, and their customer service is top-notch.

---

### Post by thomasaaron on 2010-04-22
HotshotDJ, I'd be interested in seeing any how-tos you develop.

Samalex, we're testing with the PanP5 now. I should know more in the next day or two.

---

### Post by HotShotDJ on 2010-04-22
> **thomasaaron said:**
> HotshotDJ, I'd be interested in seeing any how-tos you develop.As always, your wish is my command. :)  I've made some good progress and most things on my PanP5 are working properly in my test installation.  I'll post a detailed report as soon as I can.

EDIT:  After many hours of working on this, I'm sorry to report that Lucid RC is simply not compatible with the PanP5.  I THOUGHT I had it working, but all of a sudden, I couldn't get the thing to boot at all.  One of the MAJOR headaches is the new Plymouth boot system.  I don't know how it is working out with other video chipsets, but with NVidia, it is a complete cluster-*.  It has no business being in a LTS.  What were the developers THINKING?

Perhaps once developers get the patched Kernel out with ACPI events functioning, I might be able to get things working properly (one less hurdle to jump is always helpful).  In the meantime, I'm going to test out some other distributions.  Sorry for the disappointing news. :(

---

### Post by thomasaaron on 2010-04-23
> **HotShotDJ said:**
> 
EDIT:  After many hours of working on this, I'm sorry to report that Lucid RC is simply not compatible with the PanP5.  I THOUGHT I had it working, but all of a sudden, I couldn't get the thing to boot at all.  One of the MAJOR headaches is the new Plymouth boot system.  I don't know how it is working out with other video chipsets, but with NVidia, it is a complete cluster-*.  It has no business being in a LTS.  What were the developers THINKING?
:(

I just loaded Lucid RC on our PanP5 last night, and it went smoothly. So far I've partially tested bluetooth, and suspend/resume worked. Function keys combinations may need some work. Battery time doesn't report at all, but it recognizes when it is on ac or battery, and it reports the percentage charged.

---

### Post by HotShotDJ on 2010-04-23
> **thomasaaron said:**
> So far I've partially tested bluetooth, and suspend/resume worked.With which Kernel did you get the bluetooth to work?  Suspend/resume worked via the lid?  Can you get the PanP5 to run at full speed after resume? Did they push out the new patched Kernel while I wasn't looking?  ;)   That would make things MUCH easier!  Tons of questions... LOL -- what did you do differently than I did?  I was so frustrated  that I backed up my /home partition and completely wiped the harddrive and installed OpenSuSE 11.2 (actually worked "out-of-the-box" which quite frankly shocked me!)

---

### Post by samalex on 2010-04-23
> **HotShotDJ said:**
> With which Kernel did you get the bluetooth to work?  Suspend/resume worked via the lid?  Can you get the PanP5 to run at full speed after resume? Did they push out the new patched Kernel while I wasn't looking?  ;)   That would make things MUCH easier!  Tons of questions... LOL -- what did you do differently than I did?  I was so frustrated  that I backed up my /home partition and completely wiped the harddrive and installed OpenSuSE 11.2 (actually worked "out-of-the-box" which quite frankly shocked me!)

Honestly one reason I was sticking with Ubuntu was because it worked great with the PanP5, so if there will be problems with Lucid I'm seriously looking at this as an opportunity to branch out and try another distro.  I even posted the question to some in our LUG to see what they suggest, but good to hear OpenSuSE worked since that's one I'd love to try again since I used to run it on my main desktop years ago.

Also when you said Everything worked under OpenSuSE is that *everything*? -- webcam, modem (is that a pipe dream?), bluetooth, wifi, suspend, etc. Honsetly I'm not a huge fan of Ubuntu's release cycle every 6 months, instead I'd rather see a solid system every 8-12 months.  Seems both Karmic and probably now Lucid will both be buggy outta the gate.

Thanks -

Sam

---

### Post by thomasaaron on 2010-04-23
> With which Kernel did you get the bluetooth to work? 

******.32-21
I'm having other folks complain about BT, though. It could be that something was hosed in upgrading from alpha/beta, etc...

> Suspend/resume worked via the lid?

Nope.

> Can you get the PanP5 to run at full speed after resume?

That'll take a bit more testing, but I've put it on the white board.

 what did you do differently than I did?[/QUOTE]

Just a fresh install of RC from a CD.


EDIT: Just got this from another customer -- regarding BT.
> Yes, I can confirm that the issue appeared after an update, and happened at the 14th of april, or the day before or after. but I upgraded from karmic to lucid after the 10th of april so it was already in beta2 I guess

---

### Post by HotShotDJ on 2010-04-23
> **samalex said:**
> but good to hear OpenSuSE worked since that's one I'd love to try again since I used to run it on my main desktop years ago.
Well... I'm having major problems with multimedia in OpenSuSE 11.2.  I can't get AV chat working properly in pidgin (I can get video, but the microphone refuses to work with pidgin, although it seems to be just fine with everything else).  Lets see what I can find out.

EDIT:  Ok... multimedia isn't really a problem.  It was just me not being familiar with how to do things the "SuSE way" -- BUT, still no microphone in Pidgin (or Empathy).  I have no idea WHAT the issue is.  Microphone works swimmingly in every other application I've tried.  Just nothing but rhythmic tapping for A/V chat.

(Interestingly, I have the same problem with my friend's starling in Karmic and Lucid)

EDIT 2: Microphone actually DOES work fine in Pidgin and Empathy. The issue was with the other person's computer.

---

### Post by HotShotDJ on 2010-04-26
> **samalex said:**
> Also when you said Everything worked under OpenSuSE is that *everything*? -- webcam, modem (is that a pipe dream?), bluetooth, wifi, suspendHi, Sam --

I'm sorry it took so long for me to respond, but I wanted to be running OpenSuSE for several days, including at work.  I didn't test the modem -- I don't have a landline (no point to having one anymore!), or HDMI (I don't have any hardware upon which to test it).  I CAN tell you that the Sound Preferences list HDMI options.

The following worked out-of-the-box: Webcam, Bluetooth, Wifi, Suspend/Resume, Hibernation , VGA output (I run dual-headed most of the time).  One caveat: After resuming from suspend, my CPU is "stuck" at its slowest speed (800 mHz) -- I can get it back by changing the governor (from Ondemand to Performance or Conservative) -- but nothing but a reboot will get the Ondemand governor to work after resuming from suspend.  THis does not occur with a resume from hibernation.  This is also true in Ubuntu (Karmic and Lucid).

The following worked with minor tweeking: Sound Card -- While it worked out-of-the-box, it worked BETTER by adding the following line to /etc/modprobe.d/50-sound.conf```
options snd-hda-intel model=3stack-dig
```For whatever reason, I cannot get Pidgin or Empathy to work with the internal microphone, although Sound Recorder uses it without a problem.

EDIT:  Internal microphone works just fine with Pidgin and Empathy.  Something was wrong on the other end of the connection.

The following does not work at all:  Yast2-Finger Print Reader.  Even after installing the proper drivers (using modified fprint.py from the System76 Driver package) and confirming that it works with fprint-demo, I couldn't get the Yast2 Finger Print Reader to recognize the fingerprint device.  So, while I can verify that with a little bit of effort, you can get fprint-demo up and running properly, I cannot tell you if it would actually work as intended (for logging in, sudo, etc) since I didn't go that far with the testing (I never used it in Ubuntu other than to play with it once in awhile).

Hopefully that helps you with your decision making.  I will probably keep OpenSuSE for now. It does NOT have all the social networking stuff built in and integrated with the desktop, which is a positive for me.  Others may like that stuff.

---

### Post by gamerchick02 on 2010-04-27
> **samalex said:**
> Amy,

Thanks for the reply..  Can you verify that Wifi and Bluetooth work? Someone posted that this isn't working well in Lucid, so just curious.  Also what about HDMI output with audio and video.  That's something my panP5 can't do under 9.04, but I read it was fixed in 9.10 and hopefully in 10.04 as well.  

But I'm loving it in VirtualBox, and it's VERY fast there so hopefully it runs just as fast when installed.

Take care --

Sam

Sorry this is late; I haven't been around much.

Wifi works just fine, but I haven't really tested beyond my house.  I'd say it's good up to 50 ft or more.

I don't use bluetooth anything.  I guess I could try to hook up my Wiimote to the laptop...

Regarding HDMI... I don't have anything that does HDMI. If it's fixed in 9.10, it should stay fixed in 10.04.

Amy

---

### Post by popalor on 2010-04-27
I am running 10.04 RC on my PanP5 and it seems to be going well.  
Pros:
1. It is quick to boot up
2. New apps are pretty cool
3. A lot of things that didn't work well (sound, battery indicator),that   didn't work well in 9.10 work now
Cons:
1. Suspend doesn't function at all so far as I can tell.

---

### Post by thomasaaron on 2010-04-28
> 1. Suspend doesn't function at all so far as I can tell. 

It works on our shop machine if you access it through the shutdown menu. Doesn't work when lid is closed (lid switch not working).

Please press Fn-F12 and see if your Bluetooth icon appears. We're having difficulty duplicating inop bluetooth reports.

---

### Post by popalor on 2010-04-28
> **thomasaaron said:**
> It works on our shop machine if you access it through the shutdown menu. Doesn't work when lid is closed (lid switch not working).

For me it suspends beautifully, but waking it back up is not working at the moment.  

> **thomasaaron said:**
> 
Please press Fn-F12 and see if your Bluetooth icon appears. We're having difficulty duplicating inop bluetooth reports.

No bluetooth icon appears for me.  I can't get the bluetooth daemon to start.  What should the bluetooth show up as in 'lshw' or a similar command?

---

### Post by thomasaaron on 2010-04-28
Please run...

sudo /etc/init.d/bluetooth restart

Then try pressing Fn-F12 and see if the BT icon appears.

---

### Post by popalor on 2010-04-28
No such luck with restarting it.

---

### Post by PGScooter on 2010-06-04
has anyone had any luck solving the issue of the CPU frequency being stuck on suspend-resume? I'm still having this problem on the PanP5

---

### Post by HotShotDJ on 2010-06-05
> **PGScooter said:**
> has anyone had any luck solving the issue of the CPU frequency being stuck on suspend-resume? I'm still having this problem on the PanP5As am I. I'm not sure that there is anybody working on the issue (and, quite frankly, I haven't been putting much effort into it myself).  I'm sure that it is NOT an Ubuntu issue, as I have the same problem with OpenSuSE 11.2 on my PanP5.

---

### Post by miniyak on 2010-06-06
interesting i guess i haven't been paying attention enough to notice the issues mentioned. Im dual-booted w/ 9.10 right now and ive been using 9.10 most of the time because i would have to set up my wacom bamboo pen again in lucid. (havn't got the time)

As far as features go, i noticed 

-wsxga+&twin view (tested w/1080p) is now supported w/out proprietary nvidia driver 
-boots faster
-i like the new social features

Power management quirks have always seemed to be an issue with the panp5. problems w/ stand-by are always the deal-breaker w/ me as i use it everyday. i can live with other issues if i have no time to look into it myself. Overall i saw nothing too alarming with 10.04 besides that fact that my bamboo pad still doesn't work "out of the box", which was expected.

---

### Post by samalex on 2010-06-07
I still haven't gotten around to installing 10.04 (still running 9.04), but on my current setup I have the CPU Frequency selector setup on the menu bar and I often have to kick it to full after reboot or wake.  Could something like this 'fix' the problem?  It's a manual process, but honestly I'm used to doing it already under 9.04.

But are you guys seeing that changing this doesn't keep the setting, given the system doesn't hibernate or is restarted?

Sam

---

### Post by ginor on 2010-06-07
I have been running 10.04 for about a week now and am trying to figure out why my boot time is running about 35-40 secs and also Firefox is also very slow downloading any website. I installed 10.04 instead of upgrading and have made NO changes to configuration or hardware on my PanP5. It had 9.04 pre-installed when I received it from System76.  Other than the speed problem, I see no other problems with the new OS version. 
It does bother me though that it is slower in both areas that the previous (9.04) so I would like any hints that might lead me to solving the speed problem.



Panp5 w/ Intel P8700; 4GB Ram; NVidia G105M 512MB.; 320 GB 5400rpm SATA II

---

### Post by PGScooter on 2010-06-07
> **samalex said:**
> I still haven't gotten around to installing 10.04 (still running 9.04), but on my current setup I have the CPU Frequency selector setup on the menu bar and I often have to kick it to full after reboot or wake.  Could something like this 'fix' the problem?  It's a manual process, but honestly I'm used to doing it already under 9.04.

But are you guys seeing that changing this doesn't keep the setting, given the system doesn't hibernate or is restarted?

Sam

This does fix it. But for some reason I never got used to it... it's still a pain :)

---

### Post by HotShotDJ on 2010-06-07
> **samalex said:**
> I have the CPU Frequency selector setup on the menu bar and I often have to kick it to full after reboot or wake.  Could something like this 'fix' the problem?Well, sort of.  After resuming from suspend, choosing another governor will correct the problem.  Of course, so does a reboot (rather defeating the purpose of suspending I would think).

Unfortunately this only treats the symptom, which, in the words of the great philosopher Jack Nicholson, may be "As Good As It Gets." :)

Like I said before, I can't really complain very loudly as I haven't filed any bug reports or spent any significant time researching this particular problem.

---

### Post by isantop on 2010-06-08
> **ginor said:**
> I have been running 10.04 for about a week now and am trying to figure out why my boot time is running about 35-40 secs and also Firefox is also very slow downloading any website. I installed 10.04 instead of upgrading and have made NO changes to configuration or hardware on my PanP5. It had 9.04 pre-installed when I received it from System76.  Other than the speed problem, I see no other problems with the new OS version. 
It does bother me though that it is slower in both areas that the previous (9.04) so I would like any hints that might lead me to solving the speed problem.



Panp5 w/ Intel P8700; 4GB Ram; NVidia G105M 512MB.; 320 GB 5400rpm SATA II

You should definitely be pulling faster than 35-40 seconds on boot. That's not a bad configuration.

Could you try booting up from a LiveCD (Or even better, a bootable flash drive) and checking if your firefox problems persists in a fresh environment? You don't need to reinstall.

This could be a slight problem with your particular install CD. We can rule that out now.

---

### Post by ginor on 2010-06-08
"[I]Could you try booting up from a LiveCD (Or even better, a bootable flash  drive) and checking if your firefox problems persists in a fresh  environment? You don't need to reinstall.

This could be a slight problem with your particular install CD. We can  rule that out now."

[/I][U]Thanks isantop for the suggestion. I will give it a try at my next opportunity and let you know!
[/U]

---

### Post by ginor on 2010-06-09
Well, I booted with the 2 Live CD's I had  (the free one from Ubuntu and the other from LinuxCD.com). They both had the same response on Firefox. It seems to be more of a lookup delay than a download problem so it may be the way the local DNS nameserver is chosen altough 0.7ms doesn't seem too bad on a ping reply.
I'm more concerned about correcting the boot time as it may be indicative of some problem in configuration.If not I can live with it.

---

### Post by isantop on 2010-06-09
Could you try a fresh install to a separate partition? That way we could see how fast it's booting, since liveCDs don't give you an accurate idea.

---

### Post by ginor on 2010-06-09
Just as an additional bit of info, this is my second install. I tried first with the free CD from Ubuntu and had the slow boot-up problem. I then used the purchased LinuxCD 10.04 and re-installed only to find the boot-up time about the same. I can do it anther time, but not really sure if it will be different. 
Is there somewhere I can see where it could be hanging up in the boot process giving an error message or such? Also what should be the typical boot time on 10.04? I never clocked it on 9.04 but it seemed faster.
Thanks, by the way for your suggestions, isantop!

---

### Post by jdb on 2010-06-09
> **ginor said:**
> Just as an additional bit of info, this is my second install. I tried first with the free CD from Ubuntu and had the slow boot-up problem. I then used the purchased LinuxCD 10.04 and re-installed only to find the boot-up time about the same. I can do it anther time, but not really sure if it will be different. 
Is there somewhere I can see where it could be hanging up in the boot process giving an error message or such? Also what should be the typical boot time on 10.04? I never clocked it on 9.04 but it seemed faster.
Thanks, by the way for your suggestions, isantop!

Booting from a CD is always very slow.
What Isantop is saying is that you need to install it to disk & then boot to check the boot time.
You can install to an empty partition & not disturb your existing system.

jdb

---

### Post by ginor on 2010-06-09
Ok jdb, will give that a try as soon as I am back in town in about a week. 
Thanks also for your input!

---

