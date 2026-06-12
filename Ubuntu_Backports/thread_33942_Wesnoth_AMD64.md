---
title: "Wesnoth AMD64"
date: 2005-05-12
forum: Ubuntu Backports
---

### Post by Kemotaha on 2005-05-12
I am getting this error when I try to install Battle of Wesnoth on the Hoary 64.  It is the only thing the 64 backports but I would like to play it:

wesnoth:
  Depends: libc6 (>=2.3.4-1) but 2.3.2.ds1-20ubuntu13 is to be installed
 Depends: wesnoth-data but it is not going to be installed

I am willing to test any of the packages for Hoary 64 too.  At least for the next month or so until I upgrade to Breezy.

Nathan

---

### Post by jdong on 2005-05-13
The AMD64 backport was contributed by a user. I didn't make it.

---

### Post by Kemotaha on 2005-05-13
That's okay.  I figured some one who is on this forum had.  That is why I asked the question.  

Nathan

---

### Post by fromoze on 2005-05-14
Hi, 

```

fromoze@musashi:~ $ dpkg -l | grep libc6
ii  libc6          2.3.5-0ubuntu1 GNU C Library: Shared libraries and Timezone
ii  libc6-dev      2.3.5-0ubuntu1 GNU C Library: Development Libraries and Hea

```

This is the version of libc on my box... but looking on the hoary 'official' version it's 2.3.2... I really don't understand why I've the 2.3.5 because I'm on hoary. I can try to get the 2.3.2 and make them again. I'll send them to jdong. 

Nice! My first bug XD

---

### Post by Kemotaha on 2005-05-14
Thanks

I love the game.  I tell a bunch of people about it.  It is one of the best Open source games out there.

Nathan

---

