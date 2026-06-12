---
title: "How come we need a composite manager and Windows doesn't?"
date: 2007-05-17
forum: Windows
---

### Post by Nonno Bassotto on 2007-05-17
Today we have nice grphical features on Linux, like wobbling windows, transparencies, workspaces on a cube, clones of OSX dock and so on. However, for all this to work the use of a composite manager, like Compiz or Beryl or xcompmgr is required. Without these, we used to have just imitations of these effects. For instance we had the dock for gDesklets or we could set the transparency level of the gnome terminal, but both these only worked by drawing the wallpaper, so you could easily notice you didn't have real transparency when you tried to put a window behind it.

Instead we have quite a lot of programs using real transparency in WindowsXP, for example [RocketDock]("http://www.punksoftware.com/rocketdock"), [UberIcon]("http://www.punksoftware.com/ubericon") or [MusikCube]("http://www.musikcube.com/") (the latter is a music program, but you can set the level of transparency of its window). You can even have a [spinning cube]("http://chsalmon.club.fr/index.php?en/Yod-m-3d-about").

Still I never heard of Windows using a composite manager. How come all of this is possible in Windows?

---

### Post by jariku on 2007-05-18
As far as I know, the Aero interface in Windows Vista is using a composite window manager. It's called DWM (Desktop Window Manager).

[http://en.wikipedia.org/wiki/Desktop_Window_Manager](http://en.wikipedia.org/wiki/Desktop_Window_Manager)

---

### Post by 3rdalbum on 2007-05-18
There's true transparency in KDE without a composite manager (I believe?), but of course it only works with KDE and Qt applications.

Since Windows XP contains its own graphical shell, the same sort of thing must apply. Unless my assumption about KDE is incorrect and it does have some genuine compositing features.

---

### Post by igknighted on 2007-05-18
Xfce also has a composite manager.  It doesn't have the high graphical requirements of beryl and can run true transparencies as well as kibadock/avant just fine.  You can even run it (not well tho) without a 3d driver installed.  It does still fail with fglrx though.  The point?  Composite WM doesn't mean that much.  I bet the windows WM for XP has composite ability natively, the only reason its a big deal in linux is because our native WMs (up to now) don't have that ability.

---

### Post by Nonno Bassotto on 2007-05-18
> **jariku said:**
> As far as I know, the Aero interface in Windows Vista is using a composite window manager. It's called DWM (Desktop Window Manager).

[http://en.wikipedia.org/wiki/Desktop_Window_Manager](http://en.wikipedia.org/wiki/Desktop_Window_Manager)

Indeed I was talking about WindowsXP.

---

### Post by Nonno Bassotto on 2007-05-18
> **igknighted said:**
> Xfce also has a composite manager.  It doesn't have the high graphical requirements of beryl and can run true transparencies as well as kibadock/avant just fine.  You can even run it (not well tho) without a 3d driver installed.  It does still fail with fglrx though.  The point?  Composite WM doesn't mean that much.  I bet the windows WM for XP has composite ability natively, the only reason its a big deal in linux is because our native WMs (up to now) don't have that ability.

I know you don't need 3d acceleration to run a composite manager (this is the reason I mentioned also xcompmgr). It is possible that explorer includes a composite manager, still I didn't find any evidence of this. Anybody knows better?

---

### Post by Ateo on 2007-05-18
> **3rdalbum said:**
> There's true transparency in KDE without a composite manager (I believe?), but of course it only works with KDE and Qt applications.

You are correct. But it's infantile compared to what Beryl can do.... 

There is talk about adding Beryl features to KDE. But this is, of course, just talk. Nothing official.

---

### Post by jariku on 2007-05-18
> **Nonno Bassotto said:**
> Indeed I was talking about WindowsXP.
I realise that now, but you do mention Windows four times in your post and only on one occasion it's specifically Windows XP.

As for the transparencies in Windows XP, I don't know how it's done.

---

### Post by STREETURCHINE on 2007-05-22
> **jariku said:**
> I realise that now, but you do mention Windows four times in your post and only on one occasion it's specifically Windows XP.

As for the transparencies in Windows XP, I don't know how it's done.

a little program called glass2k will help with transparency,not as good as beryl but it is not bad

as to the spinning cube yes it can be done and i have it on windows xp but it is joke compared to beryl.

---

### Post by Nonno Bassotto on 2007-05-22
I'm not asking about what you prefer, if Beryl or Compiz or some custom effect on WinXP.

I'm asking a technical question: does Explorer incorporate a composite manager? And if the answer is no, how come you can get transparencies in WinXP?

---

### Post by STREETURCHINE on 2007-05-22
windows xp does not have a composite manager as such ,but you can down load programs to do the transparency,and the cube.
the effects these programs give you are basic and clunky.

the composite manager combines together a window manager and a composite manager using OpenGL for rendering. A "window manager" allows the manipulation of the multiple applications and dialog windows that are presented on the screen. A "composite manager" allows windows and other graphics to be combined together to create composite images.

---

### Post by Nonno Bassotto on 2007-05-23
A window manager does what the name suggests. it manages windows. That is, it draws their borders, lets you move them and so on.

A composite manager is a system utility which allows different programs to interact. Basically the differents programs instances send data to the composite manager rather than to the video output directly, and this allows the manager to combine this data before forwarding it to the video output, in order (for example) to obtain transparencies.

The composite manager can make use of the acceleration of the video card or not, and this is not the point here.

As far as I understand WindowsXP does not feature a composite manager, meaning that the different windows send their output directly to the video (the equivalent of X?). I'm NOT sure of this point. If things stand this way, I don't understand how two different outputs can interact, to create, for instance, a transparency effect.

---

### Post by Cows on 2007-05-23
Yea im pretty sure that WIndows XP has a composite manager installed by default. Maybe Explorer ? but besides that im guessing that the spinning cube is only available to vista .. so you still would need to have a good Video Card + Memory + Processor ( or the basic requirements for vista home premium ) to run the cube.

---

### Post by tehbeermang on 2007-05-25
> **Nonno Bassotto said:**
> Still I never heard of Windows using a composite manager. How come all of this is possible in Windows?
Couldn't tell you, they don't give out the source code.

---

### Post by Nonno Bassotto on 2007-05-26
> **tehbeermang said:**
> Couldn't tell you, they don't give out the source code.

But they will give some API at least. How can a programmer use the feature if nobody can even tell if it's there?

---

### Post by STREETURCHINE on 2007-05-26
so what are you exactly after .windows xp does not use a composite manager  i have already told you this.
ubuntu uses one thats why the graphics are so good.
i dont know what you are asking here you just seem to want to argue.
come to the point or just leave it alone.

---

### Post by Nonno Bassotto on 2007-05-26
I'm not trying to argue. I'm trying to understand a technical point that noone has been able to explain so far. Some say that WinXP has a composite manager, but they fail give any reference to this, Other, like you, say it doesn't, but they don't explain how different windows from different applications can interact (for instance to create transparencies).

Really, I'm not trying flame, I'm just curious to understand. If I wanted to write a program which uses the transparency, whould I have any API available? And how is that API implemented?

I don't care about good or bad graphics. I prefer the Ubuntu graphics too, but this is not the point in discussion.

---

### Post by Matakoo on 2007-05-26
> **Cows said:**
> Yea im pretty sure that WIndows XP has a composite manager installed by default. Maybe Explorer ? but besides that im guessing that the spinning cube is only available to vista .. so you still would need to have a good Video Card + Memory + Processor ( or the basic requirements for vista home premium ) to run the cube.

Just an idea...could it be that DirectX provides a composite manager?

---

### Post by STREETURCHINE on 2007-05-26
> **Nonno Bassotto said:**
> I'm not trying to argue. I'm trying to understand a technical point that noone has been able to explain so far. Some say that WinXP has a composite manager, but they fail give any reference to this, Other, like you, say it doesn't, but they don't explain how different windows from different applications can interact (for instance to create transparencies).

Really, I'm not trying flame, I'm just curious to understand. If I wanted to write a program which uses the transparency, whould I have any API available? And how is that API implemented?

I don't care about good or bad graphics. I prefer the Ubuntu graphics too, but this is not the point in discussion.

well for the tech stuff you should go ask  on a microsoft forum the techs there will be able to answer that question better.

as to the API have no idea i am not a programmer .as i said before in windows xp no composite by default.but you can install third party programs that give you transparency and the cube(but poor quality)

ubuntu i dont think the composite manager is there by default(i could be wrong)you have to install it to get the effects,like transparency and the cube ,wobbly windows.

other than that i dont know about the technical side of it.nor it seems does any one else that is why you have not recieved the technical answer you were looking for.

---

### Post by marsmissionaries on 2007-05-28
If windows XP has a compositing manager it would be used in all windows programs.

HOWEVER, only SOME programs make use of transparency. These programs are SOFTWARE RENDERED. It is a very common technique used by many software developers. It is mainly used because not everybody has the latest and greatest video card. With software rendering you need a decent amount of ram and a decent cpu.

Compositing is done through the graphics card and is MUCH MUCH MUCH more advanced than simple transparency. The windows window enviornment is more developed in certain areas, so it is compatible with software rendering, not to mention they default plug and play drivers for graphics are better so yes windows is capable of rendering transparency. But no windows XP does not have a compositing manager.

---

### Post by FuturePilot on 2007-05-29
This is interesting as I've always wondered about this too since I found out how eye candy in Linux works. All I know is that you can make windows transparent when you move them or all the time with the Nvidia drivers.

Perhaps this could explain better. Taken from the Glass2k web page
> Windows 2000 and Windows XP have native support for transparency (alpha) settings which makes it easier to make transparent windows.

---

### Post by Cyvros on 2007-05-29
There are programs for XP that can actually apply Beryl- or Aero-type effects to windows, (probably) the most popular of which is WindowBlinds - I used to use it on XP to get all shnazzy transparency effects. Comparitively, apps like Glass2k are positively primitive.

Of course, WB only 'emulates' much of these effects (very well, though) and has nowhere near the flexibility or range of fancy, smancy effects of something like Beryl. :P

Anyway, that was a phase I've grown out of now. It's Blackbox for me. :D

---

