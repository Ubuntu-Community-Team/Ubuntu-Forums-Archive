---
title: "GazP6 Dual Monitor Issues Workaround/Fix"
date: 2011-10-17
forum: System76 Support
---

### Post by chriscross93 on 2011-10-17
I've found a workaround that allows one to make use of their second monitor on Ubuntu 11.10.

After completing a fresh install of 11.10 from CD, I found myself unable to successfully apply new display configurations when using the nvidia-settings GUI.  This is what I got to work.

**Workaround for applying new monitor configuration with proprietary NVidia Driver on Ubuntu 11.10:**

1) Start NVidia Settings GUI as root.
```
sudo nvidia-settings
```

2) Using GUI, set up desired X Server Display Configuration.

3) Press "Save to X Configuration File" Button.
(If you get a message to the effect of xorg.conf not existing, you will need to make it manually.  Just copy & paste the text outputted by nvidia-settings into a text editor and save the file as /etc/X11/xorg.conf.  You will need to be root to do this, let me know if you have any questions.)

4) Press "Save" button.

5) Reboot Ubuntu.

Upon starting up, the X Server read & applied my configuration without any trouble.  The problem only appears to apply when enabling the output while "live."

**A Few Notes...**
These are some specifics to my configuration/situation that *may* have an effect on this actually working for you.  I don't know, just FYI:

- I manually set my display resolution on both monitors.
- My external display is the default X Screen.  aka, that is where I keep Unity's Launcher/Dash/Thingy.
- If I try to switch away from & back to tty7 (ctrl-alt-fkeys) I have to reboot.  The same issues occur with my displays as when trying to change configuration "live" with the nvidia-settings GUI.

- This had no effect on another problem I've been having.  LightDM does not start as it should during boot, causing Ubuntu to hang every time.  My workaround:

**Starting LightDM Manually During Boot:**
Once Ubuntu hangs, for me it is right after "checking battery state" is displayed.

1) Press "ctrl-alt-f1"
2) Log In
3) Run:
```
sudo start lightdm
```
4) Enter password when prompted.
At that point you should be transferred to the LightDM login screen and all should be well. (Until you reboot next.)

If you have any questions, feel free to ask.  I tried to be as thorough as possible - but I will post any additional details as needed.

---

