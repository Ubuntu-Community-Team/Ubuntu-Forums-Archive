---
title: "won't boot"
date: 2008-09-13
forum: Server Platforms
---

### Post by bpfeil on 2008-09-13
I have an optiplex 320 that I'm trying to install 8.04 server on. To get installation to work I had to add into the boot vga=771 and acpi=no, when trying to boot I tried to enter the same thing and I get nothing.  All the computer does is sit on a black screen with a - flashing in the top left corner, the cpu light on the tower is lit up solid also.  Is there something else I should try?

---

### Post by Krupski on 2008-09-13
> **bpfeil said:**
> I have an optiplex 320 that I'm trying to install 8.04 server on. To get installation to work I had to add into the boot vga=771 and acpi=no, when trying to boot I tried to enter the same thing and I get nothing.  All the computer does is sit on a black screen with a - flashing in the top left corner, the cpu light on the tower is lit up solid also.  Is there something else I should try?

Have you tried the "Single User" boot option?

You do get the GRUB menu at boot, right?

Before it times out, hit your down arrow and select the second boot option as opposed to the first.

If you can get in that way, please then post the contents of your '/boot/grub/menu.lst' file.

-- Roger

---

### Post by bpfeil on 2008-09-13
I can get to the grub menu but the 2nd option, recovery, does the exact same thing, I also have xp pro installed and I can boot to that just fine.

---

### Post by bpfeil on 2008-09-14
I been browsing around the forum and it seems like its a grub issue.  All the instructions say to update it from the live cd in the terminal.  From the server version I can't load it from the cd.  Can I do it from a desktop version and have it update my boot loader? Or will I have to install the desktop version first?

---

### Post by bpfeil on 2008-09-14
Ok, so I booted with a desktop live cd and got grub switched to grub2.  Now when I go to boot I get error: You need to load the kernel first.  How does one fix this?

---

### Post by Krupski on 2008-09-14
> **bpfeil said:**
> I can get to the grub menu but the 2nd option, recovery, does the exact same thing, I also have xp pro installed and I can boot to that just fine.

AH! Since you are multi-booting, it's possible that the initial install specified hard drives incorrectly.

Look at your '/boot/grub/menu.lst' file for a part that looks like this (similar, not exact - do not COPY this as it will not work in YOUR system):

```

title           Ubuntu 8.04.1, kernel 2.6.24-19-server
[COLOR="Red"]**root            (hd0,0)**[/COLOR]
kernel          /boot/vmlinuz-2.6.24-19-server root=UUID=e1fdd50d-9fb1-41d1-a028-9d5c2f0ea5c6 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-server
quiet

```

Notice what I highlighted in red... the initial install of Ubuntu may have not set the root hd properly.

During bootup, when you see the Grub menu, hit "E" to edit a line, select the line with "root (hdx,y)" in it, hit "E" again to edit the line, try different numbers (such as (hd0,0) or (hd1,0) or (hd2,0)), then hit "B" to boot.

I'm guessing that your default is NOT (hd0,0) and (hd0,0) is what you need.

In any event, you can't hurt anything since you are not editing the file, but just the one-time boot parameters.

IF you manage to boot up, go into '/boot/grub/menu.lst' and edit the line with the proper (hdx,y) numbers so it will boot properly next time without boot time editing.

Good luck!

-- Roger

---

### Post by bpfeil on 2008-09-14
From the what I've read on the forum I need to have grub2, when I hit "e" in my grub menu I have two lines the change.  

1st
linux (hd1,5/boot/vmliuz-2/6/24-19-server rppt=UUID=2eda7ea4-4a99-4f1\d-a6e3-04e9d99+de
d ro quiet splash

2nd
initrd (hd1,5)/boot/initrd.img-2.6.24-19-server

When I try and boot any of these I get 

boot a command list
error: You need to load the kernel first.

---

### Post by bpfeil on 2008-09-14
I've also lost my xp boot option once I loaded grub2

---

