---
title: "Licensing a Game"
date: 2011-03-09
forum: The Cafe
---

### Post by roadkillguy on 2011-03-09
Hi everybody, I've made a game using SDL, OpenGL, and gtkmm.  I've put hours and hours into it, and it'd definitely be nice to make some money off of it.  It has a website, which I will most definitely put banners of some sort on once it gets enough viewers.  Unfortunately, as some of you might know, ads don't pay very much unless people click on them.  Thus, you need thousands of people to get a measly dollar.

What should I do with copies of the game then?  Should I sell it?  I don't like the idea of releasing the source because the game is now multiplayer, and probably easily hackable.  I realize that the GPL and LGPL will frown on me for this, and probably most of you guys. :P

Anyway, what do you think my course of action should be? [SIZE="1"](As biased as it may be.)[/SIZE]  I'm not trying to be greedy, I just need my work to pay off.

Thanks!

---

### Post by Lucradia on 2011-03-09
Your own custom-written EULA would be good for that.

---

### Post by juancarlospaco on 2011-03-09
A licence that says when you Reach N amount of Money, the game becomes Free Libre GPL, 
and put a *BIG* Progress Bar on the website. Like Indies...  Wikipedia... 

Like:

[COLOR="Red"]Game will Die,No money for Development[/COLOR] &#9608;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617; [COLOR="SeaGreen"]Game becomes GPL,Next version coming[/COLOR]

to

[COLOR="Red"]Game will Die,No money for Development[/COLOR] &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9617; [COLOR="SeaGreen"]Game becomes GPL,Next version coming[/COLOR]

:D

---

### Post by rg4w on 2011-03-09
> **juancarlospaco said:**
> A licence that says when you Reach N amount of Money, the game becomes Free Libre GPL, 
and put a *BIG* Progress Bar on the website. Like Indies...  Wikipedia... 

Like:

[COLOR=Red]Game will Die,No money for Development[/COLOR] &#9608;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617; [COLOR=SeaGreen]Game becomes GPL,Next version coming[/COLOR]

to

[COLOR=Red]Game will Die,No money for Development[/COLOR] &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9617; [COLOR=SeaGreen]Game becomes GPL,Next version coming[/COLOR]

:D
That's a really intriguing idea.  I may adopt that for some goodies I have in the pipeline....

---

### Post by juancarlospaco on 2011-03-09
Also you can include the progress bar on the game itself, like an internet sync.

When the bar is full, REALLY start a new proyect, if you dont, the users will not pay again,
but dont change textures and try to sell the same again and again, make the game better...

:D

---

### Post by realzippy on 2011-03-09
Would like to hear more about the game itself,if you do not mind...

---

### Post by donkyhotay on 2011-03-09
> **juancarlospaco said:**
> A licence that says when you Reach N amount of Money, the game becomes Free Libre GPL, 
and put a *BIG* Progress Bar on the website. Like Indies...  Wikipedia... 

Like:

[COLOR="Red"]Game will Die,No money for Development[/COLOR] &#9608;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617; [COLOR="SeaGreen"]Game becomes GPL,Next version coming[/COLOR]

to

[COLOR="Red"]Game will Die,No money for Development[/COLOR] &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9617; [COLOR="SeaGreen"]Game becomes GPL,Next version coming[/COLOR]

:D

It's a good idea, problem is there is always the fear that people will pay and then not get anything from it. I've seen similar attempts and many of the big ones you hear about (like the humble indie bundle) work but I have encountered some that don't. I know stephen king attempted something like that, he wrote part of a story, put it for free on his website for free and asked for donations. He put that if he got enough donations to cover what he would normally get for the full book he would write and then post the rest of the story. This way people got stories cheaper (avoiding publisher costs) and he didn't waste time writing stories people weren't interested in. He figured that if enough people read the story and didn't donate then obviously they didn't like it and he should work on something else. It failed miserably as many people read it, didn't pay, and those that did got burned because they never got to finish it. I think part of the problem is he looked at it as he was asking for a flat rate from everyone and required something like 70% of pagehits should donate before he would continue. Not certain but that sounds kind of stupid since lots of people will click on a link without actually reading on the page (not to count any/all spiders) which will throw off the stats. Could be wrong about all this, it's something I remember reading about once but can't find anymore.

---

### Post by ssam on 2011-03-09
be sure that you have not included any opensource code that does not allow itself to be include into closed code. i think the libraries you mentioned are ok. (LGPL says you can link to it from any code).

you could talk to canonical about getting it into the software center.

also just because you don't release the source does not mean that no one can crack it. people could capture network packets, and manipulate them to cheat, and make crash it by sending malformed packets.

---

### Post by forrestcupp on 2011-03-09
> **ssam said:**
> be sure that you have not included any opensource code that does not allow itself to be include into closed code. i think the libraries you mentioned are ok. (LGPL says you can link to it from any code).

Good point. Make sure you are linking dynamically and not statically. If you compile it into your code statically, you'll be violating the LGPL.

If you're going to actually sell the game, you'll have to come up with some kind of proprietary license. There are plenty of examples out there that you can tweak for your own needs.

---

### Post by roadkillguy on 2011-03-09
I like the idea of the progress bar, but I can see why people wouldn't happily pay.
 
My game is based around mods, and I may be able to sell the mod-loading version and give out a default-mod demo version for free.
 
My Game?  Well, it's heavily based around the block-based gameplay of infiniminer/minecraft.  You can add custom textures and reactions to the game using mods.  I wanted to emphasize on pvp gameplay (guns, etc), but that's down the road.  I'll point you to a website when I release the new version, because the current one is kind of buggy.  I'll release the new version when I get rid of packet bias between clients on the server, if that's of any consolation.

Oh, and I'm linking dynamically, so that shouldn't be a problem.

---

### Post by roadkillguy on 2011-03-13
If anybody still cares, you can find my game at [xBlocks.net]("www.xblocks.net").

I'd love for people to (Alpha?) test it under Ubuntu.

I'm probably going to go with the indie donate bar at the top because I'm unsure as to how well I can secure the purchasing process :(.

---

