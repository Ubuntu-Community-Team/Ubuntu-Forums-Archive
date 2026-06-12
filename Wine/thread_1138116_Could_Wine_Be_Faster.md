---
title: "Could Wine Be Faster?"
date: 2009-04-26
forum: Wine
---

### Post by jsbe on 2009-04-26
Hello everyone!

This is my first thread at ubuntuforums.org, so please keep cool when you see that this question had been asked before.

My question is:

Could wine be faster in 3D rendering? I use Ubuntu 9.04 Jaunty (just updated) and I have a nVidia GeForce 6200 - Driverversion 180.44.

The game I wanted to play was TrackMania Nations Forever. So I went to the WineHQ website and installed everything like it was written there. 
Then I started TM and got only 10fps (with lowest graphical settings)! I looked for some answers in the web. Someone said it's because of the GLSL, so I deactivated it and wow I had 90fps! But after I restarted Ubuntu, wine was as slow as it was at the beginning.
So my simply question is: How can I make wine as fast as it was when GLSL was deactivated, or can I deactivate GLSL for all time?

Thanks for your answers (and sry for my bad english).:lolflag:

---

### Post by =^,^= on 2009-04-26
You can add a registery entry to disable glsl!

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

That should be a start!

---

### Post by jsbe on 2009-04-26
That's my problem. I deactivated GLSL through the registery, but after a restart, it doesn't work anymore...:(

---

### Post by =^,^= on 2009-04-26
> **jsbe said:**
> That's my problem. I deactivated GLSL through the registery, but after a restart, it doesn't work anymore...:(

That makes no sense!

Did you update to 1.1.20 yet?

---

### Post by jsbe on 2009-04-26
I made an update, but it changed nothing... Only the frame rate went from 10 to 15fps...:(:confused:

---

### Post by =^,^= on 2009-04-26
At least thats slightly better!

I dont know what else would help you!

Do you have a new or old graphics card?

---

### Post by JK3mp on 2009-04-26
Yeah...big downfall in using wine, its reliability sucks.

---

### Post by asdfoo on 2009-04-26
> **JK3mp said:**
> Yeah...big downfall in using wine, its reliability sucks.

If you have nothing constructive to add, please don't post.

Wine is very convenient for a large number of users, if you need something more reliable then you're welcome to go back to windows.

Also, to the other poster disabling glsl is unlikely to improve things.

You can try changing OffscreenRenderingMode to fbo

---

### Post by Meow27 on 2009-04-26
the dib engine needs to be implemented, without it, most apps will run slower than they should

---

### Post by asdfoo on 2009-04-26
> **Meow27 said:**
> the dib engine needs to be implemented, without it, most apps will run slower than they should

not really... it wouldn't change how OpenGL or D3D apps like WoW work.

---

### Post by Meow27 on 2009-04-26
> **asdfoo said:**
> not really... it wouldn't change how OpenGL or D3D apps like WoW work.

well, either way its going to be slow, since wine is spending time translating windows api into linux api (dont even know if thats the right name for it)

---

### Post by asdfoo on 2009-04-26
> **Meow27 said:**
> well, either way its going to be slow, since wine is spending time translating windows api into linux api (dont even know if thats the right name for it)

Not really.  A lot of applications run with no noticable difference to speed with heavy use of the Windows API, some even run faster than the Linux equivalents.

I think you're just making things up without any hard evidence.

---

### Post by jsbe on 2009-04-27
Thank you for answering! - I just changed the OffscreenRenderingMode to fbo. Now Wine works really faster - 45fps...

I also think that Wine is a really great application, because theres no need to use a virtual machine or something like this...:)

---

### Post by asdfoo on 2009-04-27
> **jsbe said:**
> Thank you for answering! - I just changed the OffscreenRenderingMode to fbo. Now Wine works really faster - 45fps...

I also think that Wine is a really great application, because theres no need to use a virtual machine or something like this...:)

Good to hear... performance improvements are always being worked on, so look forward to future versions giving higher fps in a wide range of games

---

### Post by gotsanity on 2009-04-29
another tweak you can do that generaly helps performance with most wine apps is to disable the error message output

```

$ WINEDEBUG=-all wine /path/to/app

```

and another thing you can do is to make "bottles" for your application. Doing this makes it so that if two apps need different winecfg or registry edits that conflict they wont interfere with each other. In order to pull this off just make a copy of your /home/username/.wine folder and rename it to /home/username/.wine_yourapp then when you run the app you want to run it using the wineprefix. For example. I have the following structure:

```

/home/gotsanity/.wine (basic wine bottle)
/home/gotsanity/.wine-sc (starcraft's bottle)
/home/gotsanity/.wine-l4d (left4dead's bottle)

```

starcraft is run as such:

```

env WINEPREFIX="/home/gotsanity/.wine-sc" WINEDEBUG=-all wine $HOME/.wine-sc/drive_c/\Program\ Files/Starcraft/StarCraft.exe

```

and L4D is run like so:

```

$ env WINEPREFIX="/home/gotsanity/.wine-l4d" WINEDEBUG=-all wine $HOME/.wine-sc/drive_c/\Program\ Files/Steam/steam.exe

```

in order to edit each registry or winecfg you will need to do this:
```

$ env WINEPREFIX="/home/username/.wine-bottle-to-edit" wine regedit
$ env WINEPREFIX="/home/username/.wine-bottle-to-edit" winecfg

```

And one last trick you can do is to run the application in a second X display (without all the compiz, metacity, etc effects... However this one is a much longer and more difficult tutorial so I will just post a link to the thread I learned to do it on.

[http://ubuntuforums.org/showthread.php?p=5144003]("http://ubuntuforums.org/showthread.php?p=5144003")

---

