---
title: "Clean install ubuntu16 Oryx Pro cannot boot"
date: 2018-02-10
forum: System76 Support
---

### Post by tensorflower on 2018-02-10
I bought a new Oryx Pro 17 inch a few weeks ago and I did a clean install (wipe out whole disk) with a bootable USB that installs ubuntu16 created from Ubuntu's startup disk creator. I follow the official instruction here [https://github.com/system76/docs/blob/gh-pages/_articles/install-ubuntu.md](https://github.com/system76/docs/blob/gh-pages/_articles/install-ubuntu.md) I didn't run into any Nvidia driver issue.

The installation is complete, I saw the message that asks me to remove installation media and press enter, I did and my machine does not boot. The screen shows nothing except the pinkish background colour (no text no nothing). The troubling thing is when I boot with my USB installation media and press F1/F7, it also doesn't boot. Desperate help needed please!!!!! I spend more than 2000USD on this thing and it doesn't boot now.

Extra info if needed: I use it for deep learning purposes. I installed Nvidia CUDA8.0 before. Just in case it may interfere with my boot up somehow.

---

### Post by tensorflower on 2018-02-12
[SIZE=2][COLOR=#574F4A][FONT=&amp]I reboot the system and tap ESC to get into the GRUB bootup menu. I then chose 'Advanced options for Ubuntu' and c[/FONT][/COLOR][COLOR=#574F4A][FONT=&amp]hose (recovery mode) on the newest listed kernel. I then c[/FONT][/COLOR][COLOR=#574F4A][FONT=&amp]hose 'network',[/FONT][/COLOR][COLOR=#574F4A][FONT=&amp] 'dpkg',[/FONT][/COLOR][COLOR=#574F4A][FONT=&amp] 'grub', [/FONT][/COLOR][COLOR=#574F4A][FONT=&amp]'root', which led me to terminal. 
[/FONT][/COLOR][COLOR=#574F4A][FONT=&amp]
I then follow this link [/FONT][/COLOR]http://support.system76.com/articles/grub/ to repair grub boot loader.[COLOR=#574F4A][FONT=&amp]

[/FONT][/COLOR][COLOR=#403A36][FONT=&amp]sudo parted -ls[/FONT][/COLOR][COLOR=#574F4A][FONT=&amp]

[/FONT][/COLOR][FONT=System76 Ubuntu Mono][COLOR=#403a36]sudo mkdir -p /mnt/boot/efi
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot/efi
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done[/COLOR][/FONT]
[FONT=System76 Ubuntu Mono][COLOR=#403a36]sudo cp /etc/resolv.conf /mnt/etc/
This sudo cp /etc/resolv.conf /mnt/etc is where my command failed. Because /etc/resolv.conf is a broken soft link to [/COLOR][/FONT][COLOR=#574F4A][FONT=&amp]../run/resolvconf/resolv.conf. I checked /run/resolvconf, resolv.conf doesn't exist. The thing is in /mnt/etc/, resolv.conf already exists, it is a soft link to ../runresolvconf/resolv.conf, with the absolute path /mnt/run/resolvconf/resolv.conf, which is empty.[/FONT][/COLOR]

[FONT=System76 Ubuntu Mono][COLOR=#403a36]Because of the failure, the apt install cannot fetch packages.[/COLOR][/FONT]
[FONT=System76 Ubuntu Mono][COLOR=#403a36]sudo chroot /mntapt install --reinstall grub-efi-amd64 linux-generic linux-headers-generic

I still cannot boot.[/COLOR][/FONT][/SIZE]

---

### Post by monkeybrain20122 on 2018-02-13
Since you bought it yourself can you get support from system76? [http://support.system76.com/](http://support.system76.com/)

---

