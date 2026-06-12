---
title: "[IDEA] Option to disable Compiz for certain applications"
date: 2008-01-02
forum: Ubuntu Brainstorm
---

### Post by FuturePilot on 2008-01-02
I was thinking and I thought this might be a good idea in a couple different situations.

1.  Bill is a big gamer. He wants to get the best performance out of his graphics card. By disabling Compiz he can get a few extra FPS but doing this manually every time gets annoying and/or he doesn't know the command to do it manually.

2.  Sam has a somewhat older computer. It can run Compiz fine, but it doesn't run Compiz and a game at the same time very well. He needs as much GPU as he can get. By disabling Compiz he will see a huge performance increase. Same thing: doing this manually ever time gets annoying and/or he doesn't know the command to do it manually. 

I was thinking this could possibly be incorporated into Alacarte. See attachment. Or perhaps in a more obvious place? Basically it would execute "metacity --replace" before running the applications and then when the application is closed it would execute "compiz"

---

### Post by smartboyathome on 2008-01-02
Seems like a good idea to me, but it may have people asking why they don't have effects if a game crashes (effects may not be restored when an app crashes).

---

### Post by ninjkiran on 2008-02-05
A modification to this idea, the fact that most games wont even work with Compiz running~

The one Button switch approach works fairly well but perhaps something that detects OpenGL is being called by another program.  It would keep tabs on this program as long as the process is active but once the process shuts down it restores compiz.  Or rather be able to select in compiz itself which process's running would shut it down.

---

### Post by smartboyathome on 2008-02-05
That still doesn't take care of when a game crashes, though (same with resolution not being restored if you are playing a game at a different resolution than X). That is the biggest potential bug I see with this, and could be pretty annoying.

---

### Post by eye208 on 2008-02-10
Compiz should be off by default.

Why? Because OpenGL compositing conflicts with XVideo. After installing Ubuntu for the first time, many new users find themselves unable to play back video. Just look at the number of threads related to this problem.

This is a bad thing. It is damaging Ubuntu's reputation.

Making X11 software rendering the default output method of Totem is no solution. X11 output looks pixelated when scaled to fullscreen. This is not what you would expect from a state-of-the-art desktop operating system.

---

### Post by smartboyathome on 2008-02-10
If it were off by default, I think we would find a lot of upset users saying "why don't I get all the cool effects like in Gutsy?". Personally, I like that Compiz is on by default, it provides many cool effects that people like.

---

### Post by IsawSp4rks on 2008-04-03
> **eye208 said:**
> Compiz should be off by default.

Why? Because OpenGL compositing conflicts with XVideo. After installing Ubuntu for the first time, many new users find themselves unable to play back video. Just look at the number of threads related to this problem.

This is a bad thing. It is damaging Ubuntu's reputation.

Making X11 software rendering the default output method of Totem is no solution. X11 output looks pixelated when scaled to fullscreen. This is not what you would expect from a state-of-the-art desktop operating system.

The problem you describe is only an issue for ATI and Intel drivers.  Nvidia drivers work with Xv within Compiz Fusion.

There are two solutions possible and one already available:-
[LIST]
[*]Get Intel and ATI drivers up to the same specs as Nvidia, that, is allow Xv to work with compositing and thus Compiz Fusion on ATI and Intel VGA chipsets.  As Nvidia's driver is closed source that may be harder to achieve in the short term.

[*]Modify Totem's Xv output to be 'Compiz Fusion aware' a la the [Mplayer 1.0rc2 Xv compositing capable patch]("http://ubuntuforums.org/showthread.php?t=636277&highlight=mplayer+compiz") that's already available.  Totem is open source and so this seems a likely option should the developers and Canonical come together to make it happen.

[*][URL="http://ubuntuforums.org/showthread.php?t=636277&highlight=mplayer+compiz"]
[*]Use Mplayer 1.0rc2 source along with the aforementioned patch[/URL] and compile a working Mplayer (integrating whatever skins you might prefer) that works happily in Xv fully accelerated with Compiz Fusion.
[/LIST]

Hope that helps.

---

### Post by Martje_001 on 2008-04-03
> **smartboyathome said:**
> That still doesn't take care of when a game crashes, though (same with resolution not being restored if you are playing a game at a different resolution than X). That is the biggest potential bug I see with this, and could be pretty annoying.
That's not true. If the game crashes the process ends, and the effects will be restored. However, if the game crashes, the resolution will not be restored, because the game does this.

Simple said: Enable/Disable effects got nothing to do with the application.

---

### Post by Outworlder on 2008-04-03
> **Martje_001 said:**
> That's not true. If the game crashes the process ends, and the effects will be restored. However, if the game crashes, the resolution will not be restored, because the game does this.

Simple said: Enable/Disable effects got nothing to do with the application.

So what? 

If the game crashes, Compiz or whatever else you got must be watching, to be able to turn the effects back on. If the game crashes, whatever is watching would be able to change the resolution back as well. It's the same thing.

This whole "enable/disable-compiz-button" is just an ugly hack. The proper solution is to fix whatever is causing those problems.

---

### Post by zikade on 2008-04-04
> **Outworlder said:**
> So what? 
This whole "enable/disable-compiz-button" is just an ugly hack. The proper solution is to fix whatever is causing those problems.

I'd like to agree, but then getting the drivers fixed seems to be a task which nobody outside AMD or Intel can do. So it might be not the optimal solution, agreed, but much better as turning compiz off - manually - run your 3D-app and afterwards turning it on again.

But then - perhaps I am just lazy....

---

### Post by xelapond on 2008-04-07
I think this is a great idea, but should be implemented into compiz itself, and not gnome or Ubuntu.  I run KDE4, and a program called eagle for schematic design.  It does not render correctly with compiz on, so I have to manually run kwin --replace.  That gets annoying.  Even if the game/program does crash its not that hard to start compiz back up.  It could even put a window under the game/program that closes it the game returns an exit code, but if it does not the use will see it and they could click start compiz.

---

### Post by pwnprog on 2008-08-14
i agree that this is a good idea. i love how compiz looks, but certain apps take a small performance hit, or simply do not work well with compiz. (matlab comes to mind) it would be nice if compiz had a section saying "disable compiz for these applications". it would list all apps installed on your system, and you could click a check box beside the apps which you would like to disable it for.

---

### Post by rahulthewall3000 on 2008-08-15
> **FuturePilot said:**
> I was thinking and I thought this might be a good idea in a couple different situations.

1.  Bill is a big gamer. He wants to get the best performance out of his graphics card. By disabling Compiz he can get a few extra FPS but doing this manually every time gets annoying and/or he doesn't know the command to do it manually.

2.  Sam has a somewhat older computer. It can run Compiz fine, but it doesn't run Compiz and a game at the same time very well. He needs as much GPU as he can get. By disabling Compiz he will see a huge performance increase. Same thing: doing this manually ever time gets annoying and/or he doesn't know the command to do it manually. 

I was thinking this could possibly be incorporated into Alacarte. See attachment. Or perhaps in a more obvious place? Basically it would execute "metacity --replace" before running the applications and then when the application is closed it would execute "compiz"

Have you tried fusion-icon which lets you change your WM with a single click. You can also use compiz with or without emerald. I use it quite regularly and it is a brilliant piece of software as far as I am concerned.

---

