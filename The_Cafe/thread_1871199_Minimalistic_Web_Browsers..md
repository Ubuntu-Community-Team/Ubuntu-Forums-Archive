---
title: "Minimalistic Web Browsers."
date: 2011-10-28
forum: The Cafe
---

### Post by galacticaboy on 2011-10-28
I am looking for a Mini Web Browser, if you will. Sorta like Luakit ([http://www.linuxjournal.com/content/luakit-extensible-micro-browser](http://www.linuxjournal.com/content/luakit-extensible-micro-browser)). I like Luakit, but it has a few quirks that have me pulling out my tounge after dirtying up the room with my words. Does anyone know of any other ones?

---

### Post by Fragadelic on 2011-10-28
Have you tried Midori?

---

### Post by galacticaboy on 2011-10-28
> **Fragadelic said:**
> Have you tried Midori?

I have and I cannot stand Midori. I am looking for something super minimal, like the picture here: [http://goo.gl/r951o](http://goo.gl/r951o)

---

### Post by koleoptero on 2011-10-28
[http://pwmt.org/projects/jumanji/](http://pwmt.org/projects/jumanji/)

---

### Post by urukrama on 2011-10-28
> **koleoptero said:**
> [http://pwmt.org/projects/jumanji/](http://pwmt.org/projects/jumanji/)

You mean like in the attached image? That is Opera, with all the bars (address, status, menu, tab, etc.) disabled.

---

### Post by galacticaboy on 2011-10-28
> **urukrama said:**
> You mean like in the attached image? That is Opera, with all the bars (address, status, menu, tab, etc.) disabled.

Yes like that, but not opera, I don't want a browser with "disabled" anything, I just don't want them, Just like Jumanji and Luakit, now, with Jumanji, how do I install it?

---

### Post by krapp on 2011-10-28
Conkeror is not exactly minimalist, but it has a clean interface with a modeline and is controlled by Emacs-like bindings.

It's fun for awhile, but I find something like Chromium to be a better compromise. Anyway, it's nice to use the mouse once in a while!

---

### Post by juancarlospaco on 2011-10-28
128 Lines long Web Browser, Webkit, Qt, HTML5 compatible, easy to hack, single file: 
[http://code.google.com/p/devicenzo/source/browse/trunk/devicenzo-pretty.py](http://code.google.com/p/devicenzo/source/browse/trunk/devicenzo-pretty.py)

I start including it bundled on my works, 
because it "understand" more HTML5 than Firefox Nightly, plus this: [http://www.firefoxwithbing.com](http://www.firefoxwithbing.com)

---

### Post by landwell on 2011-10-28
[Uzbl]("http://uzbl.org/")

[Surf]("http://surf.suckless.org/")

---

### Post by galacticaboy on 2011-10-28
I don't understand how to install any of those browsers, I need a .deb or some instructions.

---

### Post by landwell on 2011-10-28
> **galacticaboy said:**
> I don't understand how to install any of those browsers, I need a .deb or some instructions.

I thought they were in the repos so you could install with apt. If not, there should be a README and INSTALL text file inside the tarball you can read. Both are pretty straight forward installs as I recall.

---

### Post by krapp on 2011-10-28
If Ubuntu maintains their packages, search for them in Synaptic. Or install in the command line.

For instance,

```
apt-get install uzbl
```

installs uzbl.

If other packages are not in the repo's you're going to have to install a binary package or simply go to another distro.

---

### Post by vehemoth on 2011-10-28
> **krapp said:**
> If Ubuntu maintains their packages, search for them in Synaptic. Or install in the command line.

For instance,

```
apt-get install uzbl
```installs uzbl.

If other packages are not in the repo's you're going to have to install a binary package or simply go to another distro.
Though from memory you want ```
apt-get install uzbl-browser
or
apt-get install uzbl-tabbed
``` It's the most minimilast browser I know of so long as you don't mind it being mostly keyboard controlled (or fully if you want to use they keyboard for things like scrolling and links). You can disable the scrollbar and it has a single small bar down the bottom that you can turn on and off with a single key press.
[http://ubuntuforums.org/attachment.php?attachmentid=203849&d=1318133563](http://ubuntuforums.org/attachment.php?attachmentid=203849&d=1318133563)
[http://ubuntuforums.org/attachment.php?attachmentid=203850&d=1318133563](http://ubuntuforums.org/attachment.php?attachmentid=203850&d=1318133563)
some screens of it in action, though I don't know where the black border came from

---

### Post by juancarlospaco on 2011-10-28
> **galacticaboy said:**
> I don't understand how to install any of those browsers, I need a .deb or some instructions.

Open a Terminal Window, copy, paste into the Terminal, and press ENTER:
```

wget http://code.google.com/p/devicenzo/source/browse/trunk/devicenzo-pretty.py && python devicenzo-pretty.py

```

---

### Post by krapp on 2011-10-28
^ You might wanna say what that is before he runs on it his system!

---

### Post by juancarlospaco on 2011-10-28
> **krapp said:**
> ^ You might wanna say what that is before he runs on it his system!

> **juancarlospaco said:**
> 128 Lines long Web Browser, Webkit, Qt, HTML5 compatible, easy to hack, single file


[click here]("http://twitpic.com/4bvpgh/full")

---

### Post by matthew.ball on 2011-10-28
> **krapp said:**
> Conkeror is not exactly minimalist, but it has a clean interface with a modeline and is controlled by Emacs-like bindings.

It's fun for awhile, but I find something like Chromium to be a better compromise. Anyway, it's nice to use the mouse once in a while!
You can use a mouse with Conkeror.

---

### Post by del_diablo on 2011-10-28
Why do you want minimalizm when you have Opera?

---

### Post by krapp on 2011-10-28
> **matthew.ball said:**
> You can use a mouse with Conkeror.

Not much point to it! I'd rather have a proper mouse interface.

---

### Post by matthew.ball on 2011-10-28
Ummm, you can use a mouse with Conkeror just as much as you can use a mouse with, say Chromium.

Conkeror just enables you to be entirely keyboard oriented, if you want. You don't have to enable anything extra to use the mouse.

---

### Post by krapp on 2011-10-28
In order to use the mouse solely, yeah you do. Back and forward buttons for instance.

---

### Post by SadisticCheeto on 2011-10-29
There's [dwb](http://portix.bitbucket.org/dwb/), which is similar to jumanji, luakit, uzbl, etc. It seems to get overlooked a lot. I decided to create a ppa for both the GTK2 and GTK3 versions. The ppa is [here](https://launchpad.net/~jomasti/+archive/ppa-dwb).

---

### Post by Naiki Muliaina on 2011-10-29
> **juancarlospaco said:**
> Open a Terminal Window, copy, paste into the Terminal, and press ENTER:
```

wget http://code.google.com/p/devicenzo/source/browse/trunk/devicenzo-pretty.py && python devicenzo-pretty.py

```

```
nai@nai:~$ wget http://code.google.com/p/devicenzo/source/browse/trunk/devicenzo-pretty.py && python devicenzo-pretty.py
--2011-10-29 09:13:45--  http://code.google.com/p/devicenzo/source/browse/trunk/devicenzo-pretty.py
Resolving code.google.com... 74.125.230.102, 74.125.230.110, 74.125.230.108, ...
Connecting to code.google.com|74.125.230.102|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `devicenzo-pretty.py'

    [ <=>                                   ] 57,861      --.-K/s   in 0.1s    

2011-10-29 09:13:46 (496 KB/s) - `devicenzo-pretty.py' saved [57861]

  File "devicenzo-pretty.py", line 5
    <!DOCTYPE html>
    ^
SyntaxError: invalid syntax
```

Nadgers. :(

---

### Post by SadisticCheeto on 2011-10-29
> **Naiki Muliaina said:**
> ```
~
```

Nadgers. :(

It wasn't a direct link to the .py file.
```
wget https://devicenzo.googlecode.com/svn/trunk/devicenzo-pretty.py && python devicenzo-pretty.py
```
Be sure to have python-qt4 installed, too. However, it segfaulted for me.

---

### Post by juancarlospaco on 2011-10-29
omg, ...its not so hard to download a single file from the internet:
[http://devicenzo.googlecode.com/svn/trunk/devicenzo-pretty.py](http://devicenzo.googlecode.com/svn/trunk/devicenzo-pretty.py)

---

### Post by mips on 2011-10-30
Ignore this post, did not read the OP properly.

---

### Post by Erik1984 on 2011-10-30
Program it yourself :P [http://vimeo.com/26739037](http://vimeo.com/26739037)

---

### Post by Minguo on 2012-01-02
> **koleoptero said:**
> [http://pwmt.org/projects/jumanji/](http://pwmt.org/projects/jumanji/)

> **SadisticCheeto said:**
> There's [dwb](http://portix.bitbucket.org/dwb/)

> **galacticaboy said:**
> I don't understand how to install any of those browsers, I need a .deb or some instructions.


Surf, Uzbl, and Luakit are now in the repos for 11.10 but I am unable to compile jumanji or dwb.  

I have opened a thread in general help about it.
[http://ubuntuforums.org/showthread.php?p=11581644#post11581644](http://ubuntuforums.org/showthread.php?p=11581644#post11581644)

Also, I think xxxterm [https://opensource.conformal.com/wiki/XXXTerm](https://opensource.conformal.com/wiki/XXXTerm)
may be pertinent to the thread, despite its unfortunate name.

I agree with the OP in that luakit would be ideal if it weren't for some blood boiling annoyances that seem unique to it. (It's method of link highlighting for one.)

---

