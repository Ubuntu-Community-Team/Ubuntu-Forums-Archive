---
title: "Java problems with my Serval"
date: 2007-06-06
forum: System76 Support
---

### Post by sgtron on 2007-06-06
I think I've loaded every java package I could find but I still can't get Java to work with Firebird correctly.  In particular I'll try to load a java page and get the message saying that the page is trying to load a java applet and it may cause damage, blah, blah, blah, then I say go ahead and load the applet and the page will display but java functions are disabled.

The pages I need to work are youmail.com and an internal security application that I think will be fine if I can get youmail to work first.

Any help would be greatly appreciated.

---

### Post by thomasaaron on 2007-06-07
Sounds like a pretty specialized problem.

At this link, there is a mailing list for firebird-java problems.
[http://www.firebirdsql.org/index.php?op=lists#firebird-java](http://www.firebirdsql.org/index.php?op=lists#firebird-java)

Best,
Tom

---

### Post by sgtron on 2007-06-07
Not sure if I should call this a "cop-out" answer or not.. so I'll just make a new thread that is a bit narrower in scope to see if I can get a better answer.

---

### Post by sgtron on 2007-06-07
SOLVED!!!

This page had the answer:
[http://www.mozilla.org/support/firefox/faq.html#q2.2](http://www.mozilla.org/support/firefox/faq.html#q2.2)

I needed a symbolic link from my java directory to my firefox plugins directory.  Don't know why this isn't created instantly when you install the java package, but whatever, I'm just glad it works now.

Now I can access my favorite website, youmail.com and my internal security program works great too.  Now I can monitor my surveillance system from the comfort of my own home and my System76 laptop instead of resorting to windows or something.

---

### Post by thomasaaron on 2007-06-08
It was not a cop-out answer.
You said Firebird (...BIRD), not Firefox, in your previous post.

As it turns out FIREBIRD is also made by mozilla. It is a relational database program.
[http://www.firebirdsql.org/](http://www.firebirdsql.org/)

That's why I said it seemed a little more specialized than what we commonly deal with around here. :D

---

### Post by sgtron on 2007-06-08
Yeah, I said firbird, cause I'm an idiot.. :)

Also I guess I'm used to firebird since that was the old name before firefox.. and I have the flu.. and, and , and..

---

