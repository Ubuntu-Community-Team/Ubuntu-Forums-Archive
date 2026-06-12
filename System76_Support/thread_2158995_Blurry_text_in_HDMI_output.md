---
title: "Blurry text in HDMI output"
date: 2013-07-01
forum: System76 Support
---

### Post by kihjin on 2013-07-01
Just received my Gazelle Pro 9 last week. Everything is working good except there's an issue with HDMI out. Text just doesn't appear very crisp. Red text is especially blurry. I'm using a Sceptre 42". I had the same problem with my previous ubuntu laptop (an Acer Aspire). I discovered I was able to resolve the issue previously by switching to a VGA cable. Some time later discovered that by using a different graphics driver, I could use the HDMI cable and get crisp looking text.

When I move a window over to the laptop's screen, the display is perfect. The HDMI output screen is only a few months old, plus it still displays crisp using my previous laptop.

---

### Post by kihjin on 2013-07-02
This morning I hooked up my laptop to my larger display. To my surprise, the text no longer appeared blurry! I decided to investigate the issue further. My laptop was closed, so I opened it up. This caused the display to adjust. Consequently, the text is blurry again. Not sure on how to go back.

---

### Post by rorschachwalter on 2013-07-02
I can't offer any help, other than perhaps some solace in knowing that you're not alone. HDMI and sleep/wake have strange effects on my Gazelle, and they're not entirely consistent.

---

### Post by kihjin on 2013-07-02
Actually I have the suspend mode disabled when I close the laptop. I have an external display at home (26" Dell), and another external display at work (42" Spectre).

When using the external display at home via HDMI, the text is perfect. 

When using the external display at work via HDMI, the text is blurry. Red text on a black background is especially difficult to look at.

I discovered that if I disconnect the laptop from my home monitor without opening it, and re-attach it to my work monitor, again, without opening it, this causes the text to display correctly.

Tomorrow I will be bringing a VGA cable to work to see if that corrects the issue, although I will be disappointed in being unable to use HDMI.

---

### Post by 3Miro on 2013-07-02
In my experience blurry text is usually due to wrong resolution. Check your settings and make sure to use the monitor's native resolution. Do you know what resolution the monitor usually uses?

---

### Post by kihjin on 2013-07-02
The external monitor is a 42" screen with a maximum resolution of 1920x1080. In Display, it is configured as 1920x1080.

---

### Post by kihjin on 2013-07-03
Tried out the VGA cable today. Text shows up perfectly. Switching over to HDMI, text shows up not so great, especially red.

I think the problem might me that this external screen is reporting invalid EDID information. In Ubuntu Display settings via HDMI it registers as a 19" Spectre. Over VGA it registers as a 42" Spectre.

---

