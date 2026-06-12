---
title: "OpenOffice.org 2.1 packaged with better fonts (maybe)"
date: 2006-12-29
forum: Repositories &amp; Backports
---

### Post by Treviño on 2006-12-29
Hi all, bored by the bad font hinting of edgy's standard OpenOffice.org and curious to test the latest openoffice build, I decided to build (package) it by my own starting from the Debian experimental sources which included the fedora patches for a better font rendering...
After some hours of compiling and hand-made fixes to the sources I finally got some working packages and this is the result (click to enlarge):

[[IMG]http://farm1.static.flickr.com/139/337992843_a16517a216_m.jpg[/IMG]]("http://www.flickr.com/photos/trevi55/337992843/")

I know that the rendering isn't good as the one you can get using the patched freetype libs (as you can see on the background window), however I think that it's much better than the one you get using the standard Ubuntu packages...

Actually I can't post the packages yet because I'm rebuilding some of them to include extra languages (to speed-up the compilation I firstly made oo.o only on en_US), but I hope to post the newer debs (in a new repo) as soon as I can...

Let me know if you want these debs and share your impressions regarding the font thing...

---

### Post by slimdog360 on 2006-12-29
My fonts are okay for typing etc but the menu fonts are huge. Bad thing is Ive tried all the fixes I could find on the net and none worked.

You can see my fonts here.
[http://img174.imageshack.us/img174/2830/snapshot4sw3.jpg]("http://img174.imageshack.us/img174/2830/snapshot4sw3.jpg")

---

### Post by supertux on 2006-12-30
i'd like to see your debs!

---

### Post by filo01 on 2006-12-31
> **Treviño said:**
> 
Let me know if you want these debs and share your impressions regarding the font thing...
Treviño, your fonts looks great, so I would like to ask you for your deb package too.
Thank you very much.

---

### Post by hikaricore on 2006-12-31
> **Treviño said:**
> Hi all, bored by the bad font hinting of edgy's standard OpenOffice.org and curious to test the latest openoffice build, I decided to build (package) it by my own starting from the Debian experimental sources which included the fedora patches for a better font rendering...
After some hours of compiling and hand-made fixes to the sources I finally got some working packages and this is the result (click to enlarge):

[[IMG]http://farm1.static.flickr.com/139/337992843_a16517a216_m.jpg[/IMG]]("http://www.flickr.com/photos/trevi55/337992843/")

I know that the rendering isn't good as the one you can get using the patched freetype libs (as you can see on the background window), however I think that it's much better than the one you get using the standard Ubuntu packages...

Actually I can't post the packages yet because I'm rebuilding some of them to include extra languages (to speed-up the compilation I firstly made oo.o only on en_US), but I hope to post the newer debs (in a new repo) as soon as I can...

Let me know if you want these debs and share your impressions regarding the font thing...

First delivering semidaily builds of beryl svn and now a customized OOo  ^.^  You're quite the packaging machine.  <3   Can't wait to see the end result of this.

---

### Post by Treviño on 2006-12-31
LOL... Packaging machine :D

I'm happy you like these fonts (maybe they're better on CRTs than on LCDs)...
Anyway I've now added other languages to compilation queue, the problem is that actually OO.org needs about 6-7GB of memory and... Now I've the disk quite full, so you should wait more than I think...
I'd like, then, to try also another font subpixel patch. I'll let you know progresses...

Bye!

---

### Post by Hairy_Palms on 2006-12-31
is this any better than the openoffice 2.1 official fonts? 

[http://four.fsphost.com/hairypalms/ooffice.png](http://four.fsphost.com/hairypalms/ooffice.png)

---

### Post by Treviño on 2007-01-03
I've tried to apply also this patch [http://go-ooo.org/patches/src680/ooo59127.vcl.honourcairofont.diff](http://go-ooo.org/patches/src680/ooo59127.vcl.honourcairofont.diff) that should enable the support for the subpixel rendering, but nothing changed here (tested both in a kubuntu and ubuntu laptop)... So the hinting isn't so good as the rest of the system yet, anyway it's better than the standard...

I can't understand why openoffice simply doesn't read the system settings :(

---

### Post by NeoChaosX on 2007-01-12
Hey, mind posting some debs? I'd love to try this out in Kubuntu.

---

### Post by Treviño on 2007-01-12
Hi, my problem is that I've been offline for some days, and I've no bandwidth now... And.. I've also no more space on disk to compile a localized version of debs; so... If you want them I could provide only in en_US now...

---

### Post by NeoChaosX on 2007-01-13
> **Treviño said:**
> Hi, my problem is that I've been offline for some days, and I've no bandwidth now... And.. I've also no more space on disk to compile a localized version of debs; so... If you want them I could provide only in en_US now...
Well, I live in the States, so that's no problem for me. I'd be willing to wait however long it takes for you to get the resources needed, though.

---

### Post by Treviño on 2007-01-14
Mh... Ok I'll try to upload them on next days btw actually it isn't real subpixel rendering... Just hinting :( :(

---

### Post by beefcurry on 2007-01-15
if you need a hosting, i dont mind donating some since i pay for some webhosting. PM if you need :). That is considering you need a http host for your debs. But if you have your own repository thats just better :D. How big are they? you can attach them to your forum messages right?

---

### Post by fd0man on 2007-01-29
> **Treviño said:**
> Hi, my problem is that I've been offline for some days, and I've no bandwidth now... And.. I've also no more space on disk to compile a localized version of debs; so... If you want them I could provide only in en_US now...
I could settle for the en_US debs.  I am looking for packages of OOo 2.1 anyway for Ubuntu.  The ones that came with Linux Mint (an Ubuntu spin-off) were… less than desirable (read: quite unstable).

---

### Post by compuguy1088 on 2007-03-25
I hate to resurrect a post that is around two months old, but I was wondering, has there been any progress with the OpenOffice 2.1 packages?

---

