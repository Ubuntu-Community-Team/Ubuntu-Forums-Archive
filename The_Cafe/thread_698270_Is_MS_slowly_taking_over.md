---
title: "Is MS slowly taking over?"
date: 2008-02-16
forum: The Cafe
---

### Post by quinnten83 on 2008-02-16
sure, 
[it]("http://boycottnovell.com/2008/02/15/mono-contamination-in-ubuntu/") has a high degree of conspiracy theory, but the idea is scary nonetheless.

---

### Post by gsmanners on 2008-02-16
Well, let's see what this does...

```
$ grep-available -F Depends -ri '.*libmono.*' -nds Package | awk '{l1=$0;getline;l2=$0;getline; print l1," - ", l2}' | sort
f-spot  -  personal photo management application
libart2.0-cil  -  CLI binding for libart 2.3
libgconf2.0-cil  -  CLI binding for GConf 2.16
libgecko2.0-cil  -  CLI binding for the GtkMozEmbed library, unstable version
libglade2.0-cil  -  CLI binding for the Glade libraries 2.6
libglib2.0-cil  -  CLI binding for the GLib utility library 2.12
libgmime2.2-cil  -  CLI binding for the MIME library, unstable version
libgnome2.0-cil  -  CLI binding for Gnome 2.16
libgnome-vfs2.0-cil  -  CLI binding for GnomeVFS 2.16
libgtk2.0-cil  -  CLI binding for the GTK+ toolkit 2.10
libgtkhtml2.0-cil  -  CLI binding for GtkHTML 3.8
libmono1.0-cil  -  Mono libraries (1.0)
libmono2.0-cil  -  Mono libraries (2.0)
libmono-accessibility2.0-cil  -  Mono Accessibility library
libmono-cairo1.0-cil  -  Mono Cairo library
libmono-data-tds1.0-cil  -  Mono Data library
libmono-data-tds2.0-cil  -  Mono Data Library
libmono-microsoft-build2.0-cil  -  Mono Microsoft.Build libraries
libmono-peapi1.0-cil  -  Mono PEAPI library
libmono-peapi2.0-cil  -  Mono PEAPI library
libmono-relaxng1.0-cil  -  Mono Relaxng library
libmono-security1.0-cil  -  Mono Security library
libmono-security2.0-cil  -  Mono Security library
libmono-sharpzip0.84-cil  -  Mono SharpZipLib library
libmono-sharpzip2.84-cil  -  Mono SharpZipLib library
libmono-sqlite2.0-cil  -  Mono Sqlite library
libmono-system1.0-cil  -  Mono System libraries (1.0)
libmono-system2.0-cil  -  Mono System libraries (2.0)
libmono-system-data1.0-cil  -  Mono System.Data library
libmono-system-data2.0-cil  -  Mono System.Data Library
libmono-system-runtime1.0-cil  -  Mono System.Runtime library
libmono-system-web1.0-cil  -  Mono System.Web library
libmono-system-web2.0-cil  -  Mono System.Web Library
libmono-winforms2.0-cil  -  Mono System.Windows.Forms library
libndesk-dbus1.0-cil  -  CLI implementation of D-Bus
libndesk-dbus-glib1.0-cil  -  CLI implementation of D-Bus (GLib mainloop integra
tion)
librsvg2.0-cil  -  CLI binding for RSVG 2.0
monodoc-base  -  shared MonoDoc binaries
monodoc-browser  -  MonoDoc GTK+ based viewer
mono-gac  -  Mono GAC tool
mono-gmcs  -  Mono C# 2.0 compiler
mono-mcs  -  Mono C# compiler
mono-utils  -  Mono utilities
tomboy  -  desktop note taking program using Wiki style links
```

---

### Post by peabody on 2008-02-16
This has been a subject of some controversy for a while, I'm not too worried about it myself.  Open source communities have often voted with their feet over fishy things in the past, if you don't believe me lookup the story of Corel Linux.

---

### Post by forrestcupp on 2008-02-16
Could we make this a poll for how long we think it will take this thread to be moved to Recurring Discussions?

**Mono is not Microsoft**.  It's not Microsoft any more than Wine is.  Don't you remember in the beginning of the Mono days, how they were forced by Microsoft to stop emulating their patented System.Windows.Forms namespace and classes?  If this were really an evil plot by MS, they would allow us to use Forms.

Mono is an implementation of the .NET framework to try to get some cross-compatibility.  Whether people like it or not, .NET is the way the world is going.  So what's wrong with shooting for cross-compatibility?  Why shouldn't people be able to program in C# at work *and* at home on their Linux machine?  If you've ever actually programmed in C# and .NET, you would recognize the benefits of it.

My main concerns are about Mono's bugginess compared to .NET, not some conspiracy theory.

---

### Post by kripkenstein on 2008-02-16
That's a pretty far-fetched conspiracy theory. Their 'example' is Cheese, a new GNOME app, which doesn't use Mono. It just recommends F-Spot (which does use Mono) for some optional export functionality. That is hardly 'sneaking in Mono' without people noticing.

If someone is concerned about Microsoft patents in Mono, it's very easy to not use Mono. There isn't a single important GTK app that relies on Mono at this point, and might never be. So it's hardly reason to consider other desktop environments like KDE, which has its own potential legal problems anyhow (especially since the acquisition of Trolltech by Nokia).

I'm not too worried about Mono myself. What **would** worry me is if there wasn't a replacement for something critical in our FOSS desktops, just because I am afraid about any single point of failure. That's why it's good we have GNOME and KDE, Python and Java as alternative modern platforms vs. Mono, and so forth.

That said, I do recognize the importance of people like the boycottnovell.com guys. We need extremists to remind us of important things, even when they personally take them much too far. With them on the watch, we won't be caught offguard from some patent trickery later on.

---

### Post by leftorvo on 2008-02-16
i don't care at all about patents. mono is open source, i don't really see the problem.

---

### Post by SomeGuyDude on 2008-02-16
I heard Microsoft actually owns Linux and is using it to lure in anti-MS users by giving them a cheaper alternative to buying a Mac, then slowly over time... they will be assimilated like all the others.

I also heard they have a Fortress of Doom in the works.

---

### Post by blastus on 2008-02-16
FOSS/Linux can't be stopped no matter what Microsoft does. Think about it. People all over the world are planting FOSS seeds and watching them grow; witnessing the conversions from Windows to Linux and MS Office to OpenOffice or alternatives. NO-ONE is trying to convert anyone from Linux to Windows or OpenOffice.org to MS Office. No-one except Microsoft. 

I'm working on my second Linux conversion as we speak. The first conversion was successful; except for the printer which we knew ahead of time wouldn't work but they wanted to buy a new printer anyway. They were very satisfied and liked Ubuntu much better than Windows 2000 (which constantly crashed for them.) I setup everything for them.

My second conversion will be someone who uses XP and actually has a license for Vista but doesn't want to go with Vista :) None of the software they run requires Windows anymore as last year or the year before I converted them to FOSS equivalents. Before I got involved their XP machine was infested with malware everywhere. Hint...computer problems are a breeding ground for Linux conversions!

My biggest FOSS seed came about through an instructor at a local college. I converted their household from MS Office to OpenOffice.org. Because the instructor likes OpenOffice.org a lot, I heard he now takes every opportunity to tell his students about OpenOffice.org and has a lot of conversions under his belt. :)

---

### Post by KiwiNZ on 2008-02-16
Title of thread corrected

---

### Post by phrostbyte on 2008-02-16
> **forrestcupp said:**
>   Don't you remember in the beginning of the Mono days, how they were forced by Microsoft to stop emulating their patented System.Windows.Forms namespace and classes?  If this were really an evil plot by MS, they would allow us to use Forms.

No, no I don't. Mono [supports WinForms]("http://www.mono-project.com/WinForms") and as far as I am aware, Microsoft never threatened the Mono project.

---

### Post by LookTJ on 2008-02-16
No, I think FOSS is taking over slowly. :P Microsoft can't stop FOSS projects.

---

### Post by 23meg on 2008-02-16
The last time I saw so much fact twisting and misinformation together was the last time I read an "article" on this same site.

---

### Post by forrestcupp on 2008-02-16
> **phrostbyte said:**
> No, no I don't. Mono [supports WinForms]("http://www.mono-project.com/WinForms") and as far as I am aware, Microsoft never threatened the Mono project.

Well, I'm actually glad to find that out.  I must have gotten some misinformation. 

I used to program in C# with .NET and I loved it.  I've never used Mono; I've just read some stuff about it.  I mainly use C++ with wxWidgets now.  C# is great for getting nice things done quickly.  But now I'm liking being able to compile to native binaries and not depend on a middleman framework.

> **KiwiNZ said:**
> Title of thread corrected
Thank you.

---

### Post by justin whitaker on 2008-02-16
> **23meg said:**
> The last time I saw so much fact twisting and misinformation together was the last time I read an "article" on this same site.

Between the Boycott Novell guy and Beranger, we really have our own negativity factory in the open source community. I wonder which one is on Redmond's payroll. :)

---

### Post by quinnten83 on 2008-02-23
well,
I am not a coder and I haven't been around F/LOSS long enough to know that this was a recurring thread. 
But I can understand MS wanting to do everything in their power to discourage the FLOSS comm. 
So this did sounded plausible.

---

### Post by sayakb on 2008-02-23
Don't think so.. After Vista being a huge failure, M$ is losing its blind following..

---

### Post by Daveski on 2008-02-23
> **forrestcupp said:**
> I used to program in C# with .NET and I loved it.  I've never used Mono; I've just read some stuff about it.

+1 for C#. Perhaps the best language Microsoft has EVER got out the door. What I find interesting is that C# and to some degree the .NET framework is SUPPOSED to be platform independent like Java. The whole system is designed to be a layer than can sit on virtually any platform and provide a 'virtual machine' which should follow the Write Once, Run Anywhere philosophy. It is not really a surprise that Microsoft has not invested anything in actually getting this stuff out to other platforms, so in a way I am glad the Mono project has made this a reality.

---

### Post by cardinals_fan on 2008-02-23
> **justin whitaker said:**
> Between the Boycott Novell guy and Beranger, we really have our own negativity factory in the open source community. I wonder which one is on Redmond's payroll. :)

I absolutely agree - Boycott Novell is a profound waste.  And Beranger is loud and obnoxious.

---

### Post by kripkenstein on 2008-02-24
> **Daveski said:**
> +1 for C#. Perhaps the best language Microsoft has EVER got out the door. 
If you like C#, perhaps you'll be interested in [Vala]("http://live.gnome.org/Vala"). Vala is a language similar to C#, that is compiled into plain C with GObject (so it's about as fast as C). Vala is still a work in progress, but you can already do quite a lot with it.

For those that care, Vala has nothing to do with .Net, Mono, Microsoft, etc.

---

### Post by kooolrock on 2008-02-24
> **quinnten83 said:**
> sure, 
[it]("http://boycottnovell.com/2008/02/15/mono-contamination-in-ubuntu/") has a high degree of conspiracy theory, but the idea is scary nonetheless.
just see this image. imagine for a moment, that u r the penguin. it shows what u can do!!!!
[IMG]http://www.whylinuxisbetter.net/Images/business_news.png[/IMG]

---

### Post by Daveski on 2008-02-24
> **kripkenstein said:**
> If you like C#, perhaps you'll be interested in [Vala]("http://live.gnome.org/Vala"). Vala is a language similar to C#, that is compiled into plain C with GObject (so it's about as fast as C). Vala is still a work in progress, but you can already do quite a lot with it..

Ooh, thanks. I'm off to have a good read on that site.

---

