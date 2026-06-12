---
title: "Clock too fast in Guest vm - Ubuntu JeOS 8.04 Guest on Vmware Server 1.x with Ubuntu"
date: 2008-06-10
forum: Virtualisation
---

### Post by dmatrix on 2008-06-10
I have been experiencing problems with the clock running too fast in my Ubuntu JeOS vmware guests running on Ubuntu Server as the host. I am also running CentOS5 using the same software (Ubuntu Server, Vmware 1.x) and not having any issues with time at all in these vms.

For Ubuntu Servers Hosts I install Vmware 1.x with the any-any patch. I also apply 'elevator=deadline' to the hosts. 

On CentOS5 guests I apply 'nosmp noapic nolapic apci=off divider=10 clocksource=acpi_pm elevator=noop' to grub. This seems to work great on CentOS5 which uses a 2.6.18 kernel and these HZ options:

CONFIG_HZ_1000=y
CONFIG_HZ=1000


For the Ubuntu JeOS guests I tried running with no options applied to grub. The clock seems to run fast and gains time in the guest by 10 minutes within a week. The host clock is perfect and the host is using ntpd to sync time fine. Ubuntu JeOS uses a 2.6.24 kernel and these HZ options in the default linux-image-virtual kernel:

CONFIG_HZ=250
CONFIG_HZ_250=y
CONFIG_NO_HZ=y

I am currently trying to apply these options on Ubuntu JeOS 'noapic nolapic apci=off divider=10 clocksource=acpi_pm elevator=noop'. Only time will tell now if this is the fix, but I constantly see these in my Ubuntu Server Host syslog, where I do not see them with CentOS5 as guests:

kernel: [432058.725321] [6049]: host clock rate change request 378 -> 33
kernel: [432058.725877] [6049]: host clock rate change request 33 -> 377



I also have these options enabled in the vmx files for both CentOS5 and Ubuntu JeOS guests:

MemTrimRate = "0"
sched.mem.pshare.enable = "FALSE"
MemAllowAutoScaleDown = "FALSE"
tools.syncTime = "TRUE"


Any ideas or tips to make Ubuntu JeOS better as a guest vm? I have searched all the vmware threads in these forums and have gathered all the options from these threads.

---

### Post by amorangi on 2008-07-14
Anybody? Mine too have the clocking ticking over at about 2 hours every hour

---

### Post by dimibo on 2008-08-05
Hi,

Any ideas about this problem?

My clock also running fast.
I have Ubuntu 8.04.1 host, VmWare Workstation and WinXP as a guest OS.

---

### Post by dreamgear on 2009-09-23
Ditto.  I am running JeOS 8.04 under VMware ESX 3.0.3, and it gains steadily on the host.  The VMware tools can catch up a clock that runs slow, but they can't do anything about one that gains.

Did your kernel option tweaks help, or not?  

I have noticed that JeOS with no kernal options has the lowest idle CPU usage of any Linux variant I've tried.  It's even less than FreeBSD 7.  This is a plus, but I don't really want to have to resort to running NTP on the guests.  

BTW there is a whole writeup on timekeeping in virtual machines at [http://www.vmware.com/pdf/vmware_timekeeping.pdf](http://www.vmware.com/pdf/vmware_timekeeping.pdf).

---

### Post by dmatrix on 2009-09-23
I resorted to running ntpd on the guests, both Ubuntu 8.04LTS and CentOS 5.x. Time seems to be solid now. Although on some of my Ubuntu guests I get these errors on the host, not sure if this is due to ntpd or the nohz kernel options. Only seems to happen on vm guests that have heavier load.

[6968212.158807] printk: 12 messages suppressed.
[6968212.158819] rtc: lost some interrupts at 256Hz.
[6968212.178743] rtc: lost some interrupts at 256Hz.
[6968212.198700] rtc: lost some interrupts at 256Hz.
[6968212.218652] rtc: lost some interrupts at 256Hz.
[6968212.238596] rtc: lost some interrupts at 256Hz.
[6968212.258553] rtc: lost some interrupts at 256Hz.
[6968212.278499] rtc: lost some interrupts at 256Hz.
[6968212.298449] rtc: lost some interrupts at 256Hz.
[6968212.318404] rtc: lost some interrupts at 256Hz.
[6968212.338358] rtc: lost some interrupts at 256Hz.
[7083117.949244] printk: 9 messages suppressed.
[7083117.949253] rtc: lost some interrupts at 512Hz.
[7083117.969194] rtc: lost some interrupts at 512Hz.
[7083117.989155] rtc: lost some interrupts at 512Hz.
[7083118.009100] rtc: lost some interrupts at 512Hz.
[7083118.029044] rtc: lost some interrupts at 512Hz.
[7083118.048997] rtc: lost some interrupts at 512Hz.
[7083118.068951] rtc: lost some interrupts at 512Hz.
[7083118.088908] rtc: lost some interrupts at 512Hz.
[7083118.108849] rtc: lost some interrupts at 512Hz.
[7083118.128792] rtc: lost some interrupts at 512Hz.
[7237522.800506] printk: 6 messages suppressed.
[7237522.800521] rtc: lost some interrupts at 512Hz.
[7237522.820451] rtc: lost some interrupts at 512Hz.
[7237522.840418] rtc: lost some interrupts at 512Hz.
[7237522.860349] rtc: lost some interrupts at 512Hz.
[7237522.880311] rtc: lost some interrupts at 512Hz.
[7237522.900259] rtc: lost some interrupts at 512Hz.
[7237522.920207] rtc: lost some interrupts at 512Hz.
[7237522.940159] rtc: lost some interrupts at 512Hz.
[7237522.960106] rtc: lost some interrupts at 512Hz.
[7237522.980067] rtc: lost some interrupts at 512Hz.

---

### Post by dcstar on 2009-09-25
> **dmatrix said:**
> I have been experiencing problems with the clock running too fast in my Ubuntu JeOS vmware guests running on Ubuntu Server as the host. I am also running CentOS5 using the same software (Ubuntu Server, Vmware 1.x) and not having any issues with time at all in these vms.
...........

Any ideas or tips to make Ubuntu JeOS better as a guest vm? I have searched all the vmware threads in these forums and have gathered all the options from these threads.

[http://communities.vmware.com/thread/108877](http://communities.vmware.com/thread/108877)

---

