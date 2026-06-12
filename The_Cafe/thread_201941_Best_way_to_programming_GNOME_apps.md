---
title: "Best way to programming GNOME apps?"
date: 2006-06-22
forum: The Cafe
---

### Post by nemesa on 2006-06-22
Hi!

I would like to learn programming GUI apps for GNOME. Which are the best programming languages / tools / ways for that purpose? I know PHP and I work with it everyday... I learned Pascal, C, Visual Basic (.NET) in school... and tasted Java and C# a bit.

What do you recommend?

Thanks... :)

---

### Post by GeneralZod on 2006-06-22
Ruby and Python have great GTK bindings, and are wonderfully easy languages to learn and use.

---

### Post by xtacocorex on 2006-06-22
I've been messing with Python and GTK+ and using Glade to design the interface for my program.

---

### Post by zachtib on 2006-06-22
[QUOTE=xtacocorex]I've been messing with Python and GTK+ and using Glade to design the interface for my program.[/QUOTE]

thats what id recommend.  im using python, gtk, and glade for gTorrent.  Python was incredibly easy to learn and use.

---

### Post by Kimm on 2006-06-22
If you know VB.NET you can use that...

I havnt tried GTK# in VB, but its great in C#!

---

### Post by Virogenesis on 2006-06-22
Surprised no one has suggested mono as nemesa has done a bit of c#

---

### Post by Kvark on 2006-06-22
I agree that Python is the way to go. Python programs are usually shorter, cleaner and clearer then programs in most other languages.

For the GUI use wxWidgets. GTK and wxWidgets both uses GTK widgets so they achieve exactly exactly the same result and blend in perfectly with Gnome. Therefore GTK has no real advantage over wxWidgets. wxWidgets on the other hand has a big advantage if you would ever want to port one of your apps to other platforms. It blends in perfectly on Windows and OSX too by using the native widgets on those platforms.

---

### Post by bruce89 on 2006-06-22
[QUOTE=Virogenesis]Surprised no one has suggested mono as nemesa has done a bit of c#[/QUOTE]
Saying as that's true, MonoDevelop is a nice IDE for C#, VB.net etc.

---

### Post by Kimm on 2006-06-22
[QUOTE=Virogenesis]Surprised no one has suggested mono as nemesa has done a bit of c#[/QUOTE]

Ehem... I believe I suggested VB.NET...

---

### Post by Virogenesis on 2006-06-22
[QUOTE=Kimm]Ehem... I believe I suggested VB.NET...[/QUOTE]
Unaware that mono supported VB.net, no getting offended by a simple mistake.

---

### Post by bruce89 on 2006-06-22
[QUOTE=Virogenesis]Unaware that mono supported VB.net, no getting offended by a simple mistake.[/QUOTE]
It doesn't have a compiler for VB.NET yet AFAIK, but they are working on it on the Google SoC.

---

### Post by Kimm on 2006-06-22
[QUOTE=bruce89]It doesn't have a compiler for VB.NET yet AFAIK, but they are working on it on the Google SoC.[/QUOTE]

Huh, your kidding??
My Monodevelop can compile VB...

And I wasnt offended, I was merely making an atempt at being humorus :-P

---

### Post by bruce89 on 2006-06-22
I know this is a bit offtopic (I'll add more to this post in a minute), but if you lookup mono in google, you get disease info.  It reminds me of Polyp audio renaming itself, after people complained that polyp sounds like a disease.
It seems you are right about the VB.net compiler, I thought it wasn't complete - [http://www.mono-project.com/VisualBasic.NET_support](http://www.mono-project.com/VisualBasic.NET_support).

---

### Post by ronoc on 2006-08-19
guys i am trying to use gnome with ruby. I have installed the ruby bindings
but when i try to use 'require gnome2' in my rubyscripts I get a load error on that line

---

