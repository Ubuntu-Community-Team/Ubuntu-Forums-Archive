---
title: "Installing Visual Basic"
date: 2009-09-01
forum: Wine
---

### Post by gobberpooper on 2009-09-01
I'm taking an intro to computer science course offered by my high school and our teacher said that he can offer a full licensed version of Microsoft Visual Basic. I asked him what to do if we're running linux and he told me to check its compatibility with WINE.WineHQ says that Visual Basic is garbage. But these tests are very old. Before I get Visual Basic has anybody run any more recent tests?

---

### Post by jpeddicord on 2009-09-01
Haven't tried myself, but installing [MonoDevelop]("apt:monodevelop") with the [VisualBasic runtime libraries]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=visualbasic") might be an alternative.

---

### Post by jasonditz on 2009-09-01
I'd try to download the Express Edition first and see if that works. Personally I think VB.NET is one of the nicest development environments out there, but with MonoDevelop already native there's probably not a ton of work being put into getting it Wine compatible.

---

### Post by jasonditz on 2009-09-02
I tested the VB.NET Express Edition 2008 and it doesn't work at all in Wine. I suspect the retail version of Visual Studio will be the same (and WineHQ's app db suggests this is also the case). 

I doubt it'll be useful for the class, but MonoDevelop's VB.NET support has actually gotten decent (just make sure to "sudo apt-get install vbnc" because for some reason just installing MonoDevelop and Mono doesn't).

---

### Post by directhex on 2009-09-02
> **jasonditz said:**
> for some reason just installing MonoDevelop and Mono doesn't).

Most people using MonoDevelop are going to use it for C# - technically though MD supports many languages & doesn't force environments for any of them to be installed

---

### Post by jasonditz on 2009-09-02
> **directhex said:**
> Most people using MonoDevelop are going to use it for C# - technically though MD supports many languages & doesn't force environments for any of them to be installed

I guess that's true, but if someone coming over from Windows is trying to use MonoDevelop as a replacement for Visual Studio they'd expect both C# and VB.NET to come with it.

---

### Post by directhex on 2009-09-02
> **jasonditz said:**
> I guess that's true, but if someone coming over from Windows is trying to use MonoDevelop as a replacement for Visual Studio they'd expect both C# and VB.NET to come with it.

So where should I stop? Include GCC and G++ since MD supports those? Boo? Java? Python?

---

### Post by jasonditz on 2009-09-02
> **directhex said:**
> So where should I stop? Include GCC and G++ since MD supports those? Boo? Java? Python?

[http://mono.ximian.com/monobuild/snapshot/sources-trunk/](http://mono.ximian.com/monobuild/snapshot/sources-trunk/)

I'd say those top four that are bunched together under "mono" would be stuff most people would expect to find. 

Not that it's ruining anyone's life to have to add vbnc support afterward, I guess I assumed it was a more popular part of the system though.

---

### Post by directhex on 2009-09-02
> **jasonditz said:**
> I guess I assumed it was a more popular part of the system though.

There isn't a single app in Ubuntu written in VB.NET

---

### Post by jasonditz on 2009-09-02
> **directhex said:**
> There isn't a single app in Ubuntu written in VB.NET

Wow, that's surprising. I guess there's no point in bundling it after all, are people just using it for ASP.NET? 

It seems a shame that a perfectly good language like that isn't been used for something by someone.

---

### Post by directhex on 2009-09-02
> **jasonditz said:**
> Wow, that's surprising. I guess there's no point in bundling it after all, are people just using it for ASP.NET? 

It seems a shame that a perfectly good language like that isn't been used for something by someone.

No idea. I only packaged it a year ago. Personally I think VB's a crap language, but as long as people are learning it, they should be able to learn it on Ubuntu

---

### Post by masque7 on 2009-10-23
> **directhex said:**
> No idea. I only packaged it a year ago. Personally I think VB's a crap language, but as long as people are learning it, they should be able to learn it on Ubuntu
Proprietary language, proprietary standards, proprietary IDE/visual environment... open-source operating system.

I share your pain, I have to use VB.NET/Visual Studio 2008, too. I'm currently looking into MonoDeveloper+mono-vbnc+gtksharp-2. Whilst I only have to create simple applications so far, hand coded buttons and the like is a little tedious. 

The alternatives seem to be: integrate gtk-sharp2 with VB.NET using mono and the VB compiler, or just use Visual Studio and then do what you can with MonoDev....

---

### Post by grndzro on 2009-10-24
You can practically build a Win XP environment in Wine. Hell I got DX9.0c to work. I have installed VB in the past, I don't see why you can't use it to learn VB.

Imo your time would be much better spent learning something like Java/PHP/C/Maya.....etc (I'm not a fan of anything MS)

---

### Post by masque7 on 2009-10-30
> **grndzro said:**
> You can practically build a Win XP environment in Wine. Hell I got DX9.0c to work. I have installed VB in the past, I don't see why you can't use it to learn VB.

Imo your time would be much better spent learning something like Java/PHP/C/Maya.....etc (I'm not a fan of anything MS)
Most of us here are forced into using VB.NET. Wine appdb gives Visual Studio 2005, and 2008 'garbage'

Good luck to anyone that wants to get VS working...

---

### Post by grndzro on 2009-10-31
that's using wine in it's default setup. 
it takes a lot of tweaking to get VB installed. just save yourself the headache, install Virtualbox.

---

