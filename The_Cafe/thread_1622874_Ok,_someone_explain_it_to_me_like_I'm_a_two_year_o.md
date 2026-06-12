---
title: "Ok, someone explain it to me like I'm a two year old..."
date: 2010-11-16
forum: The Cafe
---

### Post by TNT1 on 2010-11-16
What the heck is this wayland thing?

---

### Post by KiwiNZ on 2010-11-16
Its a new display server for Linux

[http://en.wikipedia.org/wiki/Wayland_(display_server)](http://en.wikipedia.org/wiki/Wayland_(display_server))

---

### Post by TNT1 on 2010-11-16
"On November 4, 2010, [Mark Shuttleworth]("http://en.wikipedia.org/wiki/Mark_Shuttleworth") announced that unspecified future versions of [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29") (not 11.04) will use Wayland as the display server for the [Unity]("http://en.wikipedia.org/wiki/Unity_%28desktop_environment%29") interface"

But not for any other interface? Or is unity going to be all there is across UNR and desktop? And what if I want to bin unity and stick KDE or Gnome on? Will they be fine with wayland?

Oh, and does wayland bring us closer to direct 3d rendering like directx?

Oh, and can I put wayland on my existing install and remove x?

---

### Post by smellyman on 2010-11-16
I would be patient with this one.  nobody will be moving to wayland anytime soon.  This could be over 2 years away, possibly 4.  Fedora is also looking to move to it as well or at least have it as an option.

---

### Post by Rasa1111 on 2010-11-16
yeah this wont be for awhile.. 
and already there are people completely "ready to leave ubuntu' over it. lol :/

---

### Post by Sslaxx on 2010-11-16
I doubt it'll happen within 4 years, if ever, simply because of the inertia of companies such as Nvidia and AMD. People forget it was a struggle to get them to support X at all in the first place.

---

### Post by zer010 on 2010-11-16
> **Sslaxx said:**
> I doubt it'll happen within 4 years, if ever, simply because of the inertia of companies such as Nvidia and AMD. People forget it was a struggle to get them to support X at all in the first place.

Hopefully, it won't be so much of a struggle this time around. With the two most popular[Citation Needed] distros looking towards Wayland, maybe NVIDIA and AMD will realize that the market is bigger than just Win*.

---

### Post by smellyman on 2010-11-16
> **zer010 said:**
> Hopefully, it won't be so much of a struggle this time around. With the two most popular[Citation Needed] distros looking towards Wayland, maybe NVIDIA and AMD will realize that the market is bigger than just Win*.

[Fedora]("http://www.osnews.com/story/24029/Fedora_To_Eventually_Move_to_Wayland_Too")

Also, I don't know anything about writing drivers or how they interact with X or wayland, but doesn't the possibility exist that since Wayland is more streamlined and uses openGL, it will be easier for AMD and Nvidia to write drivers?

---

### Post by forrestcupp on 2010-11-16
> **TNT1 said:**
> What the heck is this wayland thing?Wayland makes da priddy pictures. :)

> **TNT1 said:**
> 
Oh, and does wayland bring us closer to direct 3d rendering like directx?

No.  It's opengl.  Much different.  They're not doing this for gaming compatibility.  It's more for streamlining desktop graphics and cutting out the middle man, like aiglx and compiz.

---

### Post by TNT1 on 2010-11-16
> **forrestcupp said:**
> Wayland makes da priddy pictures. :)



No.  It's opengl.  Much different.  They're not doing this for gaming compatibility.  It's more for streamlining desktop graphics and cutting out the middle man, like aiglx and compiz.

Ah, great, I don't use a pc for gaming, God invented the PS for that.

So wayland will make for a faster, more stable desktop environment?

---

### Post by Gremlinzzz on 2010-11-16
Ok, someone explain it to me like I'm a two year old 
Like a smart two year old OK never mind here it goes
Wayland first appeared in Timothy Zahn's Heir to the Empire novel. The planet was home to the Emperor's Mount Tantiss storehouse, which contained a cloaking device and cloning chambers that Grand Admiral Thrawn used in his war against the New Republic. Wayland was also home to the insane clone of the Jedi Master Joruus C'Baoth. The Mount Tantiss storehouse was eventually destroyed and C'Baoth killed.
and that's the Wayland thing.

---

### Post by TNT1 on 2010-11-16
> **Gremlinzzz said:**
>  Timothy Zahn.

Is he related to Steve Zahn? I like his movies, they're funny.

---

### Post by samalex on 2010-11-16
I think it's just the natural evolution of things.  When I first got into Linux full time over a decade ago almost everything was based on XFree86, then that was dropped about 5 years ago for X.org, and now it appears Wayland is the next up on the 'X' evolutionary tract.

What sucks is this will probably mean some incompatibilities with some graphic card drivers because when X.org was adopted and XFree86 was dropped I lost support for a few of my graphics cards which only had vendor supplied drivers for XFree86.

But I'm anxious to see where Wayland goes. 

Sam

---

### Post by MasterNetra on 2010-11-16
> **zer010 said:**
> Hopefully, it won't be so much of a struggle this time around. With the two most popular[Citation Needed] distros looking towards Wayland, maybe NVIDIA and AMD will realize that the market is bigger than just Win*.

Even if so, Canonical plans to have a X compatibility with it so its not going to be wayland or the highway.

I'm for one curious about their direct and am waiting and watching. I'm not one of those who are going to leave Ubuntu because of its changes. I prefer to let it come then decide if I want to continue using it. Even if not, there is still Xubuntu, Kubuntu (which hopefully will be gnome stable by then, not holding my breath though) and a tons of other alternative, so not that big of a deal to me.

---

### Post by forrestcupp on 2010-11-16
> **TNT1 said:**
> 
So wayland will make for a faster, more stable desktop environment?
That remains to be seen. ;)

---

### Post by TNT1 on 2010-11-16
> **forrestcupp said:**
> That remains to be seen. ;)

Yeah, yeah, but that's the idea, right?

So back to my other question, could you, if wayland is a bust, swap it for something else? As in could you swap X for something else right now?

---

### Post by TNT1 on 2010-11-16
> **MasterNetra said:**
> Even if so, Canonical plans to have a X compatibility with it so its not going to be wayland or the highway.
.

> **TNT1 said:**
> 
So back to my other question, could you, if wayland is a bust, swap it for something else? As in could you swap X for something else right now?

Ok, really? And now, what could you swap X for?

---

### Post by earthpigg on 2010-11-16
> **TNT1 said:**
> Ok, really? And now, what could you swap X for?

[this thread]("http://ubuntuforums.org/showthread.php?t=1459910") comes to mind, but the replacement discussed there is proprietary. 

YeOK's prediction four months ago sums it up well:

> Being closed source means distro's like Fedora and Debain wouldn't touch this at all, so I can't see it finding a huge following.

I pretty sure, if mainstream Linux really wanted to migrate away from X, something like wayland would be the preferred choice. 

---

### Post by whiskeylover on 2010-11-16
Its a small town about 30 minutes east of Boston.

---

