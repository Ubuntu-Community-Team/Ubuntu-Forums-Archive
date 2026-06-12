---
title: "Webkit browsers rendering pages differently?"
date: 2011-08-11
forum: The Cafe
---

### Post by capink on 2011-08-11
I've been using different webkit browsers for some time now. I noticed that they render pages differently. Each one has a problem rendering a specific website.

It is not about them using different versions of webkit, as I use them all one the same distro. Plus these problems have been going for more than one year for the same websites covering three Ubuntu cycles.

Obviously, I made the wrong assumption that browsers using the same rendering engine would render pages exactly the same.

Can someone please explain the boundaries between the functions of a browser and its rendering engine.

---

### Post by el_koraco on 2011-08-11
Which ones? There's Chrome's webkit, webkit-gtk for Midori and Epiphany, webkit-qt for Rekonq and Arora...
I'd rate them
Chrome
webkit-qt
webkit-gtk

They all choke on OMGUbuntu, that's the kicker, only Chrome can keep going, while the other crash :lolflag:

---

### Post by jerenept on 2011-08-11
> **el_koraco said:**
> Which ones? There's Chrome's webkit, webkit-gtk for Midori and Epiphany, webkit-qt for Rekonq and Arora...
I'd rate them
Chrome
webkit-qt
webkit-gtk

They all choke on OMGUbuntu, that's the kicker, only Chrome can keep going, while the other crash :lolflag:

strange, i've never had any problems with omgubuntu.

---

### Post by el_koraco on 2011-08-11
Did you try opening up three or four tabs and then scroll on the first one? Mine always chokes up a little (Chrome, that is, the others either crash or "become unresponsive"). I tried both openJDK and SunJava, thinking maybe something is amiss there, but to no avail.

---

### Post by kaldor on 2011-08-11
All I know is that WebKit is highly standards compliant. The only time a website has trouble is because of non-standard or browser-specific markup. This is, of course, entirely from my experience. I use Firefox as my main browser, but use Chromium quite frequently.

---

### Post by juancarlospaco on 2011-08-11
Chromium-Webkit is compatible with HTML5, 
Firefox dont (random example: it dont support 3D Transforms).

So the correct appereance of a website should be the Webkit ones...

---

### Post by capink on 2011-08-11
> **kaldor said:**
> All I know is that WebKit is highly standards compliant. The only time a website has trouble is because of non-standard or browser-specific markup. This is, of course, entirely from my experience. I use Firefox as my main browser, but use Chromium quite frequently.

The problem is not webkit not able being able to render certain page. This is understandable especially if the page is not standard compliant. The main problem is that some webkit browser renders the page, and another webkit browser renders it differently. Why this happens when the rendering engine is the same.

---

### Post by kaldor on 2011-08-11
> **capink said:**
> The problem is not webkit not able being able to render certain page. This is understandable especially if the page is not standard compliant. The main problem is that some webkit browser renders the page, and another webkit browser renders it differently. Why this happens when the rendering engine is the same.

There could be variations between different browsers. And like some people mentioned, it could be due to webkit-qt and webkit-gtk.

---

### Post by jpeddicord on 2011-08-11
WebKit changes relatively frequently, so what might work in one browser might work differently in another. Then there's the different flavors of it, such as GTK, Qt, Chrome, Android... etc.
And there there are the different default font settings of each browser, which further move things around. :P

---

### Post by mcduck on 2011-08-12
It's hard to say without seeing a screenshot of the rendered pages or something, there are unlimited amount ways how a page can be rendered "differently", most of them for different reasons of course.

Anyway, you could start by checking that each browser is set to use same fonts, and same font sizes. Sometimes  even very similar looking font can actually take different amount of space, and depending on how the page is designed that can change the page's layout and look quite radically.

---

### Post by capink on 2011-08-12
> **jpeddicord said:**
> And there there are the different default font settings of each browser, which further move things around. :P



> **mcduck said:**
> Anyway, you could start by checking that each browser is set to use same fonts, and same font sizes. Sometimes  even very similar looking font can actually take different amount of space, and depending on how the page is designed that can change the page's layout and look quite radically.

Thank you both. That turned out be the cause of the problem.

---

