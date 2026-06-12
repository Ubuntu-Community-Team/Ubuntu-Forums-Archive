---
title: "HOWTO: Fix suspend sleep mode from S0 s2idle to S3 deep in Xubuntu 22.04.1 LTS"
date: 2022-10-02
forum: Tutorials
---

### Post by Copter on 2022-10-02
Hi.

It has been 11 years since my last post on Ubuntu Forums. I hope that someone still finds this information useful.

I had a problem with suspend on Acer Apire Vero laptop (i5 1155G7, Iris Xe) running Xubuntu 22.04.1 LTS with stock kernel (5.15.0-48-generic). It turned out that after closing the lid or clicking Menu - Logout - Suspend button the computer did not enter deep sleep mode. The processes were suspended but the fan was still running for a while. Leaving laptop unplugged in that state for 10 hours resulted in 11% of battery loss. According to the document below, the system was entering S0 state (s2idle). This is the "shallowest" of sleep modes. The processes are stopped but the power consumption is not reduced to minimum.

[https://www.kernel.org/doc/Documentation/power/states.txt](https://www.kernel.org/doc/Documentation/power/states.txt)

```

copter@plastic:~$ journalctl | grep -C 2 suspend

Oct 02 19:39:04 plastic systemd[1]: Starting Record successful boot for GRUB...
Oct 02 19:39:04 plastic systemd[1]: Starting System Suspend...
Oct 02 19:39:04 plastic kernel: PM: suspend entry (s2idle)
Oct 02 19:39:04 plastic systemd-sleep[2917]: Entering sleep state 'suspend'...
Oct 02 19:39:04 plastic systemd[1]: grub-common.service: Deactivated successfully.
Oct 02 19:39:04 plastic systemd[1]: Finished Record successful boot for GRUB.

```

On this system both S0 and S3 states were available but S0 was selected as a default:

```

copter@plastic:~$ cat /sys/power/mem_sleep 

[s2idle] deep

```

What is interesting is that on another laptop with Xubuntu 20.04.5 LTS, mem_sleep also returned s2idle but the system seemed to correctly suspend into S3.

The fix was to change mem_sleep to deep (through sudo / root):

```

root@plastic:~# cat /sys/power/mem_sleep 

[s2idle] deep

root@plastic:~# echo "deep" > /sys/power/mem_sleep

root@plastic:~# cat /sys/power/mem_sleep 

s2idle [deep]

```

To persist this setting I have created a script in root's home:

```

root@plastic:~# cat /root/fix-sleep.sh 

#!/bin/bash

echo "deep" > /sys/power/mem_sleep
logger "fix-sleep mem sleep: $(cat /sys/power/mem_sleep)"

find /sys/bus/usb/devices/*/power/wakeup -exec sh -c "echo disabled > {}" \;

grep . /sys/bus/usb/devices/*/power/wakeup | while read -r line ; do    
    logger "fix-sleep usb wakeup: $line"
done

```
```

root@plastic:~# chmod +x /root/fix-sleep.sh 

root@plastic:~# ls -l /root/fix-sleep.sh 

-rwxr-xr-x 1 root root 216 Oct  2 21:34 /root/fix-sleep.sh

```

This script is doing few things. It sets deep sleep mode and logs the information in system log. Additionally it disables all USB devices from waking up the computer from sleep. In my case it addressed an annoying issue as moving a mouse cause the system resume.

Next thing to do is to call this script on system startup. For sake of simplicity I decided to use crontab for that. As a **root** user edit the crontab with the following command

```

root@plastic:~# crontab -e

```

Add the following line at the end

```

@reboot /root/fix-sleep.sh

```

To verify that the script is actually called during the startup, execute this command (as any user):

```

copter@plastic:~$ journalctl | grep fix-sleep

Oct 02 21:34:10 plastic root[6433]: fix-sleep mem sleep: s2idle [deep]
Oct 02 21:34:10 plastic root[6436]: fix-sleep usb wakeup: /sys/bus/usb/devices/1-10/power/wakeup:disabled
Oct 02 21:34:10 plastic root[6437]: fix-sleep usb wakeup: /sys/bus/usb/devices/1-5/power/wakeup:disabled
Oct 02 21:34:10 plastic root[6438]: fix-sleep usb wakeup: /sys/bus/usb/devices/1-7/power/wakeup:disabled
Oct 02 21:34:10 plastic root[6439]: fix-sleep usb wakeup: /sys/bus/usb/devices/usb1/power/wakeup:disabled
Oct 02 21:34:10 plastic root[6440]: fix-sleep usb wakeup: /sys/bus/usb/devices/usb2/power/wakeup:disabled

```

For testing, after resuming from suspend execute this command. You should see "suspend entry (deep)":

```

copter@plastic:~$ journalctl | grep -C 2 suspend

Oct 02 19:40:06 plastic systemd[1]: Starting Record successful boot for GRUB...
Oct 02 19:40:06 plastic systemd[1]: Starting System Suspend...
Oct 02 19:40:06 plastic systemd-sleep[3154]: Entering sleep state 'suspend'...
Oct 02 19:40:06 plastic kernel: PM: suspend entry (deep)
Oct 02 19:40:06 plastic systemd[1]: grub-common.service: Deactivated successfully.
Oct 02 19:40:06 plastic systemd[1]: Finished Record successful boot for GRUB.

```

To verify that the fans were properly stopped I used the stress tool. It is available in the repository.

```

copter@plastic:~$ sudo apt install stress

```

The following commands results in 100% CPU usage on 4 physical cores. It can be stopped with CTRL-C.

```

copter@plastic:~$ stress --cpu 4

stress: info: [3762] dispatching hogs: 4 cpu, 0 io, 0 vm, 0 hdd

```

You should hear the noise from fans in few seconds. After they are quite loud close the lid or suspend the computer through the menu button. If the fans completely stop in about 5 seconds, then you are in the deep sleep state (S3, suspend to RAM). If the fans continue to spin and will gradually slow down within 1-10 minutes, then most likely you are in S0 state. Let me know and we will try to figure it out together :)

If you have also problems with screen locking and screen saver, install light locker:

```

copter@plastic:~$ sudo apt install light-locker

```

In my case, default screen locking through xfce4-screensaver resulted in blank screen and no password prompt after resume. It worked just fine with light locker.

Good luck!

---

### Post by ccerrillo on 2023-07-09
You solved my day! Thanks!

---

### Post by julius-nepos on 2023-08-28
Running xUbuntu LTS 22.04 on a HP Xenon server.  When my system enters sleep mode, I can't wake it up.  Doesn't respond to keyboard nor mouse.  Only way is to pull the plug and reboot the computer losing all data & everything it's been working on.

This is absolutely unworkable for a computer server that has to process jobs that take longer than the sleep timeout.  System power saving has a maximum time of 5hr 50 min which means it should go to sleep during the night.

---

### Post by #&amp;thj^% on 2023-08-28
To change this setting temporarily:
```
sudo su
echo deep > /sys/power/mem_sleep
```
Test that for some time, and if happy, then make this change permanent, you can pass a setting to the Grub bootloader
```
sudo nano /etc/default/grub
```
add this:
```
mem_sleep_default=deep
```
on mine it looks like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash mem_sleep_default=deep"
```
And don't forget to tell grub about the change.
```
sudo update-grub
```
Good Luck

---

### Post by julius-nepos on 2023-08-28
Being tested now...  tks!

---

### Post by julius-nepos on 2023-08-30
Hi & tks,

Tried your recommendations for sleep mode but they didn't work.
Also edited grub and did the update but no dice.

One this I may try is that my Linux PC uses a Nvidia NVS 510 graphics card w/ 4 mini-display port outlets.  Yet I'm using an old HDMI monitor with it.  I do have an Nvidia Display port monitor.  I'll make that the main display and see if it helps.

---

### Post by julius-nepos on 2023-08-30
also the whisker menu apparently has sleep functions.  Will see if any of these work...
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292670&stc=1[/IMG]

Does this control the sleep function?

---

### Post by julius-nepos on 2023-09-05
I plan to upgrade to 22.10 from 22.04 and see if that fixes the problem.  22.10 is said to be compatible with OpenFOAM CFD, but nothing is said about 23.04 (a non-LTR).

---

### Post by julius-nepos on 2023-09-06
I may have found a solution.  This problem affects recent Ubuntu distros for servers.  I'll quote from the the website:
[https://linux-tips.us/how-to-disable-sleep-and-hibernation-on-ubuntu-server/](https://linux-tips.us/how-to-disable-sleep-and-hibernation-on-ubuntu-server/)

> For some reason, Ubuntu Server comes with ‘power management’ enabled. 

It [Ubuntu server] was shutting itself down after periods of inactivity. This isn’t acceptable behavior for a device that’s meant to be running all the time.

I checked in my logs and I found entries like this one:
Apr 3 12:18:27 server systemd[1]: Reached target Sleep.

That was entirely unacceptable. I do not know why power management was installed, nor do I know why it was active by default. I merely know that it was and that I couldn’t have that behavior with a server, a device meant to be always powered on.

Once you have your terminal open, you’re to kill everything that has to do with suspend, sleep, or hybrid-sleep. It’s actually pretty easy. Start by opening said terminal, by pressing CTRL + ALT + T and then enter the following commands:


First, you mask ‘sleep.target‘:
```
sudo systemctl mask sleep.target

```
Then mask ‘suspend.target‘:
```
sudo systemctl mask suspend.target

```
And mask ‘hibernate.target‘:
```
sudo systemctl mask hibernate.target

```
Finally, mask ‘hybrid-sleep.target‘:
```
sudo systemctl mask hybrid-sleep.target

```
Later, should you change your mind, you can unmask them and that’ll enable them again. Just change ‘mask’ to ‘unmask’ and run the commands again. See? Pretty easy!


If you want, you can verify the efficacy. Simply use the following:


```
systemctl status sleep.target

```(You can change ‘sleep.target’ to one of the above services and check them individually.) 

Finally I should add that to make the changes permanent, once testing is complete, these commands can be added to grub.conf or to a seperate script file called upon startup.

---

### Post by willysantika on 2023-11-12
> **Copter said:**
> Hi.

It has been 11 years since my last post on Ubuntu Forums. I hope that someone still finds this information useful.

I had a problem with suspend on Acer Apire Vero laptop (i5 1155G7, Iris Xe) running Xubuntu 22.04.1 LTS with stock kernel (5.15.0-48-generic). It turned out that after closing the lid or clicking Menu - Logout - Suspend button the computer did not enter deep sleep mode. The processes were suspended but the fan was still running for a while. Leaving laptop unplugged in that state for 10 hours resulted in 11% of battery loss. According to the document below, the system was entering S0 state (s2idle). This is the "shallowest" of sleep modes. The processes are stopped but the power consumption is not reduced to minimum.

[https://www.kernel.org/doc/Documentation/power/states.txt](https://www.kernel.org/doc/Documentation/power/states.txt)

```

copter@plastic:~$ journalctl | grep -C 2 suspend

Oct 02 19:39:04 plastic systemd[1]: Starting Record successful boot for GRUB...
Oct 02 19:39:04 plastic systemd[1]: Starting System Suspend...
Oct 02 19:39:04 plastic kernel: PM: suspend entry (s2idle)
Oct 02 19:39:04 plastic systemd-sleep[2917]: Entering sleep state 'suspend'...
Oct 02 19:39:04 plastic systemd[1]: grub-common.service: Deactivated successfully.
Oct 02 19:39:04 plastic systemd[1]: Finished Record successful boot for GRUB.

```

On this system both S0 and S3 states were available but S0 was selected as a default:

```

copter@plastic:~$ cat /sys/power/mem_sleep 

[s2idle] deep

```

What is interesting is that on another laptop with Xubuntu 20.04.5 LTS, mem_sleep also returned s2idle but the system seemed to correctly suspend into S3.

The fix was to change mem_sleep to deep (through sudo / root):

```

root@plastic:~# cat /sys/power/mem_sleep 

[s2idle] deep

root@plastic:~# echo "deep" > /sys/power/mem_sleep

root@plastic:~# cat /sys/power/mem_sleep 

s2idle [deep]

```

To persist this setting I have created a script in root's home:

```

root@plastic:~# cat /root/fix-sleep.sh 

#!/bin/bash

echo "deep" > /sys/power/mem_sleep
logger "fix-sleep mem sleep: $(cat /sys/power/mem_sleep)"

find /sys/bus/usb/devices/*/power/wakeup -exec sh -c "echo disabled > {}" \;

grep . /sys/bus/usb/devices/*/power/wakeup | while read -r line ; do    
    logger "fix-sleep usb wakeup: $line"
done

```
```

root@plastic:~# chmod +x /root/fix-sleep.sh 

root@plastic:~# ls -l /root/fix-sleep.sh 

-rwxr-xr-x 1 root root 216 Oct  2 21:34 /root/fix-sleep.sh

```

This script is doing few things. It sets deep sleep mode and logs the information in system log. Additionally it disables all USB devices from waking up the computer from sleep. In my case it addressed an annoying issue as moving a mouse cause the system resume.

Next thing to do is to call this script on system startup. For sake of simplicity I decided to use crontab for that. As a **root** user edit the crontab with the following command

```

root@plastic:~# crontab -e

```

Add the following line at the end

```

@reboot /root/fix-sleep.sh

```

To verify that the script is actually called during the startup, execute this command (as any user):

```

copter@plastic:~$ journalctl | grep fix-sleep

Oct 02 21:34:10 plastic root[6433]: fix-sleep mem sleep: s2idle [deep]
Oct 02 21:34:10 plastic root[6436]: fix-sleep usb wakeup: /sys/bus/usb/devices/1-10/power/wakeup:disabled
Oct 02 21:34:10 plastic root[6437]: fix-sleep usb wakeup: /sys/bus/usb/devices/1-5/power/wakeup:disabled
Oct 02 21:34:10 plastic root[6438]: fix-sleep usb wakeup: /sys/bus/usb/devices/1-7/power/wakeup:disabled
Oct 02 21:34:10 plastic root[6439]: fix-sleep usb wakeup: /sys/bus/usb/devices/usb1/power/wakeup:disabled
Oct 02 21:34:10 plastic root[6440]: fix-sleep usb wakeup: /sys/bus/usb/devices/usb2/power/wakeup:disabled

```

For testing, after resuming from suspend execute this command. You should see "suspend entry (deep)":

```

copter@plastic:~$ journalctl | grep -C 2 suspend

Oct 02 19:40:06 plastic systemd[1]: Starting Record successful boot for GRUB...
Oct 02 19:40:06 plastic systemd[1]: Starting System Suspend...
Oct 02 19:40:06 plastic systemd-sleep[3154]: Entering sleep state 'suspend'...
Oct 02 19:40:06 plastic kernel: PM: suspend entry (deep)
Oct 02 19:40:06 plastic systemd[1]: grub-common.service: Deactivated successfully.
Oct 02 19:40:06 plastic systemd[1]: Finished Record successful boot for GRUB.

```

To verify that the fans were properly stopped I used the stress tool. It is available in the repository.

```

copter@plastic:~$ sudo apt install stress

```

The following commands results in 100% CPU usage on 4 physical cores. It can be stopped with CTRL-C.

```

copter@plastic:~$ stress --cpu 4

stress: info: [3762] dispatching hogs: 4 cpu, 0 io, 0 vm, 0 hdd

```

You should hear the noise from fans in few seconds. After they are quite loud close the lid or suspend the computer through the menu button. If the fans completely stop in about 5 seconds, then you are in the deep sleep state (S3, suspend to RAM). If the fans continue to spin and will gradually slow down within 1-10 minutes, then most likely you are in S0 state. Let me know and we will try to figure it out together :)

If you have also problems with screen locking and screen saver, install light locker:

```

copter@plastic:~$ sudo apt install light-locker

```

In my case, default screen locking through xfce4-screensaver resulted in blank screen and no password prompt after resume. It worked just fine with light locker.

Good luck!

Hi, thanks for the tutorial and sorry for my bad english. But i have a problem. When i tried this, the sleep works very well with closing lid and by clicking suspend on menu. But when i try to resume by opening the lid, the laptop turned on, the fan spinning, but nothing on the screen. I also have installed light-locker as suggested. Is there something wrong with my settings? Thanks for the help.

---

