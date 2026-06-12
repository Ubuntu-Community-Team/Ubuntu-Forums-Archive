---
title: "HU: A bug from 17.10 that might affect us with 18.04-to-be..."
date: 2017-12-20
forum: Ubuntu Development Version
---

### Post by zika on 2017-12-20
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

---

### Post by uRock on 2017-12-20
From the bug report.> SRU Justification

Impact: Many users are reporting issues with bios corruption with 17.10. This seems to stem from enabling the intel-spi-* drivers in the kernel, which don't appear to be ready for use on end-user machines.

Fix: Disable this driver.

Test Case: Fix has been verified by our HWE team on affected hardware.

Regression Potential: Minimal, it's unlikely anyone is actually doing anything which requires this driver.

---

---

### Post by IanW on 2017-12-21
I blame the laptop manufacturers for going off-standard with their BIOS/UEFI builds.

---

### Post by uRock on 2017-12-21
Lenovo is known for their colorful BIOS builds. [https://thehackernews.com/2015/09/lenovo-laptop-virus.html](https://thehackernews.com/2015/09/lenovo-laptop-virus.html)

---

### Post by rrnbtter on 2017-12-22
Greetings,

> **uRock said:**
> Lenovo is known for their colorful BIOS builds. 

They are definitely building them. 

sudo dmidecode -s bios-vendor
[sudo] password for rrnbtter: 
LENOVO
rrnbtter@rrnbtter-110-15ISK:~$ 
After Investigating all of this I think I did the right thing to wipe Win10, set bios to legacy and Install my 17.10 (now 18.04 dev) without UEFI. That being said, I have yet to see my 110-15isk on the list. But it is a Lenovo Bios.

---

### Post by #&amp;thj^% on 2017-12-22
> **rrnbtter said:**
> Greetings,



They are definitely building them. 

sudo dmidecode -s bios-vendor
[sudo] password for rrnbtter: 
LENOVO
rrnbtter@rrnbtter-110-15ISK:~$ 
After Investigating all of this **_I think I did the right thing to wipe Win10, set bios to legacy_** and Install my 17.10 (now 18.04 dev) without UEFI. That being said, I have yet to see my 110-15isk on the list. But it is a Lenovo Bios.
+1 Same here.
```
sudo dmidecode -s bios-vendor
[sudo] password for me: 
AMI

```
And:
```
Machine:   Device: desktop System: HP product: 750-417c v: 1.01 serial: N/A
           Mobo: HP model: 828A v: 1.01 serial: N/A
           **_UEFI [Legacy]: AMI v: F.14 date: 09/19/2016_**

```
HP's aren't much better.
Try and install a Nvidia GPU card on one of these in UEFI with Windows 10.

---

### Post by linuxyogi on 2017-12-23
Hi, I am using Xubuntu 18.04. After reading all that I am feeling a bit nervous. How can I be sure this bug doesn't effect my hardware ?  ```
 $ sudo dmidecode -s bios-vendor [sudo] password for mypc:  American Megatrends Inc.
```  I know I may be worrying for no reason but still needed to know I am safe.

---

### Post by rrnbtter on 2017-12-23
Greetings,
Are you dual booting Windows OS?
What kernel are you using, output of  "uname -a".
If it is just a linux install, output of       [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
Just for starter's.

---

### Post by linuxyogi on 2017-12-23
> **rrnbtter said:**
> Greetings,
Are you dual booting Windows OS?
What kernel are you using, output of  "uname -a".
If it is just a linux install, output of       [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
Just for starter's.

No I am not dual booting  Windows. 

```
$ uname -a
Linux mypc 4.13.0-17-generic #20-Ubuntu SMP Mon Nov 6 10:04:08 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

```
$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
EFI boot on HDD

```

---

### Post by rrnbtter on 2017-12-23
Greetings,
Not booting Windows = Good!
Kernel [COLOR=#000000][FONT=&amp]4.13.0-21 has been released to fix this problem. It is in the "Proposed" repos. 
[/FONT][/COLOR]If you are not booting Windows then a Legacy install is the safer option. 

Note: It seems to me that much of this problem is due to bios tampering on behalf of the PC vendors. So the question as to whether you are at risk at all may be hard to determine. Lenovo has been the big culprit but the problem has been found elsewhere.

If it were me, I would backup /Home and set the bios to legacy and reinstall.

---

### Post by linuxyogi on 2017-12-23
> **rrnbtter said:**
>  4.13.0-21 has been released to fix this problem. It is in the "Proposed" repos. 

I just enabled "Proposed" and upgraded the kernel.

I am now running ```
4.14.0-13-generic  
```

Am I safe now ?

---

### Post by zika on 2017-12-23
> **linuxyogi said:**
> Am I safe now ?Simply check changelog file(s)...

---

### Post by linuxyogi on 2017-12-23
> **zika said:**
> Simply check changelog file(s)...

Never done that before. Where are the changelog files ? How do I read them ?

---

### Post by linuxyogi on 2017-12-23
Did a check with the following result  
```
$ grep SPI_INTEL_SPI_PLATFORM /boot/config*
 	/boot/config-4.13.0-17-generic:CONFIG_SPI_INTEL_SPI_PLATFORM=m
 	/boot/config-4.14.0-13-generic:# CONFIG_SPI_INTEL_SPI_PLATFORM is not set
```

Then did

```
sudo apt remove linux-image-4.13.0-17-generic 
```

Now I get 

```
$ grep SPI_INTEL_SPI_PLATFORM /boot/config*
# CONFIG_SPI_INTEL_SPI_PLATFORM is not set 
```.

I guess I am okay now. Thanks for your replies.

---

### Post by rrnbtter on 2017-12-23
Greetings,
@linuxyogi
Looks good, however I would't say ok since that would be foolish.  Nothing less than a Legacy install would do it for me. The gravity of the problem is too great. One kernel upgrade and you could be back where you started. 
If the end result of the UEFI boot is vendor installed spyware then that could very well have been the original intent.  It is a dangerous backdoor perpetrated and put upon all of us. I take it to be my responsibility to protect myself from this foolishness.  Legacy boot/No windows.

---

### Post by linuxyogi on 2017-12-23
> **rrnbtter said:**
> One kernel upgrade and you could be back where you started.    You mean a future kernel can actually reintroduce this bug ?

---

### Post by rrnbtter on 2017-12-23
Greetings, 
@linuxyogi, I'm saying that a future kernel update could inadvertently fail to protect from the bug.  It isn't on it's face an actual bug.  Millions of Windows users are buying these UEFI machines with spyware and data mining software embedded in the bios and installed after purchase and boot.  They are collecting data from you (Windows Users) and selling it to advertisers primarily. 
Linux is not susceptible to this spyware. However, in a dual boot situation the Linux install could leave the bios in a non-writable condition and make it impossible for the user Windows or Linux to access the install or log into the bios to change the boot settings to reinstall the system. It can turn you computer into a doorstop. It can be fixed but most of these computers are so cheap that it isn't worth the time or effort. Some users want to blame Ubuntu but it would be close to impossible for the kernel writers to assess every bios produced and most users expect a Linux download to install on anything, ignoring the Ubuntu authorized list.  
Hence, Legacy install/No Windows.

Hope I haven't said too much here and get myself blacklisted. Just my take on things. 

PS Thank you Zika for starting this thread.

---

### Post by rrnbtter on 2017-12-23
Greetings,
The following is the output from my bios. I'm not an expert on this but it is the bolded line that concerns me. There may be other data here to be concerned about. Not sure.  The UEFI was supposed to protect from rootkit viruses but instead it is a rootkit virus. 

```
sudo dmidecode -t bios -q
[sudo] password for rrnbtter: 
BIOS Information
    Vendor: LENOVO
    Version: 1TCN19WW(V2.00)
    Release Date: 08/09/2016
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 6144 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        **Targeted content distribution is supported**
        UEFI is supported
    BIOS Revision: 2.19
    Firmware Revision: 2.19
```

---

### Post by QIII on 2017-12-23
Please stop with the FUD and the tinfoil-hattery.

This is nothing more, nor less, than faulty and sloppy BIOS development on the part of the hardware vendor and (dare I say it) a very, very bad miss for Canonical.  Both parties had a part in this.

There was no directed malice.  There was only poor firm/software and a failure in quality/testing engineering.  Canonical needs to own up to its part.  Lenovo to theirs.

Keep this thread to objective support and the search for solutions or it will be closed.

---

### Post by zika on 2017-12-24
> **QIII said:**
> Keep this thread to objective support and the search for solutions or it will be closed.[IMG]https://emojipedia-us.s3.amazonaws.com/thumbs/120/apple/118/thumbs-up-sign_1f44d.png[/IMG]

---

### Post by zika on 2017-12-31
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.10-Laptop-Fix](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.10-Laptop-Fix)

---

### Post by ventrical on 2018-01-03
> **zika said:**
> [https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.10-Laptop-Fix](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.10-Laptop-Fix)

Oh Really!


From bionic-desktop iso Jan. 0101/18 daily.

---

### Post by oldfred on 2018-01-06
If you remove a hard drive with UEFI, and then reinstall it, most UEFI do not re-read the ESP for entries. Some seem to find the Windows entry.
I always create the fallback entry also, /EFI/Boot/bootx64.efi as copy of shimx64.efi.
You can either re-install grub, or use efibootmgr to add entries into UEFI on motherboard.
man efibootmgr

---

### Post by ventrical on 2018-01-10
> **oldfred said:**
> If you remove a hard drive with UEFI, and then reinstall it, most UEFI do not re-read the ESP for entries. Some seem to find the Windows entry.
I always create the fallback entry also, /EFI/Boot/bootx64.efi as copy of shimx64.efi.
You can either re-install grub, or use efibootmgr to add entries into UEFI on motherboard.
man efibootmgr

It didnt work but disabling UEFI and enable legacy worked just fine.

---

