---
title: "What was that app called that let you see hard disk usage?"
date: 2007-02-23
forum: The Cafe
---

### Post by user1397 on 2007-02-23
what's that app called?  i'm using feisty, so i no longer see it.  i think all versions from warty to edgy had this app, located in system > administration, and i believe it was called something like "disks" or something.  

I just happen to like it, and i'd like to know what the package name is so i can download it.

thanks for your time.

---

### Post by Skidpad on 2007-02-23
Maybe Applications>Accessories>Disk Usage Analyzer?

Like this...?

---

### Post by ButteBlues on 2007-02-23
> **ubuntuman001 said:**
> what's that app called?  i'm using feisty, so i no longer see it.  i think all versions from warty to edgy had this app, located in system > administration, and i believe it was called something like "disks" or something.  

I just happen to like it, and i'd like to know what the package name is so i can download it.

thanks for your time.
It was moved to Applications > Accessories.

---

### Post by aysiu on 2007-02-23
You can also check out *filelight* in the Universe repositories. Pretty cool program.

---

### Post by 454redhawk on 2007-02-23
```
sudo apt-get install kdf
```

KDE version

[img]http://www.penguin.cz/~sidlo/RH80/KDiskFree.png[/img]

---

### Post by user1397 on 2007-02-23
okay i found a screenshot of what i was talking about here: [http://debianadmin.com/copper/displayimage.php?album=41&pos=12](http://debianadmin.com/copper/displayimage.php?album=41&pos=12)

just click on it to make it bigger.

see the program in system > administration called 'Discs' ?

that's the one.  (i guess it lasted up to dapper, they removed it in edgy

---

### Post by shareMenaPeace on 2007-02-23
> **aysiu said:**
> You can also check out *filelight* in the Universe repositories. Pretty cool program.

Thnx because i really dont like disk analyzer which is buildin, it takes forever to load and the overview is not logic to me. Sofar i used the system monitor to check filesize or "df". filelight looks really nice!

```
sudo aptitude install filelight
```

---

### Post by Skidpad on 2007-02-23
> **aysiu said:**
> You can also check out *filelight* in the Universe repositories. Pretty cool program.
Downloaded and installed - you are correct - pretty cool program!  Thanks.

---

### Post by Wolki on 2007-02-24
> **ubuntuman001 said:**
> see the program in system > administration called 'Discs' ?

that's the one.  (i guess it lasted up to dapper, they removed it in edgy

It was removed because it was unmaintained.

Personally, I dodn'T like it that uch to begin with. It had a lot of problems.

---

### Post by mips on 2007-02-24
Another cool one is [Baobab]("http://www.marzocca.net/linux/baobab.html")

---

### Post by TheWizzard on 2007-02-24
i like xdiskusage
[http://xdiskusage.sourceforge.net/](http://xdiskusage.sourceforge.net/)

---

### Post by user1397 on 2007-02-24
> **Wolki said:**
> It was removed because it was unmaintained.

Personally, I dodn'T like it that uch to begin with. It had a lot of problems.ah, ok.  all i really liked about it was its succinct hard drive statistics.  but o well, disk usage analyzer is good too.

---

### Post by highneko on 2007-02-24
I prefer the terminal over gui programs. I could go on for days saying how much I love the terminal. n_n
```
sudo du -ch --max-depth=0 /*
```

---

### Post by shareMenaPeace on 2007-02-24
Intresting :)
What does 

```
/*
```

mean?

---

### Post by highneko on 2007-02-24
It's a glob, or globbing, aka a wildcard. 
[http://www.faqs.org/docs/abs/HTML/globbingref.html](http://www.faqs.org/docs/abs/HTML/globbingref.html)
n_n

---

