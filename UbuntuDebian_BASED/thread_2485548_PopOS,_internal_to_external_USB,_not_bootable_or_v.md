---
title: "PopOS, internal to external USB, not bootable or visible in BIOS?"
date: 2023-04-01
forum: Ubuntu/Debian BASED
---

### Post by themacmeister on 2023-04-01
I recently removed my 500GB internal HDD from my laptop, and replaced it with a 500GB SSD. I then cloned the original drive (in USB external enclosure) to the now-internal SSD, and it worked magnificently...

I now wish to use the existing install HDD (which has many updates, installs and modifications) as a USB bootable PopOS, but the drive is not bootable, and does not appear in BIOS or under any bootloader?

I was thinking of trying to reinstall EFI systemd-boot from [https://support.system76.com/articles/bootloader](https://support.system76.com/articles/bootloader)

Anyone have any ideas how I can resurrect this install without damaging the PopOS install partition?

many thanks in advance for any tips or pointers...

---

### Post by themacmeister on 2023-04-01
NOTE: The machine I will be booting off does NOT have an existing Linux install, only Win 10 or macOS Mojave, neither of which have efibootmgr :-/

just so you know...

---

### Post by tea for one on 2023-04-02
rEFInd boot manager on a USB stick is a very useful tool.
See [COLOR="#0000FF"]USB flash drive image file[/COLOR] > [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

---

### Post by yancek on 2023-04-02
Was the original install of Pop OS a Legacy/CSM install or an EFI install.  Are the comments you made about it not being bootable and not being seen in the BIOS on the original machine or the other machine with windows/mac?  Or both?  On the original HDD with Pop OS, how were you booting it?  From Pop OS bootloader or another OS?  The suggestion in post 3 might be your only alternative as I am not aware of any windows/mac tool to boot Linux.  If your drive doesn't show in the BIOS it may be a hardware problem.

---

### Post by oldfred on 2023-04-02
Do not know about POP.
But it would not boot on original laptop as you have duplicate UUIDs & GUIDs.

Many with Mac use rEFInd, I also use it on my PC as an emergency boot flash drive. I had old tiny flash drive that I was able to resurrect as rEFInd is tiny.
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) &
[https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions](https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions)

---

