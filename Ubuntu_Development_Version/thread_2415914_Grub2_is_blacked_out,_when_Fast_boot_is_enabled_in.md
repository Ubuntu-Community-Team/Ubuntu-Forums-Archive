---
title: "Grub2 is blacked out, when Fast boot is enabled in Laptop's UEFI"
date: 2019-04-02
forum: Ubuntu Development Version
---

### Post by boqsc on 2019-04-02
I've installed Ubuntu 19.04 Disco Dingo, and Grub2 is blacked out due to enabled Fast boot. 
However, it boots perfectly, I just can't see Grub2 menu - I see instead - completely black-blank screen, and few seconds later - Ubuntu starts booting.

Ubuntu 18.10, Ubuntu 18.04 had no such problem.

I would like to know where I should report this, and what could be responsible as I have a fear that this bug might be unnoticed even after final release of Ubuntu 19.04 Disco Dingo.

Any help to trace the responsible project/package is appreciated.

---

### Post by oldos2er on 2019-04-02
19.04 is not released yet; thread moved.

---

### Post by meijer.o on 2019-04-06
This might solve your issue if you use Intel hardware, it will probably not increase boot time.

Try the following:

edit /etc/default grub:

```
sudo nano /etc/default/grub 
```

Add the boot parameter

```
i915.fastboot=0
```

Update grub

```
sudo update-grub
```

Reboot.
Kind regards,

Otto

---

### Post by boqsc on 2019-04-07
Well, I have:  

**CPU:** [Intel® Core&#8482; i7-3630QM]("https://ark.intel.com/content/www/us/en/ark/products/71459/intel-core-i7-3630qm-processor-6m-cache-up-to-3-40-ghz.html")
**GPU:** [AMD Radeon&#8482; HD 7670M Graphics (2GB dedicated memory)]("https://www.techpowerup.com/gpu-specs/hp-hd-7670m-2-gb.b5401")
*More general information available about the Laptop: *[http://www.toshiba.co.uk/discontinued-products/satellite-l855-149/]("http://www.toshiba.co.uk/discontinued-products/satellite-l855-149/#")


I did exactly as you wrote:
> 
vaidas@vaidas-SATELLITE-L855:~$ sudo update-grub
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: i915.fastboot=0: not found
vaidas@vaidas-SATELLITE-L855:~$ 


Nothing changed, I even rebooted to check if anything got affected.

> it will probably not increase boot time.
I was expecting exactly this. That's bad news for me, even if what you suggested would have worked.
And kind of annoying, as Windows 10 is booting way faster than Ubuntu. (By around 6-8 seconds faster) 
I hope that will get fixed and it's just temporal.

---

### Post by oldfred on 2019-04-07
This is only for Skylake an newer Intel chips.
        i915.fastboot=1 kernel parameter. Fastboot helps provide a clean, flicker-free Linux boot experience.
New 5.1 kernel will include it by default on Skylake and newer 
    
Some find removing snaps improves boot time. And they are working on making them faster.
       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements) 
    
For your system you can see what takes the time to boot.
        systemd-analyze
systemd-analyze critical-chain

---

### Post by meijer.o on 2019-04-07
I have tested your issue on my laptop

If /etc/default/grub looks like this, the grub menu will _not_ appear:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=4
```


If /etc/default/grub looks like this, the grub menu will appear:

```
GRUB_DEFAULT=0
# GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=4
```

I do not have an entry for Windows

Best regard, Otto

---

### Post by boqsc on 2019-04-07
The file **/etc/default/grub **that I have, does not contain **GRUB_TIMEOUT_STYLE **option.
> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


---

### Post by boqsc on 2019-04-07
Some insights that systemd gave:

**The critical-chain output as Image:**
[IMG]https://i.ibb.co/Dkt93tn/Screenshot-from-2019-04-07-22-39-29.png[/IMG]


**The critical-chain output as text:**
```

vaidas@vaidas-SATELLITE-L855:~$ systemd-analyze critical-chain 
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @22.790s
&#9492;&#9472;multi-user.target @22.790s
  &#9492;&#9472;kerneloops.service @7.426s +13ms
    &#9492;&#9472;network-online.target @7.420s
      &#9492;&#9472;NetworkManager-wait-online.service @1.303s +6.115s
        &#9492;&#9472;NetworkManager.service @1.167s +135ms
          &#9492;&#9472;dbus.service @1.164s
            &#9492;&#9472;basic.target @1.148s
              &#9492;&#9472;sockets.target @1.147s
                &#9492;&#9472;snapd.socket @1.146s +1ms
                  &#9492;&#9472;sysinit.target @1.141s
                    &#9492;&#9472;systemd-backlight@backlight:radeon_bl0.service @1.980s +65
                      &#9492;&#9472;system-systemd\x2dbacklight.slice @1.967s
                        &#9492;&#9472;system.slice @155ms
                          &#9492;&#9472;-.slice @155ms



```


Simply launching **systemd-analyze**, the output:
```

vaidas@vaidas-SATELLITE-L855:~$ systemd-analyze 
Startup finished in 6.144s (firmware) + 10.259s (loader) + 2.258s (kernel) + 22.802s (userspace) = 41.464s 
graphical.target reached after 22.790s in userspace


```

---

### Post by oldfred on 2019-04-07
Network manager seems to be an issue.

Not sure if this helps or not.
       Slow boot issue
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1723809](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1723809)
[https://forums.linuxmint.com/viewtopic.php?t=282437](https://forums.linuxmint.com/viewtopic.php?t=282437)
$ systemctl unmask NetworkManager-wait-online.service
$ systemctl enable NetworkManager-wait-online.service

---

### Post by boqsc on 2019-04-07
Before disabling: (Took a picture for fun historical records)
[IMG]https://i.ibb.co/8xgsdz1/Screenshot-from-2019-04-07-23-34-39.png[/IMG]

I Disabled **NetworkManager-wait-online.service, **haven't felt any huge improvements (actually any)
```
vaidas@vaidas-SATELLITE-L855:~$  systemctl disable NetworkManager-wait-online.service
Removed /etc/systemd/system/network-online.target.wants/NetworkManager-wait-online.service.


```

After Disabling **NetworkManager-wait-online.service**
```

vaidas@vaidas-SATELLITE-L855:~$ systemctl status NetworkManager-wait-online.service
&#9679; NetworkManager-wait-online.service - Network Manager Wait Online
   Loaded: loaded (/lib/systemd/system/NetworkManager-wait-online.service; disab
   Active: inactive (dead)
     Docs: man:nm-online(1)
lines 1-4/4 (END)


```


**NetworkManager-wait-online.service **seems to be gone from[B] critical-chain of systemd-analyze

As mentioned - haven't felt any actual improvements, the black screen before loading ubuntu keeps taking a long time.[/B]

[IMG]https://i.ibb.co/X3gJHFk/Screenshot-from-2019-04-07-23-27-33.png[/IMG]

---

