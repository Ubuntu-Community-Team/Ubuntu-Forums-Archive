---
title: "What webcomics would you like in a webcomic-reader?"
date: 2014-11-03
forum: The Cafe
---

### Post by theo-friberg on 2014-11-03
Hello.

I (Théo Friberg) have been writing a webcomic-reader app for Ubuntu Mobile. For the time being I have only integrated three comics I personally like (xkcd, Freefall and Twokinds). I would want to ask you the following question:

What webcomics would you like in the app? I will try to integrate them, but they must either have a permissive license or an author willing to co-operate.

Here are some screenshots for those that can't test the app in an emulator or a physical device (though it is available in the Ubuntu Mobile Software Scope):

[IMG]https://myapps.developer.ubuntu.com/site_media/appmedia/2014/11/screen_1.png[/IMG]

[IMG]https://myapps.developer.ubuntu.com/site_media/appmedia/2014/11/screen_2.png[/IMG]


[IMG]https://myapps.developer.ubuntu.com/site_media/appmedia/2014/11/screen_3.png[/IMG]

Also, would this question be better fitted in some other place (AskUbuntu or some other corner of the forums)?

Sincerely, Théo Friberg

---

### Post by theo-friberg on 2014-11-08
Please, could you post your favourites here. I would greatly appreciate it, and add them to my app if possible. Do you really not want to tell a developer what features you want? :p

---

### Post by Matthew_Harrop on 2014-11-08
I tend to look at [http://memebase.cheezburger.com/webcomics?ref=navbar](http://memebase.cheezburger.com/webcomics?ref=navbar)
I particularly like Cyanide and Happiness :)

---

### Post by Elfy on 2014-11-08
> **theo-friberg said:**
> Please, could you post your favourites here. I would greatly appreciate it, and add them to my app if possible. Do you really not want to tell a developer what features you want? :p

At a guess, I would have thought that people would rather the app allowed them to choose what they wanted, when they wanted, for as long as they wanted - not have to ask a developer to add something for them. Just a thought ;)

---

### Post by theo-friberg on 2014-11-10
> **Matthew_Harrop said:**
> I tend to look at [http://memebase.cheezburger.com/webcomics?ref=navbar](http://memebase.cheezburger.com/webcomics?ref=navbar)
I particularly like Cyanide and Happiness :smile:

Thank you, i will look into it. I was really starting to think i wouldn't get any suggestions at all. :p

> **Elfy said:**
> At a guess, I would have thought that people would rather the app allowed them to choose what they wanted, when they wanted, for as long as they wanted - not have to ask a developer to add something for them. Just a thought ;)

That would make sense, allas it is not really possible for now. Though if I or you find any viable way to do it, I would be more than happy to implement it. For now my plan is to get a list of about twenty-to-thirty most popular comics for users to pick from. The comics would be added automatically to the list as they get published, though. As for when the user wants them: I will try to get some kind of cache working.

PS: For geeky people: Link to the the GitHub repo: [https://github.com/nomelif/ComicShelf](https://github.com/nomelif/ComicShelf) .

---

### Post by Matthew_Harrop on 2014-11-10
Perhaps you could market the app as a way for comic writers to further market their comics? What does the app add that using a website doesn't? 
Interactive comics perhaps?

---

### Post by GeoRW on 2014-11-11
You can implement support for some comic book format which supports  webcomics viewing like ACBF for example: [https://launchpad.net/acbf](https://launchpad.net/acbf)

```
<?xml version="1.0" encoding="utf-8"?>
<ACBF xmlns="http://www.fictionbook-lib.org/xml/acbf/1.0">
 <meta-data>
   ...
 </meta-data>
 <body>
   <page>
     <image href="http://imgs.xkcd.com/comics/manuals.png"/>
   </page>
   <page>
     <image href="http://imgs.xkcd.com/comics/digits.png"/>
   </page>
   ...
 </body>
</ACBF>
```

People can then create those files for themselves.

---

### Post by theo-friberg on 2014-11-11
> **Matthew_Harrop said:**
> Perhaps you could market the app as a way for comic writers to further market their comics? What does the app add that using a website doesn't?
Interactive comics perhaps?

The main points would be convenience for the reader (all in the same place) and indeed a way for authors to further market their comics. As for interactive comics: That would be a **huge** amount of work.

> **GeoRW said:**
> You can implement support for some comic book format which supports webcomics viewing like ACBF for example: [https://launchpad.net/acbf](https://launchpad.net/acbf)

```
<?xml version="1.0" encoding="utf-8"?>
<ACBF xmlns="http://www.fictionbook-lib.org/xml/acbf/1.0">
 <meta-data>
   ...
 </meta-data>
 <body>
   <page>
     <image href="http://imgs.xkcd.com/comics/manuals.png"/>
   </page>
   <page>
     <image href="http://imgs.xkcd.com/comics/digits.png"/>
   </page>
   ...
 </body>
</ACBF>
```

People can then create those files for themselves.

That looks like a great idea. The thing I was thinking first was to get many web-based comics in the same place (and especially stories that update regularly on a site rather than archives), but I will have a look at that. I don't know how doable that is. Thank you for the tip anyway. :p

And to Matthew_Harrop: I looked into *Cyanide and Happ**ines* eysterday, but today it seems to have completely vanished!? (When I go to the site, it says the account has been suspended). This seems rather mysterious.

---

### Post by Matthew_Harrop on 2014-11-11
> The main points would be convenience for the reader (all in the same  place) and indeed a way for authors to further market their comics. As  for interactive comics: That would be a **huge** amount of work.

Would be an **EPIC **App though!

Cyanide and Happiness has gone :( Hopefully it'll be back soon though!

---

### Post by theo-friberg on 2014-12-18
I have updated the app (to fix a failure caused by a site updating), and would most kindly ask what content should I add. Sadly supporting .cbz or such seems very complicated at this point.

Sincerely, Théo Friberg

---

