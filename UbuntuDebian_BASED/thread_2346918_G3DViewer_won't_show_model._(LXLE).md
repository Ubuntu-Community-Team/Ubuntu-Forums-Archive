---
title: "G3DViewer won't show model. (LXLE)"
date: 2016-12-20
forum: Ubuntu/Debian BASED
---

### Post by lukon on 2016-12-20
I use LXLE on this old Compaq Presario R3000 laptop.

I installed a 3D model viewer called "G3DViewer" to look at 3d models in formats like .obj.

I load a test .obj file (from a web site with test models for just this purpose) into G3DViewer and a message on the bottom of the window says the file loaded successfully. But all I see in the viewer window is the background colour. I tried changing various view settings and navigating the model space, but nothing reveals the object.

Anyone know why no object appears?

---

### Post by DuckHook on 2016-12-20
Oh goodness. I haven't seen one of those lumbering beasts in over a decade. Weighed more than a brick. I used to hold mine out at arm's length to do squats…

…but I digress.

The fact that you got it running at all… my hat's off to you. If I recall, it has a tiny little CPU with a tiny little GPU that does not even have discreet DRAM. It "borrows" video memory from system RAM which is pretty spartan to begin with, around 256 MB if I recall. I don't remember if the GPU even has 3D acceleration.

Long story short: I'm pretty sure that your unit is simply not capable of what you are asking it to do. 3D modelling is not trivial. The equipment you have (unfortunately) *is*.

I would hate to see you get rid of it just because of this. You are asking something of it for which it was not designed. But it's still *The Little Engine That Could* if you give it the right tasks, say, backup server, torrent server, etc without the burden of a GUI.

At any rate, your query (and your avatar) almost make me feel young again&#8213;and I thank you for that&#8213;I wonder how many of our younger members know where that picture comes from?

---

### Post by howefield on 2016-12-20
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by lukon on 2016-12-20
Thanks for your speculation, DuckHook.

Yr speculation seems highly plausible.

What seems a bit odd is this: since I wrote that post I experimented by actually installing Blender on this laptop and importing the same .obj files, as well as other .obj files. And this worked. Blender displays them fine. I was sceptical whether this laptop would even load Blender, let alone display a model. But it all worked.

I use the laptop when I take extended trips, such as right now, and for playing dance mixes into P.A. systems at the televised dance parties I produce.

Ya. The avatar I use shows my everlasting crush on UFO's Gay Ellis, and the fact that I got on board Ubuntu with their release called "Dapper Drake", as Gay Ellis was played by Gabrielle Drake.

---

### Post by DuckHook on 2016-12-20
> **lukon said:**
> &#8230;Yr speculation seems highly plausible&#8230;But it all worked.Heh, heh. It's nice of you to say that, but my speculation is out to lunch if you got Blender to work and display properly. Obviously, there's more in that *Little Engine That Could* than I gave it credit for. Gives me a warm feeling, to be honest. I've a soft spot for old-geezer equipment that can still strut its stuff.> I use the laptop when I take extended trips, such as right now, and for playing dance mixes into P.A. systems at the televised dance parties I produce.If you actually travel with that thing, then I'm even more impressed. As for the dance parties&#8230; this makes our *Little Engine That Could* a very hip and happenin' unit.> The avatar I use shows my everlasting crush on UFO's Gay Ellis, and the fact that I got on board Ubuntu with their release called "Dapper Drake", as Gay Ellis was played by Gabrielle Drake.Aw. You had to go and give it away. I was hoping for something to challenge the youngsters.

My eye was always drawn to Wanda Ventham. Her son's done pretty well lately too (now don't go giving *that* one away ;) ).

Re: your original question.

It's always useful to look at the logs to chase something down. In your case, it would be useful to bring up *dmesg* right after you launch G3DViewer and try to open a file. Also useful is having *top* running when you launch app and load file. Not least, try wading through syslog. Yet another strategy is to launch the app from a terminal command line and note whatever error messages are thrown out when you try to manipulate the object.

Of course, if Blender does the trick for you, then these other procedures are pretty academic unless you are just curious.

I note that you use LXLE. My help is limited on that OS, as there are enough differences to render my knowledge inapplicable.

---

### Post by lukon on 2016-12-22
Well, I'm only stuck using my laptop for a few more weeks. So I will use Blender if I need to for this time.

I know nothing about Wanda's son. I did not even know she had one.

---

### Post by DuckHook on 2016-12-22
> **lukon said:**
> I know nothing about Wanda's son.He's a fine actor who's played the titular role in *Sherlock*, Smaug in *The Hobbit*, Alan Turing in *The Imitation Game* and is now starring in *Dr Strange*. Benedict Cumberbatch. Wanda must be pretty proud of him.

But the fact that even her son is now 40. :sigh: Time sure flies.

Good luck with your faithful old laptop and have a great Holiday Season!

---

