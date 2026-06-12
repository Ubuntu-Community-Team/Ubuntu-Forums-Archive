---
title: "KHTML + Firefox?"
date: 2006-10-28
forum: The Cafe
---

### Post by Sunnz on 2006-10-28
This idea just pops up in my head...

Well, I have been using Firefox for a while now, I liked its interface and about:config and how extensions and be easily written and stuff... but its Gecko engine is huge and slow and just isn't as up to date as other ones, like khtml...

So yea, do you think it is possible to "swap" the html parsing/rendering engines used in Firefox, as in plugging in the khtml in it instead of Gecko?

---

### Post by banjobacon on 2006-10-28
Firefox's interface is XUL-based, which requires Gecko, so probably not.

---

### Post by kripkenstein on 2006-10-28
Google for it, a proof-of-concept was made a while back. So this is possible, but it is so much work that it will probably not be done in the forseeable future.

---

### Post by mostwanted on 2006-10-28
Gecko renders the entire Firefox interface (with additional native GUI elements) and provides the JavaScript back-end for Firefox extensions. Take away Gecko and you take away the foundation of Firefox.

---

### Post by chaosgeisterchen on 2006-10-28
You could more easily realize Konqueror with a good plugin interface (which are written in popular languages just as Python or Ruby)

---

### Post by mostwanted on 2006-10-28
> **chaosgeisterchen said:**
> You could more easily realize Konqueror with a good plugin interface (which are written in popular languages just as Python or Ruby)

You mean "(...) like Python or Ruby". Using "as" in that sentence gives the impression that the languages Ruby and Python have a good plugin interface (whatever that means in relation to a programming language), not that the plugins for Konqueror are written in Python and Ruby.

:)

Sorry for being a grammar nazi.

---

### Post by chaosgeisterchen on 2006-10-28
I was already thinking hard about the sentence as it seemed corrupted to me. Thanks for correcting me, I am a grammar nazi as well (concerning German) - in English I am far away from being good enough for it.

But criticism makes it better.

---

### Post by .t. on 2006-10-28
But, as I said in a thread with you before, German is much stricter!

---

### Post by Virogenesis on 2006-10-28
like been said before, firefox uses gecko, a gtk version of khtml did exist, but don't know what happened to the project.

Heres the url.

[http://gtk-webcore.sourceforge.net/](http://gtk-webcore.sourceforge.net/)

---

### Post by maniacmusician on 2006-10-28
is it gecko itself that's heavy or is it the firefox associations that it has? I'd rather pop the gecko rendering engine into Konqueror. Konqui has the interface I want, but KHTML gives me a lot of problems.

---

### Post by Virogenesis on 2006-10-28
maniacmusician, I believe its xul thats heavy, could be wrong but many have stated in the past that epiphany is lighter, reason why this could be the case is that epiphany doesn't use xul instead it uses native gtk widgets.
Removing xul would take away some of the key things about firefox for instance the extensions.

---

### Post by GeneralZod on 2006-10-29
> **chaosgeisterchen said:**
> You could more easily realize Konqueror with a good plugin interface (which are written in popular languages just as Python or Ruby)

Hopefully "Kross" will be used for this on KDE4.  I've no idea whether there are any plans to integrate Kross into Konqueror, but it seems like an obvious idea to me.

Javascript is more likely to be used than Python or Ruby for the time being as I believe the latter two have unproven sandboxing features, which are of course essential from a security point of view.

---

