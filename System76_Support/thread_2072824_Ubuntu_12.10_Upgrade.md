---
title: "Ubuntu 12.10 Upgrade"
date: 2012-10-18
forum: System76 Support
---

### Post by isantop on 2012-10-18
Alright! The new version of Ubuntu was just released this morning, and everything is looking good. System76 users are clear to upgrade immediately!

Just a couple of notes, as always:

[LIST]
[*]As usual, we recommend waiting a week or two after the release before attempting a direct upgrade to give time for the servers to cool down.
[*]Fresh installs are good to go immediately. 
[*]Don't forget to install the System76 Driver after installation! Just go to [http://planet76.com](http://planet76.com) and click the download link to automatically grab the latest version!
[*]As a note for users with dedicated graphics cards, the proprietary driver installation is now completed through the Software Sources item in System Settings. The Additional Drivers Utility has been removed. 
[/LIST]

That should be everything. The direct upgrade instructions are located at: [Knowledge76 - Quantal Upgrade](http://knowledge76.com/index.php/QuantalUpgrade).

---

### Post by aukan on 2012-11-03
Hi,

Hopefully you can help me. I have a panp7 and when I upgraded to Ubuntu 12.10, the opensource driver for the video card (ATI Mobility Radeon 4570) was installed, so everything looked fine.

My problem is that I do need the propietary driver mainly for 2 reasons:

- The first one is that I usually attach one monitor to my panp7 when working and the opensource driver seems to have an issue with this and Unity. You see the resoluction fine, but the screen starts flickering randomly. Having the propietary driver solves this issue.

- The second reason is that the opensource driver does not use the video card in a 100%, so that creates a problem when trying to play games.

Well, the problem is that when I tried installing the driver from the Ubuntu software center, it crashed. I later on found [this article]("http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html") that tells you that the propietary driver is now legacy and won't be supported. It also tells you how to install the legacy driver. I tried this solution and it works, but the problem is that I'd like to use only the official repos that Canonical provides, and obviously yours.

So, what do you recommend to me? Do you have a solution for this?

Thank you in advance,
Pablo Gonzalez

---

### Post by isantop on 2012-11-05
> **aukan said:**
> Hi,

Hopefully you can help me. I have a panp7 and when I upgraded to Ubuntu 12.10, the opensource driver for the video card (ATI Mobility Radeon 4570) was installed, so everything looked fine.

My problem is that I do need the propietary driver mainly for 2 reasons:

- The first one is that I usually attach one monitor to my panp7 when working and the opensource driver seems to have an issue with this and Unity. You see the resoluction fine, but the screen starts flickering randomly. Having the propietary driver solves this issue.

- The second reason is that the opensource driver does not use the video card in a 100%, so that creates a problem when trying to play games.

Well, the problem is that when I tried installing the driver from the Ubuntu software center, it crashed. I later on found [this article]("http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html") that tells you that the propietary driver is now legacy and won't be supported. It also tells you how to install the legacy driver. I tried this solution and it works, but the problem is that I'd like to use only the official repos that Canonical provides, and obviously yours.

So, what do you recommend to me? Do you have a solution for this?

Thank you in advance,
Pablo Gonzalez

No, unfortunately, I don't. As a fellow PanP7 owner, I can personally sympathize with how frustrating it is, though.

---

### Post by IAmWhatWasDavidBowman on 2012-11-08
> **aukan said:**
> Hi,

Hopefully you can help me. I have a panp7 and when I upgraded to Ubuntu 12.10, the opensource driver for the video card (ATI Mobility Radeon 4570) was installed, so everything looked fine.

[...]

So, what do you recommend to me? Do you have a solution for this?

Thank you in advance,
Pablo Gonzalez

I'm glad I came browsing through the forum before updating my panp7. I was not aware that the drivers are now considered legacy. That's frustrating. I use HDMI output all the time, and not having that working properly is a deal breaker for me.

This may or may not apply to 12.10 or the panp7, but on my desktop computer - which also has AMD graphics - in order to get the updated drivers to install properly for 12.04, I had to follow the instructions here: [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers)

I could be wrong, but it looked to me that by following those instructions, you build the drivers specifically for your setup and then they walk you through installing them.

There are also instructions there for installing the drivers for 12.10 by downgrading the xorg installation. I haven't tried this on my panp7 yet, and I may not unless someone can convince me that it's worth updating to 12.10.

Anyway, that's all the info I could find. I hope it helps.

---

### Post by isantop on 2012-11-08
> **IAmWhatWasDavidBowman said:**
> I'm glad I came browsing through the forum before updating my panp7. I was not aware that the drivers are now considered legacy. That's frustrating. I use HDMI output all the time, and not having that working properly is a deal breaker for me.

This may or may not apply to 12.10 or the panp7, but on my desktop computer - which also has AMD graphics - in order to get the updated drivers to install properly for 12.04, I had to follow the instructions here: [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers)

I could be wrong, but it looked to me that by following those instructions, you build the drivers specifically for your setup and then they walk you through installing them.

There are also instructions there for installing the drivers for 12.10 by downgrading the xorg installation. I haven't tried this on my panp7 yet, and I may not unless someone can convince me that it's worth updating to 12.10.

Anyway, that's all the info I could find. I hope it helps.

I'd say it's definitely worth upgrading. Some of the new features are very slick, and at least on newer hardware, we've found it to be mre stable. 

Also, HDMI would work fine without the proprietary drivers. Unless you need 3D, there isn't really a reason to install the proprietary drivers anymore.

---

### Post by IAmWhatWasDavidBowman on 2012-11-08
> **isantop said:**
> I'd say it's definitely worth upgrading. Some of the new features are very slick, and at least on newer hardware, we've found it to be mre stable. 

Also, HDMI would work fine without the proprietary drivers. Unless you need 3D, there isn't really a reason to install the proprietary drivers anymore.

Well under 12.04, HDMI did work using the free driver, however it was buggy for me. I also noticed other graphical quirks, though nothing show-stopping. Perhaps I can try again with better results under 12.10. I may not have given the free driver an honest shot. I really never do anything that needs 3D (so naturally once I go down this road, I'll need 3D. Ha ha).

I have looked at the new features of 12.10, and I don't see anything that would make it worth my time to upgrade, at least not out of any of the advertised features. Maybe the 3.5 kernel makes it worth it?

I will say though - with no small amount of satisfaction - not one other computer I have ever owned was as easy to get Ubuntu working perfectly on than my panp7, so I may give this a shot anyway. The drivers System76 supplies really make this easy (and a BIG kudos for getting the fingerprint reader drivers working again!).

Have a good one!

---

