---
title: "OK who was it?"
date: 2006-10-11
forum: The Cafe
---

### Post by Raval on 2006-10-11
OK which one of you guys put a curse on me??? :-k 

Installed Ubuntu 6.06 lTS a week or two ago and everything worked fine but never spent much time using it. 

Yesterday I decided I was ready to start using Ubuntu on a daily bases, but first I need the driver for my PCTel modem.

Problem one: I could sign into my Ubuntu forum account (usrname: underpressure) but couldn't post so had to create this one. Anyway got modem driver.

This morning I decided to attempt to load the modem driver

Problem two: Xserver won't load (did all the time before). wanted to post error log before asking for help, I had to learn how to mount a memory stick in CLI and after a few hours I did. I then rebooted Ubuntu and guess what? GUI loaded and has been ever since.:confused: 

time to load modem drivers (789 series) first I needed to load build-essentials and linux-headers-386 from cd

Problem three: both cd-rom drives not showing up, thats right! they did a houdini. Booted up in Windows still no cd-roms.

moral of this story? Bill Gates has anti linux code in SP2

---

### Post by PriceChild on 2006-10-11
> **Raval said:**
> I could sign into my Ubuntu forum account (usrname: underpressure) but couldn't post so had to create this one.I'll take a look into this for you.

---

### Post by Raval on 2006-10-11
> **PriceChild said:**
> I'll take a look into this for you.

Thanks any help would be appreciated. I'd also like to mention a few days ago I sent an email using the contact us page about this matter and never got a response, a day or two after I was able to send a PM from the account to Ubuntu Geek and still no reply.

---

### Post by PriceChild on 2006-10-11
> **Raval said:**
> Thanks any help would be appreciated. I'd also like to mention a few days ago I sent an email using the contact us page about this matter and never got a response, a day or two after I was able to send a PM from the account to Ubuntu Geek and still no reply.Please bare in mind that all the staff here are volounteers. No-one is paid.

The Staff Team will do their best to get round to answering all questions but thankyou for your patience.

Pricey

As for the missing cdroms... could you please post your /etc/fstab here and give a description of all the drives in your system.

---

### Post by Lord Illidan on 2006-10-11
If the missing cd rom drives are not showing up in both oses, are they showing up in the POST?

---

### Post by jdong on 2006-10-11
> **Raval said:**
> Thanks any help would be appreciated. I'd also like to mention a few days ago I sent an email using the contact us page about this matter and never got a response, a day or two after I was able to send a PM from the account to Ubuntu Geek and still no reply.

I don't think people begin to imagine the volume of PM's and e-mails that the staff has to sort through. :)

Patience, please :)

---

### Post by Raval on 2006-10-12
> **Lord Illidan said:**
> If the missing cd rom drives are not showing up in both oses, are they showing up in the POST?

Well the entire system was freaking out. Since that post the modems became non-functional. 

A friend advised me to remove the battery so BIOS to reset to default. After I did this the CD ROMs came back. The system is also detecting my modems but will not auto install the drivers.
got to figure that one out.

Anyway, tried to install Linux-headers-386 and build-essential. I was able to install L-H-386 but error for build-essentials.

> [COLOR="Navy"]W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb)
  Temporary failure resolving 'security.ubuntu.com'


W: Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb
  Unable to unmount the CD-ROM in /media/cdrom0/, it may still be in use.


W: Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/g/glibc/libc6-dev_2.3.6-0ubuntu20_i386.deb
  Unable to unmount the CD-ROM in /media/cdrom0/, it may still be in use.[/COLOR]

---

### Post by Raval on 2006-10-12
> **Lord Illidan said:**
> If the missing cd rom drives are not showing up in both oses, are they showing up in the POST?

> **jdong said:**
> I don't think people begin to imagine the volume of PM's and e-mails that the staff has to sort through. :)

Patience, please :)

Well the only problem (then and now)I am unable to use my preferred username but beyond that no worries.

---

### Post by PatrickMay16 on 2006-10-12
Disappearing drives? I had this problem with my old computer. 
Sometimes for long periods (like a month or a few weeks) it'd be absolutely fine, then suddenly drives would start vanishing and I'd get weird errors and lock ups. Eventually it crashed one day and wouldn't boot any more. (wouldn't do anything, just a blank screen when you turned it on).
The motherboard was dying. When I took a look at it, there were loads of bulging capacitors, some of which had leaked their fluid.

---

### Post by Raval on 2006-10-12
Part of me believes the board might be dying. On the other hand last year I was out of the country for 3 months and when I came back it was acting up mostly trouble booting I had to clean the entire PC since it was filled with a lot of dust. I recently came back from a six month trip and while I did take precautions to prevent dust build up the idea that dust may be a factor is at the back of my mind.

If it is the board, my board is an Intel D850GB and I can get a new one off of Ebay for $40.00 USD

I'm using my Dell Celeron I bought while in the US.

---

### Post by Raval on 2006-10-14
> **Raval said:**
> Part of me believes the board might be dying. On the other hand last year I was out of the country for 3 months and when I came back it was acting up mostly trouble booting I had to clean the entire PC since it was filled with a lot of dust. I recently came back from a six month trip and while I did take precautions to prevent dust build up the idea that dust may be a factor is at the back of my mind.

If it is the board, my board is an Intel D850GB and I can get a new one off of Ebay for $40.00 USD

I'm using my Dell Celeron I bought while in the US.

Incase this might be of help to anyone: PROBLEM FOUND!

The problem was caused by a defective Modem and an Intermittent Keyboard. I started by pulling out all my PCI devices and unplugging my CD ROMs, I then installed one at a time and see how the machine would boot. 

Also I had a 128Mb Coby memory stick / Audio player plugged in and noticed it caused the boot process to take over 1 minute.

---

