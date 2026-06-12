---
title: "Multiple EFI boot entries -&gt; change default"
date: 2024-11-29
forum: Ubuntu/Debian BASED
---

### Post by malonn2 on 2024-11-29
Hey all.  My Debian 12 install has two EFI options to choose from when I boot.  One is the "normal" boot.  The other (default) is some kind of "safe mode".  Simply: how can I tailor the default behavior of booting directly into "safe mode"/recovery desktop.  I hope to be able to do it strictly via the "grub" configuration file in /etc/default/.  I went though a drawn out ordeal with the efibootmgr command that was nothing more than a time drain (though I think I was on to a valid method).

---

### Post by Dennis N on 2024-11-30
> Hey all. My Debian 12 install has two EFI options to choose from when I boot.

Are you looking at the Grub menu? Or the EFI boot menu? The default grub menu for Debian 12 has three options:

```
Debian Gnu/Linux
Advanced Options for Debian GNU/Linux
UEFI Firmware Settings

```
There is no safe mode mentioned.

If it's the EFI boot menu, that is set in your UEFI bios. The procedure to change this menu depends on the firmware that's installed.

The defaults for the grub menu are set in the file /etc/default/grub. The line beginning
```
GRUB_DEFAULT=

```
controls which entry of the grub menu is pre-selected for booting and the default value is 0 (meaning first entry).

---

### Post by malonn2 on 2024-12-01
> **Dennis N said:**
> Are you looking at the Grub menu? Or the EFI boot menu? The default grub menu for Debian 12 has three options:

```
Debian Gnu/Linux
Advanced Options for Debian GNU/Linux
UEFI Firmware Settings

```
There is no safe mode mentioned.

If it's the EFI boot menu, that is set in your UEFI bios. The procedure to change this menu depends on the firmware that's installed.
Thanks, @Dennis N.  It's not the GRUB menu proper (as you printed in the code tags above), but is an entry in the UEFI boot menu.  You say changing it depends on firmware, eh?

What steps or literature can I reference to correct this?  The problem for me is that it defaults to what I *think *is a recovery mode (I called it a 'safe mode'), and I don't want that.

I can tell it boots the EFI file I don't want because the GRUB menu that follows will use a lower resolution font.  The EFI boot entry I want to be default uses a higher res font.  Other than that, they look identical to the GRUB menu you posted.

---

### Post by Dennis N on 2024-12-01
> What steps or literature can I reference to correct this?

The "UEFI Firmware Settings" as Debian calls it (also called uefi bios, or just bios), is accessed when you start your computer but instead of booting the operating system, you quickly press delete or a certain function key to enter the settings where you can change the boot priority for what boots on startup. What key that is depends on who created the firmware for your system. It varies.  If you watch the screen on startup, you will usually see a message when it starts up like "press DEL to enter BIOS". Once you get this to load, you need to navigate to where one sets the boot options. It's here you can set the boot priority to another choice.

On my desktop computer, DEL is the key to press. On my laptop, it's F12. Yours might be one of these. If you wait to long to press the key, you boot into the OS.

---

### Post by malonn2 on 2024-12-02
Yessir, yessir.  In the UEFI settings page(s), there is the "boot priority" section.  I have one physical bootable device but there are two entries to choose from, both labeled the same:
```
debian <my storage media>
debian <my storage media>
```
Both of these entries cause the same default boot behavior: the recovery boot (I think that's what it is.  It boots to a low-res GRUB menu)

As a reminder: I'd like to disable the default one (what I call the "recovery" entry).  Debian does something funky 'cuz I can't achieve this via the BIOS (if it's even possible with Debian's configuration on *any* motherboard).  GRUB should be able to handle this easily.

I am a total noob to Debian.  I am not sure what they've done with these EFI entries.

---

### Post by yancek on 2024-12-02
You should probably post more detailed information on your UEFI entries which you can do by using the command below when booted into Debian.

```
sudo efibootmgr -v
```

---

### Post by malonn2 on 2024-12-02
@yancek
```
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* debian    HD(1,GPT,053b2caf-5793-4887-9b71-1745ba5442ec,0x800,0xf3800)/File(\EFI\DEBIAN\SHIMX64.EFI)
Boot0001  debian    HD(1,GPT,053b2caf-5793-4887-9b71-1745ba5442ec,0x800,0xf3800)/File(\EFI\DEBIAN\GRUBX64.EFI)..BO
```

I've been playing with this command off and on for several days.  My understanding: BootCurrent means Boot0001 was used.  It says the order should prefer Boot0000 (which it does) and is, AFAIK, related to Secure Boot, which I don't use.  I think the asterisk next to Boot0000 means it is active?  Boot0000 is the one I don't want, if I'm understanding correctly.  It's just a pain to me to have to be seated at the PC every reboot because it defaults to 0000.

---

### Post by Dennis N on 2024-12-02
> **malonn2 said:**
> @yancek
```
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* debian    HD(1,GPT,053b2caf-5793-4887-9b71-1745ba5442ec,0x800,0xf3800)/File(\EFI\DEBIAN\SHIMX64.EFI)
Boot0001  debian    HD(1,GPT,053b2caf-5793-4887-9b71-1745ba5442ec,0x800,0xf3800)/File(\EFI\DEBIAN\GRUBX64.EFI)..BO
```

I've been playing with this command off and on for several days.  My understanding: BootCurrent means Boot0001 was used.  It says the order should prefer Boot0000 (which it does) and is, AFAIK, related to Secure Boot, which I don't use.  I think the asterisk next to Boot0000 means it is active?  Boot0000 is the one I don't want, if I'm understanding correctly.  It's just a pain to me to have to be seated at the PC every reboot because it defaults to 0000.

The * marks the current default.
This command will change the boot order to boot 0001 by default:
```
sudo efiboomgr -o 0001,0000

```

On some systems, this command has no effect. If it doesn't work, you have to change the order in the BIOS.

---

### Post by malonn2 on 2024-12-03
I installed Debian on an old OCZ Vertex 2 SSD I bought back @ 2010.  Having read your post, I know it's related to that.

I have tried a bunch of stuff using efibootmgr prior to the original post, and the system just reverts a lot of it after reboot.  I concluded that efibootmgr just isn't the way to go with this drive.  However, like my original post said: I'd like to tune this (and think I can) via the GRUB configuration file (not the boot script, but the /etc/default/grub file, which I know are used together).  I was hoping GRUB_DISABLE_RECOVERY=true would do the trick, but it did not (after changing the "grub" file, I ran update-grub, maybe I should've used grub-mkconfig instead).

Anyway, I'm no fan of 2010 hardware for my daily driver, so my test of this old OCZ is drawing to a close.  Time to get back to my NVMe gen4 bliss, install Ubuntu LTS on it and get on down the road.  Debian trial period drawing to a close; to be continued in the future...

---

### Post by yancek on 2024-12-03
> I ran update-grub, maybe I should've used grub-mkconfig instead). 

No, would not matter as all update-grub does is run grub-mkconfig which you can see by reading the update-grub script in /usr/sbin.

If you cannot use efibootmgr to change the order to Boot0001 or you can't make the change in the BIOS to boot that entry you can try to delete it either with efibootmgr or in BIOS.  You have old hardware and that may be part of the problem as UEFI installs did not become standard until 2012.  efibootmgr does not work well on some computers as it will allow creating/deleting but not changing order and other options.  I have found this to be the case on my HP so you might take a look at your BIOS for these options.  The option Boot0000 is the shimx64.efi entry which is generally used with Secure Boot on.

---

