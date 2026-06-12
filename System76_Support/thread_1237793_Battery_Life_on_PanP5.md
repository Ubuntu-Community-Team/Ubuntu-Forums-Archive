---
title: "Battery Life on PanP5"
date: 2009-08-11
forum: System76 Support
---

### Post by samalex on 2009-08-11
Hi...

I've been lovin' my PanP5 Laptop for the last few days.  I finally got almost everything tweaked the way I'd like, but i'm wondering if I made the right move going with a 7200 rpm drive because after my last reboot i only got 45 minutes from the battery.

Any tips or tricks on how to get this up to at least an hour and a half outside of the normal things like reducing screen brightness, etc?  Any kernel or system tweaks to speak of?

Thanks --

Sam

---

### Post by HotShotDJ on 2009-08-11
> **samalex said:**
> I've been lovin' my PanP5 Laptop for the last few days.  I finally got almost everything tweaked the way I'd like, but i'm wondering if I made the right move going with a 7200 rpm drive because I'm getting 45 minutes to an hour tops from the battery.45 min to an hour?  I hope that this is a configuration error or a bad battery that System76 will replace.  That battery run time, if typical for the Pangolin, would be a deal-breaker for me.  Following this thread with high interest as I was looking forward to purchasing a Pangolin for myself.

---

### Post by XKCD64 on 2009-08-11
Ditto.  I would NEVER buy one if this is true.

---

### Post by samalex on 2009-08-11
The only thing I can think of that may have drained the power was I had VirtualBox going running Windows XP.  I've gotten about an hour and a half another time, so I'm trying to track down exactly what drained the power this go around.

The Gnome Power Manager had a chart showing power history so I'll let the battery charge to 100% then test various scenarios to see how much I can squeeze out of it.

Some things that worry me are the Device Information in Gnome Power Manager lists the capacity at 88% (Fair), but when I got the laptop it was only at 94% Capacity.  Does this mean only 88% of the battery is available to use?  I wonder if this is a bum battery.

I'll keep some notes on battery life and what's running to see if I can track down what's going on.

XKCD64 and HotShotDJ... there's something going on here, so please don't take this as a deal breaker if you're looking at the PanP.  This laptop is truly awesome and this is the first issue with battery life I've heard of, and I've been researched this laptop for well over a year.  I'll do some more research and tests and email tech support to see if they have any suggestions.  

Sam

---

### Post by XKCD64 on 2009-08-11
Yeah, you probably got to drain it and fully charge it each and every time.  

On my laptop (not a system 76) it's currently at 95%, and I was told by Best Buy that it's because I charge it before it's all drained (if it's low and I need to take it with me....) and because I don't fully charge it EVERYTIME (It's almost charged and I have to go NOW with it...)

---

### Post by HotShotDJ on 2009-08-11
> **XKCD64 said:**
> Yeah, you probably got to drain it and fully charge it each and every time.This is absolutely untrue with modern, lithium ion batteries.  It WAS true with older battery technology (such as NiCad).  Lithium Ion batteries have no memory effect.

Having said that, they should be calibrated in your laptop.  When one gets a new battery (or new laptop with a, presumably, new battery) they should follow the following steps:

1) Fully charge the battery over night before using it the first time.
2) Discharge the battery in your laptop all the way until the laptop warns that your battery is critically low (3% - 5%)
3) Repeat for 2 or 3 full charge/discharge cycles.

> Unlike nickel and lead-based batteries, a new lithium-ion pack does not need cycling through charging and discharging. Priming will make little difference because the maximum capacity of lithium-ion is available right from the beginning. Neither does a full discharge improve the capacity of a faded pack. However, a full discharge/charge will reset the digital circuit of a 'smart' battery to improve the state-of-charge estimation

SOURCE: [http://www.batteryuniversity.com](http://www.batteryuniversity.com)  (A LOT of great information at that site!)

After this initial calibration, you can plug the battery in to charge at any point during the discharge cycle.  You should run a full discharge/recharge cycle every 3 to 4 weeks.

Samalex:  After you do the initial calibration, could you let us know if it helps?  I would be VERY happy if your problem is simply an uncalibrated battery/laptop kit. :)

---

### Post by HotShotDJ on 2009-08-11
> **samalex said:**
> XKCD64 and HotShotDJ... there's something going on here, so please don't take this as a deal breaker if you're looking at the PanP.  This laptop is truly awesome and this is the first issue with battery life I've heard of, and I've been researched this laptop for well over a year.  I'll do some more research and tests and email tech support to see if they have any suggestions.  

SamUnderstood and I am inclined to agree with your assessment.  Where I've seen estimates of battery run-time for the Pangolin, it has been 2 - 2.5 hours.  Since the Pangolin (as far as I can tell) is something of a compromise between a true "desktop replacement" system and a portable system, 2 to 2.5 hours of battery time seems reasonable on a 6 cell battery. (for comparison, my Dell E1505, which is a very low-end laptop, gets 2.5 hours on a new 6 cell and 4.2 hours on a new 9 cell)

---

### Post by samalex on 2009-08-11
I had it charged to 100% while at work earlier, but unplugged it to show a co-worker in another office for about 30 minutes on battery then shut down and brought home.  Then this evening I turned it on and within 15 minutes it was at 6% which is what prompted the original post.

It's been charging now for 1 hour and 25 minutes and it's up to 71% charged. When it's at 100% I'll start casually surfing with no VirtualBox and see how long it takes to go down.  As I said before a couple of nights ago I got almost 90 minutes out of it, so I'm wondering if VirtualBox running XP on a 7200 RPM drive is the culprate.

I doubt I'll be up long enough to test the power tonight (it's already 9:30pm) but if not tonight I'll watch it at work tomorrow.

Sam

---

### Post by miniyak on 2009-08-11
An Hour and 45 minutes is about right for the pangolin with normal usage. I can imagine virtualbox cutting down that time significantly.

best power saving feature so far for me is turning the wireless card off. Obviously this is only so practical though. I think I got about two hours with the wireless off. (playing standard def video content through miro.. i may have got better results if i had played the file directly with Mplayer)

another quick and easy power saving feature is the silent mode button. (the third hot key on the top left of the key board, the one with the M) This throttles the fan and the cpus(1.6ghz). For some reason i get the feeling that this only adds about 10 to 15 minutes of extra time though

throttling to 800ghz per cpu should in theory save more, but I think it is a negligible difference. It also has the compromise of slowing down HD content and unwieldy firefox sessions. Plus i'm sure virtualbox would be unusable in this state (maybe 1.6 too)

once i get wireless working in puppy ill tell you if i see better battery life there (minimal linux distro that runs from ram mainly)

---

### Post by miniyak on 2009-08-11
i also have the 7200rpm drive btw.. im sure i could do better in terms of battery life with out it. (my grandfather convinced me to upgrade to compare with a dell..... hmph) However it may not make much of a difference in terms of minutes saved though.

---

### Post by HotShotDJ on 2009-08-11
> **samalex said:**
> It's been charging now for 1 hour and 25 minutes and it's up to 71% charged. When it's at 100% I'll start casually surfing with no VirtualBox and see how long it takes to go down.  As I said before a couple of nights ago I got almost 90 minutes out of it, so I'm wondering if VirtualBox running XP on a 7200 RPM drive is the culprate.Assuming that the battery itself is not the problem, and that it has been calibrated to your laptop properly, here are some things that might be useful in diagnosing this:

Add two "CPU Frequency Scaling Monitors" to your gnome panel -- set one to CPU 0 and the other to CPU 1.

Add the system monitor to your panel and set preferences (right click the monitor and select preferences) and check off "Processor" and "Harddisk" -- this will give you two graphs, one for processor and one for the harddisk.  There are several other monitors that you can check off, but I'm not sure how useful they will be -- maybe "Load" would also be helpful.  

Now you can actively see your CPU scaling, CPU usage, and Harddrive read/writes in real-time.

Click on the CPU Frequency Scaling Monitors and make sure they are set to "On-Demand" -- from all my reading, this is the least power hungry setting, even compared to "Conservative" or "Powersave"

Finally, click on the Power Management applet in your system tray -- in the "On Battery Power" tab, make sure that "Reduce Backlight Brightness" and "Dim display when idle" boxes are checked.  In my experience, these two settings significantly increase battery run time.

EDIT:  I just ran some tests on my Dell E1505 to see what effect Windows XP running under VirtualBox 3.0.4 has on system loads.  I really don't think this is your problem. I'm not seeing any difference between running Windows apps in VBox vs. similar native apps on CPU usage, CPU scaling or Harddrive Read/Write access.

My test was this.  Open Windows XP/VirtualBox, Open Microsoft Word 2007.  Type a couple sentences (I used a magazine article that was handy and just typed the first two sentences.).  I made a mental note of the activities I saw on the monitors, and then closed Word without saving the document.  Leaving XP/VBox open but with no applications running, I switched desktops and ran OpenOffice Writer 3.1 and typed the same sentences, also making note of the activities I saw on the monitors.  I did not notice any difference in CPU Frequency Scaling, processor activity, or harddrive read/writes. And remember, this is without hardware virtualization and with only 2G ram.  Your results should be even better than mine, since you have twice the RAM and hardware virtualization support with your CPU.

I then added the "Load" monitor to my panel.  Again, no difference.  It looks like an XP session under VirtualBox produces no greater loads on your system than any other active application.  I've also checked with idling... that is, doing nothing at all... just having the computer sitting there with VBox/XP open, but doing no work.  The system monitors and CPU Frequency monitors are identical to an idle system without VBox/XP open.

CONCLUSION: At baseline and for word processing, Running VirtualBox with an XP VM creates no greater drain on your system than using native applications.  Of course, your mileage will vary depending on the applications your running in XP and the host.

Maybe I'll look and see if I can get the data from these monitors dumped in real-time to a comma-delineated text file.  Then I could import the data to SPSS and run some more accurate statistical analyses -- ok... my "geek" is showing.  LOL.

---

### Post by samalex on 2009-08-12
This morning I charged the battery to 100%, shut down, unplugged power, and powered it back up.

I do have wireless enabled, but the only application I'm running is Amarok to listen to MP3's, no email client or anything else going.  I'm checking Gnome Power Manager periodically and noting the changes, plus i have the Power History on screen.  

When it's down to 2%-3% I'll make a screenshot of the Power History and post it plus my log to the forum, then charge it to 100% and try it again but with VirtualBox along with some other applications I normally run (Skype, Pidgin, Evolution, etc).

The Design Charge is at 48.8 Wh but the last full charge was only 43.8 Wh which is where I think how it's calculating the Capacity of 88%.  I wonder if this is normal...

Once I go through a couple of cycles from 100% to 0% I'll see if it increases the Last Full Charge.  

At this point the laptop has been going for about 45 minutes (started at 8:55am and it's now 9:40am) and Gnome Power Manager shows 58% charge and 1 hour 3 minutes until discharge which actually isn't bad and MUCH better then I got yesterday.

I'll keep tracking and post updates when it hits 0%.

Sam

---

### Post by samalex on 2009-08-12
The battery just died and shut down the laptop, and i got about an hour and 35 minutes on the charge.  Below is my log and attached are screenshots of the power history and also the final Device Info from Gnome Power Manager.

The first hour or so went smooth, but most of the last 20-30 minutes i had the screensaver going which is Hyperspace, and it seemed the battery dropped much quicker during that time.  I wonder if just a blank screen would've been better.  I changed to hyperspace from GLMatrix thinking that would be less taxing, but I guess both taxed the video card which sucked more juice.

After it shut down I plugged the power in where it's already up to 8% charged (it's 10:38am now).  

Anyway, review my logs and screenshots, and when it's back to 100% I'll shut down once more and do more testing plus see what the Last Full Charge capped out at.  Maybe it'll be more than the 41.3 Wh it has been.  Also I'll test with more applications open and change the screensaver to just blank screen.

Also thinking back to yesterday when the system drained so quickly, I did have the GLMatrix screensaver going for about 25 minutes of that, so maybe that was the culprit.  The screen saver is set to blank screen, so we'll see on the next go around.  

Sam


> 
8:55am - 100% - Reboot
8:55am - 99% - Start up on Battery
- From Gnome Power Manager
-  Charge Time - 1 hour 12 minutes
-  Discharge Time - 1 hour 36 minutes
-  Capacity - 88%
-  Current charge - 37.5 Wh
-  Last full charge - 43.3 Wh
-  Design charge - 48.8 Wh
- Screen Brightness at about 60%
- Starting Amarok to play MP3's

9:03am - 91%
- Discharge Time - 1 hour 51 minutes
*Hmmm, less percentage but more Discharge time*

9:09am - 86.0%
- Discharge Time - 1 hour 45 minutes

9:21am - Screensaver GLMatrix Started

9:27am - 69.0%
- Discharge Time - 1 hour 12 minutes
- Current charge - 30.3 Wh

9:30am - 66.0%
- Changed screensaver to Hyperspace
- Discharge Time - 56 minutes
- Current charge - 28.7 Wh

9:43am - 52.0%
- Discharge Time - 51 minutes
- Current charge - 22.8 Wh

9:45am - Made screenshot of Power History and opened in Gimp -- Worked great!

9:55am - 42%
9:56am - Screensaver kicks in - Hyperspace

10:20am - 14% -- 
- Discharge Time - 13 minutes
- Current charge - 6.1 Wh

10:30am - 2%
- Discharge Time - 2 minutes
- Current charge - 0.9 Wh

10:31am - System shut down


---

### Post by jdb on 2009-08-12
> **samalex said:**
> The battery just died and shut down the laptop, and i got about an hour and 35 minutes on the charge.  Below is my log and attached are screenshots of the power history and also the final Device Info from Gnome Power Manager.

The first hour or so went smooth, but most of the last 20-30 minutes i had the screensaver going which is Hyperspace, and it seemed the battery dropped much quicker during that time.  I wonder if just a blank screen would've been better.  I changed to hyperspace from GLMatrix thinking that would be less taxing, but I guess both taxed the video card which sucked more juice.

After it shut down I plugged the power in where it's already up to 8% charged (it's 10:38am now).  

Anyway, review my logs and screenshots, and when it's back to 100% I'll shut down once more and do more testing plus see what the Last Full Charge capped out at.  Maybe it'll be more than the 41.3 Wh it has been.  Also I'll test with more applications open and change the screensaver to just blank screen.

Also thinking back to yesterday when the system drained so quickly, I did have the GLMatrix screensaver going for about 25 minutes of that, so maybe that was the culprit.  The screen saver is set to blank screen, so we'll see on the next go around.  

Sam

Does the fan speed increase when the screen saver is on?
I you have another linux computer you can ssh into the PanP5 when the screen saver is on & run top.
Even if the cpu isn't being taxed, the video card might be.
I think you've nailed it.
I'll bet if you let it go straight to screen saver & leave it there the battery will discharge in record time. ](*,)
jdb

---

### Post by samalex on 2009-08-12
[QUOTE="jdb"]Does the fan speed increase when the screen saver is on?
I you have another linux computer you can ssh into the PanP5 when the screen saver is on & run top.
Even if the cpu isn't being taxed, the video card might be.
I think you've nailed it.
I'll bet if you let it go straight to screen saver & leave it there the battery will discharge in record time. [/QUOTE]

I didn't notice the fan turning on, but it may have... As for the video card and screensaver, I installed SSH and connected in from another system.  When I did a preview on the GLMatrix screensaver it did sit at about 18%-21% CPU usage depending on how involved the screen was.  I suppose sustained over 20-30 minutes this would drain the battery. 

While I had top open I launched VirtualBox, and while booting it used 100% or more of CPU (peaked at 103%), but when I logged into Windows it settled down to about 10%.  Watching it though it goes back and forth, going as low as 5% but spiking to 75% or more at times with no activity by me (sitting at blank desktop).  Also System Monitor through Gnome shows both processors are all over the map as XP is going in VirtualBox.  This must've contributed to the drain yesterday as well. 

I'll continue running some tests, but it looks like with average use and the screen saver only blanking the screen, I may get 1:45 - 2:00 out of it, but the Last Full Charge of only 41.3 Wh where the Design Charge is 48.8 has me worried that the battery may have issues.  I'll let it charge to 100% and see what it is, then unplug the power and let it deplete again in hopes that this'll improve.

And for the other suggestions, on battery I do have it set to dim display when idle and reduce backlight brightness.

Thanks --

Sam

---

### Post by jdb on 2009-08-12
> **samalex said:**
> I didn't notice the fan turning on, but it may have... As for the video card and screensaver, I installed SSH and connected in from another system.  When I did a preview on the GLMatrix screensaver it did sit at about 18%-21% CPU usage depending on how involved the screen was.  I suppose sustained over 20-30 minutes this would drain the battery. 

While I had top open I launched VirtualBox, and while booting it used 100% or more of CPU (peaked at 103%), but when I logged into Windows it settled down to about 10%.  Watching it though it goes back and forth, going as low as 5% but spiking to 75% or more at times with no activity by me (sitting at blank desktop).  Also System Monitor through Gnome shows both processors are all over the map as XP is going in VirtualBox.  This must've contributed to the drain yesterday as well. 

I'll continue running some tests, but it looks like with average use and the screen saver only blanking the screen, I may get 1:45 - 2:00 out of it, but the Last Full Charge of only 41.3 Wh where the Design Charge is 48.8 has me worried that the battery may have issues.  I'll let it charge to 100% and see what it is, then unplug the power and let it deplete again in hopes that this'll improve.

And for the other suggestions, on battery I do have it set to dim display when idle and reduce backlight brightness.

Thanks --

Sam

This is from my Daru2 which I've had for over a year & a half.

```
13:26:17 ~ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         4800 mAh
last full capacity:      4445 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            MS-1221

serial number:           

battery type:            LION

OEM info:                MSI Corp.

13:26:24 ~ cat  /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      4445 mAh
present voltage:         16507 mV
```

(1 - 4445/4800) * 100 = 7% down from design capacity.

I have never purposely recycled my battery & don't let it run all the way down very often.
I leave it on the charger whenever it is on my desk which is most of the time & I still
get over three hours on battery.

The one thing that has the most effect on a lithium ion battery is how many times it has
been deeply discharged so it is probably not a good idea to do that very often if you
are not actually away from AC power.


jdb

---

### Post by HotShotDJ on 2009-08-12
> **samalex said:**
> The battery just died and shut downCould you clarify this please.  Did the laptop shut down properly, or was it a hard shut down (more like unplugging a desktop computer)?  In any case, the more you tell us, the more I suspect a faulty battery.

Apparently, Thomasaaron has left for vacation. (see: [http://ubuntuforums.org/showthread.php?t=1237481](http://ubuntuforums.org/showthread.php?t=1237481)) but I wouldn't wait.  If the next full charge isn't reaching design capacity, then email System76 and report the problem.

I hope this gets worked out.  With the exception of this SNAFU, the Pangolin looks like a great machine.

---

### Post by samalex on 2009-08-12
[QUOTE="HotShotDJ"]
Quote: Originally Posted by samalex
The battery just died and shut down
Could you clarify this please. Did the laptop shut down properly, or was it a hard shut down (more like unplugging a desktop computer)? In any case, the more you tell us, the more I suspect a faulty battery.[/QUOTE]

When the laptop battery was completely depleted I assume it went into hibernate mode and shut down.  When I plugged the power back in and turned it on, it came into Linux where it was before, even picking-up the MP3 where it left off which was nice.  

> I hope this gets worked out. With the exception of this SNAFU, the Pangolin looks like a great machine. 

Honestly looking at the capacity of the battery, I'm wondering if it's just a bum battery because if I'm only at 84% capacity and it's getting 1:30 to 1:45, at 100% or close to that capacity it should be well into the two hour range.  

Also it just hit 100% so here's what I have:

```

alarm:                   unsupported
present:                 yes
design capacity:         4400 mAh
last full capacity:      3725 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M740TX
serial number:            
battery type:            LION
OEM info:                Clevo CO.
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      3725 mAh
present voltage:         14800 mV

```

Comparing this to jdb's output, I'm sitting at about 15.3% loss in battery capacity (1 - 3725 / 4400) and it's less than a week old.  I'll let it sit on the charger for some more time and see if it goes beyond 3725 mAh, but given it says 'charged' I wonder if it's topped out.  This is what it was before I did the test.

In Thomas's absence I'll email support and see if they have any suggestions or options.

Also I've added a screenshot from the Gnome Power Manager showing battery capacity is down to 84%.  This is down 4% from the [screen shot I posted earlier today]("http://ubuntuforums.org/attachment.php?attachmentid=124574&d=1250091296") which showed 88%.

Sam

---

### Post by jdb on 2009-08-12
> **samalex said:**
> When the laptop battery was completely depleted I assume it went into hibernate mode and shut down.  When I plugged the power back in and turned it on, it came into Linux where it was before, even picking-up the MP3 where it left off which was nice.  



Honestly looking at the capacity of the battery, I'm wondering if it's just a bum battery because if I'm only at 84% capacity and it's getting 1:30 to 1:45, at 100% or close to that capacity it should be well into the two hour range.  

Also it just hit 100% so here's what I have:

```

alarm:                   unsupported
present:                 yes
design capacity:         4400 mAh
last full capacity:      3725 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M740TX
serial number:            
battery type:            LION
OEM info:                Clevo CO.
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      3725 mAh
present voltage:         14800 mV

```

Comparing this to jdb's output, I'm sitting at about 15.3% loss in battery capacity (1 - 3725 / 4400) and it's less than a week old.  I'll let it sit on the charger for some more time and see if it goes beyond 3725 mAh, but given it says 'charged' I wonder if it's topped out.  This is what it was before I did the test.

In Thomas's absence I'll email support and see if they have any suggestions or options.

Also I've added a screenshot from the Gnome Power Manager showing battery capacity is down to 84%.

Sam

It would be interesting to see the data from some other PanP5 machines.
That might be a normal reading for that battery.
The gnome power manager can only report based on what the battery gives to the kernel & the kernel then writes to /proc .

jdb

---

### Post by samalex on 2009-08-12
[QUOTE="jdb"]It would be interesting to see the data from some other PanP5 machines.
That might be a normal reading for that battery.
The gnome power manager can only report based on what the battery gives to the kernel & the kernel then writes to /proc .
[/QUOTE]

I was just about to ask the same thing...  I just started another cycle to see how long it takes for the system to deplete the battery.  I started it at 1:25pm at 100% and now at 1:42pm it's down to 82%.  I'm currently running Amarok (streaming audio), Skype, and Pidgin.  

According to 'top' none are using any sizable resources with each hanging around 2%-4% CPU usage.  It does however look like it's going down faster than before, whether due to streaming audio over the network card or due to Skype and Pidgin going.  Not sure...  

I'll post results when it's down to 0%.  Also I emailed support, so hopefully they'll have some advice.  

Sam

---

### Post by samalex on 2009-08-12
Hey Guys --

I just finished another test where I ran the battery down to 0%.  The results were about the same with about 1 hour and 35 minutes.  I had the screen saver set to blank screen, but this go around I had Amarok streaming Internet radio, Skype and Pidgin, plus I played 30 minutes of video from YouTube.  Here's some info:

```

1:25pm - 100% 
- Disconnected power and rebooted
- Started Amarok and turned on streaming audio

1:38pm - 87%
- Current charge: 36.1 Wh
- Discharge Time: 1 hour 36 minutes
- Opening Skype and Pidgin

1:47pm - 78%
- Current charge: 32.6 Wh
- Discharge Time: 1 hour 32 minutes

2:02pm - 64%
- Current charge: 26.6 Wh
- Discharge Time: 1 hour 6 minutes
- System for the most part is idle with blank screen.  Only listening to music.

2:12pm - 53%
- Current charge: 21.9 Wh
- Discharge Time: 49 minutes
- Going into Firefox to hit some sites

2:14pm - 49%
- Current charge: 20.6 Wh
- Discharge Time: 51 minutes
- Opened Youtube and started Tech Talk episode where Torvalds talks about git
  It's like an hour long so I'll let it play and see what happens to the power.
  npviewer.bin (Flash plugin for Firefox) is sitting at 36% CPU usage while Youtube plays
- I'm keeping the Power History window open, and I can see the Battery Percentage plumiting.

2:30pm - 32%
- Current charge: 13.4 Wh
- Discharge Time: 33 minutes

2:47pm - 15%
- Current charge: 6.3 Wh
- Discharge Time: 15 minutes
- Closed Firefox... video was at 32 minutes.
- Odd, chipcardd4 is using 1% of CPU but I have no smart cards connected.  (hitting google)

2:52pm - 10%
- Current charge: 4.2 Wh
- Discharge Time: 10 minutes
- Display just went dim since I guess it's at 10% or less.

2:57pm - 5%

3:02pm - Hibernation kicked in due to battery being depleted

```

And here's the battery info when it was down to like 2%:

```
alarm:                   unsupported
present:                 yes
design capacity:         4400 mAh
last full capacity:      3725 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M740TX
serial number:            
battery type:            LION
OEM info:                Clevo CO.
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      99 mAh
present voltage:         14800 mV

```

Also I'm attaching screenshots of the Power History and Details.  

The results were still better than yesterday where I'm getting around 90 minutes, but I noticed npviewer.bin chewed up CPU cycles keeping it at around 40% for the entire time YouTube was playing video.  I bet if not for that I could've gotten more out of it.

I've reconnected power and will let it charge to 100%, but it looks like 3725 mAh (41.3 Wh) is that it's maxing out at now, even though the capacity shows to be 48.8 Wh.  That's still 15% loss in capacity :confused: .

For any other PanP users, can you post the output of this:
$ cat /proc/acpi/battery/BAT0/*

As jdb mentioned I'd be curious to see what others are running with.  I did a search for the model number and [found this thread]("http://ubuntuforums.org/archive/index.php/t-945221.html") which lists a number of people's battery info, several of which are using the same model as I.  Most seem to have far better capacity after a decent length of time, so I'm back to wondering if this battery has issues.

Thanks --

Sam

---

### Post by bill516 on 2009-08-12
I have had a PanP4 for several months now and I bought it knowing that battery life probably was going to be an issue.

I consistently get 1:45 to 2 hours on a machine that has a T6400 processor and a 7200 RPM HD.

Would I buy a larger capacity battery if one were available?  Sure, but there is not one.

So I think of the Pangolin as a line-power machine that takes short breaks on my back deck or ??? before I plug it in again.

My Pangolin is a very nice machine.  It is NOT the machine I would buy if I needed to operate for extended time away from line power.  And yes, I knew that before I ordered it.

---

### Post by samalex on 2009-08-12
[QUOTE="bill516"]My Pangolin is a very nice machine. It is NOT the machine I would buy if I needed to operate for extended time away from line power. And yes, I knew that before I ordered it.[/QUOTE]

Bill,

Like you I ordered my Pangolin knowing the battery life wouldn't be outstanding, but what prompted the post was 45 minutes of life from 100% to 0%.  I'm finding that this was probably due to a couple of applications that chewed CPU power (screensaver and VirtualBox mainly).  Though I can live with an hour and a half, 45 minutes was really not groovy.  Also the Gnome Power Manager showing I've lost 15% capacity in the battery is worrisome as well.

Given you also have a PanP laptop, would you mind running this and posting the output?:
$ cat /proc/acpi/battery/BAT0/*

If Gnome Power Manager is incorrect I can live with that, but given it showed 94% after two days, 88% yesterday, and now 84%, I see a blah trend.  But from what I read this comes directly from the battery so who knows.

As you this laptop is a desktop replacement, and for me I put performance above battery life.  The laptop is outstanding, but if I can squeeze 90 minutes to two hours out of it on average, that'll work for me.  I don't do alot of unplugged work, but from time to time while traveling I do have to slide into a B&N or Panera Bread to get some work done or check email, and power isn't always available.  I'll probably order a second battery before my next road trip, which if 1:30-2:00 is the average per charge will work great. 

Take care --

Sam

---

### Post by thomasaaron on 2009-08-12
Sent you an email. Let me know if that works. If not, we can replace the battery for you.

---

### Post by jordansc on 2009-08-12
> Originally Posted by [B]samalex
[/B]Given you also have a PanP laptop, would you mind running this and posting the output?:
$ cat /proc/acpi/battery/BAT0/*Here's my output with a 100% charged battery on a PanP5 I've had for 2 weeks . The results appear even worse than Sam's as the battery capacity is maxing out at only 3688 mAh. Maybe that explains several recent sessions in which the battery went from 100% charge to 0% in less than 50 minutes:

alarm:                   unsupported
present:                 yes
design capacity:         4400 mAh
last full capacity:      3688 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M740TX
serial number:            
battery type:            LION
OEM info:                Clevo CO.
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      3688 mAh
present voltage:         14800 mV

Any more ideas?

Jordan

---

### Post by thomasaaron on 2009-08-13
Hi, Jordan.

Responded to your email this morning, so let me know how those instructions work out.

As for battery capacity, run your battery down, turn off your machine, remove battery/ac adapter. Let everything cool down to room temp for about an hour. Then plug the battery back in and charge it up. Does that give you full capacity?

---

### Post by miniyak on 2009-08-13
```
alarm:                   unsupported
present:                 yes
design capacity:         4400 mAh
last full capacity:      3950 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M740TX
serial number:            
battery type:            LION
OEM info:                Clevo CO.
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      2166 mAh
present voltage:         14800 mV
```

device information is telling me that capacity is at 89%(fair) at the moment but that may be different on a full charge

---

### Post by jordansc on 2009-08-14
> Originally Posted by [B]thomasaaron
[/B]As for battery capacity, run your battery down, turn off your machine, remove battery/ac adapter. Let everything cool down to room temp for about an hour. Then plug the battery back in and charge it up. Does that give you full capacity?After following your instructions, battery capacity is worse than before:

```
alarm:                   unsupported
present:                 yes
design capacity:         4400 mAh
last full capacity:      3654 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M740TX
serial number:            
battery type:            LION
OEM info:                Clevo CO.
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      3654 mAh
present voltage:         14800 mV

```Please see my emails, especially the second one.

Jordan

---

### Post by samalex on 2009-08-14
Maybe this is normal for a battery, I'm not sure.  I never had access to this information on any laptop I've ever owned, but given the PanP5 laptop isn't known for awesome battery life anyway I'd like to make sure the battery is as good of shape as possible.  I wonder if that Last Full Capacity is some line in the sand that gets marked and once set it never goes back up.  Again, i don't know much about how these batteries work, so I'm not sure.  After reading a [few posts]("http://fostergrant.ubuntuforums.org/showthread.php?t=945221") from people with similar batteries it looks like most are having better luck than we are though.

Last night I went unplugged for about 80 minutes while surfing and also played Nexuiz for about 20 minutes which taxes the system heavily.  After it hit 5% I shut down for the evening.  If I have to stay plugged in while at home and work I can do that if it means keeping a reliable battery.  I guess with my iBook having 3-4 hours of go on a charge I rarely depleted it or needed to worry much about it, but if running the battery down is bad I'll try to be more mindful of this in the future.

I have asked support if I can switch out the battery, but if someone has words of wisdom to keep the battery in tip-top shape I'd like to hear.  I've heard some suggest to run it down from time to time while others say this isn't good.  

Thanks --

Sam

---

### Post by HotShotDJ on 2009-08-14
This thing about battery life has been bugging me, so I've been researching. My reading has lead me to look at the graphics card for some significant power saving.  Of course, my current laptop does not have a discrete graphics card like your PanP5 so I have no way of testing this stuff.  But the specs of the GeForce G105M suggest that the following should work -- set your graphics card for maximum power savings when on battery, and either "adaptive strategy" or "max performance" when on AC.  [HERE]("http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/#power-saving") is the "howto" that I found.

What I don't know is if the G105M already does this by default.  I suspect it defaults to "adaptive strategy" if parameters are not set by the user in xorg.conf ... but I'm just guessing.  You can use the tools listed in the above link to see what the default behaviors are when on AC and when on battery, and then make adjustments using xorg.conf if necessary.

It would be great if you guys/gals with PanP5's could test this out and let us all know the results.  What I'd especially like to see results for:[LIST=1]
[*]does the G105M correctly detect AC vs Battery power,
[*]What is the default power mode for both AC and Battery,
[*]If it does not switch to power saving mode by default when on battery power, does configuring it to do so result in any significant extension of battery run-time.
[*]How is the graphics performance for standard applications (non-gaming) such as compiz, google earth, video playback, etc., whilst in power saving mode.
[/LIST]

---

### Post by miniyak on 2009-08-14
> This thing about battery life has been bugging me, so I've been researching. My reading has lead me to look at the graphics card for some significant power saving. Of course, my current laptop does not have a discrete graphics card like your PanP5 so I have no way of testing this stuff. But the specs of the GeForce G105M suggest that the following should work -- set your graphics card for maximum power savings when on battery, and either "adaptive strategy" or "max performance" when on AC. Here is the "howto" that I found: [http://tutanhamon.com.ua/technovodst.../#power-saving](http://tutanhamon.com.ua/technovodst.../#power-saving)


WOT is telling me that this is an untrustworthy site... the report says something about spam but i would be weary

---

### Post by HotShotDJ on 2009-08-14
> **miniyak said:**
> WOT is telling me that this is an untrustworthy site... the report says something about spam but i would be wearyI don't know what "WOT" is, but I suspect you received a false positive.  In any case, I created the link incorrectly.  [HERE]("http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/#power-saving") is the proper link (corrected in OP as well).  I have found similar instructions on the NVidia forums.

(I further suspect that you would be wary (cautious) rather than weary (tired))

EDIT: I now know what "WOT" is.  I stand by my original comment.  Looks like a false positive.  If you Google "+nvidia +powermizer +xorg" you will find similar advise as that found in the link I provided.  The linked page provides the clearest "howto" that I've found.

---

### Post by cutterjohn on 2009-08-24
Don't feel too badly, I get about 2h 45m or so with my MSI GT725 (9 cell) under Vista 32 w/MSI's turbo battery mode while under linux I am doing well to get about 1h 30m of battery life(Ubuntu 9.04 64b).

Power management under linux seems to be rather poor.

Also you may wish to check the load_cycle count on your hdd.  The bug was supposed to have been "fixed" under 9.04 but the fix may not work for all hdds.  Google the Ubuntu laptop hdd killer bug...

---

