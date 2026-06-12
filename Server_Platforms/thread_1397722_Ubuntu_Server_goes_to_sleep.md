---
title: "Ubuntu Server goes to sleep"
date: 2010-02-03
forum: Server Platforms
---

### Post by AThomsen on 2010-02-03
Hi,

I've installed Ubuntu Server 9.10 on a small VIA C7 pc. Every now and then (it can take days or hours) the server goes to sleep. It can't be reached by network. If I hit the keyboard it comes to life within a second.

I've looked in the bios and I cannot find any option that would prevent this. I used to run Debian Lenny on the same machine and never experienced the problem.

Is there any way to turn this behaviour off in Ubuntu?

---

### Post by yogeshg1987 on 2010-02-04
Hey,
Check out: 
[http://www.unix.com/sun-solaris/17975-remove-server-sleep-mode.html](http://www.unix.com/sun-solaris/17975-remove-server-sleep-mode.html)

---

### Post by AThomsen on 2010-02-21
That link seems very specific to Solaris :confused:

---

### Post by AThomsen on 2010-04-03
Upgraded to 10.4 - the problem remain.

Adding acpi=off seems to work. Should I file a bug report?

---

### Post by duceduc on 2011-03-14
> **AThomsen said:**
> Upgraded to 10.4 - the problem remain.

Adding acpi=off seems to work. Should I file a bug report?

I am having the same issue. Can you explain what you did to solve it?

---

### Post by wojox on 2011-03-14
> **duceduc said:**
> I am having the same issue. Can you explain what you did to solve it?

Try:

```
sudo nano /etc/default/grub
```

Look for **GRUB_CMDLINE_LINUX_DEFAULT**

Add **acpi=off**

```
sudo update-grub
```

---

### Post by tgalati4 on 2011-03-14
Via C7's are ultra low power.  It's possible that the ACPI goes to sleep automatically, without any BIOS switch.  I have Hardy server running on one, but I haven't kept it running long enough to notice that behavior.  Next time I boot mine, I will look at it.

You could install acpitool and use some switches to keep parts of the bus constantly powered (like the PCI slot that has the network card).

sudo apt-get install acpitool
man acpitool
acpitool -w

---

### Post by abalo13 on 2013-04-13
thanks >>>>[COLOR=#000000][**wojox**]("http://ubuntuforums.org/member.php?u=802919") [/COLOR]
, fixed!:P

---

### Post by sffvba[e0rt on 2013-04-14
*Old thread **closed**.*


404

---

