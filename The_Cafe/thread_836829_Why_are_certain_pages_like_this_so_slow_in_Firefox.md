---
title: "Why are certain pages like this so slow in Firefox?"
date: 2008-06-21
forum: The Cafe
---

### Post by hotweiss on 2008-06-21
[http://www.damninteresting.com/?p=964](http://www.damninteresting.com/?p=964)

Why are certain pages like this so slow in Firefox? It seems that you need a Pentium 10,000 to scroll through the page.

I'm using Firefox 3.

---

### Post by cardinals_fan on 2008-06-21
It's because it's a long page.  Still works fine in Opera though :)

---

### Post by RiceMonster on 2008-06-21
I use firefox. It scrolls just fine for me. Use Page Up/Dn if you think it's too slow.

---

### Post by mrgnash on 2008-06-21
It's rather puzzling. I find that the following sites (not just pages, so it has nothing to do with length) are quite sluggish for me: [Neurologica Blog](http://www.theness.com/neurologicablog/index.php) and [Oliver Kamm](http://oliverkamm.typepad.com/).

---

### Post by Can+~ on 2008-06-21
Talking about that, here's "The World's Highest Website":

[http://worlds-highest-website.com/#pos1](http://worlds-highest-website.com/#pos1)

---

### Post by hotweiss on 2008-06-21
> **Can+~ said:**
> Talking about that, here's "The World's Highest Website":

[http://worlds-highest-website.com/#pos1](http://worlds-highest-website.com/#pos1)

It actually scrolls fine here...

---

### Post by hotweiss on 2008-06-21
> **mrgnash said:**
> It's rather puzzling. I find that the following sites (not just pages, so it has nothing to do with length) are quite sluggish for me: [Neurologica Blog](http://www.theness.com/neurologicablog/index.php) and [Oliver Kamm](http://oliverkamm.typepad.com/).

Yes exactly. The two sites that you provided exhibit the same slow behavior! Those are simple sites....

---

### Post by hanzomon4 on 2008-06-21
Try facebook, it's god awful. It's just the linux of version firefox however. Which sucks because it's almost perfect. Does this happen on other distros besides Ubuntu?

---

### Post by FuturePilot on 2008-06-22
> **mrgnash said:**
> It's rather puzzling. I find that the following sites (not just pages, so it has nothing to do with length) are quite sluggish for me: [Neurologica Blog](http://www.theness.com/neurologicablog/index.php) and [Oliver Kamm](http://oliverkamm.typepad.com/).

It's something really weird with the background images that those sites use. If you adblock them and reload the page it's really fast.

Same goes for the site in the OP's post.

---

### Post by Can+~ on 2008-06-22
> **FuturePilot said:**
> It's something really weird with the background images that those sites use. If you adblock them and reload the page it's really fast.

Same goes for the site in the OP's post.

You're right.

Looks like the problem resides in the background attachment method (fixed). Fixed attachment makes images (or anything in fact) look like they stay on the same place when scrolling.

---

### Post by reyfer on 2008-06-22
There must be something wrong with my Firefox, every page and site mentioned here loads and scrolls fast, fast, fast on my machine.....what's wrong with my Firefox?

---

### Post by EdThaSlayer on 2008-06-22
Maybe

a)You have TONS of tabs open
b)Have a slow computer...
c) Just unlucky-and firefox has become a memory hog for you by now


It works alright with me!
And I have a single core AMD Athlon 64 3000+ processor. :confused:

---

### Post by FuturePilot on 2008-06-22
I think it might have more to do with the graphics card than the CPU. I'm wondering if it has something to do with 2D rendering and some drivers. Or maybe even just if you have an older card.
I have an old GeForce 2 Go and scrolling on those sites is painful.

---

### Post by hotweiss on 2008-06-22
> **EdThaSlayer said:**
> Maybe

a)You have TONS of tabs open
b)Have a slow computer...
c) Just unlucky-and firefox has become a memory hog for you by now


It works alright with me!
And I have a single core AMD Athlon 64 3000+ processor. :confused:

a) no tabs open
b) I have a Core 2 Duo overclocked at 3.8 GHz.
c) happens on every install

---

### Post by hanzomon4 on 2008-06-22
> **EdThaSlayer said:**
> Maybe

a)You have TONS of tabs open
b)Have a slow computer...
c) Just unlucky-and firefox has become a memory hog for you by now


It works alright with me!
And I have a single core AMD Athlon 64 3000+ processor. :confused:

a)no
b)no
c)no

It's only certain sites, for me only facebook. It's not the sites though cause they work with other browsers even firefox on OSX.

---

### Post by hotweiss on 2008-06-22
> **FuturePilot said:**
> I think it might have more to do with the graphics card than the CPU. I'm wondering if it has something to do with 2D rendering and some drivers. Or maybe even just if you have an older card.
I have an old GeForce 2 Go and scrolling on those sites is painful.

I have a Nvidia 8800GT overclocked at 700 MHz.

---

### Post by FuturePilot on 2008-06-22
> **hotweiss said:**
> I have a Nvidia 8800GT overclocked at 700 MHz.

Ok maybe not :p
I know the Nvidia drivers never have been too great at 2D rendering, perhaps that's it. Anyone see slow scrolling on a non Nvidia card?

---

### Post by hotweiss on 2008-06-22
Hahahaha, check this out:

[http://lubosz.de/Firefox3PerformanceBug/](http://lubosz.de/Firefox3PerformanceBug/)

And this bug has been reported:

[https://bugs.launchpad.net/firefox/+bug/125970](https://bugs.launchpad.net/firefox/+bug/125970)

---

### Post by mrgnash on 2008-06-22
> **hotweiss said:**
> Hahahaha, check this out:

[http://lubosz.de/Firefox3PerformanceBug/](http://lubosz.de/Firefox3PerformanceBug/)

And this bug has been reported:

[https://bugs.launchpad.net/firefox/+bug/125970](https://bugs.launchpad.net/firefox/+bug/125970)

Hehehe good to know. Well, a quick and dirty fix seems to be selecting 'no style' in the view menu when viewing one of these sites that causes the slowdown.

---

### Post by FuturePilot on 2008-06-22
> **hotweiss said:**
> Hahahaha, check this out:

[http://lubosz.de/Firefox3PerformanceBug/](http://lubosz.de/Firefox3PerformanceBug/)

And this bug has been reported:

[https://bugs.launchpad.net/firefox/+bug/125970](https://bugs.launchpad.net/firefox/+bug/125970)
Ah, good to know it's been reported.

> **mrgnash said:**
> Hehehe good to know. Well, a quick and dirty fix seems to be selecting 'no style' in the view menu when viewing one of these sites that causes the slowdown.

The other alternative is to adblock the image. You still get to enjoy the page layout. :)

---

### Post by hotweiss on 2008-06-22
> **FuturePilot said:**
> Ah, good to know it's been reported.



The other alternative is to adblock the image. You still get to enjoy the page layout. :)

Yes, it's been reported over a year ago. A solution doesn't look like it's coming any time soon, lol.

---

### Post by hotweiss on 2008-06-22
According to this:

[http://www.nvnews.net/vbulletin/showthread.php?p=1672814](http://www.nvnews.net/vbulletin/showthread.php?p=1672814)

...it seems to be a driver issue. I hope what ever fixes that bug, fixes the Flash video tearing also.

---

### Post by bufsabre666 on 2008-06-22
everythings a-okay in swiftweasel, no lag or anything, do you have smooth scrolling enabled?

---

### Post by hotweiss on 2008-06-22
> **bufsabre666 said:**
> everythings a-okay in swiftweasel, no lag or anything, do you have smooth scrolling enabled?

Yes, smooth scrolling is enabled. Do you have a Nvidia video card?

---

### Post by bufsabre666 on 2008-06-22
> **hotweiss said:**
> Yes, smooth scrolling is enabled. Do you have a Nvidia video card?

yeah, 7600gt with 173.14.05 drivers

---

### Post by hotweiss on 2008-06-22
> **bufsabre666 said:**
> everythings a-okay in swiftweasel, no lag or anything, do you have smooth scrolling enabled?

Wow, swiftweasel really helped out with the page I originally had trouble with, but it still had trouble with this page:

[http://lubosz.de/Firefox3PerformanceBug/](http://lubosz.de/Firefox3PerformanceBug/)

It seems that the CPU tweaks help out the renderer, but they can only do so much. None the less, Swiftweasel is my new browser, lol.

---

### Post by FuturePilot on 2008-06-22
> **hotweiss said:**
> Yes, it's been reported over a year ago. A solution doesn't look like it's coming any time soon, lol.

Yeah, I just noticed that, unfortunately :(

---

### Post by bufsabre666 on 2008-06-22
> **hotweiss said:**
> Wow, swiftweasel really helped out with the page I originally had trouble with, but it still had trouble with this page:

[http://lubosz.de/Firefox3PerformanceBug/](http://lubosz.de/Firefox3PerformanceBug/)

It seems that the CPU tweaks help out the renderer, but they can only do so much. None the less, Swiftweasel is my new browser, lol.

swiftweasel has been my browser of choice for 6 months now, the cpu optimization is nothing to squak at, it works very nice. and version 3 was released about 12 hours ago, its very nice, enjoy the browser

---

### Post by quanumphaze on 2008-06-22
> **reyfer said:**
> There must be something wrong with my Firefox, every page and site mentioned here loads and scrolls fast, fast, fast on my machine.....what's wrong with my Firefox?

Do you have NoScript? I find that on sites with some JavaScript special content scroll faster without the JavaScript part. eg: Slashdot comments use js and scroll faster without it. 
Not sure if most other js heavy sites will even function without js though. You have to test it yourself.


Anyway I also find that blocking the background image in those listed blogs did speed it up significantly.
The [http://lubosz.de/Firefox3PerformanceBug/](http://lubosz.de/Firefox3PerformanceBug/) site did slow me down and the CPU load applet even froze while scrolling it, and I'm using Swiftweasel 3 RC1

---

### Post by hanzomon4 on 2008-06-22
AHhhhhhh!!! 

Why can't this just be fixed? I've had to use so many "workarounds" I can barley stand it. Do they at least know what's wrong? I thought it might be cairo but then wouldn't it affect every site? It works fine in OS X and Vista. Shouldn't it be perfect on the open source OS? Is this bug in any of the other alt OSes like Freebsd based systems?

---

### Post by Moustacha on 2008-06-22
I get this horrible lag too, nvidia card (9600GT), FF3. It doesn't lag *as much* in opera, but firefox is near unusable when it's suffering this s***

---

### Post by Hells_Dark on 2008-06-22
o/
Me too
:(

(quad core, 8800GT, 2go ram..)

---

### Post by bonzodog on 2008-06-22
The first few sites you sent me to were fine on FF3 in Arch Linux, but the performance bug one was very slow.

It seems Ubuntu is affected by this more than other distros.

---

### Post by xlinuks on 2008-06-22
For those who experience "slow scrolling" go to
Edit->Preferences->Advanced->General.
Uncheck "Use autoscrolling" and "Use smooth scrolling".
I did so and now Firefox seems to scroll a lot faster.
I don't know if this works for you as well.

---

### Post by mrgnash on 2008-06-22
> **xlinuks said:**
> For those who experience "slow scrolling" go to
Edit->Preferences->Advanced->General.
Uncheck "Use autoscrolling" and "Use smooth scrolling".
I did so and now Firefox seems to scroll a lot faster.
I don't know if this works for you as well.

Problem is, I love autoscrolling :P

---

### Post by xlinuks on 2008-06-22
Then I would suggest unchecking only the "Use smooth scrolling" option. Should help as well.

---

### Post by quanumphaze on 2008-06-22
Well I just upgraded to Swiftweasel 3.0 (pentium3m I have a Celeron M) and the scrolling is still poor, but usable.

Hopefully this bug will eventually be fixed, however I doubt it will be soon.

Smooth scrolling is disabled on my one, yet Konqueror uses smooth scrolling and has no problems.

---

### Post by hotweiss on 2008-06-23
Actually Opera 9.5 is just as fast as Firefox and it does not exhibit this laggy behavior. I've switched over to it and so far, so good.

---

### Post by swoll1980 on 2008-06-23
Your computer, or internet conection perhaps? I clicked the link, and loaded the entire page in about 2 1/2 seconds. After the entire page loaded I scrolled through it with no problem.

---

### Post by hotweiss on 2008-06-23
Back to Firefox as Opera is a bit too buggy, I almost lost an hours work because it reset everything that I have written in a text box. Thank god for auto-save.

---

