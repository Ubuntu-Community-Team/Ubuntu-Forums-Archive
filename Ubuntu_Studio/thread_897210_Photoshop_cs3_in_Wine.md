---
title: "Photoshop cs3 in Wine"
date: 2008-08-21
forum: Ubuntu Studio
---

### Post by aladinonl on 2008-08-21
Hi,
I'm going to take a design course and have to use Photoshop cs3.

I look around and it seems that currently Wine doesn't support Photoshop cs3 yet. But the posts are dated back few months ago while Wine is quite fastly developed. 

So is there anyway to use photoshop cs3 in ubuntu? do u recommend running virtual machine in a 1.83 GHz, 512 DDRAM laptop?

---

### Post by ShinobiTeno on 2008-08-22
You can try crossover wine. But its not free...

---

### Post by rylleman on 2008-08-22
Not sure about CS3 but CS2 works quite well in wine.
Should work in virtualbox though but the 512 MB RAM is a little low, even for running photoshop native in windows.
I would recommend you to upgrade on the RAM, it's not very expensive nowadays, and run CS3 virtually.

---

### Post by Loaded.len on 2008-08-22
Photoshop is a RAM whore.  For anything more than the most rudimentary tasks I wouldn't try to run it on 512 on the host, let alone a guest OS. 

Does it have to be CS3?  CS2 has a Gold rating in the Wine AppDB

---

### Post by artrbinfo on 2008-08-22
Here is guide:

First off: don't expect this to work.  Wine does not yet support Photoshop CS3.  Only read these instructions if you feel like fiddling around, not if you expect to get a working Photoshop.

OK, now that you know that Wine does not yet support Photoshop CS3, here's how one person got it to install and run a while ago:

1. Copy mshtml, shdocvw, urlmon, shlwapi, mlang and jscript.dll from an XP partition to ~/.wine/drive_c/windows/system32

2. Do 'regsvr32 jscript.dll'

3. Do 'wget kegel.com/wine/winetricks && sh winetricks msxml3'

4. Set mshtml, shdocvw, urlmon, shlwapi, mlang to native in winecfg

All this is only needed to make the installer happy and finish fine. The actual Photoshop.exe doesn't need any native dlls set here, you only need gdiplus:

5. Do winetricks gdiplus (in console of choice)

Note: If Photoshop CS3.exe crashes, update to the very latest git, got it running there

Thanks to Louis Lenders for this step-by-step guide. 

[Lint to site!]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584")


If you don't have windows and you can't get those dll, there is site [dll-files]("http://www.dll-files.com/") you can download all dll you need from there.

---

### Post by aladinonl on 2008-08-22
i just install CS2 through wine, quite smooth. CS2 starts up with around 50MB which is same with Firefox but i'm not sure how it is after awhile. The class takes focus on CS3 but the teacher also explains by CS2 so I hope I can get through.
However, my problem is CS2-wine doesn't accept the activation code. Does Adobe not accept old key anymore so users are forced to buy new version? Is anyone of you experience this?

---

### Post by aladinonl on 2008-08-22
@artrbinfo
thanks, but i already read that piece. It doesn't work for me.
I heard that Wine is an actively developed project. However, CS3 came out for some time already. I hope i can get cs3 to run before cs2 trial time is over.

---

### Post by aladinonl on 2008-08-22
> **Loaded.len said:**
> 
Does it have to be CS3?  CS2 has a Gold rating in the Wine AppDB
For productivity, people say cs3 has more edges. The reason CS3 haven't got any rating because it just doesn't work :)

---

### Post by artrbinfo on 2008-08-22
> **aladinonl said:**
> @artrbinfo
thanks, but i already read that piece. It doesn't work for me.
I heard that Wine is an actively developed project. However, CS3 came out for some time already. I hope i can get cs3 to run before cs2 trial time is over.

I'll try to find personally new install method. Please give me some time, and I'll get back to you when I'll be ready!

---

### Post by liquidfunk on 2008-08-22
Photoshop CS3 won't even install without a 1Gb RAM or more. 

 Good luck.

---

### Post by aladinonl on 2008-08-23
I'm not sure whether it's my problem but cs2 seems buggy in wine. This same laptop run cs2 ok in windows few years ago. 
My class requires some other adobe products that are not wine-able yet. I'm considering dual boot with xp now. 
lol, now i want the class to over soon. This is an implemetary course for my business and marketing major.
@artrbininfo: :)

---

### Post by aladinonl on 2008-08-23
I'm not sure whether it's my problem but cs2 seems buggy in wine. This same laptop run cs2 ok in windows few years ago. 
My class requires some other adobe products that are not wine-able yet. I'm considering dual boot with xp now. 
lol, now i want the class to over soon. This is an implemetary course for my business and marketing major.
@artrbininfo: :)

---

