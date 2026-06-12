---
title: "what is the difference?"
date: 2006-07-27
forum: The Cafe
---

### Post by TheRingmaster on 2006-07-27
I wanted to know the difference between the mozilla and ubuntu versions of firefox. There has been a lot of talk lately about these two versions.

---

### Post by mostwanted on 2006-07-27
The Ubuntu version uses Pango (the Gnome/Gtk+ text renderer) to render text on websites, the Mozilla version just uses Gecko I suppose. The difference isn't all that great, I suppose the Pango method is more integrated with the rest of Gnome in the way it presents text (conforms to your font settings, highlights same way as in other Gnome apps), but it also comes with a performance penalty.

---

### Post by TheRingmaster on 2006-07-27
So you are saying that ubuntu's version of firefox doesn't use gecko. Then why does it say "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.4) **Gecko**/20060608 Ubuntu/dapper-security Firefox/1.5.0.4" in the about firefox menu?

---

### Post by Lord Illidan on 2006-07-27
> **jpazindustries said:**
> So you are saying that ubuntu's version of firefox doesn't use gecko. Then why does it say "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.4) **Gecko**/20060608 Ubuntu/dapper-security Firefox/1.5.0.4" in the about firefox menu?

It uses Gecko to render the page, but not the text, which it leaves to pango, is what I'm gessing mostwanted meant to say.

---

### Post by TheRingmaster on 2006-07-27
do I have to uninstall the ubuntu version **before** installing the mozilla version?

---

### Post by Lord Illidan on 2006-07-27
Not necessarily. 

Just remember that if you unpack firefox to your /home directory.

Say, under /home/jpazindustries/software/firefox, you have to do 

```
/home/jpazindustries/software/firefox/firefox
``` to run the Mozilla version instead of typing firefox in a terminal. You can circumvent this by changing the firefox icon in the gnome menu. Change its command to the one above, and use that.

---

### Post by mostwanted on 2006-07-27
> **Lord Illidan said:**
> It uses Gecko to render the page, but not the text, which it leaves to pango, is what I'm gessing mostwanted meant to say.

Yes, that's not only what I meant to say, it's what I DID say :)

---

### Post by Lord Illidan on 2006-07-27
> **mostwanted said:**
> Yes, that's not only what I meant to say, it's what I DID say :)
My humble apologies..:D

---

### Post by Jucato on 2006-07-27
Do not uninstall Ubuntu's Firefox version. Some programs are dependent on it, like Yelp. Removing it will break dependencies.

You can install the "real" Firefox version while keeping the Ubuntu version, just like what Lord Illidan described.

---

