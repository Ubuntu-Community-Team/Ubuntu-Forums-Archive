---
title: "I miss Jaunty"
date: 2010-04-16
forum: Testimonials &amp; Experiences
---

### Post by uRock on 2010-04-16
I am installing it in a VBox for me to use a 32bit program that refuses to install on Lucid AMD64. I really have to admit that is was the best looking default setup of any OS I have ever installed. It is almost heart breaking that it only has 6 months of support left. 

Cheers and beers,
Ronnie

---

### Post by JonRohan on 2010-04-16
Have you tried 10.04? I think its the smartest ubuntu yet. Give it a go. :)

---

### Post by Revolutionary101 on 2010-04-16
Just to help you solve your problem with the 32-bit program not installing, try and type this into terminal:

```
sudo dpkg -i --force-architecture nameofpackage.deb
```

---

### Post by uRock on 2010-04-16
> **Revolutionary101 said:**
> Just to help you solve your problem with the 32-bit program not installing, try and type this into terminal:

```
sudo dpkg -i --force-architecture nameofpackage.deb
```

Thanx, I tried, but even that wouldn't work. Earlier today I added a triple boot to go along with the Lucid and W7, but then I realized how much of a pain it is two have to restart just to get back to the faster 64 bit system. 

I could have added Lucid into the vbox with no problems, but I like the solidarity that Jaunty brought.

I will add that I have loved every version of Ubuntu I have used, from Hardy to Lucid and in a month I am sure I will get the Maverick Meerkat tool chain going in a VBox, too.

---

### Post by 3rdalbum on 2010-04-17
Some 32-bit programs won't work on a 64-bit system unless you install some 32-bit libraries too. The "getlibs" program can help with this; unfortunately it's not in the repositories, but a quick Ubuntu Forums search will find it.

---

