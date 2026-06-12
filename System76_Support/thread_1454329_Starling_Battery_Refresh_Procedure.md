---
title: "Starling Battery Refresh Procedure"
date: 2010-04-14
forum: System76 Support
---

### Post by thomasaaron on 2010-04-14
Battery Refresh Procedure
Overview

If The Battery Drive Time Is Shorter Than Expected
If the computer is operated by the battery for a short period of time and then charged by the AC adapter, this causes a shallow charge-discharge cycle. The repetition of such shallow charge-discharge cycles causes the battery's drive time to decrease temporarily. The above should be kept in mind if you decide to run the computer off the battery after it has been running off the AC adapter for an extended period of time.
If you leave a fully charged battery for 2 to 4 weeks in temperatures above 35 degrees C (95 degrees F), the battery's drive time may decrease temporarily.
The situations above are not due to a fault in the battery. Normal performance can generally be restored by fully charging and then discharging the battery two or three times in succession with the resume function disabled (if your notebook has this feature).

How To Refresh Rechargeable Batteries
1. Connect the AC adapter and charge the battery fully.
2. Fully discharge the battery (by running the unit) until the power LED goes off.
3. Connect the AC adapter and charge the battery fully a second time.
4. Fully discharge the battery until the power LED goes off again.
If after this procedure your battery life is not restored please refer to Battery Service Life section below.

Important Notes

Battery becomes warm to the touch
Mounting and attempting to charge a battery pack that is already fully charged, or mounting and removing a battery pack several times in quick succession, can result in overcharging and cause the battery to heat up. Such treatment can damage the battery pack.
The battery pack will become somewhat warm during normal use. This is not a malfunction.

Operating temperature
It is recommended to operate the computer at an operating temperature between 5 degrees and 35 degrees C (41degrees F and 95 degrees F) (Charging may not be possible if the temperature is outside this range.)
The battery's operating time will decrease if the operating temperature is low.
An unusually high or low operating temperature during charging will reduce the battery's storage capacity.

Battery Service Life
If the battery pack's period of use becomes very short and its performance is not restored after a few cycles of refreshing, the battery pack has reached the end of its service life and it should be replaced with a new one.
Also, a situation such as that described below can occur if the battery has been in use for a long time. This means that the battery is at the end of its service life. Purchase a new battery to replace it.
After being fully charged, the low battery warning appears after only a short period of use. Performance does not improve even after two or three charge-discharge cycles (refreshing procedure).

---

### Post by jbraswell on 2010-06-10
This is a timely message, as I just started having this problem. 

Looking at your prescribed fix, though, what if I can't get the battery to a full charge?  For example, last night I turned my netbook off and plugged in the adapter.  After 6-7 hours of charging, it only went from reading 50 minutes of power remaining to 1.5 hours remaining.  I'm guessing I should try to completely drain it?

---

### Post by thomasaaron on 2010-06-10
> Looking at your prescribed fix, though, what if I can't get the battery to a full charge? 

You can try to run the above procedure a couple of times to see if that helps. If a battery is often run down to zero, it will (eventually) permanently loose its capacity to charge all the way up.

---

### Post by jbraswell on 2010-06-12
> **thomasaaron said:**
> You can try to run the above procedure a couple of times to see if that helps. If a battery is often run down to zero, it will (eventually) permanently loose its capacity to charge all the way up.

OK, I ran it until it shutdown, and then I left it to charge for two days with it totally turned off. It only made it up to 15%. But last night I left it on while it charged, and now it's back up to 85%.  (I had it set to not hibernate or suspend; I don't know if that made a difference.)

I've never run the battery completely down until the other day.  Should I do that regularly?

---

### Post by flukeairwalker on 2010-06-13
Is it normal while doing this for the battery to take *forever* to charge completely? Because I plugged it in for 24 hours and got a little less than half charge.

---

### Post by jbraswell on 2010-06-14
Last night I left it to charge, and when I first looked at it, it said it was fully charged, and the red charging indicator light was out.  After I unplugged the adapter, though, it took about a minute for the little lighting bolt AC-power indicator on the battery icon to change.  Once it did, the charge dropped down to < 30%.  So, I'm pretty sure the battery and the OS are disagreeing on when the battery needs charging.

Regardless, I doubt the problem is with the battery.  It's not even a year old, and this behavior began rather suddenly.

---

### Post by jbraswell on 2010-06-14
Another possible clue...

I realized that my earlier attempts to run the battery all the way down may have failed since it was set to shut down automatically.  So, I killed the Gnome power management and did it again.

Now, when I first started charging it again a few hours ago, it wouldn't charge *at all.* That is, after charging for about 30 minutes, upower -d showed "energy" at 0.  I let it hibernate after that, and now, a few hours later, it's only showing me at 3.55, ~7%.

The weird thing is that every time I get the upower readout, it reads that my time to full is 3.6 minutes!?

---

### Post by jbraswell on 2010-06-16
Currently, it's taking forever to charge (~2%/hr).  Also I have to occasionally unplug/replug it because it will suddenly think that it's done charging and quit. (When that happens, both the red charge light goes out, and upower's output indicates that it's not charging.)

If buying a new battery will fix this, I don't really mind, but I'd hate to get a new one and have the same problem.

---

### Post by isantop on 2010-06-17
Was the battery dropped? I'm thinking that if it was, there may have been some damage to the cells in the battery, rendering them inoperable.

---

### Post by jbraswell on 2010-06-17
Hmmm, not that I can recall.  I think I'll probably just order a new battery.  If you can think of any other ways to test the battery itself in the meantime, though, let me know if you can.

Thanks!

---

### Post by isantop on 2010-06-17
If you have the battery in and are running on AC power, you can click on the battery icon in the panel, then click on the status of the battery. It should be the first item in the menu.

This should open up a window with details about the battery in it. Please take a screen shot (Press Alt+Prt Sc) and post it here.

---

### Post by jbraswell on 2010-06-17
Here you go.  The current charge rate is such that it'll take about 3 days to go from empty to full, *provided* that it doesn't suddenly think it's 100% and quit charging.

It's weird, when I first started having this problem, I don't think the charge *rate* was slow; it's just that it would quit charging periodically until I un/re-plugged it.  Since I truly ran the battery to 0, though, the rate is super slow as well.

For good measure:


```
Device: /org/freedesktop/UPower/devices/line_power_ACAD
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/ACPI0003:00/power_supply/ACAD
  power supply:         yes
  updated:              Thu Jun 17 13:15:17 2010 (84 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             yes

Device: /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0A:00/power_supply/BAT1
  vendor:               SIMPLO
  model:                UM08A51
  serial:               000B
  power supply:         yes
  updated:              Thu Jun 17 13:16:24 2010 (17 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              25.9632 Wh
    energy-empty:        0 Wh
    energy-full:         46.4292 Wh
    energy-full-design:  51.84 Wh
    energy-rate:         706.73 W
    voltage:             11.247 V
    time to full:        1.7 minutes
    percentage:          55.92%
    capacity:            89.5625%
    technology:          lithium-ion
  History (charge):
    1276798584	55.920	charging
    1276798554	55.897	charging
    1276798520	55.873	charging
    1276798518	0.000	unknown
  History (rate):
    1276798584	706.730	charging
    1276798520	706.741	charging
    1276798518	0.000	unknown

Daemon:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes
```

---

### Post by isantop on 2010-06-17
Hmm. Why does 1.7 minutes to charge from 55% to full seem a bit off... :)

I would try another battery. It seems this one doesn't like to report It's percentages properly. I had this happen to the battery on my old laptop, and a new one fixed it right up.

---

### Post by jbraswell on 2010-06-17
Yeah, it's always like that, another oddity. I ordered another battery. Hopefully that will do it.

---

### Post by jbraswell on 2010-06-26
So, I got a new battery, but I'm still having problems.  No matter what level of charge I'm showing, the properties page always shows somewhere between 1 and 3 minutes until full charge.

Also, this morning I unplugged the charger and took my computer to a coffee shop. I worked on it for three and a half hours, and the whole time, the display showed 100% charge.  I then suspended it, and when it came back up, it showed less than 5% charge.

Something is simply wrong with how the system is evaluating the charge level.  Although I can't recall exactly when this started, it wasn't too far from the time I upgraded to Lucid.  Anyone else have battery problems that started when they upgraded?

---

### Post by smulloni on 2010-07-04
> **jbraswell said:**
> 
Something is simply wrong with how the system is evaluating the charge level.  Although I can't recall exactly when this started, it wasn't too far from the time I upgraded to Lucid.  Anyone else have battery problems that started when they upgraded?

My battery problems started around the same time.  I had just performed a kernel update and upgraded the system76 drivers.  I was on Jaunty and afterwards upgraded to Lucid, but the problem remained.  Same problem you report -- charging takes forever, and the battery state is misreported -- it will say fully charged, but if I unplug, within seconds it will drop down to something much lower.  I once managed to get it close to 100% by unplugging periodically to reset it.

I'm a little reluctant now to order a battery just yet, given your report, so I'll put up with it for a little while and see what happens.

---

### Post by jbraswell on 2010-07-05
I will say that after using a bit, it's gotten better.  I can pretty reliably get a full charge now.  *Sometimes* when I unplug it after it's fully charged, I have to suspend/hibernate it once before it will start showing the charge level actually changing again.  I'd say it's still worth a shot to get a new battery.

---

### Post by flukeairwalker on 2010-07-05
I got good results when I charged the battery while the computer was off as opposed to in suspend mode.I have to try it again to see if that's really all it takes to get a full, fast charge.

---

### Post by gamerchick02 on 2010-08-02
Sorry to revive an old thread, but I'm having Starling battery issues.

I'm not getting any charging when plugged in while off, and VERY slow charging when plugged in and on.  I'm attempting to do the refresh procedure right now, but I've had the netbook plugged in since yesterday afternoon and it's at 50%.

Is there something I can do to speed this along, or am I stuck spending the next month trying to charge the battery and then discharge it?

Amy

EDIT: I've attached a couple of screenshots from the battery information window.

---

### Post by gamerchick02 on 2010-08-06
I hate to bump threads, but now my starling is not charging on A/C power.

I'm enabling backports and proposed as we speak and installing all the updates.

Any thoughts as to why I'm not getting any charging?

I've done the "refresh procedure" twice over the past week (yes, it takes about 3 days to charge completely) and I'll do it again after enabling and updating these repos.

Amy

---

### Post by isantop on 2010-08-06
This sounds like the same problem from above. A new battery might help the problem.

One option is to create a LiveUSB and boot from it. Tell us if the battery performs any better there.

---

### Post by gamerchick02 on 2010-08-06
I did a fresh install, thinking that maybe my upgrade did something.  (Not that there was an issue before, but you never know.)

I'll try a live USB right now and see what happens.

Amy

EDIT: It's still charging very slowly.  Do you think I should try to redo the refresh procedure?  This battery is just a year old and hasn't been abused in any way, shape, or form.

---

### Post by gamerchick02 on 2010-08-06
Another update:

Seems like it's charging faster in the LiveUSB.

I'll let it sit overnight and see where the charge is.

Amy

---

### Post by gamerchick02 on 2010-08-08
I ordered a new battery.  Let's see if this will help things.

Amy

---

### Post by sgy on 2010-08-12
> **jbraswell said:**
> Currently, it's taking forever to charge (~2%/hr).  Also I have to occasionally unplug/replug it because it will suddenly think that it's done charging and quit.

I am having a similar problem.  The battery of my Starling Netbook charges slowly -- about 2%/hr as above.  Once charged, however, the lifetime is comparable to before the problem arose, roughly 3-3 1/2 hours.  Mine also sometimes abruptly indicates that it is 100% charged, although it is clearly not.  An unplug/replug corrects the mis-indication.  Although with mine it seems to continue to charge throughout.

Also, mine gets ridiculously hot.

I have discharged it completely and recharged it fully more than a few times in an effort to correct the problem.  There has been no change in behavior since the problem began.

Any suggestions?

---

### Post by thomasaaron on 2010-08-13
If you've tried the battery refresh procedure in the first post of this thread, and it didn't work, contact support...at...system76...dot...com.

If you're still under warranty, we can get you a new battery. Otherwise, you may need to purchase a new one.

---

### Post by rdelfin on 2010-08-16
May I ask if all the issues being reported here in regards of recharging the battery are exclusively from equipments of the 1st generation model of the Starling?    

Recently, a new 2nd generation of the Starling has been made available, and I'm wondering if someone reporting battery issues in this thread was specifically referring to this newer model.  Anyone?

Thanks in advance!

---

### Post by thomasaaron on 2010-08-16
The refresh procedure is primarily for the first generation Starling.

---

### Post by gamerchick02 on 2010-08-16
I got my new battery today (just 15 minutes ago, in fact) and I'd like to report that it's charging nicely.

Thanks to System76 for all the troubleshooting on this issue.

Amy

---

### Post by sgy on 2012-02-05
Back in August, System 76 replaced my battery free of charge, and things were great until recently.

Now, about 6 months later, the second battery is having the exact some problem.  It charges very slowly (about 60%/day), and discharges and the usual rate (about 25%/hour).

What should I do?

Thanks.

---

### Post by isantop on 2012-02-06
Try charging/discharging the battery to about 40-50%, then let it sit for a week or so (The longer you can, the better). Unfortunately, the Star1 batteries are no longer manufactured, and it will be very difficult to obtain one. I would recommend trying this and the battery refresh procedure to solve your battery issues.

---

### Post by superfrogman94 on 2012-02-25
Hey guys, would you recommend this for the star 1? [http://www.amazon.com/Battery-Acer-Aspire-replace-UM08A73/dp/B001NW57MU/ref=sr_1_1?ie=UTF8&qid=1330187186&sr=8-1](http://www.amazon.com/Battery-Acer-Aspire-replace-UM08A73/dp/B001NW57MU/ref=sr_1_1?ie=UTF8&qid=1330187186&sr=8-1)
or
[http://www.amazon.com/Battery-UM08A31-UM08A51-UM08A71-Notebook/dp/B001P5QD2S/ref=sr_1_fkmr0_3?s=electronics&ie=UTF8&qid=1330191504&sr=1-3-fkmr0](http://www.amazon.com/Battery-UM08A31-UM08A51-UM08A71-Notebook/dp/B001P5QD2S/ref=sr_1_fkmr0_3?s=electronics&ie=UTF8&qid=1330191504&sr=1-3-fkmr0)

because unfortunately i got this battery  [http://www.amazon.com/Extended-Capacity-Laptop-Battery-Aspire/dp/B001RBXV20/ref=sr_1_1?ie=UTF8&qid=1330188224&sr=8-1](http://www.amazon.com/Extended-Capacity-Laptop-Battery-Aspire/dp/B001RBXV20/ref=sr_1_1?ie=UTF8&qid=1330188224&sr=8-1)
and it is too big to fit, i tired many times but the body of the starling wont allow it to lock in :(

i am gonna try refreshing though, but its sad to have this happen to me, i really love this netbook, works amazing, just cant stand the battery dieing after an hour.

i know the battery is a UM08A51 correct?

anything from here correct?
[http://speakcomputers.com/electronics.aspx?&category=electronics&productsearch=simplo&pagenumber=1](http://speakcomputers.com/electronics.aspx?&category=electronics&productsearch=simplo&pagenumber=1)
or
[http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Delectronics&field-keywords=UM0a51&x=0&y=0]("http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Delectronics&field-keywords=UM0a51&x=0&y=0")

please reply.

---

### Post by isantop on 2012-02-27
> **superfrogman94 said:**
> Hey guys, would you recommend this for the star 1? [http://www.amazon.com/Battery-Acer-Aspire-replace-UM08A73/dp/B001NW57MU/ref=sr_1_1?ie=UTF8&qid=1330187186&sr=8-1](http://www.amazon.com/Battery-Acer-Aspire-replace-UM08A73/dp/B001NW57MU/ref=sr_1_1?ie=UTF8&qid=1330187186&sr=8-1)
or
[http://www.amazon.com/Battery-UM08A31-UM08A51-UM08A71-Notebook/dp/B001P5QD2S/ref=sr_1_fkmr0_3?s=electronics&ie=UTF8&qid=1330191504&sr=1-3-fkmr0](http://www.amazon.com/Battery-UM08A31-UM08A51-UM08A71-Notebook/dp/B001P5QD2S/ref=sr_1_fkmr0_3?s=electronics&ie=UTF8&qid=1330191504&sr=1-3-fkmr0)

because unfortunately i got this battery  [http://www.amazon.com/Extended-Capacity-Laptop-Battery-Aspire/dp/B001RBXV20/ref=sr_1_1?ie=UTF8&qid=1330188224&sr=8-1](http://www.amazon.com/Extended-Capacity-Laptop-Battery-Aspire/dp/B001RBXV20/ref=sr_1_1?ie=UTF8&qid=1330188224&sr=8-1)
and it is too big to fit, i tired many times but the body of the starling wont allow it to lock in :(

i am gonna try refreshing though, but its sad to have this happen to me, i really love this netbook, works amazing, just cant stand the battery dieing after an hour.

i know the battery is a UM08A51 correct?

anything from here correct?
[http://speakcomputers.com/electronics.aspx?&category=electronics&productsearch=simplo&pagenumber=1](http://speakcomputers.com/electronics.aspx?&category=electronics&productsearch=simplo&pagenumber=1)
or
[http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Delectronics&field-keywords=UM0a51&x=0&y=0]("http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Delectronics&field-keywords=UM0a51&x=0&y=0")

please reply.

Unfortunately, none of the batteries you supplied links to will fit in the Starling. They're designed for Acer netbooks.

---

### Post by Schrollini on 2012-03-17
Has anyone actually had success with either refresh procedure?  I have a star1 that has settled into the 2%/hour charging rate, and I'm hoping against hope that it's fixable.

---

### Post by isantop on 2012-03-19
For most of the people I know of who try it, it works great. I've had good success using it myself.

---

### Post by Schrollini on 2012-04-10
I finally got the chance to let it sit for a week at 50% charge.  The recharge afterwards was still slow.  I'm running it all the way down now to try the first procedure, but given the charging speed, it'll be another few days before it's finished.

Fingers crossed.

---

### Post by Sebastian Konrad Laski on 2012-04-16
Thanks.

William Sebastian Konrad Laski

---

### Post by Schrollini on 2012-05-01
I've tried running the battery all the way down twice.  Recharging is a bit faster -- maybe 4%/hr instead of 2.  But it's still painfully slow.  Should I try more full discharges?  I'm worried that too many could damage the battery.

---

### Post by isantop on 2012-05-02
> **Schrollini said:**
> I've tried running the battery all the way down twice.  Recharging is a bit faster -- maybe 4%/hr instead of 2.  But it's still painfully slow.  Should I try more full discharges?  I'm worried that too many could damage the battery.

You're unlikely to damage the battery with charge-discharge cycles. I would try a few more to see what results you have.

---

