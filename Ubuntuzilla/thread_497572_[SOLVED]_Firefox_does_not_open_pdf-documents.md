---
title: "[SOLVED] Firefox does not open pdf-documents"
date: 2007-07-10
forum: Ubuntuzilla
---

### Post by ingridt on 2007-07-10
When clicking a link to a pdf document in Firefox 2 (installed with the ubuntuzilla-script) I can choose to save it to disk or to browse for a program to open it.

When it is saved I simply click on it and it opens in KPDF 0.5.2. (using KDE 3.5.2), but I do not always want to save fist, you see.

Where can I find the program that will open the file? I do not know  the way outside the /home directory.

---

### Post by moore.bryan on 2007-07-10
*you would choose to browse, head over to /usr/bin/kpdf, and voila!*

---

### Post by nanotube on 2007-07-10
as moore.bryan says, kpdf is in /usr/bin/kpdf
so when it says browse, just find that. :)

---

### Post by nanotube on 2007-07-10
oh, by the way, is there any particular reason you chose to install 6.06 instead of the latest 7.04 of ubuntu?

---

### Post by ingridt on 2007-07-11
if everything was to be solved as easy as that!

I chose 6.06 because I had a CD ready (from a magazine from quite a while ago) while my computer just had a hard disk crash and needed a new "C:-drive" (it was windows before the crash).

And I had read something about the time this version will stay supported - I like computer-stuff, but I am a bit fed up with installing and configuration  things. So if a new install can be postponed I am happy to use the stuff I have. 

PS
some things do not come out of the box, which gives me still install and configuration fuss > if it was not for this, I would tell all my friends to move to kubuntu instead of buying a new PC when windows becomes too slow.

---

### Post by Bharath Krishnan on 2007-07-28
I have a really strange problem. I installed the adobe pdf plugin (blame it on automatix), but I didn't like it. So I just uninstalled it and now pdfs won't open. I don't even get the the option to download or open using a program. Instead, I just get an pop up window saying that the PATH variable to adobe is not set. How do I just revert to how it was?

---

### Post by stinger30au on 2007-07-28
> **ingridt said:**
> When clicking a link to a pdf document in Firefox 2 (installed with the ubuntuzilla-script) I can choose to save it to disk or to browse for a program to open it.

When it is saved I simply click on it and it opens in KPDF 0.5.2. (using KDE 3.5.2), but I do not always want to save fist, you see.

Where can I find the program that will open the file? I do not know  the way outside the /home directory.

im sure if you go hunthing thru the firefox addons at the mozilla site there is one there that will do what you want

infact here it is

[https://addons.mozilla.org/en-US/firefox/addon/636](https://addons.mozilla.org/en-US/firefox/addon/636)

---

### Post by nanotube on 2007-07-29
> **Bharath Krishnan said:**
> I have a really strange problem. I installed the adobe pdf plugin (blame it on automatix), but I didn't like it. So I just uninstalled it and now pdfs won't open. I don't even get the the option to download or open using a program. Instead, I just get an pop up window saying that the PATH variable to adobe is not set. How do I just revert to how it was?

are you using the repos version of firefox, or the official mozilla version?

what is the exact text of the pop up?

do you have anything pdf-related listed in the "about:plugins" page for firefox?

---

