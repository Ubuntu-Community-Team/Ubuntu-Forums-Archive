---
title: "Why Compiz?"
date: 2009-05-01
forum: The Cafe
---

### Post by jfloydb on 2009-05-01
I want to start a friendly thread about a topic that seems to be quite important to Linux users. The subject is Compiz (if my spelling is correct) and Compiz fusion. I have noticed several complaints on this forum that Compiz doesn't work with 9.04. My question is this: what is so important about Compiz? What's the big deal? I suppose that it means some video card or driver is not functioning, which needs to be corrected, but the real question is: why would anybody want to use Compiz anyway?

I didn't know what Compiz was until I looked on YouTube and watched some of the animated desktop videos. I watched a few Compiz vids and thought (in a non-derogatory way), "so what, a dancing desktop". I was concerned when my wifi didn't work (8.04) and when my desktop didn't fit onto my screen (8.10). Now I'm quite happy; everything important works! 

Apparently I'm a stick-in-the-mud. I never use that neon desktop crap on Vista, for example. With Ubuntu, I use the Human desktop with a plain brown background and with the effects turned off. The flashy stuff seem like a waste of time to me, so why is so important to everyone else?

I have probably written too much to be interesting. But clue me in. Let me know why Compiz is important to you, my friend... Thanks...

---

### Post by FuturePilot on 2009-05-01
[LIST=1]
[*]Eye candy
[*]Letting your CPU do drawing operations on your screen is old school. Why not let something that's good at drawing graphical stuff do it, like your graphics card. This is exactly what Compiz does by offloading all the screen drawing to your GPU, thus allowing your CPU do to more other useful things
[/LIST]

---

### Post by RaZe42 on 2009-05-01
Believe it ir not, but Compiz actually enhances my productivity, particularly the Scale(Like Expose on OS X) and Grid(think tiling WM) plugins. 

Wobbly Windows and the like are just nice extras for me, but I still think Wobbly Windows is underrated, it isn't useless as it gives a natural feel when moving windows.

---

### Post by pwnst*r on 2009-05-01
> **RaZe42 said:**
> Believe it ir not, but Compiz actually enhances my productivity, particularly the Scale(Like Expose on OS X) and Grid(think tiling WM) plugins. 



same for me ^

---

### Post by jfloydb on 2009-05-01
> **FuturePilot said:**
> 
Letting your CPU do drawing operations on your screen is old school. Why not let something that's good at drawing graphical stuff do it, like your graphics card. This is exactly what Compiz does by offloading all the screen drawing to your GPU, thus allowing your CPU do to more other useful things


> **RaZe42 said:**
> Believe it ir not, but Compiz actually enhances my productivity, particularly the Scale(Like Expose on OS X) and Grid(think tiling WM) plugins. 

Wobbly Windows and the like are just nice extras for me, but I still think Wobbly Windows is underrated, it isn't useless as it gives a natural feel when moving windows.


That doe's make sense...

On the other hand...

> **Npl said:**
> There are two 2 steps involved.
1) Drawing the Windows of applications into a buffer
2) Taking the drawn windows and composing (placing) them on the screen

Without compiz you only have to do the first step and draw directly to the screen, and this is already HW-Accelerated (DRI for example).

With compiz you have to do both steps, and to make matters worse, the first step will potentially NOT be HW-Accelerated.
So in a best case scenario Compiz will only be slower by the additional 2nd step. In the worst case it will do the entire first step using only the CPU (whereas it would be HW-Accelerated without Compiz) and have an additional 2nd step.

---

### Post by Stefanie on 2009-05-01
I use openbox because I use tons of keyboard shortcuts for all sorts of actions, but I still load a compositing manager, not Compiz but Cairo-compmgr. I use it for transparent terminals, it's nice if you can look through your terminal to look at the directions on some site. The dropdown shadows also make your desktop look less flat.

---

### Post by FraggedLocust on 2009-05-01
Right now I have compiz doing Expo, Cube and Ring Switcher with hotkeys as my main reasons for using Compiz. If anything, I say why mice? :P

---

### Post by boogers on 2009-05-01
I like the effects because they are awesome XD.  Plus when introducing a friend to Linux, a little eye candy doesn't hurt to draw them in.

---

### Post by Shpongle on 2009-05-01
> **FuturePilot said:**
> [LIST=1]
[*]Eye candy
[*]Letting your CPU do drawing operations on your screen is old school. Why not let something that's good at drawing graphical stuff do it, like your graphics card. This is exactly what Compiz does by offloading all the screen drawing to your GPU, thus allowing your CPU do to more other useful things
[/LIST]

thats cool i didnt know that it offloads to the gpu!, way to improve efficiency!

---

### Post by mp3_freak_721 on 2009-05-01
Because you can. You don't have to run it if you don't like it.

---

### Post by SomeGuyDude on 2009-05-01
I enjoy it. Why do we care if flash works? I don't do anything in my day that "requires" flash but I really like watching stuff on YouTube. Similarly, a smoothly running Compiz is one of the best aesthetic joys in all of computerdom.

---

### Post by Therion on 2009-05-01
The additional desktops are nice to help keep things "sorted" while I'm working.  I can keep my Internet radio-stream open on a desktop, separate from my spreadsheet, for instance.  It's a small thing I grant you, but once you get used to having it, it's hard to give up.

---

### Post by Npl on 2009-05-01
> **FuturePilot said:**
> Letting your CPU do drawing operations on your screen is old school. Why not let something that's good at drawing graphical stuff do it, like your graphics card. This is exactly what Compiz does by offloading all the screen drawing to your GPU, thus allowing your CPU do to more other useful thingsThere are two 2 steps involved.
1) Drawing the Windows of applications into a buffer
2) Taking the drawn windows and composing (placing) them on the screen

Without compiz you only have to do the first step and draw directly to the screen, and this is already HW-Accelerated (DRI for example).

With compiz you have to do both steps, and to make matters worse, the first step will potentially NOT be HW-Accelerated.
So in a best case scenario Compiz will only be slower by the additional 2nd step. In the worst case it will do the entire first step using only the CPU (whereas it would be HW-Accelerated without Compiz) and have an additional 2nd step.

Vista does the same (first step entirely on CPU), Windows 7 wont have that limit.

---

### Post by SunnyRabbiera on 2009-05-01
Compiz has become a big thing as people like flash and eye candy, now I can live without compiz personally and i really dont need it but I have gotten used to it being there :D

---

### Post by Grez on 2009-05-01
I've got a newish computer (onboard graphics) which I use as my main machine and it doesn't do compiz.

Upstairs, I've just refurbed a 6 year old machine (got rid of Win XP, added an old 128MB AGP fx5200 card, loaded Jaunty and installed compiz.) I love the cube because it's so easy to use and to sort out different things you're working on. It looks cool too. I don't see it as essential, but it's useful, nice to look at and fun. Didn't know it offloaded drawing tasks solely to the graphics card, so it's useful for productivity too.

As they say, if you don't like it, don't use it.

It add a little *je ne sais quoi* to my day and helps keep the kids off my main computer downstairs. So it's win-win for me!

:lolflag:

---

### Post by chucky chuckaluck on 2009-05-01
the only useful thing i do with my laptop is email myself reminders. otherwise, it's just a toy, so i want all the silly crap working.

---

### Post by wsonar on 2009-05-01
> **RaZe42 said:**
> Believe it ir not, but Compiz actually enhances my productivity, particularly the Scale(Like Expose on OS X) and Grid(think tiling WM) plugins. 

Wobbly Windows and the like are just nice extras for me, but I still think Wobbly Windows is underrated, it isn't useless as it gives a natural feel when moving windows.

Sorry I hate wobbly windows

But I like Cubed Desktop

6 one way half a dozen another :)

---

### Post by SomeGuyDude on 2009-05-01
> **SunnyRabbiera said:**
> Compiz has become a big thing as people like flash and eye candy, now I can live without compiz personally and i really dont need it but I have gotten used to it being there :D

It makes a sexy WM, too. It's fun to be running a system that's lighter on resources than a standard GNOME/KDE/XFCE desk but looks way cooler. ;)

---

### Post by Keyper7 on 2009-05-01
> **jfloydb said:**
> I didn't know what Compiz was until I looked on YouTube and watched some of the animated desktop videos.

If your knowledge is limited to watching those videos, you *still* don't know what Compiz is. Test it. Use it. Learn it. Customize it. Then take your own conclusions. The question is not "why should people use Compiz?", it is "why should I use Compiz?". And the only person who can answer this is yourself. But you can only answer it with sufficient knowledge about it, and such knowledge comes from experience.

Your question is no different from "why Gnome instead of KDE?", "why emacs instead of vi?", "why your favorite color is green and not blue?"...

---

### Post by wsonar on 2009-05-01
I'd say people want it to work same reason they want to watch video's burn cd's and play music.

it's a feature they know is available they have seen others use it and just want to have all the features working weather they use them or not

you may not use your cigarette lighter in your car much but you want it to work in case you you do want it  one day

---

### Post by gnomeuser on 2009-05-01
I have no problem with the technology as such, it can be used to enhance the computing experience and even enhance usability and accessibility. However Compiz is unintegratable by design choice, unstable and the development is without focus. It is not about fitting into the desktop where it can enhance things, it is increasingly about making stuff burn, beam up or worse. 

Additionally it causes crashes and instability for the platform. As such I have it disabled, but i do use compositing - just via Metacity instead.

---

### Post by chucky chuckaluck on 2009-05-01
> **gnomeuser said:**
> it is increasingly about making stuff burn, beam up or worse. 

worse? ooh! tell me more!

---

### Post by HammerOfDoubt on 2009-05-01
> **jfloydb said:**
> That doe's make sense...


That's not a valid rebuttal. The responses you quoted make perfect sense.

---

### Post by HammerOfDoubt on 2009-05-01
> **jfloydb said:**
> I want to start a friendly thread about a topic that seems to be quite important to Linux users. The subject is Compiz (if my spelling is correct) and Compiz fusion. I have noticed several complaints on this forum that Compiz doesn't work with 9.04. My question is this: what is so important about Compiz? What's the big deal? I suppose that it means some video card or driver is not functioning, which needs to be corrected, but the real question is: why would anybody want to use Compiz anyway?

I didn't know what Compiz was until I looked on YouTube and watched some of the animated desktop videos. I watched a few Compiz vids and thought (in a non-derogatory way), "so what, a dancing desktop". I was concerned when my wifi didn't work (8.04) and when my desktop didn't fit onto my screen (8.10). Now I'm quite happy; everything important works! 

Apparently I'm a stick-in-the-mud. I never use that neon desktop crap on Vista, for example. With Ubuntu, I use the Human desktop with a plain brown background and with the effects turned off. The flashy stuff seem like a waste of time to me, so why is so important to everyone else?

I have probably written too much to be interesting. But clue me in. Let me know why Compiz is important to you, my friend... Thanks...

When I was a teenager and opening up my first bank account, I got into a bank where the account agent did not tell me about the monthly fees until I was almost done setting it up. I told him to cancel the process because I didn't want to pay for something I can get free elsewhere. His response was "Oh, well think of how much you kids spend each week on entertainment, movies, music. What's five bucks a month? why do you care?"

You sound like that guy. The tone of your post is sort of rude and dismissive of people who don't like to keep their desktops as minimally spartan as yours is.

---

### Post by lykwydchykyn on 2009-05-01
I'm not running compiz, but I am using kwin4 with compositing enabled.  Your question is really "why have a compositing window manager?"

 - I use 8 desktops, and often they are all full of applications because I multitask a lot.  Something like "present windows" (expose on compiz) is priceless.  Also, the cube + transparency helps me locate which desktop a set of windows is on.
 - Transparency is useful when I'm writing a script or editing a config file and need to look at several windows at once.  I can make one a little bit transparent and still see the others behind it.
 - I stare at a computer screen 5 -10 hours a day.  Aesthetics is not trivial.  Effects that make onscreen objects appear more natural and physical seem to help make things easier to comprehend for me.  

Of course, some people don't need any of it.  I enabled compiz on my wife's laptop and she didn't care for it at all.  Whatever works for you.

---

### Post by Idefix82 on 2009-05-01
When I first enabled wobbly windows I thought "that's cute but useless". Of course, I left it anyway. After a few days I had to boot up Windows XP and it felt like having a brick in your hand instead of the usual feather you are used to. Moral: the effects make the computing experience more pleasant, they make the OS seem lighter and more natural and I think that that's important.

Secondly, Compiz has some features that are seriously useful, like transparency and tabbing. This is not to say that Compiz is the only WM with these features and I am sure there are valid reasons for using other WMs, too.

---

### Post by HavocXphere on 2009-05-01
> **mp3_freak_721 said:**
> Because you can.
That pretty much sums it up.

Any car can get you from A to B, but some cars do it with style & class.:KS

---

### Post by jfloydb on 2009-05-02
> **HammerOfDoubt said:**
> That's not a valid rebuttal. The responses you quoted make perfect sense.

> **HammerOfDoubt said:**
> When I was a teenager and opening up my first bank account, I got into a bank where the account agent did not tell me about the monthly fees until I was almost done setting it up. I told him to cancel the process because I didn't want to pay for something I can get free elsewhere. His response was "Oh, well think of how much you kids spend each week on entertainment, movies, music. What's five bucks a month? why do you care?"

You sound like that guy. The tone of your post is sort of rude and dismissive of people who don't like to keep their desktops as minimally spartan as yours is.

Friend, you missed the point of my comment. It was not intended to be a "rebuttle"; It was intended to be a positive response to a good answer.

Again, I wanted this to be a friendly thread where I could listen and learn something. Please don't turn this thread into something else...

Thanks to everyone who has tried to inform me concerning Compiz.

---

### Post by swoll1980 on 2009-05-02
> **HammerOfDoubt said:**
>  What's five bucks a month? why do you care?"



If someone said that to me, I would say fine, then you wouldn't mind paying it for me. Right?

---

### Post by mamamia88 on 2009-05-02
makes it more fun

---

### Post by chris4585 on 2009-05-02
Compiz zoom effect anyone?  Compiz zoom helps me a lot because of my poor eye vision.

---

### Post by Delever on 2009-05-02
> **Npl said:**
> There are two 2 steps involved.
1) Drawing the Windows of applications into a buffer
2) Taking the drawn windows and composing (placing) them on the screen

Without compiz you only have to do the first step and draw directly to the screen, and this is already HW-Accelerated (DRI for example).

With compiz you have to do both steps, and to make matters worse, the first step will potentially NOT be HW-Accelerated.
So in a best case scenario Compiz will only be slower by the additional 2nd step. In the worst case it will do the entire first step using only the CPU (whereas it would be HW-Accelerated without Compiz) and have an additional 2nd step.

Vista does the same (first step entirely on CPU), Windows 7 wont have that limit.

Just open some gtk program, for example, open office, and drag window over it. Watch open office behind it lag when redrawing contents.

Without compiz, if a window is moved, there is a need to redraw any window behind it. I will describe that briefly:

- You move a window
- any window visible behind it gets signal: redraw this area
- GTK must go over controls and send appropriate signal to every control in that area to redraw.
- I will be impressed if this is HW-accelerated. Even if it is, CPU is involved into this alot.

With compiz:
- New coordinates of window position are sent to GPU. Done! (simplified ;))

If you have good graphics card and enough memory, use Compiz. There is nothing to "save" with metacity.

---

### Post by Kareeser on 2009-05-02
Nothing wrong at all with metacity, it does its job superbly...

However, I find some nice accessibility improvements with Compiz as well. I use it to shuffle windows around MUCH faster than I would if I were to use my mouse.

The Expo plugin is also very nice if you want to see all of your workspaces at once.

---

### Post by apocalypse80 on 2009-05-02
Workspace management is just so much easier/faster with compiz.
Expose, scale and window rules (easier than devil's pie) are incredibly handy.

Performance-wise the system feels less snappy with compiz enabled, but far more consistent.
As already mentioned, moving a window around with compiz enabled doesn't require a full cpu core....

I also HATE gnome's focus stealing prevention and it doesn't allow me any configuration options - compiz does.

---

### Post by Calmatory on 2009-05-02
> **boogers said:**
> I like the effects because they are awesome XD.  Plus when introducing a friend to Linux, a little eye candy doesn't hurt to draw them in.

Why do you have to try to get people into linux anyway? What if I tried to introduce you to the music I listen to because I like it better than the music you like to listen to? Yeah, same thing.

Let people be and do what they want to, please!

---

### Post by swoll1980 on 2009-05-02
> **Calmatory said:**
> Why do you have to try to get people into linux anyway? What if I tried to introduce you to the music I listen to because I like it better than the music you like to listen to? Yeah, same thing.



What what be wrong with that? You mean you never once said to someone "Hey listen to this song"?

---

### Post by drawkcab on 2009-05-02
Compiz really helps me with my passtime, marine archeology.  I use the aquarium plugin to help plan my nautical adventures in advance.

---

### Post by chucky chuckaluck on 2009-05-02
> **Kareeser said:**
> The Expo plugin is also very nice if you want to see all of your workspaces at once.

just discovered that one today. might be too useful for me.

---

### Post by Npl on 2009-05-02
> **Delever said:**
> Just open some gtk program, for example, open office, and drag window over it. Watch open office behind it lag when redrawing contents.

Without compiz, if a window is moved, there is a need to redraw any window behind it. I will describe that briefly:

- You move a window
- any window visible behind it gets signal: redraw this area
- GTK must go over controls and send appropriate signal to every control in that area to redraw.
- I will be impressed if this is HW-accelerated. Even if it is, CPU is involved into this alot.

With compiz:
- New coordinates of window position are sent to GPU. Done! (simplified ;))

If you have good graphics card and enough memory, use Compiz. There is nothing to "save" with metacity.What are you doing while you are moving Windows? **Nothing** because you are moving windows!

Now consider you have 20 overlapping windows, since Compiz seperates both steps (and has plugin-architecture) it cant predict which Windows are (partially) visible and which arent.

If some of those Windows have animations/counter/whatever they will be redrawn in Compiz repeatly, even if they are fully occluded. Which yields to higher CPU-Usage while you are **doing something else** and could use the CPU there.

Compiz does break alot of stuff for me, like MDI-Windows (Code::Blocks) so there are ample reasons not to use it.

I dont have much interest in moving around Windows more smoothly or Desktop-Cubes. The only thing I miss is having thumbs in the App-Switcher, and Compiz is overkill for that

---

