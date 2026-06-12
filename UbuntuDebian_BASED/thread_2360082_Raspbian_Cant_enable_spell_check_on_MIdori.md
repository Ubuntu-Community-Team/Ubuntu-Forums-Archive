---
title: "Raspbian: Cant enable spell check on MIdori"
date: 2017-05-01
forum: Ubuntu/Debian BASED
---

### Post by linuxyogi on 2017-05-01
[ATTACH=CONFIG]274895[/ATTACH]

Cant enable spell checking on Midori. Any ideas ?

---

### Post by #&amp;thj^% on 2017-05-01
You'll have to go Midori, and 'add' Spell-Check to the browser

Browser > Preferences > Extensions > Add (click on ) Spell-Check

In the meantime, forget the built-in spell check and just install a different dictionary. I prefer hunspell, but there's others out there. A good mini-guide on setting up the aspell dictionary is available in the FAQ. Once you have a dictionary installed in your preferred language, go into your uzbl config and add the following two variables:

set enable_spellcheck            = 1
# You'll have to specify what language uzbl should use.
# Use the "spellcheck_languages" variable for this and give it your language choice in lang_COUNTRY form
# I'll just use en_US, but you can have more than one. As long as you separate them with a comma.
set spellcheck_languages         = en_US

---

### Post by linuxyogi on 2017-05-01
> **1fallen said:**
> You'll have to go Midori, and 'add' Spell-Check to the browser

Browser > Preferences > Extensions > Add (click on ) Spell-Check

In the meantime, forget the built-in spell check and just install a different dictionary. I prefer hunspell, but there's others out there. A good mini-guide on setting up the aspell dictionary is available in the FAQ. Once you have a dictionary installed in your preferred language, go into your uzbl config and add the following two variables:

set enable_spellcheck            = 1
# You'll have to specify what language uzbl should use.
# Use the "spellcheck_languages" variable for this and give it your language choice in lang_COUNTRY form
# I'll just use en_US, but you can have more than one. As long as you separate them with a comma.
set spellcheck_languages         = en_US

Browser > Preferences > Extensions > Add (click on ) Spell-Check

^^ There is no Spell-Check under the extensions menu.
I have already installed the hunspell-en-us but the spell check option in MIdori is still grayed out.

---

### Post by #&amp;thj^% on 2017-05-01
Curious...what version do you have?
Edit: I also have apsell and aspell-en installed.

---

### Post by linuxyogi on 2017-05-01
> **1fallen said:**
> Curious...what version do you have?

Midori 0.4.3

---

### Post by #&amp;thj^% on 2017-05-01
> **linuxyogi said:**
> Midori 0.4.3

I remember a few bad bugs with that version.
You may need to upgrade to 0.5.11
But check that you have "aspell && aspell-en" installed first to check again.

---

### Post by linuxyogi on 2017-05-01
> I also have apsell and aspell-en installed.

These is no apsell or apsell-en in the Raspbian repos.

---

### Post by #&amp;thj^% on 2017-05-01
> **linuxyogi said:**
> These is no apsell or apsell-en in the Raspbian repos.

This would have been a good thing to know **(Raspbian) **at the beginning.
I have nothing more to advise.

---

### Post by linuxyogi on 2017-05-05
Upgraded to the testing branch. Spell check works now.

---

### Post by vasa1 on 2017-05-05
> **1fallen said:**
> This would have been a good thing to know **(Raspbian) **at the beginning.
 ...
+1. I wonder why this information is not provided in the first place :(

---

### Post by linuxyogi on 2017-05-05
I thought since I am posting in the Ubuntu/Debian based forum and Raspbian is Debian based I can skip mentioning that. From now on I will mention it. Sorry about the confusion.

---

### Post by QIII on 2017-05-05
The more detail you provide up front, the fewer questions have to be asked, the more accurate the diagnosis and the more effective the advice.

In this case, not only does Raspbian indicate the specific distro, but there is implicit in that an idea of the hardware.

---

