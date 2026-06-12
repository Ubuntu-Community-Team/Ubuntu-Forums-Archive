---
title: "[SOLVED] css issues with &amp;lt;div&amp;gt;"
date: 2008-06-19
forum: The Cafe
---

### Post by moore.bryan on 2008-06-19
okay, the "interweb" has been completely unhelpful on this, so i thought i'd pose my questios/issue to the only place i ever seem to get useful feedback! ;-)

if my css is as follows
```

#left{float:left;margin-left:auto;margin-right:auto;width:50%;}
#right{float:right;margin-left:auto;margin-right:auto;width:50%;border-left:2px solid black;}

```
shouldn't i have two-columned text with a divider line between the two? alas, it's nothing like that.

---

### Post by _DD_ on 2008-06-19
You don't need to set the margins and also (depending on the browser) the border might push the float over; if both are set to 50% width then they fill up 100% of the container they are in - floated divs start to stack in columns when there isn't enough width, so in some box models where the border adds size to the div rather than taking up space within the div, there won't be enough room.

Try simply...

```

#left{float:left;width:50%;}
#right{float:right;width:50%;border-left:2px solid black;}

```

If that doesn't work then try...

```

#left{float:left;width:49%;}
#right{float:left;width:49%;border-left:2px solid black;}

```

Part of the idea of floating is that you can float things in the same direction and then they stack against each other and once they've filled up the width, begin going into columns. You don't always have to float things left *and* right.

---

### Post by SupaSonic on 2008-06-19
Aaaa, design with divs. What a PITA.

---

### Post by moore.bryan on 2008-06-19
@ _DD_:
the first suggestion was actually all i had on my page, with no luck. your second suggestion worked magnificently; such an easy solution, i'm banging my head against the wall. one issue still remains, though... a strange line has appeared in the remaining space on the page (i've attached a snap).

> **SupaSonic said:**
> Aaaa, design with divs. What a PITA.
you hit the nail right on the head SupaSonic.

---

### Post by _DD_ on 2008-06-19
Erm, sorry, I don't really know what it could be. Is it a horizontal rule (<hr />) which has slipped itself in somewhere? Could I see the rest of the HTML/CSS?

> **SupaSonic said:**
> Aaaa, design with divs. What a PITA.
I wouldn't say so. Much better than those horrible table things people used in the 90s :D.

---

### Post by Paqman on 2008-06-19
> **_DD_ said:**
> I wouldn't say so. Much better than those horrible table things people used in the 90s :D.

^^This.

It's much more elegant to position things on the screen relative to each other, instead of some arbitrary framework.

---

### Post by moore.bryan on 2008-06-19
> **_DD_ said:**
> Erm, sorry, I don't really know what it could be. Is it a horizontal rule (<hr />) which has slipped itself in somewhere?
genius! i completely forgot i even had an hr on the page... success!!! once again, ubuntuforums and its wonderful users save the day...
> Could I see the rest of the HTML/CSS?
attached.
> I wouldn't say so. Much better than those horrible table things people used in the 90s :D.
oh, but all the wonderful control!!!
:shrug:

---

### Post by SupaSonic on 2008-06-19
> **_DD_ said:**
> 
I wouldn't say so. Much better than those horrible table things people used in the 90s :D.

But tables have a crucial advantage: I know how they work )

---

### Post by _DD_ on 2008-06-19
> **moore.bryan said:**
> 
attached.


No need now if its sorted :)


As well as being generally a much better and flexible way of doing designs, CSS also has the advantage that it keeps the design and the content separate.

It would take aaaages to type out all the advantages this has, but I'm sure you can think of most of them.

---

### Post by moore.bryan on 2008-06-19
i've been going back-and-forth with css vs. tables, read what feels like every single blog, post, thread, and webpage on the topic, and still don't think i have a firm stance. for some things, css hasn't yet come up-to-speed with the html code and/or the browsers are a little behind. regardless, i try to be as "standard" as possible with the output looking the way i want it to look.

thanks for all your help!

---

### Post by Paqman on 2008-06-19
And speaking of web standards, you might want to try pointing your brand-new Firefox 3 at [Acid 2](http://www.webstandards.org/files/acid2/test.html) and see what happens.

So that just leaves IE dragging behind. What a surprise.

---

### Post by moore.bryan on 2008-06-19
one of the first i hit... now only if acid3 tests go well!

---

