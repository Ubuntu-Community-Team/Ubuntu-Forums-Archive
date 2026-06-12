---
title: "Per-pixel alphablending support in a window manager?"
date: 2006-02-25
forum: The Cafe
---

### Post by Alterion on 2006-02-25
so i'm new to linux and i wondered if this can be achived with any current window manager if not am i right in think this is the kind of thing that KDE4 will support?- to get a feel for what i mean check out this skin for windowsblinds [http://www.deviantart.com/view/29094815/](http://www.deviantart.com/view/29094815/) it enaqbles all sorts of cool effects like alphablended corners ect..:mrgreen:  A

---

### Post by welsh_spud on 2006-02-25
I believe that [this]("http://ubuntuforums.org/showthread.php?t=115974&highlight=knome") HOWTO has what you are looking for.

Here is a [screenshot]("http://www.ubuntuforums.org/gallery/showimage.php?i=1734&original=1&c=2")

---

### Post by Alterion on 2006-02-25
That is about half-way to what i want- it provides the transparency effects but thier just simple transparencies. To get a better idea look at the corners of the skin i posted and then look at the screenshot you posted- by defining the alpha-channel we have perpixel alpha blending and the option for certain area's to be poaque while others are translucent ect

---

### Post by vayu on 2006-02-26
[QUOTE=Alterion]That is about half-way to what i want- it provides the transparency effects but thier just simple transparencies. To get a better idea look at the corners of the skin i posted and then look at the screenshot you posted- by defining the alpha-channel we have perpixel alpha blending and the option for certain area's to be poaque while others are translucent ect[/QUOTE]

I still don't understand what you are describing.   I see the rounded corners in the windowblinds screenshot are smoother looking, is that it, or is there more?
The description describes several things that are "per pixel".

---

### Post by Alterion on 2006-02-26
that is essentially it but per-pixel means that each pixel of the window can be assaigned a differnt transparency value to all of the others around it. It allows for smoother corners ect Its essesntially the difference between a .png image and a .bmp image at 80% opacity i can;t really explain it further than that.

---

### Post by red_Marvin on 2006-02-26
He might mean alpha blending combined with anti-aliasing.

---

### Post by Kvark on 2006-02-26
It sounds like instead of setting the whole window to have for example 70% opacity he wants to set different opacity values for each individual pixel in the window. So that some pixels in a window can have for example 20% opacity at the same time as other pixels in the same window has 60% opacity.

The only thing thats needed to achieve that is proper support for transperant png images but I have no idea if any window/composite managers have that yet.

---

### Post by mcduck on 2006-02-26
I think Compiz does what you want. But it only has one theme.. :)

---

### Post by joflow on 2006-02-26
[QUOTE=mcduck]I think Compiz does what you want. But it only has one theme.. :)[/QUOTE]

Right now I'm in love with the cairo + compiz combo.  Best thing ever to hit desktop computing.

---

### Post by MKlemm on 2008-06-14
AFAIK what we can see in the Compiz screenshot above isn't a real example of per-pixel alphablending, since the transparent/blending part is only the window title bar, over which the WM/CompMgr has total control.

I doubt that real per-pixel alphablending will be possible with the current version of compiz, since applying the alpha mask actually takes place inside the application, which might contain its own model of combining graphics layers. The window manager/compiz currently only treats windows "as a whole", without looking at what an application really does "inside" the window, so it also doesn't apply any alpha masks from set in the application to the surface it renders the window on.
A "hack" would be necessary to achive that: Compiz would need to have an interface on which an application can set it's own alpha mask that Compiz associates with the application's window, and Compiz would use that when rendering the application window. To my knowledge, there is no such interface yet.
Recently, the Java Runtime Environment has added support for this, but it doesn't currently work with Compiz correctly, as I could verify. The other new features, like shaped windows and evenly translucent windows work very well, if you have turned on Compiz...

---

### Post by klange on 2008-06-14
Major bump there Mr. MKlemm.

Anyway, if anyone happens to be interested in this ancient topic - it was done and quite simply. [Obligatory screenshot](http://random.ogunderground.com/compiz/cftheme/fusion-live-theme.png). Most apps don't support it, and forcing them to almost always ends badly.
[Apps with support](http://www.cimitan.com/murrine/rgba-support/list). Also, on a side note, with DRI2 (on Intel), OpenGL apps have proper alphas under certain conditions.

[insert necromancing picture here]

---

### Post by madjr on 2008-06-14
lulz

---

### Post by acelin on 2008-06-14
And people said my theme (the original one) couldnt be done!

---

### Post by madjr on 2008-06-15
> **acelin said:**
> And people said my theme (the original one) couldnt be done!

who said that :o

anything can be done with enough work :)

---

### Post by FuturePilot on 2008-06-15
> **WindowsSucks said:**
> Major bump there Mr. MKlemm.

Anyway, if anyone happens to be interested in this ancient topic - it was done and quite simply. [Obligatory screenshot](http://random.ogunderground.com/compiz/cftheme/fusion-live-theme.png). Most apps don't support it, and forcing them to almost always ends badly.
[Apps with support](http://www.cimitan.com/murrine/rgba-support/list). Also, on a side note, with DRI2 (on Intel), OpenGL apps have proper alphas under certain conditions.

[insert necromancing picture here]

*drools* :D
Were did you get that wallpaper?

---

### Post by hanzomon4 on 2008-06-15
> **madjr said:**
> who said that :o

anything can be done with enough work :)

Like turning ID into science? I think not... 

joking folks..

Sweet theme by the way

---

### Post by MKlemm on 2008-06-16
Oh, sorry for the bump...

And I'm happy to see that this is actually supported now!

But now comes the question: How can you make your own application support this? Is there any docs?

Thanks,
Mirko

---

### Post by klange on 2008-06-16
It's about three lines at the start of a GTK application that switches it to an ARGB colormap and *viola*, the Murrine engine will draw with clear stuff. I'd have to look it up, it's not something I tend to remember. I think the newest version of Clearlooks (SVN only) will do it, they're both from Cimitan...

(Also, works with Metacity+compositing, of course)

---

### Post by MKlemm on 2008-06-16
> **WindowsSucks said:**
> It's about three lines at the start of a GTK application that switches it to an ARGB colormap and *viola*, the Murrine engine will draw with clear stuff. I'd have to look it up, it's not something I tend to remember. I think the newest version of Clearlooks (SVN only) will do it, they're both from Cimitan...

(Also, works with Metacity+compositing, of course)

Thanks a lot! I think if it's that simple, I'm gonna find it!

---

