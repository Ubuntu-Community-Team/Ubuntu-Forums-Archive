---
title: "Wake-on-LAN (WOL) for System76 lemu2?"
date: 2012-09-25
forum: System76 Support
---

### Post by Geremia on 2012-09-25
My System76 Lemu2 has this version of Phoenix BIOS:
[CENTER]CALPELLACRB.86C.0000.X.0000000000

[/CENTER]
I called System76, and this is the most recent BIOS for the Lemu2, but unfortunately the BIOS doesn't support WOL. (Or does it?)

How do I get WOL functionality? I've tried```
suduo ethtool -s eth0 wol g
```but to no avail.

Thanks

---

### Post by Sidner on 2012-09-25
Have you entered the BIOS menu to check if it supports? You should start there...

[http://www.mythtv.org/wiki/ACPI_Wakeup#S3_.28Suspend_to_RAM.29]("http://www.mythtv.org/wiki/ACPI_Wakeup#S3_.28Suspend_to_RAM.29")

---

### Post by Geremia on 2012-09-25
> **Sidner said:**
> Have you entered the BIOS menu to check if it supports?Yes, there is no power management menu in my BIOS menu, thus there is no ACPI WOL feature> **Sidner said:**
> You should start there...

[http://www.mythtv.org/wiki/ACPI_Wakeup#S3_.28Suspend_to_RAM.29](http://www.mythtv.org/wiki/ACPI_Wakeup#S3_.28Suspend_to_RAM.29)Thanks
I ran```
echo 0 > /sys/class/rtc/rtc0/wakealarm ;  echo `date '+%s' -d '+ 2 minutes'` > /sys/class/rtc/rtc0/wakealarm ;   /usr/sbin/pm-suspend
```, but it didn't wake after 2 minutes.

Thanks again

---

### Post by isantop on 2012-09-26
Our laptops don't feature wake on LAN capability. For that, you would need to go with our Desktops.

---

### Post by Geremia on 2012-09-26
Are there any free BIOSs for Intel(R) Core(TM) i3 CPU U 330 @ 1.20GHz that I could try? Thanks

---

### Post by isantop on 2012-09-27
> **Geremia said:**
> Are there any free BIOSs for Intel(R) Core(TM) i3 CPU U 330 @ 1.20GHz that I could try? Thanks

BIOSs are specifically developed for each motherbaord, and are not interchangeable. There are no other BIOSs that are compatible with your Lemur.

---

### Post by Geremia on 2012-09-27
My LemU2 uses a CLEVO 3100 subsystem. The [CLEVO manual for it says, on PDF pg. 197, that it supports WOL]("ftp://sftp.clevo.com.tw/USRMANUAL/S310xx/S310x_EUM.zip"), even with the Phoenix Tech BIOS.[URL="ftp://sftp.clevo.com.tw/USRMANUAL/S310xx/S310x_EUM.zip"]
[/URL]

---

### Post by Geremia on 2012-09-27
> **isantop said:**
> BIOSs are specifically developed for each motherbaord, and are not interchangeable. There are no other BIOSs that are compatible with your Lemur.Not even [CoreBoot]("http://www.coreboot.org/Supported_Chipsets_and_Devices")?

I know my LemU2 has an Intel(R) Core(TM) i3 CPU U 330 @ 1.20GHz CPU and an Intel Corporation 82801 Mobile PCI Bridge, which [this page says CoreBoot v4 supports]("http://www.coreboot.org/Supported_Chipsets_and_Devices"). However, when I run **make menuconfig** for CoreBoot, there is no option for "CLEVO/KAPOK Computer Device 3100". Perhaps CoreBoot does not support CLEVO/KAPOK boards?

Thanks

---

### Post by isantop on 2012-09-28
> **Geremia said:**
> My LemU2 uses a CLEVO 3100 subsystem. The [CLEVO manual for it says, on PDF pg. 197, that it supports WOL]("ftp://sftp.clevo.com.tw/USRMANUAL/S310xx/S310x_EUM.zip"), even with the Phoenix Tech BIOS.[URL="ftp://sftp.clevo.com.tw/USRMANUAL/S310xx/S310x_EUM.zip"]
[/URL]

No, our systems do not use a Clevo BIOS.

> **Geremia said:**
> Not even [CoreBoot]("http://www.coreboot.org/Supported_Chipsets_and_Devices")?

I know my LemU2 has an Intel(R) Core(TM) i3 CPU U 330 @ 1.20GHz CPU and an Intel Corporation 82801 Mobile PCI Bridge, which [this page says CoreBoot v4 supports]("http://www.coreboot.org/Supported_Chipsets_and_Devices"). However, when I run **make menuconfig** for CoreBoot, there is no option for "CLEVO/KAPOK Computer Device 3100". Perhaps CoreBoot does not support CLEVO/KAPOK boards?

Thanks

Coreboot (and any other BIOS) has to be developed to support a specific motherboard. Many computer companies use more than one motherboard in even the same laptop model, and many of them use highly proprietary BIOSes in the first place, which makes developing Coreboot for them extremely difficult. Most of the systems Coreboot supports are desktop motherboards, and with all the laptops available out there, it's no wonder they haven't developed support for ours yet.

BIOS support is much more complex than OS support. You can't develop for one specific CPU, chipset, PCI controller, etc. You have to develop for an entire motheboard (since the BIOS handles all low-level communication between hardware and software). If a particular component isn't supported within the BIOS, then that component won't be available to the OS (at best), and the entire system could end up unstable or permanently broken (at worst). In short, the number of BIOSes available for any given system is usually one; the manufacturer's.

---

### Post by cy1 on 2012-12-07
Dang. The only time WOL really makes sense is for a laptop. You don't have to stress the case and your back opening it to turn it on when using an external monitor and keyboard. My desktops are either "on all the time" or not, and if they're not I sure don't want them turning on by themselves! Laptop's another matter though. Maybe I could rig up some kind of external button...

---

