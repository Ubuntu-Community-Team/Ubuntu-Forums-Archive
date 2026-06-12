---
title: "LibreOffice Paper Size Format"
date: 2011-06-25
forum: The Cafe
---

### Post by badaveil on 2011-06-25
Without resorting to saving a template, is there any way to set the default paper size from Letter to A4 so that it automatically sets to A4 every time text document opens? I was told the default setting is based on the OS locale setting. The thing is my locale setting is Kuala Lumpur, Malaysia and metric has been the official norm since 1980 so how does one inform LibreOffice developers to change that?

---

### Post by 73ckn797 on 2011-06-26
Have you looked at the Open Office help forums? The current "Document Foundation" which is LibreOffie does not have a forum yet (at least as far as I can tell) but there may be an answer in the OO forums.

[http://support.openoffice.org/index.html](http://support.openoffice.org/index.html)

---

### Post by LowSky on 2011-06-26
this should put you on the right track
[http://wiki.documentfoundation.org/Documentation#Getting_Started_with_LibreOffice](http://wiki.documentfoundation.org/Documentation#Getting_Started_with_LibreOffice)

---

### Post by badaveil on 2011-06-29
> **LowSky said:**
> this should put you on the right track
[http://wiki.documentfoundation.org/Documentation#Getting_Started_with_LibreOffice](http://wiki.documentfoundation.org/Documentation#Getting_Started_with_LibreOffice)

My, this is an excellent reference:shock:

---

### Post by koleoptero on 2011-06-29
> **badaveil said:**
> my, this is an excellent reference:shock:

+1

---

### Post by Michal77 on 2012-07-20
I was struggling with this one for a wile, but solution it's very simply:
edit file /etc/paperesize, just put there size you require
a4, letter etc
Reboot and all applications will use the same paper format. At the end you should check printer settings, if it use also the same format.

If for some reason you don't have this file, them install: libpaper 

M.

---

