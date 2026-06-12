---
title: "Problems with the clock in Ubuntu server"
date: 2007-07-26
forum: Server Platforms
---

### Post by kimtiede on 2007-07-26
Hi all,

I have some clock problems with my ubuntu server installation.

The problem is that the clock does not seem to tick right. It seems to stop and sometimes move backwards as you can see below:

Thu Jul 26 15:38:00 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:00 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:02 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:00 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:01 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:03 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:00 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:01 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:00 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:02 CEST 2007
kim@tiedeserver:~$ hwclock
2007-07-26T15:48:28 CEST  2.418111 seconds
kim@tiedeserver:~$ date
Thu Jul 26 15:38:06 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:06 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:07 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:04 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:05 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:05 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:07 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:03 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:04 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:04 CEST 2007
kim@tiedeserver:~$ date
Thu Jul 26 15:38:06 CEST 2007

As you can see the hardware clock seems to work ok, but the system clock works in mysterious ways. I have looked in different log files in the /var/log directory but it seems ok. 

Any good ideas?

Thanks in advance 

kim

---

### Post by kimtiede on 2007-07-26
I seem to find a pattern in the reported clock

kim@tiedeserver:/boot/grub$ date
Thu Jul 26 16:06:42 CEST 2007
kim@tiedeserver:/boot/grub$ date
Thu Jul 26 16:06:43 CEST 2007
kim@tiedeserver:/boot/grub$ date
Thu Jul 26 16:06:44 CEST 2007
kim@tiedeserver:/boot/grub$ date
Thu Jul 26 16:06:45 CEST 2007
kim@tiedeserver:/boot/grub$ date
Thu Jul 26 16:06:45 CEST 2007
kim@tiedeserver:/boot/grub$ date
Thu Jul 26 16:06:46 CEST 2007
kim@tiedeserver:/boot/grub$ date
Thu Jul 26 16:06:42 CEST 2007
kim@tiedeserver:/boot/grub$ date
Thu Jul 26 16:06:44 CEST 2007

It forwards 4 seconds (from 42 -> 46) and then goes backwards 4 seconds again (46 -> 42) and this happens over and over again. At some point it continues and forwards another 4 seconds :confused:

By the way: uname -a = Linux tiedeserver 2.6.15-28-server #1 SMP Thu May 10 10:40:27 UTC 2007 i686 GNU/Linux

Cheers

Kim

---

### Post by kimtiede on 2007-07-27
When I got home yesterday i connected a keyboard and a screen to my ubuntu server to see what was going on and then the machine woke up and worked again.

I suspect that it has something to do with acpi so I added the following line to the kernel loader:

acpi=off apm=off

Since it is a periodical error I have to wait and see if the error returns.

What do you think?

Cheers

Kim

---

### Post by codmate on 2007-07-27
Maybe install ntpd.

This demon syncs your local time with a selected ntp server's time  :)

---

### Post by kimtiede on 2007-07-27
Thanks for your reply.

I think that it must be something more fundamental than setting the clock because the date process reports a time that moves backwards :confused:

Cheers

Kim

---

### Post by codmate on 2007-07-27
Maybe your BIOS battery is going?

Have a poke around in the BIOS and see what time & date it's reporting.

---

### Post by kimtiede on 2007-07-27
Hi,

I thought that the CMOS battery was only used for holding the time when the computer is shut down and without power. 

If it was the CMOS battery then I would think that the hwclock also reports false times. In my case it is only the system clock that behaves in mysterious ways.

But perhaps it could be the battery??

/Kim

---

