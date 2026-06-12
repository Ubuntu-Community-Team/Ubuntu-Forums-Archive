---
title: "Dual core issues with wine, and a possiable fix?"
date: 2009-06-16
forum: Wine
---

### Post by Azuu on 2009-06-16
From what I understand, wine issues relating to dual core processing could be fixed by simply assigning one core specifically to wine. This should solve the problems of the second core 'trying to butt it's way in'. This-I assume- would also fix the issue of sound cutting off on any wine emulated program.

The sad fact is, I have no idea how to tell wine to do this.

---

### Post by nolliecrooked on 2009-06-16
> **Azuu said:**
> From what I understand, wine issues relating to dual core processing could be fixed by simply assigning one core specifically to wine. This should solve the problems of the second core 'trying to butt it's way in'. This-I assume- would also fix the issue of sound cutting off on any wine emulated program.

The sad fact is, I have no idea how to tell wine to do this.

what are you talking about?

---

### Post by Azuu on 2009-06-16
> **nolliecrooked said:**
> what are you talking about?

Well, I have already figured out that wine itself does not allow multi threading. This is due to the differing ways Linux threads as opposed to Windows. Even with this however, a dual core processor will still try to use both cores. It would seem that telling wine to use one core specifically would stop "hiccups" that are a result of the following logic:
1)Wine says core one.
2)Core one does everything but at a point where the resources run thin the second core tries to step in.
3)Wine says again one core, but has to reselect one core causing a 'hiccup'.

To be more specific, I want to know if (like windows), there is a way to select one core permanently for the duration of the wine session.

---

### Post by nolliecrooked on 2009-06-16
> **Azuu said:**
> Well, I have already figured out that wine itself does not allow multi threading. This is due to the differing ways Linux threads as opposed to Windows. Even with this however, a dual core processor will still try to use both cores. It would seem that telling wine to use one core specifically would stop "hiccups" that are a result of the following logic:
1)Wine says core one.
2)Core one does everything but at a point where the resources run thin the second core tries to step in.
3)Wine says again one core, but has to reselect one core causing a 'hiccup'.

To be more specific, I want to know if (like windows), there is a way to select one core permanently for the duration of the wine session.

okkkkkkkkkkkkkkkkkkkk.

 Im pretty sure WINE can muti-thread, but dont quote me on that :P

---

### Post by Azuu on 2009-06-16
> **nolliecrooked said:**
> okkkkkkkkkkkkkkkkkkkk.

 Im pretty sure WINE can muti-thread, but dont quote me on that :P
Well it CAN, but the methods are flawed (they were used in windows XP when it first came out), and cause more problems than it fixes. I would post a link to the docs from wine, but I can't find them. 

something about forcing it to lock one thread at a time. It does work, which is good, but adds a possible issue that can make the program crash.

I also think that the sound issue (sound cuts off in Foobar or any other program), is related to the dual core. I don't know this, but if this works it will tell me.

---

### Post by nolliecrooked on 2009-06-16
> **Azuu said:**
> Well it CAN, but the methods are flawed (they were used in windows XP when it first came out), and cause more problems than it fixes. I would post a link to the docs from wine, but I can't find them. 

something about forcing it to lock one thread at a time. It does work, which is good, but adds a possible issue that can make the program crash.

I also think that the sound issue (sound cuts off in Foobar or any other program), is related to the dual core. I don't know this, but if this works it will tell me.

it could also be how you set up your audio in winecfg. try setting the default audio to OSS.

---

### Post by Azuu on 2009-06-16
> **nolliecrooked said:**
> it could also be how you set up your audio in winecfg. try setting the default audio to OSS.

that makes it cut out faster.

---

### Post by nolliecrooked on 2009-06-16
> **Azuu said:**
> that makes it cut out faster.

lmao xD

---

### Post by NightMKoder on 2009-06-16
What you're referring to is decades old, back wine kernel 2.5 was out. The threading stack was largely improved in 2.6, but it doesn't actually matter since 2.6 has been out for almost 6 years. Wine has the api to support the 2.5 kernels, but its not maintained and thread support has been fixed for a while now.

[http://www.winehq.org/docs/winedev-guide/threading](http://www.winehq.org/docs/winedev-guide/threading)

what you're referring to is just a bug in sound. First, pulseaudio does not work under wine, (so if you're on normal ubuntu, you have to jump hoops), and second, the wine alsa driver is somewhat not-very-good.

---

### Post by Azuu on 2009-06-17
> **NightMKoder said:**
> What you're referring to is decades old, back wine kernel 2.5 was out. The threading stack was largely improved in 2.6, but it doesn't actually matter since 2.6 has been out for almost 6 years. Wine has the api to support the 2.5 kernels, but its not maintained and thread support has been fixed for a while now.

[http://www.winehq.org/docs/winedev-guide/threading](http://www.winehq.org/docs/winedev-guide/threading)

what you're referring to is just a bug in sound. First, pulseaudio does not work under wine, (so if you're on normal ubuntu, you have to jump hoops), and second, the wine alsa driver is somewhat not-very-good.

Then what is the stuttering about? The program I use the most is neverwinter nights, and it stutters as if the processors were jumping over eachother. I only recently switched to Linux and this worked on higher settings than I have it on now (albeit much slower on said higher settings).

---

### Post by NightMKoder on 2009-06-17
The stuttering is a graphics issue. What video card do you have? Not all video cards are created equal under linux - mainly ATI and Intel have drivers that...well...suck. For now anyway.

There are a couple of things you can do to speed it up, like switching the offscreenrenderingmode to backbuffer/pbuffer, as well as supressing output with WINEDEBUG=-all.

And FYI - games are usually not very multithreaded on the rendering side. It's incredibly hard to get multithreaded rendering right and usually noone does it. (The game itself may use multiple threads, but the rendering engine doesn't)

---

