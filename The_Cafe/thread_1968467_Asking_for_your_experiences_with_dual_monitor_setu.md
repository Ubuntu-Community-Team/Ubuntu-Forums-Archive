---
title: "Asking for your experiences with dual monitor setups..."
date: 2012-04-29
forum: The Cafe
---

### Post by keithpeter on 2012-04-29
Hello All

I'm experimenting with dual monitor setup on Ubuntu 12.04 using Unity 3d. This recycled HP workstation has an Nvidia GeForce GT520 card with a DVI/D and a VGA video output.

At present I'm using the **nvidia twinview** setting with an old 1280by 1024 monitor and my new 1920 by 1080 monitor. One is electroluminescent panel and the other is LED, so the colour and contrast mismatch is horrible, but I'm just testing the concept and logistics.

Under Unity 3d, the launcher is on both screens, so I just set it to hide using MyUnity.

Questions:

[LIST=1]
[*]Is there a better way of setting up two monitors with an nvidia card and Unity 3d? I like the compiz rendered screen, less flicker than with metacity. I'd like to try one launcher on the left most screen always on.
[*]Is anyone using a couple of matched screens side by side in *portrait* mode? That is the arrangement I'm moving towards. 
[/LIST]

Mods: this is not a support question, as I'm not having any problems as such so I stuck the questions here.

---

### Post by mips on 2012-04-29
> **keithpeter said:**
> 
At present I'm using the **nvidia twinview** setting with an old 1280by 1024 monitor and my new 1920 by 1080 monitor. One is electroluminescent panel and the other is LED, so the colour and contrast mismatch is horrible, but I'm just testing the concept and logistics.

You will have to perform a median calibration from the nvidia control panel followed by calibrating each monitor individually from their built in menu system accessed via the front of the monitors. I run a 23" Samsung & 22" LG this way.
Have a look at some of these links [https://www.google.com/search?client=ubuntu&channel=fs&q=mips+monitor+calibration+site%3Aubuntuforums.org%2F&ie=utf-8&oe=utf-8]("https://www.google.com/search?client=ubuntu&channel=fs&q=mips+monitor+calibration+site%3Aubuntuforums.org%2F&ie=utf-8&oe=utf-8")

Can't help on the Unity questions as I use xfce and that works fine but I have heard some people having difficulty setting up dual monitors on unity.

---

### Post by keithpeter on 2012-04-29
> **mips said:**
> Can't help on the Unity questions as I use xfce and that works fine but I have heard some people having difficulty setting up dual monitors on unity.

Thanks for the google search on colour calibration - I suspect that might get frustrating given the different illumination technology these monitors use but I'll give it a try.

I just plugged the old LCD into the VGA socket and selected twinview from the nvidia-settings application. Works fine on Debian Wheeze with the default Gnome-Shell desktop as well. I suspect the nvidia driver is doing the heavy lifting.

Don't assume I know what I am doing... Ruth likes having an image in GIMP full screen on the big monitor with the control pallettes on the small one.

---

### Post by hoangklam on 2012-04-29
> **keithpeter said:**
> Hello All

I'm experimenting with dual monitor setup on Ubuntu 12.04 using Unity 3d. This recycled HP workstation has an Nvidia GeForce GT520 card with a DVI/D and a VGA video output.

At present I'm using the **nvidia twinview** setting with an old 1280by 1024 monitor and my new 1920 by 1080 monitor. One is electroluminescent panel and the other is LED, so the colour and contrast mismatch is horrible, but I'm just testing the concept and logistics.

Under Unity 3d, the launcher is on both screens, so I just set it to hide using MyUnity.

Questions:

[LIST=1]
[*]Is there a better way of setting up two monitors with an nvidia card and Unity 3d? I like the compiz rendered screen, less flicker than with metacity. I'd like to try one launcher on the left most screen always on.
[*]Is anyone using a couple of matched screens side by side in *portrait* mode? That is the arrangement I'm moving towards.
[/LIST]

Mods: this is not a support question, as I'm not having any problems as such so I stuck the questions here.

Have you tried this:
 - Use CompizConfig Setting Manger, go to Desktop -> Ubuntu Unity Plugin.
 - At Experimental tab, set "Edge Stop Velocity" to 1 and change "Launcher Monitors" to "Primary Desktop".
 - At Behaviour Tab, set "Hide Launcher" to Never.
I have succeed in my laptop with using external LCD.

---

### Post by mips on 2012-04-29
> **keithpeter said:**
> Thanks for the google search on colour calibration - I suspect that might get frustrating given the different illumination technology these monitors use but I'll give it a try.

Don't assume I know what I am doing... Ruth likes having an image in GIMP full screen on the big monitor with the control pallettes on the small one.

I did the search as I knew I contributed to a few of those threads, easier to list one link than me copy & pasting many. ;)

I could be wrong but I think they also moved gimps menus to the panel in unity after they said they would not from what I have heard.

Just play around with the settings on the monitors, it can be a time consuming and frustrating experience but you will get there.

---

### Post by keithpeter on 2012-04-29
@hoangklam: that procedure works, thanks! I just had to change which of the monitors was tagged as the 'primary desktop' in nvidia settings.

@mips: yes GIMP has a global menu, but I have the main GIMP window maximised on the large right hand screen, so the menu is on the top of that window. I use F10 a lot anyway.

Now we are just going to see if we can cope with this acreage of LCD for a bit, then I'll consider a couple of Dell 1600 by 1200 VESA mountable monitors and a mounting bar. The whole lot is half the cost of a 2500px widescreen monitor.

---

### Post by mips on 2012-04-29
> **keithpeter said:**
> 
Now we are just going to see if we can cope with this acreage of LCD for a bit, then I'll consider a couple of Dell **1600 by 1200 **VESA mountable monitors and a mounting bar. The whole lot is half the cost of a 2500px widescreen monitor.

Look into 1980x1200 monitors, they are rare but really nice compared to your average 1920x1080 ones. Personal preference but for me 16:10 aspect ratio is better than 16:9

---

### Post by Zukaro on 2012-05-01
So far my experience with trying to get my second monitor working has been a bad one (I've given up for the time being as I don't actually need it and really only need it when in Windows and playing games).

Basically I tried to use the NVIDIA settings to set it up and ended up having to reinstall Ubuntu.  :P

---

### Post by dikkjo on 2012-05-06
Hi,

to have the launcher only on the leftmost screen you have to set the screen under "System Settings -> Displays -> Launcher Placement". Despite recognizing wrongly the screens with Twinview, if this is set to "All Displays" you will get the launcher on each monitor.

I'm not in portrait mode myself, but I don't see why that would be a problem. You can also mix up the orientations, there is a very good tutorial [here]("http://zuttobenkyou.wordpress.com/2009/10/04/linux-nvidia-xinerama-guide-rotating-just-one-monitor-in-a-dual-head-setup/"). Even if you dont want to mix orientations there are good hints for portrait config.

Have fun with your dual monitor setup ;-)

---

