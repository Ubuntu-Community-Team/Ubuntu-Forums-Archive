---
title: "Annoying font rendering in Opera 9.20."
date: 2007-04-17
forum: The Cafe
---

### Post by Quillz on 2007-04-17
Whenever I view the Ubuntu Forums in Opera 9.20, this is what I see...
[IMG]http://orange.quickshareit.com/share/ubuntuforums8f99c.png[/IMG]
Basically, all the text appears bold, and I have no idea why. Does anyone who uses Opera know how to get the fonts to render properly?

---

### Post by karellen on 2007-04-17
I use opera 9.20 in ubuntu (and windows) and I happen to like the font rendering (especially in ubuntu as in xp it never looks the way I want)

---

### Post by Quillz on 2007-04-17
Thanks, but that doesn't help me. I'm just the opposite... It displays like it should in Windows, but on OS X and Linux all the text everywhere is in bold.

---

### Post by karellen on 2007-04-17
:D....maybe because I like the more bolded fonts as I have myopia...:)

---

### Post by Quillz on 2007-04-17
Okay, that's good to hear that Opera is working well for you, but I'm not a fan of all text being displayed in bold, and I forgot to mention that every other web page I visit except for Ubuntu Forums displays properly. I've tried using a user-defined style, but that doesn't work. Isn't there a simple way of telling *x* web page to use _my_ fonts, instead of *their* fonts?

---

### Post by karellen on 2007-04-17
in opera I don't know....in firefox there is the option "allow pages to choose their own fonts...etc" with a checkbox :)

---

### Post by Quillz on 2007-04-17
Yes, I know how to fix it in Firefox. But I'm using Opera, not Firefox.

---

### Post by RAV TUX on 2007-04-17
> **Quillz said:**
> Whenever I view the Ubuntu Forums in Opera 9.20, this is what I see...
[IMG]http://orange.quickshareit.com/share/ubuntuforums8f99c.png[/IMG]
Basically, all the text appears bold, and I have no idea why. Does anyone who uses Opera know how to get the fonts to render properly?

Not sure what your talking about, font rendering in Opera is fine for me, do you have a screenshot?

---

### Post by Quillz on 2007-04-17
I'll try to get a screenshot, but just imagine the text all over the board being in bold. Everything, from the thread titles to the message boxes are in bold.

[IMG]http://mandarin.quickshareit.com/share/picture1358bc.png[/IMG]

---

### Post by Rhapsody on 2007-04-17
Works for me. Exactly the same as in Firefox.

---

### Post by dbbolton on 2007-04-17
you can fix it by```
$ sudo aptitude purge opera
$ /usr/bin/firefox
```

;)

---

### Post by Quillz on 2007-04-17
> **dbbolton said:**
> you can fix it by```
$ sudo aptitude purge opera
$ /usr/bin/firefox
```

;)
If you're suggesting I use Firefox instead of Opera, then... no. I use Firefox, but I prefer Opera in many aspects.

Surely no one would know what is causing this on both Linux and OS X? No one knows how you can tell a specific web page to use your defined fonts instead of the web page's? (I say this because I don't want to override the web page with an entire custom user style, I just want to replace the fonts.)

---

### Post by dbbolton on 2007-04-17
it was like, a joke.

---

### Post by Quillz on 2007-04-17
> **dbbolton said:**
> it was like, a joke.
Joke or not, it doesn't help me out, nor anyone else who may be having a similar issue with Opera 9.20. And as I've stated previously, this font rendering issue is only present on the Ubuntu Forums. I've yet to go to any other site where it's been a problem. Is the site optimized for browsing with all the popular browsers?

---

### Post by dbbolton on 2007-04-17
if you're that serious about it, i suggest that you post somewhere other than the cafe. perhaps [**Forum Feedback & Help**](http://ubuntuforums.org/forumdisplay.php?f=48).

---

### Post by Quillz on 2007-04-17
> **dbbolton said:**
> if you're that serious about it, i suggest that you post somewhere other than the cafe. perhaps [**Forum Feedback & Help**](http://ubuntuforums.org/forumdisplay.php?f=48).
I've asked on a few other boards, apparently it could be an isolated incident. I actually had this very same issue with Firefox on OS X, which I remedied by telling Firefox to use my user-defined fonts instead of web page-defined fonts, so I'm quite sure I can do the same thing in Opera, if only I knew how. I might have to go into the Preferences Editor.

---

### Post by rai4shu2 on 2007-04-18
Looks like your Tahoma is stuck in bold. If you have that font somewhere, try removing it.

---

### Post by Quillz on 2007-04-18
> **rai4shu2 said:**
> Looks like your Tahoma is stuck in bold. If you have that font somewhere, try removing it.
It's using Lucida Grande, though, and not Tahoma. Nevertheless, I'll try seeing if it can use Times or Arial.

---

### Post by Quillz on 2007-04-18
And for comparison, here's how my Firefox looks, more or less normal, the way the page should be displaying. It's also using the Lucida Grande font.

---

### Post by karellen on 2007-04-18
:confused: man, I don't know how to help you...try using another font and keep digging around here....

---

### Post by Quillz on 2007-04-18
> **karellen said:**
> :confused: man, I don't know how to help you...try using another font and keep digging around here....
Yeah, I've tried a few others but still get the same issue. I guess I'll just stop using Opera...

---

### Post by karellen on 2007-04-18
that's a screenshot of my current opera 9.20 displaying ubuntuforums

---

### Post by Colonel Kilkenny on 2007-04-18
> **Quillz said:**
> Yeah, I've tried a few others but still get the same issue. I guess I'll just stop using Opera...

Are you sure you have correct settings in site preferences? No UserJS which would affect the font? User defined CSS? Shared or static version of Opera?
Does opera -debugfont say anything which might be causing the bolder fonts? Have you tried on new profile?

Have you tried asking on [http://my.opera.com/forums](http://my.opera.com/forums) ?

Imho, it's just stupid to switch browser only because you have little problem which no one else can see.

I'd say that the problem lies in your fonts / in font which this site uses. I'd try changing it with my own CSS.

Edit. Apparently you had already tried your own CSS.

---

### Post by Quillz on 2007-04-18
> **Colonel Kilkenny said:**
> Are you sure you have correct settings in site preferences? No UserJS which would affect the font? User defined CSS? Shared or static version of Opera?
Does opera -debugfont say anything which might be causing the bolder fonts? Have you tried on new profile?

Have you tried asking on [http://my.opera.com/forums](http://my.opera.com/forums) ?

Imho, it's just stupid to switch browser only because you have little problem which no one else can see.

I'd say that the problem lies in your fonts / in font which this site uses. I'd try changing it with my own CSS.

Edit. Apparently you had already tried your own CSS.
Yeah, I've tried using a custom user style, fixed the problem per se but at the expense of the entire style of the page being thrown out and everything just being displayed as text. I'll try making a new profile, and no, I don't have any UserJS other than the stock pieces that get installed with Opera.

---

### Post by rai4shu2 on 2007-04-18
Your Opera snapshot was *not* showing you Lucida. That was Tahoma. Notice the serifs in the capital I.

---

### Post by TheRingmaster on 2007-04-18
try using sans font.

---

### Post by Ambimom on 2007-04-18
Silly question, but in your tools/preferences/fonts....what have you selected?

You can change the fonts in Opera for every single aspect of a web page.  Perhaps you have already changed the fonts?   There's the overall font selection, but then a long laundry list of individual font selections.  You can change any or all of these.   See if this helps. 

Also you should try to load the true type fonts from Synaptic.

Good luck.

---

