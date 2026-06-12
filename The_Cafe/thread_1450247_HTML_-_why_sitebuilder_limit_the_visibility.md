---
title: "HTML - why sitebuilder limit the visibility?"
date: 2010-04-08
forum: The Cafe
---

### Post by yester64 on 2010-04-08
I often see sites that are build to be only viewed in a certain way which is 1024x768.
So if you have a widescreen monitor, the pages doesn't fill the rest of the screen.
This can be kinda annoying.
This forum, as an example, allows to fill the screen.
So why is it, that pages are designed like that.
I did webpages a long time ago and at that time it was fairly easy to build one.
Now its more complicated and i am not sure if i could do a page.

---

### Post by Psumi on 2010-04-08
Some people don't maximize their browsers.

Always good to do percentage widths/heights.

---

### Post by Eestlane on 2010-04-08
Making dynamic width pages with css, without tables, requires more time than simply setting pixels.

The positive sides are that the text line will remain at readable length and the overall design would not look weird.

The negative side is wasted screen space.

---

### Post by Psumi on 2010-04-08
> **Eestlane said:**
> Making dynamic width pages with css, without tables, requires more time than simply setting pixels.

The positive sides are that the text line will remain at readable length and the overall design would not look weird.

The negative side is wasted screen space.

Some CSS Styles won't work in IE though, and some of my friends are too stubborn to switch to a "good" browser.

---

### Post by Eestlane on 2010-04-08
And?

You can basically still do stuff for IE(6) with some workaround, the biggest cost is wasted time, though.

---

### Post by Psumi on 2010-04-08
> **Eestlane said:**
> And?

You can basically still do stuff for IE(6) with some workaround, the biggest cost is wasted time, though.

As long as it looks pretty in all browsers, I care not for standards.

---

### Post by loell on 2010-04-08
making a page fluid even using css frameworks seem to take a lot of efforts. but if you get through with it, it's also rewarding, pagewise that is.

I still prefer fixed width, when time is of the essence. ;)

---

### Post by aklo on 2010-04-09
I think fixed width sites are still the norm.

Reason why this forum has a fluid width is simply because there is not much design in it. Just text and text and text.

I'm not sure about you guys but i view a fix width page with a maximized browser everytime.

I'm on 1680x1050.

---

### Post by mcduck on 2010-04-09
There's also a limit for how long lines of text can be to be easily readable, so considering the high resolutions some monitors have these days it makes sense to limit how wide the layout can scale to.

Not to mention the problems that you get with graphics when you try to make a site's layout scalable. Until  we get support for scalable SVG or something like that, making the layout scalable will place some serious limits on what kind of visual appearance you can have.

When it comes to just the content, and graphics are not concerned, I have never had any problems with making scalable layouts with CSS. Apart perhaps from issues caused by poor CSS support on old IE versions, which was still somehting you could work around even if it required a bit more code than you'd really need.

---

### Post by madnessjack on 2010-04-09
I tend to have a min and a max width that I allow the page to be resized to

---

