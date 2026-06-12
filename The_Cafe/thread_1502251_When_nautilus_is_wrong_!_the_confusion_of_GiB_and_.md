---
title: "When nautilus is wrong ! the confusion of GiB and GB !"
date: 2010-06-05
forum: The Cafe
---

### Post by medya on 2010-06-05
Today I tried to burn a folder on my computer , which Nautilus said it is 4.5 GB and strangely it wouldn't fit on a 4.7 GB blank DVD-R !

Using another file manger , I found out my actual folder size is 4.5 GiB which is equal to 4.83 GB , and I was convinced that it wouldn't fit on a 4.7 GB blank DVD .

it seems that Nautilus the File manager of Ubuntu doesn't care about difference of GB and GiB .

so whats the difference of GB , and GiB ?

Giga in math means 1 billion . we all know digital world is binary , and computers work by binary numbers, while the humans use decimal numbers.
GB =Decimal Giga Byte = one billion bytes
GiB=Binary Giga Byte = 2^20 billion bytes

The capacity of storage devices [for i.e blank dvd , or hard disk] are measured in Decimal GB .
probably because it is meant to be read by a humans .
for instance , you buy a 300 GB hard disk which literally means 300 hundred billion bytes . [but for the binary world of computers it is actually 2^20*300= 279 GiB]
therefore a 4.7 GB DVD-ROM is actualy 4.3772 GiB for a computer .

IEC Standard :
"MiB [Meby Byte] GiB (Geby Byte) is a standard that was defined by the International Electrotechnical Commission (IEC) in December 1998 to solve the confusion of Decimal and Binary Giga Byte." (src : wikipedia)


Nautilus is not following the IEC Standard but KDE applications are already using IEC standard . Hi5 to KDE fans ;)

I submitted a Bug in Launchpad .

+ P.S :Here is online convertor to calculate GiB and GB .


this post is from my blog [Shevin , Life and Ubuntu]("http://blog.shevin.info/2010/06/when-nautilus-is-wrong-confusion-of-gib.html")
to see the links and color notes , read it on my blog .

---

### Post by Old Marcus on 2010-06-05
*yawn*

---

### Post by kaldor on 2010-06-05
> *yawn*

Ah, elitism :)

That's the way that UNIX has done it for years. Whatever works for you though. And yes, KDE is great! :)

---

### Post by Old Marcus on 2010-06-05
Elitism? Moi? :P

But seriously, most of the time it makes little difference.

---

### Post by medya on 2010-06-05
> **Old Marcus said:**
> Elitism? Moi? :P

But seriously, most of the time it makes little difference.

2 GB diffrence is not little ! 

we need ubuntu to be accurate !

---

### Post by Shining Arcanine on 2010-06-05
> **medya said:**
> Today I tried to burn a folder on my computer , which Nautilus said it is 4.5 GB and strangely it wouldn't fit on a 4.7 GB blank DVD-R !

Using another file manger , I found out my actual folder size is 4.5 GiB which is equal to 4.83 GB , and I was convinced that it wouldn't fit on a 4.7 GB blank DVD .

it seems that Nautilus the File manager of Ubuntu doesn't care about difference of GB and GiB .

so whats the difference of GB , and GiB ?

Giga in math means 1 billion . we all know digital world is binary , and computers work by binary numbers, while the humans use decimal numbers.
GB =Decimal Giga Byte = one billion bytes
GiB=Binary Giga Byte = 2^20 billion bytes

The capacity of storage devices [for i.e blank dvd , or hard disk] are measured in Decimal GB .
probably because it is meant to be read by a humans .
for instance , you buy a 300 GB hard disk which literally means 300 hundred billion bytes . [but for the binary world of computers it is actually 2^20*300= 279 GiB]
therefore a 4.7 GB DVD-ROM is actualy 4.3772 GiB for a computer .

IEC Standard :
"MiB [Meby Byte] GiB (Geby Byte) is a standard that was defined by the International Electrotechnical Commission (IEC) in December 1998 to solve the confusion of Decimal and Binary Giga Byte." (src : wikipedia)


Nautilus is not following the IEC Standard but KDE applications are already using IEC standard . Hi5 to KDE fans ;)

I submitted a Bug in Launchpad .

+ P.S :Here is online convertor to calculate GiB and GB .


this post is from my blog [Shevin , Life and Ubuntu]("http://blog.shevin.info/2010/06/when-nautilus-is-wrong-confusion-of-gib.html")
to see the links and color notes , read it on my blog .
1GB = 2^30 bytes.

It has been this way for the longest time and it is the most natural way of representing things in computers. The fact that there is an almost perfect correspondance between powers of 2 and powers of 10 as a consequence of the change of base fomula has led those that want to advertise that they sell more for less (ISPs and hard drive manufacturers) to substitute the base 10 approximation, but that is not strictly correct.

What is sad is that they managed to get the SI system to recognize the base 10 approximation as the valid system to allow themselves to dodge lawsuits over unethical business practices involving weights and measures. That is where all of this XiB nonsense originated.

---

### Post by Mr. Picklesworth on 2010-06-05
There was work towards clarifying this across the desktop, and defaulting to real GBs in Lucid. Unfortunately, people complained (occasionally for good reason), so it was held off for a more complete set of fixes. I believe that may be finding its way into Maverick...

[https://wiki.ubuntu.com/UnitsPolicy](https://wiki.ubuntu.com/UnitsPolicy)

---

### Post by Shining Arcanine on 2010-06-05
That is a stupid policy. It should be reversed based on historical precedent, such that XiB is used for base 10 while XB is used for base 2.

---

### Post by medya on 2010-06-05
it is not the Qustion which Unit ubuntu should use, 
the problem is ,  ubuntu's nautilus says it is using GB [XB] but infact it is showing us the file sizes in  GiB [XiB] 

so they can change the unit to GiB and say it is GiB .
or they can change the unit to GB and say it is GB . 
not use GiB and say it is GB !!!

it is a big mistake .

---

### Post by Shining Arcanine on 2010-06-05
> **medya said:**
> it is not the Qustion which Base ubuntu should is, for now ubuntu's nautilus says it is using GB [XB] but infact it is showing us the GiB [XiB] 
so either they can show us GiB and say it is GiB 
or they show us Reall GB . 

so it is not qustion of which standard ubuntu has chosen, ubuntu's nautilus  , has chosen GB but it shows GiB . [a big mistake]
Please specify what units they are using and what base they are using. Otherwise, your post is unclear.

---

### Post by medya on 2010-06-05
> **Shining Arcanine said:**
> That is a stupid policy. It should be reversed based on historical precedent, such that XiB is used for base 10 while XB is used for base 2.

actualy GiB is used for Binary Giga [2^20]
and GB is used for Decimal Giga  .

---

