---
title: "Hibernate not envoked when lid is closed"
date: 2013-07-12
forum: Ubuntu Development Version
---

### Post by EricKit on 2013-07-12
When I go to settings -> Power and I put hibernate in both on power and not on power when lid is closed, it does not work.  When I close the screen the screen goes black and when I open it there is a prompt for me to type in my password, but the computer never turns off.  It doesn't fully suspend either, I can tell because the power light stays on.  

sudo pm-hibernate works.

I had edited the local policies to allow hibernate in ```
/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```

Someone here on askubuntu has the same issue. 
[http://askubuntu.com/questions/291903/ubuntu-not-is-hibernating-when-lid-is-closed](http://askubuntu.com/questions/291903/ubuntu-not-is-hibernating-when-lid-is-closed)

---

### Post by Toz on 2013-07-12
What is the make and model of your computer?

What video card do you have? Open a terminal window, type in the following command and post back the results:
```
sudo lspci -vnn | grep -A12 VGA
```

Any special additions to your kernel command line?
```
cat /proc/cmdline
```

Some info about your swap file:
```
swapon -s
```

Can you also post your /var/log/pm-suspend.log file:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

And finally:
```
cat /var/log/syslog | grep PM:
```

---

### Post by EricKit on 2013-07-12
Thank you for the detailed explanation on how to get you the information you need!  I have a Lenovo Twist:

Here is the link
[http://paste.ubuntu.com/5868800/](http://paste.ubuntu.com/5868800/)

I just edited the post because I did a sudo pm-hibernate at 2:02 PM today.  Then I set it to hibernate and tried it 3 times by closing the lid.  It never powered down the laptop.  Then I set it to suspend and closed the lid and let it suspend.  Reposted the link.  I believe those tests start on line 7830.  I appears the 3 attempts to hibernate by closing the lid never even attempted to hibernate.  It just skips from the hibernate via sudo pm-hibernate to the suspend from closing the lid.

```
$ sudo lspci -vnn | grep -A12 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:2205]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])

```
```
$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.10.0-2-generic.efi.signed root=UUID=4ed0903a-c5d2-4b4d-b66c-3970006a769a ro RESUME=UUID=6bbe46ed-444f-410b-930f-41aa2e5ad452 quiet splash vt.handoff=7

```
```
$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda7                               partition    8388604    36    -1

```
```
$ cat /var/log/syslog | grep PM:
Jul 12 09:46:28 Laptop kernel: [28829.776732] PM: Syncing filesystems ... done.
Jul 12 09:46:28 Laptop kernel: [28830.666606] PM: suspend of devices complete after 691.753 msecs
Jul 12 09:46:28 Laptop kernel: [28830.666743] PM: late suspend of devices complete after 0.135 msecs
Jul 12 09:46:28 Laptop kernel: [28830.746567] PM: noirq suspend of devices complete after 79.785 msecs
Jul 12 09:46:28 Laptop kernel: [28831.447622] PM: Saving platform NVS memory
Jul 12 09:46:28 Laptop kernel: [28831.760506] PM: Restoring platform NVS memory
Jul 12 09:46:28 Laptop kernel: [28832.137114] PM: noirq resume of devices complete after 159.897 msecs
Jul 12 09:46:28 Laptop kernel: [28832.137267] PM: early resume of devices complete after 0.125 msecs
Jul 12 09:46:28 Laptop kernel: [28834.464535] PM: resume of devices complete after 2326.183 msecs

```

---

### Post by Toz on 2013-07-12
Well, the good news is that your system is going through complete suspend&hibernate/resume cycle (in other words, its not being inhibited anywhere). The bad news is, something is waking it up right after it goes to sleep.

Can we have a look at your wakeups?
```
cat /proc/acpi/wakeup
```

And info on your network cards:
```
sudo lspci -vnn | grep -A12 -i network
```

In the meantime, can you try the **acpi_osi=linux** kernel parameter? See the "Kernel Boot Parameters" link in my signature for information on how to test it.

Would also be curious to know the model number of your twist. The following command should retrieve it:
```
sudo dmidecode -s system-product-name
```

---

### Post by EricKit on 2013-07-12
Toz I don't think it is trying to hibernate at all.  It doesn't add anything to that log when I try to hibernate it closing the lid.  The log only gets new information when I actual force a hibernate with the terminal. I verified this again just now.  Also added acpi_osi to GRUB, rebooted, tested for same result.

```
$ cat /proc/acpi/wakeup 
Device    S-state      Status   Sysfs node
P0P1      S4    *disabled
EHC1      S3    *enabled   pci:0000:00:1d.0
EHC2      S3    *enabled   pci:0000:00:1a.0
XHC      S3    *enabled   pci:0000:00:14.0
HDEF      S3    *disabled  pci:0000:00:1b.0
RP01      S4    *disabled  pci:0000:00:1c.0
PXSX      S4    *disabled  pci:0000:02:00.0
RP02      S4    *disabled  pci:0000:00:1c.1
PXSX      S4    *disabled  pci:0000:03:00.0
RP03      S4    *disabled
PXSX      S4    *disabled
RP04      S4    *disabled  pci:0000:00:1c.3
PXSX      S4    *enabled   pci:0000:04:00.0
RP05      S4    *disabled
PXSX      S4    *disabled
RP06      S4    *disabled
PXSX      S4    *disabled
RP07      S4    *disabled
PXSX      S4    *disabled
RP08      S4    *disabled
PXSX      S4    *disabled
PEG0      S4    *disabled
PEGP      S4    *disabled
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
LID0      S4    *enabled 

```
```

$ sudo lspci -vnn | grep -A12 -i network
[sudo] password for eric: 
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f1d00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-3d-ff-ff-bf-c0-14
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl

```

The Thinkpad Twist is a 230U
```

$ sudo dmidecode -s system-product-name
33474HU

```

---

### Post by Toz on 2013-07-12
> **EricKit said:**
> Toz I don't think it is trying to hibernate at all.  It doesn't add anything to that log when I try to hibernate it closing the lid.  The log only gets new information when I actual force a hibernate with the terminal. I verified this again just now.
Perhaps [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1194328") is relevant then. If you force a hibernate from the terminal, does the system hibernate or does it return right away (like your initial problem)?

> 
```
$ cat /proc/acpi/wakeup 
Device    S-state      Status   Sysfs node
P0P1      S4    *disabled
EHC1      S3    *enabled   pci:0000:00:1d.0
EHC2      S3    *enabled   pci:0000:00:1a.0
XHC      S3    *enabled   pci:0000:00:14.0
HDEF      S3    *disabled  pci:0000:00:1b.0
RP01      S4    *disabled  pci:0000:00:1c.0
PXSX      S4    *disabled  pci:0000:02:00.0
RP02      S4    *disabled  pci:0000:00:1c.1
PXSX      S4    *disabled  pci:0000:03:00.0
RP03      S4    *disabled
PXSX      S4    *disabled
RP04      S4    *disabled  pci:0000:00:1c.3
PXSX      S4    *enabled   pci:0000:04:00.0
RP05      S4    *disabled
PXSX      S4    *disabled
RP06      S4    *disabled
PXSX      S4    *disabled
RP07      S4    *disabled
PXSX      S4    *disabled
RP08      S4    *disabled
PXSX      S4    *disabled
PEG0      S4    *disabled
PEGP      S4    *disabled
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
LID0      S4    *enabled 

```

Using lspci, can you verify which devices are at these addresses:
EHC1      S3    *enabled   pci:0000:00:1d.0
EHC2      S3    *enabled   pci:0000:00:1a.0
XHC       S3    *enabled   pci:0000:00:14.0
PXSX      S4    *enabled   pci:0000:04:00.0

---

### Post by EricKit on 2013-07-12
If I hibernate from the terminal it works just fine.  I think that bug report is relevant and this just must be a bug.  Thanks for the information!

```
EHC1      S3    *enabled   pci:0000:00:1d.0
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
```

```
EHC2      S3    *enabled   pci:0000:00:1a.0
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
```

```
XHC       S3    *enabled   pci:0000:00:14.0
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
```

```
PXSX      S4    *enabled   pci:0000:04:00.0
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
```

---

### Post by mc4man on 2013-07-12
> **EricKit said:**
> When I go to settings -> Power and I put hibernate in both on power and not on power when lid is closed, it does not work.  When I close the screen the screen goes black and when I open it there is a prompt for me to type in my password, but the computer never turns off.  It doesn't fully suspend either, I can tell because the power light stays on.  

sudo pm-hibernate works.

I had edited the local policies to allow hibernate in ```
/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```

Someone here on askubuntu has the same issue. 
[http://askubuntu.com/questions/291903/ubuntu-not-is-hibernating-when-lid-is-closed](http://askubuntu.com/questions/291903/ubuntu-not-is-hibernating-when-lid-is-closed)
I can't hibernate because 1. it may not work & 2. use a very small swap,  so just a thought.

Even though you changed the .pkla in /etc it may be overridden by the one in /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla (from my experience /var/lib/polkit-1/* trumps all
In 13.10 there are 2 policies in there concerning hibernate, try adjusting both.
(you need to be root to browse there or just open in editor of choice - 
```
sudo nano /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```

(after edit - ctrl+o, enter, ctrl+x if using nano

---

### Post by EricKit on 2013-07-12
Thanks!! Changing the two settings in 10-vendor.d fixed it!

Did some reading and realized the order in which Ubuntu does local policies.  I put my 10-vendor.d file back to the original and modified my file to add the second entry:
Edit the two hibernate entries to read:

  
```

[Enable hibernate by default in upower]
Identity=unix-user:* 
Action=org.freedesktop.upower.hibernate 
ResultActive=yes  

[Enable hibernate by default in logind] 
Identity=unix-user:* 
Action=org.freedesktop.login1.hibernate 
ResultActive=yes
```

The 1st setting enables you to pick hibernate in the power options, but the 2nd setting is also required to be yes to actually hibernate.  Since the 10- file was setting it to no, when the 50- file ran it was still set to no since it only changed the upower option.

Here is a link that describes how they are ran under the section "Evaluation Order"

[http://manpages.ubuntu.com/manpages/maverick/man8/pklocalauthority.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/pklocalauthority.8.html)

---

### Post by mc4man on 2013-07-13
Thanks for manpage

---

### Post by ooddiittyy on 2013-09-12
I too have a problem with hibernate on lid closed, but it has an additional eccentricity: by editing the /etc/../50-local.d/com.ubuntu.enable-hibernate.pkla file and adding the two entries referenced in post #9, I was able to get hibernate working on lid closure just fine, although I was never able to get it to show up as an option in the power menu on the desktop (perhaps due to interplay between the /var/ and /etc/ hierarchies?). Recently, however, I started up the laptop and noticed that the "hibernate" option is missing from the drop-down menu under "When lid is closed" on battery. What's strange is a) that is reverted without apparent cause and b) that the "hibernate" option is still listed under "When power is critically low". I have also now tried modifying the /var/lib/../10-vendor.d/com.ubuntu.desktop.pkla file to no avail.

I'm on 13.10, pm-hibernate works fine and like I said, until today the fix mentioned in this thread worked like a charm. I have very minimal experience with Linux in general, and any help would be most appreciated.

---

