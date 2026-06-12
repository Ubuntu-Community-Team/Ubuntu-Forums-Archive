---
title: "Duplicate Monitor (Dell)"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wpexpert on 2012-04-02
Hi everyone,

I just installed ubuntu! Very cool so far! I am having a little problem though. I have a Lenovo t61 and I use a docking station. I rarely every actually use the laptop screen. Instead, I use my big Dell screen. However, I cannot get it hoked up. When my computer boots it displays fine on the Dell screen but than as soon as it hits the login screen it goes into sleeping mode. 

I am using the Ubunto 12 version.

I have tried both the blue and the white hookup cable. The monitor is a Dell E2009W. 

Many thanks!

---

### Post by wpexpert on 2012-04-03
Extra information:

The driver that I have installed is called "NVIDIA accelerated graphics driver (version current)" and I also have the (post-release updates)(version current-updates) driver installed. I have tried them both with no luck.

The Dell monitor works fine when the computer starts but as soon as it hits the login screen it switches over to my laptop screen and the monitor goes to "sleep." 

I would really appreciate any help as this is a somewhat urgent matter. It was working fine with Windows 7 just yesterday.

Many thanks.

---

### Post by cortman on 2012-04-03
Hi,

What happens if you run

```
xrandr --output VGA1 --auto
```

This bit of code assumes you have it plugged into the VGA port. If it's HDMI, substitute HDMI1 for VGA1. If DVI, DVI1.

---

### Post by wpexpert on 2012-04-03
> **cortman said:**
> Hi,

What happens if you run

```
xrandr --output VGA1 --auto
```

This bit of code assumes you have it plugged into the VGA port. If it's HDMI, substitute HDMI1 for VGA1. If DVI, DVI1.

Many thanks for your help. Unfortunately that didn't seem to work. I received the following message: 

xrandr: Failed to get size of gamma for output default
warning: output VGA1 not found; ignoring.

---

### Post by oldos2er on 2012-04-03
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by cariboo on 2012-04-03
Are you using Nvidia Xserver settings to setup your dual monitor setup? Just open the dash and type *nv* and press enter.

---

### Post by wpexpert on 2012-04-03
> **oldos2er said:**
> Thread moved to Ubuntu +1 (Precise Pangolin).

Thanks for moving it to the appropriate place. :p .

I was actually able to get it to work in the mean time by playing around with the nvidia settings. However, even the best screen resolution doesn't display as clear as it would on a windows OS.

---

### Post by bmbaker on 2012-04-03
i was having a similar problem which i solved by changing to twinview in nvidia settings!

---

### Post by wpexpert on 2012-04-03
Perfect! Thanks a lot for the help everyone! I really appreciate it...

One last question: How often should I be visiting the Update Manager since I'm on the beta version? I installed a whole bunch of updates this morning. I do notice that there are still a few bugs like sometimes opening up Thunderbird brings a huge white screen which I then have to minimize and so forth.

Also, in Chromium, why are there two sets of close, minimize and maximize buttons in the left upper corner? Seems redundant.

---

### Post by cariboo on 2012-04-03
I'd suggest check for updates at least daily, I'm just in the process of updating my Ubuntu and Xubuntu installs on my netbook. The Ubuntu install hasn't been updated in a week, and there were over 460 packages that needed upgrading. The Lubuntu install was done on Saturday, and it needed 220 packages upgraded.

---

### Post by wpexpert on 2012-04-03
Thanks for the advise, I'll frequent the update manager then. Is there a feed or an email list I can subscribe to in order to say informed about what's going on in these releases?

I also just noticed with the last set of updates that I installed that the lock screen still shows the menu dock on the left along with the time and my name and all those icons top right. It may be best for the lock screen to just display the login prompt with a background?

I'll keep submitting any errors I come across. Thanks!

Also, how would I be able to update the actual version - say 12.04 to 12.05? Does that all happen through the update manager? I'm still new here and trying to find an answer to that.

---

### Post by meborc on 2012-04-03
if you want more info and discussion on updates, check out the ubuntu-devel mailing list - [https://lists.ubuntu.com/](https://lists.ubuntu.com/)

If you keep updating, you will have the final 12.04 version in the end of April, also read this - [http://ubuntuforums.org/showthread.php?t=1859235](http://ubuntuforums.org/showthread.php?t=1859235)

---

