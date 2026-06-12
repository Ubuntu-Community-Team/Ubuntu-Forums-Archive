---
title: "Make life easier for developers"
date: 2008-10-23
forum: Ubuntu Brainstorm
---

### Post by DrMega on 2008-10-23
Here's my idea to make Linux (not just Ubuntu but other distros too), even more brilliant.

We all know that sometimes things don't work for some people. This forum, others like it, and launchpad are proof of that.

The trouble is, as a developer myself (albeit on Windows, not Linux), I know that a good bug report is a rare gem. You can't blame ordinary users though, if they don't have a good technical background they simply don't know how to make a good report.

Why don't we have a new facility, either on this forum or as a seperate desktop app, that helps people make a good bug report?

What I envisage is some sort of form, into which they detail, in seperate fields (and from drop down lists) things like the make and model of their motherboard, graphics card, which driver they are using, kernel version, desktop environment etc. Then you could have drop down lists for the category of problem they encountered, like Freeze up, app failed to start etc. You could also have free text fields for answers to specific questions such as "what were you running at the time?", "What were the error messages/consult output you saw?" etc. Finally some free text for any more info.

All this info would go into a big database that developers could search, so they could look for common factors in specific bugs etc.

I know we have the forums, but if you have to wade through pages and pages of text, which may or may not be all in the same thread, and may include red herrings and on occassion inconclusive resolutions, it is not the most clear way to pick out the facts.

As for gathering the necessary details, perhaps a desktop utility could gather the key details of your config and stick it in an XML file for upload.

---

### Post by smartboyathome on 2008-10-23
We already have this, Starting with Hardy, we got apport which allows users to report a bug when a program crashes. I think this could be expanded to an item in the "System" menu which says "Report a bug", and then the user could fill out all the "necessary" info, and the computer would fetch the rest.

---

### Post by bruce89 on 2008-10-23
> **smartboyathome said:**
> We already have this, Starting with Hardy, we got apport which allows users to report a bug when a program crashes.

apport has been around since Gutsy actually.

I find it fairly useless, when you want to debug a crash, it doesn't bother itself. When you don't care, it works.

Also, only brain implants would make people file good bug reports.

---

### Post by DrMega on 2008-10-24
> **bruce89 said:**
> apport has been around since Gutsy actually.

I find it fairly useless, when you want to debug a crash, it doesn't bother itself. When you don't care, it works.

Also, only brain implants would make people file good bug reports.

At my place of work, through years of education and an official stance that we will ignore any reports that lack the necessary info (and an unofficial stance that we don't ignore them), we have got our userbase making out fairly good reports these days. It makes our life so much easier when instead of say "it crashed out", they say something like "it raised error message 'so and so' when I tried to update the 'x' on reference number y".

---

### Post by neighborlee on 2008-10-28
> **smartboyathome said:**
> We already have this, Starting with Hardy, we got apport which allows users to report a bug when a program crashes. I think this could be expanded to an item in the "System" menu which says "Report a bug", and then the user could fill out all the "necessary" info, and the computer would fetch the rest.

I read at [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport), that apport isn't enabled out of box on 'stable releases'..considering the huge #'s of hardware/software out there that the various users use, why would this be left disabled on stable releases ?? :)

cheers
nl

---

