---
title: "wild dog trouble trying to install feisty 64"
date: 2007-05-16
forum: System76 Support
---

### Post by whb on 2007-05-16
I have my brand new wild dog computer with an AMD64 cpu and 4 gig of memory. I had the 32 bit feisty pre-installed forgetting that it would not see all the memory so I decided to install the 64 bit version.. With the live cd I cannot get past "kernel is alive"  etc before it hangs. I have tried the noapic and acpi=off boot options with the same result. Any advice welcome,

Hunter Blair

---

### Post by thomasaaron on 2007-05-17
Hello.

Are you sure you want 64-bit Ubuntu? We do not install it on our computers for several reasons. Some of them are outlined in this bug report:
[https://answers.launchpad.net/ubuntu/+question/4036](https://answers.launchpad.net/ubuntu/+question/4036)

My advice would be to re-install 32-bit.

You'll likely need some help setting up that GeForce8800 graphics card. It's a monster, but I have a tutorial that will help you.

Best,
Tom

---

### Post by whb on 2007-05-17
Thanks Tom.

 I have 2 drives and finally got the alternate 64 bit Feisty to install on the second SATA drive. I still have my intact 32 bit working on the first drive. The bios for some reason best known to itself does not recognize the second drive, but Feisty does when loaded. This means that GRUB does not believe that the second drive exists and so it cannot boot it. Foolishly, I flashed the bios with the utility cd and now it tells me that I have a new CPU installed and I have to press F2 to load the defaults and get to the GRUB loader. I still have a working system, but it is a pain to boot. 

As far as 64 bits goes, I will get rid of it off the drive and use drive two for storage as I originally intended before I got stupidly ambitious. Does anyone have any suggestions as to how I can restore the bios to its previous fine state,

Hunter

---

### Post by thomasaaron on 2007-05-17
I see.
Shoot me an email: support(at)system76(dot)com and I will send you the files for the bios upgrade that will patch the "new CPU" message.

Best,
Tom

---

