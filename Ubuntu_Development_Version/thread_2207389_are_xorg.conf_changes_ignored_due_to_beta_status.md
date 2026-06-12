---
title: "are xorg.conf changes ignored due to beta status?"
date: 2014-02-23
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-23
I installed the nvidia driver and absolutely nothing has any effect on a reboot. 
I make changes no change occurs.

I make changes through nvidia- settings saving to xorg, or I make manual changes usng gedit.
I can not do a thing with it.
All changes are transient to the current session only, a reboot loads something but not what is in xorg.conf

Where does it get the load info for video configuration?

---

### Post by QDR06VV9 on 2014-02-23
> **sdowney717 said:**
> I installed the nvidia driver and absolutely nothing has any effect on a reboot. 
I make changes no change occurs.

I make changes through nvidia- settings saving to xorg, or I make manual changes usngvlc ppaif gedit.
I can not do a thing with it.
All changes are transient to the current session only, a reboot loads something but not what is in xorg.conf

Where does it get the load info for video configuration?
Are you still trying to set your monitors to your specs?
If so, have you tried just switching the conections on your video card?

---

### Post by sdowney717 on 2014-02-23
There is no other way to connect what I have.
I have a monitor Samsung LCD connected with DVI
I have an svideo going to TV

the TV always comes up as the primary display and always to the right of the monitor.

It worked fine in 12.04, so I think either a bug or is deliberate due to beta status.

---

### Post by muktupavels on 2014-02-23
Have you tried to use System Settings -> Displays to configure your monitors?

---

### Post by QDR06VV9 on 2014-02-23
> **sdowney717 said:**
> There is no other way to connect what I have.
I have a monitor Samsung LCD connected with DVI
I have an svideo going to TV

the TV always comes up as the primary display and always to the right of the monitor.

It worked fine in 12.04, so I think either a bug or is deliberate due to beta status.
Scott try [here]("https://help.ubuntu.com/community/NvidiaTVOut")

---

### Post by sdowney717 on 2014-02-23
> **albertsmuktupavels said:**
> Have you tried to use System Settings -> Displays to configure your monitors?

It may be where it gets its orientation, there is nothing there to configure as far as left, right, or primary.

The big problem, is after a boot, you get the TV as the primary display, which is then difficult to work with. the TV is only good for showing video, not text and windows.
Then I have to open nvidia-settings and set up the displays again.

---

### Post by muktupavels on 2014-02-23
> **sdowney717 said:**
> It may be where it gets its orientation, there is nothing there to configure as far as left, right, or primary.

The big problem, is after a boot, you get the TV as the primary display, which is then difficult to work with. the TV is only good for showing video, not text and windows.
Then I have to open nvidia-settings and set up the displays again.

You can set up primary monitor and monitor order there also. 

1) Click on "Unknown Display" and move it to place where you want it to appear.
2) Black rectangle means primary monitor. If you need to change it, drag it to display you want to make primary.
3) Click Apply.

---

### Post by sdowney717 on 2014-02-23
Uh,

You fixed it!:p
Drag, apply, reboot.
Monitor is on left as primary
TV on right as secondary.

Nvidia-settings is over ridden by this Ubuntu Display program.

Can that Display program set the 'primary' monitor?
I might want to make TV to left and set LCD as primary.
It showed that config when I first looked at it, and the TV was the primary monitor but nowhere did I notice a setting for it there.

OR, does it just set whatever is to left as primary?

---

### Post by muktupavels on 2014-02-23
1) I think you can delete your xorg.conf file. But before doing that better make backup of that file.
2) Don't use nvidia-settings to configure your monitors if you only want set up monitor order and/or set primary monitor.
3) When you log in settings are loaded from ~/.config/monitors.xml. Nvidia settings does not write changes to that file - that is reason why on reboot your changes where lost.
4) Yes Display program can set primary monitor. Primary monitor is that monitor which have black rectangle on it with time. Just move that black rectangle to monitor you want to make primary.
5) If you want unity-greeter to use same configuration than copy ~/.config/monitors.xml to /var/lib/lightdm/.config/monitors.xml. But remember that currently unity-greeter does not support primary monitor. Login box will always appear on left monitor.

---

### Post by sdowney717 on 2014-02-24
thanks for this very good information.

" But remember that currently unity-greeter does not support primary monitor. Login box will always appear on left monitor."

Will it support it?

Currently, my LCD monitor is in the room on the right, and TV on the left.
Ideally to make visual sense with that, primary monitor and login greeter ought to be on the right monitor.
Also dragging video windows to the TV makes sense to drag to left, if that TV is to left of the primary monitor.

In 12.04, nvidia-settings did determine the monitor, primary and left or right, is this something new or when did this change?
I came from 12.04 into 14.04, so I had no idea.

---

### Post by muktupavels on 2014-02-27
> **sdowney717 said:**
> thanks for this very good information.

" But remember that currently unity-greeter does not support primary monitor. Login box will always appear on left monitor."

Will it support it?

Yes, fix for it is already merged. So probably next unity-greeter version will have primary monitor support.

---

