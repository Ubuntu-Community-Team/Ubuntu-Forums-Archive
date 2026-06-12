---
title: "Bootup optimization"
date: 2009-02-13
forum: System76 Support
---

### Post by sngltrk on 2009-02-13
I have a System76 Pangolin Performance laptop (model: panp4n).  I am very pleased with the performance of the laptop, except when it is booting.  I have installed BootChart to see what is holding things up.  It is unclear (to me) what is happening in the first 15-17 seconds of bootup, but after that it seems to move right along.  I haven't messed around with any of the setting in sysv-rc-conf.  I want to get a better idea of what is happening before I start making changes.  I have attached a copy of my latest bootchart output.

Thanks in advance for your help.

Sngltrk

---

### Post by thomasaaron on 2009-02-13
What's the total time it takes it to boot?

Also, please go to System > Admin > System76 Driver > Support > Create and post the logs.tar archive it creates in your home directory.

---

### Post by sngltrk on 2009-02-13
Boot Time as measured by BootChart 40 Sec.

Boot Time as measured by watch:
15 sec Bios
70 sec to Login Screen
100 sec to system ready to use.

I have attached the requested log.

Thanks,

Sngltrk

---

### Post by thomasaaron on 2009-02-13
OK. So that's over three minutes. I'm going from power button to desktop in about 1min 40 sec.

I'll have a look at your logs...

---

### Post by sngltrk on 2009-02-13
Sorry, times are not additive.  From power button to usable system is 115 secs or just under 2 minutes.

Sngltrk

---

### Post by thomasaaron on 2009-02-13
There are a ton of these in there...
> Feb 13 11:08:14 ubuntu kernel: [14207.080764] ACPI: EC: non-query interrupt received, switching to interrupt mode
Feb 13 11:08:14 ubuntu kernel: [14207.296043] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 11:08:14 ubuntu kernel: [14207.296088] usb usb1: root hub lost power or was reset
Feb 13 11:08:14 ubuntu kernel: [14207.296120] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Feb 13 11:08:14 ubuntu kernel: [14207.296164] usb usb2: root hub lost power or was reset
Feb 13 11:08:14 ubuntu kernel: [14207.296178] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Feb 13 11:08:14 ubuntu kernel: [14207.296227] usb usb3: root hub lost power or was reset
Feb 13 11:08:14 ubuntu kernel: [14207.312096] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Feb 13 11:08:14 ubuntu kernel: [14207.328143] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Feb 13 11:08:14 ubuntu kernel: [14207.416677] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb 13 11:08:14 ubuntu kernel: [14207.416731] usb usb5: root hub lost power or was reset
Feb 13 11:08:14 ubuntu kernel: [14207.416750] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Feb 13 11:08:14 ubuntu kernel: [14207.416799] usb usb6: root hub lost power or was reset
Feb 13 11:08:14 ubuntu kernel: [14207.416815] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb 13 11:08:14 ubuntu kernel: [14207.416867] usb usb7: root hub lost power or was reset
Feb 13 11:08:14 ubuntu kernel: [14207.432024] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Feb 13 11:08:14 ubuntu kernel: [14207.448307] NVRM: RmPowerManagement: 5

...which I find worrisome. Please disconnect all USB devices from your computer and see if it still takes as long to boot.

Also, there are a lot of lines in there indicating that your computer is awakening from a sleep state. I was assuming that you are saying it is slow booting from a fresh reboot. Am I mistaken?

---

### Post by sngltrk on 2009-02-13
You are correct, slow boot from a completely powered off system.  I typically put the laptop to sleep instead of shutting it off.  It wakes up faster than it reboots.

The only usb device that I'm currently using with the system is a wireless mouse (Logitech V450).  I don't think it makes a difference, but I'll verify after posting this.

Thanks

---

### Post by thomasaaron on 2009-02-13
OK. But just under two minutes doesn't seem that slow to me. Our shop machine is just under two minutes.

That's pretty normal for the Pangolin, I think. Maybe we can get some other customers to time their boot-up and weigh in.

---

### Post by sngltrk on 2009-02-13
Reboot time with no USB devices is the same as before.  I also get the following error during text bootup:

USB 1-2 device not accepting address .... wasn't quick enough to get the rest.  I'm wondering if that is causing the 15-20 sec of inactivity at the beginning of the bootchart chart?

I also have a 5 year old HP ZT3200 laptop that boots Intrepid in just over a minute.  My expectations were that this laptop would boot faster.  However, this laptop clearly out performs the old laptop in every other way.

---

### Post by thomasaaron on 2009-02-13
I'm not getting all of those USB errors on the shop machine. Googling them pulls up a lot of errors mounting printers and usb drives.

Can you tell me more about how you have your machine set up? What software do you have installed? What devices are you using with it?

Have you modified the BIOS? Are you running VirtualBox or VMWare? If so, do you have them set up to start automatically on boot?

---

### Post by sngltrk on 2009-02-13
I'm using the laptop as my primary machine.  I connect to an office network.  The only usb device that I use on a regular basis in the logitech mouse.  

I have the following software installed beyond what system76 loads.  AWN, gnome commander, virtualbox, dia, spicebird, skype, googleearth, openproj, openoffice3.0, texmaker, vlc, pdftk, and vobcopy.

The only program that I have load on startup is AWN.

How long does your test system say "starting up" before it acts like anything is happening.

---

### Post by thomasaaron on 2009-02-13
About 18 seconds.

---

### Post by thomasaaron on 2009-02-13
OK. I'm not so concerned with the USB errors. There are bugs all over the place that have those errors. This one...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/95144](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/95144)

...links it with suspend (which you are using a lot). So, we may need to do some research and testing on it later, but if all of your USB ports are working fine, then we can keep focusing on the problem at hand.


I'm curious about something, though. Could you please clear your logs by running these commands...

sudo rm /var/log/syslog
sudo rm /var/log/messages

Then, turn your computer all the way off and turn it back on. Then create logs via the System76 Driver and post them. I'd like to see a nice clean set of logs and see how they are timing the boot process.

---

### Post by sngltrk on 2009-02-13
OK, cleared the logs as requested.  Shutdown, rebooted and generated the log again.  I have attached in for you to review.

Thanks

---

### Post by thomasaaron on 2009-02-13
Thanks. So, all of those USB errors are gone. That's good. I'm certain now that it probably has to do with suspending. Will research more next week on it.

The logs don't give a good indication of boot-up time, but they do look pretty similar to my own logs.

So, honestly, I think everything is OK with your machine. If it's just under two minutes, that's the best I'm getting on the shop machine too.

I'm surprised that the HP boots so fast. Jaunty is supposed to seriously improve boot time by implementing an ext4 filesystem.

---

