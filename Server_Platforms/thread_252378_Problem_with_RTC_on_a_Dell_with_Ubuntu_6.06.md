---
title: "Problem with RTC on a Dell with Ubuntu 6.06"
date: 2006-09-06
forum: Server Platforms
---

### Post by jkugler on 2006-09-06
](*,)

FYI, this is a Dell PowerEdge 830 with an Intel Pentium D CPU 2.80GHz.

Well, originally this started out as a Debian problem.  Then it turned into an Ubuntu problem.  How?  Read on. :)

I had a Dell system set up with kernel linux-image-2.6.16-2-686-smp.  During boot, it could not set the clock, and was giving me the error:

select to /dev/rtc to wait for clock tick timed out

This was creating problems for applications that used the real time clock, namely VMWare Server, which uses the RTC to keep the guest OS's clocks in sync.

When VMWare server (actually the vmware-rtc module) was running, syslog would fill with messages like these:

Sep 2 06:25:13 <hostname> kernel: rtc: lost some interrupts at 512Hz. 
Sep 2 06:25:44 <hostname> last message repeated 1521 times 
Sep 2 06:26:45 <hostname> last message repeated 3050 times 
Sep 2 06:27:46 <hostname> last message repeated 3050 times 
Sep 2 06:28:47 <hostname> last message repeated 3049 times

That's 3050 messages every 61 seconds.  Well, after going through the VMWare forums, someone made a comment that since Etch was bleeding edge, it would really not be supported.  So I decided to go with a distro that *is* officially support by VMWare, and wasn't currently under heavy development: Ubunutu.

I reinstalled the machine with Ubunut 6.06.1 from the Alternate CD, since I had MD devices to set up.  The only option for the kernel was an i386 kernel (2.6.15-26-386), so I installed that.  Upon boot, what does greet me, except:

select to /dev/rtc to wait for clock tick timed out

I've not yet installed an i686 kernel or VMWare server to see if I get the same log flooding.

Searching on /dev/rtc in Ubuntu bugs nets me nothing.  I really don't want to have to tell my boss that this machine isn't supported by Linux...ship it back. :)  Dell will preinstall Redhat and Suse on this machine, so I'm sure I'm missing something somewhere.

Output of lspci:

0000:00:00.0 Host bridge: Intel Corporation E7230 Memory Controller Hub
0000:00:01.0 PCI bridge: Intel Corporation E7230 PCI Express Root Port
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
0000:00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:02:00.0 PCI bridge: Intel Corporation 6702PXH PCI Express-to-PCI Bridge A (rev 09)
0000:04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
0000:06:05.0 VGA compatible controller: XGI - Xabre Graphics Inc Volari Z7

Any ideas before I file a bug?

j

---

### Post by jkugler on 2006-09-07
Well, I'm not exactly sure *why* it's solved, but I do know it is solved, at least for now.  Just for the sake of experimentation, I installed the linux-server kernel package: no more RTC errors, and VMWare server runs without generating all the lost interrupts errors.

So, whatever gets changed in the -server kernel apparently fixed it.

Kernel currently running: 2.6.15-26-server

If anyone has any ideas about this, I'd still like to hear them.

j

---

### Post by reenen on 2006-09-08
> **jkugler said:**
> Well, I'm not exactly sure *why* it's solved, but I do know it is solved, at least for now.  Just for the sake of experimentation, I installed the linux-server kernel package: no more RTC errors, and VMWare server runs without generating all the lost interrupts errors.

So, whatever gets changed in the -server kernel apparently fixed it.

Kernel currently running: 2.6.15-26-server

If anyone has any ideas about this, I'd still like to hear them.

j

I found a german site where somebody figured it out:

Beim Kernel habe ich die Timer frequency von 250Hz auf 1000Hz 
erhöht, natürlich Kernel neu kompiliert und das Problem war weg.

[http://linuxinfoserver.de/forums/showthread.php?p=1329432](http://linuxinfoserver.de/forums/showthread.php?p=1329432)

Which says that changing the timer frequency from 250Hz to 1000Hz in the kernel fixes this problem. This seems to require a kernel recompile.

Same problem as you on Debian etch btw, though it seems to run fine regardless of the logs. Will recompile anyway.

-R

---

