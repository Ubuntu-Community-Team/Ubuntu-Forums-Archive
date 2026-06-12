---
title: "No laptop lid closing power options in Ubuntu 13.04"
date: 2013-04-01
forum: Ubuntu Development Version
---

### Post by Odzinic on 2013-04-01
[COLOR=#333333][FONT=Ubuntu Beta]I installed 13.04 last night on my laptop. I opened up the power settings to choose what the system should do when the lid is closed, but there is no option. There is only options for blank screen, automatic suspend, wifi and when the battery is critical.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Is anyone else experiencing this issue?[/FONT][/COLOR]

---

### Post by cariboo on 2013-04-02
I have the option on this system running Ubuntu Gnome. See the screenshot.

---

### Post by rrnbtter on 2013-04-02
Greetings,
I have the option in my power settings but it doesn't activate the function when set. I think this ACPI stuff is machine specific and has problems across the board with Linux since it depends on kernel drivers. Also, I've seen blurbs where prying ACPI info from hardware developers is hit and miss. You can't suspend if you don't know how the electronic button works. Probably the priority goes to video, network, audio and other primary functions. "I suppose".

---

### Post by cariboo on 2013-04-02
I got my Compaq netbook around the end of Lucid testing, suspend on lid closing has always worked on this system, it actually works better running the development versions since then, than it did running Windows.

---

### Post by rrnbtter on 2013-04-02
Greetings,

> **cariboo907 said:**
> I got my Compaq netbook around the end of Lucid testing, suspend on lid closing has always worked on this system, it actually works better running the development versions since then, than it did running Windows.

Interesting! My wifes Toshiba NB505 Netbook has had suspend since Lucid and still does with Kernel 3.9RC5 and Raring. My Toshiba L305 still doesen't suspend. Both computers have tested every release along the way with the same results.

---

### Post by Odzinic on 2013-04-02
> **cariboo907 said:**
> I have the option on this system running Ubuntu Gnome. See the screenshot.
Strange. This is what mine looks like with Gnome shell 3.7.92

---

### Post by mc4man on 2013-04-02
You'll find a lot of options in gsettings (dconf-editor > org/gnome/settings-daemon/plugins/power
Whether changes/settings there have the intended or any effect on your setup is only something you can tell.
(some work here, some don't

---

### Post by Odzinic on 2013-04-03
> **mc4man said:**
> You'll find a lot of options in gsettings (dconf-editor > org/gnome/settings-daemon/plugins/power
Whether changes/settings there have the intended or any effect on your setup is only something you can tell.
(some work here, some don't
I tried editing the gconf settings and it had no effect.

---

### Post by pfeiffep on 2013-04-03
I have daily 13.04 installed on an ancient Dell laptop. I didn't upgrade my 12.10 install, I installed on a USB hdd. I performed all the 'unity' upgrades and configurations prior to installing gnome session fallback. My power settings are normal for a laptop.

---

### Post by kinggo on 2013-04-05
well, yes if you are still on gnome 3.6.
This all suspend fiasco also bugs me a lot. I've beeen reading a lot around and if I understand correctly, for now, there's no way to turn on anything with a lid switch. 
But what I don't know is if this will ever return as an option or not.

---

### Post by Odzinic on 2013-04-05
> **kinggo said:**
> well, yes if you are still on gnome 3.6.
This all suspend fiasco also bugs me a lot. I've beeen reading a lot around and if I understand correctly, for now, there's no way to turn on anything with a lid switch. 
But what I don't know is if this will ever return as an option or not.
It will most likely be implemented. Doesn't make much sense not having lid options for laptops. I guess we just have to give it time since the release of the final beta still didn't fix the issue for me.

---

### Post by rrnbtter on 2013-04-05
Greetings,
Raring has suspend and resume working for supported hardware.  You can check the change logs for the various kernels if your system won't suspend. I use kernel 3.9RC5 and my computer won't suspend but my wife's netbook will.  Like any other hardware the support will be machine specific. I don't know of hibernate or shutdown functions working.

---

### Post by kinggo on 2013-04-05
this has nothing to do with kernel. Suspend works if it is trigered with keyboard or via menu. But for some technical and privacy concerned reasons lid switch is ignored. There's no option for it in power settings or privacy settings or in gnome tweak tool.

---

### Post by kevpan815 on 2013-04-06
My two Laptops are displaying the Battery Charge Icon Normally with Unity 13.04 Beta 2. Have not tried to open up Power Options, but the system does go to Sleep Normally when the Lid is Closed. It also Resumes from Standby normally.

---

### Post by kinggo on 2013-04-06
well, I don't know for unity, but in gnome shell doesn't.
But I found a way to turn on suspend with a lid switch. [https://bugs.launchpad.net/ubuntu-gnome/+bug/1160995](https://bugs.launchpad.net/ubuntu-gnome/+bug/1160995)
 It's not configurable, it's not available in any settings but it does what I want, always suspend when I close the lid.

---

### Post by Odzinic on 2013-04-06
> **kinggo said:**
> well, I don't know for unity, but in gnome shell doesn't.
But I found a way to turn on suspend with a lid switch. [https://bugs.launchpad.net/ubuntu-gnome/+bug/1160995](https://bugs.launchpad.net/ubuntu-gnome/+bug/1160995)
 It's not configurable, it's not available in any settings but it does what I want, always suspend when I close the lid.
This worked for me. Thanks for the temporary fix.

---

### Post by emdeem on 2013-04-29
Just adding another datapoint to this discussion:

My laptop is a Lenovo X1 Carbon.  Lid suspend worked fine out-of-the-box with Quantal.  It does not work on a clean install of Raring.

The fix in the bug report works for me.  Also, please note, the bug report implies that the fix is Gnome-specific.  It is not and works for me on a stock Unity install.

---

