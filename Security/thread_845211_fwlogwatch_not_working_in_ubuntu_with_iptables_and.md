---
title: "fwlogwatch not working in ubuntu with iptables and syslog-ng"
date: 2008-06-30
forum: Security
---

### Post by mrf76 on 2008-06-30
Hello,

Fwlogwatch don't work properly in Ubuntu because it can't count numbers of iptables events in syslog/syslog-ng and fwlogwatch output looks like there is always only one packet from source, which is not good. I believe that's problem is here:

**Ubuntu FW syslog sample:**

Jun 30 17:08:09 fw kernel: [COLOR="Red"][247590.490623][/COLOR] FORWARD: IN=eth1 OUT=eth2 SRC=10.*.*.128 DST=213.129.*.* LEN=31 TOS=0x00 PREC=0x00 TTL=127 ID=27693 PROTO=UDP SPT=6970 DPT=8372 LEN=11

**Suse FW syslog sample:** 

Jun 30 16:52:29 relay kernel: FW-in-drop: IN=eth0 OUT= MAC=*:*:* ... SRC=221.206.*.* DST=195.122.*.* LEN=485 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=UDP SPT=42361 DPT=1027 LEN=465

Please, how can I get rid off these syslog kernel numbers? Thanks for your help.

Peter

---

### Post by orbisvicis on 2008-09-30
They're part of the kernel's logging interface
Switching over to ULOG (ulogd) should remove them

---

### Post by NickD-NLUG on 2009-01-05
> **orbisvicis said:**
> They're part of the kernel's logging interface
Switching over to ULOG (ulogd) should remove them

Did you try this?  Did it work?

---

### Post by mrf76 on 2009-03-04
Thanks for your answers. I tried ulogd today and yes it is working well. But there is new problem for me that comes with ulogd. Should I'll be happy with it when now i need run another daemon (as root) on my firewall server when considering security risks? And even more problem right now. There is no option in ulogd to log alerts also to remote syslog server. Maybe I should forget on fwlogwatch as a nice summary stats for firewalls, or make myself a script for remove kernel numbers, or even patch fwlogwatch source, i don't know yet. Thank you.

Peter

---

### Post by mrf76 on 2009-03-04
I'm wondering even more now. I tried others Firewall report/analyzer tools (fwanalog and wflogs) and every one of them have the same problem with syntax of iptables logs like fwlogwatch have. I like to ask why they are part of such a nice distro when they are not working out-of-box ? 

Yes I know there is no need to panic. Nothing is final yet, and still we have lots of options :)

Peter

---

### Post by mrf76 on 2010-02-18
Finally found way to get fwlogwatch and syslog-ng working. Magic is called 'printk.time=n'. 

Add this option to /boot/grub/menu.lst so it look like this:

## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash printk.time=n

Then run "sudo update-grub", restart and you're done :)

---

