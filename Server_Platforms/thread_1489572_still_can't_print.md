---
title: "still can't print"
date: 2010-05-21
forum: Server Platforms
---

### Post by ZizzerZuz on 2010-05-21
Ubuntu Server 10.4, On dual processor 1.3's and 2 gigs ram.  128 gigs over 3 drives.  Trying to print to Nec Superscript 870 attached to parallel port.  

CUPS is running.  I can get to the admin pages.  I'm also using webmin to help administer this system.  The printer has been ... or at least attempted to configure the printer from both interfaces.  When I send a print job it looks like CUPS gets it and send it to the printer however it does not print,.  The light on the printer starts to flash and if I press the button on the printer three times it prints, however the formatting is incorrect.

karl@zeus:~$ cat foo
foo
foo
foo
foo
karl@zeus:~$ lp foo
request id is nec-9 (1 file(s))

light flashes on printer, press the button three times, prints this:

foo
         foo
                  foo
                            foo

Currently the BIOS is set following article: [http://en.wikipedia.org/wiki/Parallel_port](http://en.wikipedia.org/wiki/Parallel_port)
It's set to this [IRQ]("http://en.wikipedia.org/wiki/Interrupt_Request") 7 0x3bc 0x3bf
Here's some terminal output that I hope will help.

karl@zeus:~$ dmesg | grep lp0
[   40.779487] lp0: using parport0 (interrupt-driven).
karl@zeus:~$ dmesg | grep parport
[   40.653644] parport_pc 00:05: reported by Plug and Play ACPI
[   40.653708] parport0: PC-style at 0x3bc, irq 7 [PCSPP]
[   40.778867] parport0: Printer, NEC SuperScript 870
[   40.779487] lp0: using parport0 (interrupt-driven).
karl@zeus:~$ lpstat -t
scheduler is running
system default destination: nec
device for nec: parallel:/dev/lp0
nec accepting requests since Thu 20 May 2010 10:34:38 PM EDT
printer nec is idle.  enabled since Thu 20 May 2010 10:34:38 PM EDT

Zizzer

---

### Post by cariboo on 2010-05-22
Does anything show up in /var/log/cups/error.log?

---

### Post by ZizzerZuz on 2010-05-22
-rw-r-----  1 root lpadmin    0 2010-05-21 06:31 error_log

When I print the access-log and the page-log increase, but look pretty normal.

root@zeus:/var/log/cups# more access_log
localhost - - [22/May/2010:08:42:12 -0400] "POST /printers/nec HTTP/1.1" 200 340
 Create-Job successful-ok
localhost - - [22/May/2010:08:42:12 -0400] "POST /printers/nec HTTP/1.1" 200 268
 Send-Document successful-ok

---

