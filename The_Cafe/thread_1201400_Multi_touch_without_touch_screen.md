---
title: "Multi touch without touch screen?"
date: 2009-07-01
forum: The Cafe
---

### Post by Walther -FI- on 2009-07-01
Multitouch is on the way to homes. The technology is ready, multi-touch screens are being sold, and the prices are going down. (too slowly, but anyway ;) ) Multitouch increases the usability and the easiness of use in many ways; you can do so many things much faster, (f.ex. zooming, rotating) and with multitouch you can do so visual things (that you can amaze your friends with and get some respect :D )

Though, those screens and panels that you can add on your screen are still too expensive to most of us.

What I'm thinking of is: wouldn't it be REALLY cool to have multitouch features with paying only like 10€?

My solution is to add another mouse, and I don't mean those scenarios that already are on Brainstorm threads, where they are talking about two users on a same computer,I'm talking about having all the visual and useful multitouch features, using two mouses.

I have seen videos showing that multitouch tablets do work with linux kernel. So, it doesn't seem to be impossible to do.

It would be so great - like having a multitouch screen, with normal multitouch screen configuration, but only having another mouse. (again, not talking about those two users-scenarios...)


Is this possible yet? Is this in developement in this particular way?

This really should be done.


Walther

---

### Post by Nevon on 2009-07-01
Have you tried using two mice at the same time? I don't know, but it seems to me like trying to write with one pen in each hand.

---

### Post by Walther -FI- on 2009-07-02
Well, this is quite offtopic, that reply didn't actually help me in any ways...

But I have to say - I'm a magician, I play guitar, and I do many other things where I need to use my both hands. And as a magician, I have to be able to do everything precisely without depending on which hand I use.

So, that won't be a problem for me ;)

Back to the topic, please :)

---

### Post by Mr. Picklesworth on 2009-07-02
What you want is called MPX (Multi pointer X), which is coming with Xinput 2, along with lots of other awesome stuff. Xinput 2 is probably going to exist in either Ubuntu Karmic or 10.04. The switch should be mostly seamless for more basic operation, but xinput 2 does have some differences so it could be a little while before everything is perfect and using the features to their potential.

Here's a demo video I quickly found:
[http://www.youtube.com/watch?v=0MUOn_nJmRA](http://www.youtube.com/watch?v=0MUOn_nJmRA)
One that you've probably seen:
[http://www.youtube.com/watch?v=olWjnfBoY8E](http://www.youtube.com/watch?v=olWjnfBoY8E)

And here is the fellow who we can thank for it:
[http://who-t.blogspot.com/](http://who-t.blogspot.com/)

Oh, and an interview:
[http://gizmodo.com/gadgets/touch-me/linux-mpx-multi+touch-table-may-become-alternative-microsoft-surface-278613.php](http://gizmodo.com/gadgets/touch-me/linux-mpx-multi+touch-table-may-become-alternative-microsoft-surface-278613.php)

And Wikipedia, of course:
[http://en.wikipedia.org/wiki/Multi-Pointer_X](http://en.wikipedia.org/wiki/Multi-Pointer_X)

---

### Post by Walther -FI- on 2009-07-02
Thanks for info about those - I knew already something about MPX, but it's always good to learn something new about todays newest inventions.

I really hope that those softwares/plugins/updates to Xserver/whatever are coming for multi-touch enabled touchscreens AND without.

(still waiting for Asus T101H, tablet netbook... :D)

---

### Post by geoken on 2009-07-02
I don't see the use in multitouch when you already have a mouse. I have an iPhone and I'd personally rather have a trackball for zooming than have pinch gestures. To me it feels gimicky.

---

### Post by jonian_g on 2009-07-02
Check this page. How to make a screen multitouch using the wii remote control.

[http://johnnylee.net/projects/wii/](http://johnnylee.net/projects/wii/)

---

### Post by Walther -FI- on 2009-07-03
Wow - many thanks to that Wiimote reply! Those Nintendo Wii controllers aren't so expensive, I might try to get one of those :D

How reliable and accurate is that wiimote interface to use - is it really possible to use a computer with one?

But still I think that using a mouse per hand could be more accurate.

---

### Post by jonian_g on 2009-07-03
I don't know how reliable it is. I haven't used one. You can search youtube for "wii ubuntu" to see it in action. Also there is an app in the repos to configure the controller and use it with ubuntu.

---

### Post by geoken on 2009-07-03
> **Walther -FI- said:**
> Wow - many thanks to that Wiimote reply! Those Nintendo Wii controllers aren't so expensive, I might try to get one of those :D

How reliable and accurate is that wiimote interface to use - is it really possible to use a computer with one?

But still I think that using a mouse per hand could be more accurate.

Can you please tell me one thing that would be better executed using some convoluted 2 mouse setup instead of a single mouse and it's scroll wheel?

---

### Post by Mr. Picklesworth on 2009-07-03
> **geoken said:**
> Can you please tell me one thing that would be better executed using some convoluted 2 mouse setup instead of a single mouse and it's scroll wheel?

There are some neat applications with DJ software - tinkering with more than one channel at once in real time :)

MPX is more than just multiple mice, too. If you plug a drawing tablet in, that could be given its own pointer. This way one can use the mouse to control tools and the tablet to draw without them interfering with each other. Touch screens, naturally, could get the same magic.
For contrast, the competition at the moment has the touch screen controlling a single conventional system-wide pointer, so if you have a mouse plugged in and someone (or some thing!) touching the touch screen, that mouse won't be very useful. In addition, the pointer behaves in a way that really feels like cruft from its mouse functionality, including being visible quite frequently. Perhaps when MPX becomes more established that kind of cruft can be eradicated.

As I understand it, mouse grabs are now per pointer (though I may be wrong), so if one mouse gets grabbed and never released by a broken application, there is hope to recover the GUI way by using a second mouse.

---

### Post by geoken on 2009-07-03
> **Mr. Picklesworth said:**
> There are some neat applications with DJ software - tinkering with more than one channel at once in real time :)



That makes sense and I'm sure there are some other really specific situations where it can be use full.

I was referring more to traditional desktop tasks. For example, the OP noted zooming and rotating both of which are far more cumbersome and convoluted with multi-touch. Holding the right mouse button while hovering over an image and scrolling up and down is faster, easier, more efficient, etc. than some multi-touch pinch gesture. Likewise, holding the right mouse button and moving the mouse up and down to rotate is far superior to multi-touch two finger rotation. Have you ever seen any multi-touch demo where the user didn't inadvertently scale the image when he/she was just trying to rotate it (or rotate the image when they where just trying to scale)?

---

