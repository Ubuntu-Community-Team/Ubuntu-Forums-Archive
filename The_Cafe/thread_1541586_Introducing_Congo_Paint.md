---
title: "Introducing Congo Paint"
date: 2010-07-29
forum: The Cafe
---

### Post by Simian Man on 2010-07-29
Hello all,

I have been working for some time on a simple paint program for GTK+ called Congo Paint.  It has now reached a point where it is fairly usable - especially for small scale pixel art which is what I wrote it for.  So I decided to release the current version as 0.1!

**Features**
[LIST]
[*]Loading and saving image files
[*]Zooming in and out
[*]Unlimited undo and redo
[*]Lots of tools:
[LIST]
[*]Pencil
[*]Paint can
[*]Line
[*]Spray can
[*]Rectangle
[*]Ellipse
[*]Eyedropper
[*]Paint brush with 4 strokes
[/LIST]
[*]Easy to use and familiar interface
[/LIST]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164896&stc=1&d=1280414888[/IMG]

**Caveats**
As it is only the 0.1 release, there are unfortunately a few problems with Congo Paint still:
[LIST]
[*]There is no select, copy, cut or paste functionality yet
[*]Some functionality is implemented in a naive and slow way
[*]In particular flood fill should not be used on areas more than a few hundred square pixels unless you want to hang your computer.
[/LIST]

You can [download Congo Paint here]("http://code.google.com/p/congo-paint/downloads/list") in source form.  Instructions on building it are found in the README.  If anyone has any problems or finds any bugs other than the ones I mentioned, please post here or file a bug on the Google Code site.

I have already started using it myself for some purposes.  I hope somebody else finds it useful :)

---

### Post by gnomeuser on 2010-07-29
That looks really cool, have you thought of working with the pinta people?

---

### Post by Simian Man on 2010-07-29
> **gnomeuser said:**
> That looks really cool, have you thought of working with the pinta people?

Pinta is a really cool project, but it's also more than I want.  I just wanted a *really* simple program for doing pixel art.  I don't need layers or affects or anything like that.  I honestly just *really* like MS Paint and wanted it for GTK+ :).  Thanks for your comment!

---

### Post by RiceMonster on 2010-07-29
Cool. I think I'll check it out when I get home the evening. What language are you writting this in, C?

Edit: I should have looked at the site. It says you're using C#.

---

### Post by Simian Man on 2010-07-29
> **RiceMonster said:**
> Cool. I think I'll check it out when I get home the evening. What language are you writting this in, C?

Edit: I should have looked at the site. It says you're using C#.

Hey thanks.  Yeah, another reason I started this was because I wanted to do a good-sized project with C# and Monodevelop.  It's a really nice development platform.

---

### Post by RiceMonster on 2010-07-29
I've written some minor paint stuff in Java for a small college assignment before, and I've been telling myself I'm going to learn C# for a while, so I'm pretty interested in looking at your code.

---

### Post by Simian Man on 2010-07-29
> **RiceMonster said:**
> I've written some minor paint stuff in Java for a small college assignment before, and I've been telling myself I'm going to learn C# for a while, so I'm pretty interested in looking at your code.

The code itself is pretty hackish because I didn't make much of an effort to learn C# or GTK before hand.  I just kind of started coding :).  I am planning on a refactoring phase, but wanted to make an initial release while it was still somewhat stable.

---

### Post by Cuddles McKitten on 2010-07-29
Did you draw the little monkey-in-a-hat icon for the program in your program? :)

---

### Post by Simian Man on 2010-07-29
> **Cuddles McKitten said:**
> Did you draw the little monkey-in-a-hat icon for the program in your program? :)

No, it's an svg, so I used Inkscape.  I did use my program to make the tool icons and mouse cursors, but those need some work to I think :).

---

### Post by Ric_NYC on 2010-07-29
Web-based painting app:

[http://www.sumopaint.com/app/](http://www.sumopaint.com/app/)


No need to install anything.

---

### Post by realzippy on 2010-07-29
> **Ric_NYC said:**
> Web-based painting app:

[http://www.sumopaint.com/app/](http://www.sumopaint.com/app/)


No need to install anything.



Spoiler.

---

### Post by Simian Man on 2010-07-29
> **Ric_NYC said:**
> Web-based painting app:

[http://www.sumopaint.com/app/](http://www.sumopaint.com/app/)


No need to install anything.

That's actually pretty cool for a web app, but isn't really what I want.  I like desktop apps, and it's a bit complicated.  Worst of all it doesn't seem to let me turn off anti-aliasing which makes it useless for pixel work.  I love the symmetry tool though, that's very neat.

---

### Post by Ric_NYC on 2010-07-29
> **Simian Man said:**
> That's actually pretty cool for a web app, but isn't really what I want.  I like desktop apps, and it's a bit complicated.  Worst of all it doesn't seem to let me turn off anti-aliasing which makes it useless for pixel work.  I love the symmetry tool though, that's very neat.

Ok. I agree!

---

### Post by user1397 on 2010-08-04
I posted this on my thread, but it makes more sense here:

Not too shabby at all Simian Man, I thought Congo Paint was quite simple yet effective. I'll be watching its progress.

As for any bugs I had, the only thing was I couldn't use the spray nor the bucket filler (don't know what that's called exactly) too much at one time, or else it would freeze or lock up. Other than that, tried all features and everything worked. Good job!

---

### Post by phrostbyte on 2010-08-04
You didn't use MonoDevelop's GTK+ designer? Wow. :)

---

### Post by forrestcupp on 2010-08-04
> **Ric_NYC said:**
> Web-based painting app:

[http://www.sumopaint.com/app/](http://www.sumopaint.com/app/)


No need to install anything.Anything anybody makes is going to have a hundred different things out there like it that are already way better.  Sometimes it just exciting to create something for yourself and have it actually work.

> **phrostbyte said:**
> You didn't use MonoDevelop's GTK+ designer? Wow. :)Those designers are for cheaters and noobs. :D

---

### Post by Simian Man on 2010-08-04
> **ubuntuman001 said:**
> I posted this on my thread, but it makes more sense here:

Not too shabby at all Simian Man, I thought Congo Paint was quite simple yet effective. I'll be watching its progress.

As for any bugs I had, the only thing was I couldn't use the spray nor the bucket filler (don't know what that's called exactly) too much at one time, or else it would freeze or lock up. Other than that, tried all features and everything worked. Good job!
Thanks for the feedback!  I knew that the paint can tool was extremely slow, but I hadn't noticed the spray can, thanks for that.  I have to rewrite the drawing code to use only GDK pixbufs.  Right now it uses pixmaps which make things easier, but are a lot slower.  I've been putting this off for a while, but the positive feedback is good motivation :).

> **phrostbyte said:**
> You didn't use MonoDevelop's GTK+ designer? Wow. :)
The interface is such a small part of the code that I didn't think I'd gain that much from using it.

---

### Post by phrostbyte on 2010-08-04
> **Simian Man said:**
> Thanks for the feedback!  I knew that the paint can tool was extremely slow, but I hadn't noticed the spray can, thanks for that.  I have to rewrite the drawing code to use only GDK pixbufs.  Right now it uses pixmaps which make things easier, but are a lot slower.  I've been putting this off for a while, but the positive feedback is good motivation :).


The interface is such a small part of the code that I didn't think I'd gain that much from using it.

It's quite hard to make a seemingly simple algorithm like flood fill ("paint can") efficient. Take a look at the source code of Pinta, there should be a FloodTool.cs file in there under PintaTools. You should be able to mostly ninja the FillStencilFromPoint method in there, which implements flood fill.

---

### Post by Simian Man on 2010-08-04
> **phrostbyte said:**
> It's quite hard to make a seemingly simple algorithm like flood fill ("paint can") efficient. Take a look at the source code of Pinta, there should be a FloodTool.cs file in there under PintaTools. You should be able to mostly ninja the FillStencilFromPoint method in there, which implements flood fill.

It's actually not my algorithm that's slow, but the way I get the value of each pixel from the pixmap to test whether or not it should be filled.  I checked the Pinta source code and they use largely the same basic algorithm I use.

Once I rewrite this all to use pixbufs it won't be a problem :).

---

### Post by phrostbyte on 2010-08-04
> **Simian Man said:**
> It's actually not my algorithm that's slow, but the way I get the value of each pixel from the pixmap to test whether or not it should be filled.  I checked the Pinta source code and they use largely the same basic algorithm I use.

Once I rewrite this all to use pixbufs it won't be a problem :).

I can see three optimisations you make that doesn't involve changing how you draw to the screen:

1. Use System.Collections.Generic.Queue<Point>  instead of System.Collections.Queue 
2. Change "Point" to a struct instead of a class.
3. Memorise (put in memory) CongoPaint.Canvas.GetWidth() and CongoPaint.Canvas.GetHeight()

EDIT: I made these changes, and it is still quite slow. :(

---

### Post by Simian Man on 2010-08-04
> **phrostbyte said:**
> I can see three optimisations you make that doesn't involve changing how you draw to the screen:

1. Use System.Collections.Generic.Queue<Point>  instead of System.Collections.Queue 
2. Change "Point" to a struct instead of a class.
3. Memorise (put in memory) CongoPaint.Canvas.GetWidth() and CongoPaint.Canvas.GetHeight()

EDIT: I made these changes, and it is still quite slow. :(

1.  Oh cool, I didn't really realize C# had proper generics.  I thought it was like Java.
2.  Good idea.  I like how in C# there is a difference between classes and structs and I should take advantage of that.
3.  Good idea :).

Another optimization that Pinta uses is they scan horizontal lines directly rather than enqueing the points.  Thanks a lot for the tips.

I am sure that the cause of the slowdown is from setting and getting the pixels in the Canvas code.  I tried commenting out those calls and the tool works nearly instantly.  Of course it doesn't actually *do* anything, but it does loop through the pixels and enqueue them properly :).

Thanks again for the tips.

---

### Post by phrostbyte on 2010-08-04
I'm surprised getting and setting pixels is really all that slow. It makes me feel something is wrong with that code path.

---

### Post by gnomeuser on 2010-08-05
> **Simian Man said:**
> Pinta is a really cool project, but it's also more than I want.  I just wanted a *really* simple program for doing pixel art.  I don't need layers or affects or anything like that.  I honestly just *really* like MS Paint and wanted it for GTK+ :).  Thanks for your comment!

That is an admirable goal and I think it is the path towards an application that can be installed by default. Pinta is very good, however I was thinking more in the area of pilfering their likely fairly optimized backend and simply replacing the UI with the Congo Paint (brilliant name btw. I laugh every time I hear it) UI.

---

### Post by gnomeuser on 2010-08-05
[QUOTE=Simian Man]1. Oh cool, I didn't really realize C# had proper generics. I thought it was like Java.
[/QUOTE]

C# 3.0's big feature was Generics

Just you wait till you see C# 4.0:

[http://channel9.msdn.com/pdc2008/TL16/](http://channel9.msdn.com/pdc2008/TL16/)

---

### Post by Simian Man on 2010-08-05
> **phrostbyte said:**
> I'm surprised getting and setting pixels is really all that slow. It makes me feel something is wrong with that code path.
Yeah, it is because I am using pixmaps and have to call the GetImage function to get a 1x1 image for each pixel I need to read and DrawPoint for each point I need to set.  I need to use a pixbuf instead and figure out how to get and set pixels from that.  If it were C, I'd just be able to read and write ints from an array.

> **gnomeuser said:**
> That is an admirable goal and I think it is the path towards an application that can be installed by default. Pinta is very good, however I was thinking more in the area of pilfering their likely fairly optimized backend and simply replacing the UI with the Congo Paint

I won't copy and paste any of their code directly, but I will definitley see how they access their pixbufs :).

> **gnomeuser](brilliant name btw. I laugh every time I hear it)[/quote]
Thanks :).

[QUOTE=gnomeuser said:**
> C# 3.0's big feature was Generics

Just you wait till you see C# 4.0:

[http://channel9.msdn.com/pdc2008/TL16/](http://channel9.msdn.com/pdc2008/TL16/)

Cool link, thanks.  I will watch the rest of it when I get home :).

---

