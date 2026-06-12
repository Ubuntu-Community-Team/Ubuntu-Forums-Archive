---
title: "GPL question"
date: 2007-03-11
forum: The Cafe
---

### Post by naerae on 2007-03-11
Hello. If I use a part of GPL licenced material in my project , do I have to release my project in GPL? For example, If I use a picture from Wikipedia which is GPL licenced ,  ought the rest of the project  ,which is not constituting any GPL licenced material, released also in GPL? 
Thanks.

---

### Post by IYY on 2007-03-11
You can use the GPL item in your project without licensing your project under the GPL *unless* you make modifications to the object. For example, you can have some sort of a hardware system that uses Linux and runs a few proprietary apps on top of it, but the changes made by the company to Linux itself must be released. 

So, if your project is a programming project, and you borrow GPL licensed *code*, your entire project will have to be GPL.

---

### Post by naerae on 2007-03-11
> **IYY said:**
> You can use the GPL item in your project without licensing your project under the GPL *unless* you make modifications to the object. For example, you can have some sort of a hardware system that uses Linux and runs a few proprietary apps on top of it, but the changes made by the company to Linux itself must be released. 

So, if your project is a programming project, and you borrow GPL licensed *code*, your entire project will have to be GPL.

I am sorry I havent yet understood completely . Does GPL only apply to program codes? If not I cannot borrow any picture from wikipedia. If I do, then I have to release my project under GPL according to your explanation above. It is the same way as borrowing a linux program into a new os project. Am I wrong?

---

### Post by Tomosaur on 2007-03-11
Have you actually read the GPL? It's not too long, and it's pretty easy to understand:
[Full GPL text here](http://www.gnu.org/licenses/gpl.txt). Basically - you can't relicence GPLd code. You cannot take GPL code, and lock it away under a different licence. You must allows users of your product to modify and redistribute as they see fit, to suit their own needs.

---

### Post by 23meg on 2007-03-11
The GPL is a software licence. Wikipedia's text content isn't software, thus isn't licensed under the GPL, but the [GFDL]("http://en.wikipedia.org/wiki/Wikipedia:Text_of_the_GNU_Free_Documentation_License") (GNU Free Documentation License). Images have different licensing and usage terms, which are usually listed in boxes below them.

---

### Post by IYY on 2007-03-11
> I am sorry I havent yet understood completely . Does GPL only apply to program codes?

No, it can be used for all sorts of content.

> If I do, then I have to release my project under GPL according to your explanation above.

If you modify the pictures themselves, you will have to release the modified pictures under the GPL. You do not have to release the *project* under the GPL.

> It is the same way as borrowing a linux program into a new os project.

Taking Linux code and using it to make new code is like taking a picture and using it to make a new picture. Taking a picture and placing it in a document is like building an application to run on Linux, or using Linux as the operating system for a new piece of hardware. In this case, you do not have to release your entire project under the GPL, only the modifications you made to Linux itself (often no such modifications are even needed).

---

### Post by 23meg on 2007-03-11
[QUOTE=IYY]No, it can be used for all sorts of content.[/QUOTE]

It [can be]("http://www.gnu.org/licenses/gpl-faq.html#GPLOtherThanSoftware"), but for documents, the GFDL is mostly preferred. Wikipedia's text content is GFDL'd as well.

[QUOTE=IYY]If you modify the pictures themselves, you will have to release the modified pictures under the GPL. You do not have to release the project under the GPL.[/QUOTE]

Images in Wikipedia have their own usage terms, which one is expected to respect. Neither the GPL nor the GFDL apply.

---

### Post by IYY on 2007-03-11
> Images in Wikipedia have their own usage terms, which one is expected to respect. Neither the GPL nor the GFDL apply.

Not quite so: every image in Wikipedia has an individual license. GPL is among the options, and many images in Wikipedia are indeed GPL. I think most of them are CC, though, which means the OP can use them anyway.

---

### Post by 23meg on 2007-03-11
> **IYY said:**
> Not quite so: every image in Wikipedia has an individual license. GPL is among the options, and many images in Wikipedia are indeed GPL. I think most of them are CC, though, which means the OP can use them anyway.

What I'm saying is that there isn't a single license that covers all the images, but that there are multiple ones selectable, and you're expected to respect whatever the uploader of the particular image you're interested in has selected. Using GPL for self submitted images is discouraged; only images that come as part of a software package are GPL'd. In general, using the GPL for things where the definition of "source code" can be ambiguous isn't a good idea; GFDL and similar licenses are almost always better choices.

---

### Post by IYY on 2007-03-11
> What I'm saying is that there isn't a single license that covers all the images, but that there are multiple ones selectable, and you're expected to respect whatever the uploader of the particular image you're interested in has selected. Using GPL for self submitted images is discouraged; only images that come as part of a software package are GPL'd. In general, using the GPL for things where the definition of "source code" can be ambiguous isn't a good idea; GFDL and similar licenses are almost always better choices.

That's what I was saying as well, just clarifying. I was under the impression that the OP was referring to specific images in Wikipedia which *are* licensed under the GPL, asking if he could use them in a document.

---

### Post by deanlinkous on 2007-03-12
> **naerae said:**
> Hello. If I use a part of GPL licenced material in my project , do I have to release my project in GPL? For example, If I use a picture from Wikipedia which is GPL licenced ,  ought the rest of the project  ,which is not constituting any GPL licenced material, released also in GPL? 
Thanks.
The picture used in your project would still be licensed under the GPL. The license does not change.

As long as your project is a seperate work then it does not need to be licensed under the GPL.

If your project is derived from the picture, if your project is intrinsically based upon the picture, if the picture is inseperable from your project then I would say you must license your project under the GPL.

---

