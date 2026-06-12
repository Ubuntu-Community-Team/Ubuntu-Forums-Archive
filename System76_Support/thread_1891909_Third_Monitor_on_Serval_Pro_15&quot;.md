---
title: "Third Monitor on Serval Pro 15&quot;"
date: 2011-12-06
forum: System76 Support
---

### Post by StatsJunkie on 2011-12-06
I have a 15" Serval Pro with an Nvidia chipset. I have disabled the onboard display, and currently connect to a Samsung SyncMaster 2333 using TwinView.

I have a free HDMI port, and I imagine I can connect a second monitor via this port since the onboard display is disabled. I am having a lot of issues doing so.

Whenever I try to enable the second monitor, I can configure it, and write the settings to the X11 config file, but the settings are never saved. When I reboot X, the second monitor is disabled again.

I also tried using "New X Window" for the second monitor which promptly crashed the control panel.

I would like to eventually have the following setup:

Samsung SyncMaster 2333, primary monitor, horizontal/standard, 1920x1080.
Samsung SyncMaster 2443, secondary monitor, **vertical/portrait**, 1920x1080.

Does anyone have suggestions?

---

### Post by osx424242 on 2011-12-06
Kind of a shot in the dark here, but.... Are you using nvidia-settings or nvidia-xconfig?  If so, are you *sure* the settings are being written to the file?  I remember having a lot of problems (with a non-System76 laptop) getting one or the other of those programs (I think nvidia-xconfig) to actually write out to a file.  I had to either run it as root, or change the permissions of /etc/X11 and /etc/X11/xorg.conf to give write access to my regular user account (once I got the config files written, I changed that back).

---

### Post by StatsJunkie on 2011-12-06
> **osx424242 said:**
> Kind of a shot in the dark here, but.... Are you using nvidia-settings or nvidia-xconfig?  If so, are you *sure* the settings are being written to the file?  I remember having a lot of problems (with a non-System76 laptop) getting one or the other of those programs (I think nvidia-xconfig) to actually write out to a file.  I had to either run it as root, or change the permissions of /etc/X11 and /etc/X11/xorg.conf to give write access to my regular user account (once I got the config files written, I changed that back).

I am not sure :-/ It is the nvidia settings control panel available in the Ubuntu menu: nvidia X Server Settings. I am guessing that would be nvidia-xconfig.

---

### Post by osx424242 on 2011-12-06
> **StatsJunkie said:**
> I am not sure :-/ It is the nvidia settings control panel available in the Ubuntu menu: nvidia X Server Settings. I am guessing that would be nvidia-xconfig.

Actually, I suspect that is nvida-settings.  If you care, you could try running each from the command line and seeing which one matches the program you're running from the menu.  I don't think it matters, though, as long as you really are running one of those.

So, you could *try* this:
```
sudo chmod o+w /etc/X11 /etc/X11/xorg.conf
```
then change your settings.  Then restore the permissions:
```
sudo chmod o-w /etc/X11 /etc/X11/xorg.conf
```
and reboot, and see if it worked.

Like I said, pretty much a shot in the dark, but I *think* I remember seeing *similar* symptoms to what you described, and I *may* have gotten things to work this way.

---

### Post by StatsJunkie on 2011-12-06
Thanks. I tried that, and my settings were not saved. :(

---

### Post by isantop on 2011-12-07
None of our system support using two simultaneous external monitors. Multi-monitor set ups are possible, but they must use the built-in display in addition to one external display.

---

