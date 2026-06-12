---
title: "portable encrypted volume creator"
date: 2012-10-07
forum: Security
---

### Post by dijxtra on 2012-10-07
Hi, I'd like to backup my stuff to an encrypted virtual volume on USB drive and then be able to open it in MS Windows easily (in case I lose access to my home linux machine). What tool do you advise?

Google tells me truecrypt is the thing I need, but unfortunately truecrypt is not in Ubuntu repos (because of licencing issues, if I got that right). Then, google told me that standard way to do what I want in Ubuntu is through dm-crypt/LUKS. But, then there is no way to use that volume on Windows (or at least it's not trivial). So is there a tool which is in Ubuntu repos and for which there is a free tool on MS Windows which allows me to backup my home dir to an encrypted file on my USB disk?

I do not need all that fancy boot sector encrypthion, plausible deniability. All I need is to rsync my home directory to the USB drive and have it encrypted there. So, what's the standard way to do that?

---

### Post by tornadof3 on 2012-10-07
It's true that TrueCrypt isn't in the repositories, but that does not mean it is unavailable.

The 'downloads' section of the TrueCrypt website gives linux downloads, which I have used before and can confirm they work. TrueCrypt is a great tool (although there are other things that do similar stuff...)

---

### Post by dijxtra on 2012-10-07
> **tornadof3 said:**
> It's true that TrueCrypt isn't in the repositories, but that does not mean it is unavailable.
Yeah, but then I won't get updates etc. That's why I'd prefer a tool which is in the repositories. Except if truecrypt is by far the best tool available in which case it would be reasonable to install it by hand.

---

### Post by BrandonIngalls on 2012-10-09
TrueCrypt is the best way to go -- all you have to do is check for updates once every three months. But if you don't want to use it you could give encfs a try.

I have never used encfs4win so I can not say if it will work, but I am sure that if this one does not work there is another out there for windows that will.
[http://members.ferrara.linux.it/freddy77/encfs.html](http://members.ferrara.linux.it/freddy77/encfs.html)

You would have to setup the encrypted window in windows first then open it using your linux distro -- otherwise you may end up with settings that the windows version can not handle.

To mount a folder from your flashdrive/hdd
```
encfs /medial/NAME ~/tmp
```

-=:Edit #1:=-
Here is a link with more information.
[http://www.funzt.info/?p=910](http://www.funzt.info/?p=910)

---

### Post by dijxtra on 2012-10-10
> **BrandonIngalls said:**
> But if you don't want to use it you could give encfs a try.
Thanks for the tip, I'll look into encfs and compare it with truecrypt and then decide.

---

