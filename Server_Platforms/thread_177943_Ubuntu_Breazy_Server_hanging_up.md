---
title: "Ubuntu Breazy Server hanging up"
date: 2006-05-17
forum: Server Platforms
---

### Post by RAGNAR86 on 2006-05-17
Hi guys!

I would need some tips&tricks for my ubuntu server. The server is a P4 2,4 Ghz with 1Gb of RAM. Services installed are Apache 1.3, MySQL 4.xx and PHP 4.xx - it's a plain webserver. The server is great, fast and almost perfect, exept sometimes i hangsup. Not rebooting, not powering off, but just stop responding on everything - SSH, web, mysql, etc. I've used some monitoring software to monitor temperature, disk space, used memory, traffic, etc, and everything looks fine.

So, what I would like some help with is checking the system, is it anything more i should check? Logs, files, etc? I would really apritiate if someone could give me some tips. 

Thank you!
/Kenneth

---

### Post by mority on 2006-05-17
I would have a look in /var/log/kern.log. If your system completely freezes, probably the kernel is hangig up (kernel oops) and if so you should find something in kern.log since this is where the kernel messages go.

---

### Post by RAGNAR86 on 2006-05-17
Hello mority!

I've looked inside my kern.log and cut this out:

May 16 22:24:20 tiesto kernel: [5869201.338000] i2c /dev entries driver
May 17 12:37:56 tiesto kernel: Inspecting /boot/System.map-2.6.12-10-386
May 17 12:37:56 tiesto kernel: Loaded 29010 symbols from /boot/System.map-2.6.1$
May 17 12:37:56 tiesto kernel: Symbols match kernel version 2.6.12.

The time of the hangup was May 17 - 02:10 and the reboot was May 17 - 12:37:56. I couldn't find anything wrong in my kern.log, any ideas?

BTW, the reason i know the time of the hangup is that i was currently working on the server with a SSH session, not doing anything fancy just reading logs.

Thanks,
/Kenneth

---

### Post by mority on 2006-05-17
Hmm, yes, those log lines don't look wrong something.

You could plug a monitor and keyboard or a serial connection to the machine and watch dmesg by the time it crashes again. 

I don't have any other ideas, sorry.

---

### Post by nverhaar on 2006-05-18
I had a similar problem here at work on a fairly recent machine running an Ubuntu server install and doing nothing more than acting as a firewall. Every couple of days the server would freeze completely, with no real explanation as to why.

I searched high and low and couldn't find a definitive solution, until I tried booting the kernel with a few different options.

I found that by adding the below options to the kernel boot parameters in Grub, my system went from randomly freezing and having a max of 2-4 days uptime, to having over 50 days uptime. The only reason it came down after 50 days was because we had a power outage longer than the UPS could sustain power to the box.

The options were:
acpi=off noapic nolapic

I have since had one or two brand new IBM servers giving similar flaky results, and after setting these options it made them behave as they should. Give it a shot!

---

### Post by RAGNAR86 on 2006-05-19
Thank you nverhaar!

I will try your tip right away.

---

