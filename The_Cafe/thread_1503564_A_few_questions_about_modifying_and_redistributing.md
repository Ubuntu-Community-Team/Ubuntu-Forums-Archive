---
title: "A few questions about modifying and redistributing source code"
date: 2010-06-06
forum: The Cafe
---

### Post by diablo75 on 2010-06-06
I am working on editing some source code for a program I like to use and am trying to make it more fitting for my own personal uses.  I have never edited source code before but find the relevant parts that I'm interested in editing fairly easy to do.  I am essentially trying to modify the ease of use (save time) for the users I want to distribute the program to.  I just don't want to break any laws or hurt anyones feelings.

The software I'm wanting to modify is distributed under GPL v3.  I haven't read the entire license agreement, but my understanding is that I have the right to edit the source code to my liking and produce my own custom binaries from this source code and distribute them along with the modified source code.  I know the license gets into a lot more detail, but is this the basic sum of it?  Anything in particular that I should know besides this?

I was also wondering, since you are allowed to edit the source code to your hearts content, if there were any limitations to this privilege?  Could you do it to the point where you actually rename the program itself to something else?

Also, am I obligated to contact the original developers every time I decide to make a modification, or even at all?

How much detail is required when documenting modifications made to the original source and attaching this documentation to the modified source code?  Is there an easy way to do this; perhaps with a piece of software that can compare two folders with source code files and print out the difference between the two of them?

I think that's all I have on my mind right now.  Thanks in advanced for any advice you guys can provide.

---

### Post by Dr. C on 2010-06-07
IANAL

> The software I'm wanting to modify is distributed under GPL v3. I haven't read the entire license agreement, but my understanding is that I have the right to edit the source code to my liking and produce my own custom binaries from this source code and distribute them along with the modified source code. I know the license gets into a lot more detail, but is this the basic sum of it? Anything in particular that I should know besides this?


The resulting program remains under GPLv3. Do not try to restrict the user by adding additional restrictive terms or DRM since that would be infringing.

> I was also wondering, since you are allowed to edit the source code to your hearts content, if there were any limitations to this privilege? Could you do it to the point where you actually rename the program itself to something else?
 

You may have to rename the program if you modify it. This is a trademark issue not a copyright issue.

> Also, am I obligated to contact the original developers every time I decide to make a modification, or even at all?

No 

> How much detail is required when documenting modifications made to the original source and attaching this documentation to the modified source code? Is there an easy way to do this; perhaps with a piece of software that can compare two folders with source code files and print out the difference between the two of them?


Section 5a requires > The work must carry prominent notices stating that you modified it, and giving a relevant date.

It does make sense to properly document your code so that another programmer can figure out the changes that were made.

---

