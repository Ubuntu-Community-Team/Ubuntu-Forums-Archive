---
title: "[SOLVED] syslog-ng with dlink router"
date: 2007-11-29
forum: Server Platforms
---

### Post by MatsB on 2007-11-29
Hi,

Need some help seting up syslog from my DLINK DGL-4300 router to Ubuntu server 7.10.

I've installed syslog-ng and not changed anything, so it's all deafult settings atm. I also enabled my router to send syslog to my server. The problem is that I can't see anything in any logfiles related to my router. 

Do I need to change any settings in /etc/syslog-ng/syslog-ng.conf?
If so what?

---

### Post by gg234 on 2007-11-29
yes you need to configure syslog-ng config file check this [http://www.debianhelp.co.uk/syslog-ng.htm](http://www.debianhelp.co.uk/syslog-ng.htm)

---

### Post by MatsB on 2007-11-30
> **gg234 said:**
> yes you need to configure syslog-ng config file check this [http://www.debianhelp.co.uk/syslog-ng.htm](http://www.debianhelp.co.uk/syslog-ng.htm)

Thanks for the tip. No I got it working by adding this:

/etc/syslog-ng/syslog-ng.conf
uncomment :
udp();

/etc/deafult/syslog-ng
Adding these rows:
CONSOLE_LOG_LEVEL
KERNEL_RINGBUF_SIZE

case "x$KERNEL_RINGBUF_SIZE" in
x[0-9]*)
dmesg -s $KERNEL_RINGBUF_SIZE
;;
x)
;;
*)
echo "KERNEL_RINGBUF_SIZE is of unaccepted value."
;;
esac

One would think that syslog-ng would receive syslog traffic by default when installed, but nothing is simple in the Linux world :mad:

---

### Post by jdbg on 2008-04-06
Hi,

I have a similar issue to this topic.
However - I can't figure out where should I configure that the ubuntu box received the packets from the router? Where do I put the address of the router?

10x in advance!

---

