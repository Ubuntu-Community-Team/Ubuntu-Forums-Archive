---
title: "Dictionary language, independent of system language"
date: 2008-01-18
forum: Ubuntu Brainstorm
---

### Post by Bou on 2008-01-18
Hi,

I'm a Spanish speaker and so is everyone else who uses my computer, so I like my system to be in Spanish. I and my bunch just feel more comfortable that way.

However, I often find myself doing stuff in English, like posting to these forums, chatting on IRC or taking notes in Tomboy. What's more, I often have to switch between both languages once and again.

I wish there was an easy method to select one (or better, more than one) spell dictionaries that were independent of your system language.

---

### Post by AlKhatib on 2008-01-18
An application that allows different input languages per application, pretty much like pulse audio allows per application control?

Should be interesting. You got my vote!

---

### Post by Bou on 2008-01-18
I have filed this bug in language-support:

[https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/184028](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/184028)

[IMG]http://img267.imageshack.us/img267/7199/pantallazo1ob7.png[/IMG]

> I have made a mockup how how this idea could be implemented: the interface of the language selector would be the same, only with a second "spell check" column. Only languages with their first column checked (that is, installed languages) would have their second column available, all others would have the second checkbox greyed out.

In the mockup English, Esperanto and Estonian are installed but only English and Estonian have spell checking activated. Esperanto is available as a system language but words won't be checked in Esperanto. About Zdongkha and Faroese, they're not even installed so the spellcheck checkbox is greyed out.

By default, only the default language would be checked for spellcheck. But the user could easily check other languages.

What do you guys think of it?

---

### Post by smartboyathome on 2008-01-18
I like it. I think it is a good idea. :)

---

### Post by mangar on 2008-01-18
instead of making it an explicit option, whatr about activating the 
dictionary according to the active language?
meaning - if the active language is X (using the language switcher applet/key combination) than the active dictionary will be the one for language X. (I don't really know how it is implemented currently, as my native language does not have an active dictionary in ubuntu).

---

### Post by Bou on 2008-01-18
> **mangar said:**
> instead of making it an explicit option, whatr about activating the dictionary according to the active language?

That's how it's done now, but you can only use one dictionary at a time (that is, you need to log out to change dictionaries) and have to change the system language if you want to use another dictionary.

That's hardly ideal.

---

### Post by mangar on 2008-01-18
On my machine, alt-Caps changes the active input language for the active application. Does changing the active input language changes the active dictionary?

(if not, that's probably a bug)

---

