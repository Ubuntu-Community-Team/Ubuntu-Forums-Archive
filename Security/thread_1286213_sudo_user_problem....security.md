---
title: "sudo user problem....security"
date: 2009-10-08
forum: Security
---

### Post by chipyoung on 2009-10-08
I am running Ubuntu 8.10.  I went to the command line to run "chkrootkit" by typing "sudo chkrootkit".  It asks for my password and when I type it "segmentation fault" comes back.  If I type in a wrong password, it just asks me to try again.  I can't run Nautilus as root for the same reason.

These are the lines concerning this issue when I type "dmesg" at the command line.

[  103.560553] sudo[6611]: segfault at 0 ip b7d0abcb sp bfd32fd0 error 4 in pam_smbpass.so[b7cae000+12a000]
[  191.868417] sudo[6717]: segfault at 0 ip b7d10bcb sp bf9373e0 error 4 in pam_smbpass.so[b7cb4000+12a000]


[  554.879619] [fglrx] GART Table is not in FRAME_BUFFER range 
[  554.939917] [fglrx] CMM init INV FB MC:0xd0000000, length:0x8000000
[  554.939929] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  561.029361] hda-intel: Invalid position buffer, using LPIB read method instead.
[  617.603262] sudo[12181]: segfault at 0 ip b7caabcb sp bfbd1670 error 4 in pam_smbpass.so[b7c4e000+12a000]
[  650.855928] sudo[12196]: segfault at 0 ip b7cb6bcb sp bfcdef80 error 4 in pam_smbpass.so[b7c5a000+12a000]
[  705.771876] sudo[12259]: segfault at 0 ip b7db9bcb sp bfbdfe90 error 4 in pam_smbpass.so[b7d5d000+12a000]
[  777.550103] [fglrx] GART Table is not in FRAME_BUFFER range 
[  777.579505] [fglrx] CMM init INV FB MC:0xd0000000, length:0x8000000
[  777.579517] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  835.651822] gdm[11650]: segfault at 0 ip b7171bcb sp bfafac80 error 4 in pam_smbpass.so[b7115000+12a000]
[  838.027093] [fglrx] GART Table is not in FRAME_BUFFER range 
[  838.073619] [fglrx] CMM init INV FB MC:0xd0000000, length:0x8000000
[  838.073630] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  889.883723] sudo[12612]: segfault at 0 ip b7db4bcb sp bffdb280 error 4 in pam_smbpass.so[b7d58000+12a000]
[  943.775999] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 1060.677083] sudo[12711]: segfault at 0 ip b7c89bcb sp bffb0e80 error 4 in pam_smbpass.so[b7c2d000+12a000]

I have never had this problem before.  I am worried about security issues.

I have Puppy Linux on another partition.  I started Puppy and ran ftprot against my Ubuntu install and it came up negative for viruses.

I did do an update the other day on Ubuntu and this is the first time I have had problems logging with root privileges.

HELP!

Thank you in advance.

---

### Post by witeshark17 on 2009-10-08
You may well find some useful info if you Google for "  segmentation fault  "  I left spaces for easy copy/paste.

---

### Post by chipyoung on 2009-10-08
That was the first thing I did.  It didn't help.  Is there a way to fix this from the "recovery" boot?  This is really a problem.  I can't modify any files and I can't upgrade to 9.04 to possibly fix it that way.  I'm at a loss.

---

### Post by witeshark17 on 2009-10-08
This was caused by a single entry of a wrong password? Have you run a file system check?

---

### Post by chipyoung on 2009-10-08
Fixed.

I booted into recovery mode and ran the command...

"apt-get purge libpam-smbpass"

Now everything is working fine. It was a PAM issue which effected all things that had to be run by root.

Thank you.

---

### Post by witeshark17 on 2009-10-08
Cool, glad it's sorted! ::popcorn:

---

