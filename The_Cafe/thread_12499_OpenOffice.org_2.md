---
title: "OpenOffice.org 2"
date: 2005-01-24
forum: The Cafe
---

### Post by TravisNewman on 2005-01-24
So has anyone tried it out yet? It looks like it hit sid recently (or maybe one of my other sources, but I don't think any of them would have it), and I'm waiting on it to download right now (cable internet is going slow lately).

---

### Post by TravisNewman on 2005-01-25
Scratch that, forgot I added the sid repositories.
yes, I did do some apt-pinning :)

But anyway, i would like to know what people think. In general, i think it's about the same unfortunately.

---

### Post by poofyhairguy on 2005-01-25
[QUOTE=panickedthumb]Scratch that, forgot I added the sid repositories.
yes, I did do some apt-pinning :)

But anyway, i would like to know what people think. In general, i think it's about the same unfortunately.[/QUOTE]

Actually it WAS recently added to Hoary!

I'm using the Openoffice2 writer right now, its sweet. Much less clutted than the old one. I always liked Abiword more, but now I'm going to give the new Openoffice a chance.



NOTE TO DEVS: The OpenOffice2 in the repo. currently has the ugly splash screen.

---

### Post by Lovechild on 2005-01-25
it appears that full OpenOffice2 has hit Hoary, I'm apt-getting as we speak.

---

### Post by poofyhairguy on 2005-01-25
[QUOTE=Lovechild]it appears that full OpenOffice2 has hit Hoary, I'm apt-getting as we speak.[/QUOTE]


be sure to get the 

openoffice.org2-gnome package as well!

---

### Post by wayover13 on 2005-01-25
[QUOTE=panickedthumb]But anyway, i would like to know what people think. In general, i think it's about the same unfortunately.[/QUOTE]

You've obviously never tried creating, or importing, page-spanning table columns or cells. I've been using the development branch since 680m65 or something and this problem is fixed there (this is the 2.0 development branch). You can now create and/or successfully import tables with columns or cells that span pages. This is a big improvement. I had to use a really horrible kludge in the paper I'm writing under the 1.x series to get the sort of pseudo-table layout I needed. Many business users were complaining on the forums about tables getting butchered when imported from other formats. So, this is a big improvement in functionality. I found another bug that would not allow insertion of pages at the beginning of a document that used text frames, and I hope they're fixing that one, too. But I've read about some misfeatures as well (they've tried to make some things work more like the competing proprietary product, which has upset some OOo users who like the way it worked before). My .02

James

---

### Post by Lovechild on 2005-01-25
[QUOTE=poofyhairguy]be sure to get the 

openoffice.org2-gnome package as well![/QUOTE]


Did that, it dies on startup with a message that an unforseen action happened.

---

### Post by TravisNewman on 2005-01-25
Yeah I've got openoffice.org2-gnome installed , and yeah James you're right, I hadn't played with it that much, but the more I do the more I notice changes, and unfortunately the more it works like that proprietary product you mentioned. I do like some of the changes that they made toward that, because some stuff in OOo was kinda counterintuitive, but some stuff is going in the wrong direction. Ah well, it's not final yet, so no use complaining about it yet I don't guess, I'll just see how it turns out. Overall I'm liking it better.

---

### Post by Spif on 2005-01-25
Will OOo 2.0 be available for Warty?

---

### Post by TravisNewman on 2005-01-25
I think that by the time OOo 2 comes around final, it'll be close to time for Hoary to come out. I'm editing my first post though, just so there's no confusion. I didn't get OOo2 from the hoary repositories.

---

### Post by leech on 2005-01-27
I don't have spell check working in OOowriter 2, and it just crashed on me when I clicked the little lightbulb thing.  Spell check works in 1.1.3.  I installed it from the Hoary repo.  No sid here.

Leech

---

### Post by BWF89 on 2005-01-28
I'm still useing OOo 1.1.2 on my WinXP box...

How long until the stable OOo 2.0 hits the digital shelves?

---

### Post by LB06 on 2005-01-28
Will Hoary be using an integrated version of OOo 1.1.x, if OOo 2.0 hasn't arrived by then?

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=LB06]Will Hoary be using an integrated version of OOo 1.1.x, if OOo 2.0 hasn't arrived by then?[/QUOTE]

It seems that 1.1.3 will be the default....and 2.0 will be in the unsupported repo.

---

### Post by KiwiNZ on 2005-01-31
Open Office 2 is a big improvement .However it still has that annoying slow start up problem that has plagued OO.O since the begining

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=KiwiNZ]Open Office 2 is a big improvement .However it still has that annoying slow start up problem that has plagued OO.O since the begining[/QUOTE]


install the 

ooqstart-gnome

package. That plus prelinking really speeds up the start time!

---

### Post by CowPie on 2005-01-31
[QUOTE=panickedthumb]So has anyone tried it out yet? It looks like it hit sid recently (or maybe one of my other sources, but I don't think any of them would have it), and I'm waiting on it to download right now (cable internet is going slow lately).[/QUOTE]
 It's nicer than 1.0 that's for sure.  But, I still don't don't know how to make a specific colour transparent like in MS Word and the help crashes on me.  And the drawing toolbar icons are really big.

I still prefer the speedy Abiword...for anyone who apt-gets that, make sure you install all the *suggested* packages after!

---

### Post by CowPie on 2005-01-31
[QUOTE=poofyhairguy]install the 

ooqstart-gnome

package. That plus prelinking really speeds up the start time![/QUOTE]
 Oh thanks I'll try that.  I forgot to add that it also takes longer than OO1.0 to start...as in 2 minutes longer :(  But I'll try this

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=CowPie]Oh thanks I'll try that.  I forgot to add that it also takes longer than OO1.0 to start...as in 2 minutes longer :(  But I'll try this[/QUOTE]

This helps too:

[http://www.ubuntuforums.org/showpost.php?p=9864&postcount=80](http://www.ubuntuforums.org/showpost.php?p=9864&postcount=80)

---

### Post by WirelessMike on 2005-02-21
Is there an easy way to get firefox to default OOo2 for mime types doc, xls, etc.?

---

### Post by BWF89 on 2005-02-21
I went to OpenOffice.org but it still says version 1.1.4 at at top of the screen.
[http://www.openoffice.org/](http://www.openoffice.org/)

When will the stable Windows XP version be out?

---

### Post by poofyhairguy on 2005-02-21
[QUOTE=BWF89]I went to OpenOffice.org but it still says version 1.1.4 at at top of the screen.
[http://www.openoffice.org/](http://www.openoffice.org/)

When will the stable Windows XP version be out?[/QUOTE]

Probably same time the Linux version is released. The version in Hoary is a preview release.

---

### Post by BWF89 on 2005-02-21
[QUOTE=poofyhairguy]Probably same time the Linux version is released. The version in Hoary is a preview release.[/QUOTE]
Thanks, that clears things up.

---

### Post by poofyhairguy on 2005-02-21
[QUOTE=BWF89]Thanks, that clears things up.[/QUOTE]

No prob. I have high hopes that OpenOffice.org 2 will be more native to windows. I want to spread it like I spread Firefox. That way, when all my family and friends dong want to buy Longhorn, I can move them to an OS (Ubuntu if it keeps kicking ass) that uses the same Apps they already use.

Firefox is what got me hooked.

---

### Post by macewan on 2005-02-22
OpenOffice.org2 on Warty

For what it's worth I just installed OOo2 on Warty via apt-get using the Hoary rep & things seem to work fine.

---

### Post by defkewl on 2005-03-04
I don't even know how to add page number in Open Office 1.1.4. Hopefully they have it in OO 2.

---

### Post by jallamann_ on 2005-03-10
I'm a newbie in Ubuntu, and have a little dumb question.. How do I install Open Office 2?

---

### Post by macewan on 2005-03-10
System > Administration > Synaptic Package Manager

search OpenOffice.org

---

