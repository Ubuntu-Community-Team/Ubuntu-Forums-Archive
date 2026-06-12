---
title: "font smoothing idea"
date: 2010-02-21
forum: The Cafe
---

### Post by daverich on 2010-02-21
I've been pondering the sub-par look of fonts on linux and came up with an idea..

I'm wondering how much of a pain it would be to have something like Compiz essentially draw the whole screen 4 times bigger than your monitor, and then scale the whole thing down to fit the screen using a decent scale filter.

I just wonder if it would look better and how much the performance penalty would be (I'm guessing you could make it so that it only scaled/rescaled text somehow).

Just an idea to throw at folks who can do the clever bit :)

Kind regards

Dave Rich

---

### Post by BuffaloX on 2010-02-21
Ubuntu default font smoothing is very good IMO.
Font smoothing is always a compromise between smoothness and how true it is to the original design.

I think you could simulate what you suggest.
Make a GIMP image with some text in it.
Double the size, and reduce it back again. That should do just about the same thing you suggest.

---

### Post by NovaAesa on 2010-02-21
What you are suggesting is called super-sampling. It's a fairly naive algorithm for font smoothing. Not that I'm basing this on any knowledge, but I would assume that Ubuntu would already be using a more intelligent algorithm for font smoothing.

---

### Post by hobo14 on 2010-02-21
Fonts looked pretty poor to me on 8.10 until I did some tweaking, but they look great on 9.10 (much better than fonts on XP for example, when the two are placed next to each other)

---

### Post by daverich on 2010-02-22
ah ok,- supersampling.

I figured it was such a simple idea it must already have been explored.

Kind regards

Dave Rich

---

### Post by siimo on 2010-02-22
Use the Apple patented bytecode interpreter and fonts look crisp.  I think its default in Ubuntu too.

---

### Post by madnessjack on 2010-02-22
Tell you what - have a play around with fonts and font sizes. It makes a lot of difference. The default Windows XP font renders well.

---

