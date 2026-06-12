---
title: "Autumn Compiz Plugin"
date: 2007-11-17
forum: The Cafe
---

### Post by PatrickFisher on 2007-11-17
I've recently been busy adapting the "Snow" plugin for Compiz so it works well with leaves. I've uploaded a preliminary video [ _**here**_ (youtube) ]("http://www.youtube.com/watch?v=cHLDtJXc8fg")

Before you guys say "Oh, you just changed the pictures", that's not true (it looks really awful if you do). I've adapted the plugin so that the leaves rotate semi-randomly and drift more. I would like to develop this plugin further, but there is almost no point if there is no support from you guys.

So, what do you think? Would you install it?

*****************
Future development:
-Completely randomize rotation
-Better imitate left-right movement of real leaves
-Get permission from Snow script writers to distribute (big step)
-Better integrate with Compiz Settings manager.
-Gather ideas from community
*****************

---

### Post by -grubby on 2007-11-17
I didn't even notice that as a desktop until I looked on the left and saw your desktop bar

---

### Post by FuturePilot on 2007-11-17
Wow! With that wallpaper it looks like it's real! The movement looks so real!

---

### Post by Jose Catre-Vandis on 2007-11-17
It's great, where can i get it, and the wallpaper :)

---

### Post by PatrickFisher on 2007-11-17
Thanks for the support guys! So far, it looks like I'll be continuing my development. 

Unfortunately, I cannot release the plugin now. It uses large chunks of code from the Snow plugin, and I really do want permission from them before I release this to everyone. Plus, it's simply not ready (it doesn't even show up properly in Effects Manager)

but hey, in the mean time, here's the **_[background]("http://www.sverus.com/widescreen/Autumn_Park_Wall_Mural_WG271XL.jpg")_**. I will attach a couple of the leaf textures too. If you use them with the Snow plugin, you should get a reasonable effect. 

I wouldn't mind a bit of help from someone who would know how to integrate the plugin into the Manager. Please message me if you think you can help.

Thanks again guys!

---

### Post by jespdj on 2007-11-17
It looks really nice! :) When it's ready, please tell us where we can get it! :KS

---

### Post by Golyadkin on 2007-11-17
Cool, this reminds me of the ancient program by Rick Jansen ( [http://www.euronet.nl/~rja/](http://www.euronet.nl/~rja/) ) who made xsnow for windows, and later Autumn Leaves, with mushrooms, variable winds, playing squirrels, heapes of leaves, etc. Very cool that you do this.

---

### Post by PatrickFisher on 2007-11-18
Well, I did a bunch of work on it today and since it seemed pretty popular, I decided to release it.

I made a how-to here:

[http://ubuntuforums.org/showthread.php?p=3792520#post3792520]("http://ubuntuforums.org/showthread.php?p=3792520#post3792520")

---

### Post by cabaro on 2007-11-18
I just installed this and it works great. Looks very nice.

Good work!

---

### Post by nikoPSK on 2007-11-24
I like how the leaves sway, tell me how hard is it to make plugins?

---

### Post by PatrickFisher on 2007-11-24
> **nikoPSK said:**
> I like how the leaves sway, tell me how hard is it to make plugins?

It's not too hard.  You'll need to know some C/C++ before you even try though. The rest I got from trial and error.

I know that there are tutorials out there (check the Compiz community forums), but I hate tutorials, so I just kept trying different things.

Oh yeah, one piece of wisdom to pass on:

It's not a good idea to make a plugin start on boot while you're editing it. :)

---

### Post by ticopelp on 2007-11-24
Incredible. Well done.

---

### Post by nikoPSK on 2007-11-24
> **PatrickFisher said:**
> It's not too hard.  You'll need to know some C/C++ before you even try though. The rest I got from trial and error.

I know that there are tutorials out there (check the Compiz community forums), but I hate tutorials, so I just kept trying different things.

Oh yeah, one piece of wisdom to pass on:

It's not a good idea to make a plugin start on boot while you're editing it. :)

I know some c/c++, but only a bit. I'm only in grd 8, I could get a book from the library.

---

### Post by stunner on 2007-11-24
Very, very lovely.

---

### Post by Linuxratty on 2007-11-24
> **PatrickFisher said:**
> I've recently been busy adapting . I would like to develop this plugin further, but there is almost no point if there is no support from you guys.

So, what do you think? Would you install it?

*****************

Would I install it!?
Do ducks swim? 
Do birds fly?
Do rats dig?
Do squirrels climb?
 if there was an easy way to install it,I'd do so in a heartbeat.
 Ive also sent a link over to Klikit Linux and this also needs to go on Digg.
 I'd like to see a springtime one with a budding and blooming cherry tree.

---

### Post by DoctorMO on 2007-11-26
OK I got it installed and it's pretty good; I have found a bug though.

Larger leaves are naturally closer to the viewers point of view, yet they are not on top with tiny leaves crossing their paths it ruins the effect somewhat.

Make sure that the bigger the leaf is, the higher z-index it has.

---

### Post by PatrickFisher on 2007-11-26
> **DoctorMO said:**
> OK I got it installed and it's pretty good; I have found a bug though.

Larger leaves are naturally closer to the viewers point of view, yet they are not on top with tiny leaves crossing their paths it ruins the effect somewhat.

Make sure that the bigger the leaf is, the higher z-index it has.

Huh. Earlier today I couldn't reproduce this, but now I can. It's interesting because size is determined by z-index. Well, I'll definitely work on it and include the update in the combined plugin.

---

### Post by Exonimus on 2007-11-29
nice! you should make this an all-seasons kind of thing! :D

anyway, I created a little variation for myself because I wanted to have something for next spring(actually, I did it just for the heck of it, I like messing around), with some falling flowers =) Only thing I did was change the pictures. I think it looks kind of colorful :P it's just for personal use.

[http://www.youtube.com/watch?v=kOuLa34Qp-Q](http://www.youtube.com/watch?v=kOuLa34Qp-Q)

---

### Post by PatrickFisher on 2007-11-29
> **Exonimus said:**
> nice! you should make this an all-seasons kind of thing! :D

anyway, I created a little variation for myself because I wanted to have something for next spring(actually, I did it just for the heck of it, I like messing around), with some falling flowers =) Only thing I did was change the pictures. I think it looks kind of colorful :P it's just for personal use.

[http://www.youtube.com/watch?v=kOuLa34Qp-Q](http://www.youtube.com/watch?v=kOuLa34Qp-Q)

If you send me the images you used, I'll include them in Elements.

---

### Post by n3tfury on 2007-11-29
That's great! keep up the good work and i'll be looking forward to the plugin too :)

---

### Post by Tristam Green on 2007-11-29
Simply incredible.  I love it :D

---

### Post by Exonimus on 2007-11-29
sure, I'll send them to you.

edit: I hate to say this, but I have no clue whatsoever how to include attachments in my forum posts =/

---

### Post by DoctorMO on 2007-11-29
> Huh. Earlier today I couldn't reproduce this, but now I can. It's interesting because size is determined by z-index. Well, I'll definitely work on it and include the update in the combined plugin.

Curious, well good look with your quest.

With the spring one, we need to have Japanese cherry blossoms falling down.

---

### Post by RAV TUX on 2007-11-29
> **PatrickFisher said:**
> I've recently been busy adapting the "Snow" plugin for Compiz so it works well with leaves. I've uploaded a preliminary video [ _**here**_ (youtube) ]("http://www.youtube.com/watch?v=cHLDtJXc8fg")

Before you guys say "Oh, you just changed the pictures", that's not true (it looks really awful if you do). I've adapted the plugin so that the leaves rotate semi-randomly and drift more. I would like to develop this plugin further, but there is almost no point if there is no support from you guys.

So, what do you think? Would you install it?

*****************
Future development:
-Completely randomize rotation
-Better imitate left-right movement of real leaves
-Get permission from Snow script writers to distribute (big step)
-Better integrate with Compiz Settings manager.
-Gather ideas from community
*****************Very nice.

Isn't snow under GPL?  I would love to try this one day, perhaps you could make a realease for e17? perhaps as an animated background?

also it would be cool if a leaf stuck to the screen and then blew off. ;)

> **Exonimus said:**
> nice! you should make this an all-seasons kind of thing! :D

anyway, I created a little variation for myself because I wanted to have something for next spring(actually, I did it just for the heck of it, I like messing around), with some falling flowers =) Only thing I did was change the pictures. I think it looks kind of colorful :P it's just for personal use.

[http://www.youtube.com/watch?v=kOuLa34Qp-Q](http://www.youtube.com/watch?v=kOuLa34Qp-Q)

> **DoctorMO said:**
> Curious, well good look with your quest.

With the spring one, we need to have Japanese cherry blossoms falling down.

My thoughts exactely about the Japanese Cherry Blossoms. ;)

---

### Post by prodigalson666 on 2007-11-29
Looks great would definently use it!!

---

### Post by nikoPSK on 2007-11-29
I like ravs suggestions. Also the water plugin should have some other features I was ranting about to my buddy, but now forgot...

---

### Post by RAV TUX on 2007-11-29
> **nikoPSK said:**
> I like ravs suggestions. Also the water plugin should have some other features I was ranting about to my buddy, but now forgot...
The leaves could fall on a reflecting pool of water, something like MC Eschers "Three Worlds", with Japanese Koi below the water leaves on top and trees reflecting from above?

reference:

MC Escher "Three Worlds"
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=51823&d=1196387741[/IMG]

Inspired image:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=51824&d=1196387741[/IMG]

When the Leaves or even Cherry Blossoms hit the water the water effect would kick in.

---

### Post by nikoPSK on 2007-11-29
awesome idea! I love Escher btw.;)

---

### Post by chewearn on 2007-11-29
This plug-in is awesome!
:popcorn:


[SIZE=1]but... if you are taking feedback:[/SIZE]

I got screen artifacts after enabling this plug-in.  In my set-up, I turned on Desktop Cube, and enable cube opacity = 0.  Then I also have dock opacity=70 (in General Options)

First, this plug-in invalid the dock opacity.  Second, while the plug-in is on (leaves are falling), the side cubes (left and right) will flash every time a new window is created.

Just a feedback, it is still a very awesome plug-in, and I will continue to use it despite the minor hick-up.

---

### Post by RAV TUX on 2007-11-30
> **RAV TUX said:**
> The leaves could fall on a reflecting pool of water, something like MC Eschers "Three Worlds", with Japanese Koi below the water leaves on top and trees reflecting from above?

reference:

MC Escher "Three Worlds"
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=51823&d=1196387741[/IMG]

Inspired image:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=51824&d=1196387741[/IMG]

When the Leaves or even Cherry Blossoms hit the water the water effect would kick in.

> **nikoPSK said:**
> awesome idea! I love Escher btw.;)I would have the leaves fall at a slower rate also.

---

### Post by -grubby on 2007-11-30
> **RAV TUX said:**
> I would have the leaves fall at a slower rate also.

About those Ideas, I think that would be great....having leaves floating in the water

---

### Post by nikoPSK on 2007-11-30
I still don't remember my water rants...:(

---

### Post by Exonimus on 2007-11-30
There you go, there's a pm with the images in your inbox! =) I might see if I can get a good japanese cherry blossom image :)

---

### Post by maniacmusician on 2007-12-08
Have you considered just joining the Compiz Fusion team? It's quite possible, and I'm sure they would welcome your help with other stuff as well.

---

### Post by PatrickFisher on 2007-12-08
> **maniacmusician said:**
> Have you considered just joining the Compiz Fusion team? It's quite possible, and I'm sure they would welcome your help with other stuff as well.

As much as I'd love to, I don't really have the time or ability. Typically I do coding when I'm procrastinating from studying, and since I'm going out on an internship right away, I won't have my usual procrastination time. :P

---

### Post by maniacmusician on 2007-12-09
> **PatrickFisher said:**
> As much as I'd love to, I don't really have the time or ability. Typically I do coding when I'm procrastinating from studying, and since I'm going out on an internship right away, I won't have my usual procrastination time. :P
If you joined the community, it would at least be easier to submit your plugin directly into their git repos to make it part of compiz-fusion. I'm sure people would love the plugin.

---

### Post by PatrickFisher on 2007-12-09
> **maniacmusician said:**
> If you joined the community, it would at least be easier to submit your plugin directly into their git repos to make it part of compiz-fusion. I'm sure people would love the plugin.

Well then, maybe I will. We'll see how long it takes me to get Elements together first, because I'd much rather have that in git than Autumn.

---

### Post by spiralx on 2009-05-04
Ok, I'm officially lost now.  Patrick, I am writing here because although there is another "Elements" thread, Search can't find it.  I've downloaded and (I think, there was an abort message at the end) your newer "Elements" thing, but don't know how to locate it as a plugin.  Ubuntu's "Help" is no help at all.   I'm running 9.04, by the way.

---

