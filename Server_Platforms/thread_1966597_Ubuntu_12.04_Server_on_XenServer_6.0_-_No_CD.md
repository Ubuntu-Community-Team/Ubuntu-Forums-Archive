---
title: "Ubuntu 12.04 Server on XenServer 6.0 - No CD"
date: 2012-04-27
forum: Server Platforms
---

### Post by Dkl on 2012-04-27
Hi all, im experiencing this issue.. i can select languages and keyboard locales then when it tries to mount the CD-ROM it says that no CDROM is available... 

This happen with the local iso mounted either via cifs or locally stored.. im trying a burned copy of it directly in the proliant that im using for testing.

Hope someone could help..

I've found the bug description at [https://bugs.launchpad.net/bugs/982430](https://bugs.launchpad.net/bugs/982430)
but still unassigned.. 

Can i install 11.10 then upgrade?

---

### Post by ShinCTL on 2012-04-27
Same for me.. :P

---

### Post by Gohtar on 2012-04-27
Same here

---

### Post by Gohtar on 2012-04-30
Anyone? Anything? Troubleshooting tips maybe?

---

### Post by Dkl on 2012-05-02
Alternate CD Install not working too...

Looking for support in XenForums, when i've got a working solution i'll post here.

I can test in both xenservers version 5.6 and 6 so stay tuned.

---

### Post by Dkl on 2012-05-04
Smile.. NOACPI did the trick.. press F6 before installation and cd works..

but if I need acpi? :o)

---

### Post by Gohtar on 2012-05-15
Yep confirmed that NOACPI worked for me too.

Also installing on XenServer 5.6 FP1 works without having to disable ACPI.

Thanks

---

### Post by volkswagner on 2012-05-15
> **Gohtar said:**
> Yep confirmed that NOACPI worked for me too.

Also installing on XenServer 5.6 FP1 works without having to disable ACPI.

Thanks


I have not been able to get anything to work except memtest using 12.04 32bit-server .iso.  I have only tried via .iso on Share, not an burned CD.

I have tried NOACPI and all other F6 options.  

Using XenServer 5.6.0  Build Number 31188p.

---

