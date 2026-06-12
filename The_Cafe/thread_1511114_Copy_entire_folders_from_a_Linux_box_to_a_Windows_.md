---
title: "Copy entire folders from a Linux box to a Windows box"
date: 2010-06-16
forum: The Cafe
---

### Post by Yes on 2010-06-16
I'd like to copy my entire Music folder on my Linux computer over to my new Windows laptop... does anyone know of a simple way to do this, besides a flash drive?

Thank you :)

---

### Post by sydbat on 2010-06-16
Network? Portable HDD?

---

### Post by alphaniner on 2010-06-16
Mount or smbclient into a windows share from the Linux machine, and copy.  You may need to make a registry edit*, I had to do so on my W7 box.  But you would be better served posting in another forum...

*Windows kept dropping the connection.  The registry setting was something to do with having Windows act as a file server, but I don't remember exactly what it was.

---

### Post by squilookle on 2010-06-16
How big is the Music folder in question? 

Generally, if it were me moving the file, I would use Drop Box if it were under 2gb, a DVD if it were under 4gb, my 8gb usb stick, it if were under 8gb. 

If it were bigger, I'd be looking at network, or portable hard drive, but others have beat me to suggesting those.

---

### Post by alphaniner on 2010-06-16
> **squilookle said:**
> How big is the Music folder in question? 

Generally, if it were me moving the file, I would use Drop Box if it were under 2gb, a DVD if it were under 4gb, my 8gb usb stick, it if were under 8gb...

Why not just use the usb stick in all of those cases?

---

### Post by whiskeylover on 2010-06-16
sftp

---

### Post by sydbat on 2010-06-16
> **alphaniner said:**
> Why not just use the usb stick in all of those cases?Oh you...always pointing out the obvious...:p

---

### Post by squilookle on 2010-06-16
> **alphaniner said:**
> Why not just use the usb stick in all of those cases?

Good question. 

And it's because I don't know where I put it and can't be bothered to look for it.

---

### Post by RiceMonster on 2010-06-16
> **alphaniner said:**
> Why not just use the usb stick in all of those cases?

If your music collection is more than 2 times the size of your flash drive, that would get pretty tedious, don't you think?

---

### Post by alphaniner on 2010-06-16
> **squilookle said:**
> Good question. 

And it's because I don't know where I put it and can't be bothered to look for it.

I approve of (and relate to) this response.

---

### Post by cariboo on 2010-06-16
You shouldn't have to do anything to your Linux system, just make sure you have file sharing setup on the laptop and transfer the files via your network assuming you have a wireless router.

---

### Post by alphaniner on 2010-06-16
> **RiceMonster said:**
> If your music collection is more than 2 times the size of your flash drive, that would get pretty tedious, don't you think?

Apparently you didn't read the bit I was responding to.  Do you need some golden rice to improve your eyesight? :P

---

### Post by RiceMonster on 2010-06-16
> **alphaniner said:**
> Apparently you didn't read the bit I was responding to.  Do you need some golden rice to improve your eyesight? :P

Didn't notice you snipped it, no.

---

### Post by Yes on 2010-06-16
Actually, I think I got it with Filezilla.  I started the SSH server on my Linux computer and connected with Filezilla on the laptop, and then just dragged the Music folder from one computer to the other and it seems to be working nicely.

Thanks everyone!

---

### Post by CharlesA on 2010-06-16
sftp rocks. :D

---

### Post by Tristam Green on 2010-06-16
> **squilookle said:**
> Good question. 

And it's because I don't know where I put it and can't be bothered to look for it.

Buy a new one.

---

