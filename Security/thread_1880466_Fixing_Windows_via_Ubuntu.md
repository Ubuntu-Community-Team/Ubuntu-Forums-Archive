---
title: "Fixing Windows via Ubuntu"
date: 2011-11-13
forum: Security
---

### Post by mirbi on 2011-11-13
A friend of mine has a serious problem with his Windows Vista based box (almost certainly virus related) and called me in to help. As a long time Ubuntu user I used a boot off CD so I could probe around his machine; I tried using Clam AV to fix offending files but it died after about an hour. 

Does anyone know of any other Linux-based tools that might be of help?

Thanks in advance,

M

---

### Post by sammiev on 2011-11-13
Have you tried [BitDefender]("https://help.ubuntu.com/community/BitDefender") or [Avast]("http://www.avast.com/linux-home-edition") yet? :)

---

### Post by OpSecShellshock on 2011-11-13
Not sure what to suggest without more to go on than serious problem. I'd be most inclined to boot to the live CD, copy whatever files your friend wants to save over to external storage, and then reinstall Windows. That should go much faster than ruling out every potential problem.

---

### Post by emiller12345 on 2011-11-13
take a look at [http://rescuedisk.kaspersky-labs.com/rescuedisk/updatable](http://rescuedisk.kaspersky-labs.com/rescuedisk/updatable)  Kaspersky Rescue 10 Linux Livecd (free download). If the Windows computer isn't too old, it should boot up okay.  It can remove many viruses.

---

### Post by jramshu on 2011-11-14
OP, you will have to be more specific than that. Are you sure it's a virus? What are the symptoms? 

There are several easy methods for cleaning virus'. Just depends on which one you, or your friend have.

---

### Post by Ms. Daisy on 2011-11-14
> **opsecshellshock said:**
> not sure what to suggest without more to go on than serious problem. I'd be most inclined to boot to the live cd, copy whatever files your friend wants to save over to external storage, and then reinstall windows. That should go much faster than ruling out every potential problem.
+1

---

### Post by lisati on 2011-11-14
> **emiller12345 said:**
> take a look at [http://rescuedisk.kaspersky-labs.com/rescuedisk/updatable](http://rescuedisk.kaspersky-labs.com/rescuedisk/updatable)  Kaspersky Rescue 10 Linux Livecd (free download). If the Windows computer isn't too old, it should boot up okay.  It can remove many viruses.

AVG have a linux-based free rescue CD as well: [http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

---

### Post by mirbi on 2011-11-15
Thanks to everyone for responding so quickly - and my apologies for not saying so sooner!

I take what you say about backing up the data and then re-installing Windows - yep, that may well be the best way. Vista is a nightmare.

Basically it's a Dell box with an NVidia Ion and the boot 'disk' is a RAID 0 setup. When the machine boots into Windows, Explorer is empty, I can't run regedit (I get a message saying it's been disabled) and I can't run gpedit.msc (I get a message saying it can't be found).

Some of the rescue CDs can't seem to detect the RAID 0 and won't even start up as a result.

All in all, a complete pain!

---

