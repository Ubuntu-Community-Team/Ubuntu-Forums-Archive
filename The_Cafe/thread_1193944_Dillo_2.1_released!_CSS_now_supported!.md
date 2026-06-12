---
title: "Dillo 2.1 released! CSS now supported!"
date: 2009-06-22
forum: The Cafe
---

### Post by sertse on 2009-06-22
Dillo is one of the lightest and fastest (if limited) graphical web browsers. The latest version 2.1 was released on Saturday, but posting here to draw some attention since no one has done so yet.

Main features in this release: IT NOW SUPPORTS (basic) CSS! Keybindings can also be reconfigured now. 

I redid mine to follow the shortcuts done in Firefox and practically every other browser, personally.

Full changelog: [http://hg.dillo.org/dillo/file/tip/ChangeLog](http://hg.dillo.org/dillo/file/tip/ChangeLog)

You can get at their site at [http://www.dillo.org/download.html](http://www.dillo.org/download.html) . It has links to tarballs, debs and rpms. 

It was alternating between Dillo and (x)links2 for a while. Now I thing Dillo is indisputably best in its class again.

---

### Post by bryonak on 2009-06-22
I've been using it for two days now, and it's really nice!

Apropos keybindings... has anyone figured out what commands there are to bind to? I'd like to set <Shift>Space to "scroll-up-one-screen", yet I can't find a list of available commands. The only documentation AFAICT are the available keys in .dillo/keysrc.

---

### Post by billgoldberg on 2009-06-22
Hold the presses. Did that mean that Dillo 2.0 and before didn't support CSS?

And it now only has basic CSS support, whatever that might be?

You must be desperate on system resources if you would go with this subpar browser.

---

### Post by RiceMonster on 2009-06-22
> **billgoldberg said:**
> Hold the presses. Did that mean that Dillo 2.0 and before didn't support CSS?

And it now only has basic CSS support, whatever that might be?

You must be desperate on system resources if you would go with this subpar browser.

My thoughts exactly.

---

### Post by bryonak on 2009-06-22
> **billgoldberg said:**
> Hold the presses. Did that mean that Dillo 2.0 and before didn't support CSS?

And it now only has basic CSS support, whatever that might be?

You must be desperate on system resources if you would go with this subpar browser.

Hehe, that's right, Dillo 2.0 didn't have CSS. But it does start up in less than half a second on my system, and renders huge pages much faster than Firefox or any other browser. Not to speak about the default memory usage of 2-3 MB.

The Dillo project started out before CSS was widely used, and the browser is still very popular in minimalistic GUI distros like Puppy.
Development then stalled at Dillo 0.8, but was taken up again 8 months ago. They jumped directly to version 2.0, which was a big code cleanup and port to FLTK.
2.1 brought basic support for "that newfangled CSS stuff" ;) and many other improvements. They plan to release twice a year, so 2.2 is coming in 6 months... and will hopefully have complete CSS support.

Besides, JavaScript or Flash are out of question. Dillo simply isn't aimed at such people (which make up the majority, I know), but rather for true connaisseurs of lightweight web browsing.
I use it on a set of pages I know it works well with. I can use it to browse RFCs and huge indexes which render *visibly* in Firefox.
Quickly checking 5 such pages while doing something else is quite comfortable when startup and rendering times... simply don't exist ;)

---

### Post by K.Mandla on 2009-06-22
> **billgoldberg said:**
> Hold the presses. Did that mean that Dillo 2.0 and before didn't support CSS?

And it now only has basic CSS support, whatever that might be?

You must be desperate on system resources if you would go with this subpar browser.
I use it occasionally, not necessarily on the basis of system resources, but because it's so exceptionally fast.

As an example, back when I used to moderate, it was significantly faster to use Dillo than to use Firefox. Dillo didn't necessarily do everything Firefox could, and it's true at times that the pages weren't "perfect," but it was hard to complain when I could get five or six things done with Dillo in the time it would take to do one (two if I was lucky) with Firefox.

Depends on what you need it for, if you ask me. 

Of course, Dillo's got nothing on elinks. :twisted:

---

### Post by bryonak on 2009-06-22
> **billgoldberg said:**
> Hold the presses. Did that mean that Dillo 2.0 and before didn't support CSS?

And it now only has basic CSS support, whatever that might be?

You must be desperate on system resources if you would go with this subpar browser.
Just quoting again because the 3 posts before this one did it... so nobody gives me funny looks for breaking the line ;)


> **K.Mandla said:**
> 
Of course, Dillo's got nothing on elinks. :twisted:

Of course, elinks's got nothing on **wget -O -**
What, you can't render the HTML yourself!? :P



Hmm, do I have anything actually meaningful to add?
Oh yes.. anybody got the available keybinding commands figured out yet?

---

### Post by sertse on 2009-06-22
Some tips when using Dillo.[http://www.dillo.org/dillo2-help.html](http://www.dillo.org/dillo2-help.html) is a good resource!!

Enable cookies! Dillo disables all cookies by default due to their views on privacy, security, anonymity etc. To enable follow [http://www.dillo.org/Cookies.txt](http://www.dillo.org/Cookies.txt) and edit your ~/.dillo/cookiesrc appropriately. 

Configurable keybindings: Place a file at ~/.dillo/keysrc and paste this in [http://www.dillo.org/keysrc](http://www.dillo.org/keysrc) Adjust accordingly. 

bryonak; That's all I know about bindings too, it think it's still somewhat limited.

Other have already covered what I said, but reason to use dillo are extreme speed and lightness. Strangely though, elinks does render pages better, aside from the fact it's a text browser, but I actually think dillo is faster. If someone would remerge elinks/xlinks2... it'll be the ultimate browser. But Dillo does for now :)

---

### Post by johnraff on 2009-07-16
> **billgoldberg said:**
>  Did that mean that Dillo 2.0 and before didn't support CSS?Yes, and it was great for browsing through some enormous folder of html documentation, or doing a quick web search. In fact, if I can't find a way to *disable* CSS in Dillo 2.1 I might well go back to 2.0! 

For me, the current half-way implementation of CSS just makes pages less readable in many cases for no particular advantage. Full, flawless rendering ala Gecko might slow it down too much anyway...

---

### Post by sertse on 2009-07-16
> **johnraff said:**
>  In fact, if I can't find a way to *disable* CSS in Dillo 2.1 I might well go back to 2.0! 

For me, the current half-way implementation of CSS just makes pages less readable in many cases for no particular advantage. Full, flawless rendering ala Gecko might slow it down too much anyway...

Tools -> Uncheck "use remote CSS" and "use embedded CSS".

---

### Post by johnraff on 2009-07-16
Thanks sertse, that does it!

---

