---
title: "Upgrading from Jaunty to Studio?"
date: 2009-08-06
forum: Ubuntu Studio
---

### Post by natallica on 2009-08-06
Hello all -

I've installed Ubuntu in the past and then upgraded to Studio by grabbing the ubuntustudio packages.

I just installed a fresh copy of Jaunty and wanted to do the same, but the WIKI pages seem to point to these instructions: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

These instructions seem to be much more complicated than what I was doing before.  Is it really not possible to just do this with a vanilla Jaunty install???:

sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

Thanks!

-- N

---

### Post by luvr on 2009-08-06
Your aptitude method should still work equally well.

The page that you refer to, apparently attempts to avoid a number of problems that may occur and take you by surprise if you're not prepared.

Do keep in mind that the Real-Time kernel is somewhat brittle, and may not even be able to boot up your system. That's why the page recommends that you stay on Hardy for serious work.

---

### Post by natallica on 2009-08-06
> **luvr said:**
> Your aptitude method should still work equally well.

The page that you refer to, apparently attempts to avoid a number of problems that may occur and take you by surprise if you're not prepared.

Do keep in mind that the Real-Time kernel is somewhat brittle, and may not even be able to boot up your system. That's why the page recommends that you stay on Hardy for serious work.

Gotcha.  I got the page from here under Jaunty upgrade: [https://help.ubuntu.com/community/UbuntuStudio/Installation](https://help.ubuntu.com/community/UbuntuStudio/Installation)

I'm at a bit of an impasse as it looks like Jaunty has better hardware support for the hardware in my Macbook, but doesn't seem to be as stable with the RT kernel.  What to do...what to do???

-- N

---

### Post by trulan on 2009-08-06
Try it and see.  My AMD64 desktop is perfectly stable on Jaunty, but my dual core Intel Dell laptop freezes at random intervals on the Jaunty RT kernel, so it's Hardy RT for that machine.  But, with stuff actually working as it is supposed to (as opposed to windoze) I am far from complaining.  Oh, the joys and the woes of an open source operating system!

---

### Post by natallica on 2009-08-06
So far so good with the RT kernel on my Macbook.  I'll have to stress it more and see if I can get it to freeze.

Thanks everyone!

-- N

---

