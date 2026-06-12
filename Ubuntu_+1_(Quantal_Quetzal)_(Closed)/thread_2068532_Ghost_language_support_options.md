---
title: "Ghost language support options"
date: 2012-10-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pressureman on 2012-10-09
Ok, this has intrigued me since installing this system from the beta1 CD a few weeks back.

In System Settings > Language Support, I noticed what appeared to be Chinese characters at the bottom of the list of "Language for menu and windows". I don't know how it got there, because I installed this system as English. Chinese options also appear in the Regional Formats, and in the Keyboard Layout settings app. Let me emphasize, **no Chinese language packs were installed on the system**.

For fun, I thought I'd try installing a Chinese language pack, then remove it, in case during the building of the beta1 CD it hadn't been purged. After removing the language pack, I now have even more Chinese options - presumably simplified and traditional.

So.... where the heck are these Chinese language options being cached, and why are the settings apps showing support for languages that have been purged?

Incidentally, I have not yet found a way to have a user account with a locale that is different to the system locale. I just can't get it to work. Am I the only one who finds quantal's multi-language support quite buggy?

---

### Post by dino99 on 2012-10-09
I have had such issue but it was a while back during alpha. When you open the language list to set your locale and system language:
- set the language you want to use on top , then click "apply"
- do the same for locale.

Inside dconf-editor, are you having your previously set language : System -> locale -> area ; you should have your utf8 language.

But i agree that trying to add a second/third language(s) and switching them is a real problem; i've never been able to set russian language as a second language for example. Some time ago there was issue with unicode, but i suppose that ascii 1205 is an other non resolved one.

---

### Post by ventrical on 2012-10-09
Does it matter if I go ahead and install these?

---

### Post by grahammechanical on 2012-10-09
As well as those Chinese characters at the bottom of that Language Support list you may also find that there are Chinese fonts in Libreoffice. Why? Who knows? In fact there are quite a few language fonts in Libreoffice that seem to come as standard.

Regards.

---

### Post by pressureman on 2012-10-09
> **grahammechanical said:**
> As well as those Chinese characters at the bottom of that Language Support list you may also find that there are Chinese fonts in Libreoffice. Why? Who knows? In fact there are quite a few language fonts in Libreoffice that seem to come as standard.

I think you're referring to something different. Ubuntu has always shipped by default a variety of non-latin character set fonts, presumably so that you don't get square blocks instead of characters when viewing non-latin web pages.

What I'm talking about is something recent. I have another install which I had installed from the alternate CD (before it was discontinued), and that has no traces of these ghost Chinese language choices.

---

### Post by funicorn on 2012-10-10
dpkg -l | grep '^rc' | awk '{print $2}' | sudo xargs dpkg --purge

---

### Post by pressureman on 2012-10-11
> **funicorn said:**
> dpkg -l | grep '^rc' | awk '{print $2}' | sudo xargs dpkg --purge

Already done that. Read my sig. I'm not exactly a n00b.

---

