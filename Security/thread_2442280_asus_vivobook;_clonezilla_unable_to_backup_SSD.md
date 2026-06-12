---
title: "asus vivobook; clonezilla unable to backup SSD"
date: 2020-05-01
forum: Security
---

### Post by Alistair George on 2020-05-01
Hi. 
Asus really lock down their notebooks. My new Lenovo E590 gave no such problems:
Going through the functions in Clonezilla all works till I get to select source drive (which is onboard SSD) and the error message 'there is no source unmounted' or similar.
So I go to CMD and #mount which provides a list showing backup drive and no SSD drive.

Anyone have any idea what might be going on?
Thanks, Al.

---

### Post by EuclideanCoffee on 2020-05-01
Is it possible that E590 doesn't have an SSD but an M2? It might be enough to fool Clonezilla.

It's hard to say without having full context.

Anyway you can provide logs, for example any of these files?

/var/log/clonezilla.log

/var/log/partclone.log

Also, please review this guide and see if it may help. [https://jasoncoltrin.com/2018/02/09/how-to-clone-a-dell-optiplex-7050-m-2-nvme-hard-drive-with-clonezilla-and-an-external-usb-hdd/](https://jasoncoltrin.com/2018/02/09/how-to-clone-a-dell-optiplex-7050-m-2-nvme-hard-drive-with-clonezilla-and-an-external-usb-hdd/)

---

### Post by Alistair George on 2020-05-01
HI thanks for concise reply. My lappy is a Lenovo thinkpad, the offender is this: ASUS Vivobook S15 S530FN-EJ575T Entertainment Ultrabook 15.6" FHD Anti-Glare Intel i7-8565U 16GB 512GB PCIe NVMe M.2 SSD
So I presume what you say is correct NVMe M.2 sounds like what you say. Is there any workaround for Clonezilla? Its my student daughters and I'd like to backup the drive just in case it gets pinched or lost.

---

### Post by Alistair George on 2020-05-01
BTW I am using a live boot so logs may be a tad difficult the clonezilla version im using is clonezilla-live-20200302-eoan-amd64.iso

---

### Post by EuclideanCoffee on 2020-05-01
Doing a quick query around the Internet, I've found others have had the same compliant. I think if you try that blog post [https://jasoncoltrin.com/2018/02/09/how-to-clone-a-dell-optiplex-7050-m-2-nvme-hard-drive-with-clonezilla-and-an-external-usb-hdd/](https://jasoncoltrin.com/2018/02/09/how-to-clone-a-dell-optiplex-7050-m-2-nvme-hard-drive-with-clonezilla-and-an-external-usb-hdd/) here, you may have some success. I would review this first of course. It appears you may need to disable secure boot. I'm guessing that may be the true culprit. That's the best I can offer at this time. Good luck!

---

### Post by Alistair George on 2020-05-01
Yep, did that yesterday eg disabled secure boot. The Asus seems to be really locked down; nice Lappy, but unlike my Lenovo, really hard to do anything outside Windows.

---

### Post by EuclideanCoffee on 2020-05-01
Ah, then the logs would be necessary to troubleshoot. Perhaps a different forum would have more community experts available.

---

### Post by Alistair George on 2020-05-01
I just tried the latest unstable of Clonezilla and boot of a usb stick just in case. Still no joy the best I can do for a log is the attached image of 'mount' which IMHO shows nothing.
[ATTACH=CONFIG]285726[/ATTACH]

---

### Post by EuclideanCoffee on 2020-05-01
Hm, yes. I will need the log and more context.

Mount just shows me some partition tables.

Please use the attachment tool. Redirecting users to a source they need to verify is risky.

---

