---
title: "Is this license GPL-compatible?"
date: 2009-02-21
forum: The Cafe
---

### Post by Skofo on 2009-02-21
Hey guys, I'm working on a software project and I get hard for making all of my work GPL-compatible all the way down to the kernel, so I want to figure out if the license which one of the libraries I'm using is licensed under is GPL-compatible.

Anyone care to help me out? :D

The license at the time of this post is located here: [http://love2d.org/wiki/index.php?title=LPC_License&oldid=532#The_License](http://love2d.org/wiki/index.php?title=LPC_License&oldid=532#The_License)

```
             Lovely Public Community License (LPCL)
                Version 1.1, February 20, 2009
----  ------  ------  ------  ------  ------  ------  ------  --

Copyright (c) 2009 Bart Bes and Osuf Oboys
  This license, but not the licensed product, is licensed to
"the LCPL Development Team" under LPCL.

  The intention of this license is to provide a means to release
a product in a community without any particular user governing
the project. In particular, the license should encourage the
liberties taken in wiki systems, provide a means to settle
disputes, and allow new users to continue a project where every
developer has gone inactive. This license imposes NO
restrictions on work that is released under other names than the
name of this product. If such restrictions are desired, the work
may be licensed under more than one license.

Definitions.
  "This product" refers to all copyrightable work licensed under
this license. A "derivative work" is any copyrightable material
based on or using this product. "The community of this product"
is a body of entities, usually people, which may be defined in
an accompanying policy document or section as stated below.

  A separate document or section defining this product's
community and policy may accompany this license and is treated
as constituent of the referenced product as far as this license
is concerned. Such a document or section may only define "the
community" and how "the community" may exercise  clause 3.2 of
this license. In particular, changing such a document does not
demand a new release of this license but it does demand a new
release of the product. If no such document or clause
accompanies the product, then "the community" is the empty set.

Terms and Conditions.
  This product comes without any warranty, express or otherwise.
Under no circumstances will the creators of this product be held
responsible for any negative effects arising from the use of
this or derivative works.
  Permission is granted to use this product in any fashion and
for any purpose, including commercial, with or without this
license, provided the following conditions are met.
 1. Derivative works released under more than one license are
subject to the restrictions of each such license.
 2. Any derivative work advertised under the same name and the
same version as this product must constitute a complete
unaltered copy of this product without any additions and be
accompanied by an unaltered copy of this license.
 3. If a derivative work is advertised under the same name as
this product but under a different version, then the following
additional conditions apply.
  3.1. The derivative work must clearly state that they are a
derivative of this product and the license of the derivative
work must include this clause.
  3.2. The community of this product has the right to demand
that any derivative work, or any derivative work of a derivative
in any number of steps, changes the name of the derivative work
to a name other than the name of this product or else be subject
to copyright infringement. The owners of the derivative work
must in such an event be notified about the decision. The
community has no right in choosing the new name.
  3.3. Clause 3.2 may be invoked any number of times permitted
by the accompanying policy.

The LPCL Development Team.
  This section does not apply to work licensed under LPCL other
than the license itself. The LPCL Development Team can NOT
invoke clause 3.2 for any work other than the license and the
license only.
  The LPCL Development Team consists of every real person with
an unbanned account on any forum hosted by http://love2d.org
with at least ten posts made a week or more ago.
  To invoke clause 3.2, a post must be made by a team member in
a new thread hosted by the domain http://love2d.org. This post
must clearly state the opening of a vote, the expected format of
votes, and the effect of the respective answers.
  A valid vote is any post in this thread made by a member of
the LPCL development team which
 * contains "yes." or "no.", but not both, as a subword of any
capitalization,
 * does not have any other valid vote cast by the same member of
the same or a newer time,
 * is stamped at most 604800 seconds (one week) older than the
post that opened the vote.
  After one week, the votes are tallied with the winning being
either 'yes.' or 'no.', whichever received the most answers. In
the case of a draw, clause 3.2 is not invoked.
  At most three votes per can be made about the same product and
at least one week apart. A vote may concern more than one
product. No legal person may open more than four votes per
month.
----  ------  ------  ------  ------  ------  ------  ------  --

```

Thanks a bunch!

---

### Post by Grant A. on 2009-02-21
For future reference, here's a list of things that break GPL compatibility:

[LIST]
[*]Share alike with just a certain license
[*]Not allowed to be used for commerical purposes
[*]Attribution
[*]No derivatives
[*]Choice of law
[/LIST]

If you're going for public domain with a few added things, you may want to go with the [BSD]("http://www.opensource.org/licenses/bsd-license.php") or [MIT/X11]("http://www.opensource.org/licenses/mit-license.php") licenses, respectfully.

Although, if you prefer to make your own license, go right ahead, just be sure that it doesn't conflict with any other Open Source licenses, as a divided software community is a bad thing. :(

By the way, I am not a lawyer.

---

### Post by lukjad on 2009-02-21
Before reading the whole thing, I have to ask. Which version of the GPL? And secondly, I'm pretty sure that it doesn't, simply because GPL v3 is not compatible with GPL v2. BUT, here is a web page that should help you. [http://www.gnu.org/philosophy/license-list.html](http://www.gnu.org/philosophy/license-list.html)

It tells you of compatible and incompatible licenses.

---

### Post by Skofo on 2009-02-21
Hum, thanks guys! Cheers.

---

### Post by ssam on 2009-02-21
i am not a lawyer but it looks to me like as long as you change the name of the project you could re-licence it as GPL.

there are a few project in the foss world that achieve the same thing using trademarks. eg if you make any changes to firefox you are no longer allowed to call it firefox, all the redhat enterprise linux derivatives (cent OS, scientific linux) have to strip out all RH trademarks.

i am not sure about how this bit works.
"1. Derivative works released under more than one license are
subject to the restrictions of each such license."
if i tooks some of your code and put it into my GPL code, then do you get the right to demand that i change the name of a derivative?

---

### Post by Skofo on 2009-02-21
I haven't a clue about your question, but I posted on the forums which the authors of this license hang out at and they should reply.

Thanks for your help!

EDIT:
> If it is released under more than one license, then each license should apply, that's all it says. It says nothing about what license should be used.

But I see, yes, it should be removed as compatibility does what we want that clause to do. I replaced it with
1. Do whatever you want as long as you do not advertise anything as a version of this product.
Note that this clause is actually redundant since it already says that you can release derivative work under a different license and none of the clauses applies to derivative work under a different name.

If it is released as a derivative work under a different name, then the license says that you do not have to release it under LPCL. If it is released under the same name, then it says that you have to include a clause that says that it is a derivative work of the previous version and then the community can force you to change the name of your project. I presume the unclear part is what happens if you use an unaltered copy of an LPCL software in your own program. By the previous version (1.2), the copy would be considered part of your derivative work, not the original software. Hence, if the LPCL license is not visible, you have it licensed under whatever else your work is licensed under. If you kept the license visible, I presume it either means that that subdirectory will either be subject to LPCL or subject to both LPCL and the license of the entire work (and hence you can be forced to not advertise the subdirectory as a new version of the used software). I changed the license somewhat to make it clear that you can use an unaltered copy of a product in your program without labelling the copy a derivative work.
A product may contain an unaltered copy of this
product without labelling it a derivative work under a
different name. 

---

### Post by Brunellus on 2009-02-21
I am not (yet) a lawyer, but I can tell you one thing for sure:  If you need to make sure that your license is compatible/consistent with the terms of an existing license, then you should REALLY pay the money and have a qualified attorney review both licenses and give you a reliable opinion.  

In the event that, in the future, someone mounts a legal challenge to your license, you can at least show justifiable reliance on a legal opinion by a qualified attorney.  The consensus of unknown people on Internet forums will not protect you.

---

### Post by ssam on 2009-02-21
can i suggest that you have a read of this [http://itmanagement.earthweb.com/osrc/article.php/12068_3803101_1/Bruce-Perens-How-Many-Open-Source-Licenses-Do-You-Need.htm](http://itmanagement.earthweb.com/osrc/article.php/12068_3803101_1/Bruce-Perens-How-Many-Open-Source-Licenses-Do-You-Need.htm)

it looks to me like you want to achieve a gift license, but are worried that people create things that get confused with your program, and you don't want that to effect your programs reputation. That is a similar aim to a lot of programers.

however if you go the current way of making a new licence you will just confuse people. i would not want to incorporate any of your code into one of my projects without consulting a lawyer. however if you used Apache License 2.0 plus a trademark policy, i would know straight away what was allowed.

---

### Post by CarpKing on 2009-02-21
> **ssam said:**
> it looks to me like you want to achieve a gift license, but are worried that people create things that get confused with your program, and you don't want that to effect your programs reputation. That is a similar aim to a lot of programers.

however if you go the current way of making a new licence you will just confuse people. i would not want to incorporate any of your code into one of my projects without consulting a lawyer. however if you used Apache License 2.0 plus a trademark policy, i would know straight away what was allowed.

He isn't making the license.  He wants his product to be GPL-compatible, but one of the libraries he wants to use has a weird license that may or may not be so.

---

