---
title: "Here the source of notepad2, could we get a package for LINUX?"
date: 2009-09-12
forum: The Cafe
---

### Post by frenchn00b on 2009-09-12
Notepad2, very famous if you like coding:

[http://www.flos-freeware.ch/notepad2.html](http://www.flos-freeware.ch/notepad2.html)

---

### Post by muep on 2009-09-12
> **frenchn00b said:**
> Notepad2, very famous if you like coding:

[http://www.flos-freeware.ch/notepad2.html](http://www.flos-freeware.ch/notepad2.html)

It's been coded in C, but using the Windows interfaces. Wine includes an implementation of these and the application seems to run just fine in a Wine environment, but it'd require very intrusive modifications to the program to make it look like an usual Ubuntu program.

The application could probably be packaged inside a .deb, but it's not done very often for Windows-based software.

---

### Post by huwnet on 2009-09-12
Which features do you need in Notepad2 that aren't available in Linux text editors? :)

---

### Post by kerry_s on 2009-09-12
scite is in the repo, since thats based on it should be similar.

---

### Post by Exodist on 2009-09-12
Use GEdit. Your not going to get a better text editor then GEdit anywhere.




I cant understand why so many people want windows crap in linux. I dont think people realize that most crap in windows was cloned from or an idea already being used on a *nix based system. /sigh

---

### Post by Jim! on 2009-09-12
> **Exodist said:**
> Use GEdit. Your not going to get a better text editor then GEdit anywhere.
I also prefer Gedit.




> I cant understand why so many people want windows crap in linux. I dont think people realize that most crap in windows was cloned from or an idea already being used on a *nix based system. /sigh
To tell you the truth I think it's reasonably even. A lot of Software on Linux could be considered (And often is) just a clone of Windows software. The upcoming "ribbon" design for OpenOffice.org is a perfect example.

---

### Post by frenchn00b on 2009-09-12
> **huwnet said:**
> Which features do you need in Notepad2 that aren't available in Linux text editors? :)

we just catch the code, and make it available as a package.

Linux ever !
Wine is not a solution, 

we need linux packages, and notepad2 would be cool

---

### Post by Sublime Porte on 2009-09-12
> Use GEdit. Your not going to get a better text editor then GEdit anywhere.

No offence, but gedit has gotta be one of the most annoying aspects of gnome. Coming from KDE, kate puts gedit to shame.

Especially for Python coding, it has a really bad habit of messing up indentation which instantly introduces errors into a python program. I think it's clumsy and under-featured as a code editor, yet too bloated as a generic text editor.

Geany weighs in about the same resource-intensiveness-wise, yet has a ton more features and is a good solid code editor/IDE.

As for a generic text editor, leafpad isn't too bad, or (being biased) I use my own text viewer/editor (linked in my signature), textview.

---

### Post by Exodist on 2009-09-12
> **Sublime Porte said:**
> No offence, but gedit has gotta be one of the most annoying aspects of gnome. Coming from KDE, kate puts gedit to shame.

Especially for Python coding, it has a really bad habit of messing up indentation which instantly introduces errors into a python program. I think it's clumsy and under-featured as a code editor, yet too bloated as a generic text editor.

Geany weighs in about the same resource-intensiveness-wise, yet has a ton more features and is a good solid code editor/IDE.

As for a generic text editor, leafpad isn't too bad, or (being biased) I use my own text viewer/editor (linked in my signature), textview.

Many debate the whole Kate -vs- Gedit thing as much as KDE -vs- Gnome. Either or, they both got there good and bads. :KS

---

### Post by Sublime Porte on 2009-09-12
Well since I use Gnome at present, I don't use Kate :)

But even on Gnome, I prefer geany+leafpad or even just geany instead of gedit.

---

### Post by red_Marvin on 2009-09-12
> **Exodist said:**
> Use GEdit. Your not going to get a better text editor then GEdit anywhere.
Except that what is percieved as good is very much subjective. I used to swear by gedit, but when editing code with heavvy markup and perhaps longer than standard rows of code (or data) gedit sometimes really slows down to a crawl. But it's not a bad editor, and I suspect that as the thread is on notepad2, vim or emacs is not really in the scope of what the op wants.
[/vim-user]

---

### Post by SuperSonic4 on 2009-09-12
I use nano or kate for text editing but then I'm no programmer

---

### Post by RATM_Owns on 2009-09-12
> **Exodist said:**
> Use GEdit. Your not going to get a better text editor then GEdit anywhere.
Vim. :D

---

### Post by Tibuda on 2009-09-12
> **Exodist said:**
> Use GEdit. Your not going to get a better text editor then GEdit anywhere.
+1. It is so underrated, but with the external tools plugin, it becomes really powerful. (G)Vim it a lot better, but is requires some time learning it (it is worth, I assure).

---

### Post by Bölvaður on 2009-09-12
Gedit with plugins or Geany? I'd use Geany, but that is only because I am in love.

---

### Post by frenchn00b on 2009-09-12
> **danielrmt said:**
> +1. It is so underrated, but with the external tools plugin, it becomes really powerful. (G)Vim it a lot better, but is requires some time learning it (it is worth, I assure).

come on; the source is there, let's import it in our linux

---

### Post by red_Marvin on 2009-09-12
> **frenchn00b said:**
> come on; the source is there, let's import it in our linux

Indeed. What is stopping you?

---

### Post by dumblebee100 on 2009-09-12
as far I feel the vim rules all editors ...basically I dont use but I know its power 

so if we want some excellent editor then why dont we mix up all good things from gedit kate and vim ...

and considering notepad2 ...its just a vim copy but with different commands and implementation I feel so .....

we the linux people has the best editor(vim) but we dont care much about it ....

---

### Post by orlox on 2009-09-12
> **frenchn00b said:**
> come on; the source is there, let's import it in our linux

It's a common misconception that a thing can be ported only because we have the source code. Sometimes, this even happens between kde and gnome apps, and it's the same story.

Porting something so heavily dependand on system libraries both for the GUI and the basic functionality is a tremendous work to done, besides, after being ported to gnome or kde, notepad2 would only be a (very) sub-kate or sub-gedit application respectively.

Notepad was one of the most useless pure text editors I've had a chance to use. Anytime I really needed it (i.e. had only access to windows), it did something awkward (like, not recognizing certain line-breaks properly and displaying a single line document) and besides, it was ugly...Do you really have a need for native notepad on linux?? it works fine under wine...

---

### Post by Warpnow on 2009-09-12
> **frenchn00b said:**
> come on; the source is there, let's import it in our linux

Porting might sound simple, but its an extremely complicated and drawn out task.

---

### Post by orlox on 2009-09-12
> **dumblebee100 said:**
> as far I feel the vim rules all editors ...basically I dont use but I know its power 

so if we want some excellent editor then why dont we mix up all good things from gedit kate and vim ...

and considering notepad2 ...its just a vim copy but with different commands and implementation I feel so .....

we the linux people has the best editor(vim) but we dont care much about it ....

Actually, vim is also available for windows...

---

### Post by Tibuda on 2009-09-12
> **orlox said:**
> Actually, vim is also available for windows...

and mac.

---

### Post by collinp on 2009-09-12
You want a real text editor for programming?

Emacs.

That is all.

---

### Post by bailout on 2009-09-12
Another text editor - just what linux needs ;)

---

### Post by xuCGC002 on 2009-09-12
Editor wars, lol.

*uses nano*

---

### Post by forrestcupp on 2009-09-12
> **frenchn00b said:**
> come on; the source is there, let's import it in our linuxRead muep's post, which is the 2nd post in this thread.  The program was written using the win32 api.  It would probably be easier to create a completely new editor than to port it to some Linux GUI framework.

> **orlox said:**
> 
Notepad was one of the most useless pure text editors I've had a chance to use. Anytime I really needed it (i.e. had only access to windows), it did something awkward (like, not recognizing certain line-breaks properly and displaying a single line document) and besides, it was ugly...Do you really have a need for native notepad on linux?? it works fine under wine...
True.  But this thread isn't about Notepad, which comes with Windows.  This thread is about [Notepad2](http://www.flos-freeware.ch/notepad2.html) which is something completely different.

---

### Post by Namtabmai on 2009-09-12
> **forrestcupp said:**
> Read muep's post, which is the 2nd post in this thread.  The program was written using the win32 api.  It would probably be easier to create a completely new editor than to port it to some Linux GUI framework.

Exactly, and even if you did manage to disentangle the win32 stuff and create a Linux version, what you'd end up with would be so different from the original ( in terms of source ) you'd have to maintain it separately.

---

### Post by Frak on 2009-09-12
That would require a lot of work to change any and all Win-specific code. They are attempting to do something like this with Paint.NET.

As for development, I use GEdit + Eddt plugin (from GitHub).

---

### Post by frenchn00b on 2009-09-12
> **bailout said:**
> Another text editor - just what linux needs ;)

there is never too much ;)

---

### Post by twright on 2009-09-12
> **Exodist said:**
> Use GEdit. Your not going to get a better text editor then GEdit anywhere.

I cant understand why so many people want windows crap in linux. I dont think people realize that most crap in windows was cloned from or an idea already being used on a *nix based system. /sigh
Well whilst that is true most Window programs people hanker for are not much good, notepad2 is fairly awesome and has many things not found in gedit such as macros. (oops, I was thinking of notepad++ but the principle is the same).

I now just use Vim but for normal people notepad2 would be useful. As others have said it runs fine under wine and it would not be worth porting and rewriting the interface as that is the best bit.

---

### Post by twright on 2009-09-12
> **Frak said:**
> That would require a lot of work to change any and all Win-specific code. They are attempting to do something like this with Paint.NET.

Actually it is a lot easier for paint.net as that is written in dot.net which can just be replaced with mono. The hardest bit of that port was actually not the interface but special api calls :-)

---

### Post by Frak on 2009-09-12
> **frenchn00b said:**
> there is never too much ;)
+9001

If Linux had TextMate and/or Coda and/or Espresso, I'd be in HEAVEN. I'd never need to go back to Mac, well, besides Photoshop and the like (this is a PowerPC Mac).

@twright
I am aware, but the biggest issue is working out all of the code that just isn't compatible at all with Mono. Last I heard, when they passed the source through the Analyser, Kittens cried.

---

### Post by twright on 2009-09-12
> **frenchn00b said:**
> come on; the source is there, let's import it in our linux
Basically to port something you need to be sufficiently adept at programming to virtually write it from scratch and care enough to spend many hours on doing so.

In Linux land most people who have the programming knowledge to rewrite it would rather use Vim anyway.

---

### Post by phrostbyte on 2009-09-12
Paint.NET has already been ported to Linux. It just has some (minor) issues.

Here is a patented phrostbyte one-click(tm) install:

```

sudo apt-get -y install mono-devel libmono-winforms2.0-cil subversion
svn checkout http://paint-mono.googlecode.com/svn/trunk/ paintdotnet
cd paintdotnet/src
./configure
make
sudo make install
paintdotnet


```

---

### Post by Frak on 2009-09-12
> **phrostbyte said:**
> Paint.NET has already been ported to Linux. It just has some (minor) issues.

Here is a patented phrostbyte one-click(tm) install:

<code snipped for great justice>
The point wasn't if it has or hasn't already been ported, it's just the time it took to port it over, which took, what, about 2 years?

---

### Post by twright on 2009-09-12
> **Frak said:**
> The point wasn't if it has or hasn't already been ported, it's just the time it took to port it over, which took, what, about 2 years?
Lucky I only heard about it once it was done in that case :KS

---

### Post by Frak on 2009-09-12
> **twright said:**
> Lucky I only heard about it once it was done in that case :KS
Yep, only 47 minutes ago in fact.

---

### Post by twright on 2009-09-12
> **Frak said:**
> Yep, only 47 minutes ago in fact.
Actually a few weeks ago but I had not really thought about it until then :-)

---

### Post by tubasoldier on 2009-09-12
There is nothing in notepad2 that is not already available in Kate. To port over yet another text editor would be one of those re-inventing the wheel things that people always complain about with Linux. 

Notepad2 exists because the simple text editors for Windows sucked. Linux has loads of great text editors already available. notepad2 will not be a great enough application to convince anyone to use Linux over anything else. 

Good luck to the OP with porting it over. Being that it is written with the the MS windowing system it won't be an easy task. Its much more simple to use an editor already in existence. Kate, Gedit, vim, emacs, ect...

---

### Post by phrostbyte on 2009-09-12
> **tubasoldier said:**
> There is nothing in notepad2 that is not already available in Kate. To port over yet another text editor would be one of those re-inventing the wheel things that people always complain about with Linux. 

Notepad2 exists because the simple text editors for Windows sucked. Linux has loads of great text editors already available. notepad2 will not be a great enough application to convince anyone to use Linux over anything else. 

Good luck to the OP with porting it over. Being that it is written with the the MS windowing system it won't be an easy task. Its much more simple to use an editor already in existence. Kate, Gedit, vim, emacs, ect...

It's worth noting that Notepad2 has a Wine AppDB "Platinum" rating, meaning it runs near flawlessly in Wine. With Winelib in theory you could compile it into a "native" Linux binary without modifying much of any code, but it would retain a foreign look and feel.

---

### Post by frenchn00b on 2009-09-13
> **Frak said:**
> +9001

If Linux had TextMate and/or Coda and/or Espresso, I'd be in HEAVEN. I'd never need to go back to Mac, well, besides Photoshop and the like (this is a PowerPC Mac).

@twright
I am aware, but the biggest issue is working out all of the code that just isn't compatible at all with Mono. Last I heard, when they passed the source through the Analyser, Kittens cried.

  
Ahhhh, you see, Notepad2 would make people happy.
There is never too much packages ;) :)

---

### Post by samjh on 2009-09-13
> **Hellow said:**
> You want a real text editor for programming?

Emacs.

That is all.

[IMG]http://blogs.smh.com.au/screenplay/BigRedButton.jpg[/IMG]

[IMG]http://lh6.ggpht.com/fisherwy/RxDbhy2KpBI/AAAAAAAAKCs/Ewm-Ytp52KE/Beautiful+Image+of+French+1968+Nuclear+Test%5B2%5D.jpg[/IMG]

---

### Post by frenchn00b on 2009-09-18
We have to admit that notepad2, is much better than gedit, beaver, or whatever we have.

Hey guys, realize, that Mac OS 7 had already a notepad that talks ;)
try Mac is better than Linux (but not free)

[here the emulator made for you ]("http://ubuntuforums.org/showthread.php?t=1265153") I made there an howto to use macintosh under linux.
Find and google this : [[IMG]http://img245.imageshack.us/img245/4400/setupmac.jpg[/IMG]](http://img245.imageshack.us/i/setupmac.jpg/)
and you have sound in your notepad and lot of features :)

---

### Post by Grifulkin on 2009-09-18
> **xuCGC002 said:**
> Editor wars, lol.

*uses nano*

+1 

Same here.

---

### Post by frenchn00b on 2009-11-30
Hi guys

even better

can we get this super mega notepad ?
[http://notepad-plus.sourceforge.net/uk/download.php](http://notepad-plus.sourceforge.net/uk/download.php)

---

### Post by twright on 2009-12-03
> **frenchn00b said:**
> 
Hey guys, realize, that Mac OS 7 had already a notepad that talks ;)[/URL]
and you have sound in your notepad and lot of features :)
Um, Vim can do that too:
```

:!cat filename > festival

```

Vim has always been and will always be the best text editor in my book...

---

### Post by frenchn00b on 2009-12-05
> **frenchn00b said:**
> Hi guys

even better

can we get this super mega notepad ?
[http://notepad-plus.sourceforge.net/uk/download.php](http://notepad-plus.sourceforge.net/uk/download.php)

this notepad is really cool 

here a shot>
[http://notepad-plus.sourceforge.net/commun/screenshots/scrsh_dockingFeature.png](http://notepad-plus.sourceforge.net/commun/screenshots/scrsh_dockingFeature.png)

---

### Post by RATM_Owns on 2009-12-05
[The only editor you'll ever need.](http://www.vim.org/)

---

