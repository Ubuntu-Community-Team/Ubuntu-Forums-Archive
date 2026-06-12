---
title: "Cool writing program, Kabikaboo"
date: 2009-05-17
forum: The Cafe
---

### Post by jslinux on 2009-05-17
Thought I'd call attention to this nice new program being developed by one aidave

[http://sourceforge.net/projects/kabikaboo](http://sourceforge.net/projects/kabikaboo) 

Kabikaboo - Recursive Writing Assistant

In the vein of scrivener, pagefour, and ywriter.

Personally I think Ubuntu is a fine writing environment, and would love to see this program continue to be developed.

Some screenshots:

[[IMG]http://img242.imageshack.us/img242/2963/screenshotamj.th.png[/IMG]](http://img242.imageshack.us/my.php?image=screenshotamj.png)

[[IMG]http://img195.imageshack.us/img195/1992/screenshot1o.th.png[/IMG]](http://img195.imageshack.us/my.php?image=screenshot1o.png)

---

### Post by drawkcab on 2009-05-17
This appears to be based on a 9th grade understanding of literature.  I wonder if there's a "conflict" button that pulls down a menu for *man vs. man* / *man vs nature* / *etc.*

:roll:

---

### Post by jslinux on 2009-05-18
That's just an example layout smart guy.

---

### Post by monsterstack on 2009-05-18
Looks quite interesting. The code isn't particularly massive, either, so maybe I can hack around with it a bit. And maybe not completely break it.

---

### Post by Warpnow on 2009-05-18
I've been looking for something like this for years.

Zim/Notecase were close. I really hope this meets my needs better.

---

### Post by Warpnow on 2009-05-18
Is there no readme on how to build this application, though? I don't know hardly anything about python, and the only downlaod I could find were the coee files in the SVN.

---

### Post by MikeTheC on 2009-05-18
It looks interesting, but when I went to check it out over at Sourceforge, there's nothing to download!

---

### Post by jslinux on 2009-05-18
(check it out using subversion)

sudo apt-get install subversion

svn co [https://kabikaboo.svn.sourceforge.net/svnroot/kabikaboo](https://kabikaboo.svn.sourceforge.net/svnroot/kabikaboo) kabikaboo 

(then browse to the code subfolder)
cd kabikaboo/code
python kabikaboo.py

---

### Post by MikeTheC on 2009-05-18
Oh, this thing is just source-code for the moment?

Never mind, then.

---

### Post by monsterstack on 2009-05-18
> **MikeTheC said:**
> Oh, this thing is just source-code for the moment?

Never mind, then.

You can choose "browse svn" from sourceforge, and download a tarball and extract it. There's nothing to compile: it's just a bunch of Python scripts. Extract them and find the py files, then run

```
python kabikaboo.py
```

---

### Post by tadcan on 2009-05-18
Storybook is more polished and easier to install. 

[http://storybook.intertec.ch/joomla/](http://storybook.intertec.ch/joomla/)

---

### Post by jslinux on 2009-05-18
Storybook has a different layout philosophy.

Personally, I think it looks like an office application. 

I think most people are looking for a program that comes close to scrivener and fits well in a gnome environment. This is a step in the right direction.

---

### Post by joey-elijah on 2009-05-18
Has everyone forgotten Celtx?

---

### Post by Warpnow on 2009-05-18
> **joey-elijah said:**
> Has everyone forgotten Celtx?

Its a massively huge program for the simple task of writing.

---

### Post by monsterstack on 2009-05-18
If somebody gives Kabikaboo a linking feature, I think I'd use it quite a lot. Zim is okay, but it doesn't have that cool hierachy-type structure.

---

### Post by jslinux on 2009-05-18
Yeah, I think the author just needs a little encouragement. He's having some difficulty moving the program to launchpad, a subject about which I know nothing. 

Linking would be nice. Rich text for italics. Full screen mode. Being able to drag nodes around would be helpful.  

Eventually, a storyboard, for people who use that sort of thing. Yada yada.
Pdf/jpeg support in program. Perhaps it wouldn't be terribly hard to borrow code from evince and eye of gnome, with some c programming.

But the program already looks really nice, is not clunky at all, and seems to have gnome HIG in mind. I like the "children" metaphor too.

---

### Post by Chilli Bob on 2009-05-19
This program is FREAKING PERFECT for what I need.  I have been trying to do this with Geany and Notecase, both of which can almost sorta do what I want, but this is perfect.  (Assuming it can handle LARGE files).

Will also try storybook, but it looks a bit of overkill really.

---

### Post by aidave on 2009-06-04
> **jslinux said:**
> Thought I'd call attention to this nice new program being developed by one aidave

[http://sourceforge.net/projects/kabikaboo](http://sourceforge.net/projects/kabikaboo) 

Kabikaboo - Recursive Writing Assistant

In the vein of scrivener, pagefour, and ywriter.

Personally I think Ubuntu is a fine writing environment, and would love to see this program continue to be developed.


:grin:

:)!  Wow it makes me happy someone has found this and sees the value in it.  I am still developing it, albeit as a hobby, but the more important thing is I use it every time I write my sci-fi novel!  Even when I'm not writing my novel, I use it to jot down random ideas that pop into my head, or to paste in tidbits of research.

It's true its very basic and doesn't have many text-editing features.  I'd like to fix that.  One high-priority feature to add next is undo/redo.  I dont want to go too hogwild on the advanced text-editing, it would consume all my time.  GtkSourceView component looks worth checking out to see if it does all the dirty work.

The latest feature I just added this week (v1.1) is a tabbed notebook.  It will remember the latest 5 nodes you clicked on.  I find this very helpful because I am constantly jumping between a few nodes, but got annoyed because the tree list was too long between them.  I hate scrolling, especially on a laptop!  

So you may want to update from the repo (Sourceforge or now Launchpad).  Make sure to backup any document you made, just in case, because it brings along a new doc format to remember your tabs (it autoconverts to 1.1 for you).  I should probably add some preference settings for it, and make Ctrl-Tab keys do switching.  If you have any suggestions please let me know.

Finally, I wish to see Kabikaboo available in the Debian/Ubuntu repositories.  I'm trying to learn how to make a .deb package.  It's not easy for me... if anyone can help, I'm willing to learn.

Thanks for the compliments, and I hope Kabikaboo helps you! :)

cheers
aidave 8-)

---

### Post by aidave on 2009-06-04
> **Chilli Bob said:**
> This program is FREAKING PERFECT for what I need.  I have been trying to do this with Geany and Notecase, both of which can almost sorta do what I want, but this is perfect.  (Assuming it can handle LARGE files).

Will also try storybook, but it looks a bit of overkill really.

Thanks Chilli Bob. 

I think it can handle large files.  The file I use is quite large with a few hundred nodes.

Might I suggest you dump a huge text block into one node, save and load that?  If that works, it stands to reason that it should handle what you need.

---

### Post by aidave on 2009-06-04
> **drawkcab said:**
> This appears to be based on a 9th grade understanding of literature.  I wonder if there's a "conflict" button that pulls down a menu for *man vs. man* / *man vs nature* / *etc.*

:roll:

:-\"

Basically when you load up Kabikaboo, it gives you a sample layout.
It is meant to show you the capabilities of the program, nothing more.
From there you create a new blank slate to work from.

Anyone is welcome to create a more advanced sample layout.

The whole point of Kabikaboo is freedom to make whatever layout you want.  When you create a new document, you have one root node.  From there you add nodes and create any hierarchy you like.  So it in theory could be used for other purposes beyond writing a novel.

When you have an idea about one of your characters, like a quote they say, but it happens to him far in the future, you can go to your Kabikaboo document, and type in a note about it.  Instead of one massive document where you'd have to search for the characters section, find the character, then find his quotes subsection, etc, now its a little easier to find and retrieve that info!

You might find if your novel, or series of novels, is quite complex, Kabikaboo could be a good aid.  I personally can't remember everything I think of, and my previous strategy of keeping all notes in one big file was getting very frustrating.  Kabikaboo solves that problem.

Even though a big note file is annoying, it would be just as annoying to click on each node and see the text inside.  That's why there is a "View" style node in addition to "Edit".  This style of node lets you recursively see the text of all children and/or grandchildren.  So you can see all the stuff on all your characters by clicking the "Characters" node, or all the subnotes on one character by clicking on that node, etc.

Hope that makes sense.

Please please please DON'T use Kabikaboo to write your novel.  You could if you really wanted to, but you're in for pain.  It's meant to be a note-taker to help plan your novel.  I write my book in AbiWord in another window.

---

### Post by aidave on 2009-06-05
Another update: Have working GtkSourceView with undo/redo in the SourceForge repository!  

May need to install package python-gtksourceview2 before running.

---

### Post by azangru on 2009-06-05
For anyone trying to create a cool writing program: try to copy Scrivener. It seems to be well-suited not just for fiction or screenplays (where you need to keep track of characters), but for any large writing projects as well. It helps organize the material (bpth written and graphical), ***and*** provides a non-distracting full-screen writing environment, ***and*** exports all the writing into a universally recognized format (like rtf). It looks like the developers of Scrivener got it exactly right :)

---

### Post by aidave on 2009-06-07
> **azangru said:**
> For anyone trying to create a cool writing program: try to copy Scrivener. It seems to be well-suited not just for fiction or screenplays (where you need to keep track of characters), but for any large writing projects as well. It helps organize the material (bpth written and graphical), ***and*** provides a non-distracting full-screen writing environment, ***and*** exports all the writing into a universally recognized format (like rtf). It looks like the developers of Scrivener got it exactly right :)

I wanted to create something that is not a place to make a novel, but a place to plan a novel.  As far as I am concerned the tools already exist to write a novel (AbiWord, OpenOffice, LyX, Kile, etc)

I have no time to add all those features, and to top it off, recreate AbiWord or a fancy editor.  A time-line would be nice, I am pondering adding that, it would be a 2.0 feature.  It could link to nodes.  I just wonder how to add it without cluttering the interface up, and for it to be a generic feature, not specific to a novel.

As for Scrivener, if you want it, it's already made, go buy it.  ;)  
If you tried to recreate Scrivener you probably wouldn't have time to write a novel.  hehe.  But if someone copies it, great for the community!

I am happy with using AbiWord/LyX+Kabikaboo!

Now if I could only figure out the Debian packaging.....

---

### Post by azangru on 2009-06-07
> **aidave said:**
> As for Scrivener, if you want it, it's already made, go buy it.  ;) 

And a Mac to go along with it? ;)

> **aidave said:**
> If you tried to recreate Scrivener you probably wouldn't have time to write a novel.  hehe.  But if someone copies it, great for the community!

Yep, that's what I'm talking about :)

---

### Post by aidave on 2009-06-09
Debian Installer packages are out:
[https://launchpad.net/kabikaboo/+download](https://launchpad.net/kabikaboo/+download)

I have tested them but I dont know 100% that they will install correctly.  Please post feedback if you try it out.  Thanks!

---

### Post by aidave on 2009-08-19
Update: New version of Kabikaboo, 1.2 is now out!

:popcorn:

---

### Post by mehaga on 2009-08-19
Hi,

installed, but can't run it:

ImportError: No module named gtksourceview

libGtkSourceview and py bindings are installed. Ubuntu 9.04 64.

---

### Post by mehaga on 2009-08-19
lol looks like i fixed it.

import gtksourceview**2**

edit: ok, maybe not. i only see the tree on the left side :/

---

### Post by aidave on 2009-08-23
> **vekaz said:**
> Hi,

installed, but can't run it:

ImportError: No module named gtksourceview

libGtkSourceview and py bindings are installed. Ubuntu 9.04 64.


Try to install package: "python-gtksourceview2"

It is supposed to automatically install if you use the Debian package.

---

### Post by aidave on 2009-09-02
Version 1.4 is out!

---

### Post by aidave on 2009-09-30
Version 1.5 now out, with:
- Bookmarks
- and more
[https://launchpad.net/kabikaboo/+announcement/3872](https://launchpad.net/kabikaboo/+announcement/3872)

:KS

---

### Post by LMelior on 2009-10-18
I just found this program and it's perfect for my NaNoWriMo planning.  I tried StorYBook and yWriter but they are overwhelming for a non-writer like me.  Those programs expect you to know a great deal about your book beforehand, but I'd just like to build as I go along and fill in the detail later.  Most of the time I just want to create a scene, I don't want to put it in the timeline, or decide who is in it, or where it is, or any of that stuff!  Those things made me feel like I had to know everything about the characters and settings right off the bat.

So anyway, thanks a bunch for making this.  I had it installed, up and running in no time.  It's very intuitive, unlike the other software I've tried.  Keep up the good work!

---

### Post by JDShu on 2009-10-18
> **LMelior said:**
> I just found this program and it's perfect for my NaNoWriMo planning.  I tried StorYBook and yWriter but they are overwhelming for a non-writer like me.  Those programs expect you to know a great deal about your book beforehand, but I'd just like to build as I go along and fill in the detail later.  Most of the time I just want to create a scene, I don't want to put it in the timeline, or decide who is in it, or where it is, or any of that stuff!  Those things made me feel like I had to know everything about the characters and settings right off the bat.

So anyway, thanks a bunch for making this.  I had it installed, up and running in no time.  It's very intuitive, unlike the other software I've tried.  Keep up the good work!

Same here, I learned of NaNo from another thread in this forum, and this tool seems perfect!

---

### Post by koleoptero on 2009-10-18
How did I miss this thread? :-k

Thank you, I was looking for a program that does exactly this. Keep up the good work. :)

---

### Post by RPG Master on 2009-10-18
I am so glad I found this thread! Kabikaboo is really going to help me with writing my first NaNoWriMo :D

I am doing it with my homeschool group, I'll have to recommend Kabikaboo to my two Linux using friends :)

---

### Post by Warpnow on 2009-10-18
I'm using it for nanowrimo, too. Too bad it doesn't have word count, though.

---

### Post by LMelior on 2009-10-20
Glad some new people found this program. :)

You can always export to .rtf and use Abiword or OpenOffice.org to do your word count.  Personally I'm just using it for planning though, as the developer suggests.

---

### Post by aidave on 2009-10-30
Thanks for the nice replies!  Glad others are making good use of this.

Kabikaboo 1.6 is out and has document statistics, among other nice new features.  

[https://launchpad.net/kabikaboo/kabikaboo1.6/kabikaboo1.6](https://launchpad.net/kabikaboo/kabikaboo1.6/kabikaboo1.6)

The stats include word count, new words, words per minute, etc.  A user doing NanoWrimo requested this feature, so I added it just in time for Nov 1.  However, I wont be using that since I only use Kabikaboo for planning my novel and Abiword for writing it.

Will also be adding a darkroom feature for the next release 1.7. (edit: didnt get around to it)
If you have any ideas for it please share/contribute!

---

### Post by aidave on 2009-12-22
Kabikaboo 1.7 is now out, with a new repository as well!

[https://launchpad.net/kabikaboo/trunk/1.7](https://launchpad.net/kabikaboo/trunk/1.7)

Big thanks to Jeremy Bicha who basically retooled the entire application to be more GNOME-compliant, and got Launchpad working right.

New features:
- Spellcheck
- Visits
- More saving features
- etc

---

### Post by Oreo_King on 2010-03-17
Wow, this is a pretty awesome program.  Looks like the perfect application to organize my novel.  Haha, and I found it randomly looking through the forums for an alternative to Scrivener (haven't tried it but the idea seems nice).  Though it doesn't have the option to import images and video, that's easily remedied by putting that stuff in folders on your hard drive. :p

Kudos to aidave. :)

I can't wait for further releases. (well I can but everyone says that, hehe)

---

### Post by Oreo_King on 2010-03-27
After using it for a while there's an idea that would make it easier to use a bit.  Is it possible to add the ability to drag and drop the sections?

I realized at one point that I needed to move a section into a subsection and couldn't figure it out after a while. I know you can move to the right and all but drag and drop would make it faster, well that's just my two cents.

Also if there was a way to increase the space between sections in the tree that'd be cool, after you start putting a lot of sections it gets a little to harder to find things.

---

### Post by HalfEmptyHero on 2010-05-09
Anyone know if this is still being worked on?

---

### Post by Oreo_King on 2010-05-27
Actually I have no idea, nothing new on Launchpad.  But we shouldn't really worry--unless it becomes a years worth of inactivity. :(

Also, aidave, is it possible to add in the ability to have multiple instances of Kabikaboo open? 

Not an important feature but I started to use the program just now (literally just now, it's been a while since I've written any fiction so it's been seldom used) to sort my to do list (I keep lists of stuff) and wanted to open up another .kaboo where I keep a list of media to consume and it replaced the current .kaboo.

Also, even less priority, making web links click-able.  That way I don't have to cut and paste.  Even less importance. :P

Thanks for creating the program, by the way, it's *very* useful.  :)

PS EDIT: Actually it turns out Kabikaboo can already have multiple instances open, never mind. :P

---

### Post by aidave on 2010-06-17
Hello.  Yes, Kabikaboo already supports multiple instances (so you can work on two or more documents), the caveat is you have to open each instance from the Application menu (or other).  It doesnt currently open a new window from itself, but i suppose that could be added.

Kabikaboo is kind of in hiatus, the only activity in the last while has been a bug fix.  We should really release a 1.7.1 patch.  I've recently moved and been busy doing family stuff.  I also lost my home computer.  So I'd like to get back into adding more features but in the meantime I cant.  Eventually I will tho... when I begin work on my second novel I will need more features from Kabikaboo, and that'll give me the kick in the butt i need to keep going on it :)

cheers
Dave

> **Oreo_King said:**
> Actually I have no idea, nothing new on Launchpad.  But we shouldn't really worry--unless it becomes a years worth of inactivity. :(

Also, aidave, is it possible to add in the ability to have multiple instances of Kabikaboo open? 

Not an important feature but I started to use the program just now (literally just now, it's been a while since I've written any fiction so it's been seldom used) to sort my to do list (I keep lists of stuff) and wanted to open up another .kaboo where I keep a list of media to consume and it replaced the current .kaboo.

Also, even less priority, making web links click-able.  That way I don't have to cut and paste.  Even less importance. :P

Thanks for creating the program, by the way, it's *very* useful.  :)

PS EDIT: Actually it turns out Kabikaboo can already have multiple instances open, never mind. :P

---

### Post by Fourcultures on 2010-11-28
Since this project seems to be quiet I'll dare to mention that Scrivener is now, finally, available in beta for Windows which** *also works with Linux***. You can read the [forum thread]("http://www.literatureandlatte.com/forum/viewtopic.php?f=30&t=9154") for details.

The down side is it's not free software, but there's an emerging free software solution with [LyX-outline]("https://launchpad.net/lyx-outline") (this makes more sense if you read the [blog]("http://blog.oak-tree.us/index.php/science-and-technology/lyx-outline")). It's is an extension to the [LyX]("http://www.lyx.org/") document processor, which aims to clone the usability of Scrivener.

I don't think either of these projects do quite what Kabikaboo sets out to do, but aspiring writers might like to check them out.

---

