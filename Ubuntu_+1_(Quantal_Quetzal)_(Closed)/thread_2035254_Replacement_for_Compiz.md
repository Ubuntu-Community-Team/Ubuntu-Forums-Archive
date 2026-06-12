---
title: "Replacement for Compiz?"
date: 2012-07-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Farvez Afridi on 2012-07-30
If i'm not wrong, I heard that Ubuntu 12.10 will be dropping Compiz, Is there any replacement for it announced yet?

---

### Post by cecilpierce on 2012-07-30
> **Farvez Afridi said:**
> If i'm not wrong, I heard that Ubuntu 12.10 will be dropping Compiz, Is there any replacement for it announced yet?

Any thing would be better  :P

---

### Post by ronacc on 2012-07-30
there already is something better , gnome classic !

OPPS  my bad , posted to the wrong thread

---

### Post by jbicha on 2012-07-30
Ubuntu 12.10 will not drop Compiz.

---

### Post by EgoGratis on 2012-07-30
Can somebody rationally explain to me why exactly Compiz WAS BEING dropped? If for Unity Ubuntu would not choose to use Compiz it would probably become history soon. 

Why exactly would that be good thing too drop the best compositor for Linux? The only outcome i see is another compositor would be made and in ten years time it would allow user to enable "fire effect".

Why didn't other DE just drop their compositors and just use Compiz instead? That would be a good thing and i can't understand why it didn't happen and almost the opposite thing happened and for what purpose?

---

### Post by ronacc on 2012-07-30
In my not very humble opinion it is criminally stupid for any DE to REQUIRE a compositor , they should be strictly optional  You can play with your eye candy like wobbly windows and fire effect but don't steal my cycles to do it .

---

### Post by mc4man on 2012-07-30
> **EgoGratis said:**
> Can somebody rationally explain to me why exactly Compiz WAS BEING dropped? 
Curious, who said compiz was being dropped?

> **EgoGratis said:**
> Why didn't other DE just drop their compositors and just use Compiz instead?  
Maybe they'd like something reasonable stable & efficient

---

### Post by ojdon on 2012-07-30
Unfortunately, Compiz is required for Unity 3D as it is just a plugin for Compiz. Really can't stand Compiz to be honest, I here it gives lots of users issues but there just isn't a solid alternative at the moment.

---

### Post by EgoGratis on 2012-07-30
> In my not very humble opinion it is criminally stupid for any DE to  REQUIRE a compositor , they should be strictly optional  You can play  with your eye candy like wobbly windows and fire effect but don't steal  my cycles to do it .

The problem is that this kind of arguments reminds me to PulseAudio  vs. Alsa debates and in the end ask yourself do u use PulseAudio and Unity 3D and why if u can use just Alsa without PulseAudio and Unity 2D without Compiz?

It's easy to say i don't like PulseAudio or Compiz but why do majority of users then prefer it over just Alsa and Unity 2D?

> Curious, who said compiz was being dropped?

Who would use Compiz by default if Unity would not choose to use it and would Compiz still be relevant today in Gnome 3 era? I think not.

> Maybe they'd like something reasonable stable & efficient

Exactly! Maybe it's time to create something like that and not to waste resources by doing it in a way  throwing away something like Compiz and start again only to have "fire effect" implemented again in 10 years time.

> Unfortunately,  Compiz is required for Unity 3D as it is just a plugin for Compiz.  Really can't stand Compiz to be honest, I here it gives lots of users  issues but there just isn't a solid alternative at the moment.

Yes there is it's called Unity 2D and if u can't stand Compiz why use Unity 3D?

---

### Post by EgoGratis on 2012-07-30
An the point is we actually like to use and we do need Compiz and why exactly was this great piece of software thrown away by other DE's and why do they prefer to offer alternatives that can't compare to Compiz?

If "Wobbly Windows" is the cause then don't enable it? Compiz has plugins architecture and any decent compositor should have it too?

---

### Post by thatguruguy on 2012-07-30
> **Farvez Afridi said:**
> If i'm not wrong, I heard that Ubuntu 12.10 will be dropping Compiz, Is there any replacement for it announced yet?

You're wrong.

Providing a source would be nice.

---

### Post by Merk42 on 2012-07-30
> **ronacc said:**
> In my not very humble opinion it is criminally stupid for any DE to REQUIRE a compositor , they should be strictly optional  You can play with your eye candy like wobbly windows and fire effect but don't steal my cycles to do it .I thought the point of a compositor was to use the video card to do the rendering to **free up** 'cycles' (ie processor) for other tasks.

---

### Post by EgoGratis on 2012-07-31
I am interested on some facts how Weston/Compiz story will evolve? Is this decided yet? 

Compiz standalone with implemented Wayland protocol or Compiz as plugin for Weston or Weston standalone without Compiz or something completely different...

---

### Post by ojdon on 2012-07-31
> **EgoGratis said:**
> 
Yes there is it's called Unity 2D and if u can't stand Compiz why use Unity 3D?

Seriously? Unity 2D is meant to be a fallback option for if your hardware can't do 3D acceleration, for example if you are having driver issues, it's not meant to be for daily usage. 

If you sit in a non-accelerated environment then you are putting additional pressure on your CPU and your GPU is doing nothing at all.

---

### Post by ronacc on 2012-07-31
> **Merk42 said:**
> I thought the point of a compositor was to use the video card to do the rendering to **free up** 'cycles' (ie processor) for other tasks.

on my sys  

unity 3d   compiz  1% cpu  4.49 % mem   xorg  1% cpu   1.3% mem

gnome shell  1% cpu  (mutter not even shown in sys monitor )  3.4% mem  xorg 1% cpu   3.4% mem

gnome classic (no effects)   xorg  1% cpu  1.7% mem


so it really seems to be a wash , acceleration only uses a little bit more cpu and mem , an insignificant amount but the principle remains .

---

### Post by ojdon on 2012-07-31
Imagine if you were trying to do something really processor intensive such as compiling. I'd rather try and remove any form of unneeded stress away from my CPU if it can be done on the GPU. That's the way I look at it anyway.

---

### Post by EgoGratis on 2012-07-31
> **ojdon said:**
> Seriously? Unity 2D is meant to be a fallback option for if your hardware can't do 3D acceleration, for example if you are having driver issues, it's not meant to be for daily usage. 

If you sit in a non-accelerated environment then you are putting additional pressure on your CPU and your GPU is doing nothing at all.

And basically you just described why we want to use Compiz or am i missing something?

---

### Post by ojdon on 2012-07-31
I never mentioned Compiz. I was talking about any 3D compositor.

---

### Post by EgoGratis on 2012-07-31
> **ojdon said:**
> I never mentioned Compiz. I was talking about any 3D compositor.

Yes we did this part before in this topic too and i suggested that other DE drop their compositor that lacks in many areas and use Compiz instead that has few years more development built in already and work on that instead.

And if it has plugins architecture i think developers should stop wasting effort telling the users they should not enable "Wobbly Windows" effect and not to use dual pane mode in Nautilus and not to use icons all over the desktop. The only outcome is some developers migrate to other project and users frustration. 

The only thing i don't know is what will be the story with Weston because Weston could end up being default standard compositor for Linux desktop but it still lacks in many areas and it will take few years to compare to Compiz and yes users do want optional "Wobbly Windows"effect and probably every single decent compositor that will be built again from scratch will eventually have "Wobbly Windows" support.

---

### Post by EgoGratis on 2012-07-31
Can somebody with enough technical knowledge explain to me the difference between:

**Weston and Clutter/Mutter. **This is display server vs. windows manager debate and nothing more?

**Weston and Compiz.** Compiz is just Window manager or it could replace Weston too with Wayland protocol support or/and could Weston replace Compiz and offer Desktop Cube and Wobbly Windows by itself?

---

### Post by EgoGratis on 2012-07-31
OK so you can rotate Windows with just Weston:

[http://www.youtube.com/watch?v=Oj_kr2KG904](http://www.youtube.com/watch?v=Oj_kr2KG904)

I guess "Wobbly Windows" support is next logical step? Weston could in theory be direct replacement for Compiz and both use GPU acceleration?

---

### Post by mc4man on 2012-07-31
> **ojdon said:**
> Imagine if you were trying to do something really processor intensive such as compiling. I'd rather try and remove any form of unneeded stress away from my CPU if it can be done on the GPU. That's the way I look at it anyway.
If that's the case you'd be better off doing so in unity-2d or classic no effects or just about anything other than unity/compiz
(- time wise in a test doing the same non compiling actions 2d completes a vlc build about 12% faster & remains a bit quicker during the compiling for some of those actions

---

### Post by ventrical on 2012-07-31
Kwin seems to work quite well for  Kubuntu. It is suggested that kwin can run  in standard Ubuntu also.

   I think , as usual, that compiz is getting a bad rap by persons who have slower PCs.  Even if people do not like compiz I think it is a great beta testing tool to push adapter cards to the max on mid-range machines.

---

