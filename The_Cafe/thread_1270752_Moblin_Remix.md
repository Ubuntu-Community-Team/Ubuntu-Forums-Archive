---
title: "Moblin Remix"
date: 2009-09-20
forum: The Cafe
---

### Post by brandoncolorado on 2009-09-20
I am currently downloading the LiveCD for Ubuntu Moblin Remix.  

Has anyone else tried this on a netbook yet?

---

### Post by NormanFLinux on 2009-09-20
I burned Ubuntu Moblin Remix to a CD but it does not boot. None of the choices boot to the desktop.

---

### Post by gnomeuser on 2009-09-20
It's the Moblin you can get from moblin.org but with brown. Really there is no real additions outside shipping the hopelessly bloated OpenOffice on machines that are way underpowered to run it.

It is in need of stability and polish, both things should be able to happen in time for Karmic+1.

---

### Post by brandoncolorado on 2009-09-20
Can anyone tell me how to do this without an ethernet port?
[http://slaine.org/_slaine/Dell_Mini_9.html](http://slaine.org/_slaine/Dell_Mini_9.html)

---

### Post by gnomeuser on 2009-09-20
> **brandoncolorado said:**
> Can anyone tell me how to do this without an ethernet port?
[http://slaine.org/_slaine/Dell_Mini_9.html](http://slaine.org/_slaine/Dell_Mini_9.html)

1) download files on second machine
2) copy files to usb key
3) profit?

---

### Post by NormanFLinux on 2009-09-20
Ubuntu 9.04 supports Broadcom wireless OOTB. UBMR is based on Karmic Koala alpha so I presume it doesn't see the drivers? Then you will probably have to connect via Ethernet to install them.

---

### Post by brandoncolorado on 2009-09-20
> **gnomeuser said:**
> 1) download files on second machine
2) copy files to usb key
3) profit?

I'm almost (not quite) half retarded, so I need more explanation.

Would I have to do this for the packages that they list too (the repository ones)?  If so, do I just sudo install (their directory location)?

---

### Post by NormanFLinux on 2009-09-20
Or you could use Ndiswrapper. Download the Dell drivers to a Windows machine run and install the driver package and extract and copy the INF. file to your USB drive. Install it in a convenient location in Moblin Ubuntu and let Ndiswrapper identify and configure it. Then you should be good to go online.

---

