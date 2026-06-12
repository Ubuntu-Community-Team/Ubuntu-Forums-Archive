---
title: "Need HTML help"
date: 2006-09-25
forum: The Cafe
---

### Post by alecjw on 2006-09-25
Hi. I've made a table in HTML, but there are transparent gaps between the cells. How do I push the cells togeter and get rid of these lines (using CSS)?

Thanks

---

### Post by GuitarHero on 2006-09-25
just do it with html.  cellspacing="0" in the table tag

---

### Post by maniacmusician on 2006-09-25
unless there's a bunch of tables. then its easier to use css.

---

### Post by alecjw on 2006-09-26
> **maniacmusician said:**
> unless there's a bunch of tables. then its easier to use css.

I'm using XHTML srict. I can't use syle attrubutes such as border, bgcolor, cellspacing etc. I have to use CSS. What's the CSS attribute?

---

### Post by DirtDawg on 2006-09-26
maybe {padding:0px} ?

---

### Post by alecjw on 2006-09-26
> **DirtDawg said:**
> maybe {padding:0px)?

Just curious, does using tables hold an advantage over a box model when using CSS?

Nope. It doesn't work. And I've never heard of a box model.

---

### Post by DirtDawg on 2006-09-26
> **alecjw said:**
> Nope. It doesn't work. And I've never heard of a box model.

Box model just means no tables. Everything is contained in <div> tags, which essentially act like boxes. Then you use CSS to layout the boxes in their desired spot. It's how I built my website(see sig), though I am a self taught hack.

Anyways, I'm not familiar with tables, but I have an Orielly CSS pocket guide here I'm using for reference. According to this thing, there's only padding and margins between each cel, if I'm understanding correctly. It sounds like there's strict rules concerning borders when more than one cel is adjacent. 

For example, here's part of rule #3:
```
If at least one of the collapsing borders has a value other than NONE or HIDDEN, 
then narrow borders lose out to wider ones... 
```

Maybe the borders need tweaking?

---

### Post by DirtDawg on 2006-09-26
Maybe [this]("http://www.safaribears.de/content.php?page=csstutorial&chap=7") is what you're looking for? 
Something about a {border-collapse:collapse}

---

### Post by v8YKxgHe on 2006-09-26
Have you got a link or could you post some code?

---

### Post by skymt on 2006-09-26
If you're using XHTML you shouldn't be using tables for layout anyway. Read up on modern web design. The [latest article](http://alistapart.com/articles/12lessonsCSSandstandards) on [A List Apart](http://alistapart.com/) has some good advice. After that, read up on CSS at [W3Schools](http://www.w3schools.com/).

---

### Post by v8YKxgHe on 2006-09-26
Who said he's using tables for layout? But yes, Tables should _NOT_ be used for layouts, DIV + CSS is the way to go.

---

### Post by DirtDawg on 2006-09-26
> **AlexC_ said:**
> Have you got a link or could you post some code?

Sorry, the link was coded in the word "this". That probably wasn't very clear.

Here it is again:
[http://www.safaribears.de/content.php?page=csstutorial&chap=7](http://www.safaribears.de/content.php?page=csstutorial&chap=7)

---

### Post by v8YKxgHe on 2006-09-26
hehe, sorry - I meant to the first poster who was asking for help,

---

### Post by skymt on 2006-09-26
> **AlexC_ said:**
> Who said he's using tables for layout? But yes, Tables should _NOT_ be used for layouts, DIV + CSS is the way to go.

If he's using tables to display tabular data, he'd want borders. Since he doesn't, he isn't.

---

### Post by DirtDawg on 2006-09-26
> **AlexC_ said:**
> hehe, sorry - I meant to the first poster who was asking for help,

oh right. DAR!

---

### Post by alecjw on 2006-09-26
[http://192.168.2.102/marsh/](http://192.168.2.102/marsh/)

I've tried border-width:0px, border-style:none and margin:0 and padding:0, none of which work.

---

### Post by alecjw on 2006-09-26
Sorry, that's the local address. It's [http://alecjw.no-ip.org/marsh/results.php](http://alecjw.no-ip.org/marsh/results.php)

---

### Post by DirtDawg on 2006-09-26
I fixed it by adding:
table {border-collapse:collapse;}

Of course, you'll likely want to refine it, and who knows if it works in IE, but that's a start.

---

### Post by alecjw on 2006-09-26
Doesn't work in IE or Opera.

---

### Post by DirtDawg on 2006-09-26
> **alecjw said:**
> Doesn't work in IE or Opera.

Well short of a box model solution, I'm out of ideas. Sorry.

---

### Post by alecjw on 2006-09-26
Just found out that cellspacing isn't depereceated! It's the only style attribute which isn't! (Presumably because of these browser incompatabilities)

---

### Post by v8YKxgHe on 2006-09-26
> **skymt said:**
> If he's using tables to display tabular data, he'd want borders. Since he doesn't, he isn't.

Not always =)

---

