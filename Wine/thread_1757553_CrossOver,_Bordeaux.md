---
title: "CrossOver, Bordeaux"
date: 2011-05-13
forum: Wine
---

### Post by coljohnhannibalsmith on 2011-05-13
Hello,

I've just installed a program called CrossOver from the repositories.  It claims that it makes using Wine easy...

Does it require Wine to run?

Does it store apps to the same C:\ that wine does?

Does it add any functionality to; or is it any less buggy than Wine?

Is it any different than Bordeaux? (Which, I've found to be basically usesless).

Is it any different than Play On Linux? (Which, I'm also not sure is very useful).


[B][I]I have the 1.3 x64 version of Wine installed.

[IMG]http://www.h-online.com/imgs/43/6/2/3/1/1/5/CrossOver_Impersonator_Logo_200-870a7289a5d68739.png[/IMG]
[/I][/B] 




Thanks Hannibal

---

### Post by Perfect Storm on 2011-05-13
> Does it require Wine to run?

No.

> Does it store apps to the same C:\ that wine does?

Only if you want to. Usually you split apps into bottles which can contain different settings and stuff to make it work.

> Does it add any functionality to; or is it any less buggy than Wine?
Yes and no. Those stuff that are official supported works very well.


But if you're looking for playing games, it's better to get crossover Games instead.

---

### Post by coljohnhannibalsmith on 2011-05-13
[COLOR=Blue]Wow 14,592 beans...  Jeeze!!![/COLOR]

Hello Master Yoda!!!:D

Thanks for your reply...

Actually, I'm more interested in installing apps like ***MS Office, *** ***Camtasia, & MS SharePoint.***  Camtasia almost installed under Wine 1.3, & MS SharePoint not at all.

Also, I have Bordeaux, Play On Linux, and Now CrossOver installed.  I think I'm going to leave Wine installed; but can I get rid of Bordeaux and Play On Linux; or should I leave these installed as well?


[B][I]BTW, I just checked the CrossOver site.  CrossOver Games is a separate app from CrossOver Pro???  Can I still install large Windows apps with CrossOver Games, or is it an "either/or" situation???  Which would you recommend; or can I should I install both side-by-side???

[/I][/B] [IMG]http://mattovermatter.com/wp-content/uploads/2010/11/yoda.jpg[/IMG]




**Deus Ex Machina** ( [***day**-&#601;s*]("http://en.wikipedia.org/wiki/Wikipedia:Pronunciation_respelling_key") [*eks*]("http://en.wikipedia.org/wiki/Wikipedia:Pronunciation_respelling_key") [***mah**-kee-n&#601;*]("http://en.wikipedia.org/wiki/Wikipedia:Pronunciation_respelling_key")) in English; means [COLOR=Blue]*"god from our hands"*[/COLOR] or [COLOR=Blue]*"god that we make",  [COLOR=Black]implying[/COLOR] that the device of said god is entirely artificial or conceived  by man.*[/COLOR]

---

### Post by coljohnhannibalsmith on 2011-05-15
Well,

It turns out that CrossOver Pro, CrossOver Standard, & CrossOver Games are indeed separate apps.

CrossOver Pro and CrossOver Standard are both available in the repositories and CrossOver Games must be downloaded from their site as a .deb.

[http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/)

In 'all' CrossOver products, there is a list of supported applications.  CrossOver Games does not 'list' support for large Windows applications, while CrossOver Pro does.  Also, they do 'not' appear to want to exist side-by-side; so it appears CrossOver Pro is the correct choice for me.  CrossOver Pro does offer game support, so I'm not sure what the difference is...  It may be that CrossOver Games offers better frame-rates and other game optimized features.  They sure have some neat looking games!!!

[COLOR=Blue]***I can't wait to try some!!!!***[/COLOR] (Pro has Game Support)

[IMG]http://www.youtube.com/watch?v=YRdVI3TEJS0[/IMG][IMG]http://www.youtube.com/watch?v=YRdVI3TEJS0[/IMG][http://www.youtube.com/watch?v=YRdVI3TEJS0](http://www.youtube.com/watch?v=YRdVI3TEJS0)





[COLOR=Red]**Hannibal**[/COLOR]

P.S., If someone has found a way to get Pro & Games to coexist on the same system; please post...

---

### Post by ajackson on 2011-05-16
Crossover Pro/Standard is aimed more at the non-gaming side of Windows applications, things like Office, etc.

Crossover Games is, as the name suggests, meant more for gaming.

Both are built upon Wine (they both use 1.3.9 at the moment) but with tweaks added that can't be included in mainstream Wine, obviously Games has tweaks aimed at stuff like directx while Pro/Standard has tweaks to get around some of the oddities that cause issues with certain apps.

> **coljohnhannibalsmith said:**
> P.S., If someone has found a way to get Pro & Games to coexist on the same system; please post...

Just install both, they are designed to co-exist. Games stores it bottles in ~/.cxgames and Pro/Standard in ~/.cxoffice, each bottle is a Wine prefix (the default Wine default for mainstream wine is ~/.wine).

The Crossover products are Wine with a lot of spit and polish plus support and Codeweavers are the main supporter of the Wine project in fact a lot of the Wine developers are actually Codeweavers staff.

---

### Post by coljohnhannibalsmith on 2011-05-16
> **ajackson said:**
> Just install both, they are designed to co-exist. Games stores it bottles in ~/.cxgames and Pro/Standard in ~/.cxoffice, each bottle is a Wine prefix (the default Wine default for mainstream wine is ~/.wine).


[COLOR=Blue]***You're absolutely right...  I don't know why I was having trouble...***[/COLOR]

I think it might have been because Software Center crashed.  It's much better integrated with the other package managers; but it doesn't shut down properly, and hasn't since Maverick.  I'd also like to see Software Center intergated with PACO as well.

BTW, CrossOver Pro and CrossOver Games are both free trials.  Do you have any idea what Codeweavers is going to charge, when they finally demand payment???






[COLOR=Blue]**Thanks Hannibal**[/COLOR]

---

### Post by Perfect Storm on 2011-05-16
If you buy it now you can get a crossover Bundle (Crossover Office (normal version) & Crossover Games) for $16 because they have 15 years birthday today. + 1 year of free upgrades.
[http://www.codeweavers.com/products/bundle/](http://www.codeweavers.com/products/bundle/)


Crossover Games cost normally 39.95 a year

Crossover Office (normal version) cost normally 39.95 a year

Crossover Office (pro version) cost normally 69.95 a year


I only use Crossover Games the last couple of years as I'm only need some games to play that I can't live without :P

---

### Post by coljohnhannibalsmith on 2011-05-16
Thank you for your reply,

The CrossOver apps seem like excelent products; and the discount seems reasonable; but having to pay again every year doesn't seem that attractive.  Do the yearly payments just provide me with updates and support; [COLOR=Blue]***or will the app stop working if I don't renew at year 2[COLOR=Black]???[/COLOR]***[/COLOR]





Thanks Hannibal

---

### Post by ajackson on 2011-05-16
> **coljohnhannibalsmith said:**
> The CrossOver apps seem like excelent products; and the discount seems reasonable; but having to pay again every year doesn't seem that attractive.  Do the yearly payments just provide me with updates and support; [COLOR=Blue]***or will the app stop working if I don't renew at year 2[COLOR=Black]???[/COLOR]***[/COLOR]
No the money gets you updates and support for a year, after that (if you don't renew) you still have a working version but no support or updates.

---

### Post by Perfect Storm on 2011-05-16
It will still work after it expires, but you won't get any new updates.

---

### Post by coljohnhannibalsmith on 2011-05-16
> **ajackson said:**
> No the money gets you updates and support for a year, after that (if you don't renew) you still have a working version but no support or updates.

Thank you gentlemen.  That makes perfect sense.

I think I can live with this arrangment.





Hannibal

---

