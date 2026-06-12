---
title: "What exactly is OpenJDK and IcedTea?"
date: 2009-08-30
forum: The Cafe
---

### Post by keiichidono on 2009-08-30
I'm reading the Wikipedia pages of both and they don't seem to be different at all. OpenJDK is open source, except for 1%, and IcedTea is fully open source made with open source software. I want to use fully open source software so do i use IcedTea or is OpenJDK the same? Also, why is there an IcedTea6 and OpenJDK6? :confused:

---

### Post by hanzomon4 on 2009-08-30
I believe IcedTea is an implementation of OpenJDK

---

### Post by keiichidono on 2009-08-30
> **hanzomon4 said:**
> I believe IcedTea is an implementation of OpenJDK

That is fully open source?

---

### Post by hanzomon4 on 2009-08-30
Yeah it was made by redhat I believe

---

### Post by keiichidono on 2009-08-30
So even though i may choose IcedTea because i want to use what's more open, i still haven't had my question of why is there an IcedTea6 and OpenJDK6 and what the difference between these two new versions are.

---

### Post by keiichidono on 2009-08-30
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
if no.reply=true then
{bump}
if false then
{solved}
</>

---

### Post by keiichidono on 2009-08-30
{bump}

---

### Post by Jimleko211 on 2009-08-30
As far as I understand it, IcedTea and OpenJDK are really not that different, kind of like the difference between Firefox and IceWeasel (or whatever the name is now).  As for IcedTea6 and OpenJDK6, I believe that that means it's compatible with Java 6, which is the current version of Java.  If not, it's just version numbers...or both may apply.

---

### Post by keiichidono on 2009-08-30
> **Jimleko211 said:**
> As far as I understand it, IcedTea and OpenJDK are really not that different, kind of like the difference between Firefox and IceWeasel (or whatever the name is now).  As for IcedTea6 and OpenJDK6, I believe that that means it's compatible with Java 6, which is the current version of Java.  If not, it's just version numbers...or both may apply.

It's certainly not a naming issue so that's kind of a bad analogy. I kinda get what you're saying but I'd rather use IcedTea because it's more free than OpenJDK as far as I can tell.

---

### Post by Jimleko211 on 2009-08-30
I'd suggest googling it, but the only thing relevant that pops up is the post I just posted.

From the article on Wikipedia:
The goal is to make the [OpenJDK]("http://en.wikipedia.org/wiki/OpenJDK") software which [Sun Microsystems]("http://en.wikipedia.org/wiki/Sun_Microsystems") released as [free software]("http://en.wikipedia.org/wiki/Free_software") in 2007 usable without requiring any other software that is not free software

---

### Post by keiichidono on 2009-08-30
That's great then, it's free software that only requires free software. Nothing bad about that.

---

### Post by fwendt on 2011-01-01
> **keiichidono said:**
> I'm reading the Wikipedia pages of both and they don't seem to be different at all. OpenJDK is open source, except for 1%, and IcedTea is fully open source made with open source software. I want to use fully open source software so do i use IcedTea or is OpenJDK the same? Also, why is there an IcedTea6 and OpenJDK6? :confused:

OpenJDK6 is an attempt to create a "Free" Java implementation. However, to build OpenJDK you're normally required to use some non-free tools. IcedTea is an attempt to replace those build tools with free alternatives, and thereby making it possible to create a truly free OpenJDK build.

---

