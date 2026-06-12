---
title: "Using Mono Professionally?"
date: 2009-06-25
forum: The Cafe
---

### Post by Dragonbite on 2009-06-25
Ok, first off 
[B][INDENT][COLOR="Red"]### DISCLAIMER: this is not meant to be a "I hate Mono" and such, 
so for those of you looking for another anti-Mono rant kindly don't post.###[/COLOR][/INDENT][/B]
I am curious of professional Mono adoption, whether from custom-made applications or deployed on servers or elsewhere.

I don't mean using applications such as Tomboy, F-Stop, Banshee or Beagle.  Monodevelop for purposes of developing a Mono/.NET solution is acceptable though.

Anyone?

---

### Post by gnomeuser on 2009-06-25
Mono is used in several games such as Second Life, and it is at the core of tools like Unity. 

Mono is also key to a number of long tail custom applications allowing customers to move to a Linux solution. The most hilarious example I know of is the adult movie industry, there is an XML standard for storing actress data and existing .NET programs to interact with this data, Mono has allowed the option of moving to Linux to that industry.

---

### Post by Dragonbite on 2009-06-25
> **gnomeuser said:**
> Mono is used in several games such as Second Life, and it is at the core of tools like Unity. 

Mono is also key to a number of long tail custom applications allowing customers to move to a Linux solution. The most hilarious example I know of is the adult movie industry, there is an XML standard for storing actress data and existing .NET programs to interact with this data, Mono has allowed the option of moving to Linux to that industry.

That's one of the few industries that adopts newer technology faster than anybody else.  It's no wonder it's the first industry that made money online!

---

### Post by -grubby on 2009-06-25
Apparently the Sims 3 is written in Mono.

---

### Post by directhex on 2009-06-25
> **grubby- said:**
> Apparently the Sims 3 is written in Mono.

[img]http://www2.apebox.org/wordpress/wp-content/gallery/00-single/simswho.png[/img]

---

### Post by Mateo on 2009-06-25
You have to ask yourself what advantages Mono has over other languages that would CAUSE professional adoption.  I guess the main reason is that it is cross-platform.  So that is great.  But then you have to ask yourself what advantages does it hold over other cross-platform languages.  Over Java.. over Python..

I guess one advantage is that there are many c# programmers out there.  There are many IT developments companies, especially on the east coast, that only do .NET applications.  So if these companies where ever in a position where they needed to sign a contract and a requirement was that it be written for both Windows and Mac, then mono would be a natural choice for this type of company.

---

### Post by billgoldberg on 2009-06-25
> **Mateo said:**
> You have to ask yourself what advantages Mono has over other languages that would CAUSE professional adoption.  I guess the main reason is that it is cross-platform.  So that is great.  But then you have to ask yourself what advantages does it hold over other cross-platform languages.  **Over Java.. over Python..**



It's faster and it seems it's also easier.

I'm no coder but that's what I've read on the subject.

---

### Post by Delever on 2009-06-25
Right now I am adapting my .NET web site framework to run on mono (basically, adding support for another db, otherwise - done). I plan to get platform flexibility - running on mono IS better than on IIS6.

---

### Post by gnomeuser on 2009-06-25
> **Delever said:**
> Right now I am adapting my .NET web site framework to run on mono (basically, adding support for another db, otherwise - done). I plan to get platform flexibility - running on mono IS better than on IIS6.

could you perhaps do a series of blog posts or something to illustrate the level of work involved in something like that.

---

### Post by TheLions on 2009-06-25
> **Mateo said:**
>  But then you have to ask yourself what advantages does it hold over other cross-platform languages.  Over Java.. over Python..

Because it got huge library and great development enviroment.
But python is the easiest language (besides VB) i ever tried.

---

### Post by Mateo on 2009-06-25
> **TheLions said:**
> Because it got huge library and great development enviroment.
But python is the easiest language (besides VB) i ever tried.

I don't know about Mono's libraries... certainly .NET has a huge library.. is Mono compatible with all of those?  Even if so.... it's not as huge as Java's libraries.

Mono has a great development environment?  Really?  Last time I tried it, MonoDevelop's visual debugger wasn't even working.. unless things have changed.

---

### Post by Mr. Picklesworth on 2009-06-25
> **Mateo said:**
> I don't know about Mono's libraries... certainly .NET has a huge library.. is Mono compatible with all of those?  Even if so.... it's not as huge as Java's libraries.

In fairness, the last time I checked Java, it had its own unique set of libraries that you were stuck with and it was impossible to just use anything that the rest of the world uses. GUIs? Swing / SWT. Mono, on the other hand, plugs in to existing APIs like GTK+... and it isn't hard to make bindings where necessary.
Loses in portability (which is where Java really excels), gains in integration and performance.

---

### Post by fevans on 2009-06-26
> **Mateo said:**
> Even if so.... it's not as huge as Java's libraries..

IKVM let's mono use jar files, or compile jar files into .NET dlls. Based on my experience, this works incredibly well. I suspect it has its limits, but has worked for everything I've thrown at it.

> **Mateo said:**
> I don't know about Mono's libraries... certainly .NET has a huge library.. is Mono compatible with all of those?.

DirectX/XNA based stuff won't work. Otherwise, everything I've tried has worked with zero changes needed.

Lest I leave an overly optimistic impression, I'm sure there are some .NET libraries out there that won't work or will require modification. Ditto for jar files. Porting applications will always require some effort.

---

