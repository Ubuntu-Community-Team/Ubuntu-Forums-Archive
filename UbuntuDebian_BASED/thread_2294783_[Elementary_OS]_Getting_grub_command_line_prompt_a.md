---
title: "[Elementary OS] Getting grub command line prompt after new install"
date: 2015-09-13
forum: Ubuntu/Debian BASED
---

### Post by calum4 on 2015-09-13
I completely formatted my hard drive and performed a full install of Elementary OS from USB. Whenever I rebooted my computer I am met by the Grub2 command line. I have worked out that I can boot using the following code:
```
grub>  set boot=(hd0,gpt2)
grub>  set prefix=(hd0,gpt2)/boot/grub
grub>  insmod normal  
grub>  normal 
```

I then try to fix grub by using the following code (upon load)

```
sudo grub-install /dev/sda 
sudo grub-update

```

But the same thing happens every time I reboot.

How can i avoid this and boot straight to Elementary?

Thank you for any help.

---

### Post by howefield on 2015-09-13
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by westie457 on 2015-09-13
Do you get a command not found  output when using the command 'sudo grub-update' ?

Instead try ```
sudo update-grub
```followed by ```
sudo reboot
```

You should now be booting as normal.

---

### Post by calum4 on 2015-09-13
When i try: ```
sudo grub-install /dev/sda
```

I receive this error: ```
error ../../..modinfo.sh doesn't exist
```

When I ```
sudo grub-update
``` two linux and two initrd images are found (xx-3.19.0-28-generic and xx-3.19-0.26-generic)

---

### Post by calum4 on 2015-09-13
Any help?

---

### Post by for_alderaan on 2015-09-24
For what it's worth, I'm having the exact same issue with the latest version of Elementary (Freya). The install completes successfully, but, upon reboot, I'm greeted by the Grub2 terminal. 

Everything seems fine in the various grub files, but the settings aren't getting picked up on boot for some reason.

---

### Post by osocron on 2015-10-17
After doing the steps that calum4 showed in the grub prompt I was able to log into Elementary and from there I was able to correct the problem by installing boot-repair and running it with the option to purge grub. This option is found on advanced settings. Hope it helps somebody.

---

### Post by mpt2 on 2015-11-15
Thanks everyone for their input! Was having the same "Boot to Grub terminal after installing Elementary OS as dual boot with Windows 10" issue and these steps resolved the issue:

- From the grub 2 terminal, since in my case the /home partition was gpt5, I typed:
```
grub>  set boot=(hd0,gpt5)
grub>  set prefix=(hd0,gpt5)/boot/grub
grub>  insmod normal  
grub>  normal
```

This booted to Elementary OS where I tried fixing grub:
```
sudo grub-install /dev/sda 
sudo grub-update
```

Following that, installed boot-repair as osocron suggested, making sure to choose the advanced option to "purge grub". Didn't change anything else within the advanced options:
```
sudo apt-add-repository ppa:yannubuntu/boot-repair
sudo apt-add update
sudo apt-add install boot-repair -y && boot-repair
```

One more restart, and booted automatically to windows once more, where I followed boot-repair's suggestion to 

> [FONT=arial]type the following command in an admin command prompt:
[/FONT][FONT=arial]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi[/FONT]
I started the cmd with "Run as administrator.." just to be sure ;)

Final restart and booted into grub2 with all the options for Elementary and Windows :)

---

