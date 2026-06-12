---
title: "live session requests login and password - so what is it?"
date: 2017-07-30
forum: Ubuntu Development Version
---

### Post by orange2k on 2017-07-30
I downloaded 17.10 Ubuntu Mate Alpha 2, and upon loading it requests a username and password, without it, I can't start the desktop...so does anyone know what I should type in?

---

### Post by #&amp;thj^% on 2017-07-30
This is odd it asking for a username and password? Unless you burnt it to a USB in  Persistence mode.
But try "ubuntu-mate" for user name, and should not have to enter a password.

---

### Post by orange2k on 2017-07-30
No, I burned it using dd - (sudo dd if=blabla.iso of=/dev/sdb bs=1M), but it does ask for a username and password, gonna try "ubuntu-mate" as you suggested...thanks

---

### Post by Chanath on 2017-07-30
> **orange2k said:**
> No, I burned it using dd - (sudo dd if=blabla.iso of=/dev/sdb bs=1M), but it does ask for a username and password, gonna try "ubuntu-mate" as you suggested...thanks

Have look here, [https://ubuntu-mate.community/c/development-discussion/artful](https://ubuntu-mate.community/c/development-discussion/artful)

---

### Post by orange2k on 2017-07-30
"ubuntu-mate" doesn't work - the login screen disappears for a moment, looking like its going to start the live session, but then it only comes back to it...

Either it is a bug, or I don't have the right information - I know its an alpha release, but how are users supposed to test the release if they aren't even given a chance? :?

---

### Post by orange2k on 2017-07-30
Thanks, I just posted the question there...

---

### Post by mc4man on 2017-07-30
No issues here with the latest ubuntu-mate image. Are you using the 64-bit image?

---

### Post by orange2k on 2017-07-31
Yes, 64-bit latest Alpha I got following the link from Distrowatch...

---

### Post by ventrical on 2017-07-31
Just try (mate) with no brackets then enter or mate-session enter.  It should just boot up if you are using ubuntu disks utility to to restore image to usb.

Regards..

---

### Post by orange2k on 2017-07-31
> **ventrical said:**
> Just try (mate) with no brackets then enter or mate-session enter.  It should just boot up if you are using ubuntu disks utility to to restore image to usb.

Regards..

Just tried that - doesn't work...
Like I said, no login/password combo seems to be accepted except "ubuntu-mate" as login and password empty, but even this only leads back to the login form...

---

### Post by mc4man on 2017-07-31
Feels like this is either a Setup issue (windows, UEFI, ect.) or a hardware issue (typically video.
Maybe boot up to login screen then, go to a tty (ctrl+alt+F3), login (ubuntu-mate no pass)
Then cd to /var/log & run ls
If there are any interesting looking logs open them in less or nano & see what's there..

---

### Post by orange2k on 2017-08-01
Nah, I gave up...I also checked out the older Ubuntu-Mate release, 17.04, but it failed completely - it wouldn't boot at all...
There are plenty of distros out there that work just fine, and I must say I'm quite dissapointed with Ubuntu-Mate as it is...

---

### Post by VMC on 2017-08-01
"[COLOR=#000000]Feels like this is either a Setup issue (windows, UEFI, ect.) or a hardware issue (typically video."[/COLOR]
[COLOR=#000000]I think mc4man's reply is spot on. If this were an issue, then it would be widespread.

One last thing you could try is boot the ISO using grub:
(change set isofile and hd info to your location)
[/COLOR] ```
menuentry "ISO" {
    set isofile="/ISO/Xartful-desktop-amd64.iso"
    loopback loop (hd0,8)$isofile
    linux (loop)/casper/vmlinuz.efi boot=casper toram maybe-ubiquity iso-scan/filename=$isofile noprompt noswap noeject
    initrd (loop)/casper/initrd.lz
        }
```

---

