---
title: "Elementary OS stuck at booting"
date: 2014-08-30
forum: Ubuntu/Debian BASED
---

### Post by warsong on 2014-08-30
Hey all!

Just installed Elementary OS on my Asus eeePC (2gb ram, Intel Atom n270) via USB.
The live version of the OS works perfectly fine.

When I go to boot from the one I installed on disk it gets stuck right after 
```
Starting CUPS printing spooler/server                           [OK]
```

After reading other threads in this forums I saw that some people were having issues with their video drivers and were told to boot with 'nomodeset' and install the correct drivers.
Unfortunately mine still got stuck at starting CUPS even with the 'nomodeset' param.

Any ideas would be greatly appreciated.

Just something else to note in case it makes a difference:
GRUB didn't install properly when the installation was finished. I had to use the boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) tool to fix it before I could get grub to load.

Thanks!

---

### Post by ben104 on 2014-08-30
Hi, did you have an internet connection while installing? I had trouble with GRUB installation as I didn't have an internet connection and had to end up using a wired connection until it all installed and updated and then the WiFi worked. Are you dual-booting or is it a stand alone install?

---

### Post by kurja on 2014-08-30
Maybe there's something in either [COLOR=#111111][FONT=Arial]/var/log/boot.log or [/FONT][/COLOR][COLOR=#111111][FONT=Arial]/var/log/dmesg that could hint at the culprit? One might guess that whatever is trying to load after cups, is causing the hang.

I'm presuming those logs are there, I've never tried elementary os.[/FONT][/COLOR]

---

### Post by warsong on 2014-08-30
Thanks for the replies.

I tried installing the OS while using both wireless and wired connections. Same outcome either way for me. It's a stand alone install.
I checked both log files

boot.log contains:
```

Starting system logging daemon        [OK]
Starting mDNS/DNS-SD daemon        [OK]
Starting bluetooth daemon                [OK]           
Starting CUPS printing spooler/server [OK]

```

dmesg contains:
```

(Nothing has been logged yet.)

```

Nothing too useful lol. Thought for sure there was going to be an error in there. Still no leads :(

---

### Post by ugrin.lu on 2014-12-21
Any updates? I have the same problem... Everything was running smoothly, I updated everything. Then I restarted and I can't boot up now.

Any help is appreciated, thanks!

Edit:
It was the Nvidia driver causing problems...
Thanks to [NikTh]("http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely") So I fixed it using these commands:
sudo apt-get remove --purge nvidia-*
sudo apt-get install elementary-desktop

---

