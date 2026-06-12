---
title: "wine 1.1.15, can it be compiled in hardy?"
date: 2009-02-18
forum: Wine
---

### Post by Meow27 on 2009-02-18
at the end of doing ./configure, im told that i need a newer version of gnutils

```
configure: libgnutls development files not found, no schannel support
```
what do i do? i need a newer version of libc6 for it >.>

i cant find any ubuntu 1.1.15 package

i didnt have this problem compiling 1.1.14 >.> (or 1.1.12, regardless i cant compile it now)

i was able to compile it in intrepid though >.>

---

### Post by whoop on 2009-02-18
Waiting for a deb myself. check: [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)
I expect it will be released soon. It did compile on jaunty for me.

---

### Post by cogadh on 2009-02-18
The 1.1.15 Ubuntu package should be available on the WineHQ repository shortly. Its already up on the Launchpad build system, so it won't be long before it is place in the repository:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

As for compiling it yourself, you should be able to as long as you have already installed all the dependencies (apt-get build-dep wine) and the necessary build tools (sudo apt-get install build-essential).

---

### Post by Meow27 on 2009-02-18
> **whoop said:**
> Waiting for a deb myself. check: [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)
I expect it will be released soon. It did compile on jaunty for me.

i know and i would expect it to work on jaunty

READ THIS AGAIN PLZ

my problem is is that the dependency (above) is too old. i cant compile the newer versions of wine consequently [on hardy]. 
i always to sudo apt-get build-dep wine but it only works once because the dependencies dont get updated when they need a higher version of libc6.

if you guys still dont understand me, please dont be afraid to ask -.-

edit---- 
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
isnt this site any better?

---

### Post by cogadh on 2009-02-18
That site is the WineHQ Ubuntu repository, its just the archive access to it.

In regards to your ongoing compile error, I don't read that message as telling you that you need a newer version of libc6, I read it as you are missing the dev files completely, i.e. you haven't actually obtained all of the dependency files needed to build Wine. If you needed a newer version, the error message would directly say something like "libc6 version x.x.x found, version y.y.y needed", not "development files not found".

---

### Post by Emanuele_Z on 2009-02-18
1.1.15 isn't available yet as .deb for ubuntu, am I right?

Cheers,

---

### Post by whoop on 2009-02-18
> **Emanuele_Z said:**
> 1.1.15 isn't available yet as .deb for ubuntu, am I right?

Cheers,
You are right.

---

### Post by YokoZar on 2009-02-18
I'm building it now (the Intrepid packages are already up), I've finally fixed the problems the build daemon was facing by cherry-picking a patch from 1.1.16.

---

### Post by Meow27 on 2009-02-18
> **cogadh said:**
> That site is the WineHQ Ubuntu repository, its just the archive access to it.

In regards to your ongoing compile error, I don't read that message as telling you that you need a newer version of libc6, I read it as you are missing the dev files completely, i.e. you haven't actually obtained all of the dependency files needed to build Wine. If you needed a newer version, the error message would directly say something like "libc6 version x.x.x found, version y.y.y needed", not "development files not found".

the newer version can be installed because they depend on newer versions of glib and other gtk like things which require higher version of libc6. and yes its not libc6, if it was it would bluntly say that like in gimp. im not that insensitive of this knowlegde.

....anyway. if you need to to show you a screenshot that i have it installed ill be more than glad to. ill just let you know that configure and make dont give messages that say 'your version is too old' most of the time its either you have it as needed, or not at all.

AGAIN i did not have problems with this in the past, 1 dependency is just outdated in my case

(if it helps, my configure script completed, just said that that function would be disabled because if couldn't find the right version)


@yoko thanks for uploading them, can you teach me how to get the shortcuts to work 'winecfg', 'drive c' and 'uninstall' ready? it doesnt appear in my menu when i make install right off the bat after make (in a normal situation)

---

### Post by Meow27 on 2009-03-02
ok since 1.1.16 is not up as a single package (broken link)

i request either: it be fixed

OR someone explain to me whats wrong here?

heres a screenshot. 

[IMG]http://i119.photobucket.com/albums/o144/flamehawk/Screenshot-10.png[/IMG]

---

### Post by cogadh on 2009-03-02
The 1.1.16 package is up at the WineHQ repsoitories:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

And in the archive:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Meow27 on 2009-03-02
no its not in the archive. try it

and i dont want to do with thru the updater..

just dont wanna

---

### Post by cogadh on 2009-03-02
I just tried it through the archive, downloaded fine, all three variations.

---

### Post by Meow27 on 2009-03-02
for hardy?

---

### Post by cogadh on 2009-03-02
Whoops! No, I was looking at the Intrepid links. 

BTW - Why don't you want to use the repository?

---

### Post by Meow27 on 2009-03-02
because then it would be too easy...


no its just cause it never works for me the 1st time, i sometimes need to reboot and then it bugs me and so on... .i just don't like it. (though i wouldn't care if i could download it as a deb file separately from that place)

---

### Post by cogadh on 2009-03-02
You know, you don't have to use the auto-update at all. You can use the repository with Synaptic, Add/Remove and simple apt-get. However, if you use the auto update, the Wine package never requires a reboot and it has always worked for me on the first try. Frankly, using the repository to install packages is way more reliable than any other method, especially compiling it yourself.

---

### Post by Meow27 on 2009-03-02
true, however when i try applying a patch, at the moment im forced to use either jaunty or intrepid, i want to know how yokozar was able to compile it for hardy >.>

---

### Post by Meow27 on 2009-03-03
bump

---

### Post by YokoZar on 2009-03-04
> **Meow27 said:**
> no its not in the archive. try it

and i dont want to do with thru the updater..

just dont wanna

1.1.15 for Hardy was uploaded when you called it a "broken" link, but by then 1.1.16 was out (which was what you were clicking on).

For some reason 1.1.16 built on all arches *except* hardy-i386 just fine.  It turned out to be a problem with the launchpad build daemon, which eventually worked - it just took about 5 days to build the hardy-i386 package for 1.1.16.  It's up now, and the link is no longer broken.

Sorry about the delays.

---

### Post by Meow27 on 2009-03-04
thanks, by the way, now that i have a screenshot in there, do you have any suspicions as to what went wrong with my compilation?

---

