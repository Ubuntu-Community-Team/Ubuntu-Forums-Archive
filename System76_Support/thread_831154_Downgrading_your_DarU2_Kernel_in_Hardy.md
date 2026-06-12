---
title: "Downgrading your DarU2 Kernel in Hardy"
date: 2008-06-16
forum: System76 Support
---

### Post by walkeraj on 2008-06-16
[COLOR="Red"]Healthy Warning[/COLOR]: *While there is very little risk of doing anything catastrophic or unreversible to your system by following these instructions, you ARE doing things that are a little outside of the norm by pulling from an older repository and, for all I know, this will make your laptop explode, killing you and everyone who loves you.  It works fairly well for me, but your mileage may vary.  Caveat emptor.*

So, yes.  It seems as if the 2.6.24 (Hardy) kernel series is borked and no one knows why.  Hopefully this will be remedied in the near future, but it can definitely be annoying given that it's Hardy's default kernel.  You can go back to Gutsy, or you can just install the Gutsy kernel/modules (2.6.22) and use those in the meantime.

In order to do this, you'll need to pull them from the gutsy repositories, because 2.6.22 isn't supported in Hardy.

the simplest way to do this is from the commandline:

```

echo "deb http://us.archive.ubuntu.com/ubuntu gutsy main">/tmp/gutsy.list
sudo mv /tmp/gutsy.list /etc/apt/sources.list.d
sudo apt-get update
sudo apt-get install linux-image-2.6.22-14-generic
sudo apt-get install linux-ubuntu-modules-2.6.22-14-generic
sudo apt-get install linux-backports-modules-2.6.22-14-generic
sudo rm /etc/apt/sources.list.d/gutsy.list
sudo apt-get update

```

The reason we run *apt-get update* twice is so that synaptic won't bother you with "updates" from the gutsy repository.  If you've made changes to your /boot/grub/menu.lst, it may attempt to overwrite the file with a more generic version.  It should be safe to let it, but, before you reboot, you might want to edit the default boot image to your "new" 2.6.22-14 kernel, otherwise you'll have to hit escape every time you boot in order to chose the older kernel.  To do this, just issue:

```
sudo gedit /boot/grub/menu.lst
```

Ensure that your 2.6.22-14-generic entry reads something like this (except with your UUID):

```

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx ro quiet splash ec_intr=0
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

You'll probably have to add "ec_intr=0" to the end.  This kernal option ensures that power management works better on your DarU2.  Depending on where the installation places this entry in your menu.lst, you'll need to change the value of "default" (which is towards the beginning of the file) accordingly.  Just remember that the entries start at 0, so if your new kernel is the third set of options down, the line should read:

```
default		2
```

Restart your machine, and it should boot into the new (but actually older) kernel.  Your system should function better, but will include some of the older annoyances like brightness levels that do nothing and maybe some problems with hibernate.  The upswing is that you'll be able to remain up-to-date with the rest of Hardy as it moves forward.

Once we actually get a working 2.6.24-series kernel (whenever that may be) you can remove the packages from synaptic or the command line by issuing:

```

sudo apt-get purge linux-image-2.6.22-14-generic

```

Which will also uninstall the module packages.  In the meantime, until the all-clear is given, I'd avoid taking any kernel updates from synaptic unless you want to test them out.  If you take any kernel updates, they'll probably change the value of default in /boot/grub/menu.lst, and you'll have to change it back if you want it to automatically boot into the 2.6.22 kernel.

So, yeah.  That will give you a Hardy install with a Gutsy kernel, and it's probably totally unsupportable, but at least it works better, right?

---

### Post by walkeraj on 2008-06-16
Well, sort of.

Issues discovered so far:

**Wireless doesn't work after returning from suspend.**
When I come back from suspend, networking is disabled, and checking the box again does nothing.  Wireless doesn't show up and I have tried the following things to no avail:

-set STOP_SERVICES="networking" in /etc/default/acpi-support
-set MODULES="iwl4965" in /etc/default/acpi-support
-set gconf gnome-power-manager/general/network_sleep to "on"
-added acpi=noirq to kernel options (didn't work, and borks brightness et al)

Seem to recall this might have been a fixed problem in Gutsy, but can't recall.  Will continue to work on this.  Aside from this setback, everything else seems to work.

---

### Post by thomasaaron on 2008-06-16
Try: sudo /etc/dbus-1/event.d/25NetworkManager restart

Also, you probably should try running your System76 driver. If it detects your system as being on Gutsy, then it may apply the appropriate fix.

---

### Post by walkeraj on 2008-06-16
That sort of worked.  I ran the driver script, rebooted and it suspended and came back with wireless.  I suspended again, and it was gone.  I told the Network manager to restart by issuing ```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

The screen sat at ```
 * Restarting network connection manager NetworkManager
``` for about a minute and a half or two minutes, then the wireless connecting icon cycled for a while.

Now, instead of the signal strength, it displaces the two monitors icon as if I'm connected through eth0, but I'm actually connected to wireless.  If I go to a prompt and start nm-applet manually, I get another icon with the signal bars.  This is... strange.

---

### Post by walkeraj on 2008-06-16
Output of ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:19:db:ee:6a:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:19:db:ee:6a:a2  
          inet addr:169.254.9.108  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7700 (7.5 KB)  TX bytes:7700 (7.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:70:9e:49  
          inet addr:172.16.0.99  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe70:9e49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149917 (146.4 KB)  TX bytes:111621 (109.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-70-9E-49-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by thomasaaron on 2008-06-16
It's starting to sound a bit like this one...

[https://bugs.launchpad.net/system76/+bug/122298](https://bugs.launchpad.net/system76/+bug/122298)

---

### Post by walkeraj on 2008-06-16
The solution contained in that bug works sporadically.  Sometimes, the machine will resume from suspend and will scan for a new wireless network.  Sometimes it will not.  In either case, after resuming from suspend the machine will not restart properly.  Shutdown, yes.  Restart freezes in the final stages.

---

### Post by thomasaaron on 2008-06-17
OK, well it's probably because of something funky with the downgrade. The DarU2 suspends and hibernates great with a fresh install of 64-bit Gutsy.

There's an awful lot that could be amiss with the method you used to downgrade.

---

### Post by walkeraj on 2008-06-18
Well, looks like that's what I'm going to be installing, then. :)

---

