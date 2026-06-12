---
title: "So called 'Web Safe' fonts..."
date: 2009-04-13
forum: The Cafe
---

### Post by smartboyathome on 2009-04-13
I don't like how my class uses the term Web Safe fonts to refer to fonts that are proprietary to Microsoft and can only be used on Microsoft or Mac computers. On linux, you have to install the illegal (or legally gray?) msttcorefonts to get these, but they are "web safe" because they are included on the big 2. Is this right?

---

### Post by ad_267 on 2009-04-13
That's pretty much the way it is I guess. It's always good practice to include a few alternative fonts in your style sheet and end with a generic family like sans-serif.

---

### Post by sekinto on 2009-04-13
I think CSS3 has this awesome feature that downloads the font file (if provided) when you visit a site and don't have it. I hope people use it.

As for web-safe fonts, I would consider web-safe fonts to not be actual fonts but generic families like san-serif, serif, monospace, etc.

---

### Post by Mokoma on 2009-04-13
> **ad_267 said:**
> That's pretty much the way it is I guess. It's always good practice to include a few alternative fonts in your style sheet and end with a generic family like sans-serif.

i use trebuchet ms for everything :popcorn:

---

### Post by smartboyathome on 2009-04-13
> **sekinto said:**
> As for web-safe fonts, I would consider web-safe fonts to not be actual fonts but generic families like san-serif, serif, monospace, etc.

I would agree with that, but the problem is that my class is teaching everyone to use Arial, Times New Roman, Comic Sans MS, et al for their pages, as those are the web safe fonts. :(

---

### Post by ad_267 on 2009-04-13
Really, the majority of people are going to have those fonts. They're not going to have Deja Vu or any of the free fonts. I think it's OK as long as you specify the default family.

---

### Post by CharmyBee on 2009-04-14
Do they also teach you to as much as possible, use only the Web Safe 8-bit color palette too so you don't offend the majority of 8bpp desktop users? :P

---

### Post by samjh on 2009-04-14
> **smartboyathome said:**
> I would agree with that, but the problem is that my class is teaching everyone to use Arial, Times New Roman, Comic Sans MS, et al for their pages, as those are the web safe fonts. :(

It's true.  They are safe fonts.

Hardly anyone has "free" fonts, while most users have Times New Roman, Arial, Courier New, Verdana, etc.  Keep in mind that Linux users are in the minority; the majority are Microsoft Windows users.

As for "Core fonts for the Web" from Microsoft (aka. msttcorefonts), they are legally redistributable as long as they are kept in their original packaging and file names, and not used for commercial profit.  This is why Debian, Ubuntu, and other Linux distros make them available.

My favourites happen to be Trebuchet MS and Verdana. :)

---

### Post by SunnyRabbiera on 2009-04-14
> **smartboyathome said:**
> I would agree with that, but the problem is that my class is teaching everyone to use Arial, Times New Roman, Comic Sans MS, et al for their pages, as those are the web safe fonts. :(

Well in linux oftentimes the liberation TTF fonts are used, or Dejevu.
I never had a problem with the Dejevu fonts myself.
Sans is seems universal no matter if I use it in windows or Linux, Comic sans MS will turn into Dejevu sans is very close...

---

### Post by sekinto on 2009-04-14
I personally like the font Geogia, a beautiful example of its usage can be seen here:
[http://poignantguide.net/ruby/chapter-2.html](http://poignantguide.net/ruby/chapter-2.html)
Very smooth and readable.

---

### Post by Barrucadu on 2009-04-14
In your style sheet specify free fonts ahead of the 'safe' ones. Thus, if the user has those fonts installed, they'll be used. If not, it'll fall back to something worse, but working.
Also, if CSS3 web fonts work in the three main browsers any time soon (I know they do in Opera 10, not sure about FF, almost certainly not in IE), then that will no longe be a problem as browsers will just download the font file if need be.

---

### Post by anurag_envyinc on 2009-04-14
i think i might use Segoe UI

---

### Post by miggols99 on 2009-04-14
> **Barrucadu said:**
> In your style sheet specify free fonts ahead of the 'safe' ones. Thus, if the user has those fonts installed, they'll be used. If not, it'll fall back to something worse, but working.
Also, if CSS3 web fonts work in the three main browsers any time soon (I know they do in Opera 10, not sure about FF, almost certainly not in IE), then that will no longe be a problem as browsers will just download the font file if need be.
This is what I do! I put Liberation Sans first, then Dejavu Sans, then Arial, Verdana, sans-serif.

---

### Post by samjh on 2009-04-14
> **miggols99 said:**
> This is what I do! I put Liberation Sans first, then Dejavu Sans, then Arial, Verdana, sans-serif.

I'm curious.  Why not put the fonts that are more likely to be used first?  For example, if your prefered font is Verdana: Verdana, Arial, Dejavu Sans, sans-serif.

---

### Post by Mehall on 2009-04-14
> **samjh said:**
> I'm curious.  Why not put the fonts that are more likely to be used first?  For example, if your prefered font is Verdana: Verdana, Arial, Dejavu Sans, sans-serif.

Because if he wants to use the free fonts, then he puts them first so that is his font of choice, then only those using MS see the other fonts, but if you're using Linux, you'll see free fonts even if you're using msttcorefonts.

---

### Post by Tristam Green on 2009-04-14
> **smartboyathome said:**
> Comic Sans MS

Abomination :lolflag:

---

