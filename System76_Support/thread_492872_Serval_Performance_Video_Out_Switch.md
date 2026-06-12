---
title: "Serval Performance Video Out Switch"
date: 2007-07-05
forum: System76 Support
---

### Post by hartt on 2007-07-05
Hi everyone,

Anyone out there with a Serval Performance found a way around the video switching issue? Meaning that when you hit Fn-F3 the computer doesn't cycle through an attached projector.

Would be nice if I could do this on the fly as well.

Tim

---

### Post by thomasaaron on 2007-07-05
I've been working on this one. 
As far as I can tell, the Fn-F3 combination does not seem to be generating a key-code.
We've managed to fix it on some computers, but not the Serval yet.
Here is a work-around that should work for you until we get it all wrapped up.

Open a text editor: gedit
Paste the following code in (without the code tags).
Save it to your Desktop as video-switch.sh
Make it executable: sudo chmod a+x ~/Desktop/video-switch.sh

Now you can double click the text file's icon, and then click run, to cycle through the vga out options ( LCD only, LCD + External Projector/Monitor, Ext. Monitor Only).

You could also create a launcher on your upper panel to run it.

```
#!/bin/sh
#filename: video-switch.sh

switch=`cat /proc/acpi/asus/disp`

switchChange=`expr $switch + 1`

if [ $switchChange -gt 3 ]; then
switchChange=1
fi

echo $switchChange > /proc/acpi/asus/disp

exit 0
```

---

### Post by hartt on 2007-07-05
That script didn't work. Couldn't find that program in that folder. Could it be somehwere else on the Serval?

---

### Post by thomasaaron on 2007-07-05
Yep. You're right. It doesn't exist.
It's because it has the nVidia graphics, I think.
That file exists on the machines with Intel Integrated graphics.

Still working on the problem.

Best,
Tom

---

### Post by sgtron on 2007-07-07
This came up before.  Carl told me to use Yanc.  You can find it here: [http://www.ygriega.de/index.php?id=2&detail=1]("http://www.ygriega.de/index.php?id=2&detail=1")

It worked fine for me with the S-video, but not with vga out.  Fn-F3 still didn't work, but at least you can use the yanc to get the desired results.

---

### Post by jvslice on 2007-07-18
I am having the same problems with a Pangolin Value (panv2)  Fn F3 does not work and the script does not work when I run the script I get "video-switch.sh command not found" 

Renamed file to video_switch.sh just to check, but no luck

Here is the output of my shell if that helps:

john@green:~$ cd Desktop
john@green:~/Desktop$ ls
video_switch.sh
john@green:~/Desktop$ sudo video_switch.sh
sudo: video_switch.sh: command not found
john@green:~/Desktop$ file video_switch.sh
video_switch.sh: Bourne shell script text executable
john@green:~/Desktop$ cd /proc/acpi/asus/
john@green:/proc/acpi/asus$ ls
brn  disp  info  lcd  mled  wled
john@green:/proc/acpi/asus$ file disp
disp: empty
john@green:/proc/acpi/asus$

---

### Post by Yhetti on 2007-07-25
> **jvslice said:**
> I am having the same problems with a Pangolin Value (panv2)  Fn F3 does not work and the script does not work when I run the script I get "video-switch.sh command not found" 

Renamed file to video_switch.sh just to check, but no luck

Here is the output of my shell if that helps:

john@green:~$ cd Desktop
john@green:~/Desktop$ ls
video_switch.sh
john@green:~/Desktop$ sudo video_switch.sh
sudo: video_switch.sh: command not found
john@green:~/Desktop$ file video_switch.sh
video_switch.sh: Bourne shell script text executable
john@green:~/Desktop$ cd /proc/acpi/asus/
john@green:/proc/acpi/asus$ ls
brn  disp  info  lcd  mled  wled
john@green:/proc/acpi/asus$ file disp
disp: empty
john@green:/proc/acpi/asus$

Two things to look at. 

First, since "." is (rightly) never included in the path, you would have to do 

sudo ./video_switch           OR           sudo bash video_switch

To actually run it.  Second, /proc/acpi/asus/disp is a special file, so most normal file operations won't work on it.  For instance:

wes@skeletor:/proc/acpi/processor/CPU0$ ls
info  limit  power  throttling
wes@skeletor:/proc/acpi/processor/CPU0$ file info 
info: empty
wes@skeletor:/proc/acpi/processor/CPU0$ cat info 
processor id:            0
acpi id:                 1
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no

---

### Post by jvslice on 2007-07-26
Tried the above after hooking up an external monitor to my laptop.

When using "./video_switch.sh" I no longer get "command not found" but the external monitor still does not work.

I did a cat /proc/acpi/asus/disp after each try and the file alway displays "0"

Any ideas, I will also try "Yanc" when I get home tonight to see if that works.

---

### Post by thomasaaron on 2007-07-26
Here's a workaround:

From a terminal, enter:
sudo gedit /etc/X11/xorg.conf

In the resulting file, find the "Screen Section." Scroll down to the bottom of the screen section (it will say "End of section") and enter the following lines just before the "End of Section" line:
Option        "TwinView" "true"
Option        "TwinViewOrientation" "Clone"

Save the file, and then click Ctrl-Alt-Backspace.

Now, whenever you want to see both your LCD and the projector image:
Turn on the projector and plug it into the vga port.
Hit CTRL-ALT-Backspace to restart X.
Log in.

You can further adjust the resolution displayed by the projector by doing the following:

From a terminal, type: nvidia-settings
In the resulting window, select the resolution for the monitor and click "Apply"

---

### Post by jvslice on 2007-07-26
I guess I should not have hijacked this thread, since the thread started with a Serval laptop but I was having the same problem on my Pangolin Value (panv2) laptop which I believe does not have a Nvidia graphics card.

Because my laptop has an Intel graphics card ???? I do not think I can use "nvidia-settings

Sorry for any confusion.

---

### Post by thomasaaron on 2007-07-26
> guess I should not have hijacked this thread, since the thread started with a Serval laptop but I was having the same problem on my Pangolin Value (panv2) laptop which I believe does not have a Nvidia graphics card.

Because my laptop has an Intel graphics card ???? I do not think I can use "nvidia-settings

Sorry for any confusion.

The second post down in this thread should work for you.

---

### Post by sgtron on 2007-07-31
Update to my previous reply about using YANC.  We can now use ```
 gksudo nvidia-settings
``` and configure our tv-out directly.  On my tv using my Serval as a media player I can get the screen pretty close to perfect.  But not 100% more like 96.5%.

---

