---
title: "Screen Resolution Issues"
date: 2008-12-09
forum: System76 Support
---

### Post by earrame on 2008-12-09
Time for my own screen resolution thread.

I upgraded to Ibis to eliminate the missing sound problem. Everything seemed fine except the screen resolution. I've been working with it but am now completely stumped.

My vitals:

[B]uname -r: 2.6.27-9-generic
System: panp4i
Ubuntu 8.10
System76 driver version: 2.2.7[/B]

After the upgrade to 8.10 my available resolutions were only 1024, 800, 640. All of which are useless on a wide screen format.

First I did this:

#Backup your xorg.conf...
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

#Re-create it... Use ALL defaults
sudo dpkg-reconfigure xserver-xorg

After a reboot there was no change in available resolutions. Just to see what would happen I set the resolution to the only other available option; 'off'.

Little did I expect that to turn the display off **forever**. I have to wonder what use that setting could possibly offer.

Next I tried to log in with a different session. With one exception everything went black, even 'Gnome Failsafe'. The login itself seems fine in all cases. Except that the screen goes black as soon as I log in.

The exception is terminal failsafe.

Once at the terminal I did:

sudo dpkg-reconfigure xserver-xorg

reboot, no change.

I restored the xorg.conf.backup to xorg.conf

reboot, no change.

Next I opened xorg.conf using nano.

I don't see how this file is doing anything to the screen resolution. Here is the display section:

(painstakingly typed here on my wife's iMac)

[I]Section "Screen"
        Identifier  "Default Screen"
        Monitor     "Configured Monitor"
        Device      "Configured Video Device"
EndSection[/I]

Shouldn't that list the screen resolution modes? Google searches tell me  that xorg.conf is the master of all things display related. I don't see anything in this file that I would even guess might be the correct setting to adjust.

Where is the file that is actually telling the screen to go black when I log in?

---

### Post by Alvinius on 2008-12-10
video driver?

---

### Post by earrame on 2008-12-10
Not sure where to look. Would sudo lshw -c display provide the neccessary info?

The output is:

*-display:0 UNCLAIMED
description: VGA compatible controller
product: Mobile 4 series Chipset Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 07
width: 64 bits
clock: 33MHz
capabilities: msi pm bus_master cap_list
configuration: latency=0
*-display:1 UNCLAIMED
---all following info identical to the above

I've also been poking around in gnome configuration files. Looking for whatever file is being fed the contents of xorg.conf in order to display the resolution options in the drop down list.

Something in /.gconf/desktop/gnome/screen   ...except that there is no /screen directory under my /gnome.

---

### Post by Lee_Machine on 2008-12-10
Do you have your video drivers installed?

If not install the nvidia video drivers. They are in symantic. The newest one is 177.82

Also envy is a good way of installing them.


[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

envy will install the driver and edit xorg with the correct resolutions. just a short time ago you had to do that manually if you wanted peak resolution your monitor could possibly handle. That and dual screen support with an HDTV, but it all just works now :p

---

### Post by thomasaaron on 2008-12-10
**Lee_Machine**, this is not an nVidia computer. It has Intel graphics.

The problem is that the PanP4i has a ghost monitor present when it is first imaged with Intrepid. The resolution defaults to the ghost monitor. 

This is a particularly idiotic bug, but there it is.

**earrame**, I wish you wouldn't have turned the resolution to off. That makes it a little more difficult to fix. But here is what you need to do:

1. Hook your computer up to an external monitor and turn it on. This should give you a display on the external monitor. 
2. Go to System > Preferences > Screen Resolution and you will see two rectangles: one of them represents your LCD. Click that rectangle, and then turn your resolution back on.
3. Shut your machine down. Remove the external monitor. Restart your machine. Your LCD should now work.
4. Now, go into System > Prefs > Screen resolution. Select the rectangle that represents the non-existent ghost monitor and turn it OFF.
5. Now you should be able to correctly set your LCD resolution.

---

### Post by Lee_Machine on 2008-12-10
Oh i apologize. I assumed the difference between the Panp4i and n were the screen resolutions.

Sorry for the bad advise.

---

### Post by earrame on 2008-12-11
That's ok Lee_Machine. I would have answered something about not knowing the status of video drivers after the upgrade.

> **thomasaaron said:**
> I wish you wouldn't have turned the resolution to off.

That makes two of us.:biggrin:

Especially as the 2nd monitor procedure is being funny. I don't have any stand alone monitors at home so I declaired today 'Take your Pangolin to work day'.

I ran through it a good dozen times or so. No matter what state I leave the Screen Resolution settings the Pangolin LCD won't turn back on unless the 2nd monitor is plugged in.

Step by step;

I ran through the procedure. When I started Pangolin with the 2nd monitor not only did the display work but there were three monitors in the Resolution dialog. 'Notebook 15', Dell and 'Unknown'. Notebook 15 was set to 1024 so it seemed like it should be ok. I applied the dialog settings and rebooted. No dice. I did that again, this time physically changing the resolution, reboot, no change.

I should note that at no time during the 2nd monitor procedure, even the first time I did it, did the Notebook 15 monitor in screen resolutions show that it was in the off state.

At some point I started getting a higher available resolution on the Notebook 15 list. The Dell monitor always showed a dozen or so options.

Sometimes the display would be on the Dell monitor only and the Pangolin screen was just an empty desktop 'below' the Dell screen as the mouse moves.

Changes never stuck to the 'Unknowm' monitor. It was always 'off' when I got back to the resolution dialog box. Is this the ghost monitor?

Regardless of what resolutions I set any of the three monitors to, when I booted up Pangolin without the 2nd monitor, the screen went black when I logged back in.

Now that I know my forum password (couldn't remember it at work today) I'll be here on the boards as I have another go at it on Friday. If the problem doesn't clear tomorrow I'll just bring the Dell monitor home for the weekend to continue working with it.

---

### Post by Lee_Machine on 2008-12-12
Are you pushing the Fn-f2 button to cycle between LCD screens?

---

### Post by earrame on 2008-12-12
Nope. Not familiar with that.

---

### Post by thomasaaron on 2008-12-12
Yes, the unknown monitor is the ghost monitor. 

Let's try this...

Connect the Dell monitor and turn on the computer.

Try setting your notebook monitor to whatever resolution you can.
Then turn the resolution for the unknown monitor off.
Then turn the resolution for the Dell monitor off.

At this point, you should have a display only on your Notebook monitor. 

Now, disconnect the Dell monitor.

Go to a terminal and run these commands:

#Pay attention to capitalization...
> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

#Use ALL default answers on this one
> sudo dpkg-reconfigure xserver-xorg 

Now, Turn the computer off. Reboot.

If that doesn't work, give me a call at support... Use ext. 603.

---

### Post by earrame on 2008-12-12
Tom, a funny thing happened while awaiting your email.

In the various attempts yesterday and today I had never done this exactly;

With the Pangolin up and running with the Dell monitor;

1) I set the new resolution that appeared yesterday; 1280 x 800 (16:10).

2) The monitor flicked off and on and the display was only using about 75 percent of the screen. The bottom and right portions were just filled with some kind of noise; thin B&W lines.

3) I unplugged the Dell to prepare for another reboot attempt. (I didn't lose the Pangolin display)

4) I decided I didn't want to reboot with the messed up display so I set it back to 1024. Screen flicked off and back on and it was back to normal.

5) I got curiuos about the display flicking off and on during those resolutiuon changes without the Dell. I shut down and cold booted without the Dell.

The laptop LCD is back without it's Dell crutch!

I got your email but I have not yet run the install instructions.

Now we're back to simply getting the resolution corrected following the upgrade to Ibis.[-o<

The new 1280 is still present in the list but I'm not touching anything display related until you tell me to. :-D

---

### Post by thomasaaron on 2008-12-12
OK, good. What's happening now, is that you're LCD is actually taking the resolution of the ghost monitor.

So, go to System > Prefs > Screen Resolution and uncheck the "Mirror Screens" box, and turn the resolution of the *ghost monior* off.

Now, you should be able to click the notebook LCD square and set the resolution correctly. If not, the option should be there after rebooting.

---

### Post by earrame on 2008-12-12
Ok, Mirror Screens is unchecked and the ghost monitor is off.

The 1280 x 800 is the only additional resolution that is available. (after reboot too)

When I set it I get this:

[IMG]http://i26.photobucket.com/albums/c134/earrame/linux/PC120078.jpg[/IMG]

---

### Post by thomasaaron on 2008-12-12
OK, then, let's try to run those commands that we never got too...

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get --purge remove xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg
sudo reboot -h now

---

### Post by thomasaaron on 2008-12-12
I'm not sure, but you may need to uncheck the "Mirror Screens" box again after all of that.

But the point of that exercise was to get rid of any unwanted configurations that may have been caused by the previous testing and Dell monitor and get everything back to factory specs.

---

### Post by earrame on 2008-12-12
I'll do that. It will have to wait until I am home. If I can, I'll try to do it as soon as I get home. I think you are two hours behind me so I should be able to post results before the end of your work day. If not, the resuls will be here sometime over the weekend.

Thanks for your help!

---

### Post by earrame on 2008-12-12
Done. The display is working perfectly at the correct resolution.

Thanks for your help!

---

