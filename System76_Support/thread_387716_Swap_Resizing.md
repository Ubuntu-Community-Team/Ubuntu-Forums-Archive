---
title: "Swap Resizing?"
date: 2007-03-18
forum: System76 Support
---

### Post by slack42 on 2007-03-18
Hi , I got my Gazelle value laptop about a month ago , it's a great laptop but I've noticed that the swap file is pretty big. It shows as 3.7 Gigs in the System monitor utilitie . I got links from system76 support on how to resize but I didn't find it to helpful. And I've run into other things that I have questions about. 

With some searching I found that I could use fdisk to show me the partition table so when I do fdisk -l I get this :

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9243    74242871   83  Linux
/dev/hda2            9243        9730     3907872+   5  Extended
/dev/hda5            9243        9730     3907872   83  Linux

It doesn't say witch one is the swap partition but I used a knoppix cd and qtparted and it told me that hda5 is the swap partition. But I'm confused about why I show two partitions , had2 and had5. They have the same start and end points so are they the same thing? I've created partitions before but I really don't know that much about this and don't know if this is normal. 

So what I'm wondering is should I use the knoppix cd to do this or the fdisk utilitie? Also witch one will I resize? The hda2 or the hda5 one? And how will that affect the other one? And I also want to know is there anything that I have to do or any commands I have to run so that the OS will recognize the new swap partition?

Also my suspend doesn't work and so I'm wondering if this is related to the way my swap partition is set up. I'd like to get the swap partition resized before I try and figure that out thought.


Thanks

---

### Post by crichell on 2007-03-19
Hi slack42

hda5 is swap as you've determined.  another way to figure out where swap is is the command:

```
swapon -s
```

> So what I'm wondering is should I use the knoppix cd to do this or the fdisk utilitie?

The knoppix cd is probably easier (you can use an Ubuntu LiveCD too.)  You can use gparted to adjust partitions with the knoppix or Ubuntu cd.

> Also witch one will I resize? The hda2 or the hda5 one?

hda5 - make it smaller and then make hda1 larger.  You don't want to make it too much smaller or Suspend won't work at al

l (we'll get to that part).  Maybe 2 GB - at least the amount of RAM you have if not a little more.

> And I also want to know is there anything that I have to do or any commands I have to run so that the OS will recognize the new swap partition?

Nope - just run swapon -s to make sure swap is recognized as hda5 once you're done.

> Also my suspend doesn't work and so I'm wondering if this is related to the way my swap partition is set up.

We've found that S1 Suspend works better on the Gazelle Value.  It doesn't save as much energy but it's much more reliable.

Make a backup of your original acpi-support file

```
sudo cp /etc/default/acpi-support /etc/default/acpi-support_backup
```

Open the file to edit:

```
sudo gedit /etc/default/acpi-support
```

Change this line:

```
# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem
```

TO

```
# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=standby
```

Let me know if you have any trouble.  We're working on supporting full S3 suspend.

---

### Post by slack42 on 2007-03-19
Hi,

      I did all the things you said and it sort of worked. I booted into knoppix and I used qtparted to resize the had5 partition but I couldn't add the left over space to hda1. When I right clicked on hda1 the only options it gave me where for format or properties. I resized hda5 to 1 Gig because that is the amount of ram I have. When I did it it only let me resize it one way so that I ended up with about 2.4 Gigs after the swap partition. So I tried moving the swap to the end of the drive and it seemed to work but I still couldn't resize hda1. Should I delete hda2? Here is the new output of fdisk -l 


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9243    74242871   83  Linux
/dev/hda2            9243        9730     3907872+   5  Extended
/dev/hda5            9599        9729     1052257+  82  Linux swap / Solaris


I have the swap file at the size I want but I don't know how to add the extra space to hda1. I don't mind using the command line if you think it would be better to do it that way . And I was also wondering is it something that I should do from a live CD? Because when I used qtparted it said to make sure the partition was unmounted before I continued.

I changed the line in acpi-support that you said and suspend seems to work now. If I select suspend from the shutdown options it will go into suspend and to wake it up I have to hit the power button. Hitting any other key won't work but that's okay because at least it works. And when I close the lid the screen shuts off but I don't know if it goes into suspend because when I open it again I get a active desktop right away, I don't have to hit any buttons. In power management I selected suspend when I close the lid so I don't know if this is the way it's suppose to work . This is my first laptop and I'm not familier as to how it's suppose to work. 

Since I've made the changes I've found that the cancel touch pad button now doesn't work. I really liked that feature, can I just use the system76 driver utilitie to get it back?


Thanks

---

### Post by crichell on 2007-03-20
Sorry - I should have been clearer.  hda2 is an extended Linux partition containing your swap partition.  Decrease hda2 to the same size as your swap partition.  You will them be able to increase the size of hda1 since it won't have another partition bumped up against it.

> And when I close the lid the screen shuts off but I don't know if it goes into suspend because when I open it again I get a active desktop right away, I don't have to hit any buttons.

In Power Manager check that closing the lib puts the machine into suspend on both Battery and while plugged in.  You should be prompted for a password when coming out of suspend.

> Since I've made the changes I've found that the cancel touch pad button now doesn't work. I really liked that feature, can I just use the system76 driver utilitie to get it back?

Go to System > Preferences > Touchpad

If you receive an error that states "GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics" we need to add SHMConfig to your xorg.conf file.

Backup your current xorg.conf file (you can copy and paste these commands into your terminal)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Open your current xorg.conf for editing

```
sudo gedit /etc/X11/xorg.conf
```

Change the following lines to match mine (We're adding the last "SHMConfig" option line)

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"1"
EndSection

Save, close, and restart X or reboot.  You can restart X by pressing CNTRL + ALT + Backspace

---

### Post by slack42 on 2007-03-20
Success!

I booted into knoppix and resized hda2 but it wouldn't let me resize hda1 for some reason. So I booted into a Ubuntu CD and used gparted and that let me resize had1 . It took three tries for some reason , the first time it would say that there was some king of error and then it wouldn't do it. So I tried it one last time and for some reason it took and I now have it the way I want it. 

I also now have suspend working. I had missed the other tab in power management , sorry I should have saw that. And I didn't have to make the changes that you said to xorg because it was already set up that way . When I first booted up the cancel touch pad button was working. But I took a look at xorg just to see and then after that it wasn't working again. So I rebooted and now it's working again , it's kind of weird but at least it's working now. 

Seeing as how you did such a great job of answering my questions I was wondering if I could ask one more? I've had a on and off sound problem , sometimes it doesn't work and then it will again. The last time it stopped working I reloaded the drivers using the system76 driver utilitie and it started working again and has only stopped once since. That time I was on battery power so I don't know if that would have anything to do with it. The issue isn't really that it's not working but that I have to have it turned up all the way with both the FN + F8 button and in the sound panel to be able to hear sound. It's not that it's really really low at full level but I'm not sure it is normal to have to have them turned up all the way to be able to hear. So I was just wondering if there is a setting somewhere that I can make adjustments to?


Thanks for all the help, it's great that my issues are getting resolved and I'm also learning a few things .

---

### Post by crichell on 2007-03-22
My guess is that one of the Volume Control toggle buttons isn't active.  Open up volume control (right click on speaker > Open Volume Control).  Click Edit > Preferences.

Make sure all the boxes are ticked on.  You should have PCM and Master.  FN + F8 increases Master and FN + F7 decreases Master.  Increase PCM to it's highest level and you can then use the hot keys for increase/decrease with a broad range of volume.  If there is any distortion when Master is increased all of the way lower PCM slightly until the distortion is gone.

---

### Post by slack42 on 2007-03-22
That helped a bit. My PCM was set at about 3/4 percent. Now I get a little more volume than I had before. I think the volume is now at about what I would expect for laptop speakers.


Thanks again for all the help , I really appreciate it.

---

### Post by slack42 on 2007-03-31
UPDATE

My suspend is still working but it only seems to work once. That is it will work the first time I close the lid. But if I close the lid any time after that it will not go into suspend. Sometimes when I wake the laptop up I will get the log in prompt but the key board won't work. This seems to happen when I put the laptop in suspend with the suspend button. So no matter what I do I can't sign in. My only option is I have to hold the power button until the system shuts down. Another little oddity is that after I wake the computer up the first time the buttons at the top of the keyboard don't work. And restarting X doesn't get them back. I have to do a complete reboot to get everything working again. 

I try not to use the buttons to go into suspend or hibernate because I'm afraid I will have to do the hard shutdown. I tried changing it back to ACPI_SLEEP_MODE=mem in /etc/default/acpi-support but then suspend didn't work at all. So for now I am just not using the buttons to suspend or hibernate the computer . But as I said it will only work once. So for now I am just not using the buttons to suspend or hibernate the computer for now.

---

