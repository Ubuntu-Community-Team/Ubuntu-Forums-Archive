---
title: "VB.net development under linux with mono?"
date: 2010-10-21
forum: The Cafe
---

### Post by kio_http on 2010-10-21
I heard about mono having a vb.net compiler? Is it possible to develop in vb.net under linux?

About mono: I don't find it a very good thing. It is not about licensing issues (I am quite sure there are no licensing issues), but about the way apps run; they tend to reproduce similar issues of Windows itself and it is not a very practicle solution performance wise.

However if it is possible to have a vb.net IDE under linux; it does not need to be able to compile; I can compile on windows.

---

### Post by samalex on 2010-10-21
Mono and DotNet on Windows have different GUI frameworks so you can't build a GUI interface in say Mono and have it compile in Visual Studio.  The underlying code should be portable between Mono and Visual Studio, but not the GUI forms.

As for developing VB.Net on Mono, I'm working with some C# projects now in Mono, but I haven't done any VB.Net on Mono and don't plan to either.  There's just much more support for C# out there than VB.Net, and even in the Microsoft side of things it seems most people are starting to move towards C# and dropping VB.Net.  Not to say VB is deprecated, but I don't see it being in as high demand as C# now or in the future.

For licensing though, there still are unanswered questions in that arena.  Microsoft has indemnified users to some degree, but honestly there's nothing stopping MS from pulling the lawyer card for anyone using Mono who steps on their toes.  Unlikely, but still possible.

Sam

---

### Post by forrestcupp on 2010-10-21
[Here's the page](http://www.mono-project.com/VisualBasic.NET_support) you need to visit to learn about VB.net in mono.

> **samalex said:**
> 
For licensing though, there still are unanswered questions in that arena.  Microsoft has indemnified users to some degree, but honestly there's nothing stopping MS from pulling the lawyer card for anyone using Mono who steps on their toes.  Unlikely, but still possible.

Sam

I thought they got that worked out when they came out with their own implementation of Windows.Forms.

---

### Post by user1397 on 2010-10-21
i thought visual basic used the .net framework which basically is written in C#...or was i informed terribly wrong :(

---

### Post by samalex on 2010-10-21
> **ubuntuman001 said:**
> i thought visual basic used the .net framework which basically is written in C#...or was i informed terribly wrong :(

The last time I heard Windows.Forms in Mono was iffy at best, but it looks like my knowledge is outdated -- [http://mono-project.com/Gui_Toolkits](http://mono-project.com/Gui_Toolkits) .  They've now got Windows.Forms working in Mono, but I'd bet there'd still be some caveats when porting a GUI app written in Visual Studio to Mono.  I need to do some testing with this.

One question though is can MonoDevelop do Windows.Forms?  I know it does GTK#, but to build Windows.Forms apps would you need something like Visual Studio?

Sam

---

### Post by Dragonbite on 2010-10-21
VB.net works mostly in Mono, but like Kubuntu gets less "luv'n" than Ubuntu for development time, so VB.Net gets less than C# in Mono.  I think the compiler was first developed in C#, but now is in VB.NET. Either way, I don't know if that matters much so long as it compiles correctly.

Monodevelop does allow programming in VB.NET, but does not include the integrated GUI builder (Stetic? gtk#) that C# enjoys.

For VB.NET, Visual Studio is still the best environment, but once it is developed and compiled it should run in Mono with few, if any, issues.

Mono also includes the Moma application that scans a solution for Mono compatibility and lists exactly what is not compatible.

There is a mailing list for VB.NET programming (or is it their "forum"?  something strange like that).

Otherwise, Mono is more C# orientated, but then again Microsoft is slowly turning more C#-focused over VB.NET!

---

### Post by directhex on 2010-10-21
There is a VB.NET compiler and runtime in Ubuntu, written in VB.NET, and compiled with itself. You can use it to write VB.NET or run apps.

As Dragonbite points out, it's treated as something of a second-class citizen within the Mono project - which is why it has no GUI designer, for example. But you can write a GUI app by hand using System.Windows.Forms or GTK#, in VB.NET, and run the app fine unmodified on Windows, Ubuntu and Mac OS X. And vice versa, of course - you can write a proper well-written VB.NET app in Visual Studio.NET, and run it on Ubuntu or Mac OS X with Mono. The key is good, cross-platform-friendly code (e.g. no p/invoking user32.dll, or hard-coding case-insensitive file paths)

---

### Post by phrostbyte on 2010-10-21
I would say, just use C#. VB.NET support is quite behind in Mono!

Also, we have a better forum full of smart people here for these kinds of questions: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by forrestcupp on 2010-10-21
> **phrostbyte said:**
> I would say, just use C#. VB.NET support is quite behind in Mono!

Or if you absolutely don't want to take the time to learn C#, just use the real .NET in Windows. ;)

---

### Post by phrostbyte on 2010-10-21
> **forrestcupp said:**
> Or if you absolutely don't want to take the time to learn C#, just use the real .NET in Windows. ;)

I didn't want to give him bad advice. :)

---

### Post by kio_http on 2010-10-22
> **forrestcupp said:**
> Or if you absolutely don't want to take the time to learn C#, just use the real .NET in Windows. ;)

I was asking this for a project that has to be VB.Net. It is not necessary to be able to develop it under linux but I was wondering if it were possible as that would facilitate the task. Any way, I see no big use for C# and GTK for me as I am more in favor of C++ QT combination as I am more KDE oriented.

What exactly are the differences in C# and C++?

---

### Post by RiceMonster on 2010-10-22
> **kio_http said:**
> What exactly are the differences in C# and C++?

They're vastly different. It's not a short answer, but think of C# as more similar to Java (though for .NET) and C++ as C with object orientation.

---

### Post by endotherm on 2010-10-22
> **kio_http said:**
> I was asking this for a project that has to be VB.Net. It is not necessary to be able to develop it under linux but I was wondering if it were possible as that would facilitate the task. Any way, I see no big use for C# and GTK for me as I am more in favor of C++ QT combination as I am more KDE oriented.

What exactly are the differences in C# and C++?

in the end, your life will be much easier using the right tools and environment for your task. you'll likely spend lots of time just getting things to work right, and cross platform code takes a lot more work than just selecting a cross-platform langague/runtime.

C# is a very high level langague, that is "compiled" to a virtual assembler langague. at runtime, this virtual assembler code is JIT compiled and executed as native machine code. like Java, this means that the code can be compiled for any system for which there is a runtime. think of C# and java and Python all being on about the same level. 
Java and C# in particular are focused on business programming needs.

C++ however is a high level langague which is compiled straight to machine code, so it is tied to the hardware platform of the box on which it was compiled.

---

