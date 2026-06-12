---
title: "Connect monitor with DVI connection"
date: 2010-10-22
forum: System76 Support
---

### Post by volkerbradley on 2010-10-22
My system is a Serval Pro running Ubuntu 10.4, 64 bit. 
I would like to use an external monitor which has a DVI connector.
I connected this DVI connector to the DVI port on the laptop but the monitor did not display anything.
In the NVidia X Server Settings utility, I see that the Dell E207WFP is disabled. When I click on configure, I am given the choice of Separate X screen or Twinview.
I really don't know how to configure the monitor.  Could you help? 
Thanks.

---

### Post by isantop on 2010-10-22
Hi.

You'll want separate X screen if you need both monitors to have separate sets of settings. For example, 24-bit color on one and 16 on the other. Otherwise, you'll want twinview, since this will let you drag windows between monitors.

---

### Post by volkerbradley on 2010-10-23
> **isantop said:**
> Hi.

You'll want separate X screen if you need both monitors to have separate sets of settings. For example, 24-bit color on one and 16 on the other. Otherwise, you'll want twinview, since this will let you drag windows between monitors.
Thank you for the suggestion.  It works just fine now.  The only residual problem is that Docky does not show on the screen of the accessory monitor.  Clicking on the Applications -> Accessories -> Docky to start Docky has no effect.
Have you heard of this before? Any suggestions?
Thanks.

---

### Post by volkerbradley on 2010-10-24
OK, I figured it out.  In order for the Docky to show up on the monitor, I stopped the display on the laptop.  The accessory monitor displays everything now.
Thanks for your help.

---

