---
title: "QuoteMarks Firefox ext: save and paste forum quotes, apply bbcode to text and more..."
date: 2010-04-04
forum: The Cafe
---

### Post by lovinglinux on 2010-04-04
Quotemarks will no longer be developed.

---

### Post by lovinglinux on 2010-04-04
Edit

---

### Post by brucemartin on 2010-04-05
very nice extension, thanks. while i don't find any use for the quote function, the templates feature is great :D

---

### Post by lovinglinux on 2010-04-05
> **brucemartin said:**
> very nice extension, thanks. while i don't find any use for the quote function, the templates feature is great :D

Thank you. The quote function is useful for those who give a lot of tech support here. There are several recurring questions every day, so it saves a lot of time locating the proper reply or writing them all over again.

Like all my other extensions, I wrote QuoteMarks to make my life easier :)

Please let me know if you have any suggestions or if you find any bugs.

---

### Post by wojox on 2010-04-05
> **brucemartin said:**
> very nice extension, thanks. while i don't find any use for the quote function, the templates feature is great :D

Here's a quote of brucemartins quote.

---

### Post by lovinglinux on 2010-04-05
> **wojox said:**
> Here's a quote of brucemartins quote.

:)

Do you think would be nice to include an option to remove the footer completely, not only the "Powered by" line?

---

### Post by wojox on 2010-04-05
> **lovinglinux said:**
> :)

Do you think would be nice to include an option to remove the footer completely, not only the "Powered by" line?

Sure. Where does it keep this info? I looked around in /home/wojox/.mozilla/firefox/xrv8iugk.default/extensions/quotemarks@lovinglinux.megabyet.net but don't see it. If I run bleachbit will it clean out my saved quotes? I'll mess around with it today and get back with you.

---

### Post by wojox on 2010-04-05
I see in the sidebar now you can edit, delete stuff. Pretty cool.

---

### Post by lovinglinux on 2010-04-05
> **wojox said:**
> Sure.

Working on it as we speak.

> **wojox said:**
> Sure. Where does it keep this info? I looked around in /home/wojox/.mozilla/firefox/xrv8iugk.default/extensions/quotemarks@lovinglinux.megabyet.net but don't see it. If I run bleachbit will it clean out my saved quotes? I'll mess around with it today and get back with you.

All information is stored in the **quotemark.sqlite** database in your Firefox profile root. I never used bleashbit, but from what I see it won't delete the quotes database. You can backup the database file if you need and simply replace the file to restore it.

> **wojox said:**
> I see in the sidebar now you can edit, delete stuff. Pretty cool.

You can also add a button to the main toolbar, to open the sidebar easily, nevertheless, the context menu also offers this option.

---

### Post by Psumi on 2010-04-05
Have one for newgrounds or deviantart?

They take HTML, not BBCode. ;)

---

### Post by lovinglinux on 2010-04-05
> **Psumi said:**
> Have one for newgrounds or deviantart?

They take HTML, not BBCode. ;)

The template feature can do HTML too, but not the quote manager. 

Wouldn't be hard to make possible to quote and paste HTML, but crossing over quotes from a BBcode forum and a HTML forum would be more complicated.

I'm going to consider this for the next version.

---

### Post by lovinglinux on 2010-04-05
I have uploaded a new version that handles quotes differently. You can save bbcode, html and text quotes from any web site. To do that you need to select the text from a quote form, not from the displayed post. It will store the content of the quote with original tags and will properly paste them. Pasting quotes from different sites might not work as expected, due to differences in tag standards.

On ubuntuforums you can't save the quote by selecting the text, just using the "save quote" button.

This version also offers options to select the footer contents, no only the credits.

> **Psumi said:**
> Have one for newgrounds or deviantart?

They take HTML, not BBCode. ;)

Please test if the new version works fine on those sites. You will need to manually edit title, author and tags before saving the quotes.

---

### Post by Psumi on 2010-04-05
> **lovinglinux said:**
> Please test if the new version works fine on those sites. You will need to manually edit title, author and tags before saving the quotes.

I use midori, sorry.

---

### Post by lovinglinux on 2010-04-05
> **Psumi said:**
> I use midori, sorry.

Well, you asked for making the extension compatible with them.

---

### Post by Psumi on 2010-04-05
> **lovinglinux said:**
> Well, you asked for making the extension compatible with them.

No I didn't. I asked if it was compatible with HTML code.

---

### Post by lovinglinux on 2010-04-05
> **Psumi said:**
> No I didn't. I asked if it was compatible with HTML code.

I guess I misunderstood your post and presumed you needed HTML support for those sites. Anyway, it is compatible with HTML now ;)

---

### Post by lovinglinux on 2010-04-15
QuoteMarks has been approved by Mozilla, so now you can get updates automatically from Firefox add-ons manager. Please install the newest version (released today) to make sure you will get future updates.

---

