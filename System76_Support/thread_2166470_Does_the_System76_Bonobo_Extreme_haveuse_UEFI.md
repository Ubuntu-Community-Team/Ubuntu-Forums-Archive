---
title: "Does the System76 Bonobo Extreme have/use UEFI"
date: 2013-08-09
forum: System76 Support
---

### Post by hawkmage on 2013-08-09
I am considering getting a System76 Bonobo Extreme and was wondering if it used only a BIOS boot loader or UEFI?  

If it has UEFI has anyone used it and what were your experiences?

---

### Post by carl_george2 on 2013-08-09
I don't have a System76 machine, but here is a command you can run to check.

```
if [[ -e /sys/firmware/efi/vars ]] || [[ -e /sys/firmware/efi/efivars ]]; then echo "booted from EFI"; else echo "booted from BIOS"; fi
```

Reference: [https://wiki.archlinux.org/index.php/EFI#UEFI_Variables_Support](https://wiki.archlinux.org/index.php/EFI#UEFI_Variables_Support)

---

### Post by hawkmage on 2013-08-09
Thanks for the response but as I said in my post "I am considering getting a System76 Bonobo Extreme" so I have nothing to run it on.

---

### Post by carl_george2 on 2013-08-09
Sorry, I misspoke.  That is a command that a Bonobo Extreme owner can run to find out for sure and then report back.  Hopefully an owner sees it and lets us know; I am curious as well.

---

### Post by hawkmage on 2013-08-09
From some research I have done it looks like it does have UEFI but I do not know if it is enabled by default.  Having tried installing Linux on Apple Mac hardware that uses an older version of EFI I know that it can be a hassle without a good EFI boot manager, I have had to resort to building my own EFI boot partition and using rEFInd as a EFI boot manger.

---

### Post by jaylittle on 2013-08-09
I have a bonx6 (one revision back) and it uses a standard BIOS bootloader.  No UEFI here.

---

### Post by hawkmage on 2013-08-09
According to a review of the Bon6 on Jupiter Broadcasting ([http://www.jupiterbroadcasting.com/28616/bonobo-extreme-review-las-s24e09/](http://www.jupiterbroadcasting.com/28616/bonobo-extreme-review-las-s24e09/) at about 1:05) they talk about it being Win 8 certified and that it has EFI support.

---

### Post by racaspercom on 2013-08-17
> **carl_george2 said:**
> I don't have a System76 machine, but here is a command you can run to check.

```
if [[ -e /sys/firmware/efi/vars ]] || [[ -e /sys/firmware/efi/efivars ]]; then echo "booted from EFI"; else echo "booted from BIOS"; fi
```

Reference: [https://wiki.archlinux.org/index.php/EFI#UEFI_Variables_Support](https://wiki.archlinux.org/index.php/EFI#UEFI_Variables_Support)

I entered this command on my Bonobo 6 and got the "booted from BIOS" message

---

### Post by RichardET on 2013-08-17
I think that it is true that System76 does not use UEFI, because I called them last year when I was looking at a new laptop.  My older Lenovo V470 has this UEFI issue, so I did not want to make the same mistake twice without checking, but System76 cannot match the pricing of Lenovo, and I opted for a W530, and I use VMWare, running Ubuntu as a VM.  I am on it now, its pretty good, so my suggestion is to buy the most hardware you can afford, and be flexible with the OS, because tools like VMWare coupled with advanced Intel i7 processors have completely changed computing.
To me, hardware compatibility is more of an abstraction, and there is never a reason to make it a distraction!

I ran same code in my VMWare session:

rthornto@ubu1:~$ if [[ -e /sys/firmware/efi/vars ]] || [[ -e /sys/firmware/efi/efivars ]]; then echo "booted from EFI"; else echo "booted from BIOS"; fi
booted from BIOS
rthornto@ubu1:~$

---

### Post by him610 on 2013-08-17
Fwiw, I have a fairly recent (December 2012)  Pangolin 9 which I ran the code fragment on.
Response, "booted from BIOS"

---

### Post by phxpx on 2013-08-18
I have a Gazelle Professional GazP9 and it says "booted from BIOS"
Afterall one of the main reasons, I bougth this laptop from System76 is I don't want UEFI.

---

### Post by isantop on 2013-08-20
All current System76 laptops and desktop use a traditional BIOS. There are EFI elements in some of the newer systems, but they're still using BIOS overall. 

We do plan on implementing UEFI-based firmware across our range for 13.10 in October. Existing customers with current-gen hardware will be given the option of switching to UEFI. We don't have plans to enforce any secure boot settings.

EDIT: Stay tuned for September. I'm doing a talk at Ohio LinuxFest 2013 regarding myths around UEFI.

---

### Post by golfdiesel on 2014-05-28
> **isantop said:**
> All current System76 laptops and desktop use a traditional BIOS. There are EFI elements in some of the newer systems, but they're still using BIOS overall. 

We do plan on implementing UEFI-based firmware across our range for 13.10 in October. Existing customers with current-gen hardware will be given the option of switching to UEFI. We don't have plans to enforce any secure boot settings.

EDIT: Stay tuned for September. I'm doing a talk at Ohio LinuxFest 2013 regarding myths around UEFI.

I haven't seen any info on the possibility to switch to UEFI for my gazp9. Is it still coming?

---

### Post by Laurence_Montrose on 2014-06-07
I just ran the above command, and it still says booted from BIOS for 14.04, on a 2 week old BonX 8, so I'm guessing not...

---

### Post by zeke7237 on 2014-09-13
I know this is a relatively old thread, but I thought I'd throw this out there ..

I've successfully updated a bon7x with the Clevo SM370P bios offered at premamod.com
This gave me UEFI boot and enabled me to set up a triple-boot system with OSX, xubuntu and win8.1 on a single 240GB SSD

Of course my warranty is probably void now :)

---

