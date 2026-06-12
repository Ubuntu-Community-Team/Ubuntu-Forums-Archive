---
title: "vista file access from Ubuntu cd"
date: 2009-02-14
forum: Security
---

### Post by amulet on 2009-02-14
I am not entirely sure this is  the correct place to add this query, but I have discovered to my horror, that if I run Ubuntu from the live cd I can gain direct access to my Windows installation on the same computer, and can therefore view all files, without entering my user password.  This is pretty handy for me, but when I think of the number of Windows installations that are seemingly secure against anyone viewing private files I realise this makes a mockery of Vista!  Of course it's always handy to retrieve files from a corrupted Windows, but it also means anyone with an Ubuntu cd can view what I consider to be private work.
I believe this is also true of Ubuntu files on an installed Ubuntu OS, i.e. they can be viewed from a live Ubuntu cd? How do I prevent this?

---

### Post by cosine352 on 2009-02-14
set a BIOS password. It will prevent someone to boot.

---

### Post by hyper_ch on 2009-02-14
bios password won't help... fully encrypt the vista installation with truecrypt

---

### Post by cariboo on 2009-02-14
If someone has physical access to your computer, there isn't much you can do except to do what hyper_ch suggests.

Jim

---

### Post by amulet on 2009-02-15
Thanks to all the above.  Obviously I would like to think that nobody has access to my computer, but my laptop was stolen last year, and I felt comfortable at the time that at least my files could not be viewed !  However I now realise how ignorant I was.  I only discovered this gaping hole in Windows when I accessed my own Windows files this way on my new dual boot.

So, we are saying that if my pc or laptop is stolen, anyone with an Ubuntu live cd can access my Windows files, if the Firewall is off?
And the only way to avoid anyone with an Ubuntu cd from viewing my Ubuntu files is to set a bios password, or configure bios to never boot from cd?  
Surely there has to be a better way!

Oh the horror! I loved Ubuntu, and now I am wandering......

---

### Post by Dave_Connor on 2009-02-15
There is ways to bypass the BIOS password by removing the CMOS where the setting are stored and then the BIOS is reset to default settings. DM_Crypt for Ubuntu and Truecrypt for Vista or for both.

---

