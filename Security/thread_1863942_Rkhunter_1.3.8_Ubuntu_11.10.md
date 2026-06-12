---
title: "Rkhunter 1.3.8 Ubuntu 11.10"
date: 2011-10-18
forum: Security
---

### Post by obrer on 2011-10-18
Hello,

Since installation of Ubuntu 11.10 rkhunter reports me these 2 warnings, not being able to whitelist them. 

Anyone has the same problem?

Warning: Hidden ports found:
         Port number: 35822
Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'

The hidden port warning changes everytime rkhunter is executed, no think a security problem since installation was a clean one.

Thanks

---

### Post by Dangertux on 2011-10-18
> **obrer said:**
> Hello,

Since installation of Ubuntu 11.10 rkhunter reports me these 2 warnings, not being able to whitelist them. 

Anyone has the same problem?

Warning: Hidden ports found:
         Port number: 35822
Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'

The hidden port warning changes everytime rkhunter is executed, no think a security problem since installation was a clean one.

Thanks

As far as the port goes are you running bit torrent while running rkhunter? 

The other warning is a typical false positive due to the fact that Ubuntu does not conform to how most other distros place certain files. Therefor rkhunter sees it as anomalous.

Hope this helps.

---

### Post by obrer on 2011-10-18
Nope nothing running like transmission or other, every time I execute rkhunter it reports different port number.

Regarding the Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs' I know it is a false positive but whitelisting ALLOWHIDDENFILE or ALLOWHIDENDIR /dev/.initramfs still gives me the warning.

---

### Post by bhoeneis on 2011-10-18
Same problem here.

Is there a ALLOWHIDDENSYMFILE or alike in rkhunter.conf to get rid of this false positive?

cheers,
 Bernie

---

### Post by obrer on 2011-10-21
Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs' 

It is a bug, already read in Rkhunter mailing list that will be fixed in forthcoming versions. 

About the hidden ports, I think it has to be something regarding the Nvidia graphic card or driver since both the computers I have Nvidia graphic gives me random hidden ports warning another computer without Nvidia does not give me any warning. 

Will make tests and comment.

---

