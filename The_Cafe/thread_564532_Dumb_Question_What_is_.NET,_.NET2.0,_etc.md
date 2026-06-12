---
title: "Dumb Question: What is .NET, .NET2.0, etc?"
date: 2007-10-01
forum: The Cafe
---

### Post by GSF1200S on 2007-10-01
Well, im new to the whole web culture, which im getting into mainly as advice from these forums.

I understand that .NET is a MS born internet framework, but what exactly does it do? Whats its benefits, and why is such a push being made towards it?

Since im starting my journey on html, xhtml, css, xml and javascript (web design), I would also be curious to know if I would  need Windows to do .NET design. Does windows need to be around? 

Whats different with .NET2.0, 3.0, etc? 

The most important question: I know that mono can run .NET applications. Does .NET2.0, 3.0, etc apps run through mono on Linux? **Does .NET, especially the later renditions, hurt the position of Linux in general?** It seems to me its another attempt by MS to choke Linux from its ascent to the top...

I really dont know.. maybe someone out there could shed some light on some answers?

---

### Post by ynnhoj on 2007-10-01
.net isn't necessarily just an internet framework; you can write local applications in vb, c#, j#, c++, etc. using .net.  of course, you can also use .net classes as the backbone of an asp.net web application..  read about the common language interface to get a better idea of how it all works.

it looks like .net 3.0 has some new components and an updated version of the common language runtime, among other additions/changes.

all the mono-related stuff i can't speak about, as i've never had any experience with mono.  just google it.  i'm sure there's a wealth of information out there.

---

### Post by blastus on 2007-10-01
[quote=GSF1200S]I understand that .NET is a MS born internet framework, but what exactly does it do?[/quote]

.NET is for developing desktop and web-based software that will run on Windows machines. .NET supports multiple languages on one platform, Windows. In contrast Java supports one language on multiple platforms.

[quote=GSF1200S]Whats its benefits, and why is such a push being made towards it?[/quote]

.NET provides a unifying platform for Windows development. The benefits are managed code that runs in a virtual machine. Less code is required and development is easier and faster. In the future Microsoft will do away with the Windows API such that any application written for Windows (or any application written for any other Microsoft product) will need to be written in .NET.

[quote=GSF1200S]Since im starting my journey on html, xhtml, css, xml and javascript (web design), I would also be curious to know if I would need Windows to do .NET design. Does windows need to be around?[/quote]

If you want to do .NET you need Windows. You don't need Windows if you don't need to do .NET.

[quote=GSF1200S]The most important question: I know that mono can run .NET applications. Does .NET2.0, 3.0, etc apps run through mono on Linux? Does .NET, especially the later renditions, hurt the position of Linux in general? It seems to me its another attempt by MS to choke Linux from its ascent to the top...[/quote]

Mono will never be supported by Microsoft so no business will ever run their applications on Mono. Microsoft does not and will never support .NET on any operating system other than Windows.

---

### Post by igknighted on 2007-10-01
> **blastus said:**
> Mono will never be supported by Microsoft so no business will ever run their applications on Mono. Microsoft does not and will never support .NET on any operating system other than Windows.

That's not entirely true... microsoft actively helped the moonlight/silverlight team, which is a mono project.  Whether they support it as a whole .net replacement project remains to be seen, but to say they will never support when they already have is just foolish.

---

### Post by blastus on 2007-10-01
[quote=igknighted]That's not entirely true... microsoft actively helped the moonlight/silverlight team, which is a mono project.[/quote]

Microsoft gave Novell access to test suites, Silverlight specifications, and binary-only video codecs. I would hardly call providing information that really should be publicly accessible (we are talking about web technologies after all) anyway is *active* participation. There's a significant difference between this and officially supporting it.

[quote=igknighted]Whether they support it as a whole .net replacement project remains to be seen[/quote]

No it doesn't. Microsoft does not support any implementation of the .NET platform on any operating system except Windows.

[quote=igknighted],but to say they will never support when they already have is just foolish.[/quote]

Microsoft cannot possibly support Silverlight on Linux since Silverlight is based on .NET and Microsoft does not support any implementation of .NET on any operating system except Windows.

---

### Post by GSF1200S on 2007-10-01
Is this Windows only position detrimental to Linux? I mean, is this something that will hurt Linux as it evolves?

---

### Post by Polygon on 2007-10-01
> **blastus said:**
> 
Microsoft cannot possibly support Silverlight on Linux since Silverlight is based on .NET and Microsoft does not support any implementation of .NET on any operating system except Windows.

might want to take a look at the moonlight project

[http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

---

### Post by phrostbyte on 2007-10-01
.NET is basically Microsoft's answer to Java. I think it's better designed. Unfortunately, one of the biggest "flaws" in .NET is it's tied down to one platform, namely Microsoft's platform. (Which makes little sense, why bother with all the overhead of a virtual machine when you tie it down to one platform). 

There is a project, called "Mono" which is trying to make an open source implementation of .NET. It's a bit different then Wine however since .NET is partly an open standard, so there is less "reverse engineering" involved. The project while rather new can run a very large number of .NET applications.

[http://www.mono-project.org/](http://www.mono-project.org/)

Mostly, .NET *is* a threat to Linux because it's another Microsoft attempt at "locking" developers to their platform. However, with projects like Mono around, the amount of lock in they can accomplish is minimal.

---

