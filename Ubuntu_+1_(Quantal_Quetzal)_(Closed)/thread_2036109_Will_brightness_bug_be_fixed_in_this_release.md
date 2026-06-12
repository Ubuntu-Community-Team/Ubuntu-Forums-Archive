---
title: "Will brightness bug be fixed in this release?"
date: 2012-08-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Ravi5kumar on 2012-08-01
I am curious to know if the upcoming Ubuntu 12.10 will fix that issue! In Ubuntu 12.04 the brightness setting is not saved. After reboot brightness is set to maximum. I don't want every time to decrease my brightness! So will it be fixed:confused:?

---

### Post by effenberg0x0 on 2012-08-01
> **Ravi5kumar said:**
> I am curious to know if the upcoming Ubuntu 12.10 will fix that issue! In Ubuntu 12.04 the brightness setting is not saved. After reboot brightness is set to maximum. I don't want every time to decrease my brightness! So will it be fixed:confused:?

So am I. I think it won't be fixed for 12.10. I have the same problem (ASUS K43) but decided to investigate it myself some months ago. I'm working on a simple solution using only two scripts that are loaded in specific situations (boot, shutdown, suspend, resume, etc): load-brightness.sh and save-brightness.sh. 

The script approach is obvious, of course. The origin of the problem resides in /sys/class/backlight. Many affected machines have (at least) two devices there, with different scales and levels for actual_brigtness, max_brightness, current_brightness. You can echo "value" | sudo tee -a path/backlight_file to these files for test and also read them to see the levels as you use gnome-control-center/"Brightness and Lock" slider, suspend, resume, etc. Doing that, one can easily see that g-c-c/"Brightness and Lock" slider is controlling one of the devices only, but Fn+Keyboard Backlight Hotkeys controls the other. The machine always starts/wakes using the second (not controlled by g-c-c). This is definitely where the confusion happens - it's easily testable. 

So, modules loading, hardware detection and/or module blacklisting aside, if there's more than one device/scale, for whatever reason, it should be possible (or mandatory actually) to normalize both scales, whatever they are, and keep them in sync at all times. That was my initial idea. It's totally userland and not beautiful.

This is not related to GPU/APU/CPU vendor/model/type or an specific brand of laptop (although its very frequent in ASUS hardware). Most workarounds rely on non-portable tweaks to content in /etc/acpi/events/*.sh and using "acpi_osi=linux" and "acpi_backlight=vendor" args on boot command line via /etc/default/grub && sudo update-grub (which forces a acpi device in /sys/class/backlight). These two switches seem to fix the problem for most users (apparently, according to my limited research), but I'm not convinced. You should give it a try. It does not work for a percentage of users (including me). And I believe it causes an impact in other stuff, including power consumption. 

I have done a lot of research about it a while ago, when I started thinking about it, and found no complete analysis of the problem, any thorough description or suggested fix (besides the aforementioned workarounds). Due to time constrains (aka life sux), I had to halt this for a couple months. Maybe someone has already worked on a complete solution by now anyway.

Regards,
Effenberg

---

### Post by jerrylamos on 2012-08-01
Bang!  Max Bright!  Every Time! on my Acer 5253 wide screen notebook. 

Ubuntu wants to burn out my screen.  Right now.

Solution: external monitor.  QQ can't set the brightness on the external.  Hardly a portable notebook at that point.

Ubuntu's development emphasis is on "eye candy" and "tablet wannabe" and not on such pedestrian things as usability.  

Choices.  I can run 12.04 LTS or any number of other linux if I wish, I'm running QQ to find bugs.  Sometimes development jumps right on a bug, sometimes they ignore them.  ?.

Well, not a showstopper, just an anklebiter.  I boot a lot so the BRIGHT SCREEN comes up a lot - now to reboot to try 3.5.0-7.

Jerry

---

### Post by effenberg0x0 on 2012-08-01
> **jerrylamos said:**
> Bang!  Max Bright!  Every Time! on my Acer 5253 wide screen notebook. 

Ubuntu wants to burn out my screen.  Right now.

Solution: external monitor.  QQ can't set the brightness on the external.  Hardly a portable notebook at that point.

Ubuntu's development emphasis is on "eye candy" and "tablet wannabe" and not on such pedestrian things as usability.  

Choices.  I can run 12.04 LTS or any number of other linux if I wish, I'm running QQ to find bugs.  Sometimes development jumps right on a bug, sometimes they ignore them.  ?.

Well, not a showstopper, just an anklebiter.  I boot a lot so the BRIGHT SCREEN comes up a lot - now to reboot to try 3.5.0-7.

Jerry

Hey Jerry,

I was not aware of Acer machines with this problem too. Honestly it is a showstopper for me. Whenever I take my hands of the laptop enough time for it to dim a little and then touch it again my brightness rises to an almost completely white screen. I can feel the photons burning my brain through my eyes. It becomes unusable and hazardous and I have to press Fn+F5 exactly 14 times in order to start seeing characters and shapes. After doing that 100 times or so in a first half of every day I feel like throwing this laptop on the wall or inserting sharp metallic objects in its ports.

Maybe you are on the percentage of lucky users that can fix it with the switches I mentioned before. You can give a try to these changes in /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux acpi_backlight=vendor quiet splash" (**EDIT:** I forgot that GRUB_CMDLINE_LINUX instead of GRUB_CMDLINE_LINUX_DEFAULT makes more sense for some people, so edit accordingly of course) 
Then run sudo update-grub, restart and see if it helps. Hope it does, this thing is incredibly annoying.

Regards,
Effenberg

---

### Post by madjr on 2012-08-01
I have this bug with the proprietary amd driver.

the open source one seems to save the settings.

but i need the binary blob to game correctly. :)

---

### Post by Stefanhvt on 2012-08-01
I found this solution. It will work with the nvidia driver:

1. sudo gedit /etc/X11/xorg.conf

2. find the Section "Device" and add the bold line.

Section "Device"
Identifier	"Default Device"
Option	 "NoLogo"	 "True"
**Option "RegistryDwords"	"EnableBrightnessControl=1"**
EndSection

3. Reboot

This worked for me.

---

### Post by effenberg0x0 on 2012-08-01
Yep, it does for some NVidia users. I have NVidia on desktops. My current laptop has no discrete VGA, It's Intel :\
```

[16:06:37] ahsl@AL-NOTE01:[/sys/class/backlight]: lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
[16:06:38] ahsl@AL-NOTE01:[/sys/class/backlight]: ls
acpi_video0 intel_backlight
[16:06:38] ahsl@AL-NOTE01:[/sys/class/backlight]: cat */actual_brightness
14
1225

```That pretty much describes the issue.

Regards,
Effenberg

---

### Post by Stefanhvt on 2012-08-01
The only problem I still have is that the steps between the brightness levels are to high. So at the first step the screen is quite dark, and than the next step it's a bit to high.

Do you know a fix for this ?

---

### Post by effenberg0x0 on 2012-08-01
> **Stefanhvt said:**
> The only problem I still have is that the steps between the brightness levels are to high. So at the first step the screen is quite dark, and than the next step it's a bit to high.

Do you know a fix for this ?

In my case (the ASUS Laptop), I have verified that I have two devices in /sys/class/backlight. If I check the Min, Max brightness levels accepted for each of this devices, I can see that one of them allows for less than 20 brightness levels. The other allows for 2000 brightness levels: From complete pitch black to complete white screen - much more smooth adjustments and better battery usage in theory.

Gnome-Control-Center "Brightness and Lock" slider seems to use the device with less possible levels. Fn+F4/F5 Keyboard backlight hotkeys uses the other device, the one with more possible levels here.

IMO, it would be interesting that we could adjust backlight from 0 to max with as much levels and precision as possible, considering not only visual comfort but saving power. So the device with more levels should be used always and as the default.

If this is also your case (in case you also see two devices in /sys/class/backlight), you can read the values of min/max brightness for each of them to detect which is more complete (more levels). Then you can manually echo the desired value to this device&#347; current_brightness. You can script this easily as a dirty workaround. I don't think there's a working portable fix or actually any work being done on understanding this problem.

Regards,
Effenberg

---

### Post by Stefanhvt on 2012-08-01
I understand for a bit what you are saying. My knowledge of linux is not on an expert level. What I have noticed however in the dir you specified is that there is one item called actual_brightness. I opened it using gedit and found out that the vallue in that file was changin when I manually increased the brightness.

For the darkest setting the vallue started at 0, but than was followed up by 2, and 4, and so on. So it's not really necessarily for me to increase the possible steps, but to make sure that all steps are taken. Now every time I increase the brightness, one step is skipped, wich is not wanted.

Do you have any idea how to fix this ?

---

### Post by effenberg0x0 on 2012-08-01
> **Stefanhvt said:**
> I understand for a bit what you are saying. My knowledge of linux is not on an expert level.
Don't worry, me too. I can barely use this thing.
> **Stefanhvt said:**
> Do you have any idea how to fix this ?
I don't, sorry... I'm working on it.
> **Stefanhvt said:**
> What I have noticed however in the dir you specified is that there is one item called actual_brightness.
I would expect the "brightness files" (actual_brightness, bl_power, brightness, device, max_brightness, power, subsystem  type, uevent) to be inside a directory inside /sys/class/backlight. An example:
```

$ cd /sys/class/backlight
$ ls
acpi_video0  intel_backlight

```See, I am one of the happy dudes that have two devices fighting for backlight control, each with a different scale, min, max, steps, etc. If you only have one device, you're already looking better. Here's an example of the difference between devices:
```

$ cd /sys/class/backlight/acpi_video0
$ ls
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent
$ cat actual_brightness 
0
$ cat max_brightness 
10
$ cat brightness 
0
$ cat bl_power 
0

```Now let's check the same values for the other device:
```

$ cd /sys/class/backlight/intel_backlight
$ ls
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent
$ cat actual_brightness 
1225
$ cat max_brightness 
4882
$ cat brightness 
1225
$ cat bl_power 
-1337894168

```Both devices are completely different. And both respond to settings. I can write whatever value I want to using the Intel device. Example:
```

$ sudo -s
$ cd /sys/class/backlight/intel_backlight
$ echo 287 > brightness
$ echo 1200 > brightness

```Since I see changes to screen brightness using both odd and even values, I assume it has a step of 1 (yes, this is idiotic - but I'll just assume the step is not something like 11). Any value from 0 to 4882 will be accepted.

Now lets check the acpi0 device:
```

$ cd /sys/class/backlight/acpi0
$ echo 1 > brightness
$ echo 2 > brightness

```Again, it looks like the step is 1. Setting it to 1 produces a "normal", mid-to-high brightness. But even 2 is too bright for me. 3 is an eye killer. The acpi0 scale seems to be completely wrong. Why would 1 be so bright anyway?
> **Stefanhvt said:**
> 
For the darkest setting the vallue started at 0, but than was followed up by 2, and 4, and so on. So it's not really necessarily for me to increase the possible steps, but to make sure that all steps are taken. Now every time I increase the brightness, one step is skipped, which is not wanted.
I take it you were changing brightness using either the keyboard hotkeys or the slider inside Dash/Settings/"Brightness and Lock" and reading the values. 

The number of steps added/subtracted when we move the slider left/right is a mystery to me, I have no idea where it is harcoded, haven't looked for it yet. I'll look into g-c-c as soon as possible.

The keyboard brightness hotkeys, however, are associated to two scripts inside /etc/acpi: asus-brn-up.sh and asus-brn-down.sh.
As an example, here's what the "down" script does:
```

brightness=$((0x`setpci -s 00:02.0 F4.B`-16));
if [ $brightness -lt 0 ] ; then
   brightness=1;
fi
setpci -s 00:02.0 F4.B=`printf '%x' $brightness`;

```**EDIT:** *If this PCI address above is not dynamically set, it probably fails for a percentage of users. Why is it not detected dynamically, run-time?*

So, forget about all the shell script stuff, it is simply decreasing the brightness hex value (0xNN) by 16 (hexadecimal) or 10 (decimal). I could edit this script and change this step in both the "down" and the "up" scripts and it would make the transition more smooth when using the keyboard hotkeys. I actually did it and it worked as expected. But it did not affect the way the brightness slider in the Dash/Settings/"Brightness and Lock" behaves. This is expected in my case (because I have two devices). For people with a single device, the hotkeys should do the same as the slider.  

So, the current status of things is this:
1) I guess all devices, or modern devices, support steps of 1. Look at my test above and see if you can echo both odd and even values to "brightness" file and see a change in screen.
2) Brightness hotkeys invoke scripts that can be improved to make the brightness transition steps more smooth.
3) I have no idea how gnome-control-center brightness slider interacts with these. If it's hardcoded, steps can only be improved  by a change to source code (which involves a commit and FOSS politics. I probably will never submit this). 
4) People that have more than 1 device listed in /sys/class/backlight are a whole different problem. There shouldn't be more than 1 device controlling the backlight. If we must keep the devices, we must ignore the one with less brightness levels (less accuracy) and use the one that allows for better customization. If that is not possible, we need to use basic math to normalize both scales and a script to keep them in sync.

My conclusion is: It's faster, easier, less likely to involve FOSS politics to just create a solution based on scripts, that can detect if there's one or more devices, detect the more accurate device (if there's more than one) or use the single available one, associate this scripts to the brightness hotkeys, associate a load/save brightness routine to acpi events (poweron, shutdown, suspend, resume ,whatever), put it in a PPA people can use if they want to.

Sorry for the wall of text. I'm thinking as I write.

Regards,
Effenberg

**EDIT:** Another easy and fun test is to open gnome-control-center / "Brightness and Lock" and then use the keyboard brightness hotkeys. Ideally, the slider should move left / right as you press the keys to adapt to the actual brightness setting. Does not happen here.

**EDIT2: **A good way to promote the need to look into this is to put a multimeter in series between the battery and the laptop, and check how many more milliamp we're using when the laptop uses a less accurate scale and steps, instead of using one with more levels and smaller steps. It makes sense. I have a sensible enough Fluke lying around and it looks like fun :P

---

### Post by jerrylamos on 2012-08-02
> Another easy and fun test is to open gnome-control-center / "Brightness and Lock" and then use the keyboard brightness hotkeys. Ideally, the slider should move left / right as you press the keys to adapt to the actual brightness setting. Does not happen here.

Does not happen on my Acer 5253 widescreen notebook.  Max bright (ouch) no matter what.  I pound the keyboard to get the brightness back to minimum at least three times on every boot - I boot a LOT during development.

Solution is an external monitor and turn the laptop monitor off.  The external monitor absolutely ignores QQ "bright" command and uses it's internal menu, thank you.

Now my Acer Aspire1 netbook does respond to the QQ brightness which I set to about 15% when I'm not using this TV with it's own brightness set to 0.  Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller.

Anklebiter. I don't expect any interest from development.  I haven't tried Debian to see the problem is upstream too;  I'm using Debian on Raspberry Pi because there's no Ubuntu for it (yet?  If ever, Ubuntu Development is concentrated on the high end.  Lubuntu would be great.). 

Jerry

---

