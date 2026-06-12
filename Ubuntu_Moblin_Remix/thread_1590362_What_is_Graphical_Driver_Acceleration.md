---
title: "What is Graphical Driver Acceleration?"
date: 2010-10-07
forum: Ubuntu Moblin Remix
---

### Post by gccradioscience on 2010-10-07
I was reading this before installing the new version.  What the heck does this mean?   

UNE needs graphical driver acceleration to be able to run. Otherwise, you should be warned about missing them and will be logout and proposed to run standard ubuntu desktop session.

Adam E. 

Linux user since 2009

---

### Post by BigRedButton on 2010-10-11
basically, its the ability of the graphics card to preload images, textures, models, etc into its own memory for processing separately from the CPU.  Think of it as having a dual core processor, and one of them is used only for graphics related tasks (im smelling an onboard graphics hack, hehe).

If you have a graphics card, this shouldn't be a problem for you, just log in under a normal desktop session, go to the restricted hardware drivers, and install the appropriate one for your card.  If you don't, then you're probably SOL and should get one, but generally even a really cheap one will work.

---

### Post by b.schelberg on 2010-10-14
Excuse me? Do you know what UNE stands for? Ubuntu *Netbook* Edition. No, I don't have a graphics card in my netbook, and no, buying one, even a really cheap one, isn't an option.

---

### Post by jefearruda on 2010-10-19
testing

---

### Post by BigRedButton on 2011-10-19
Depends entirely on the netbook.  Most netbooks have some kind of cheap onboard graphics hardware that can be used, even if it is really slow.

---

### Post by Aditya Telang on 2011-11-17
Can anyone tell me drivers for my Compaq Presario CQ61 420TU Intel Graphics Media Accelerator.

---

### Post by Stealthp90 on 2012-04-20
Graphic driver acceleration is when your system uses your GPU to accelerate the rendering or drawing prosece of the drawing of each new frame that you see. If that is disabled your CPU will be doing all the rendering and that is a very inefficient way of doing things. Your CPU is made and designed to prosece code one string at a time which means it will do one pixel at a time. While on the other hand you GPU is built to utilize parallel proseceing which mean instead of doing one line of code at a time it can be doing hundreds if not thousands, depending of course what GPU you have. Your CPU might be able to complete anything from 1 million lines to 18 million lines of code per second, while a mid range graphic card, now a days can do 500 billion lines, and well the highest end cards can do even 1 trillion lines per second. Hope that helps :p

---

