---
title: "How to create kde&amp;Gnome themes"
date: 2009-10-05
forum: The Cafe
---

### Post by praveesh on 2009-10-05
I would like to create my own themes for my kde and Gnome . I mean complete themes . Not just changing the colours. I think I have sufficient artistic ability to do that. Does that require the knowledge in programming? I don't know too much , but I assume the qt /gtk may be needed . Am I correct ? I haven't used both of them before . If any one know, please explain

---

### Post by Sand &amp; Mercury on 2009-10-05
I've no experience with KDE themes, but here's what I have to say about GNOME ones.

The best way to learn is to grab a theme off of GNOME-look or such other site and sit down with it, and examine its ins and outs. You will find most of the guts of the layout and workings are in a file called gtkrc for most themes; open it with gedit and take a look at it. You don't need to be a genius programmer to change things, but you will need a little understanding of basic syntax when it comes to code in general. Generally though, you'll do well by starting off with someone else's theme and making your own small changes here and there to build confidence.

---

### Post by RiceMonster on 2009-10-05
I think Qt styles are a lot more complex than GTK themes, but I don't know a lot about them.

Anyway, GTK themes aren't too hard. Just look at the gtkrc for a bunch of themes, try modifying them and do some googling.

---

### Post by GeneralZod on 2009-10-05
I'd love for someone to make a theme for KDE's [QuantumStyle](http://kde-look.org/content/show.php/QuantumStyle?content=101088) engine: no coding would be required, just editing an SVG (although of course not requiring coding means that a QuantumStyle theme is limited by what the style engine allows you to change).  The need to compile Qt/ KDE themes from source (or install them via the package manager) often comes up as an advantage of GTK over Qt, and a couple of nice QuantumStyle themes might help to kickstart a move towards styles that can be installed via GHNS.  

I'm baffled as to why such a move hasn't happened years ago, to be honest.

---

### Post by praveesh on 2009-10-05
Thanks for all. let me try

---

