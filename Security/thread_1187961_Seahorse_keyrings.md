---
title: "Seahorse keyrings"
date: 2009-06-15
forum: Security
---

### Post by limeno on 2009-06-15
Hi,

I want to know where the physical keyrings are located for Seahorse?

The problem is due to failure in hardware I couldnt export keyrings. But I have backup of the
home folder for hd1, hd2 if Im lucky i can read hd2 and gain full acess to files. So if there is any file or anything in the home folder or in the whole system that can help me recover/backup my encrypted
keyrings is the question?

The thing is that I have encrypted files that are very important for, and without the encrypted keyrings I cant decrypt them.

---

### Post by kevdog on 2009-06-15
I dont use seahorse, but being this is a frontend to gnupg, aren't the keyrings located in ~/.gnupg?

---

### Post by the.scarecrow on 2009-06-15
I think what you are looking for is in

/home/*username*/.gnome2/keyrings

Hope that is what you are looking for.

---

### Post by Dr Small on 2009-06-15
> **kevdog said:**
> I dont use seahorse, but being this is a frontend to gnupg, aren't the keyrings located in ~/.gnupg?
I think Seahorse has become much more than just an interface to GnuPG. It's become GNOME's central keyring manager for keys/authenication/ssh/gnupg, which is nice, if you like GNOME.

I actually like Seahorse when I'm on Ubuntu, but otherwise, nah. I can do without it.. :)

---

### Post by xpd259 on 2009-06-22
what you want is

~/.ssh
and 
~/.gnupg 

the stuff in ~/.gnome/ etc etc is just prefernces for seahorse
not the important stuff
:D enjoyo

---

