---
title: "fsck stuck at boot"
date: 2021-07-06
forum: Server Platforms
---

### Post by techlabe on 2021-07-06
Hello i hope i'm at the good place.

I have some trouble to boot my Ubuntu. 

When i  power on my server (Dell Poweredge 340), i get stuck on a fsck check like /dev/sda* clean, files, blocks. 

- I cant CTRL+C. 
- I though it was because of a lack of space on some partition, but its not the problem. (df -h gave me used space as 1% on system partition) 
- I tried to boot on a Ubuntu LiveUSB key, go to "Try Ubuntu" and manually did a fsck test on the sda who is actually stuck at boot, but fsck test was fast and no problem was found. 
- I'm out of ideas... i watchs people who resolve it by purge Nvidia drivers but i'm afraid to try this.

Anyone have an idea ? 

Thanks a lot.

---

### Post by Irihapeti on 2021-07-06
*Thread moved to **Server Platforms** for a better fit.*

---

### Post by MAFoElffen on 2021-07-06
You say it's a server (chassis). What is the OS version, flavor and it's job? DO you have NVidia graphics actually installed on it? And if you do, is it Desktop or Server?

Next, do you ever see a Grub Boot Screen before it gets to that?

Yo usay you can boot on a Ubuntu LiveCD USB key... is there still an empty file on /dev/sdaX (whatever the root partition is) named "forcefsck"?

---

### Post by TheFu on 2021-07-08
*forcefsck* hasn't worked since systemd took over fstab mounting.
fsck of the OS partition/LV can be accomplished 4 ways.  
[LIST=1]
[*]Modify the grub boot settings to do it (either in the grub config file or at boot time via the edit option).  
[*]Boot into recovery option (this is under Advanced Boot) from the first grub screen displayed
[*]Boot from alternate media, like any Live Boot Linux media - Try Ubuntu environments.
[*]Use tune2fs to modify the fsck settings for ext2/3/4 file systems to happen more often.  It can be either X number of reboots or Y number of days since the last fsck.
[/LIST]

But if any of those show the fsck is clean, none of the others will do anything better.

I miss the **sudo touch /forcefsck** method.  It was the only way besides tune2fs that didn't require someone physically being at the system. That's handy for systems without IPMI or riblo/drac cards.

---

### Post by TheFu on 2021-07-08
If there are issues with booting, the best option for help is to boot from alternate media into a Try Ubuntu environment, install the boot-repair package, and having it gather data. DO NOT actually run the "fix boot" option. Just gather the information and post the URL here for some other people to look at.

---

### Post by MAFoElffen on 2021-07-08
In the boot process, that seems to be hung somewhere between the kernel boot process and the user space script process. fsck on reboot occurs before the disks are mounted.

If you boot from a livecd and mount the system , you then look at the logs... 

If I look at my systemd boot process statistics, to see where fsck occurs... For example, if I do:
```
mafoelffen@Opti-Ubuntu-Main:~$ sudo systemd-analyze critical-chain 

The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @16.050s
  +--multi-user.target @16.050s
    +--kerneloops.service @16.023s +26ms
      +--network-online.target @16.015s
        +--NetworkManager-wait-online.service @10.937s +5.077s
          +--NetworkManager.service @8.867s +2.066s
            +--dbus.service @8.862s
              +--basic.target @8.823s
                +--sockets.target @8.823s
                  +--cockpit.socket @8.627s +196ms
                    +--sysinit.target @8.572s
                      +--systemd-timesyncd.service @8.012s +559ms
                        +--systemd-tmpfiles-setup.service @7.667s +301ms
                          +--local-fs.target @7.656s
                            +--home-mafoelffen-WIN_G.mount @5.094s +2.561s
                              +--home.mount @4.873s +87ms
                                +--systemd-fsck@dev-disk-by\x2duuid-a5c5987f\x2d82>
                                  +--dev-disk-by\x2duuid-a5c5987f\x2d82ab\x2d4e16\>
lines 1-21/21 (END)
```
For some reason it won't let me post the whole thing in one post...

---

### Post by MAFoElffen on 2021-07-08
You can see that it goes by reverse order, and that systemd starts before   it does the "systemd-fsck@dev-disk-by"... Right after, it is supposed   to start doing any mounts of the disks and filesystems... 

Though, systemd-analyze will not show on a mounted system, because that   would be in the temporary system filespace (which the installed system   is not going to show on mounted system.) If the user had installed the   bootchart package, it then writes those stats to disk. That is why I   install that on my own.

But the sys logs of the mounted/installed system, will show it. The   system slice that you want to look at is: (And for some reason, this   forum errors out on my trying to type out this command in code   blocks???) Use "dmesg" piped through grep... to filer on "Detected  Architechture"... And look at the 25 lines after...


There seems to be a bug in the forums software which which will not let me post the command for that. Not even in code or quote tags..... It will not let me post the command in one string, so put this together into one command:
```
dmesg | 
```
```
 grep -i -a25 
```
```
 "Detected Architecture" 
```

---

