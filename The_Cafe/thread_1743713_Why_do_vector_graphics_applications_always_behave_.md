---
title: "Why do vector graphics applications always behave so weird?"
date: 2011-04-29
forum: The Cafe
---

### Post by Legendary_Bibo on 2011-04-29
I was given a copy of Adobe CS4 by a classmate and things I know how to do easily in gimp are a pain in the butt in Illustrator. The thing is if I did it in Gimp it probably wouldn't look as good. The same goes for Inkscape, it always gives me weird behavior. Even Photoshop acts like it should.

---

### Post by juancarlospaco on 2011-04-29
**vector graphics are NOT graphics.**

you are editing an .XML plain text file,
with coord and math things thats the reason,
its the most weird method to edit an xml

---

### Post by Legendary_Bibo on 2011-04-29
For instance to put a gradient in the background, I have to draw a rectangle and then fill it with a gradient, but there's no color selection with the gradient you have to drag and drop colors which is an awesome way of doing gradients but not the first thing you think of. Also, the paint bucket doesn't work unless you convert paths to live paint first, and even then it's picky, and for some reason it decides to make my outlines thinner. What I like about vector graphics is that they can account for the jiggle in your hands and correct it so you have smooth curvy lines, but the tools are really in your way.

---

### Post by juancarlospaco on 2011-04-29
You dont draw, you are doing Math but the GUI dont let you see that

thats the reason of they maintaining the proportion on scaling

---

### Post by Telengard C64 on 2011-04-29
Gimp draws points (pixels).
Inkscape draws curves (graphical expression of a mathematical function).

Can't tell you how to use your program though  ;)

---

### Post by juancarlospaco on 2011-04-29
Gimp do Vectors

Paths are a Vector element

---

### Post by Telengard C64 on 2011-04-29
> **juancarlospaco said:**
> Gimp do Vectors

Paths are a Vector element

Not a Gimp expert. If what you say is true, then Gimp should be capable of scaling a path with infinite resolution. (At least infinite up to the limits of the FPU.)

---

### Post by Legendary_Bibo on 2011-04-29
> **Telengard C64 said:**
> Not a Gimp expert. If what you say is true, then Gimp should be capable of scaling a path with infinite resolution. (At least infinite up to the limits of the FPU.)

Gimp doesn't have vector layers yet, the paths tool is just part of a gateway for when they do decide to add it in. It's not very useful in gimp.

---

### Post by juancarlospaco on 2011-04-29
> **Legendary_Bibo said:**
>  It's not very useful in gimp.

You are an Expert on Gimp ?  &#3232;_&#3232;

---

### Post by Lucradia on 2011-04-29
> **juancarlospaco said:**
> You are an Expert on Gimp ?  &#3232;_&#3232;

Gimp doesn't do vectors with layers. I'd rather have gimp + vector layers than inkscape.

---

### Post by Legendary_Bibo on 2011-04-29
> **juancarlospaco said:**
> You are an Expert on Gimp ?  &#3232;_&#3232;

Gimp has been my primary art program for the past year, I've used it a lot, and the paths tool is what I use the least. It's great for making curvier selections, but other than that there wasn't much use for it. Gimp's masking function is superb, but I rarely use it because I've yet to make something that called for that feature. It's also kind of advanced. I messed around with channels a lot when I worked on my friend's wedding photos, but I don't use it that often because I don't really work with photographs.

---

### Post by Legendary_Bibo on 2011-04-29
> **Lucradia said:**
> Gimp doesn't do vectors with layers. I'd rather have gimp + vector layers than inkscape.

+1

Even bouncing between Photoshop and Illustrator is annoying. It's not easy to bounce between them with their files (Illustrator goes all weird with photoshop files, and opening up Illustrator files in PS doesn't work right). Since how I'm familiar with Gimp, and there's nothing in PS that you can't do in Gimp, I'm bouncing between Illustrator and Gimp. The only problem is that I have to save as an SVG, and I can't bring over the layers, but it's great for backgrounds.

---

### Post by Lucradia on 2011-04-30
> **Legendary_Bibo said:**
> +1

Even bouncing between Photoshop and Illustrator is annoying. It's not easy to bounce between them with their files (Illustrator goes all weird with photoshop files, and opening up Illustrator files in PS doesn't work right). Since how I'm familiar with Gimp, and there's nothing in PS that you can't do in Gimp, I'm bouncing between Illustrator and Gimp. The only problem is that I have to save as an SVG, and I can't bring over the layers, but it's great for backgrounds.

But that's not all I want though. I want to be able to create SVGs without using the paths tool. IE: why not just paint something? Or use the pencil tool?

I'm sure it isn't hard to implement it.

But that's just like me asking HTML5 to have a WYSIWYG Editor like Flash.

---

### Post by Legendary_Bibo on 2011-04-30
> **Lucradia said:**
> But that's not all I want though. I want to be able to create SVGs without using the paths tool. IE: why not just paint something? Or use the pencil tool?

I'm sure it isn't hard to implement it.

But that's just like me asking HTML5 to have a WYSIWYG Editor like Flash.

They've been working on just turning it into a single window mode for the past year and a half (to be honest, the multi window mode is fine), but if they just had a vector paintbrush I would be happy. A raster paintbrush sucks because it shows your hand giggles.

---

### Post by Chronon on 2011-04-30
> **Lucradia said:**
> But that's not all I want though. I want to be able to create SVGs without using the paths tool. IE: why not just paint something? Or use the pencil tool?

I'm sure it isn't hard to implement it.

But that's just like me asking HTML5 to have a WYSIWYG Editor like Flash.
The problem is that for a given set of pixels there is not a unique contour that bounds them.  If you have traced bitmaps much in Inkscape you will know how different the result can be depending on what settings you use.  Also, editing the resulting vector image can reveal some surprises in how it was constructed.

---

### Post by Lucradia on 2011-04-30
> **Chronon said:**
> The problem is that for a given set of pixels there is not a unique contour that bounds them.  If you have traced bitmaps much in Inkscape you will know how different the result can be depending on what settings you use.  Also, editing the resulting vector image can reveal some surprises in how it was constructed.

And how did Flash do it then?

---

### Post by Chronon on 2011-04-30
I have never played with flash.  Does it provide a way to provide robust automatic tracing of contours based on bitmap images?  You can embed bitmaps into vector graphics formats, but this isn't what we are talking about.

You can, of course construct an algorithm for creating a contour from a bitmap image.  I'm just saying that it isn't a trivial problem and there will tend to be cases where the contour that was produced doesn't correspond to the desired contour (or set of contours).  Generally vector -> bitmap is easy (it must be converted to a bitmap to be displayed on your screen).  Bitmap -> vector is difficult and non-unique.  Font conversion faces the same basic problem.  Creating bitmap fonts from outline fonts is relatively straightforward.  Creating outline (vector) fonts from bitmap fonts can be done but the results are usually rather unimpressive.

---

