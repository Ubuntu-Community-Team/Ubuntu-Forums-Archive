---
title: "Kernel panic on boot"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Wise Ferret on 2012-03-11
Hello! I use Precise on Dell xps 1340 laptop (64 bit, nvidia-current).

Booting with the old oneiric kernel, all is fine. Booting with the new Precise kernel leads to immediate kernel panic, with blinking caps lock key.

I updated /etc/default/grub and removed the "quiet" and "splash" parameters, and I can see a long list of error messages run across the screen. However, none of this is recorded to any of the logs in /var/log. all i get is ```
Mar 11 20:42:59 aku dhclient: DHCPREQUEST of 172.29.21.83 on eth1 to 132.64.253.10 port 67
Mar 11 20:42:59 aku dhclient: DHCPACK of 172.29.21.83 from 132.64.253.10
Mar 11 20:42:59 aku dhclient: bound to 172.29.21.83 -- renewal in 274 seconds.
Mar 11 20:43:43 aku kernel: Kernel logging (proc) stopped.
Mar 11 20:43:43 aku rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="785" x-info="http://www.rsyslog.com";] exiting on signal 15.
``` on syslog, and ```
Mar 11 20:43:43 aku kernel: Kernel logging (proc) stopped.
``` on kern.log.

What can I do in order to uderstand what s going on, or even just gather sufficient information for a new bug?

---

### Post by Wise Ferret on 2012-03-15
Bumpity-bump!

---

### Post by matt_symes on 2012-03-16
Hi

Need lots more information. Give as much as you can.

When's it oopsing ?

A screen shot of the oops would be nice.

Kind regards

---

