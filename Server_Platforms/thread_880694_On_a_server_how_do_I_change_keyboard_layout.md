---
title: "On a server: how do I change keyboard layout?"
date: 2008-08-05
forum: Server Platforms
---

### Post by zazuzimbo on 2008-08-05
Hello,

I couldn´t find how should I change keyboard layout/language on a server (i.e., wihout a graphical interface installed). May you help me?

Thanks.

Zazu

---

### Post by pluviosity on 2008-08-05
What formats do you want to switch from/to?  You can try using the setxkbmap command.

---

### Post by pluviosity on 2008-08-05
Oops, I mentioned the way to do it for X, which you probably aren't using on a server.

Try this:

```
sudo dpkg-reconfigure console-setup
```

---

### Post by zazuzimbo on 2008-08-05
Thank you, pluviosity! It is what I wanted. :) And even more.

My immediate problem was that the machine expected a brazilian ABNT2 keyboard and I am using a US-international keyboard.

It was impossible to type "|" and "\" (among others), and you may imagine that this caused problems. Now all the keys are being interpreted correctly. My problem is solved. :)


However (a small side issue) I couldn´t get all "special" letters to work "áéíóúçü". Choosing USA; USA_intl; utf-8 was the best case I found, where only the cedillas (çÇ) didn´t work. **Choosing iso-8859-1 breaks the programs (they are in utf-8, I guess).**

I say this just because I think this info should be added, somehow, to the official Ubuntu documentation. And someone might really need the special characters.

Kindly,

Zazu

---

### Post by z-itou16 on 2009-04-05
thank you so much pluviosity!!!

that helped me.


Thank you!

---

### Post by prasmick on 2010-01-11
> **pluviosity said:**
> Oops, I mentioned the way to do it for X, which you probably aren't using on a server.

Try this:

```
sudo dpkg-reconfigure console-setup
```

This worked for me. Thanks a lot.:D

---

### Post by barnex on 2010-01-11
Great! When I was sporadically using the console, it drove me crazy not being able to type a |. Thanks.

---

### Post by peetaur on 2011-11-25
This (outdated) did not work for me on Ubuntu 11.10 oneiric. It only allowed me to change the font size, encoding, etc. 

But it lead me to the right command.

Instead I used:

sudo dpkg-reconfigure keyboard-configuration

---

### Post by Kurtosis on 2012-02-06
> **peetaur said:**
> This (outdated) did not work for me on Ubuntu 11.10 oneiric. It only allowed me to change the font size, encoding, etc. 

But it lead me to the right command.

Instead I used:

sudo dpkg-reconfigure keyboard-configuration

Thanks for the update peetuar, same problem, same search led me here too, old way no longer works.  Much appreciated.

---

