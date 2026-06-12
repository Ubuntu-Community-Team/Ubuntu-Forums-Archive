---
title: "M10 OTA12 HDMI Aspect Ratio"
date: 2016-08-03
forum: Ubuntu Phone and Tablet
---

### Post by dtarrant on 2016-08-03
When I connect my tablet to my Panasonic Viera TV by HDMI cable, I can never see the control icons at the sides of the M10 display. This is because my Viera aspect ratio is 16:9 and my ubuntu tablet outputs 16:10 format. I've tried all the Viera aspect settings and in every case the edges of the display are off-screen. This means that my tablet is unuseable with my Viera. Is this a fundamental limitation of the M10 or might there be a future fix? I can't afford to buy another TV.

---

### Post by lapor2 on 2016-08-03
Hey,
I had the same problem with Samsung TV. I just played a bit with TV settings and I found that non of the versions of monitor size works (16:10, 16:9, zoom, extra zoom). But one thing worked. There was somewhere to just scan the size of the monitor, and that works. Can you maybe try with some other computer over HDMI. Because devs told me that this is now a bug. But a TV problem. Check the my [bug report]("https://bugs.launchpad.net/ubuntu/+source/mir/+bug/1607445").

I hope it helped

---

### Post by dtarrant on 2016-08-03
> **lapor2 said:**
> Hey,
I had the same problem with Samsung TV. I just played a bit with TV settings and I found that non of the versions of monitor size works (16:10, 16:9, zoom, extra zoom). But one thing worked. There was somewhere to just scan the size of the monitor, and that works. Can you maybe try with some other computer over HDMI. Because devs told me that this is now a bug. But a TV problem. Check the my [bug report]("https://bugs.launchpad.net/ubuntu/+source/mir/+bug/1607445").

I hope it helped


Thanks for your reply Kristijan. I've tried connecting my Blackberry Playbook to my Viera via HDMI and it works perfectly. So the Viera is not cutting the sides of the image. However the Blackberry Playbook screen aspect ratio is 16:9 which matches the Viera. Seems I can't set the M10 to output at 16:9 and I can't set the Viera to accept 16:10.

---

### Post by dtarrant on 2016-08-03
> **lapor2 said:**
> Hey,
I had the same problem with Samsung TV. I just played a bit with TV settings and I found that non of the versions of monitor size works (16:10, 16:9, zoom, extra zoom). But one thing worked. There was somewhere to just scan the size of the monitor, and that works. Can you maybe try with some other computer over HDMI. Because devs told me that this is now a bug. But a TV problem. Check the my [bug report]("https://bugs.launchpad.net/ubuntu/+source/mir/+bug/1607445").

I hope it helped

Hi Kristijan,

When you say "there was somewhere to just scan the size of the monitor", do you mean from the ubuntu tablet or from the Samsung TV?

Cheers,

David

---

### Post by dtarrant on 2016-08-03
> **dtarrant said:**
> When I connect my tablet to my Panasonic Viera TV by HDMI cable, I can never see the control icons at the sides of the M10 display. This is because my Viera aspect ratio is 16:9 and my ubuntu tablet outputs 16:10 format. I've tried all the Viera aspect settings and in every case the edges of the display are off-screen. This means that my tablet is unuseable with my Viera. Is this a fundamental limitation of the M10 or might there be a future fix? I can't afford to buy another TV.

When I connect my Raspberry Pi running Raspbian to my Viera via HDMI, the display is fine. Raspbian has automatically determined the correct setting. In the event that Raspbian is unable to do this, there is a config file which you can edit to achieve custom settings. However 16:9 and 16:10 are provided as standard. My conclusion is that it must be technically possible to implement a similar solution for the M10.

David

---

### Post by lapor2 on 2016-08-04
Hey,

on my Samsung tv, I have to go to Settings/Size and there I can choose between 16:9, 4:3, zoom, wide, wide zoom or just scan. If I choose just scan, I get correct aspect ratio. I have not checked with some other computer and hdmi.
Did you add that to the bug report? If not, please add it.

Cheers

---

### Post by dtarrant on 2016-08-04
> **lapor2 said:**
> Hey,

on my Samsung tv, I have to go to Settings/Size and there I can choose between 16:9, 4:3, zoom, wide, wide zoom or just scan. If I choose just scan, I get correct aspect ratio. I have not checked with some other computer and hdmi.
Did you add that to the bug report? If not, please add it.

Cheers

On my Viera, there is an aspect control which I set to Auto (I assume this corresponds to Samsung's Scan). Initially this did not solve the problem. I then found a picture settings option and experimented with the option settings and the screen settings. Eventually I found a combination that worked. I'm afraid I can't explain how I achieved this as the menu system was confusing and the options displayed seemed to depend on whether the HDMI cable was connected and also whether the M10 was switched on. Anyway, I pleased to report that my HDMI display is now looking good. So many thanks for your help.

Cheers,

David

---

