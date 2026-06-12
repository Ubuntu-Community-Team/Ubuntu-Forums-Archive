---
title: "what makes a theme fast or slow?"
date: 2009-12-28
forum: The Cafe
---

### Post by chucky chuckaluck on 2009-12-28
i've seen discussions about which gtk themes are the fastest, but i have no idea what would account for the differences in speed. and speed in what manner? is it the same for qt?

(note: i don't know anything, so if you respond, pretend you're explaining this to your mom. thanks.)

---

### Post by koleoptero on 2009-12-28
> **chucky chuckaluck said:**
> i've seen discussions about which gtk themes are the fastest, but i have no idea what would account for the differences in speed. and speed in what manner? is it the same for qt?

(note: i don't know anything, so if you respond, pretend you're explaining this to your mom. thanks.)

I have noticed that when I use a theme that's based on the Aurora engine some programs go slooooow, while with the murrine engine they go ten times faster. I don't know why this happens, just an observation.

---

### Post by Pogeymanz on 2009-12-28
This is a total guess and is probably wrong.

It might have to do with how the theme's engine accesses the visual elements. For example, maybe one engine loads the "button" image every time it needs to draw one while another might keep it in memory after it is called once. Or maybe they draw things in different orders, giving the appearance of slowness in one.

---

### Post by markp1989 on 2009-12-28
> **Pogeymanz said:**
> This is a total guess and is probably wrong.

It might have to do with how the theme's engine accesses the visual elements. For example, maybe one engine loads the "button" image every time it needs to draw one while another might keep it in memory after it is called once. Or maybe they draw things in different orders, giving the appearance of slowness in one.

i was thinking a similar thing but relating to buttons needing to be resized on the fly if there overly big causing the ilusion of slowness

---

### Post by Andreas1 on 2009-12-28
only throwing this in here: you can use *gtkperf* to compare the drawing speed of different themes. if i remember correctly, mist is fastest (no wonder, considering the dull look), pixmap themes (like new wave) are slowest. i am using *nimbus*, which is appreciably faster than clearlooks or murrine, although it looks as "elaborate" as most pixmap themes.

EDIT: i just noticed i cannot really answer your question. but there is a correlation between slowliness and how elaborate a theme looks (which seems logical, e.g. mist vs. new wave), but this does not account for the entirety of variations observed. (e.g. nimbus vs. clearlooks)

---

### Post by oedipuss on 2009-12-28
> **Pogeymanz said:**
> This is a total guess and is probably wrong.

It might have to do with how the theme's engine accesses the visual elements. For example, maybe one engine loads the "button" image every time it needs to draw one while another might keep it in memory after it is called once. Or maybe they draw things in different orders, giving the appearance of slowness in one.

Not only that, but some engines might actually draw the button using for example cairo, or others might fetch and load a specific pixmap. Or a combination of both. I imagine if an engine uses a very complicated drawing procedure for a button, with lots of details, it will be much slower than drawing a rectangle.

---

### Post by chucky chuckaluck on 2009-12-28
so, pretty =slow? (as in life...sad...)

---

### Post by gnomeuser on 2009-12-28
> **chucky chuckaluck said:**
> so, pretty =slow? (as in life...sad...)

Not really, it has to do with what kind of math is required. Gradients e.g. require more calculation than solid colors. It gets worse though, it also depends on how many big a section they cover and in which direction vertical means redrawing a bigger area than horizontal which means a greater need to power up the videocard. So not only do you have to select your mathwith great care, you have to understand how to optimize between looks and power consumption. A little tweak can have a great impact. 

Then there is poor coding to contend with, as engines get more and more complex they tend to get slow just from doing work they don't need to. The quickest work is the work you don't do, the best optimization you can do normally is detect and remove these pieces.

Mostly though themes are slow because we aren't using all the capabilities of the videocards, a theme is pretty lightweight compared most other things you can do with these modern calculation monsters. This is the part of the puzzle we are working on fixing right now with modern open drivers, e.g. the Gallium driver model and the underlying llvm stack will allow drivers to optimize much better and more consistently.

---

### Post by del_diablo on 2009-12-28
> **chucky chuckaluck said:**
> so, pretty =slow? (as in life...sad...)

Pretty may equal slow. It is just a matter of how it is done.

---

### Post by urukrama on 2009-12-28
> **chucky chuckaluck said:**
> so, pretty =slow? (as in life...sad...)

I find the xfce-gtk-engine, considered one of the faster ones, the prettiest if configured properly.

---

