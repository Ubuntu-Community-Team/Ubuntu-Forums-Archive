---
title: "Ophcrack &amp; PSCP/WinSCP"
date: 2010-04-06
forum: Security
---

### Post by dominicx1889x on 2010-04-06
If I were to copy files over from a Windows platform computer from my network to my linux box, and I were to use Ophcrack to crack the password, what file(s) should I be looking for to extract from that computer?

---

### Post by dominicx1889x on 2010-04-06
If I were to copy files over from a Windows platform computer from my network to my linux box, and I were to use Ophcrack to crack the password, what file(s) should I be looking for to extract from that computer?

---

### Post by lisati on 2010-04-06
Duplicate threads merged.

Are you doing this on your own machines, or does the Windows machine belong to someone else?

---

### Post by CharlesA on 2010-04-06
Ophcrack will mount the drives automatically and scan for the passwords. I don't think it would work unless you booted from it.

---

### Post by OpSecShellshock on 2010-04-07
Seems like a lot of work for something that's already on your network. If you own the Windows computer then you already know the password. There's no need to copy the drive. But the other thing is, what do you mean by password? If it's just the user log on password then you won't need it at all if you aren't logging on. Just copy the files.

If you don't own the Windows computer then leave it alone (pretty easy solution). If it's an investigation (i.e. law enforcement or internal company audit of a system by security staff) then simply copying the files to another device is not forensically sound, and any data you obtain will be useless.

---

### Post by cariboo on 2010-04-07
There are several offline password reset programs available for Windows, that take a lot less time, I can usually reset the password in less than 5 minutes.

---

