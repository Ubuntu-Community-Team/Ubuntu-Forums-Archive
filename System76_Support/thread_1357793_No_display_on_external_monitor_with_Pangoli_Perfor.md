---
title: "No display on external monitor with Pangoli Performance panp6"
date: 2009-12-17
forum: System76 Support
---

### Post by ldt on 2009-12-17
I just unpacked my new Pangoli Performance panp6 today. Ubuntu 9.10 installed and updated just fine. All seems to be working fine so far. But I'm unable to get a display on the external monitor. I've tried connecting the monitor directly to the VGA out connector and the monitor stays black even after a reboot. When I connect my KVM switch (monitor and USB keyboard and mouse) the keyboard and mouse work fine but the monitor remains black. The monitor works fine with my other two computers through the KVM switch. I've searched the forums and surprisingly don't see this problem mentioned before. I'd be grateful for some help.

---

### Post by thomasaaron on 2009-12-17
Go to a terminal and run...

sudo nvidia-settings

You will find an option there to activate your monitor. (Although I'm not exactly sure how that shows up through a KVM switch.)

---

### Post by ldt on 2009-12-18
The nvidia-settings TwinView does turn on the second monitor. But I could use some tips on where to go from here. The problem I'm having is controlling the views. My Pangoli Performance panp6 has a resolution of 1600x900. My second monitor is a Dell at 1600x1200. When I first selected TwinView the Pangoli display stretched and I lost the panels at the bottom of the screen (I have them all configured to display at the bottom.) Each time I try a new setting things change and never seem to come back to the original baseline. At the moment I have managed to get the Pangoli display back to normal but the Dell display stretches and I lose some of the left of the display (including browser scroll bars.) .
 

 When I try to save to the configuration file I get “xorg.conf parsing error”. The terminal says “Data incomplete in the file /etc/X11/xorg.conf. Undefined Device “(null)” referenced by screen “Default Screen”.
 

 I think I need to use the Separate X screen mode, but the configuration instructions in the nvidia guide are complicated and incomplete. Is there a simple way to do this?

---

### Post by thomasaaron on 2009-12-18
This tutorial should still be pretty accurate. You will not need to follow steps 1, 2, and 3.

[http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup](http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup)

Let me know if you have any problems. We may need to get you back to the default xorg.conf.

---

### Post by ldt on 2009-12-18
The “xorg.conf parsing error” seems to be indicative of some problem other than just not knowing the right settings. I tried following the tutorial and it didn't quite work for me the way he described. I set both displays to TwinView auto and the display on the external monitor was still stretched and partially off screen. “Save to X config file” still gives a segment fault and error message. I don't get the “show preview” pop up Stephen O'Sullivan talks about. I even tried “nvidia-settings” without the sudo as he did thinking that might force the pop up. But I just got the same parsing error/segment fault result. I then rebooted to see what I had. Then things got really strange. The external monitor is off – no surprise there. But when I tried “nvidia-settings” from a terminal I get an error message at the terminal complaining about a problem with line 53 of the file %HOME/.nvidia-settings-rc. Sure enough that file now exists. Any idea what's happening?

---

### Post by thomasaaron on 2009-12-18
OK. Can you send me an email (support...at...system76...dot...com) and let's get a stock xorg.conf back in there. That will give us a clean slate to work from.

---

