---
title: "OK, hV"
date: 2011-12-23
forum: System76 Support
---

### Post by vanhenryjr on 2011-12-23
I have a gazelle professional with 8 mega RAM-runnig ubuntu 11.04. I cannot figure out how to run a video output via HDMI that I plug into my TV. I see an audio help on the system 76 website, but not a video. 

Help? have already looked at monitor settings and will try a restart while plugged in

tia
van

---

### Post by cbennett926 on 2011-12-23
I don't want to point out the obvious, but sometimes that's what everyone overlooks, is there a key to connect to a projector; perhaps that's what you need to do.

---

### Post by vanhenryjr on 2011-12-23
will look and try. i am sure it is obvious, but I have no idea

---

### Post by cbennett926 on 2011-12-23
Another thing you could try is going to displays and see which screen it is displaying on, which will in turn show if it has recognized the second screen.

---

### Post by vanhenryjr on 2011-12-23
I have a settings icon for monitor, but not displays.

What I need to is step by step procedure to do HDMI. Still doing google searches. evidently HDMI "works well" on this laptop.

---

### Post by dodo3773 on 2011-12-25
When you say that you "have already looked at monitor settings" do you mean the Ubuntu / Gnome settings or nvidia-settings? Are you using the proprietary driver?

---

### Post by vanhenryjr on 2011-12-27
I am using the driver that came with the system 76 laptop.

I have looked at both the monitor settings in the equivalent of "control settings" and looked at the nvida settings using a command line to open them. Neither show an obvious way to do hdmi output.

I guess no one else with a system 76 is doing any HDMI output or no one is occasionally browsing this thread. Being able to do HDMI output to my HD TV would be awesome.

---

### Post by dodo3773 on 2011-12-27
> **vanhenryjr said:**
> I am using the driver that came with the system 76 laptop.

Try the proprietary driver and run nvidia-settings and see if that helps.

---

### Post by isantop on 2011-12-27
Press the Ubuntu key on your laptop, then type in the word "nvidia". Click on the result. 

Now, click on"X Server Display Configuration".

Click "Detect Displays"

Click on the "(Disabled)" monitor above.

Set "Configuration" to "TwinView"

Click "Apply", then in the confirmation screen, click "OK".

The screen may become corrupted. If it does, simply wait 30 seconds for the display to return to normal, then try again. This is a known issue, and is due to bugs between Ubuntu's desktop environment, and the proprietary Nvidia driver. The configuration will save properly on the second or third attempt, and this issue will be worked out for 12.04 in April.

---

### Post by vanhenryjr on 2012-01-05
thank you isantop. 

It took a few tries as you said but I was able to watch the Sugar Bowl on our TV via HDMI. 

trying to mark this thread as SOLVED

I can't figure out why the name is what it is!

---

