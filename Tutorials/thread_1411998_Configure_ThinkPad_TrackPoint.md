---
title: "Configure ThinkPad TrackPoint"
date: 2010-02-20
forum: Tutorials
---

### Post by mastertimothy on 2010-02-20
Hey guys

I've got a ThinkPad W700 and I've been using Karmic on it since its  release.  I finally got around to really tweaking the TrackPoint's settings.

[ThinkWiki]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint") describes how to configure TrackPoint using a variety of methods.   However the article is a little out of date, incomplete, and confusing.

**1.  Introduction**

The TrackPoint is the red nub in the middle of the keyboard and the  three buttons right below the keyboard.  By default Press-To-Select, the process of pushing down on the TrackPoint to click, is turned off.  Also, by default the TrackPoint's middle click performs the Paste  function.

In this tutorial I will describe how to adjust these settings activate the middle click scroll and Press-To-Select similar to Windows.

**2.  Configure TrackPoint Middle Mouse Scroll**

I wanted to configure the middle click on the TrackPoint to scroll just  like in Windows so I used the following commands to achieve it.

**2.1:   Find the ID number for the TrackPoint**

The first step is to find the xinput id number for the IBM TrackPoint.  Run the following command.

```
 xinput list
```You should receive all the available devices for xinput.  One of the devices should say:

```
"TPPS/2 IBM TrackPoint"    id=9    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
```Or something very similar.

**2.2:  TrackPoint Middle Mouse Scroll**

Next run the following commands to enable the middle mouse scroll.

```
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation" 8 1;
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Button" 8 2;
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Timeout" 16 200;
```Now you should be able to middle scroll by pressing the middle mouse button for the TrackPoint and moving the TrackPoint up and down.

**3.  Enable Press-To-Select **

Press-To-Select is the process on pushing down on the TrackPoint to click on objects.

In the directory "/sys/devices/platform/i8042/serio1/serio2/"  There is a  file called "press-to-select".  That is the file we will be focusing on.

**3.1:  Change directory**

Open up the terminal and change the directory to "/sys/devices/platform/i8042/serio1/serio2/"

```
 cd /sys/devices/platform/i8042/serio1/serio2/
```**3.2:  Change Permissions of "press-to-select"**

Change the permissions of the "pres-to-select" file to allow others modify the file.

```
sudo chmod o=rw ./press_to_select
```**3.3:  Turn on/off Press-To-Select**

To turn on/off Press-To-Select is just a matter of adding a 1 or 0 to the file.

~Turn Press-To-Select On~
```
 echo -n 1 >  /sys/devices/platform/i8042/serio1/serio2/press_to_select;
```~Turn Press-To-Select Off~
```
 echo -n 0 >  /sys/devices/platform/i8042/serio1/serio2/press_to_select;
```Now you should be able to click by pushing straight down slightly on the TrackPoint.

Just thought I'd share.  :)

I'm not sure if this these methods work on every single ThinkPad under  every circumstance.  So if anyone has a better method of configuring the  TrackPoint, let me know.

---

### Post by jpeddicord on 2010-02-20
Approved; thank you for your contribution to Tutorials & Tips!

---

### Post by immeëmosol on 2010-03-10
FYI:
On the Thinkpad R61i(7650-D7G) the same can be done
when serio2/ is not in the pathname .

---

### Post by tgalati4 on 2010-03-10
Middle mouse button scrolling works on a thinkpad T43p.

Haven't tried press-to-select.

---

### Post by sammy0131 on 2010-09-25
It worked beautifully for my T60 as well (scrolling part). But when I restart the computer, the setting is also reset and I needed to rewrite the command. How can I save the settings?

Thanks,

---

### Post by sammy0131 on 2010-09-26
I realized it preserved on IE on Windows but not on Firefox on Ubuntu. Any idea??

---

### Post by smihaylov on 2011-10-13
Thank you for the tutorial, it works perfectly on T61, but "press-to-select" doesn't work on my Thinkpad Edge E420.
There is file:

```
/sys/devices/platform/i8042/serio1/serio2/press_to_select
```

but when I change it to "1" nothing happened. Any ideas what is wrong? Is it possible Edge E420 to not support this feature?

I have tested it with no success on both Ubuntu 11.04 and 11.10 beta2 liveCD.

Thank you.

---

