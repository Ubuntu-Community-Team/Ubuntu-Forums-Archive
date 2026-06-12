---
title: "Dual monitor setup in unity screws up icons and workspace switcher"
date: 2013-04-17
forum: Ubuntu Development Version
---

### Post by Killerah on 2013-04-17
Howdy folks, it's been a while since I have posted here, but I have a quick question about making my dual monitor set up make more logical sense in unity.

My issues are twofold and can be seen in the following image: [http://i.imgur.com/v5vnReJ.jpg](http://i.imgur.com/v5vnReJ.jpg)

First, I hate the way that unity does the workspace switcher by default if you have dual monitors enabled. It's very ugly and doesn't make sense. What would make more sense is to have each monitor show a separate grid, rather than trying to render a massive grid across the two monitors how it currently does. As you can see from the screenshot, there is some overlap in the current default way of displaying things, the Chrome window with Ubuntu forums can be seen displayed on both monitors which doesn't reflect the reality that when I get out of workspace switcher, the window is only on one workspace (namely workspace 1 on the monitor on the right). 

I hope I'm making sense here. 

My second issue is the way icons get whacked out whenever I plug in my second monitor. This also is ugly and makes no sense. As you can see in the link I provided above, unity is trying to render the icons outside of the visible range of my primary screen which doesn't do me any good if I want to use them. You can see here how it plays out when I'm not in the workspace switcher: [http://i.imgur.com/Ox1v6LK.jpg](http://i.imgur.com/Ox1v6LK.jpg)
Basically, the icons are above the actual desktop space and I can't use them at all! 

I'm wondering if anyone else has had similar problems and what solution you have come to? I have just been living with these issues for a while and have sort of gotten used to them. But they just don't make any dang sense. So if you guys have any solutions I would love to hear them!

Thanks,
Nate

---

### Post by ksanger on 2013-04-19
I assume that because you have the unity icons on the left on both displays that the displays are being mirrored.  On my system the displays are the same resolution (1920x1024) and display the same image when mirrored is checked.  You probably also need to set the display resolution for each display to the correct size so that the desktop displays correctly on each one.

I had issues unchecking mirror in System Settings, Displays.  First you need to increase the virtual display size.  Then you can successfully un-mirror the displays and get two usable desktops.  I'm running Ubuntu 12.04.  I assume 12.10 would be similar.

Note I have an AMD Radeon HD 7770.  If you have a GForce or NVidia video  card you would need a different method.  For the default Ubuntu video  drivers we probably create Xorg.conf and modify it by hand.  I loaded the ATI/AMD proprietary FGLRX graphics drivers which also loaded AMD Catalyst Control Center (administrator).  I was able to use AMD Catalyst to setup multiple displays.  [start AMD Catalyst Control Center (administrator), Select Display Manager, select Multi-Display tab, then use the drop-down list to select Multi-display desktop with displays(s) 2.]  I believe this changes Xorg.conf, including increasing the Display Virtual size.  After doing this you then go to System Settings, Displays, and uncheck mirror.  I was also able to use Catalyst to adjust the color of the monitors so that they look similar.  AMD Catalyst also would enable me to set the display resolution for each monitor.

Two displays are awesome.  Though I haven't figured out if I can put one workspace on one and another workspace on the other.  That would be more awesome as we could switch back and forth between multiple workspaces on multiple displays.

Good luck.

---

### Post by JessiDLuvr on 2013-05-10
> **ksanger said:**
> Two displays are awesome.  Though I haven't figured out if I can put one workspace on one and another workspace on the other.  That would be more awesome as we could switch back and forth between multiple workspaces on multiple displays.

Good luck.

I got two displays showing different desktops. I'm running Ubuntu 13.04. I got Google Chrome on my main (laptop) screen and VLC running on an external monitor. Works like a charm. The two monitors are fundamentally different in resolution in width (my laptop native is 1366*768 and my monitor's native is 1024*768), but it works awesome.

It took a bit of time fiddling with AMD Catalyst Control Center, but the steps I done are this:

1. Launch AMD Catalyst Control Center (Administrative).
2. Authenticate.
3. Go to Display Manager in amdccc.
4. Have your external monitor plugged in.
5. Select your secondary monitor.
6. Click on "Multi-Display."
7. Where it says "Disabled Display," change this to "Multi-Display with Display(s) 1" (It will say "1" at first, but this will change soon.)
8. Click Apply.
9. Click "Yes" when asked if you desire to keep or discard the changes.
10. If a dialog pops up reminding that settings will take effect when restarted, click "OK".
11. Reboot if needed. If not, skip to step #13.
12. Log in normally.
13. If everything looks good, you're set!
14. **Important:** If your monitors are of different resolutions, you may need to re-run AMD Catalyst Control Center again to fix it. It took me a bit of fiddling and a little bit of cussing, but I got it working.

Hope this helps! :p

JessiDLuvr -> Jessica's (my wife's) lover... I'm known as this on many fora... you'll just have to figure out *which* ones... ;)

---

### Post by cariboo on 2013-05-10
Unless you're running Saucy, there's no need to post your Raring experiences here. Thread closed.

---

