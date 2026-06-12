---
title: "Starling Netbook: how low does screen brightness go?"
date: 2009-11-17
forum: System76 Support
---

### Post by Thinkintuit on 2009-11-17
How dim can you make a Starling Netbook screen?

One of the things I love about my Asus EeePC is how low the screen brightness goes; if I set it to the lowest setting I can easily read it at night without it affecting my sleep -- whereas with any other computer I've ever used (e.g. my beloved Pangolin) I was unable to make the screen dim enough to "safely" read from late at night.

If anybody out there has experienced both an Asus EeePC and the System76 Starling, how do they compare in terms of how low you can set screen brightness?

Arthur

---

### Post by thomasaaron on 2009-11-18
jml, don't you have an Asus and a Starling?

I'm not really sure how to *quantify* the answer to this question, other than to say that the Starling dimness can be set pretty darn low. ;)

---

### Post by Teasdale on 2009-11-19
Now that you mention it, I haven't been able to dim my Starling display. I adjusted it way down (from 100 to 10 percent, and then to 40 percent) in the power-saving toolbar box, but the screen brightness didn't change at all. Is there some other place I need to make that adjustment?

---

### Post by thomasaaron on 2009-11-19
What version of Ubuntu are you using?
What version of the System76 Driver are you using?
Have you run the System76 Driver and rebooted?

---

### Post by Thinkintuit on 2009-12-06
Thanks for the replies.

As for quantifying it -- I have about a 2 year old Pangolin, and the Asus Notebook goes a LOT dimmer than that...so if anybody can compare how dim you can make a starling's screen go compared to a Pangolin, that would be helpful...

Although I'm happy to go with Thomas' "pretty darn low" metric.  ;)

I have a very high regard for System76 computers, so I'm very likely to get a Starling in any case...as soon as I can afford one...but I'm hoping I'll be able to make the screen dim enough late at night so that it won't adversely affect my sleep.  

cheers,
Arthur

---

### Post by jerickson314 on 2009-12-08
It's not as dark as my old iBook G4 could go.  So to me, it doesn't feel like "pretty darn low," but it's not extremely bright, either.  I'm not sure how it would affect your sleeping.

Teasdale, I noticed that changing the screen brightness on the power management has no effect, but using Fn-F4 and Fn-F5 you can change the brightness, which works for me.

I suspect the lack of change from the power management dialog is a bug, albeit not too annoying since the function keys are more convenient anyway.  Thomas, is it something that should be fixed in a System76 driver, or is it a problem from upstream?  The power manager is able to change the screen brightness, since the brightness does change when I switch between AC and battery like it's supposed to.

I am running Ubuntu 9.04 with the latest updates, and System76 driver 2.4.0.  After the last batch of kernel updates, I did run "sudo system76-driver -d" and reboot, since the update broke my wireless until I did that and I didn't have convenient access to a wired connection to do the GUI driver update.  This should be equivalent, correct?

---

### Post by Teasdale on 2009-12-09
> **jerickson314 said:**
> 
Teasdale, I noticed that changing the screen brightness on the power management has no effect, but using Fn-F4 and Fn-F5 you can change the brightness, which works for me.

Yes, that works - it's not all that dim, I can still see it just fine. I'll compare it to my EEE when I can. It's loaned out to a friend at the moment.

---

### Post by jml on 2009-12-10
Sorry for the delay in replying.  Yes, Tom, I do have both an EeePC and a Starling, (good memory.)  I will test tonight when I get home from wore and do a side bi side compareison and post back.

Joe

---

### Post by jml on 2009-12-10
Here is what I got.  My Starling is running Ubuntu 9.04, fully updated, running ver 2.3.7 of the System 76 driver.  My EeePC 900HA is running EeeBuntu version 2.0, also fully updated.  Both computers running on AC power.  

Subjectively,when viewing both computers in a darkened room, the EeePC looks noticeably darker than the Starling when both are set to the lowest intensity.

Semi-objectively, I used my old CdS exposure meter set to measure direct light to measure the intensity of a white background (a blank gedit document,) I did the measurements in a darkened room.  The meter was positioned approximately one inch from the screen.  I measured the light level at both maximum and minimum intensity as set by the function keys.  The results are relative measurements.

Results:EeePC maximum=5.25,    minimun=2.0
        Starling maximum=6.5   minimum=5.0

I noticed that on the Starling after I pushed the button about three times, the screen did not dim any more even though the graphical indicator indicated that I could darken the screen more.  The indicator continued to indicate a reduction in screen intensity without the screen actually dimming.

Hope this is of help.

Joe

---

### Post by thomasaaron on 2009-12-11
Thanks, JML. I appreciate your help.

---

