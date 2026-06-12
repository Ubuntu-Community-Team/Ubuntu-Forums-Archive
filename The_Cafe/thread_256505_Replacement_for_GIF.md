---
title: "Replacement for GIF?"
date: 2006-09-13
forum: The Cafe
---

### Post by NiceGuy on 2006-09-13
Hi all - I just thought I'd throw this one out to the ubuntu community.

I have, for a while now, been using .png files as my primary image format for all my websites ([instead of .gif]("http://www.gnu.org/philosophy/gif.html")) dispite IE limitations when it comes to some of the more interesting features of this format eg. transparancy etc. But now I have a problem. I'm wanting to put an animated image on my site and I'd like to use a 'free' format. The only one I've come across is .mng which is a bit like .png but it isn't very well supported (neather IE or Firefox support it!).

So my question is this - what should format should I use? Should I just bite the bullet and use .gif or should I use something else? I've heard that I can make svg animations (although IE doesn't nativley support svg). Or should I try a DHTML solution?

---

### Post by NiceGuy on 2006-09-13
Ok it looks like mng is out for the moment - I just made one in gimp and it seems that although gimp can write them it CAN'T read them!? What is the point of providing write support for a format and not read support?

---

### Post by DoctorMO on 2006-09-13
The format needs to find a use, people were so sick of animated gifs that they signed a blood oath never to invent another technoledgy like it.

besides most people thought flash was the next great thing. as such you might want to try svg animated which isn't fully supported by anything not even adobe or inkscape. :-)

---

### Post by eeGhoong0ais on 2006-09-13
> **NiceGuy said:**
> Hi all - I just thought I'd throw this one out to the ubuntu community.

I have, for a while now, been using .png files as my primary image format for all my websites ([instead of .gif]("http://www.gnu.org/philosophy/gif.html")) dispite IE limitations when it comes to some of the more interesting features of this format eg. transparancy etc. But now I have a problem. I'm wanting to put an animated image on my site and I'd like to use a 'free' format. The only one I've come across is .mng which is a bit like .png but it isn't very well supported (neather IE or Firefox support it!).

So my question is this - what should format should I use? Should I just bite the bullet and use .gif or should I use something else? I've heard that I can make svg animations (although IE doesn't nativley support svg). Or should I try a DHTML solution?

As mentioned in the GNU page to which you link, most of the patents related to GIFs expired years ago, and the last one will expire in eighteen days time. If you really need a simple animation on a website, I would have thought GIFs provide the best combination of Freedom and compatibility.

---

### Post by NiceGuy on 2006-09-13
> **Etiol said:**
> As mentioned in the GNU page to which you link, most of the patents related to GIFs expired years ago, and the last one will expire in eighteen days time. If you really need a simple animation on a website, I would have thought GIFs provide the best combination of Freedom and compatibility.

LOL - I really should read the footnotes of the stuff I link to! You are, of course, correct. However, the fact that its not a 'free' format is, in a lot of ways, a secondary concern (the reason for my link was to illustrate why I don't use gifs for static images – I did mean to link to a page about colour depths etc  as well but I... urm... forgot :oops: ). My other problem is, as with all gifs, lack of colour depth. For the image I'm making at the moment that's not such a problem but it would be nice if there was an alternative I could use (preferably a 'free' one). 

Since my first post I've made some headway with my research and it seems I'll just have to wait till the mozilla team pick a format to support (either mng or apng). Then maybe IE will provide some support for it too (albeit in the half-assed way they tend to) and I can say goodbye to gifs for good.

Unfortunately, that probably a long way off :(

---

### Post by eeGhoong0ais on 2006-09-13
> **NiceGuy said:**
> My other problem is, as with all gifs, lack of colour depth. For the image I'm making at the moment that's not such a problem but it would be nice if there was an alternative I could use (preferably a 'free' one).

Maybe javascript would be your best bet, then - an argument could be made that animation is behaviour, and therefore ought to be handled by client-side scripting anyway.

Probably a pretty thin argument, actually ... but it's nice to be able to justify your decisions ideologically ;-)

---

### Post by NiceGuy on 2006-09-13
I like the sound of that idea! That was what I was getting at with my DHTML option. I've always shunned away from javascript for some reason (I don't really know why - probably a hangup left from when I first learnt html) so maybe now is the time to rectify the matter. Can you suggest any websites to go look for more info?

---

### Post by eeGhoong0ais on 2006-09-13
I don't know of anything specifically about sprite-style animation, no ... I'm a very occasional user of Javascript, but whenever I do want to  play with it, [Quirksmode]("http://www.quirksmode.org/") is usually where I find the most useful help.

I can't imagine a simple looped animation would be difficult to do though - it's just going to be replacing images in turn that are stored in an array, after all.

---

### Post by NiceGuy on 2006-09-13
I'll have a look at that site - thanks!

I don't think its the mechanics of doing it that are going to be difficult, more the 'html integration'. I don't really want to be writing out the same script over and over for each animated image on a page - I hated having to do that with rollovers (before css became mainstream).

What I'd like (in an ideal world) is to be able to upload the different images as, say foo1.png, foo2.png, foo3.png put a standard <img> tag into the html with a css class tag, say class="animate1sec", which would call the script to swap the image foo1 for foo2 etc (ie for all fooX images) every second. Unfortunatly I've got a nasty feeling that isn't possible (mixing javascript with css) and if it is it'll probably take me an age to work out. I'll just have to see what I can come up with.

---

### Post by Brunellus on 2006-09-13
firefox supports .png just fine. IE has notable problems.

---

### Post by eeGhoong0ais on 2006-09-13
> **NiceGuy said:**
> What I'd like (in an ideal world) is to be able to upload the different images as, say foo1.png, foo2.png, foo3.png put a standard <img> tag into the html with a css class tag, say class="animate1sec", which would call the script to swap the image foo1 for foo2 etc (ie for all fooX images) every second.


[This]("http://domscripting.com/blog/display/18") might help, then ...

---

