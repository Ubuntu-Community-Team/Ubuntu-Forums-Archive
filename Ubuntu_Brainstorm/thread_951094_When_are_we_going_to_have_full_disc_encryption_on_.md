---
title: "When are we going to have full disc encryption on the livecd?"
date: 2008-10-17
forum: Ubuntu Brainstorm
---

### Post by Dr Small on 2008-10-17
As it stands, one must also download the alternate CD if you want to install Ubuntu fully encrypted. Is Ubuntu ever planning to enable full-disc encryption from the LiveCD? I know I would use it, and some other folks would love to see it.

I think it would make a full disc encryption more widespread and used by more people.

---

### Post by Polygon on 2008-10-18
report a wishlist bug on launchpad and hope someone takes heed of it =)

---

### Post by master5o1 on 2008-10-18
TrueCrypt is FOSS right?

---

### Post by Polygon on 2008-10-18
yep, but it does not support full disk encryption like it does with windows yet, most likely becuase it has to create a bootloader or do something with grub to make it work

---

### Post by Dr Small on 2008-10-18
> **master5o1 said:**
> TrueCrypt is FOSS right?
Why do we have to use TrueCrypt? I don't see why it couldn't use the same method that is on the alternate CD, only as an option in the LiveCD installer.

---

### Post by cardinals_fan on 2008-10-18
Fedora offers this, right?

---

### Post by FuturePilot on 2008-10-18
> **Dr Small said:**
> Why do we have to use TrueCrypt? I don't see why it couldn't use the same method that is on the alternate CD, only as an option in the LiveCD installer.

Probably because the live CD installer doesn't support creating an LVM setup like the alternate installer does which is needed for the full disk encryption. I know this has been requested before. I wouldn't be surprised if there is a wishlist item on Launchpad for this already.

---

### Post by t0p on 2008-10-18
> **Dr Small said:**
> Why do we have to use TrueCrypt? I don't see why it couldn't use the same method that is on the alternate CD, only as an option in the LiveCD installer.

I'm with you, Dr Small!  Heck, truecrypt ain't even in the repos!  And it doesn't offer full disk encryption.

*What do we want?* Full disk encryption on the live cd installer! *When do we want it?*  In ubuntu 9.04... or 9.10...

What a snappy slogan!  Tshirt, anyone?

:p

---

### Post by Dr Small on 2008-10-19
> **t0p said:**
> I'm with you, Dr Small!
Thanks t0p :)

> **t0p said:**
> 
*What do we want?* Full disk encryption on the live cd installer! *When do we want it?*  In ubuntu 9.04... or 9.10...
Amen. It would be more popular to see fully encrypted discs then and the average Joe could have some security without getting too technical. I would surely use it.

---

### Post by Dr Small on 2008-10-19
I went ahead and posted the idea on Brainstorm (my first idea there ;))
[http://brainstorm.ubuntu.com/idea/14574/](http://brainstorm.ubuntu.com/idea/14574/)

---

### Post by Canis familiaris on 2008-10-19
I am NOT fully aware of the technical implications of this but I +1ed the idea because as a user point of view it would be great particularly for laptops and netbooks.

---

### Post by gnomeuser on 2008-10-19
> **master5o1 said:**
> TrueCrypt is FOSS right?

Actually no.

[http://fedoraproject.org/wiki/ForbiddenItems#TrueCrypt](http://fedoraproject.org/wiki/ForbiddenItems#TrueCrypt)
[https://bugs.edge.launchpad.net/ubuntu/+bug/109701](https://bugs.edge.launchpad.net/ubuntu/+bug/109701)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=364034](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=364034)

And here are some suggested changes to their current license which would make it properly compatible Free Software.

[http://lists.freedesktop.org/archives/distributions/2008-October/000276.html](http://lists.freedesktop.org/archives/distributions/2008-October/000276.html)

That being said, having a nice little tickbox to enable full disk encryption would be neat, especially for travellers who carry around laptops and fear losing personal information. Those wanting to merely keep certain files private can probably use the Private folder in Intrepid instead and not suffer the same overhead on all IO operations.

---

### Post by cdenley on 2008-10-20
The only problem I can see with this is a bunch of new users will select to use encryption even though they have no need for it, then they will blame ubuntu for their computer's poor performance. I think the user should be warned of the cons to full disk encryption, if it is selected.

---

### Post by Dragonbite on 2008-10-20
> **cardinals_fan said:**
> Fedora offers this, right?

Yes, Fedora offers it when you install it on your hard disk.

I had a system with Fedora 9 installed encrypted and then the OS when *kaput!*.  Luckily it is easy to recover the data using the LiveCD and knowing the passphrase.

---

