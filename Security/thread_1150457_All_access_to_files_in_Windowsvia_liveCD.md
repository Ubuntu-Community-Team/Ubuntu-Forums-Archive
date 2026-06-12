---
title: "All access to files in Windows/via liveCD"
date: 2009-05-06
forum: Security
---

### Post by u3000 on 2009-05-06
Dear all,

when using a liveCD or mounting my /home partition (ext3) in Windows using a ext3-driver, i can freely look in all user's files and freely add and delete files.

What's the use of having user accounts and private /home/user folders if one can access these folders by inserting a LiveCd or mounting the partition in another OS?

How do you prevent this?

Kind regards,
u.

---

### Post by Kobalt on 2009-05-06
As far as I know Windows doesn't support UNIX file/folder permissions through the ext3-driver. 
The only way to absolutely prevent this kind of "hard" privacy breach is to use an encrypted /home directory.

---

### Post by u3000 on 2009-05-06
So anyone that finds a laptop can see any document on it, unless a folder is encrypted? 

How would a system admin overcome this problem on a public desktop computer? Disabeling cd/network/usb as boot devices in bios and set a password for changes in there is the only solution i can come up with. Will this do the job?

Using this method for encrypting the /home folder ([https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)), what's the effect on performance?

---

### Post by Kobalt on 2009-05-06
Yes, if you don't want anyone to access your files through physical access to the computer (in the event you lose you laptop for ex.) then encrypting your personal data is the best way (with bios password and so on, as you mentioned) is the best option.
I use an encrypted directory for my eeePC 901, and I see almost no difference in terms of performance. The only "lag" produced is in GDM, I have an extra second to wait before Gnome launches. Other than this, it's working like a charm...

---

### Post by u3000 on 2009-05-06
Thanks for the info, i'll give it a go :)

---

### Post by wirelessmonkey on 2009-05-06
Rule of thumb... Physical access to a device is equivalent to complete access to all information on the device.

---

