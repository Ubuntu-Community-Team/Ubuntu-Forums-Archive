---
title: "Most Complete way to globally Darker Webpages?"
date: 2009-09-11
forum: The Cafe
---

### Post by sports fan Matt on 2009-09-11
What in your opinion is the best way to achieve a dark global background for all web pages with light text?  (for those who are blinded by white on white like me?)

-Using nightshift css 
-and the ports from tjwoosta for these forums

Opinions?

---

### Post by BoyOfDestiny on 2009-09-12
I say CSS is the way to go.

I like this "lynx like" theme.
[http://delvalle26.blogspot.com/2009/02/make-your-browser-looks-like-lynx.html](http://delvalle26.blogspot.com/2009/02/make-your-browser-looks-like-lynx.html)

It offers different colors for different markup, and uses css selectors instead of just wiping all background images.

---

### Post by Viva on 2009-09-12
<Super> + N

---

### Post by yabbadabbadont on 2009-09-12
Wear sunglasses?  :D

---

### Post by Firestem4 on 2009-09-12
I use a firefox extension called InvertColors. Its a little feature incomplete and its not all purdy and nice looking but it gets the job done. it has a few intuitive features though. It should be available from add-ons.mozilla otherwise google search InvertColors Firefox

---

### Post by pwnst*r on 2009-09-12
globally darker webpages? 0_o

---

### Post by hessiess on 2009-09-12
Personally I use stylish, white backgrounds do get very annoying.

---

### Post by koleoptero on 2009-09-12
> **viva said:**
> <super> + n

:d

---

### Post by -grubby on 2009-09-12
Using some kind of negative compositing effect.

---

### Post by purgatori on 2009-09-12
> **BoyOfDestiny said:**
> I say CSS is the way to go.

I like this "lynx like" theme.
[http://delvalle26.blogspot.com/2009/02/make-your-browser-looks-like-lynx.html](http://delvalle26.blogspot.com/2009/02/make-your-browser-looks-like-lynx.html)

It offers different colors for different markup, and uses css selectors instead of just wiping all background images.

Now that's sexy!!

EDIT: Too bad it completely screws the appearance of FF itself.

---

### Post by sports fan Matt on 2009-09-12
I think I will use invert colors..The only thing is it deletes the title of webpages inside them but no biggie.

---

### Post by BoyOfDestiny on 2009-09-12
> **purgatori said:**
> Now that's sexy!!

EDIT: Too bad it completely screws the appearance of FF itself.

That's using a modified GTK+ theme. The userContent.css only effects the pages themselves, not the firefox widgets and menus. :KS

---

### Post by purgatori on 2009-09-12
> **BoyOfDestiny said:**
> That's using a modified GTK+ theme. The userContent.css only effects the pages themselves, not the firefox widgets and menus. :KS

I loaded that CSS as a usterstyle in Stylish, and it affected the appearance of the tabs and other elements of the UI.

---

### Post by BoyOfDestiny on 2009-09-12
> **purgatori said:**
> I loaded that CSS as a usterstyle in Stylish, and it affected the appearance of the tabs and other elements of the UI.


That seems like a feature of stylish or maybe something different with Ubuntu's default firefox...

I can change themes here, and it just doesn't effect anything but the pages (and viewed source of the pages...)

```

:root,body,h1,h2,h3 {background: #000000 !important; }

* {color: #00aa00 !important;
  border-color: #333333 !important;
  font-size: 10pt !important;
  font-family: "Liberation Mono" !important;
  line-height: normal !important;
  background-repeat: no-repeat !important;
  position: static;
}

```
Remove :root,

and change * to
html.* or html|*

and see if that fixes it.

---

### Post by purgatori on 2009-09-12
> **BoyOfDestiny said:**
> That seems like a feature of stylish or maybe something different with Ubuntu's default firefox...

I can change themes here, and it just doesn't effect anything but the pages (and viewed source of the pages...)

```

:root,body,h1,h2,h3 {background: #000000 !important; }

* {color: #00aa00 !important;
  border-color: #333333 !important;
  font-size: 10pt !important;
  font-family: "Liberation Mono" !important;
  line-height: normal !important;
  background-repeat: no-repeat !important;
  position: static;
}

```Remove :root,

and change * to
html.* or html|*

and see if that fixes it.

Thanks, but sadly no :( Oh well, nevermind, I'm fairly fond of nightshift anyway.

---

### Post by init1 on 2009-09-12
You could use Lynx ;)

---

### Post by HappyFeet on 2009-09-12
> **Viva said:**
> <Super> + N

That's works OK for some sites, but others it totally ruins.

---

### Post by tjwoosta on 2009-09-12
> Most Complete way to globally Darker Webpages?

I made a bunch of dark userstyles that can be found here
[http://userstyles.org/styles/browse/all/tjwoosta/popularity/desc/1]("http://userstyles.org/styles/browse/all/tjwoosta/popularity/desc/1")
Every single one of my bookmarks is styled to match my gtk theme.

There is also one called generic dark style that can be modified to work with almost any domain, although it doesn't always look the greatest.


At userstyles.org you can search for any web pages, alot of people make dark styles for their favorite sites.

---

### Post by papangul on 2009-09-12
For opera users who don't know this already > Put the css file I am attaching in '.opera/styles' and it will be available through 'View>Style' in opera menubar. It changes the background to black and text to cyan and is effective 'globally'. You may tweak it to change the two colors or in any other way to suit your taste.

---

