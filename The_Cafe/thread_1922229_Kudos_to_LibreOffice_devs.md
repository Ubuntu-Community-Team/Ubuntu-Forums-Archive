---
title: "Kudos to LibreOffice devs"
date: 2012-02-08
forum: The Cafe
---

### Post by kurt18947 on 2012-02-08
I've kept 3 .docx files that would not open in LibreOffice.  I've kept them as a sort of "state of LibreOffice" test.  They all had embedded graphics files which I assumed to be the problem though I'm not certain .  LO 3.5 b2 is current in 12.04 and opens all 3 files correctly!!  I'm sure it's not a small task to be able to decypher Microsoft's "open" (yeah right) file formats.

---

### Post by JDShu on 2012-02-08
Since the split, development on LibreOffice has been extremely fast and constant. It's amazing to watch.

[http://www.ohloh.net/p/libreoffice/analyses/latest](http://www.ohloh.net/p/libreoffice/analyses/latest)

Makes me want to send a couple of patches to help out as well. They did an extremely good job of creating a community.

---

### Post by neu5eeCh on 2012-02-08
For my own purposes, I don't see any difference between this version of Libre Office and OOo.whatever.  For example: It still takes me less mouse clicks to boot up an entirely separate operating system in virtualbox, boot up an instance of WordPerfect within that virtual operating system, and then press the "vertically center text" button, than to do the same thing in an *already running* instance of Libre Office. I hate to sound ungrateful but I really wish they would remedy this glaring limitation. Any text vertically centered in MS Office or any other MS Office compatible word processor, doesn't translate into Libre Office. It is such a glaring and basic limitation that Libre Office can't really be called MS Office compatible in my view.

---

### Post by forrestcupp on 2012-02-08
> **kurt18947 said:**
> I've kept 3 .docx files that would not open in LibreOffice.  I've kept them as a sort of "state of LibreOffice" test.  They all had embedded graphics files which I assumed to be the problem though I'm not certain .  LO 3.5 b2 is current in 12.04 and opens all 3 files correctly!!  I'm sure it's not a small task to be able to decypher Microsoft's "open" (yeah right) file formats.

My experience is that it does great at opening docx files, but it _royally sucks_ at saving them, even with very simple things. Here is an easy example. Create a new LibreOffice Writer file. In this file, create two or three bullet points that could say anything, like this:
[LIST]
[*]one
[*]two
[*]three
[/LIST]Now save it as a docx file, close it, open the file back up, and take a look at how it turns out.

It does great at opening docx files created in Word, but it can't even save something as simple as that correctly.

---

### Post by sffvba[e0rt on 2012-02-08
> **forrestcupp said:**
> My experience is that it does great at opening docx files, but it _royally sucks_ at saving them, even with very simple things. Here is an easy example. Create a new LibreOffice Writer file. In this file, create two or three bullet points that could say anything, like this:
[LIST]
[*]one
[*]two
[*]three
[/LIST]Now save it as a docx file, close it, open the file back up, and take a look at how it turns out.

**It does great at opening docx files created in Word, but it can't even save something as simple as that correctly.**

I am sure that if it was a simple matter it would do so correctly.



404

---

### Post by forrestcupp on 2012-02-08
> **not found said:**
> I am sure that if it was a simple matter it would do so correctly.



404

I didn't necessarily mean it is a simple matter, but a simple feature. There are things about Word that are a heck of a lot more complex than that.

---

### Post by kurt18947 on 2012-02-08
> **forrestcupp said:**
> My experience is that it does great at opening docx files, but it _royally sucks_ at saving them, even with very simple things. Here is an easy example. Create a new LibreOffice Writer file. In this file, create two or three bullet points that could say anything, like this:
[LIST]
[*]one
[*]two
[*]three
[/LIST]
Now save it as a docx file, close it, open the file back up, and take a look at how it turns out.

It does great at opening docx files created in Word, but it can't even save something as simple as that correctly.

I don't have Word but I guess I could download a free Word file viewer.  I'll have to try that.  My problem .docx files either wouldn't do anything or would crash Libre Office on startup so that's a step in the right direction.

Edit:  I had time so created a simple docx  [ATTACH]212339[/ATTACH]   file and installed the file reader from Microsoft so I could open .docx files.  It did quite well.  Formatting seemed to transfer correctly.  The only weirdness was the bullets in LO appeared as small copiers (or something) in MS' viewer.  I then reinserted the flash drive in the creating machine and opened the .docx file.  It opened correctly.  I'll attach my test file, it's pretty small.  The weirdness referenced was when switching from indented text to left justified.  

I had to create an archive file because the forum software won't upload a .docx file. There are two files.  They're identical content, one is saved as a .docx file, the other is .odt.  There are no nasties that I know of in them.  The file sizes are interesting, docx is about half the size of the odt file.  PS I didn't intend it to be in line but don't have time to redo.  Hope this is okay.

---

### Post by JDShu on 2012-02-08
> **kurt18947 said:**
> I don't have Word but I guess I could download a free Word file viewer.  I'll have to try that.  My problem .docx files either wouldn't do anything or would crash Libre Office on startup so that's a step in the right direction.

You don't need to use MS Word to see this issue, and in fact, from what I saw on the bug tracker regarding this bug, you don't see it in Word.  Just use LibreOffice to save the file, close LibreOffice, and then use LibreOffice to open the file you saved.

---

### Post by kurt18947 on 2012-02-08
> **JDShu said:**
> You don't need to use MS Word to see this issue, and in fact, from what I saw on the bug tracker regarding this bug, you don't see it in Word.  Just use LibreOffice to save the file, close LibreOffice, and then use LibreOffice to open the file you saved.

Did that, it seemed to work.  I'll do more with this later.

Edit:  Well, I broke it :P.  I opened one of my 'problem' .docx files that displayed properly and made changes ... changed top & bottom margin, deleted a graphic, reformatted some paragraphs then saved as an .odt file.  Closed everything, restarted LO, opened the .odt file and saved as a .docx file.  When I reopened in LO, the header on each page was gone and a couple graphics had moved from page 3 to the title page.  The body text changes seemed to translate correctly.  It appears that editing or moving graphics embedded within a .docx file  cause major problems.  Fairly simple text documents seem to survive pretty much intact.

---

### Post by forrestcupp on 2012-02-08
> **JDShu said:**
> You don't need to use MS Word to see this issue, and in fact, from what I saw on the bug tracker regarding this bug, you don't see it in Word.  Just use LibreOffice to save the file, close LibreOffice, and then use LibreOffice to open the file you saved.

Yeah, that's what I was talking about. Saving as a Word 2003 doc file works fine, but if you save it as a docx and open it back up, it looks horrible. The strange thing is that you can create the exact same thing in Word and open it up in LibreOffice and it looks perfect.

---

### Post by SeanIM on 2012-02-09
Agreed, they did a great job with it!

---

### Post by cguy on 2012-02-09
PEOPLE MUST STOP USING THE DOCX FORMAT!

/rant

---

### Post by forrestcupp on 2012-02-09
> **cguy said:**
> PEOPLE MUST STOP USING THE DOCX FORMAT!

/rant

Most of the world uses MS Word, which defaults to docx. Why should they change that just to cater to a microscopic minority who uses LibreOffice? Most people don't give a rat's backside about the philosophy of open formats.

But since I'm now using LibreOffice in Linux, I *will* start using the old doc format because it works better. No way I'm using odt. It would be silly to try to force everyone else who uses Word to have to download a plugin just to open my files because I refuse to save them in a format they can automatically open.

/rant on rant   :D

---

### Post by smellyman on 2012-02-09
> **cguy said:**
> PEOPLE MUST STOP USING THE DOCX FORMAT!

/rant

true.  MSO versions to MSO versions have trouble opening them up.  Often LO does a better job opening them than MSO.  Also the amount of corruption that happens with MSO especially with file sharing is terrible.  Yet the world plugs away using MSO because they "have to". 

Too bad it seems LO gets a bad rap for MS terrible docx format......it will be nice if someday MS has to bend and use more open formats.

---

### Post by KiwiNZ on 2012-02-09
I have stopped using Libre Office/ Open Office, it just does not cut it.

---

### Post by kurt18947 on 2012-02-10
> **forrestcupp said:**
> Most of the world uses MS Word, which defaults to docx. Why should they change that just to cater to a microscopic minority who uses LibreOffice? Most people don't give a rat's backside about the philosophy of open formats.

But since I'm now using LibreOffice in Linux, I *will* start using the old doc format because it works better. No way I'm using odt. It would be silly to try to force everyone else who uses Word to have to download a plugin just to open my files because I refuse to save them in a format they can automatically open.

/rant on rant   :D

 Not having MS Office or Word, I don't know how this works.  Let's say I send someone a .doc file.  They open it and change something then save and close.  Is the default behavior to save in the original format (.doc) or save as the latest & greatest flavor of .docx?

---

### Post by Grenage on 2012-02-10
> **kurt18947 said:**
> I've kept 3 .docx files that would not open in LibreOffice.  I've kept them as a sort of "state of LibreOffice" test.  They all had embedded graphics files which I assumed to be the problem though I'm not certain .  LO 3.5 b2 is current in 12.04 and opens all 3 files correctly!!  I'm sure it's not a small task to be able to decypher Microsoft's "open" (yeah right) file formats.

LibreOffice is a good suite, but I never had any problems with OpenOffice. If you view any of these suites as MS-compatible replacements, you'll probably be disappointed in several ways, but as stand-alone products, they are excellent.

I use it at work and at home, because like 99% of the global user base, I rarely need to do anything more advanced than change the font; Google Docs also does me fine.

Most of our office staff have MS office, but only because our main software package ties into it for merging, etc.  We would certainly have swapped them over otherwise.

---

### Post by earthpigg on 2012-02-10
> **forrestcupp said:**
> Most of the world uses MS Word, which defaults to docx. Why should they change that just to cater to a microscopic minority who uses LibreOffice? Most people don't give a rat's backside about the philosophy of open formats.

But since I'm now using LibreOffice in Linux, I *will* start using the old doc format because it works better. No way I'm using odt. It would be silly to try to force everyone else who uses Word to have to download a plugin just to open my files because I refuse to save them in a format they can automatically open.

/rant on rant   :D

Work internally in .odt, e-mail finished products in .pdf, and work collaboratively in google docs or edit.this (or any other wiki)?

What I've been doing for some time now.

Since when was a not-worthless work defined by how cute the bullets are?

---

### Post by EthioJOB on 2012-02-10
If we're going to talk about LO in general, let me include another issue in addition to file formats. The one problem I had most with regards to OOo is the loss of the document I was working on during power cuts. Auto-recovery is a joke. Though I'm not using LO right now (Ubuntu 10.10), I wish the devs take this into consideration. I understand MSO may not be free of this problem either but it performs better in this area.

---

### Post by forrestcupp on 2012-02-10
> **kurt18947 said:**
> Not having MS Office or Word, I don't know how this works.  Let's say I send someone a .doc file.  They open it and change something then save and close.  Is the default behavior to save in the original format (.doc) or save as the latest & greatest flavor of .docx?

It is set up by default to warn you that if you save it as a doc, you could lose some of your new incompatible formatting, and it offers to save it as a docx. You can choose not to do that, and it saves it as a doc. I'm sure there is a way to disable that warning, but that's what it does by default.

---

### Post by forrestcupp on 2012-02-10
> **KiwiNZ said:**
> I have stopped using Libre Office/ Open Office, it just does not cut it.

I just now installed MS Office 2007 with Wine, and it works perfectly. I'm pretty amazed at how well it works. Even though it's being run with Wine, it still opens in a fraction of the time that it takes to open LibreOffice natively.

MS Office is expensive, and LibreOffice is great if you don't have the cash. But if you have a paid for copy of MS Office lying around, there's absolutely no reason to not use it.

---

### Post by drawkcab on 2012-02-12
> **forrestcupp said:**
> MS Office is expensive, and LibreOffice is great if you don't have the cash. But if you have a paid for copy of MS Office lying around, there's absolutely no reason to not use it.

I agree.  I keep MS Office around because it's hard to beat Power Point.

---

### Post by forrestcupp on 2012-02-12
> **drawkcab said:**
> I agree.  I keep MS Office around because it's hard to beat Power Point.

Yeah. And from my week of using LibreOffice Writer (and I use wordprocessors quite a bit), going back to Word is showing me how dreadful LibreOffice's docx *and* doc support is. You can't really blame them, since they had to reverse engineer it all. But it seems like doc compatibility was better in OOo a few years ago than it is now in LibreOffice.

---

### Post by neu5eeCh on 2012-02-12
I much prefer WordPerfect, and it baffles me that Corel can't even get off their duff enough to help get it working under wine. I guess they make so much money and are so successful with WP that they don't need to compete.

---

### Post by kurt18947 on 2012-02-13
> **VTPoet said:**
> I much prefer WordPerfect, and it baffles me that Corel can't even get off their duff enough to help get it working under wine. I guess they make so much money and are so successful with WP that they don't need to compete.

If memory serves (it may not), Derek Burney Jr. killed any Corel Linux efforts as well as firing or causing to quit a bunch of senior developers and the entire government sales staff.  Corel was in serious financial straits at the time.  Remember that Microsoft injected a bunch of money to keep Corel afloat?   Burney Jr. is currently corporate vice president for Microsoft Office Data & Business Intelligence according to Wikipedia.

---

### Post by smellyman on 2012-02-13
[Powerpoint ]("http://www.youtube.com/watch?v=LoGmUeSXp5M")is boring.  :)

---

### Post by Andrew_P on 2012-02-13
All I can say is that LibreOffice 3 needs work before it's "ready for prime time".  I installed LibreOffice 3.4.5 on Ubuntu 10.04 a few days ago and it trashed the Ubuntu Software Center on my system, *among other things*.  Instead of a monolithic .deb installer, it requires stroking it in with terminal commands. ](*,)

---

### Post by Andrew_P on 2012-02-13
> **forrestcupp said:**
> Yeah. And from my week of using LibreOffice Writer (and I use wordprocessors quite a bit), going back to Word is showing me how dreadful LibreOffice's docx *and* doc support is. You can't really blame them, since they had to reverse engineer it all. But it seems like doc compatibility was better in OOo a few years ago than it is now in LibreOffice.

I also find the use of "regular expressions" to find and replace text in OpenOffice.org and LibreOffice inscrutable.  It's an absolute mess compared to the way Microsoft Word does it or the way WordStar in DOS did it.  It turns out that "regular expressions" aren't regular and aren't standard; different 'nix programs use different conventions.  Having to have a two-page cheat sheet at my side to be able to construct a regular expression to search-and-replace text in a document is *not* an efficient or rational way to work.  As a consequence, I do most of my serious document editing on a couple of aging Windows systems equipped with Microsoft Office, and for general editing on Ubuntu I use gedit.  In fact, the LibreOffice folks would do well to copy the way gedit performs find-and-replace; the "\" escape sequences to represent special characters aren't all that different than the caret ("^") escape sequences used in Microsoft Word and are easy to memorize.

---

### Post by forrestcupp on 2012-02-13
> **VTPoet said:**
> I much prefer WordPerfect, and it baffles me that Corel can't even get off their duff enough to help get it working under wine. I guess they make so much money and are so successful with WP that they don't need to compete.It's pretty sad that it can't even work with Wine when they used to distribute free of charge native Linux versions.

> **Andrew_P said:**
> As a consequence, I do most of my serious document editing on a couple of aging Windows systems equipped with Microsoft Office, and for general editing on Ubuntu I use gedit.
It's pretty easy to get all versions of MS Office to work with Wine. I'm running 2007 in Wine and it works just as well as if I were using Windows.

---

### Post by kurt18947 on 2012-02-13
> **forrestcupp said:**
> It's pretty sad that it can't even work with Wine when they used to distribute free of charge native Linux versions.

[COLOR=Blue]Perhaps not if you get rid of all the people that worked on it.[/COLOR]  [COLOR=Blue]Plus it isn't like Corel is rolling in excess $$ to fund projects that may not -- probably won't -- generate significant $$.  Plus I would not be surprised if there's an 'understanding' with Microsoft that Corel will not do anything further with Linux.[/COLOR]  [COLOR=Blue]If Corel, just like Adobe and Symantic and every other software house relies on Microsoft's cooperation to get your products to work on their operating system, would you do *anything* to antagonize them?[/COLOR]


It's pretty easy to get all versions of MS Office to work with Wine. I'm running 2007 in Wine and it works just as well as if I were using Windows.

[COLOR=Blue]That's good to know if I need better file compatibility.  Right now I don't do anything collaborative.  My needs are pretty basic.[/COLOR]

---

### Post by JDShu on 2012-02-13
I don't think anybody is arguing that LibreOffice is ready for mass deployment, for various reasons. The product as is, is not as good as MS Office, and arguably not as good as iWork. That said, for most people it does what you need fine. I have used Impress for teaching classes and Writer for all my homework - the formula function for example is great as I have yet to spend time properly learning TeX.

More interestingly to me, the whole LibreOffice movement is showing the power of the open source development process. They blogged a nice [infographic]("http://tdfsc.files.wordpress.com/2012/02/tdf-infographics2.jpg") recently that shows recent contributions and you can see the ohlol link I posted earlier. Some people thought that the fork would destroy progress of opensource office suites, but I think those people have very clearly been proven wrong. The LibreOffice organization has successfully rounded up the community to make real progress. I think it'll be exciting to see where they go from here.

One thing that I am very encouraged about is that major open source software projects are modernizing their development process. Firefox is probably the best example, with their frequent regular releases. LibreOffice is also adhering to a regular release schedule. The GIMP is a good example of what happens when you keep saying "it's ready when it's ready" and they seem to have realized it too, as after 2.8 they expect to have a regular release schedule as well.

---

### Post by neu5eeCh on 2012-02-14
> **kurt18947 said:**
> [COLOR=Blue]Perhaps not if you get rid of all the people that worked on it.[/COLOR]  [COLOR=Blue]Plus  it isn't like Corel is rolling in excess $$ to fund projects that may  not -- probably won't -- generate significant $$.  Plus I would not be  surprised if there's an 'understanding' with Microsoft that Corel will  not do anything further with Linux.[/COLOR]  [COLOR=Blue]If Corel,  just like Adobe and Symantic and every other software house relies on  Microsoft's cooperation to get your products to work on their operating  system, would you do *anything* to antagonize them?[/COLOR]

I'm sure they have a rationale, but I doubt it has anything to do with offending MS. One can't, on the one hand, say that there's no money in a Linux version, and then worry about offending MS because you're entering market where there's no money and no market share.

If I were Corel, I would assign one dev to work with something like Bordeaux Linux or Crossover to get WordPerfect working. It almost works as is. Just a tiny little kick and it would be gold or platinum. If they wanted to charge $10, or even $25 for a Linux version, I would buy it. I've already bought a copy of Textmaker.

---

### Post by Andrew_P on 2012-02-16
One thing that I loved about OpenOffice.org and now love about LibreOffice is the ease of generating PDF output.  It just works.

---

