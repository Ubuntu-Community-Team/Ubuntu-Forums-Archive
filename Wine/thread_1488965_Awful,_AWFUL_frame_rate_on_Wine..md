---
title: "Awful, AWFUL frame rate on Wine."
date: 2010-05-20
forum: Wine
---

### Post by LazyLlama on 2010-05-20
Hey guys.
I'm very new to Wine. Very. I've pretty much just installed it.
I'm using Ubuntu 10.04 and upon seeing many videos on Youtube such as "Team Fortress 2 On Wine!", seeing it run flawlessly, and I thought I'd give it a go.

Now, I'm using the Dell Studio 1555, which has pretty awful graphics. It is a laptop after all. I managed however, with a few mods I could get Team Fortress 2 running full frame rate at correct screen ratio and medium graphics - on Windows. I thought I could then run it on Wine with very small ratio and lower graphics, and I would be fine.

I wanted to test run it first, I ran Macromedia Flash 8, worked flawlessly. Then I ran Steam. Pretty bad response time with everything. But, before wasting bandwidth and time, I thought I'd run a smaller, easier game - just to see what it was like (after Steam ran badly). So I tried Plants Vs Zombies.
I got like 1fps. Yikes. Is this normal? PvZ can run on 100mb of RAM on Windows 98.
Also, I tried Civ 4 and AoM. Both just crash before starting.
So please, am I doing it wrong? Are there any settings or something I need? Or is it just not going to work?
What about PlayOnLinux - will that give me better results?

Any help will be much appreciated!

-The Cat

---

### Post by hikaricore on 2010-05-20
Please avoid posting in the form of rambles and endless questions.

Your main issue probably going to be either "video" hardware or drivers.
We're going to need to know what kinda video card you have and what driver you're using for it.
Laptops tend to use lowend chipsets like intel and are often problematic when trying to do anything gaming wise.
Yes yes yes we know it worked on windows, that means nothing.  If your hardware doesn't have proper OpenGL support
and isn't supported well by the available drivers, nothing you can do will fix it.

POL won't work any better than wine because it is wine with a simple frontend.

---

### Post by LazyLlama on 2010-05-20
Apologies, I'll try to avoid doing so next time.
Is there any code I can use to post my system information, if it's of any use?

---

### Post by Axanon on 2010-05-20
I'm not sure if it's in the repos, but there is a script called **inxi** which will output your system information in many different ways.

---

