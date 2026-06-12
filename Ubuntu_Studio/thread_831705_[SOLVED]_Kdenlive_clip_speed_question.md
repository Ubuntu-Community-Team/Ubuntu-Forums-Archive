---
title: "[SOLVED] Kdenlive clip speed question"
date: 2008-06-17
forum: Ubuntu Studio
---

### Post by Ralphie on 2008-06-17
Is it possible to change the speed (slow down, or speed up) a clip in Kdenlive? I can't seem to find such an effect anywhere. 

I am using "kdenlive 0.5.svn20071228-0" from synaptic, on Ubuntu 8.04 (gnome)

Thanks!

---

### Post by eye208 on 2008-06-17
Blender's video editor has a speed control effect.

---

### Post by Ralphie on 2008-06-17
Hi thanks for the reply, I've installed blender before, but could not figure out where the video editing takes place, all I get is a 3d modeling area. 

How would I go about editing a normal video in blender?

---

### Post by Creative2 on 2008-06-17
see here there is some screen shoot
[http://fuocotools.byethost13.com/index.php?topic=82.0](http://fuocotools.byethost13.com/index.php?topic=82.0)
and here 
[http://fuocotools.byethost13.com/index.php?topic=133.0](http://fuocotools.byethost13.com/index.php?topic=133.0)

---

### Post by cotcot on 2008-06-17
And here is another useful [[COLOR="Red"]link[/COLOR]]("http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing").

---

### Post by Ralphie on 2008-06-17
Thanks guys, I'll give it another go when I get home from work! 
I might have also found a fix for Kdenlive, if it works I will be sure to post it for anyone who might have the same issue.

---

### Post by Ralphie on 2008-06-18
Sorry Guys, I really cant use blender, it is not very user friendly for video editing.

So, back to the topic of kdenlive, 
I managed to get the speed effect working, by editing:
/usr/share/apps/kdenlive/effects/speed.xml

```
<!DOCTYPE kpartgui>
<effect tag="framebuffer">
...
```
to
```
<!DOCTYPE kpartgui>
<effect tag="motion_est">
...
```

The video will export with the speed effect and it plays just fine. 
But while editing, when I go to watch the clip on kdenlive's monitor, it moves for a few frames and stops.

Does anyone know why this would be happening?

---

### Post by eye208 on 2008-06-18
> **Ralphie said:**
> Sorry Guys, I really cant use blender, it is not very user friendly for video editing.

So, back to the topic of kdenlive, 
I managed to get the speed effect working, by editing:
/usr/share/apps/kdenlive/effects/speed.xml
Is that your definition of user-friendliness? Editing XML files? ;)

---

### Post by Ralphie on 2008-06-18
> **eye208 said:**
> Is that your definition of user-friendliness? Editing XML files? ;)

hahaha, not really, but the gui is set up in a very clean way comparable to professional applications, so once I can get this effect to work smoothly, it will be great! ;)

I found a piece of information that I need someone to decipher for me,
> **Speed**
Allows you to slow down, speed up, reverse play and make stroboscope effect. This effect is available only if Kdenlive was compiled with the latest development version of MLT, taken from its cvs. ( [http://en.wikibooks.org/wiki/Kdenlive/Video_effects](http://en.wikibooks.org/wiki/Kdenlive/Video_effects) )

What exactly is the latest development version of MLT and how do I take it from its cvs?

Maybe the version in synaptic is not this particular version.

---

### Post by imon9 on 2008-06-18
hi raphie, just so u know, the "speed" effect is available in kdenlive of older version but not the latest version in ubuntu. I think the ubuntu dev did not provide the correct version...

so i supposed downgrading will help...

---

### Post by Ralphie on 2008-06-18
> **imon9 said:**
> hi raphie, just so u know, the "speed" effect is available in kdenlive of older version but not the latest version in ubuntu. I think the ubuntu dev did not provide the correct version...

so i supposed downgrading will help...

Thank you, I will try this when I get home!

---

### Post by Ralphie on 2008-06-20
Well I found out that the speed effect actually does work, just not with the .mov files that I am editing.
So in convering my files over to .mpg, I am able to use the speed effect without an  issue.

Thanks again to everyone, and for those of you with the same issue, look on [the first page, post #7]("http://ubuntuforums.org/showpost.php?p=5209509&postcount=7") for a tutorial on how to get the speed effect to work.

---

