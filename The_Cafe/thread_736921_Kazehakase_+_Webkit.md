---
title: "Kazehakase + Webkit"
date: 2008-03-27
forum: The Cafe
---

### Post by el mariachi on 2008-03-27
Out of curiosity I compiled Kazehakase with WebKit support.

It works like a charm, with very good page rendering, as expected from the Webkit engine. Some functionality is still missing, nothing unexpected from beta software though.

It gets 90/100 @ [http://acid3.acidtests.org/](http://acid3.acidtests.org/)

To try it, checkout the latest WebKit SVN, install XULRunner, and compile kazehakase from scratch. 

```
autogen.sh
./configure --prefix=/usr
make
make install
```After this, fire up the browser, go to the preferences, "browser" section and select webkit_gtk from the drop-down menu. Happy lightweight browsing.

Ubuntu Forums is one the sites that isn't rendered right, dunno why - it's one of the few around (I've found very few indeed). Oh and don't expect Java, flash or anyother candy :p

---

### Post by Gigamo on 2008-03-27
Meh, both webkit and kazehakase fail to compile for me. Guess I fail. :)

---

### Post by el mariachi on 2008-03-27
hummm I just compiled the latest webkit SVN with SVG and HTML5 video support

---

### Post by bruce89 on 2008-03-27
> **el mariachi said:**
> hummm I just compiled the latest webkit SVN with SVG and HTML5 video support

For some reason, I get a compile error trying to do that (just the SVG).

Do you get [100/100]("http://webkit.org/blog/173/webkit-achieves-acid3-100100-in-public-build/")?

---

### Post by el mariachi on 2008-03-27
no, because the latest svn won't compile.. weird. 
I'll download a fresh set and try again

edit: The "demo" browser included in the WebKit source package renders every site i've been to correctly. Midori also renders UbuntuForums correctly. Only Kazehakase is displaying wrong behaviour. I'll post some more info in a few days - I'll be competing in the Portuguese National Swimming Championships, wish em luck haha. If anyone achieves something with kazehakase, please post it here! :D

---

### Post by bruce89 on 2008-03-27
> **el mariachi said:**
> no, because the latest svn won't compile.. weird. 
I'll download a fresh set and try again

The latest I can get to compile is r31340.

---

### Post by p3pilot on 2008-03-30
I finally got WebKit to compile using --enable-experimental-svg instead of --enable-svg.  There is a bug written against autotools.

[http://bugs.webkit.org/show_bug.cgi?id=18163](http://bugs.webkit.org/show_bug.cgi?id=18163)

George

---

### Post by p3pilot on 2008-03-30
Sorry about that, it is --enable-svg-experimental

George sherwood

---

### Post by mrgnash on 2008-03-30
I've tried this sort of thing with Epiphany. Never had much luck, unfortunately :(

---

### Post by klange on 2008-03-30
I only get a 94/100 with WebKit-enabled Epiphany (and it has a link error). But that's still better than the horribly distorted 68/100 I get with FF3b4.

---

### Post by el mariachi on 2008-04-03
The latest Webkit rev. compiles :D

---

### Post by leo1981 on 2008-04-08
Hi,
I compiled successfully WebKit-r31667.
I tested it with the script ./run-launcher --gtk and I got 100/100 on AcidTest3.
I installed XULRunner and XULRunner-1.9

But when  I run ./configure --prefix=/usr on kazehakase, I receive:
```

Configure Result:

  Gecko Engine     : -
  Gtk+ WebCore     : no
  WebKit/GTK+      : no
  GtkIEEmbed       : no
  Migemo           : no
  Ruby             : no
  Hyper Estraier   : no
  Anthy            : no
  MeCab            : no

```

Kazehakase compiles, but without any engine.

Do you know why?

Leonardo

---

### Post by el mariachi on 2008-04-08
did you actually install the engines?
(sudo make install) ?

---

### Post by leo1981 on 2008-04-08
Ops! No.
I installed WebKit from source and XULRunner from repository (sudo apt-get install xulrunner-1.9-dev).
In the configure output I can see that both engines are there.
But it doesn't compile for a Xul problem.
I remover XULRunner and Kazehakase compiles but it doesn't run.
Any suggestion?

Leonardo

--UPDATES
Kazehakase runs, but it is unstable when I change the settings.
I get only 94/100 on the acid test 3, while with  WebKit standalone  I reached 100/100.
Why is there that difference?

---

### Post by K.Mandla on 2008-04-08
Just a guess, but do the configure flags include anything like --enable-webkit? I don't know if that would help or not.

---

### Post by leo1981 on 2008-04-08
I recompiled Webkit with --enable-svg-experimental --enable-svg-filters, and I got 100/100.

The test has "LINKTEST FAILED"  error, so it is not a full result.
I found this link, for the explanation:
[http://www.atoker.com/blog/2008/03/27/webkit-gets-100-on-acid3/](http://www.atoker.com/blog/2008/03/27/webkit-gets-100-on-acid3/)

Kazehakase ./configure found  Webkit automatically without any flag.
I think that Kazehakase has still several interface issues.

---

