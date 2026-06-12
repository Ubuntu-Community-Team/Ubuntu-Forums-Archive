---
title: "Automatically Threading Code"
date: 2009-02-24
forum: Ubuntu Brainstorm
---

### Post by tomrules345 on 2009-02-24
A lot of you may have heard of this new feature that is arriving with the new Macintosh OSX "Snow Leopard". Its known as "Grand Central".

Here's some links if you need to brush up:
[http://en.wikipedia.org/wiki/Grand_Central_(technology](http://en.wikipedia.org/wiki/Grand_Central_(technology))
[http://www.apple.com/pr/library/2008/06/09snowleopard.html](http://www.apple.com/pr/library/2008/06/09snowleopard.html)

It is this feature that should be one of the main focus' of the next Ubuntu generation (I'm talking about 2010 here). This feature (among others) will surely give windows users a reason to give their OS "Das Boot", (yeah I know it means "The Boat" but for non-german speaking people it has a greater effect).

Also if anyone else supports the idea 16 bit colour printing would also be a kick in the pants to Microsoft (Windows 7 cant/wont actually do it!).

I know it seems like a huge ask but it does seem appropriate that we now allow a technology like this become fully fertile and grow into the open-source community.

Any thoughts?

---

### Post by smartboyathome on 2009-02-24
I thought most applications do support threading if you recompiled it with the right flags. The problem with this as default is that it might mess up the packages for single core computers.

By the way, GCC has supported multiple cores for a while. I know that it has supported that for a while.

---

### Post by tomrules345 on 2009-02-24
Yes I will agree that GCC currently supports threading.

I just meant that it would be better if there was some sort of sub-system that allowed an executed application to be run in a multi-core/processor environment without the need for the programmer to actually write the threads into the code.

---

### Post by smartboyathome on 2009-02-24
Ah, ok. Would this be possible without making problems for single core machines? Since Apple has been using dual core or higher for a little while now, they don't have to worry about single cores really, but we still do.

---

### Post by tomrules345 on 2009-02-24
Simple.

1) Most new desktops actually have two or more cores by default, but failing this;

2) Upon install there could be an option that is made available/chosen automatically.

Since the package would thread the programs automatically there would be no need to actually modify any of the existing packages, hence the nature of the term "automatic".

---

### Post by smartboyathome on 2009-02-24
1 would involve abandoning computers which are a few years old (I have a desktop I bought last year which is single core), not something I think Ubuntu should do.

2 how would you make it so that the packages were made single or multiple core automatically without having extra packages having to be maintained in the repos? Right now, it requires recompiling the program to switch from single to dual core, as otherwise the binaries would break on single core systems.

---

### Post by Npl on 2009-02-25
> **tomrules345 said:**
> Simple.

1) Most new desktops actually have two or more cores by default, but failing this;

2) Upon install there could be an option that is made available/chosen automatically.

Since the package would thread the programs automatically there would be no need to actually modify any of the existing packages, hence the nature of the term "automatic".
Loadsa bull.. Do you have actually any reference on "Grand Central"?

From the few words describing it will will be a set of libraries that will **help** programmers divide their Apps in "Chunks" and then manage executing those "Chunks" on multiple cores. None of this will happen automatically.

---

### Post by tomrules345 on 2009-02-25
Fine then.

If you all hate it so much I will not continue to post anymore.

Geez you guys can be <Bip Bip> sometimes!

This was supposed to be an idea. Something LIKE grand central. Hence I put it in the "Ubuntu Ideas Pool" and obviously no body likes the idea, which is fine but you don't have to be so rude!

---

### Post by uljanow on 2009-02-25
"Grand Central" is just another stupid marketing word created by Apple. That is not a new technology. Have a look at [OpenMP]("http://en.wikipedia.org/wiki/OpenMP") which is around since 1997.

---

