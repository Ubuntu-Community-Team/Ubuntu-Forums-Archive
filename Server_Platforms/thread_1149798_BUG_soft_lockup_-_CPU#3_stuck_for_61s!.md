---
title: "BUG: soft lockup - CPU#3 stuck for 61s!"
date: 2009-05-05
forum: Server Platforms
---

### Post by Herbert256 on 2009-05-05
Hi,

After upgrading a box from Suse 10.1 to Ubuntu server 9.04 the systems 'freezes' after 2 minutes of uptime with below messages on the console.

[  272.909210] BUG: soft lockup - CPU#3 stuck for 61s! [ksoftirqd/3:13]
[  366.176505] BUG: soft lockup - CPU#3 stuck for 61s! [watchdog/3:14]
[  446.119988] BUG: soft lockup - CPU#3 stuck for 61s! [watchdog/3:14]

This did happen in Ubuntu Server 9.04. After installing 8.04.2 this did not happen again, however after upgrading 8.04.2 to 8.10 the problem did occurs again.

After running the system for a few hours, all 4 CPU's are named in those messages and with many software modules (like the watchdog and ksoftirqd)

The system looks freezed, console/telnet/ssh sessions are not working anymore. pinging the box does work, however the default ping time of 1-2 ms is now more than 500 ms.  A static HTML page from Apache takes a minute, normal this is a fraction of second.

Kind Regards, Herbert

---

### Post by msrinath80 on 2009-05-05
Yup, I've seen that before. You're most likely using an Intel processor (maybe a P4 or a Xeon). You need to install the latest intel microcode to fix this. In Debian it's either called intel-microcode or microcode.ctl or both. Try this:

sudo apt-get install intel-microcode microcode.ctl

Let us know if this works.

---

### Post by Herbert256 on 2009-05-05
Manny thanks for your answer, I will try this tomorrow at work.

Reading the details for those 2 packages it says that this microcode must be loaded at every boot. Is this command also adding an autostart entry or must I manually set a autostart entry for this?

Kind Regards, Herbert

---

### Post by msrinath80 on 2009-05-05
I would assume that Ubuntu does this automatically. Check for the kernel messages in the next boot.

---

### Post by Herbert256 on 2009-05-06
> **msrinath80 said:**
> ... Try this:

sudo apt-get install intel-microcode microcode.ctl

Let us know if this works.

No, it does not work, I have tried it on 8.10 and 9.04. We are now working on 8.04, that version is fine for us.

---

### Post by msrinath80 on 2009-05-06
Sorry, can't think of anything else. Just out of curiosity, why would you run Ubuntu on a server box anyway? Isn't Debian or an RHEL clone (Scientific Linux / CentOS) a wiser choice?

---

### Post by r0ydster on 2009-05-06
If this is going to be a "production" server, you should really consider running 8.04 LTS Server Edition (Hardy Heron).

This may eliminate your issue.

Mike

---

### Post by Herbert256 on 2009-05-06
> **r0ydster said:**
> If this is going to be a "production" server, you should really consider running 8.04 LTS Server Edition (Hardy Heron).

That is exactly the version we are running right now, however the box will be used for a zope/plone website and I prefer it that zope/plone was managed by Ubuntu. Hardy has Plone 2.5, and the developers want Plone 3. Server 8.10 and 9.04 have Plone 3. We have now zope/plone installed in /usr/local from the Plone website.

hgj

---

### Post by Herbert256 on 2009-05-06
> **msrinath80 said:**
> Sorry, can't think of anything else. Just out of curiosity, why would you run Ubuntu on a server box anyway? Isn't Debian or an RHEL clone (Scientific Linux / CentOS) a wiser choice?

??? Why is Ubuntu Server not a good server version of Linux?

---

### Post by r0ydster on 2009-05-06
Try these suggestions:

1) turn off ACPI in grub:

kernel          /boot/vmlinuz-2.6.17-10-server boot=/dev/sda1 ro acpi=off

try adding noapic nolapic as well


2) Do you see any info from your log files?

Are there any relevent error messages in /var/log/messages?
What about /var/log/kern.log, syslog, etc. ??

What kind of hardware is this?  MB? memory?

Ubuntu is debian based.  I believe that it is "good".  I'm aware of multiple companies using it for production systems.  However, for mission critical DB servers, my experience seems to be that those are usually Sun boxes running solaris.  Oracle on linux isn't quite ready for prime time yet.    

Mike

---

### Post by msrinath80 on 2009-05-07
> **Herbert256 said:**
> ??? Why is Ubuntu Server not a good server version of Linux?

I don't know. It just does not feel right, that's all. I mean a server is supposed to be very reliable and very stable for the most part. And Ubuntu does not quite rhyme with that. Debain does. RHEL does. SLES does. Maybe Slackware. Not Ubuntu. Not Fedora.

---

### Post by Herbert256 on 2009-05-08
> **r0ydster said:**
> Try these suggestions:

1) turn off ACPI in grub:

kernel          /boot/vmlinuz-2.6.17-10-server boot=/dev/sda1 ro acpi=off

try adding noapic nolapic as well

unfortanly I don't have the system anymore on 8.10 or 9.04 where this problem occurs, my end-users did want a working system, the system is now running Ubuntu Server 8.04, working fine now for almost 2 days, with 9.04 it was only 2 minutes :-)

> **r0ydster said:**
> Are there any relevent error messages in /var/log/messages?
What about /var/log/kern.log, syslog, etc. ??

I did have 1 a 2 minutes after a hard-reboot to look around before it happens again, I did never see anything strange in the logs except the earlyer reported messages.

> **r0ydster said:**
> What kind of hardware is this?  MB? memory?

MB: supermicro X7DVL-3
BIOS: Phoenix Technologies LTD, version 6.00 (01/26/2007)
CPU: Intel(R) Xeon(R) CPU E5335 @ 2.00GHz, version 6.15.7

lshw gives this version 6.15.7 now under Ubuntu 8.04 for the CPU. During the crashes with server 9.04 the microcode.ctl tool with intel-microcode version 20090330 was executed during boot.

---

### Post by Herbert256 on 2009-05-08
> **msrinath80 said:**
> I don't know. It just does not feel right, that's all. I mean a server is supposed to be very reliable and very stable for the most part. And Ubuntu does not quite rhyme with that. Debain does. RHEL does. SLES does. Maybe Slackware. Not Ubuntu. Not Fedora.

hmm, I'm happy now with Server 8.04 LTS, but maybe Debian itself was a better choice.

---

### Post by msrinath80 on 2009-06-09
Hi again,

It appears that turning off hyperthreading solves this soft lockup problem. You may want to give that a shot.

Cheers ...

---

