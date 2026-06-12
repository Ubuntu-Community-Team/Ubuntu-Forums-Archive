---
title: "How do I install latest Wine on 13.10"
date: 2013-10-09
forum: Ubuntu Development Version
---

### Post by Melhisedek on 2013-10-09
As official repo doesn't seem to support latest Ubuntu.
Thank you for your time!

---

### Post by philinux on 2013-10-09
> **Melhisedek said:**
> As official repo doesn't seem to support latest Ubuntu.
Thank you for your time!

```
apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1.4.1-0ubuntu7
  Version table:
     1.4.1-0ubuntu7 0
        500 http://gb.archive.ubuntu.com/ubuntu/ saucy/universe 
```

I would say just install it. Unless you're looking for a ppa?
!.5 is beta too. Beta and wine - not a good combo if you ask me.
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by grahammechanical on 2013-10-09
As a test I just installed wine 1.4.1 from the 13.10 Software Centre without problems. Provided you do not get caught out as I did by the dialog for accepting the terms and conditions of using MS core fonts being placed behind the Software Centre application window. I get caught by that every time.

If you are referring to a PPA that has not yet been packaged for saucy, then I suggest put in the PPA in software sources and make sure it is pointing to a raring repository and not a saucy repository.

Regards.

---

### Post by Melhisedek on 2013-10-09
I thought more of installing the latest beta 1.7.3 I believe. But I'll try and point it to raring repo and see what happens :)

---

### Post by JMB74 on 2013-10-10
Can't vouch for how well it works, but someone has packaged the latest wine 1.7.3 here: [https://launchpad.net/~joe-yasi/+archive/yasi?field.series_filter=saucy](https://launchpad.net/~joe-yasi/+archive/yasi?field.series_filter=saucy)

---

