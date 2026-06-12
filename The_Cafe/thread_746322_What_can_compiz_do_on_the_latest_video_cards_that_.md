---
title: "What can compiz do on the latest video cards that it can't do on my old card?"
date: 2008-04-05
forum: The Cafe
---

### Post by diablo75 on 2008-04-05
I haven't fiddled around with the advanced compiz config panel for a while, but I remember sometimes enabling a special effect that would seemingly do nothing (motion blur comes to mind), and it was probably because of my old GeForce 5600.

Does anybody know which effects require your video card to be 'turned up to 11"?  If I were to purchase a video card that was just good enough to support all the special effects Compiz Fusion currently offers, but not so expensive that I have to take out a loan, what would I want to get?

---

### Post by 23meg on 2008-04-05
Murrine (revision 32) from SVN + GTK apps with RGBA support + Blur plugin set to Gaussian blur

[http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine/](http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine/)

---

### Post by danny joe ritchie on 2008-04-05
I would think that your old card is good enough for compiz, here a link that details setting things up

:[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
 
I have an NVidia GeForce 8600 and It seems to do a good job for me.

---

### Post by mcduck on 2008-04-05
For some efects, like Gaussian Blur, Motion Blur and the Water plugin you need to have at least Shader Model 2.0-compatible pixel shaders in your graphics card. There may be other features that also require these, but those are the ones I can remember without checking from anywhere ;)

Apart from those features, everything else should work pretty well with almost any graphics card, including quite old ones like Geforce 2.

The amount of available graphics memory also defines the maximum size for textures, which means that the more your card has memory, the higher resolution images you can use for skydome, cube caps and reflection texture.

Just for reference, my old Radeon 9600 is able to handle every Compiz feature with no problems. If you used windows, any card compatible with DirectX 9 or later has at least model 2.0 pixel shaders. Your Geforce5-series card has model 2.0a pixel shaders so yes, it should be able to deal with every single feature in Compiz.

---

### Post by xpod on 2008-04-05
I just use the onboard Nvidia 7 series on this machine and it`s capable of all the default effects as well as the extras mentioned in this thread.
[http://ubuntuforums.org/showthread.php?t=659282&highlight=compiz+plugins](http://ubuntuforums.org/showthread.php?t=659282&highlight=compiz+plugins)

I also have an older Geforcefx5500 which is also more than capable too.
Hell,even the still older 64MbMX4000 managed all bar the water effects,which as mentioned you need the pixel shading abilities for.

It`s actually quite surprising how little compiz can run on:)

---

### Post by mcduck on 2008-04-05
> **xpod said:**
> 
It`s actually quite surprising how little compiz can run on:)
It really puts Aero to shame. :D

---

### Post by xpod on 2008-04-05
> It really puts Aero to shame. 

I tried Vista once,when it first came out,but it was a less than worthy machine at the time so the Aero effects were a big no no.In fact Vista all but laughed at me with my 512Mb of ram & 64MB gfx card of the time:)
Strange that i was able to download 3rd party apps that did basically the same kinda stuff though.

I`m sure my new machine here would run Vista quite well,it said "vista ready" on all the parts anyway... but theres two chances of that happening.......little & none:)

---

### Post by mcduck on 2008-04-06
One funny thing abut Aero was that Microsoft claimed that they need a pixel shader-enabled graphics card and DirectX 10 for the blur effect.

If I remember right it took something like 2 weeks for Beryl/Compiz  developers to find a way to get the blur effect with almost every graphics card :D

---

### Post by swoll1980 on 2008-04-06
How does this guy get glass windows like that [http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine/](http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine/)

---

### Post by 23meg on 2008-04-06
With the software I mentioned in post #2.

---

### Post by klange on 2008-04-06
> **mcduck said:**
> If I remember right it took something like 2 weeks for Beryl/Compiz  developers to find a way to get the blur effect with almost every graphics card :D
Speaking of which, if the Xorg devs get some easy-to-add features into the drivers for intel and radeon, it'll now work on them (recent commit switched the blurring method to something that would be easy to accommodate)

---

### Post by Tundro Walker on 2008-04-06
Once you get DX10 installed, you'll be amazed at how much cooler Compiz is.

:)

---

### Post by diablo75 on 2008-04-06
> **Tundro Walker said:**
> Once you get DX10 installed, you'll be amazed at how much cooler Compiz is.

:)

What are you talking about?

---

### Post by Tundro Walker on 2008-04-06
> **diablo75 said:**
> What are you talking about?


:shock:

... holy crap, I'm speechless.

---

### Post by diablo75 on 2008-04-06
> **Tundro Walker said:**
> :shock:

... holy crap, I'm speechless.

Yeah that's what I thought.

---

### Post by Tundro Walker on 2008-04-06
> **diablo75 said:**
> Yeah that's what I thought.

No, srsly.  U shud try it.  A frend uv mine is 733t haxorz xtrem und Instl'd DX10 in Wyne n did compuz.  It'd blew r mind!  SRSLY!  FURREAL!

(Ok, I'll stop now.  Jokes over.  hehe)

---

