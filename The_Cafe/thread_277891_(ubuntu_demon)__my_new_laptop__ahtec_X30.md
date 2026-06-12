---
title: "(ubuntu_demon) : my new laptop : ahtec X30"
date: 2006-10-15
forum: The Cafe
---

### Post by ubuntu_demon on 2006-10-15
I bought my new laptop! 
[http://ubuntudemon.wordpress.com/2006/10/15/i-bought-my-new-laptop/](http://ubuntudemon.wordpress.com/2006/10/15/i-bought-my-new-laptop/)

Thank you everyone for your help,suggestions and feedback!

I bought an Ahtec Style X30 from Mingos ([www.mingos.nl)](www.mingos.nl)). They sell Ahtec laptops with Ubuntu on it. It's also possible to buy your laptop from Mingos without an OS at roughly the same price as ahtec sells them. Currently this laptop costs 1124 euro at mingos without tax and without Ubuntu pre-installed. I was lucky and I got a little bit of a discount.

I choose this laptop because :
-it fitted my requirements/wishes best
-ahtec and mingos are the only Dutch companies I know that sell mobile laptops without windows
-mingos has experience with Ubuntu on the X30

A week ago I went to mingos to try and see the laptop. I decided to buy it. I got my laptop last friday evening. I'm only posting about my new purchase now because I wanted to test it for a little bit first.

This are the specifications of the laptop I bought :

Mingos LT-13 = Ahtec Style X30
2,16 KG
13" , 1024x768
intel centrino 
intel GMA 950 video
Intel T2500 Core Duo 2 ghz, 2 mb cache
intel ipw3945 a/b/g wireless
2 GB ram (DDR2 667 mhz)
80 GB Sata 5400 rpm harddrive
combo drive : cd-r/rw+dvd
laptop-bag
2 years of guarantee (1 year pickup and return)

I got 2 GB of memory because :
- I study Artificial Intelligence. Some day I might need to program something which uses a lot of memory.
- My goal is to use this laptop for at least 3 years and I want to be future proof.


```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)

```

It works near perfectly!

I'm having some small but annoying issues with the video. I will investigate some more and post about this later. I'm blaming it on xserver-xorg-intel driver. The driver is open source so I'm sure it will be fixed.

I'm still testing the laptop. I will use this thread to report some findings. Once Edgy is released I will put a review on the wiki.

My laptop search on this forum :

Help me find a good laptop
[http://www.ubuntuforums.org/showthread.php?t=247158](http://www.ubuntuforums.org/showthread.php?t=247158)

My blog posts about my laptop search :

Some changes in my life
[http://ubuntudemon.wordpress.com/2006/09/01/some-changes-in-my-life/](http://ubuntudemon.wordpress.com/2006/09/01/some-changes-in-my-life/)

laptop hunt continues - feedback request
[http://ubuntudemon.wordpress.com/2006/09/24/laptop-hunt-continues-feedback-request/](http://ubuntudemon.wordpress.com/2006/09/24/laptop-hunt-continues-feedback-request/)

Possible laptops - feedback request
[http://ubuntudemon.wordpress.com/2006/09/09/possible-laptops-feedback-request/](http://ubuntudemon.wordpress.com/2006/09/09/possible-laptops-feedback-request/)

dutch Ubuntu forum thread :

help me een goede laptop vinden
[http://forum.ubuntu-nl.org/topic/3066](http://forum.ubuntu-nl.org/topic/3066)

dutch tweakers threads I participated in :

[Ervaringen] 12" Laptops Deel 2
[http://gathering.tweakers.net/forum/list_messages/1062275](http://gathering.tweakers.net/forum/list_messages/1062275)

[Ervaringen] MSI Megabook S2x0 series (deel 3)
[http://gathering.tweakers.net/forum/list_messages/1098331](http://gathering.tweakers.net/forum/list_messages/1098331)

---

### Post by tseliot on 2006-10-15
Congrats! It's a nice laptop. ;) 

I do agree with your choice of having 2GB of RAM.

---

### Post by ubuntu_demon on 2006-10-15
The normal harddrive temperature is 53-55 °C. Although I haven't put it through much work/testing yet.

**Some testing I have done with cpuburn (burnP6) :**

I used the cpu scaling applet to monitor scaling. I installed lm-sensors and sensors-applet to get my cpu temperature.

On top of my regular desktop (with some stuff open) I started burnP6 twice.

When I run one burnP6 (instead of two) only one core gets a full load and cpu-scaling happens only for that core. This is very neat!

The option "prefer power savings over performance" of gnome-power-manager doesn't seem to do anything regarding the cpu. There's no significant difference regarding scaling and cpu temperature.

There's a special "S" button on my laptop. Let's call it "in-S-mode" when it's used and "not-in-S-mode" otherwise.

[quote=manual]Silent Mode Button
Pressing the key enables the system to lower its power usage;
therefore the fan speed is reduced to achieve lowest operating
noise.
[/quote]

**ON AC :**

normal CPU temperature = 50-52 degrees celcius, 50% scaling

burnP6 (twice) :

not-in-S-mode : max CPU temperature of 76-77 degrees celcius, 100% scaling

in-S-mode : max CPU temperature of 55 degrees celcius, 100% scaling, fan makes less noise

**On battery :**

normal CPU temperature = 50-52 degrees celcius, 50% scaling

burnP6 (twice) :

not-in-S-mode : max CPU temperature of 58 degrees celcius, 66% scaling

in-S-mode : max CPU temperature of 55 degrees celcius, 66% scaling, fan makes less noise

**conclusions : **

I also decided to always set "power savings over performance" and I decided to always run "in-S-mode".

**update to clarify :**

max temperature was only after a little bit of time of running cpuburn (burnP6)

---

### Post by Perfect Storm on 2006-10-15
Meh....I want a new PC too. :-?

---

### Post by ubuntu_demon on 2006-10-15
> **tseliot said:**
> Congrats! It's a nice laptop. ;) 


Thanks! :)

> **tseliot said:**
> 
I do agree with your choice of having 2GB of RAM.

It's mostly a future-proof thing :)

---

### Post by raycast on 2006-10-15
How is battery life of that laptop?

---

### Post by matthew on 2006-10-15
Congratulations!! Nice looking piece of hardware. (Why does that sound like a bad pickup line? ...eww...)

---

### Post by chaosgeisterchen on 2006-10-15
I am hoping it lasts as long as you wish it to last :)

Great price for a notebook with that amount of power inside..

I find it funny that my 14,1" notebook is more lightweight than your new 13" ;)

---

### Post by Kateikyoushi on 2006-10-15
Congrats for your first notebook.
My notebook does not have a fan still the hard drive temperature barely changes even under full load so yours won't reach the maximum recommended 60C either.

---

### Post by John.Michael.Kane on 2006-10-15
ubuntu_demon that what i call ultra portable. nice machine.

How much does it weigh? from the pictures i would guess 1.5-3lbs

---

### Post by Kateikyoushi on 2006-10-15
According to his post it is around 2kg.

---

### Post by ubuntu_demon on 2006-10-16
I bought an X30 instead of an X20 because :
-mingos had experience with Ubuntu on th X20
-the X30 has a bigger screen but the volume of the laptop is about the same as the X20

---

### Post by chaosgeisterchen on 2006-10-16
Nontheless, GREAT notebook. I hope it will ever fit your expectations.

---

### Post by ubuntu_demon on 2006-10-16
The battery lasts at least 2 hours. I can give a better estimate later.

I'm still testing the laptop. This weekend I'm going to my "old" home by train. It's a long train ride. This gives me the perfect opportunity to get more real-world information about battery life.

The battery is made for about 300 discharges/charges. So I'm not going to waste them :).

---

### Post by ubuntu_demon on 2006-10-16
Thanks everyone for the congrats!

---

### Post by ubuntu_demon on 2006-10-16
> **SD-Plissken said:**
> ubuntu_demon that what i call ultra portable. nice machine.

How much does it weigh? from the pictures i would guess 1.5-3lbs
2.16 kg. I measured it myself :)

The Ahtec website advertises the weight without the optical drive and such : 1.9 kg.

---

### Post by chaosgeisterchen on 2006-10-16
2 hrs? I do know why I wouldn't want to own this notebook, I have some need for up to 4hrs ;)

---

### Post by ubuntu_demon on 2006-10-16
> **chaosgeisterchen said:**
> 2 hrs? I do know why I wouldn't want to own this notebook, I have some need for up to 4hrs ;)
I said **at least** 2 hours :)

I haven't tested it enough to give a good estimate.

This laptop has a 6 cell battery. More cells mean better battery life.

Battery life also depends very much on what you do with it.

I got about 2 hours and 40 minutes out of it when I just go it. But this number doesn't say very much because : 
- This includes the time it hibernated during switching trains and the time I suspended it on my "final" walk to my girlfriend
- I was playing with it (hibernate,wireless and other stuff)
- I think I wasn't running in S-mode.

---

### Post by chaosgeisterchen on 2006-10-16
It's getting better. Sounds very nice so far.. 3 and a half hour in S-Mode?

---

### Post by mips on 2006-10-16
Congrats !!!

I do have a concern though, it seems that laptop runs very hot. Heat is a component killer and something you don't want.

---

### Post by ubuntu_demon on 2006-10-16
> **chaosgeisterchen said:**
> It's getting better. Sounds very nice so far.. 3 and a half hour in S-Mode?
Maybe if :
-S-mode
-wireless turned off
-screen brightness to the lowest
-only non-power-intensive work

I think somewhere between 2 and 3 hours is more realistic though in the real world. But you just have to be patient. I will slowly report all my findings :)

---

### Post by ubuntu_demon on 2006-10-16
> **mips said:**
> Congrats !!!

I do have a concern though, it seems that laptop runs very hot. Heat is a component killer and something you don't want.
both on AC and on battery :
in-S-mode : max CPU temperature of roughly 55 degrees celcius, 100% scaling, fan makes less noise


Regarding the harddrive :

Today I was running the laptop on battery and the harddrive was about 42 degrees with normal usage. It's about 10 degrees higher when on AC with normal usage.

---

### Post by chaosgeisterchen on 2006-10-16
> **ubuntu_demon said:**
> Maybe if :
-S-mode
-wireless turned off
-screen brightness to the lowest
-only non-power-intensive work

I think somewhere between 2 and 3 hours is more realistic though in the real world. But you just have to be patient. I will slowly report all my findings :)


Too bad, I was hoping you'd write sth near 4 hrs :)

---

### Post by Kateikyoushi on 2006-10-16
> **ubuntu_demon said:**
> Regarding the harddrive :

Today I was running the laptop on battery and the harddrive was about 42 degrees with normal usage. It's about 10 degrees higher when on AC with normal usage.

My notebook also gets hotter while it is charging.
My girlfriend's U101 with the large battery pack which almost doubles the weight of the notebook gets around 9 hours, that's almost 3 times what mine has.

---

### Post by ubuntu_demon on 2006-10-16
Wireless works perfectly but sadly not for the wireless network of my university(PEAP/WEP). I created a new thread for this specific problem I have :
[http://www.ubuntuforums.org/showthread.php?t=278603](http://www.ubuntuforums.org/showthread.php?t=278603)

---

### Post by Mike Wazowski on 2006-10-17
Cool laptop!!!

By the way, how do you measure HD temperature in Edgy?:-k 
I can only measure the CPU temp.

I've been cracking my head with this.](*,) 
I'm a rookie in these things, but working to improve the status ;) 

MW

---

### Post by Kateikyoushi on 2006-10-17
You can check it in the smart of the hdd or use hddtemp.

---

### Post by Mike Wazowski on 2006-10-17
WOW!
Thanks a lot!!!!

MW

---

### Post by ubuntu_demon on 2006-10-18
> **Mike Wazowski said:**
> Cool laptop!!!

By the way, how do you measure HD temperature in Edgy?:-k 
I can only measure the CPU temp.

I've been cracking my head with this.](*,) 
I'm a rookie in these things, but working to improve the status ;) 

MW
$ sudo aptitude install hddtemp sensors-applet lm-sensors

lm-sensors is for measuring the CPU temperature

sensors-applet is for the applet you can add in your panel to actually view the data in a convenient way :)

Don&#8217;t forget to run &#8220;$sudo sensors-detect&#8221; if you want to know other things except your hddtemp. If you don&#8217;t understand the questions answer YES to all of them.

---

### Post by ubuntu_demon on 2006-10-19
**about the minor video problems :**

- suspend-to-ram either doesn't return from being suspended sometimes OR the video doesn't return from being suspended sometimes.

- hibernate-to-disk puts a white line on the screen when returning from hibernation. 

- when I log out and enter the login screen often the colours are messed up

I suspect all of this is related to the videodriver somehow. I have tried xserver-xorg-intel and xserver-xorg-i810 and both drivers seem to have this.

I will further investigate this :
-I will play with the video-settings
-I will install ssh and try logging into my laptop from an other pc
-any other ideas ?

**about hibernation :**

I haven't tried hibernation much but everything seems to work perfectly when I return from hibernation.

Right before going into hibernation I get this :

> 
[17181101.896000] pnp: Failed to activate device 00:04.
[17181101.896000] pnp: Failed to activate device 00:05.


So I looked up which devices it were with lshal :
> 
udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'  (string)
  linux.subsystem = 'pnp'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.id = 'PNP0303'  (string)
  info.linux.driver = 'i8042 kbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.bus = 'pnp'  (string)
  linux.sysfs_path_device = '/sys/devices/pnp0/00:04'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_SYN0801'
  info.udi = '/org/freedesktop/Hal/devices/pnp_SYN0801'  (string)
  linux.subsystem = 'pnp'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  info.product = 'PnP Device (SYN0801)'  (string)
  pnp.id = 'SYN0801'  (string)
  info.linux.driver = 'i8042 aux'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.bus = 'pnp'  (string)
  linux.sysfs_path_device = '/sys/devices/pnp0/00:05'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)


I have no problems after returning from hibernation whatsoever. But maybe I should report a bug anyway. Does anyone have an idea where this bug about this error message should go ?

**update :**

The videoproblems bug when logging out seems to be fixed.

Here's the suspend/hibernate bug : [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68328](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68328)

---

### Post by ubuntu_demon on 2006-10-19
> **ubuntu_demon said:**
> Wireless works perfectly but sadly not for the wireless network of my university(PEAP/WEP). I created a new thread for this specific problem I have :
[http://www.ubuntuforums.org/showthread.php?t=278603](http://www.ubuntuforums.org/showthread.php?t=278603)

To make it more clear : this was only related to the lack of a good manual on the part of my university.

I figured it out :).

---

### Post by ubuntu_demon on 2006-10-24
**0:26** to boot

On my new laptop. I installed Edgy RC and I booted a couple of times with the kernel option "profile".

Here's the bootchart thread :
[http://www.ubuntuforums.org/showthread.php?t=241604](http://www.ubuntuforums.org/showthread.php?t=241604)

---

### Post by ubuntu_demon on 2006-10-24
Some powermanagement tweaks I'm playing with :

$ sudo pico /etc/default/acpi-support

I changed false to true here :
```

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true

```

$ sudo /etc/init.d/acpid reload

another one : 

iwconfig's txpower provides a way to set the power of the wireless signals you send.
$ sudo iwconfig eth1 txpower *16*
*16* is the default value in my case

I hope this will save a little bit of power :)

---

### Post by Kateikyoushi on 2006-10-24
I am curious how much can be saved with it, testing now.
Could you report it after some testing ?

---

### Post by ubuntu_demon on 2006-10-24
> **Kateikyoushi said:**
> I am curious how much can be saved with it, testing now.
Could you report it after some testing ?
I will report my battery life when I have made a long traintrip next weekend which involves :
- 2.5 hours on battery in the train
- hibernate or shutdown
- 1 hour on battery in the train

I'll also do the trip in reverse a couple of days later :).

I will run it in S-mode without wireless on.

---

### Post by ubuntu_demon on 2006-10-25
note to self :
add this to the synaptics device in Xorg.conf to disable tapping :
```

Option      "MaxTapTime"    "0"

```

---

### Post by ubuntu_demon on 2006-10-27
I&#8217;m still happy with my new laptop :) It&#8217;s working nearly perfect. Here are some bugs I discovered though :

suspend-to-ram and hibernate-to-disk don&#8217;t work properly. Bug report : [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68328](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68328)

(good battery life and fast booting makes this problem less irritating then it would seem)

The &#8220;media&#8221;-key doesn&#8217;t start a multimedia application :) Bug report : [https://launchpad.net/distros/ubuntu/+source/hotkey-setup/+bug/68353](https://launchpad.net/distros/ubuntu/+source/hotkey-setup/+bug/68353)

The wiki page : [https://wiki.ubuntu.com/LaptopTestingTeam/AhtecStyleX30Duo](https://wiki.ubuntu.com/LaptopTestingTeam/AhtecStyleX30Duo)

---

### Post by ubuntu_demon on 2006-10-27
beryl works nicely on this laptop :
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

---

### Post by ubuntu_demon on 2006-10-27
from [http://www.ubuntuforums.org/showpost.php?p=1107464&postcount=17](http://www.ubuntuforums.org/showpost.php?p=1107464&postcount=17) :
[quote=meridius]
Linux can use different power management profiles called "governors." By default, Ubuntu does not allow you to change which governor it uses, however you can enable the option with one command:

$ sudo dpkg-reconfigure gnome-applets

After that, make sure you have the "CPU Frequency Monitor" applet running in your Gnome panel. Right click on the applet and go to the Preferences. Under "Frequency Selector" section, make sure the "Show menu" is selected on "Frequencies and Governors."

Then you can left click on the applet and from here, choose which governors or frequencies to use.

If you're confused as to which governor to use, just try them all. There shouldn't be too many.
[/quote]

This means I can now easily switch to powersave when in the train :)

This weekend I'm going to make some train rides. I will be able to test the battery. What I'm going to do :

-turn wireless off
-lower the brightness of my screen
-use powersave as a governor (still 2 processors with 1 Ghz each)
-run in "S-mode"
-I already set : "ENABLE_LAPTOP_MODE=true" in /etc/acpi-support
-use metacity instead of beryl/emerald

---

### Post by jkow on 2006-12-18
Hi,

I  [_think about_](http://jkow.livejournal.com/49961.html) buying a laptop with the intel 950 graphics adapter and I wonder if you ever tried 3d acceleration for your desktop. In some other forum I read about a user having problems activating dri. Anything you experienced?

---

