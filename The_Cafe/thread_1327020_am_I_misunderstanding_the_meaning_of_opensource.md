---
title: "am I misunderstanding the meaning of opensource?"
date: 2009-11-15
forum: The Cafe
---

### Post by jdrodrig on 2009-11-15
I recently came across an article on "The Economist" a magazine I normally respect for their work, but in this piece about EU blocking Oracle-Sun deal it says:

"Although MySQL and its underlying recipe are available free, any added code built around the open-source product must also be made open source. Most firms that develop products on top of MySQL prefer to buy a commercial licence that does not come with this obligation"

I always thought that if you modify, in this case MySQL, then you most release that code back to the community; but if I write, say an Excel/Word/PowerPoint Macro that calls MySQL to do some operations, do I need to publish such Macro as well?

I think that article is taking the concept of "code built around ..." too vaguely...am I missing something?

---

### Post by RiceMonster on 2009-11-15
No, you only need to release changes to the MySQL code. An Excel Macro is not part of it.

---

### Post by Tomone on 2009-11-15
Whether or not you have to release the code back has to do with the licensing of the original code, not the fact that it's open source. Different open source licenses differ in many ways, including the requirements of releasing code. I don't know how MySQL is licensed, but that's what the part you quoted references.

---

### Post by koenn on 2009-11-15
> **jdrodrig said:**
> 

I always thought that if you modify, in this case MySQL, then you most release that code back to the community; but if I write, say an Excel/Word/PowerPoint Macro that calls MySQL to do some operations, do I need to publish such Macro as well?

I think that article is taking the concept of "code built around ..." too vaguely...am I missing something?
You're right that this "code build around" is way too vague. In the example of your Macro, it's clear you're free to license it how you see fit. But if you'd build a program that re-uses mysql-client code or libraries, or an application or even an appliance with an embedded mysql database, things might be different. That's probably what they're refering to. 
This gets very technical then, because it depends
a/ on the exact licensing terms of each component you re-use
b/ on the way your software interacts with the re-used code / programs/ components...

---

### Post by jdrodrig on 2009-11-18
Thanks for all your replies. For sure licenses are complex objects that business should pay attention too. I just thought that the article provided a disservice to the potential opensource users, scaring them to think that they have to release anything that they build using opensource code in general.

---

### Post by Frak on 2009-11-18
If they modify the code in-house, they aren't required to release the source back. They only do that if they distribute it to someone else.

---

### Post by jdrodrig on 2009-11-18
> **Frak said:**
> If they modify the code in-house, they aren't required to release the source back. They only do that if they distribute it to someone else.

interesting...for instance, I remember a few months back there was this "rumor" that google used internally their own version of ubuntu (googlebuntu?).... if they actually modified the OS to their liking, they will not be forced to distribute it as long as it was used only in their offices...

---

### Post by Frak on 2009-11-18
> **jdrodrig said:**
> interesting...for instance, I remember a few months back there was this "rumor" that google used internally their own version of ubuntu (googlebuntu?).... if they actually modified the OS to their liking, they will not be forced to distribute it as long as it was used only in their offices...
There's probably some provisions I'm not aware of, but yeah, don't release it, you don't have to release the source or modifications.

---

