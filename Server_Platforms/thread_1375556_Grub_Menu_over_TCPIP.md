---
title: "Grub Menu over TCP/IP"
date: 2010-01-08
forum: Server Platforms
---

### Post by marwooj on 2010-01-08
Hi, can one manage grub menu over TCP/IP  (ubuntu 9.10), so in case last loaded kernel is nor working I can boot working one?

---

### Post by Lars Noodén on 2010-01-08
You can have grub failover to the last working kernel.  That allows you to try a new kernel and if it doesn't work have an easy way back to the previous kernel.

[http://www.gnu.org/software/grub/manual/html_node/Booting-fallback-systems.html](http://www.gnu.org/software/grub/manual/html_node/Booting-fallback-systems.html)

Was that the kind of thing you were looking for?

---

### Post by marwooj on 2010-01-19
> **Lars Noodén said:**
> 
Was that the kind of thing you were looking for?

Looks promising, but how would it go with,
menuentry "Ubuntu" {
        
}
I see there is 
recordfail=1
But when my boot fails (it stops on some HugeTLB entry on console), then I turn power off (with fuze circuit), nad then back on it is trying to boot in the same entry.

---

### Post by Lars Noodén on 2010-01-19
Which version of grub are you using?

The instructions in the link were for the 0.9x version.

---

### Post by huwnet on 2010-01-19
Grub cannot be run over TCP/IP. However many servers support IPMI or Intel VPro which allows a serial console. Google will show you how to send grub output to a serial port

For computers without this functionality, you can sometimes purchase addon cards

---

