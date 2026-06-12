---
title: "Music app that changes a loop's effect relative to the mouse location?"
date: 2008-12-02
forum: Ubuntu Studio
---

### Post by bgryderclock on 2008-12-02
I had the idea to create a music application that plays a loop of a sample and changes volume, pitch and distortion relative to the mouse location.

Is there an application that already does that? 

Example: It play a loop of a piano note, and I move the the mouse up and down and note's pitch goes up and down. When I move the mouse left and right the distortion goes up and down. 

Thanks!

---

### Post by Stochastic on 2008-12-03
I think that if you want to do this fast you should look at doing it with a combination of PureData sending midi messages to a program like freewheeling.  Or even just implement the whole thing in PureData.

If you want to release this to people for Linux, I think Freewheeling would be the best project for you to look into to utilize code ideas.

---

