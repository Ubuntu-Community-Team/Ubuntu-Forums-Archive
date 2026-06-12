---
title: "Maverick on Starling 1"
date: 2010-09-30
forum: System76 Support
---

### Post by bvandev on 2010-09-30
The Maverick release candidate has hit the streets.  Will my Starling 1 wireless work?  Will the System76 driver fix it if not?

Thanks in advance.

---

### Post by Noah0504 on 2010-09-30
> **bvandev said:**
> The Maverick release candidate has hit the streets.  Will my Starling 1 wireless work?  Will the System76 driver fix it if not?

Thanks in advance.

Boot from the live CD and find out.  :)

EDIT: Or I guess I should say live USB.  Haha.  But you get the gist of it...

---

### Post by bvandev on 2010-10-01
Great idea.  I ran from the usb drive and the wireless did indeed work.  I installed and it still works.

When I say it works, it works as it always has out of the box, in my case fine to about 30 feet.  The connection drops at 50.  

The System76 Driver refuses to install on Maverick (10.10).  System76 will need to put out a new driver for the new release.  (Keep in mind, I'm very early in my update.   The official release of 10.10 is Oct. 10.)  

FYI, the new Netbook release is truly innovative and most things seem to work flawlessly out of the box. Aside from the wireless, Cheese came up with the camera working.  Sound Recorder verified that the mic works, though I did need to adjust the microphone volume.   

The SD card reader is broken again.  This broke with Lucid, but was fixed along the way.  I assumed the fix came through a kernel update, but perhaps the System76 Driver is required.

In any case, things look good.  I plan to solve the wireless problem for good this afternoon by replacing the mini pci card with an Intel 5100.

---

### Post by ShowMeGrrl on 2010-10-03
>  I plan to solve the wireless problem for good this afternoon by replacing the mini pci card with an Intel 5100.

Please let us know how this works out.

---

### Post by bvandev on 2010-10-03
Worked out great.  The new card is in and came right up.  The range is considerably further and the transmission faster.  I pinged [www.google.com](www.google.com) with the old card and had average speed of 30 ms.  With the new card it's 26.  

Here is the link with the instructions I used:
[http://www.vrekk.us/2010/08/taking-apart-system-76-star1.html](http://www.vrekk.us/2010/08/taking-apart-system-76-star1.html)

The hardest part was getting the ribbon cable clips back on.  The keyboard and mouse both connect to the mother board with ribbon cables. Strangely, the cables have no ends.  The ribbon slides down into the fixture on the board and a black plastic clip slides on to hold it in place.  I'd love to know how it works.  The good news is mine still does!

---

### Post by isantop on 2010-10-05
Hi. The driver, by default, currently detects Ubuntu through 10.04. So, if it finds Ubuntu 10.10, it doesn't recognize it. With the driver, your starling should work great in maverick, even with the stock card. We currently have a maverick version in the works, and we'll have it ready in time for maverick on sunday.

---

### Post by bvandev on 2010-10-06
Hi Ian,

Great to hear the driver will be ready so soon.  

I knew I didn't need the new card, really.  Just wanted to free myself from the need for the driver.  And I enjoy taking things apart.

---

### Post by isantop on 2010-10-07
The driver is out. You can download it at [http://planet76.com/repositories](http://planet76.com/repositories). As always, it's the second link from the bottom.

---

### Post by gamerchick02 on 2010-10-07
Thank you. I'm installing on both my machines.

Amy

---

### Post by bvandev on 2010-10-09
It would be great if System76 listed the contents of the System76 Driver.  We all know it fixes the wireless problem for the Starling, but I have no good understanding what else it does.

For the record, the SD card functioned began failing with the 10.04 release.  It was a kernel issue that was fixed a couple of months ago.  It has reappeared with 10.10.  The System76 Driver does not fix it.  (The SD card problem is not severe.  The card is not recognized by a system that has already booted.  If the card is in place at boot, it will be recognized.)

Everything else seems to work great.  I forgot to test the function keys, since I seldom use them.  They work fine with the driver.  I just can't tell if the driver enabled them, or if they worked without it.

Thanks to System76 for getting the driver out so fast.

---

### Post by HotShotDJ on 2010-10-13
On my friend's Star1 in 10.04 and System76 drivers installed, when he opens System Monitor, the desktop crashes (regular gnome, not the Netbook interface) when using wireless.  This does not happen when using ethernet.  Has this issue been resolved in 10.10?

---

### Post by WarLokk on 2010-10-14
> **HotShotDJ said:**
> On my friend's Star1 in 10.04 and System76 drivers installed, when he opens System Monitor, the desktop crashes (regular gnome, not the Netbook interface) when using wireless.  This does not happen when using ethernet.  Has this issue been resolved in 10.10?

This same thing happens to me currently using 10.04

---

### Post by HotShotDJ on 2010-10-16
> **HotShotDJ said:**
> On my friend's Star1 in 10.04 and System76 drivers installed, when he opens System Monitor, the desktop crashes (regular gnome, not the Netbook interface) when using wireless.  This does not happen when using ethernet.  Has this issue been resolved in 10.10?
> **WarLokk said:**
> This same thing happens to me currently using 10.04I just finished upgrading him to Maverick and ran the System76 restore tool.  Desktop still crashes on wireless when I open the System Monitor and then click on the "Resources" tab.

---

### Post by isantop on 2010-10-19
I didn't run into this in my testing, I hadn't run the driver, but I could read from the resources tab fine. For the Star1, you shouldn't actually need the driver anymore (The Wireless drivers are now in the primary distibution).

Go ahead and try it without the driver installed. It may not make a difference, but it could.

One possibility is that because you upgraded as opposed to a fresh install, the offending file is still there, causing problems. My tests were with a fresh install, so that may be the issue.

---

### Post by HotShotDJ on 2010-10-19
> **isantop said:**
> Go ahead and try it without the driver installed. It may not make a difference, but it could.

One possibility is that because you upgraded as opposed to a fresh install, the offending file is still there, causing problems. My tests were with a fresh install, so that may be the issue.Ok.  Next time I have my hands on his machine, I'll do a clean install and not include the System76 Driver.

---

### Post by HotShotDJ on 2010-10-27
Fresh install + NOT installing System76 Driver = success.  No more crashing the desktop when running System Monitor.  Also, wireless seems to function as expected.

---

### Post by thomasaaron on 2010-10-27
What kind of wireless range are you getting? The reason System Monitor crashes the system after running the System76 Driver is that the Driver installs a realtek wireless driver that increased the range significantly... unless they've now added it to the mainstream kernel, and I missed it.

---

### Post by HotShotDJ on 2010-10-27
> **thomasaaron said:**
> What kind of wireless range are you getting?I just tested the range.  I get about 40 - 50 feet and then it disconnects from my router.  Then I did the same thing with my PanP5.  Although the signal dropped to well below 50% at the same distance, it did not disconnect.  The difference could be due to my Pangolin using "n" and the Starling using "g."

Keep in mind, I did this test in an apartment building, so there were lots of walls, metal doors and a floor between the computer and the wireless router at the farthest point of the test.

---

### Post by HotShotDJ on 2010-12-09
> **HotShotDJ said:**
> I just tested the range.  I get about 40 - 50 feet and then it disconnects from my router.I noticed updates to wireless drivers so I re-tested.  This time I got MUCH farther before the connection dropped... 3 floors away and almost to the adjacent building... significantly farther than the last test (barely to the second floor landing).  Again, this is a Star1 without the System76 driver package installed.

EDIT:  Just did the same thing with my PanP5 -- DRAT!  No change.  Now the Star1 has a greater range than my PanP5.  That just isn't right. ;)

---

