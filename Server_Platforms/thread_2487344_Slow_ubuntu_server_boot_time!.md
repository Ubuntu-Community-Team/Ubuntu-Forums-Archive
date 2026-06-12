---
title: "Slow ubuntu server boot time!"
date: 2023-05-31
forum: Server Platforms
---

### Post by eminescu on 2023-05-31
[COLOR=#ff0000][B]Ubuntu 20.04 webserver
Platforms : Webmin/Virtualmin
Hardware: i5-4570 + 8gb ram and 1 SSD[/B][/COLOR]

I had installed OpenMediaVault at some point on server and i purged it and removed ssd with the openmedia vault.
I think boot time is affected by this.
Here are some commands from logs:

```
systemd-analyze time
```
```
Startup finished in 5.827s (firmware) + 2.794s (loader) + 3.302s (kernel) + 1min 40.095s (userspace) = 1min 52.019s
graphical.target reached after 1min 39.551s in userspace
```

[B]A normal boot time is less then 25 seconds for my server, however it takes over 2min to load webserver platform from virtualmin.
[/B]
```
sudo nano /etc/fstab
```

> # /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/ubuntu-lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-CJuruIAJZ5Q4ZkBVfCqAwkGKk2ZIm32RCgDjKUKm1sYS3TRzwtOQyPyeFc3HBDR0 / ext4 defaults 0 1
# /boot was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/205cf80c-fb9e-473a-82d6-25329a34e693 /boot ext4 defaults 0 1
# /boot/efi was on /dev/sda1 during curtin installation
/dev/disk/by-uuid/26BE-A316 /boot/efi vfat defaults 0 1
# /home was on /dev/ubuntu-vg/lv-0 during curtin installation
/dev/disk/by-id/dm-uuid-LVM-CJuruIAJZ5Q4ZkBVfCqAwkGKk2ZIm32R3790Nfb6JxUmVgpjlxJwhtuwqXnJ9vDS    /home   ext4    usrquota,grpquota,quota,rw,relatime     0       1
/swap.img       none    swap    sw      0       0
LABEL=myvault   /home/myvault   ext4    defaults        0       0
/dev/sda5       /free   ext3    defaults        0       0



```
sudo blkid -o listdevice 
```

> root@ns2:/# sudo blkid -o listdevice                                                   fs_type         label            mount point                                                  UUID
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                                     vfat                               /boot/efi                                                         26BE-A316
/dev/sda2                                                     ext4                               /boot                                                             205cf80c-fb9e-473a-82d6-25329a34e693
/dev/sda3                                                     LVM2_member                        (in use)                                                          xSawZN-We9k-jleS-QCAB-nRRB-sAKr-8a3Qnd
/dev/sda5                                                     ext3                               /free                                                             53e83fc3-d397-4021-a00e-a4bc4360ba45
/dev/mapper/ubuntu--vg-ubuntu--lv                             ext4                               /                                                                 cb9e6bda-3cf2-426c-bb17-e2978292f8aa
/dev/mapper/ubuntu--vg-lv--0                                  ext4                               /home                                                             fd9bce36-259b-4012-960c-d352934d2af1
/dev/loop0                                                    squashfs                           /snap/core20/1879
/dev/loop1                                                    squashfs                           /snap/lxd/23991
/dev/loop2                                                    squashfs                           /snap/core20/1891
/dev/loop3                                                    squashfs                           /snap/snapd/18933
/dev/loop4                                                    squashfs                           /snap/lxd/24061
/dev/loop5              

```
systemd-analyze critical-chain
```

> The time when unit became active or started is printed after the "@" character.The time the unit took to start is printed after the "+" character.


graphical.target @1min 39.551s
&#9492;&#9472;multi-user.target @1min 39.551s
  &#9492;&#9472;postfix.service @1min 39.548s +1ms
    &#9492;&#9472;postfix@-.service @1min 37.427s +2.120s
      &#9492;&#9472;network-online.target @1min 37.407s
        &#9492;&#9472;systemd-networkd-wait-online.service @1min 32.257s +5.148s
          &#9492;&#9472;systemd-networkd.service @1min 32.196s +59ms
            &#9492;&#9472;network-pre.target @1min 32.195s
              &#9492;&#9472;firewalld.service @1min 31.788s +406ms
                &#9492;&#9472;polkit.service @1min 31.310s +475ms
                  &#9492;&#9472;basic.target @1min 31.281s
                    &#9492;&#9472;sockets.target @1min 31.281s
                      &#9492;&#9472;uuidd.socket @1min 31.281s
                        &#9492;&#9472;sysinit.target @1min 31.273s
                          &#9492;&#9472;cloud-init-local.service @1min 30.522s +751ms
                            &#9492;&#9472;systemd-remount-fs.service @454ms +11ms
                              &#9492;&#9472;systemd-journald.socket @439ms
                                &#9492;&#9472;system.slice @435ms
                                  &#9492;&#9472;-.slice @435ms
**[COLOR=#ff0000]*Weird jump from remount fs service from 454 ms to cloud-init-local.service at 1min30sec*[/COLOR]**


[B]I cannot play with server because i have some websites active, so i don't want to make mistakes.
Can someone help me with fixing partitions, or at least is what i think it is?[/B]

---

### Post by MAFoElffen on 2023-05-31
cloud-init has no purpose after the initial install, unless you have something external connected to that, that you use for updates and/or patches.

What I would do first is to disable 'cloud-init'...
RE: [https://cloudinit.readthedocs.io/en/latest/howto/disable_cloud_init.html](https://cloudinit.readthedocs.io/en/latest/howto/disable_cloud_init.html)
To disable cloud-init, create the empty file /etc/cloud/cloud-init.disabled. During boot the operating system&#8217;s init system will check for the existence of this file. If it exists, cloud-init will not be started. 

Example:
```

$ touch /etc/cloud/cloud-init.disabled

```
[quote]
Then do
```

sudo nano /etc/default/grub

```
and add/insert 'cloud-init=disabled' to the GRUB_CMDLINE_LINUX_DEFAULT= line boot options.

Save. exit, then pick up the changes with 
```

update-grub

```
I also add optional= yes' to the interfaces in my /etc/netplan/*.yaml file, so that they don't have to wait on the default networking job for the devices to be up until it continues... That is annoying.

Then let's see what is left over as taking too long, with (attach to a post)
```

systemd-analyze plot > /tmp/blame.svg

```

---

### Post by eminescu on 2023-06-01
Thanks!
I hope i didn't missunderstood something. Regarding **[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT= line boot options, [/COLOR]**[COLOR=#000000]I didn't knew the last part with line boot options what to do with it?[/COLOR]
This is how i edited cloud.init
> 

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT='cloud-init=disabled'
GRUB_CMDLINE_LINUX=""




My netplan is set as static ip

> root@ns2:/etc/netplan# nano 00-installer-config.yaml  GNU nano 4.8                00-installer-config.yaml
network:
  ethernets:
    enp0s25:
      addresses: [192.168.1.78/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.4.4, 8.8.8.8]
  version: 2




When i hit that command [HTML]systemd-analyze plot > /tmp/blame.svg[/HTML]
Nothing happens and when i hit only "[COLOR=#000000][FONT=&amp]systemd-analyze plot" it shows a large text class in putty[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-06-01
The re-direcion symbol redirects the output to a file, which you would then find at /tmp/blame.svg...

Since you are doing ssh, you might have to use scp to transfer that file to your local computer.

Upload that file as an attachment to a post. The Forum accepts that format of graphics files.

---

### Post by eminescu on 2023-06-01
Thanks!
I found the culprit finally, it was so horrible to restart server in the past 6 months. 
The issue was this line in fstab [B]"[COLOR=#000000]*LABEL=myvault /home/myvault ext4 defaults 0 0*[/COLOR]
[COLOR=#000000][I]/dev/sda5 /free ext3 defaults 0 0"
[/I][/COLOR][/B][COLOR=#000000][I]I commented it out and from almost 3 minutes of boot times and sometimes even freezes loops after boot i get under 20 seconds boot time.
Now i remember that i named partition for openmediavault myvault. Someone on "Ask Ubuntu" pointed to me the issue.[/I][/COLOR]

---

### Post by MAFoElffen on 2023-06-01
Happy that you found the problem! LOL

If "solved", please remember to use the Thread Tools link to mark it as that, so that others may find your solution.

---

### Post by ryomario on 2023-09-25
I just type ```
systemd-analyze blame
``` and see what services take a whole time then I disable it using ```
sudo systemctl disable <service name>
```. If "disable" still do not working I will force disable it by ```
sudo systemctl mask <service name>
```
> replace <service name> with the service name that will be disabled

---

