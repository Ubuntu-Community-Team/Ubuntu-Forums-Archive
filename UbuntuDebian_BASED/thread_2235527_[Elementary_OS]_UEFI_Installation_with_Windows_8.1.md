---
title: "[Elementary OS] UEFI Installation with Windows 8.1"
date: 2014-07-21
forum: Ubuntu/Debian BASED
---

### Post by miguel-carcamo on 2014-07-21
I bought a FreeDOS PC, and I want to do the dual boot with elementaryOS and Windows 8.1, all this due to the lack of drivers for other Windows distributions.

Anyway, I installed Windows 8.1 Pro first on UEFI Mode, and no problems here. I disabled the Fast Boot here too.

Then I installed elementaryOS also in UEFI Mode, and obviously if I put the command [COLOR=#333333][FONT=Ubuntu][ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode"
It returns Installed in EFI Mode.

I installed elementaryOS with 3 partitions, root, swap and home.

The thing is that every time I restart, or turn on the computer, there is no grub showing up. It goes directly to elementaryOS, and yes I can enter to Windows through BIOS but that's not what I want.

I'm not sure of using boot-repair, 'cause I've read that the use of it is only if I installed the linux distribution in Legacy Mode.

What should I do?

Cheers![/FONT][/COLOR]

---

### Post by ubudog on 2014-07-21
Hi,

Does this solution help you?
[http://ubuntuforums.org/showthread.php?t=2060292&p=12249599#post12249599](http://ubuntuforums.org/showthread.php?t=2060292&p=12249599#post12249599)

---

### Post by miguel-carcamo on 2014-07-21
And how many time should I put to that paremeter? 

The default is 0.

Also, the solution says that if only is Ubuntu installed.

And I have a "dual-boot"

---

### Post by ubudog on 2014-07-21
Just remove the 0, or comment (#) that line out.

You can use boot-repair, check out these instructions:
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

I'm not sure with Windows 8.1, but you might have to disable Secure Boot in order for this to work.

---

### Post by oldfred on 2014-07-21
Boot-Repair can fix UEFI systems also. It does not fix Windows except for a few very minor issues.

But often better with new UEFI systems to post link to the BootInfo report so we can see details and suggest best way to fix.

What hardware, model & video card/chip?

---

