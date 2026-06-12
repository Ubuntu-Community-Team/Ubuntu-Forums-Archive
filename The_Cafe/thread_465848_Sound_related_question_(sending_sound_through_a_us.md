---
title: "Sound related question (sending sound through a usb port to receiver)"
date: 2007-06-06
forum: The Cafe
---

### Post by kadane|R| on 2007-06-06
Hi. I have a question.

Can I connect my computer to a receiver through a usb to optical adapter and basically get a pure sound and Dolby digital? 
I have read in some forums about people doing something similar, I just don't understand how all of this works.
Theoretically the signal that comes from usb is a digital signal witch means that all I have to do is to connect a usb port, through adapter to my hi-fi and that's it. 
Because receivers have a DAC (digital to analog converter) built-in it should work.

The problem is that i don't have a clue how it is done, if at all.
I've red that there is a sound protocol S/PDIF but where exactly it is used?
I have to pipe all of my sound to a usb port instead of /dev/dsp. How do i do that?
Will my receiver be able to understand what is my computer sending?
Maybe I need a special hardware for this, maybe some kind of a... usb to s/pdif??



Thanks...in advance..

---

### Post by kadane|R| on 2007-06-06
No one?
help..please...

---

### Post by bonzodog on 2007-06-06
This may not be the place for it.

In theory, it sounds possible. It's easy to configure Linux to use something other than /dev/dsp for sound output, but I would work on getting the h/w first. I personally have never seen a set-up like you describe, and I would bet almost no-one on here has either. So, get the h/w set-up, make some enquiries with sound h/w buffs - not a local PC shop, but go to a proper high-spec audio outlet, and find the expert.

He will tell you whether the h/w exists, and where you can obtain it. 

*Then* come back here, tell us what you have set-up, and ask us what to do next.

---

### Post by .t. on 2007-06-06
Linux, which has moved on to the "Advanced Linux Sound Architechture", no longer uses /dev/dsp for most applications. I'm unsure of what hardware you are describing, but there are many supported USB audio devices.

---

### Post by kadane|R| on 2007-06-08
Thanks for your replys.

I thought that someone here could give me an advise about a Linux compatible hardware,
but anyway...   this is an interesting idea.

If I'll have any success I'll update this thread...

The hardware should be able to convert whatever comes through usb port to a digital signal that a receiver could understand.

---

### Post by kadane|R| on 2007-06-26
OK..

So this is what I was talking about..

[[COLOR="Blue"]www.turtlebeach.com/products/micro/home.aspx[/COLOR]]("www.turtlebeach.com/products/micro/home.aspx")

I've read that people actually had a success with it but can I pipe through 5.1 DTS? (Dobly Theater System)

any help would be appreciated, meanwhile I'll wait for the shipment and we'll see...

---

