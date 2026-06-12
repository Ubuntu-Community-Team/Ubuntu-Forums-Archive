---
title: "Amazon MP3 store arrangements for Precise?"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-04-02
Hello All

Installed fresh Xubuntu and Banshee.

The Amazon store plug in generates certificate errors when buying music from Amazon UK. Bug or policy change?

Rhythmbox appears not to have an Amazon plug in

What is the story for Precise for those who want to buy music from Amazon?

---

### Post by Fredo on 2012-04-12
I can confirm this for Amazon DE. I filed a bug about this: [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/980300](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/980300) Feel free to confirm it over there.

---

### Post by coffeecat on 2012-04-12
Related threads for those interested:

[http://ubuntuforums.org/showthread.php?t=1921208](http://ubuntuforums.org/showthread.php?t=1921208)

[http://ubuntuforums.org/showthread.php?t=1955149](http://ubuntuforums.org/showthread.php?t=1955149)

> **keithpeter said:**
> 
What is the story for Precise for those who want to buy music from Amazon?

I'll extend that. What about those who like to buy from both Amazon and Ubuntu Music Store? The arrangements in Oneiric were fine - you could do both from Banshee - and I'm disappointed that it looks as though it's going to be far less convenient in 12.04. I really do not wish to be running two music apps for this.

> **Fredo said:**
> I can confirm this for Amazon DE. I filed a bug about this: [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/980300](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/980300) Feel free to confirm it over there.

Thanks for that. Once I've confirmed I'm getting the same, I'll do a me-too.

---

### Post by Fredo on 2012-04-13
> **coffeecat said:**
> I'll extend that. What about those who like to buy from both Amazon and Ubuntu Music Store? The arrangements in Oneiric were fine - you could do both from Banshee - and I'm disappointed that it looks as though it's going to be far less convenient in 12.04. I really do not wish to be running two music apps for this.

The lack of an Ubuntu One store for Banshee seems to stem from the fact that Banshee is still using GTK2, and the Ubuntu devs don’t want to maintain both a GTK2 and GTK3 version of the store. But I think chances are high that Ubuntu One will return to Banshee once it is ported to GTK3.

Still, from a user’s perspective, it’s a bit annoying.

---

### Post by coffeecat on 2012-04-20
Rather belatedly I've done a me-too on the bug.

---

