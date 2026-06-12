---
title: "NIV in gnomesword"
date: 2006-09-11
forum: Ubuntu Christian Edition
---

### Post by cneil on 2006-09-11
Is there any copy of the NIV Bible that you can buy or download (such as the one from biblegateway.com) and then integrate it with gnomesword.  I am also interested in the New King James version.

---

### Post by mhancoc7 on 2006-09-11
> **cneil said:**
> Is there any copy of the NIV Bible that you can buy or download (such as the one from biblegateway.com) and then integrate it with gnomesword.  I am also interested in the New King James version.

No, they are not available. AFAIK

However, here is a link that I just found.
[http://www.cs.cmu.edu/People/karl/sword/](http://www.cs.cmu.edu/People/karl/sword/)

At the bottom of the page you will see some info and another link about creating your won sword modules using Bible texts downloaded from Biblegateway.com. This is for "personal use" only of course.

Hope that helps. Keep us posted if you try it out.

God Bless, Jereme

---

### Post by cjm5229 on 2006-09-12
The NIV and New King James are copyrighted, You have to pay Zondervan for the right to use them. They are not available for free anywhere that I am aware of. The KJB has what is known as the Kings Copyright which would be the original version of FOSS. NIV and almost all other versions are Proprietory. Think Microsoft.:wink:

---

### Post by cneil on 2006-09-13
The link mhancoc7 you posted is already dead.  

Does anyone have a cached copy?

It is hard to believe that it would be illegal to download and view content that is already available online in a non-web browser program. Downloading web content, creating a cached copy, and indexing it on your local hard drive should not be illegal.  Isn't that all that creating these modules would do?

I'm sure it would be possible to write some kind of script for this anyway.

---

### Post by mhancoc7 on 2006-09-13
> **cneil said:**
> The link mhancoc7 you posted is already dead.  

Does anyone have a cached copy?

It is hard to believe that it would be illegal to download and view content that is already available online in a non-web browser program. Downloading web content, creating a cached copy, and indexing it on your local hard drive should not be illegal.  Isn't that all that creating these modules would do?

I'm sure it would be possible to write some kind of script for this anyway.

Hi, I just tried the link again and it seems to working again.
Jereme

---

### Post by bthumper on 2006-09-16
> **cneil said:**
> I am also interested in the New King James version.

The AKJV is very similar to the NKJV.

[AKJV]("http://en.wikipedia.org/wiki/American_King_James_Version")

---

### Post by yoyoned on 2006-09-17
I like the NIV as well, but since it is copywrited, I use WEB (Word English Bible) for sword.  There are also WEB MP3's on the web that are free to use.  Although I have never looked at it, I have also heard that the American Standard version is also very readable and free.

---

### Post by brjoon1021 on 2007-01-07
I wonder if the e-sword bible downloads can be massaged and installed somehow. They have ESV, ASV and very cheap versions of the Holman and several other good ones for cheap.

Better yet, has anyone gotten e-sword to work with Wine on Linux?

B.

---

### Post by mysticrider92 on 2007-01-08
Shane2peru has a thread about E-Sword in Wine [here]("http://www.ubuntuforums.org/showthread.php?t=324792"), so you could check that and see how well it works.

I think buying and changing e-sword Bibles to work in GnomeSword (or anything other than E-sword) might be somewhat illegal, because they are written for that program and probably copyrighted, so changing the code might not be allowed.

---

### Post by LaserJock on 2007-01-10
> **cneil said:**
> The link mhancoc7 you posted is already dead.  

Does anyone have a cached copy?

It is hard to believe that it would be illegal to download and view content that is already available online in a non-web browser program. Downloading web content, creating a cached copy, and indexing it on your local hard drive should not be illegal.  Isn't that all that creating these modules would do?

I'm sure it would be possible to write some kind of script for this anyway.

It is illegal to distribute the NIV without permission from Zondervan. I believe having the content cached from some site like biblegateway is fine, but you couldn't send that cache to a friend, for instance. The Sword modules are a bit more then just cached content. They have a specific format (open sourced format) but are fairly easy to do. Again, the problem is distribution.

-LaserJock

---

### Post by chaplanger on 2007-01-11
> **brjoon1021 said:**
> I wonder if the e-sword bible downloads can be massaged and installed somehow. They have ESV, ASV and very cheap versions of the Holman and several other good ones for cheap.

Better yet, has anyone gotten e-sword to work with Wine on Linux?

B.

Gnomesword has these modules available plus many other translations as well (sorry, no NIV).    Check out Gnomesword and then Edit>Module Manager.  Under Sword>Sources you should have various categories for Crosswire.org listed under current remote sources.  Then go to Sword>Configure and choose "Remote"  Once the catalogue is complete yo can choose what you would like to download and install.  (Besides Bibles, other commentaries, devotionals and works are available).

---

### Post by rurinix on 2007-04-01
> **mysticrider92 said:**
> Shane2peru has a thread about E-Sword in Wine [here]("http://www.ubuntuforums.org/showthread.php?t=324792"), so you could check that and see how well it works.

I think buying and changing e-sword Bibles to work in GnomeSword (or anything other than E-sword) might be somewhat illegal, because they are written for that program and probably copyrighted, so changing the code might not be allowed.

e-sword is also free, thus no NKJV or NIV and converting files from e-sword to gnome-sword should not be illegal.  Windows users can always use online-bible.org's software and pay the $50 to get the NIV, but using that would probably be illegal.

---

### Post by JoshHendo on 2007-04-28
> **mhancoc7 said:**
> No, they are not available. AFAIK

However, here is a link that I just found.
[http://www.cs.cmu.edu/People/karl/sword/](http://www.cs.cmu.edu/People/karl/sword/)

At the bottom of the page you will see some info and another link about creating your won sword modules using Bible texts downloaded from Biblegateway.com. This is for "personal use" only of course.

Hope that helps. Keep us posted if you try it out.

God Bless, Jereme

With the scripts on the link you gave, I get a error 

```

josh@Zoidberg:~/Bible/niv$ ../scripts/hack.bg -h
../scripts/hack.bg: 17: Syntax error: "(" unexpected (expecting ";;")

```

When I try to run it?

I really couldn't find anywhere else to ask, so if there is a better place, please tell me :)

Thanks, Josh.

---

### Post by t2technology on 2007-06-07
To install esword in Ubuntu all you have to do is go here [http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html)

Select the esword installer and run it. It will install wine if you don't already have it.

---

### Post by ishtob on 2007-07-09
> **JoshHendo said:**
> With the scripts on the link you gave, I get a error 

```

josh@Zoidberg:~/Bible/niv$ ../scripts/hack.bg -h
../scripts/hack.bg: 17: Syntax error: "(" unexpected (expecting ";;")

```

When I try to run it?

I really couldn't find anywhere else to ask, so if there is a better place, please tell me :)

Thanks, Josh.

try using bash, i just finished porting niv and nlt on my ubuntu

here's how:
```

???@????:~/Bible/niv$ bash ../scripts/hack.bg -h

```

hope that helps

---

### Post by Nimaran on 2008-01-12
I find it almost disgusting that a version of the Bible is copyrighted and closed source. It should be available to all in whatever form they want it.

---

### Post by jonathonblake on 2008-01-12
> **Nimaran said:**
> I find it almost disgusting that a version of the Bible is copyrighted and closed source.

a) Editors and translators have to eat.   Copyright payments is one way they generate revenue so that they can eat;

b) Typically, copyright revenue generated from Bible translations goes to subsidizing the printing and distribution of Bibles to those who can not afford one;

c) There are translations that are in the public domain.  The Geneva Bible, The Smith Bible, the American Standard Version, to give but three examples.  There are also a couple of modern translations that are in the public domain.

>  It should be available to all in whatever form they want it.

In an ideal world that would be the case.  But that won't happen until after the Millennium described in Revelation 20..  

xan

jonathon

---

### Post by Nimaran on 2008-01-13
Yeah, your right and I knew most of that, but I guess for some reason it just irked me. I guess just a lot of places use the NIV as their standard and I wanted it for my computer,  but your right. Everyone's gotta eat.

---

### Post by anv on 2008-01-26
Around christmas I too searched NIV for GnomeSword . I would like to pay for the module but if it is not even offered then I have to use something else, one good translation which is possible to buy for Gnome Sword is NET bible. it costs 20$ offers app. 60 000 footnotes, in some parts it offers more closer translation which reflects the original message better than many others, but as known ther is no perfect translation. But if there is someone who is involved in NIV bible work and reads this meassage, I would recommend to sell module also for this side of "moon" because there is no biblical reason to support more Windows software than Linux softwares, even it would be political difference which i doubt bible clearly says in Gal 3:28: 

"There is neither Jew nor Greek, there is neither slave nor free, there is neither male nor female - for all of you are one in Christ Jesus."

---

### Post by jonathonblake on 2008-01-27
> **anv said:**
> I would recommend to sell module also for this side of "moon"

For reasons I won't go into here, *The Sword Project*/*Crosswire Bible Society* doesn't want anything to do with money..

Most publishers want a copyright/royalty payment for their material.  This leads to a tension in how *The Sword Projeect* distributes modern material. At *BibleTech2008*, a potential solution was proposed.  If that solution is acceptable to all parties, I suspect that a number of recent resources will become available for* The Sword Project*.

xan

jonathon

---

### Post by Andy0 on 2008-02-21
I already own and have payed for multiple paper copies of the NIV.

Why should I not be able to access my paper copy in a digital environment?

I know the legal's are hard, and I understand that editors need to eat just like the rest of us, but come on it's like paying to watch the movie in theaters, then I pay to buy it to watch it over and over ..

---

### Post by Technogenius on 2009-01-07
You can still get Karl's scripts via the Internet Archive:

[http://web.archive.org/web/20071204210441/http://karl.kleinpaste.org/sword/scripts/](http://web.archive.org/web/20071204210441/http://karl.kleinpaste.org/sword/scripts/)

Technogenius

---

### Post by dawynn on 2009-01-27
Just an FYI, gnomesword and BibleTime are front-ends for "The Sword Project", and as far as I know, don't produce any modules that aren't already available for download on the main website for "The Sword Project".

(Personally, I've found BibleTime to have better layout than gnomesword, but to each his own)

Long story short, instead of ducking around to various other websites (including gnomesword's) for modules, go straight to the source.

[http://www.crosswire.org/sword/modules/](http://www.crosswire.org/sword/modules/)

Now, in my memory, I thought they used to post purchaseable copies of the versions still under copyright.  I don't see that now, though.  Policies may have changed.  Still, there are a wide variety of English bibles listed here, and a wide variety of other language modules.  But, sorry, no NIV, not even for purchase.

This also shows commentaries, and other reference material that you can add to you Sword collection.

---

### Post by Noremacam on 2009-02-27
> **Technogenius said:**
> You can still get Karl's scripts via the Internet Archive:

[http://web.archive.org/web/20071204210441/http://karl.kleinpaste.org/sword/scripts/](http://web.archive.org/web/20071204210441/http://karl.kleinpaste.org/sword/scripts/)

Technogenius

When I downloaded the script file and opened it, it gave the error messsage:

```
gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
```

I downloaded it three times to make sure its not a fluke on my end, but I got the same result. Is there another location for these scripts?

---

### Post by jonathonblake on 2009-02-27
> **Noremacam said:**
> 
Is there another location for these scripts?

Probably not.

The copyright holders that granted BibleGateway permission to put their material on that website, were very unhappy with the number of people who downloaded the data, and converted it to the format that their Bible Study Software uses.


BibleGateway periodically changes the database tables, markup, and/or other things, to thwart that usage.  

jonathon

---

### Post by aaronhahn777 on 2009-02-27
esword can be easily installed using wine... however, the additional dictionaries/translations/maps/etc don't unpack using wine or anything else I tried in linux.

simply install them on a pc, then cut and paste all the files from the pc installation into the linux installation.

ex.  cut all files from pc in:  c:/Program Files/e-Sword/
and paste in /home/aaron/.wine/drive_c/Program Files/e-Sword/
(note:  you may need to unhide files if you are not using the terminal... simply use "ctrl+H" to unhide ".wine" folder.  This will be in the same location as "Documents")

Should work great...  cheers.

---

### Post by ag65151 on 2009-02-28
> **aaronhahn777 said:**
> esword can be easily installed using wine... however, the additional dictionaries/translations/maps/etc don't unpack using wine or anything else I tried in linux.

I have not had this problem at all. I have many resources in my eSword, all have been "installed" using wine. But even if that doesn't work, I have seen many people have success using the script located in the first post on [this]("http://ubuntuforums.org/showthread.php?t=372359") thread.

---

