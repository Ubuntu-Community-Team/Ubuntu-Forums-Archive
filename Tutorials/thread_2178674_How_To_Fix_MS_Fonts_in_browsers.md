---
title: "How To Fix MS Fonts in browsers"
date: 2013-10-04
forum: Tutorials
---

### Post by elundmark on 2013-10-04
[scroll down for the code]

This isn't the *end all - be all* solution, but it fixed the following problems for me, and fonts displaying correctly***** is *cruzial* if you're doing *any* webdesign. I found [this thread]("http://ubuntuforums.org/showthread.php?t=804242") but since it's closed I thought I'd share this fix for ya'll.
*****) By correctly I should maybe say "show it as it would for Windows", since we're trying to correctly show the default serif font as "Times New Roman" and the sans-serif font as *Arial*.

My senario was this: after using Ubuntu now for 5y I just realized that Firefox doesn't render css rules specifying ```
font-family: Times, serif;
``` as "*Times New Roman*", regardless of any msttcorefonts package installed or not. It instead gets replaced by ghostscript (gsfonts) to show "*Nimbus Roman No9*". And (atleast in Firefox), Nimbus doesn't look like Times at all.

To get a better picture of what I mean, this is how Firefox now shows Times, "Times New Roman", Arial and Helvetica after I finished fixing some things. Compare this image to the acctual page I setup here: [http://jsfiddle.net/2GzvY/3/embedded/result/](http://jsfiddle.net/2GzvY/3/embedded/result/)

[[IMG]http://files.elundmark.se/images/times_nimbus_ref.png[/IMG]]("http://jsfiddle.net/2GzvY/3/embedded/result/")

Now to the solution, which isn't to remove any packages or hack the font settings globally, but to instruct your browsers what font file to use. That, and making sure you have all the fonts installed. The latter was a shock to me, I always thought Helvetica was installed though the non-free package at system install, but it isn't.

So first, make sure you have the [FONT=courier new]msttcorefonts[/FONT] package installed, and also install [FONT=courier new]fondu[/FONT]. Then, google for "Helvetica.dfont" (about 1MB, Mac Font Package), extract the font files to your font folder ~/.fonts : ```
$ fondu Helvetica.dfont
```

Now follow the instructions [here]("https://gist.github.com/elundmark-gists/6828957") ([raw file]("https://gist.github.com/elundmark-gists/6828957/raw/6527cc25f010170e9ddceda2f750ae16483ef35a/times_numbus_fix.css")) to add the [FONT=courier new]@font-face [/FONT]rules to Firefox and Chrome(-ium). These will correct any css  rules that just says "*Times"* to, instead of using *Nimbus*, use "*Times New Roman*".

Lastly, restart your browser(s) ans check the [refernce page]("http://jsfiddle.net/2GzvY/3/embedded/result/") again. It should look like [this image]("http://files.elundmark.se/images/times_nimbus_ref.png").

I hope this comes in handy and that someday this will be corrected. Sorry if this was hard to follow, I do my best.

---

### Post by oldos2er on 2013-10-08
Moved to Tutorials.

---

### Post by livewirebt2 on 2013-10-08
> Then, google for "Helvetica.dfont" (about 1MB, Mac Font Package), extract the font files to your font folder ~/.fonts :

You're instructing users to pirate Helvetica.

You should choose a font that's available to all users if you care about a certain font being properly displayed. Picking a font you like from [Google Fonts]("http://www.google.com/fonts") or similar sites and embedding it should be easier than tinkering with various font quirks in different browsers and operating systems and require your users to do the same. Ain't happening. Especially not on mobile operating systems. The [Liberation fonts]("http://en.wikipedia.org/wiki/Liberation_fonts") might be interesting, but I couldn't find them on Google Fonts.

---

