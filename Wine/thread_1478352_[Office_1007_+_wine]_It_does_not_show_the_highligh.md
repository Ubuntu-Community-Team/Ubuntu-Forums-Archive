---
title: "[Office 1007 + wine] It does not show the highlight color when I select a text?"
date: 2010-05-09
forum: Wine
---

### Post by legolas_w on 2010-05-09
Hi.

I have an strange problem with office 2007 and lucid lynx.
When I open a doc file and select a text it does not show the additional highlight color so I can recognize whether I selected the text I meant to or some words characters are missing.

Any suggestion on what can cause this? I kept my home partition from 9.10 and performed a clean install of 10.4. The wine is wine-1.1.43 and I am using 64 bits OS.


Thanks.

---

### Post by LeStato on 2010-05-10
I have a similar problem. When i select text by mouse it doesn't highlight to me but i can format this text.
I performed a clean installation of ubuntu 10.4 32 bit. Wine version is 1.1.43. Additional libraries installed in wine is riched20, riched32 and usp10.

---

### Post by legolas_w on 2010-05-10
Hope we find a solution for this. It is really annoying.

Do you know whether the cedega or other paid products works correctly or not?


thanks

---

### Post by LeStato on 2010-05-10
> **legolas_w said:**
> Hope we find a solution for this. It is really annoying.

Do you know whether the cedega or other paid products works correctly or not?


thanks

This problem was confirmed bug "Bug 22453 - Office 2007 text is not visibily highlighted". It was fixed in version 1.1.44 of wine.
I updated to this version and now i can select text :) 
I hope this will help you too.

---

