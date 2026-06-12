---
title: "YouTube videos freeze"
date: 2012-01-02
forum: System76 Support
---

### Post by tersogar on 2012-01-02
With XFCE on 10.04 and using proprietary drivers for ati, YouTube videos freeze and/or are choppy. HTML5 video work. But when I change to open source video drivers, the YouTube videos play fine but the hdmi to 2nd monitor don´t work and the temperature rise about 9°C to 64°C.

If I use Gnome instead of XFCE, youtube videos will play fine with proprietary or open source video drivers so the problem arise only when try to use XFCE with proprietary drivers.

Is there a work around to this problem? 

My model is panp7.

---

### Post by saneearth on 2012-01-02
The easy solution would be to stick with Gnome. :) Sorry, couldn't resist.

---

### Post by tersogar on 2012-01-02
> **saneearth said:**
> The easy solution would be to stick with Gnome. :) Sorry, couldn't resist.

Linux is about choice and realizing how responsive is XFCE with it´s level of customization, I have to say it´s a winner.;)

---

### Post by dodo3773 on 2012-01-02
Flash player stores a lot of its' user defined options in /etc/adobe/mms.cfg

If you do not have that file feel free to create it. An option that used to help a lot of people was adding:

```

OverrideGPUValidation = 1

```

to your mms.cfg. You will need to be root / sudo to make all these changes.

---

### Post by tersogar on 2012-01-02
> **dodo3773 said:**
> Flash player stores a lot of its' user defined options in /etc/adobe/mms.cfg

If you do not have that file feel free to create it. An option that used to help a lot of people was adding:

```

OverrideGPUValidation = 1

```to your mms.cfg. You will need to be root / sudo to make all these changes.


Thank you for your help but unfortunately it did not work for me.  I know flash is a problem as well as the proprietary drivers of my ATI card. I wonder why it work with Gnome and not with XFCE. And also puzzle with the fact that if I use the open-source drivers for the ATI card the videos in youtube will play just fine but the HDMI out to the tv wont work.

---

