---
title: "Simple question: Why is Epiphany so much faster and reliable then Firefox or Opera?"
date: 2006-05-21
forum: The Cafe
---

### Post by RAV TUX on 2006-05-21
Simple question: but I have been wondering why Epiphany & Galeon are so much faster and reliable then Firefox, Opera and Konqueror?

---

### Post by aysiu on 2006-05-21
Firefox and Opera are designed for three platforms--Linux, Windows, and Mac.

Epiphany is designed for Linux.

That said, Firefox has worked fine for me.

---

### Post by RAV TUX on 2006-05-21
[quote=aysiu]Firefox and Opera are designed for three platforms--Linux, Windows, and Mac.

Epiphany is designed for Linux.

That said, Firefox has worked fine for me.[/quote]


Firefox has worked fine for me too. I am not knocking other browsers but was looking for a more technical reason why consistently Epiphany is faster on Ubuntu Dapper beta.

---

### Post by henriquemaia on 2006-05-21
[quote=yozef]Firefox has worked fine for me too. I am not knocking other browsers but was looking for a more technical reason why consistently Epiphany is faster on Ubuntu Dapper beta.[/quote]

Epiphany is designed for Linux, as Aysiu said. 

Have you tried [Swiftfox]("http://getswiftfox.com/")?

---

### Post by RAV TUX on 2006-05-21
[quote=henriquemaia]Epiphany is designed for Linux, as Aysiu said. 

Have you tried [Swiftfox]("http://getswiftfox.com/")?[/quote]

No, I'll try it now.

---

### Post by henriquemaia on 2006-05-21
[quote=yozef]No, I'll try it now.[/quote]

Tell us about your impressions of it, I curious to know.

---

### Post by prizrak on 2006-05-21
Firefox also uses XUL which makes it take up alot of RAM. Epiphany uses the same GTK as GNOME does so it's using a lot of the shared libraries making it faster since they are already in RAM.

---

### Post by Lucho on 2006-05-21
Maybe it's just my machine, but I've never been able to notice a
speed difference between Opera and Epiphany. Both are faster than
firefox, at least on my machine.

---

### Post by henriquemaia on 2006-05-22
[quote=Lucho]Maybe it's just my machine, but I've never been able to notice a
speed difference between Opera and Epiphany. Both are faster than
firefox, at least on my machine.[/quote]

There is this test you can do to know the rendering times of different browsers.

[http://scragz.com/tech/mozilla/test-rendering-time.php](http://scragz.com/tech/mozilla/test-rendering-time.php)

Epiphany is faster on my machine (not that I notice, but this site's results).

---

### Post by RAV TUX on 2006-05-22
I found a more in depth reason why, beyond being built for Linux, Epiphany is built for the Gnome desktop:

[http://www.gnome.org/projects/epiphany/documentation/manifesto.html](http://www.gnome.org/projects/epiphany/documentation/manifesto.html)

     **Manifesto**

      A web browser is more than an application, it is a way of thinking, it is a way of seeing the world. Epiphany's principles are simplicity and standards compliance.
      **Simplicity**

      Epiphany aims to utilize the simplest interface possible for a browser. Keep in mind that simple does not necessarily mean less powerful. We believe the commonly used browsers of today are too big, buggy, and bloated. Epiphany addresses simplicity with a small browser designed for the web -- not mail, newsgroups, file management, instant messenging or coffee making. The UNIX philosophy is to design small tools that do one thing, and do it well.
      Epiphany also address simplicity with modularity to make a light and powerful application. If something can be implemented using external applications or components, we use it rather than wasting resources in the web browser. Integration will be achived with CORBA, Bonobo, and the ever popular command line.
      Mail will be handled with your favorite e-mail application (Evolution, pine, mutt, balsa, pronto, whatever).
      **Standards compliance**

      The introduction of non-standard features in browsers could make it difficult or impossible to use alternative products like Epiphany if developers embrace them. Alternative (standards complying) browsers could not be able to fully access web sites making use of these features. The success of non-standard features can ultimately lead to forcing one browser, on one platform to dominate the market.
      Standards compliance ensures the freedom of choice. Epiphany aims to achieve this.
      **User interface lines**

      **HIG compliance**

      Epiphany is going to follow version 1.0 of the gnome user guidelines. Unless there are very serious reasons to make an exception not following it will be considered a bug. "I follow the HIG only when I like it" is not a legitimate approach. Any areas where we diverge from the HIG will communicated to the HIG team for future consideration.
      **Gnome integration**

      Epiphany's main goal is to be integrated with the gnome desktop. We don't aim to make Epiphany usable outside Gnome. If someone will like to use it anyway, it's just a plus. For example: Making people happy that don't have control centre installed is not a good reason to have mime configuration in Epiphany itself.
      **Simple design**

      Feature bloat and user interface clutter is evil :)
      **Preferences**

      We will follow the new gnome policy about preferences; Havoc Pennington already [explained]("http://www106.pair.com/rhp/free-software-ui.html") it a lot better than we could ever do.
      **User target**

      We target non-technical users by design. This happens to be 90% of the user population. (Technical details should not be exposed in the interface.) We target web users, we don't directly target web developers. A few geek-oriented feautures can be kept as long as they are non-obtrusive.
   
         Navigation[LIST]
[*][Home]("http://www.gnome.org/projects/epiphany/index.html")
[*][News]("http://www.gnome.org/projects/epiphany/news.html")
[*][Screenshots]("http://www.gnome.org/projects/epiphany/screenshots/")
[*][Downloads]("http://www.gnome.org/projects/epiphany/downloads.html")
[*][Development]("http://www.gnome.org/projects/epiphany/development/")
[*]         [Documentation]("http://www.gnome.org/projects/epiphany/documentation/index.html")[LIST]
[*][FAQ]("http://live.gnome.org/Epiphany/FrequentlyAskedQuestions")
[*]Manifesto
[*][Reference Manual]("http://www.gnome.org/projects/epiphany/documentation/reference/index.html")
[*][Extension HOWTO]("http://www.gnome.org/projects/epiphany/documentation/extensions/index.html")[/LIST] 
[*][Extensions]("http://www.gnome.org/projects/epiphany/extensions.html")
[*][Smart Bookmarks]("http://www.gnome.org/projects/epiphany/smartbookmarks.html")
[*][External Resources]("http://www.gnome.org/projects/epiphany/resources.html")[/LIST]      Contact
      You can contact developers [EMAIL="epiphany-list@gnome.org"]sending a mail[/EMAIL] to the [Epiphany mailing list]("http://mail.gnome.org/mailman/listinfo/epiphany-list/"). You do not need to be subscribed.
      We are also often available to [chat on IRC]("irc://irc.gnome.org:6667/epiphany").
    **Server:** irc.gnome.org
    **Channel:** #epiphany
   
         [[IMG]http://www.gnome.org/projects/epiphany/images/epiphany-64.png[/IMG]]("http://www.gnome.org/projects/epiphany/")       
             An epiphany in browsing.

---

### Post by RAV TUX on 2006-05-22
[quote=prizrak]Firefox also uses XUL which makes it take up alot of RAM. Epiphany uses the same GTK as GNOME does so it's using a lot of the shared libraries making it faster since they are already in RAM.[/quote]

This is more of an explanation I was looking for, Thank you.

---

### Post by Lucho on 2006-05-22
I ran the scragz.com test; that was interesting. Like I said,* I*
don't notice a difference, but here's the results from the site:
```
Opera 8.54
scragz.com:

9.096999883651733

Epiphany 1.8.3

7.953999996185303
```

  Not bad considering my very unstable internet connection
(long story: crappy provider).

---

### Post by henriquemaia on 2006-05-22
[quote=Lucho]I ran the scragz.com test; that was interesting. Like I said,* I*
don't notice a difference, but here's the results from the site:
```
Opera 8.54
scragz.com:

9.096999883651733

Epiphany 1.8.3

7.953999996185303
``` 
  Not bad considering my very unstable internet connection
(long story: crappy provider).[/quote]

I also get a 1 to 2 sec. of difference between Firefox and Epiphany.

---

### Post by fuscia on 2006-05-22
[QUOTE=Lucho]I ran the scragz.com test; that was interesting. Like I said,* I*
don't notice a difference, but here's the results from the site:
```
Opera 8.54
scragz.com:

9.096999883651733

Epiphany 1.8.3

7.953999996185303
```

  Not bad considering my very unstable internet connection
(long story: crappy provider).[/QUOTE]

on my old machine (700mhz celeron), firefox took 12 something, opera took 16 something, konqueror took 27 something (LOL! keep the file browsing job, kid) while dillo took less than 2 seconds.

---

### Post by RAV TUX on 2006-05-22
[quote=fuscia]on my old machine (700mhz celeron), firefox took 12 something, opera took 16 something, konqueror took 27 something (LOL! keep the file browsing job, kid) while dillo took less than 2 seconds.[/quote]

nice figures I will give Dillo a try, is it in the Synaptic Package Manager?

---

### Post by RAV TUX on 2006-05-22
[quote=fuscia]on my old machine (700mhz celeron), firefox took 12 something, opera took 16 something, konqueror took 27 something (LOL! keep the file browsing job, kid) while dillo took less than 2 seconds.[/quote]

OK I found Dillo in the Synaptic Package Manager and I installed it but There is no short cut icon anywhere how do I find Dillo and how do I place a shortcut for dillo in my internet menu?

---

### Post by fuscia on 2006-05-22
[QUOTE=yozef]OK I found Dillo in the Synaptic Package Manager and I installed it but There is no short cut icon anywhere how do I find Dillo and how do I place a shortcut for dillo in my internet menu?[/QUOTE]

here's a better version of dillo. it's patched to allow frames, tabs and some ssl support (whatever that is). [http://teki.jpn.ph/pc/software/index-e.shtml](http://teki.jpn.ph/pc/software/index-e.shtml)
dillo is usually found in /usr/local/bin. open your file browser, navigate to /usr/local/bin and drag the dillo icon on to your desk. or a toolbar. if you want it only in the menu, do *sudo update-menus* and this will update the debian menu in your menu list. if you don't have the debian menu (i believe it's default in ubuntu desktop), you can get it be doing *sudo apt-get install menu*. i believe this is all correct, though i'm just a humble end user and i'm never really certain about anything i write.

---

### Post by GoA on 2006-05-22
I prefer Opera, best on all platforms.

---

### Post by henriquemaia on 2006-05-22
[quote=fuscia]here's a better version of dillo. it's patched to allow frames, tabs and some ssl support (whatever that is). [http://teki.jpn.ph/pc/software/index-e.shtml]("http://teki.jpn.ph/pc/software/index-e.shtml")
dillo is usually found in /usr/local/bin. open your file browser, navigate to /usr/local/bin and drag the dillo icon on to your desk. or a toolbar. if you want it only in the menu, do *sudo update-menus* and this will update the debian menu in your menu list. if you don't have the debian menu (i believe it's default in ubuntu desktop), you can get it be doing *sudo apt-get install menu*. i believe this is all correct, though i'm just a humble end user and i'm never really certain about anything i write.[/quote]


Good suggestion! I really like Dillo and it is nice to have one that can handle frames.

---

### Post by fuscia on 2006-05-22
oops! update-menus does **not** add dillo to the menus. but, most DE/wms have some kind of menu editor.

---

### Post by henriquemaia on 2006-05-22
[quote=fuscia]oops! update-menus does **not** add dillo to the menus. but, most DE/wms have some kind of menu editor.[/quote]

Did you manage to compile this new Dillo sucessfully? If so, how? I got some error while making.

---

### Post by OffHand on 2006-05-22
On my machine Epiphane is the slowest. Here are the results of the 3rd refresh of each browser:

```

7.984 Swiftfox

8.221 Firefox

8.281 Epiphani

```

Measured on this page:

[http://scragz.com/tech/mozilla/test-rendering-time.php](http://scragz.com/tech/mozilla/test-rendering-time.php)

---

### Post by RAV TUX on 2006-05-22
[quote=fuscia]here's a better version of dillo. it's patched to allow frames, tabs and some ssl support (whatever that is). [http://teki.jpn.ph/pc/software/index-e.shtml](http://teki.jpn.ph/pc/software/index-e.shtml)
dillo is usually found in /usr/local/bin. open your file browser, navigate to /usr/local/bin and drag the dillo icon on to your desk. or a toolbar. if you want it only in the menu, do *sudo update-menus* and this will update the debian menu in your menu list. if you don't have the debian menu (i believe it's default in ubuntu desktop), you can get it be doing *sudo apt-get install menu*. i believe this is all correct, though i'm just a humble end user and i'm never really certain about anything i write.[/quote] 
 I went to the link and grabbed and dropped on my launcher panel:
[[dillo_0.8.5.orig.tar.gz]]("http://ftp.debian.org/debian/pool/main/d/dillo/dillo_0.8.5.orig.tar.gz") [[dillo_0.8.5-4.diff.gz]]("http://ftp.debian.org/debian/pool/main/d/dillo/dillo_0.8.5-4.diff.gz") 
I'm not sure if this was the right ones or not but now I have two beautiful orange glowing orbs on my launcher panel.

what do I do next? or did I do this all wrong?


here is a screenshot of the two orange glowing orbs, top panel, center:

[[IMG]http://img262.imageshack.us/img262/3742/screenshot4iw.th.png[/IMG]]("http://img262.imageshack.us/my.php?image=screenshot4iw.png")

*Duck Motif wallpaper by STMan
[http://ubuntuforums.org/gallery/showimage.php?i=2708&original=1&c=newimages](http://ubuntuforums.org/gallery/showimage.php?i=2708&original=1&c=newimages)

---

### Post by RAV TUX on 2006-05-22
[quote=subsonic_shadow]On my machine Epiphane is the slowest. Here are the results of the 3rd refresh of each browser:

```

7.984 Swiftfox

8.221 Firefox

8.281 Epiphani

``` 
Measured on this page:

[http://scragz.com/tech/mozilla/test-rendering-time.php]("http://scragz.com/tech/mozilla/test-rendering-time.php")[/quote]

how does dillo compare to these?

---

### Post by RAV TUX on 2006-05-22
[quote=henriquemaia]Tell us about your impressions of it, I curious to know.[/quote]

I'm a bit stuck on the swifterfox, as far as whch intel processor to select on this old box.

---

### Post by _simon_ on 2006-05-22
I use Swiftfox 1.5.0.3

My rendering time is loads quicker than any posted above for some reason?

See screenshot.

---

### Post by picpak on 2006-05-22
Opera loads that page in 16 seconds; Firefox in 30.

This is a no-brainer.:rolleyes:

---

### Post by fuscia on 2006-05-22
[QUOTE=yozef]how does dillo compare to these?[/QUOTE]

it loads all of the numbers and none of the wallpaper in less than two seconds (no js., so there's no time listed). it's not pretty. it's just fast.

---

### Post by aysiu on 2006-05-22
[QUOTE=picpak]Opera loads that page in 16 seconds; Firefox in 30.

This is a no-brainer.:rolleyes:[/QUOTE] If that was my computer, I would use Opera, too. As it is, my Firefox loads the page in 10 seconds. I don't see any reason to switch and lose all my useful extensions.

**Edit**: That's weird. When I enable Javascript on that page, it has a pop-up that says "6.97blahblahblah," but it definitely took 10 seconds.

In Epiphany the pop-up says "5.98blahblahblah," but it also took 10 seconds for the page to load.

---

### Post by jason.trier on 2006-05-23
Opera- 2.59
Swiftfox- 3.41
Galeon- 5.21
Epiphany- 5.47

---

### Post by picpak on 2006-05-23
[QUOTE=aysiu]If that was my computer, I would use Opera, too.[/QUOTE]

Keep in mind that this is Firefox 1.5 with tweaks from [Speeding Up Firefox The Right Way](http://codebetter.com/blogs/darrell.norton/archive/2005/01/28/48720.aspx) (Fast Computer Fast Connection, despite the fact this computer isn't very fast).

*edit* Disabling the status bar in Opera cuts it by a second. But it may just be loading from my cache.

---

### Post by aysiu on 2006-05-23
[QUOTE=picpak]Keep in mind that this is Firefox 1.5 with tweaks from [Speeding Up Firefox The Right Way](http://codebetter.com/blogs/darrell.norton/archive/2005/01/28/48720.aspx) (Fast Computer Fast Connection, despite the fact this computer isn't very fast).

*edit* Disabling the status bar in Opera cuts it by a second. But it may just be loading from my cache.[/QUOTE] I'm just going to keep in mind that's your computer, because I'm using Firefox 1.5.0.3 without tweaks, and it doesn't take 30 seconds to load that page.

---

### Post by bruce89 on 2006-05-23
I got :
ephy - 3.7230000495910645
firefox - 7.53600001335144.
Seems a bit low&#8253;
I got 9 for ephy the 2nd time, then 5 for the 3rd. I don't think this is a reliable test.

---

### Post by maddog39 on 2007-01-06
Hey all,

Well recently I decided to take a look at epiphany (the GNOME web browser) and so I took a quick look at the development versions and decided to go with 2.17.4 which is surprising very stable and I am very impressed with it so far. There arent really any bugs yet, the only thing I found is that it identified itself as epiphany 2.16, but other than that not a single problem. The new 2.17.x series also get rid of previous 2.16 annoyances like when you opened a new tab you'd have to manually click into the text box and stuff. Yea, 2.17.4 fixes all that.

So has anyone else tried it yet and or is impressed/likes it?

-maddog39

---

### Post by aysiu on 2007-01-06
I haven't found anything impressive about Epiphany except its [integration with Gnome.](http://ubuntuforums.org/showthread.php?t=93219)

For speed, there's Opera.
For customizability, there's Firefox.
For being lightweight, there's Dillo.
For being extremely lightweight, there's Lynx.

I've played around with Epiphany and have found it's nothing special. Flame away, Gnome-integration-lovers.

---

### Post by olejorgen on 2007-01-06
I found it way too limited... I guess there is plugins but I'm too lazy considering opera exsist :P The python plugin was kinda cool though

---

### Post by dbbolton on 2007-01-06
i think im going to check out dillo

---

### Post by Wolki on 2007-01-06
I do. It's my browser of choice.

Besides the GNOME integration it has some nice features like the super URL bar (offers you history, smart searches and bookmark lookup in one) and mousewheeling over the tab bar to switch tabs.

---

### Post by fuscia on 2007-01-06
as an 'intergrated' browser, i think konqueror is a much better browser. i tried epiphany for about a month and got sick of the way the bookmarks are handled.

---

### Post by Quillz on 2007-01-06
So it's similar to Internet Explorer in the sense that it's integrated into GNOME?

Also, do Firefox extensions work with it?

---

### Post by Rodneyck on 2007-01-06
I love epiphany for many of the reasons sited above. I had crashes in Firefox 2.0 and find epiphany to be very stable....and it's a Gnome browser!!!  :p

---

### Post by banjobacon on 2007-01-07
I used it on Dapper, but I'm using Firefox on Edgy. There are a few annoying bugs in the Edgy version of Epiphany that made it not worth the trouble.

What I like about Epiphany:
-Bookmark system: I don't know why anyone prefers traditional bookmarks. Tagging makes much more sense, as websites often fall into multiple categories (eg. I'd tag ubuntuforums.org as "linux", "forum", and "ubuntu". Slashdot would get tagged as "technology" and "news".). I don't use bookmarks that heavily, though, so I don't know how Epiphany handles a greater amount of bookmarks.

-Address bar: Not only does it display items in your history, it also displays bookmarks and smart bookmarks for searching. After using Epiphany, Firefox's separation of the address bar and search bar seems a little unnecessary. 

-Speed: Epiphany is generally faster than Firefox. It's probably not as fast as Opera, but it's noticeably faster than Firefox, and that difference is appreciated.

Epiphany's popularity would probably be boosted by increasing the number of extensions  (that's right people, Epiphany has extensions, too) and creating a simple way to install them (like Firefox, perhaps).

---

### Post by coder_ on 2007-01-07
Firefox has too many plugins that I need.  And if I remember correctly, Epiph. uses tagged bookmarking.  Give me [del.icio.us]("del.icio.us") for tagged bookmarking anyday.  So I can share.  And access bookmarks from any computer.

---

### Post by Johnsie on 2007-01-07
I would use epiphany if it was compatible with firefox plugins... I couldn't live without stumbleupon, unplug or aardvark.

---

### Post by RAV TUX on 2007-01-10
> **bruce89 said:**
> I got :
ephy - 3.7230000495910645
firefox - 7.53600001335144.
Seems a bit low&#8253;
I got 9 for ephy the 2nd time, then 5 for the 3rd. I don't think this is a reliable test.
I agree I think this test is completely unreliable.

---

### Post by maddog39 on 2007-01-10
Johnsie/All: Well, according to the Linux Format article comparing browsers, it said that epiphany has some sort of indirect compatibility with firefox plugins but since Epiphany uses GTK as it's interface and Firefox uses XUL (i believe), therefore rendering most plugins completely broken/incompatible, but worth a try I suppose.

Fuscia: Konqueror however, was built on and meant for intergration with KDE and last I used it in GNOME, it didnt really intergrate well at all with it. Which I do believe is part of the goal for epiphany.

As far as other things I like about eipiphany is that, yeah I have also experienced a noticable difference in speed between epiphany and firefox. I also really like the so called, *super URL bar*. :P Although, normally I'm not the sort of guy that cares that much about ease of use (unless of course it happens to be pretty bad in a particular program) but epiphany brings its level of ease of use to a point where it really saves me time when I'm doing work and stuff via the internet, as I'm a web developer and I have like 15 tabs open and stuff. I also think that firefox tends to be bloated, and I did some tests and found that with 10 tabs open on heavily graphics intensive, epiphany uses ~15MB less ram than firefox.

---

### Post by RAV TUX on 2007-01-10
another merge....please use "Advanced Search"

---

### Post by Koori23 on 2007-01-10
> **RAV TUX said:**
> Firefox has worked fine for me too. I am not knocking other browsers but was looking for a more technical reason why consistently Epiphany is faster on Ubuntu Dapper beta.

I'll be more specific.. Firefox 1.5.0.9 is more reliable than anything I've ever used.  2.0 needs a bit of work.

---

### Post by RAV TUX on 2007-01-10
> **Koori23 said:**
> I'll be more specific.. Firefox 1.5.0.9 is more reliable than anything I've ever used.  2.0 needs a bit of work.this thread was created:  			May 21st, 2006

---

### Post by fuscia on 2007-01-10
> **maddog39 said:**
> Fuscia: Konqueror however, was built on and meant for intergration with KDE and last I used it in GNOME, it didnt really intergrate well at all with it. Which I do believe is part of the goal for epiphany

what i meant was that, as intergrated browsers go (konqueror with kde and epiphany with gnome), konqueror is better.

---

### Post by maddog39 on 2007-01-11
Hmm... I supposed you could say that. I think that I really use epiphany because its the best all around browser that works with my platform, since I'm on PowerPC. There's no Swiftfox or anything like that for PPC.

Although, you guys might want to take a look at this little benchmark test I found comparing linux browsers. But it is a bit outdated and therefore modern test results could probably contridict this easily. Seeing as they are using Epiphany 1.0.7 and Konqueror 3.2, etc.

[http://www.howtocreate.co.uk/browserSpeed.html](http://www.howtocreate.co.uk/browserSpeed.html)

---

