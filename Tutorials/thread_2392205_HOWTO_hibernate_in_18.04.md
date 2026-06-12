---
title: "HOWTO hibernate in 18.04"
date: 2018-05-17
forum: Tutorials
---

### Post by s-breedveld on 2018-05-17
**Enabling hibernate in Ubuntu 18.04**

 This is one of the probably many ways to enable hibernate in Ubuntu. 

 Unfortunately, hibernate still does not work out-of-the-box. And while it is a highly desired feature for laptop users, there is also no easy way to switch it on. 

Here I will describe the steps which I needed to take to enable hibernate on my Lenovo ThinkPad E580, with Xubuntu 18.04.

I hope this will aid others in their hibernate quest.
  
 
 **Step 1: ****Secure Boot**
 Before doing anything with hibernate, something about secure boot: these two do not go well together. There is a plethora of reasons which I will not discuss here. There are 2 options: 1) disable secure boot in your BIOS, or 2) use a non-signed kernel.
 
 If you are dual-booting Windows with Ubuntu, disabling secure boot is annoying: Windows will not boot normally. Without secure boot, you will have to enter your Bitlocker decryption key on each boot. Alternatively, you will have to toggle the secure boot option for each switch between the operating systems.
 
 My solution: use a non-signed kernel. I am honestly not sure what the consequences are of using an unsigned kernel: I guess it completely disables the concept of &#8220;secure boot&#8221; for Linux, but otherwise we have to disable it anyway. Also: this works for my system, maybe this approach does not work on other systems. It is also disputed whether GRUB should allow booting unsigned kernels: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532)
 
 Either way, go to: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) where you can download &#8220;official&#8221; Ubuntu-build kernels. Pick one, download the deb files for you architecture (you can skip the -lowlatency ones), and install them using:
 ```

sudo dpkg -i *.deb
``` 
 
 Reboot.

 Check if hibernate is supported now by:
 ```

cat /sys/power/state
``` 
 
 If &#8220;disk&#8221; is one of them: congratulations! Step 1 achieved!
 
 
 
 **Step 2: ****E****nabling encrypted swap with fixed key**
 I prefer to write the state of my system to an encrypted disk: in case someone steals your laptop, your memory dump will not be readable. For this, we need to create an encrypted swap which can be unlocked by a fixed key, rather than a random key.
 
 For enabling encrypted swap, I followed this guide: [COLOR=#000080]_[https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap)_[/COLOR]
  
 Some details are different. For example, encrypted swap is not enabled by default anymore after installing Ubuntu. The steps I took are the following, please consult the link above for details on each step.
  
 **NOTE: MY SWAP PARITION WAS /dev/nvme0n1p7 CHECK THE OUTPUT OF THE FIRST COMMAND FOR YOUR LOCATION!**
```

swapon &#8211;summary # Check and record your swap partition
sudo swapoff -a
sudo cryptsetup luksFormat --cipher aes-xts-plain64 --verify-passphrase --key-size 256 /dev/nvme0n1p7
sudo cryptsetup luksOpen /dev/nvme0n1p7 cryptswap1
sudo mkswap /dev/mapper/cryptswap1
``` 

Now edit */etc/fstab*:
```

sudo nano -w /etc/fstab
```
and replace the original line with information on the swap parition with:
 ```

/dev/mapper/cryptswap1 none swap sw 0 0
``` 
 
 Save the file and continue with:
 ```

sudo swapon -a
``` 
 
 Then edit */etc/crypttab* and add the following line:
```

cryptswap1    /dev/nvme0n1p7    none    luks
``` 
 
 Also edit */etc/initramfs-tools/conf.d/resume* , and replace the existing line with:
```

RESUME=/dev/mapper/cryptswap1
``` 
 
 Finally, edit */etc/default/grub* and add:
```

resume=/dev/mapper/cryptswap1
```
to the GRUB_CMDLINE_LINUX_DEFAULT options.

 Now run:
```
[FONT=Liberation Serif][SIZE=3]
sudo update-initramfs -u -k all
sudo update-grub[/SIZE][/FONT]
```
to update grub.
 
 
 NOW REBOOT!

 When booting, the screen will ask you for your passphrase. If everything went well, the login-prompt will appear, and the encrypted swap is mounted (check with: *swapon &#8211;summary*).



 **Step 3: ****Test hibernate**
 You can now test if hibernate works. Issue:
 ```

sudo pm-hibernate
``` 
 and your system should go to sleep.
 
 
 If your system wakes up properly, resuming works!

 
 
 **Step 4: ****Enabling the option in the menu**
 Now that hibernate works, let&#8217;s integrate the functionality in the system, so you can access is from the menu.

 Edit or create: */etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla* with the following contents:
```

[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=yes

```

Depending on your window manager, the options are readily available or not. Rebooting is the easy option.
  


 **Step 5: Waking up problems**
 On some systems, resuming does not work properly. On my ThinkPad E580, I initially had 3 problems: the LAN adapter did not work, the Bluetooth connection at some point simply died, and I sometimes had a black screen after resume.
  
 These are 3 different problems.
  
 *Problem 1:*
 For the LAN adapter, unloading the module prior to hibernate and reloading on resume was sufficient. To achieve this, I followed this guide:  
  [https://ubuntuforums.org/showthread.php?t=2314905](https://ubuntuforums.org/showthread.php?t=2314905)
  
 My LAN module is the r8169, so I created a file */etc/suspend-modules.conf* with:
```
  
r8169

```
 
 [FONT=Liberation Serif][SIZE=3]Then create a file */lib/systemd/system-sleep/suspend-modules* with content:[/SIZE][/FONT]
```
  [FONT=Liberation Serif][SIZE=3]
#!/bin/bash[/SIZE][/FONT]

[FONT=Liberation Serif][SIZE=3]case $1 in[/SIZE][/FONT]
    [FONT=Liberation Serif][SIZE=3]pre)[/SIZE][/FONT]
        [FONT=Liberation Serif][SIZE=3]for mod in $(</etc/suspend-modules.conf); do[/SIZE][/FONT]
            [FONT=Liberation Serif][SIZE=3]modprobe -r $mod[/SIZE][/FONT]
        [FONT=Liberation Serif][SIZE=3]done[/SIZE][/FONT]
    [FONT=Liberation Serif][SIZE=3];;[/SIZE][/FONT]
    [FONT=Liberation Serif][SIZE=3]post)[/SIZE][/FONT]
        [FONT=Liberation Serif][SIZE=3]for mod in $(</etc/suspend-modules.conf); do[/SIZE][/FONT]
            [FONT=Liberation Serif][SIZE=3]modprobe $mod[/SIZE][/FONT]
        [FONT=Liberation Serif][SIZE=3]done[/SIZE][/FONT]
    [FONT=Liberation Serif][SIZE=3];;[/SIZE][/FONT]
[FONT=Liberation Serif][SIZE=3]esac[/SIZE][/FONT]
```[I][FONT=Liberation Serif][SIZE=3]

[/SIZE][/FONT][/I][FONT=Liberation Serif][SIZE=3]and make it executable:[/SIZE][/FONT]
```

sudo chmod a+x /lib/systemd/system-sleep/suspend-modules
```
 
 
*  Problem 2:*
  The other issue was a result from xHCI dying at some point, also resulting in disabling all USB devices. My* /var/log/syslog* showed these messages:
  
 
```

May 17 19:11:51 my kernel: [23775.839044] xhci_hcd 0000:00:14.0: xHC is not running.
May 17 19:11:51 my kernel: [23775.856855] xhci_hcd 0000:00:14.0: xHCI host controller not responding, assume dead
May 17 19:11:51 my kernel: [23775.856877] xhci_hcd 0000:00:14.0: HC died; cleaning up
```
  
  I figured out that I needed these options to my  GRUB_CMDLINE_LINUX_DEFAULT in */etc/default/grub* (see also this bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1413440](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1413440) ):
```

pci=nomsi iommu=soft
```
 and running
```

sudo update-grub
```
 This solved the problem for me.
 

 *Problem 3:*
Only when you are running the XFCE desktop (like with Xubuntu):
Sometimes, XFCE returns a black screen after logging in, mainly after resuming from suspend (see bug: [https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1431149](https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1431149) ).

The following command returns the XFCE desktop:
```
xfsettingsd --replace
```

which I added as a keyboard shortcut, so I could easily restore my desktop when needed.


 **Epilogue**
 Putting your computer to hibernate requires some effort, but is fairly straightforward. Waking-up problems are much harder to debug, and may have different sources/solutions.
 
 *Good luck!*

edit 1: added *update-grub* command for updating GRUB
edit 2: added XFCE resume bug fix

---

### Post by alanhorizon on 2019-01-13
This guide is really useful, especially all the commands, thinking process, debug process, which of the logs you used to investigate problems, etc. The most annoying part of linux stuff is the random seemingly unrelated things that fail (eg. your LAN or bluetooth dying, intermittently). So, thanks for the thorough instructions and investigation notes. I will be trying this out next weekend...

---

### Post by pranaypratyush on 2019-11-05
I followed all the above mentioned steps but still my screen just flashes when I do sudo pm-hibernate.

---

### Post by rochefort on 2020-01-03
This works, thanks. (HP 840 G3)

Is it possible to integrate hibernate into the Ubuntu options? I would like to make my laptop hibernate on time-out, instead of just standby.

---

