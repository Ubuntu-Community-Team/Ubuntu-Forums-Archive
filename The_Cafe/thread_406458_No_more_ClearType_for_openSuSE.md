---
title: "No more ClearType for openSuSE"
date: 2007-04-10
forum: The Cafe
---

### Post by Sunnz on 2007-04-10
[http://beranger.org/index.php?article=2787](http://beranger.org/index.php?article=2787)

They need to avoid MS Patent infringement, oh yeah!!!:popcorn:

---

### Post by vf514 on 2007-04-11
KDE doesn't need ClearType at all. GNOME does. Set your resolution to 1280x1024 in GNOME and watch anti-aliasing quality go down the toilet to see what I mean.

I wonder why this is.

---

### Post by pain of salvation on 2007-04-11
Fedora will disable cleartype too. Freetype project will.

---

### Post by pain of salvation on 2007-04-11
"While it's not clear to me why Red Hat's Enterprise Linux 5, recently released, still doesn't care about some Microsoft patents (usually, Red Hat is very cautious when comes to patents), it's also very curious that the patent covenant between Novell and Microsoft, which is supposed to cover openSUSE's possible patent infringements, is still ignored by the openSUSE team, even in cases where it could have been useful to them!"

The problem is that people are interpreting the deal with microsoft incorrectly. The "patent deal" just protect Novell´s consumers, not Novell.

---

### Post by karellen on 2007-04-11
fonts are, imho, one of the biggest problems of all linux distros. I couldn't have fonts that look as good as those in windows no matter what I've tried. maybe I'm just subjective...

---

### Post by bonzodog on 2007-04-11
You need freetype2 with bytecode enabled to get good fonts.

Most distro's ship with a version of freetype without it enabled, not sure how to find out if Ubuntu has it or not. It's a compile time option on the configure script.

---

### Post by Bloodfen Razormaw on 2007-04-11
> **karellen said:**
> fonts are, imho, one of the biggest problems of all linux distros. I couldn't have fonts that look as good as those in windows no matter what I've tried. maybe I'm just subjective...
This is the biggest problem with every OS.  Even when the font engine is superb, like with Microsoft's Uniscribe, the fonts they ship are still worthless garbage.  The only way to get fonts that look even remotely tolerable is to get some professional grade fonts.  Adobe's hinted fonts are all I can stand to look at.

---

### Post by mstlyevil on 2007-04-11
Novell is such a contradiction sometimes. They sign this agreement to protect themselves and the remove the so called offending function that they paid protection money for. 

Only in America people!


I agree that fonts are rendered slightly better in KDE but they still are lacking compared to Windows or MAC. That is one of my biggest complaints in Linux is that font rendering just plain blows.

---

### Post by darkhatter on 2007-04-11
> **mstlyevil said:**
> Novell is such a contradiction sometimes. They sign this agreement to protect themselves and the remove the so called offending function that they paid protection money for. 

Only in America people!


I agree that fonts are rendered slightly better in KDE but they still are lacking compared to Windows or MAC. That is one of my biggest complaints in Linux is that font rendering just plain blows.

you my friend, don't under stand the novell-microsoft deal at all. Just stop the fud

---

### Post by raublekick on 2007-04-11
I think the font rendering in Ubuntu is just fine, and much better than XP or OS X, espetially for a 1920x1200 resolution. In Ubuntu i have Sans at size 10 and 96dpi. That's the default. In XP I have to bump the DPI or the font size up so that I am not squinting, but then other things get way too big. 

I don't know what font rendering Ubuntu uses, but I like it a lot.

---

### Post by mstlyevil on 2007-04-11
> **darkhatter said:**
> you my friend, don't under stand the novell-microsoft deal at all. Just stop the fud

I understand the deal. The deal is I don't sue you and you don't sue me. You sell my products and here is some cash to keep you off my back.

That is called paying protection money pure and simple.

---

### Post by igknighted on 2007-04-11
I think gnome CAN be OK, if you go into the gconf editor and enable sub-pixel hinting and turn on full anti-aliasing.  The defaults though are awful.  I think KDE's defaults are better, but with everything turned on they turn out to be about the same.  It is easier to fix the fonts in KDE tho, gconf editor is terrible and hard to find if you don't know what you are looking for.

---

### Post by NeoChaosX on 2007-04-11
> **Sunnz said:**
> [http://beranger.org/index.php?article=2787](http://beranger.org/index.php?article=2787)

They need to avoid MS Patent infringement, oh yeah!!!:popcorn:

That article is bunk. [This filter has always been disabled by default in FreeType](http://linux.slashdot.org/comments.pl?sid=230145&cid=18673519), *long* before the Microsoft-Novell deal.

---

### Post by graabein on 2007-04-11
> **darkhatter said:**
> you my friend, don't under stand the novell-microsoft deal at all. Just stop the fud

__________________
bloodninja: ...I put on my robe and wizard hat. 

> **raublekick said:**
> I think the font rendering in Ubuntu is just fine, and much better than XP or OS X, espetially for a 1920x1200 resolution. In Ubuntu i have Sans at size 10 and 96dpi. That's the default. In XP I have to bump the DPI or the font size up so that I am not squinting, but then other things get way too big. 

I don't know what font rendering Ubuntu uses, but I like it a lot.

No relation other than I read your [bloodninja]("http://www.ebooger.com/2005/08/bloodninja-his-robe-and-wizard-hat.html") quote darkhatter -- *I put on my robe and wizard hat* -- Then I see raublekick's avatar with the orange plastic bucket... That's pretty funny huh?

On topic: Fonts are important!

---

### Post by Sunnz on 2007-04-11
Where's gconf?

---

### Post by igknighted on 2007-04-11
> **Sunnz said:**
> Where's gconf?

I think you have to run it from the cli - gconf-editor is the command.  It may not be installed by default, but is available in the repo's if it isn't.

Attached is a SS of some fonts with all AA enabled with gconf... I don't see any drop-off from windows fonts at all.

---

### Post by forrestcupp on 2007-04-11
> **graabein said:**
> No relation other than I read your [bloodninja]("http://www.ebooger.com/2005/08/bloodninja-his-robe-and-wizard-hat.html") quote darkhatter -- *I put on my robe and wizard hat* -- Then I see raublekick's avatar with the orange plastic bucket... That's pretty funny huh?

On topic: Fonts are important!

I noticed that too, and thought it was hilarious.

> **Sunnz said:**
> Where's gconf?

In Feisty, you can just go to System->Preferences->Fonts and set everything from there.

---

### Post by mstlyevil on 2007-04-11
> **igknighted said:**
> I think you have to run it from the cli - gconf-editor is the command.  It may not be installed by default, but is available in the repo's if it isn't.

Attached is a SS of some fonts with all AA enabled with gconf... I don't see any drop-off from windows fonts at all.

Just open up the menu editor and you can add gconf to the menu.

---

### Post by Adamant1988 on 2007-04-11
> **mstlyevil said:**
> I understand the deal. **The deal is I don't sue you and you don't sue me.** You sell my products and here is some cash to keep you off my back.

That is called paying protection money pure and simple.

Congratulations on proving yourself ignorant.  Now, go read about the deal.  (Hint: Microsoft can still sue Novell if they want to, the promise doesn't extend to developers, or the company itself) 

In any case, Novell has responded to this whole font ordeal: 

Source: [ http://www.novell.com/prblogs/?p=318](http://www.novell.com/prblogs/?p=318)

[quote=Bruce Lowry] “Novell will not change its development practices as a result of this agreement. It has always been our policy in all development, open source and proprietary, to stay away from code that infringes another’s patents, and we will continue to develop software using these standard practices. If any of our code is found to infringe someone else’s patents, we will try to find prior technology to invalidate the patents, rework the code to design around the infringement, or as a last resort remove the functionality. Novell is committed to protecting, preserving and promoting freedom for free and open source software.”[/quote]

I hope this will put an end to the FUD in this thread.

---

### Post by mstlyevil on 2007-04-11
> **Adamant1988 said:**
> Congratulations on proving yourself ignorant.  Now, go read about the deal.  (Hint: Microsoft can still sue Novell if they want to, the promise doesn't extend to developers, or the company itself) 

In any case, Novell has responded to this whole font ordeal: 

Source: [ http://www.novell.com/prblogs/?p=318](http://www.novell.com/prblogs/?p=318)



I hope this will put an end to the FUD in this thread.

I have read the deal and the agreement is to indemnify each other from being sued on each others patents.

---

### Post by Sunnz on 2007-04-11
> **forrestcupp said:**
> I noticed that too, and thought it was hilarious.



In Feisty, you can just go to System->Preferences->Fonts and set everything from there.
Nice, thanks.

---

### Post by Sunnz on 2007-04-11
> **Adamant1988 said:**
> Congratulations on proving yourself ignorant.  Now, go read about the deal.  (H**[B]int: Microsoft can still sue Novell if they want to, the promise doesn't extend to developers, or the company itself**[/B]) 


So they don't sue Novell customers. But who are considered as customers? Whoever uses SuSE? Then surely SuSE developers are customers themselves?

---

### Post by Adamant1988 on 2007-04-11
> **mstlyevil said:**
> I have read the deal and the agreement is to indemnify each other from being sued on each others patents.

Ok, where did you read it? Because my interpretation (and the interpretation of various financial analysts, lawyers, etc. that keep blogs on this kind of thing) is that Microsoft can sue Novell, just not their CUSTOMERS.  I'll go back and re-read the deal just to double-up, but I'm fairly certain no where in there does it say "Microsoft promises not to sue Novell!" but rather, "Microsoft promises not to sue Novell's customers, and vice versa" (paraphrased)

---

### Post by igknighted on 2007-04-11
> **Sunnz said:**
> So they don't sue Novell customers. But who are considered as customers? Whoever uses SuSE? Then surely SuSE developers are customers themselves?

I don't think the deal covers "opensuse" at all, just SLES/SLED.  In which case customers are everyone who pays for the distro.

---

### Post by Adamant1988 on 2007-04-11
> **igknighted said:**
> I don't think the deal covers "opensuse" at all, just SLES/SLED.  In which case customers are everyone who pays for the distro.

Hrmm, well, Novell does actually box and sell openSuSE (See their website) as a home product, so I assume if you pay for it, you're protected.

---

### Post by igknighted on 2007-04-11
> **Adamant1988 said:**
> Hrmm, well, Novell does actually box and sell openSuSE (See their website) as a home product, so I assume if you pay for it, you're protected.

True, I suppose that would likely be covered as well

---

### Post by mstlyevil on 2007-04-11
> **Adamant1988 said:**
> Ok, where did you read it? Because my interpretation (and the interpretation of various financial analysts, lawyers, etc. that keep blogs on this kind of thing) is that Microsoft can sue Novell, just not their CUSTOMERS.  I'll go back and re-read the deal just to double-up, but I'm fairly certain no where in there does it say "Microsoft promises not to sue Novell!" but rather, "Microsoft promises not to sue Novell's customers, and vice versa" (paraphrased)

Suing Novells customers is the same as suing Novell since they already promised to protect their own customers from lawsuits. A lawsuit against their customers would be far more costly than being sued directly. So my interpretation stands.

---

### Post by Sunnz on 2007-04-11
> **mstlyevil said:**
> Suing Novells customers is the same as suing Novell since they already promised to protect their own customers from lawsuits. A lawsuit against their customers would be far more costly than being sued directly. So my interpretation stands.
Well done!!! You have just give a very valid reason on why M$ shouldn't sue Novell customers!!!

---

### Post by darkhatter on 2007-04-11
> **mstlyevil said:**
> I understand the deal. The deal is I don't sue you and you don't sue me. You sell my products and here is some cash to keep you off my back.

That is called paying protection money pure and simple.

I thought it was you don't sue my customers I don't sue yours

> **graabein said:**
> No relation other than I read your [bloodninja]("http://www.ebooger.com/2005/08/bloodninja-his-robe-and-wizard-hat.html") quote darkhatter -- *I put on my robe and wizard hat* -- Then I see raublekick's avatar with the orange plastic bucket... That's pretty funny huh?

On topic: Fonts are important!

thats my sig, I stole the quote from that story, but mine was found on bash

[http://www.bash.org/?104383](http://www.bash.org/?104383)

---

