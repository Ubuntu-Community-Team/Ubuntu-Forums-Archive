---
title: "Linux - which toolkit?"
date: 2008-07-14
forum: The Cafe
---

### Post by Tom Mann on 2008-07-14
Hi Guys,

I have looked around the great wide web looking for a Linux replacement to a program called [Ascent Capture]("http://www.kofax.com"), which I've failed to find.

So... I'm going to attempt to build a replacement. Part of the code will be an executable and the rest will be web based.

However I've never programmed in Linux before, and unsure which toolkit is easier (Qt/Gtk+)

WITHOUT (excuse me) flame wars... can any programmers out there tell me of their experiences with the toolkits, and which they prefer?

Finally if anyone is interested in the idea please let me know as I am brainstorming this now...

Cheers,
Tom

---

### Post by saulgoode on 2008-07-14
Well, there are no C bindings for Qt, so if you are planning on coding in C then GTK is your friend.

---

### Post by sassur on 2008-07-14
I should say it depends on what programming language you know. 
If you know C++ then Qt is probably the toolkit to chose, if you know C then Gtk+. If you know C# take a look at [Mono]("http://www.mono-project.com/"), it has bindings for Gtk+.

---

### Post by red_Marvin on 2008-07-14
I've only used GTK+ myself but I found it quite nice, it also has python bindings (but I expect Qt does too) if you want to use that.

---

### Post by KingTermite on 2008-07-14
> **sassur said:**
> if You Know C++ Then Qt Is Probably The Toolkit To Chose, If You Know C Then Gtk+.
+1

---

### Post by KingTermite on 2008-07-14
> **Tom Mann said:**
> I have looked around the great wide web looking for a Linux replacement to a program called [Ascent Capture]("http://www.kofax.com"), which I've failed to find.
Just took a quick peek at that software. It appears to be something that scans documents in to an electronic format (pdf maybe??). Is that all it does? If so, can't SANE (or XSANE) do that?

---

### Post by KingTermite on 2008-07-14
BTW, whatever direction you take, you may need more details about some file types. Just in case, let me pass this website along to you as I'm sure it would help. It archives file type specs of lots of file types.

[http://www.wotsit.org/](http://www.wotsit.org/)

---

### Post by Canis familiaris on 2008-07-14
> **KingTermite said:**
> BTW, whatever direction you take, you may need more details about some file types. Just in case, let me pass this website along to you as I'm sure it would help. It archives file type specs of lots of file types.

[http://www.wotsit.org/](http://www.wotsit.org/)

Kooka does it too.

---

### Post by Tom Mann on 2008-07-14
Hi guys,

thanks for all the comments :)

Kooka is similar to Ascent Capture, though it does miss the workflow a bit - I will take a closer look at it before I continue though.

I've just come across the nastiest patent that may kill this - courtesy of Kofax, it pretty much says if you store information about a scanned page in a database it violates their patent... I will have to look into it.

And I'm going to try a bit more KDevelop/Anjuta/Eclipse testing before I pick an IDE (which will dictate language then toolkit) and go from there methinks...

Thanks again guys+gals :)

---

### Post by Daveski on 2008-07-15
> **Tom Mann said:**
> 
I've just come across the nastiest patent that may kill this - courtesy of Kofax, it pretty much says if you store information about a scanned page in a database it violates their patent... I will have to look into it

I hope it is a little more specific than that. Patents seem to have been handed out like sweeties in some countries...

---

### Post by jespdj on 2008-07-15
GTK+ is the native GUI toolkit of the GNOME desktop environment.
Qt is the native GUI toolkit of the KDE desktop environment.

So, choose GTK+ if you're using GNOME, and use Qt if you're using KDE.

---

