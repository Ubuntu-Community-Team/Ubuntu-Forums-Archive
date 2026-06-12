---
title: "Screen Brightness Levels"
date: 2010-01-28
forum: System76 Support
---

### Post by mcallenSchmee on 2010-01-28
When I use the function buttons the screen brightness goes up two levels at a time. There are an odd number of brightness levels, so if I want the brightness in between two levels I have to turn the brightness to the max or min then to the level I want it.

I can get it to go up one level at a time with the gnome brightness applet but the computer slows to a crawl when I use it for some reason.

Is there any way to adjust how much the screen brightness increases or decreases when using the brightness function buttons? This is a minor issue but it is irritating. I have a Gazelle Ultra (gazu1).

---

### Post by jdb on 2010-01-28
> **mcallenSchmee said:**
> When I use the function buttons the screen brightness goes up two levels at a time. There are an odd number of brightness levels, so if I want the brightness in between two levels I have to turn the brightness to the max or min then to the level I want it.

I can get it to go up one level at a time with the gnome brightness applet but the computer slows to a crawl when I use it for some reason.

Is there any way to adjust how much the screen brightness increases or decreases when using the brightness function buttons? This is a minor issue but it is irritating. I have a Gazelle Ultra (gazu1).

There was a period of a few kernels when the brightness keys on my Daru2 didn't work.

I wrote this script to get me by:

```
#bright                 set backlighting

if [ $# -ne 1 ] || [ $1 -lt 1 ] || [ $1 -gt 8 ]
  then
  echo "syntax: bright number-from-1-to-8"
  echo -n "brightness = "
  cat /sys/class/backlight/acpi_video0/brightness
  exit 1
  fi

sudo bash << ____END_FILE
echo $1 > /sys/class/backlight/acpi_video0/brightness
____END_FILE

```


jdb

---

### Post by thomasaaron on 2010-01-28
I'm imaging a Gazelle right now to test that. If memory serves, though, it's a know bug and we don't really have a way around it yet.

---

### Post by mcallenSchmee on 2010-01-28
Yes, I think [this]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/457530") is the bug I am affected by.

Based on comment #2 on [ this page]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/453748") the hardware may be adjusting the brightness, then gnome-power manager adjusts it again. When gnome-power-manager is not running the brightness works correctly (although the notification does not pop up showing the brightness level).

So is there a way to stop gnome-power-manager or the hardware from adjusting brightness?

[This]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/261450") bug also affects me.

---

### Post by jdb on 2010-01-28
> **mcallenSchmee said:**
> Yes, I think [this]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/457530") is the bug I am affected by.

Based on comment #2 on [ this page]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/453748") the hardware may be adjusting the brightness, then gnome-power manager adjusts it again. When gnome-power-manager is not running the brightness works correctly (although the notification does not pop up showing the brightness level).

So is there a way to stop gnome-power-manager or the hardware from adjusting brightness?

[This]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/261450") bug also affects me.

On the upper left hand menu bar:

System > Preferences > Power Management > On Battery Power

uncheck: "Reduce backlight brightness" & "Dim display when idle"

jdb

---

### Post by thomasaaron on 2010-01-28
Yep. That's the bug. I can reproduce it on our shop machine.

---

### Post by mcallenSchmee on 2010-01-28
> **jdb said:**
> On the upper left hand menu bar:

System > Preferences > Power Management > On Battery Power

uncheck: "Reduce backlight brightness" & "Dim display when idle"

jdb

That doesn't solve my problem. When I use the brightness buttons the hardware increases the brightness, then gnome power manager detects the button press and increases the brighness as well, not knowing that it has already been handled by the hardware. That's the way it seems anyway.

---

### Post by thomasaaron on 2010-01-29
Well, there's a way we can test that theory, I think.

If we disable the script that controls brightness for gnome-power-manager, that should leave just the hardware to control it...

In a terminal, run...

gconf-editor

Then in gconf-editor, go to "/apps/gnome-power-manager/backlight", and uncheck "enable".

You may or may not need to reboot after that. But check to see if the function keys do anything.

Also, once you have that disabled, there is a program called xbacklight that we may want to try. I've not tested with it yet, but I can depending on the outcome of the above test.

Here's some more info if you want to have a look...
[https://wiki.ubuntu.com/LaptopTestingTeam/AsusUL30A](https://wiki.ubuntu.com/LaptopTestingTeam/AsusUL30A)

---

### Post by mcallenSchmee on 2010-01-29
> go to "/apps/gnome-power-manager/backlight", and uncheck "enable".
I believe that just sets whether or not the brightness changes when unplugging or plugging in the power cord. I tried it and it didn't work.

xbacklight can control the backlight correctly. I set up keyboard shortcuts to change the brightness using the commands ```
xbacklight -dec 14
``` and ```
xbacklight -inc 15
``` I got these values from /proc/acpi/video/VGA/LCD/brightness. This works, although I'd prefer that it worked properly with the brightness keys and the notification popup.

**Edit:**
I accidentally discovered that if you use System>preferences>Keyboard Shortcuts to set up keyboard shortcuts using the brightness keys (they don't have to actually do anything), the brightness goes up the correct amount. The notification popup doesn't show with this method either though.

---

### Post by thomasaaron on 2010-02-01
Cool.

That sounds like a fix we can at least get into the System76 Driver. The pop-up is nice, but if I had to choose between more adjustability and the pop-up, I'd go with the adjustability.

There may be a way to get the popup to work too.

---

### Post by mcallenSchmee on 2010-02-01
I've looked into it a little more and I think the way to do it properly might be with a hal fdi file. Adding the information for the gazelle to  /usr/share/hal/fdi/information/10freedesktop/10-laptop-panel.hardware.fdi might be the solution.
```
<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <!-- Some laptops have software controllable backlights and will provide
       notifications on keypresses, but will also change the brightness
       directly in firmware. If software changes the value in response to
       a press, there's a risk that a further event will be generated and
       a feedback loop occur. brightness_in_hardware indicates to clients
       that they should not act in response to keypress notifications. -->
  <device>
    <match key="info.category" string="laptop_panel">
      <!-- For Asus EeePC -->
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor"
          string="ASUSTeK Computer INC.">
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="701">
          <merge key="laptop_panel.brightness_in_hardware" type="bool">true</merge>
        </match>
      </match>
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" string="TOSHIBA">
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="SATELLITE M100">
          <merge key="laptop_panel.brightness_in_hardware" type="bool">true</merge>
        </match>
      </match>
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" string="Hewlett-Packard">
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains_outof="2510p;2710p;nc2400">
          <merge key="laptop_panel.brightness_in_hardware" type="bool">true</merge>
        </match>
	<match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains_outof="4410s;4415s;4416s;Compaq 5X5">
	  <!-- needed since the acpi video module reports it handle the events, but it don't work on this machines-->
          <merge key="laptop_panel.brightness_in_hardware" type="bool">false</merge>
        </match>
      </match>

      <match key="linux.sysfs_path" suffix="/backlight/thinkpad_screen">
        <merge key="laptop_panel.brightness_in_hardware" type="bool">true</merge>
      </match>

    </match>
    <match key="linux.sysfs_path" contains="/sys/devices/virtual/backlight/acpi_video">
      <merge key="laptop_panel.brightness_in_hardware" type="bool">false</merge>
    </match>
  </device>
</deviceinfo>
```

---

### Post by gwachtel on 2010-02-15
This bug's been bugging me since I bought a Lenovo Ideapad s12. Thanks to the last post I was able to solve it: just put these lines into 
/etc/hal/fdi/policy/preferences.fdi
```

  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/computer_backlight>
    <merge key="laptop_panel.brightness_in_hardware" type="bool">true</merge>
    </match>
  </device>

```
Make sure they are between the <deviceinfo> tags.

---

### Post by mcallenSchmee on 2010-02-15
Unfortunately that doesn't work with the Gazelle, but I'm glad it helped you :).

---

