---
title: "Pop! OS - install GRUB bootloader"
date: 2020-03-06
forum: Ubuntu/Debian BASED
---

### Post by pianoguy628 on 2020-03-06
Would anyone know how to install the GRUB bootloader on Pop! OS? I know Pop! OS doesn't use it by default, but I really want to use it. Would anyone know how to do it?

---

### Post by yancek on 2020-03-07
Pop OS is another Ubuntu derivative so the method would be the same as installing or re-installing Grub2 on Ubuntu.  Get it from the repositories and install.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by oldfred on 2020-03-07
Pop is using SystemD boot which was Gummiboot before 2015.
It has more of the boot in the ESP and I believe kernel is in ESP.

It may be easier to use Boot-Repair and its advanced options. 
You can check full install of grub and newest kernel, so you have kernel in /boot.
Otherwise you have to move some of the boot files back from ESP to /boot.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by pianoguy628 on 2020-03-07
Which kernel should I install?

---

### Post by pianoguy628 on 2020-03-07
Also, I'm trying to use grub customizer, but I keep getting an "out of memory" error or something like that.

---

### Post by jeremy31 on 2020-03-07
Post results for ```
df -h
```

---

### Post by pianoguy628 on 2020-03-07
Filesystem      Size  Used Avail Use% Mounted on
udev            1.7G     0  1.7G   0% /dev
tmpfs           352M  1.8M  350M   1% /run
/dev/sda4        49G  7.5G   39G  17% /
tmpfs           1.8G   58M  1.7G   4% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           1.8G     0  1.8G   0% /sys/fs/cgroup
/dev/sda5        98G  3.4G   90G   4% /home
/dev/sda1       775M  216M  559M  28% /boot/efi
tmpfs           352M   16K  352M   1% /run/user/120
tmpfs           352M   52K  352M   1% /run/user/1000



Also, when booting into GRUB, it keeps booting into the command line. I imagine the GRUB EFI file just needs updated, but I can't, as GRUB Customizer is spitting out that error.

---

### Post by oldfred on 2020-03-07
Post the link to a summary report from Boot-Repair.
Not sure if it searches for gummi-boot files or not. Part of report has not been updated for several years (bootinfoscript).

---

### Post by pianoguy628 on 2020-03-07
[https://paste.ubuntu.com/p/GPNh68Tn6X/](https://paste.ubuntu.com/p/GPNh68Tn6X/)

---

### Post by jeremy31 on 2020-03-07
Is this a newer HP laptop?  You may have to go into UEFI/BIOS settings, System Config, OS Boot Loader, put ubuntu on top of the list and press F10 twice

---

### Post by pianoguy628 on 2020-03-07
> **jeremy31 said:**
> Is this a newer HP laptop?  You may have to go into UEFI/BIOS settings, System Config, OS Boot Loader, put ubuntu on top of the list and press F10 twice

Yes, it's an HP laptop I bought a year ago. I don't believe I can choose the OS boot order, just the order of the drives from which my PC boots(e.g. HDD, then USB, then disk, etc.). 

What about the issue with it booting to the command line in GRUB(when I manually boot to the GRUB EFI file)?

---

### Post by jeremy31 on 2020-03-07
Try ```
sudo efibootmgr -n 0000
```
Reboot and see if grub shows up, if it doesn't you will have to find the Boot manager settings in System Config.  The HP I bought last December is that way, the EFI refuses to accept updates from an OS as far as boot order

---

### Post by oldfred on 2020-03-07
I am not seeing a grub.cfg in sda4. If that is missing that could be the issue. It should have been created when grub was installed.

Try manual boot from grub.
If at grub>
grub> set root=(hd0,4)
grub> linux /vmlinuz root=/dev/sda4
grub> initrd /initrd.img
grub> boot


You need to turn Windows fast start up off. It is giving errors on that.
You have have multiple duplicate UEFI entries that you can delete with efibootmgr.
See lines 395 & up.

You have have multiple copies of Boot-Repair in your ESP, only need last one.
See line 33.

Do not use grub customizer. It creates copies of grub and confused everything.

---

### Post by yancek on 2020-03-07
> I don't believe I can choose the OS boot order, just the order of the  drives from which my PC boots(e.g. HDD, then USB, then disk, etc.).  

Not sure that your HP is the same as mine which shows a message on boot to hit the Esc key to pause boot.  When you get that, the screen will then show several options including using the F9 key to access boot options for a one time selection and using the F10 key for permanent changes.  In either case, you should be able to see the various options that you see in boot repair from the output of efibootmgr, lines 388-403.  Line 392 shows and Ubuntu entry and Line 400 shows PopOS.  You should be able to access any of these.  If you don't have the same option, you just need to watch the screen on boot to get the correct keys.

Of course, selecting one of these options isn't necessarily going to boot that OS as you will need the correct boot file in EFI and system partitions which don't seem to be present.

---

### Post by pianoguy628 on 2020-03-07
> **jeremy31 said:**
> Try ```
sudo efibootmgr -n 0000
```
Reboot and see if grub shows up, if it doesn't you will have to find the Boot manager settings in System Config.  The HP I bought last December is that way, the EFI refuses to accept updates from an OS as far as boot order

where would I find that?

---

### Post by pianoguy628 on 2020-03-07
> **yancek said:**
> Not sure that your HP is the same as mine which shows a message on boot to hit the Esc key to pause boot.  When you get that, the screen will then show several options including using the F9 key to access boot options for a one time selection and using the F10 key for permanent changes.  In either case, you should be able to see the various options that you see in boot repair from the output of efibootmgr, lines 388-403.  Line 392 shows and Ubuntu entry and Line 400 shows PopOS.  You should be able to access any of these.  If you don't have the same option, you just need to watch the screen on boot to get the correct keys.

Of course, selecting one of these options isn't necessarily going to boot that OS as you will need the correct boot file in EFI and system partitions which don't seem to be present.

Oh yeah, I see those. Sorry, I was thinking of it incorrectly.

---

### Post by pianoguy628 on 2020-03-07
> **oldfred said:**
> I am not seeing a grub.cfg in sda4. If that is missing that could be the issue. It should have been created when grub was installed.

Try manual boot from grub.
If at grub>
grub> set root=(hd0,4)
grub> linux /vmlinuz root=/dev/sda4
grub> initrd /initrd.img
grub> boot


You need to turn Windows fast start up off. It is giving errors on that.
You have have multiple duplicate UEFI entries that you can delete with efibootmgr.
See lines 395 & up.

You have have multiple copies of Boot-Repair in your ESP, only need last one.
See line 33.

Do not use grub customizer. It creates copies of grub and confused everything.

On the vmlinuz cmd, I'm getting an error that says "file '/vmlinuz' not found"

---

### Post by pianoguy628 on 2020-03-07
> **jeremy31 said:**
> Try ```
sudo efibootmgr -n 0000
```
Reboot and see if grub shows up, if it doesn't you will have to find the Boot manager settings in System Config.  The HP I bought last December is that way, the EFI refuses to accept updates from an OS as far as boot order



Grub still isn't showing up by default, systemd is. 

Also, I got it to boot to systemd by renaming it to the same name as the Microsoft efi(can't remember the name off the top of my head), and then placing it in the folder where the Microsoft efi file is usually located. I plan on doing it with the grub efi to boot to grub, but I'm waiting untill I can see a grub menu, and not just a command line.

---

### Post by oldfred on 2020-03-07
It seems that grub is not fully installed.
How did you install it?
Did you use Boot-Repair's advanced options & check to include the latest kernel?
You will need those files to boot.

---

### Post by pianoguy628 on 2020-03-08
> **oldfred said:**
> It seems that grub is not fully installed.
How did you install it?
Did you use Boot-Repair's advanced options & check to include the latest kernel?
You will need those files to boot.

Which kernel do I choose in boot repair?

---

### Post by oldfred on 2020-03-08
I thought it only gave a choice of purge & install latest. See grub options.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by pianoguy628 on 2020-03-08
> **oldfred said:**
> I thought it only gave a choice of purge & install latest. See grub options.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I'm looking at the 'add a kernel option' switch. Is that the wrong thing?

---

### Post by oldfred on 2020-03-08
Unless you also need boot options, you would not add a switch.
And I think that adds permanent settings which are only required in a few cases.
Most often you need a one time setting when booting & edit grub as you boot.

---

### Post by pianoguy628 on 2020-03-12
> **oldfred said:**
> Unless you also need boot options, you would not add a switch.
And I think that adds permanent settings which are only required in a few cases.
Most often you need a one time setting when booting & edit grub as you boot.

I'm confused on what to do. Could you tell me what all the controls need to be set to in boot repair so I do it right?

---

### Post by pianoguy628 on 2020-03-12
> **oldfred said:**
> I am not seeing a grub.cfg in sda4. If that is missing that could be the issue. It should have been created when grub was installed.

Try manual boot from grub.
If at grub>
grub> set root=(hd0,4)
grub> linux /vmlinuz root=/dev/sda4
grub> initrd /initrd.img
grub> boot


You need to turn Windows fast start up off. It is giving errors on that.
You have have multiple duplicate UEFI entries that you can delete with efibootmgr.
See lines 395 & up.

You have have multiple copies of Boot-Repair in your ESP, only need last one.
See line 33.

Do not use grub customizer. It creates copies of grub and confused everything.


Is *efibootmgr* the tool to use to make my PC boot to GRUB first, and not Windows(via putting GRUB's entry before Windows)?

That's completely unrelated to my issue, just wondering for reference.

---

### Post by oldfred on 2020-03-12
Post this:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok. Example:
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

To get reinstall of grub, you have to check the purge grub. And to get new kernels  (in the right place) you have to install those.

---

### Post by pianoguy628 on 2020-03-12
> **oldfred said:**
> Post this:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok. Example:
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

To get reinstall of grub, you have to check the purge grub. And to get new kernels  (in the right place) you have to install those.


K, that's all good, but how do I fix the grub customizer error? I need to update the grub config file, but I can't, 'cause grub customizer won't work...

---

### Post by pianoguy628 on 2020-03-14
I have finally given up, and have decided to switch to Manjaro. I know it's got some new stuff I'll have to learn, but it just seems to do everything Pop/Ubuntu can, and in some areas better. Just wanted to let you guys know.

---

