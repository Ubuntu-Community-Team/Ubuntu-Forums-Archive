---
title: "Linux stealing Windows Developers"
date: 2007-07-03
forum: The Cafe
---

### Post by Dragonbite on 2007-07-03
CNet (blogs) had an entry [[COLOR="Blue"]Developers cooling on Windows desktop, study finds[/COLOR]]("http://news.com.com/8301-10784_3-9739128-7.html?part=rss&subj=news&tag=2547-1_3-0-20").

> In a survey, Evans Data found that almost 65 percent of software developers are targeting some version of Windows for their applications, as opposed to nearly 75 percent last year. The research group expects the number to drop another two percent in the coming year.

The culprit? Linux. Developers are choosing to write applications for Linux desktops in almost 12 percent of cases, which is a 34 percent increase from last year. I'm not sure if they are taking into a account the number of Open Source projects that are offering Linux AND Windows/Mac? Or are they just counting the number of applications being made for Linux regarldess of redundancy like Music Players (Muine, Amarok, Banshee, Rhythmbox, Listen, etc.)

---

### Post by justin whitaker on 2007-07-03
It's a failure on the part of MSFT's Visual Studio strategy...the basic versions of Visual Studio are just not on a par with the tools available to open source developers. 

The smart thing would have been to make Visual Studio free from the beginning, say when they released XP, or Vista, making MSDN support and training. 

But Microsoft does not think that way. The NIH culture is alive and well, apparently. :p

---

### Post by cunawarit on 2007-07-03
> **justin whitaker said:**
> The smart thing would have been to make Visual Studio free from the beginning.

I agree wholeheartedly, people using VS is beneficial for MS as they get lots of people developing for Windows. And VS is really very very nice too, so I have no doubt many would opt to develop for Windows if the full version cost $0. 

What is starting to push me away from Windows development (Web) is mostly the hosting, Windows hosting is more expensive, there are less options, and some things are less manageable. I’m capable of running a Linux desktop, however, I don’t think I have the skills to run a Linux server yet... When I do, possibly whole new world of opportunities will open up :) Although, the Windows server world is getting better and better too, very excited about 2008 Server Core, and already making good use of PowerShell.

---

### Post by brim4brim on 2007-07-03
I think the visual tools are way ahead of the Linux tools.  Eclipse is the only Open Source IDE that comes close IMO.

---

### Post by Dragonbite on 2007-07-03
I wish Mono and Monodevelop was a little further along (at least for VB.NET) so I could transfer what I use and study at work to my Ubuntu box at home.

There is Visual Studio Express, which is free (but watered down some).

---

### Post by Tundro Walker on 2007-07-03
OS' used to bend over backwards to hand out development software free of charge, because more folks dev'ing for your OS meant more software for it meant more folks likely to use your OS.

MS seems to feel pretty secure in its dominance, since it's charging an arm and a leg for a useful version of VS.  I tried their free VS version before I switched to Ubuntu, and I wasn't too thrilled.  Not only was I badgered with the  authentication process, but it was a pain to use.

---

### Post by macogw on 2007-07-03
> **justin whitaker said:**
> It's a failure on the part of MSFT's Visual Studio strategy...the basic versions of Visual Studio are just not on a par with the tools available to open source developers. 

The smart thing would have been to make Visual Studio free from the beginning, say when they released XP, or Vista, making MSDN support and training. 

But Microsoft does not think that way. The NIH culture is alive and well, apparently. :p

Well yeah, programmers tend to like "tools to make tools."  In the early days of personal computers, it was all about BASIC and interpreters, because programmers wanted to have a tool for making more tools (like languages), and weren't so concerned with applications.  So now, if you want someone to develop for your stuff, make it easy on them.  If VS was free, it'd be really easy for new programmers to develop for Windows because they could get the tools to do so easily.  As it is, Eclipse is the free mammoth jack-of-all-trades IDE*, so that's what developers get, and it lets them write things that don't lock them into Windows like VS would.


* and I don't like it.  I want simple.  Vim and GCC are all I need.   None of those newfangled buttons and mice and GUIs ;)

---

### Post by macogw on 2007-07-03
> **Dragonbite said:**
> I wish Mono and Monodevelop was a little further along (at least for VB.NET) so I could transfer what I use and study at work to my Ubuntu box at home.

There is Visual Studio Express, which is free (but watered down some).

I've never used VB.NET, just VB 6 (I think it was 6), but if VB.NET is like VB 6 at all, you should be able to switch to regular BASIC without much hassle.  You won't be able to make GUIs in such a drag-n-drop way (though Glade is an OK interface designer...I actually rather miss VB's interface designer when I use Glade, but the trick is to add a "fixed positions" widget over the whole thing, then you can add parts just like on VB), but the actual coding should be very similar.

---

### Post by Dragonbite on 2007-07-04
> **Tundro Walker said:**
> Not only was I badgered with the  authentication process, but it was a pain to use.I never had any trouble with that.  Don't know if it was because I am running Windows 2000 not XP?

> **macogw said:**
> I've never used VB.NET, just VB 6 (I think it was 6), but if VB.NET is like VB 6 at all, you should be able to switch to regular BASIC without much hassle.  You won't be able to make GUIs in such a drag-n-drop way (though Glade is an OK interface designer...I actually rather miss VB's interface designer when I use Glade, but the trick is to add a "fixed positions" widget over the whole thing, then you can add parts just like on VB), but the actual coding should be very similar.VB.NET is and is not like VB6.  I used VB6 a little bit with my old company before my current company which has sent me to .NET training. VB.NET is object-oriented while VB6 is not much. Some of the syntax is different but otherwise the concept behind the structure is the same (If..Then/End If, etc.).

Now that I'm using VB.NET, I am taking some time to try and re-write my projects in C# as a means to learn the language differences. Once compiled, it doesn't matter what language it was written in for the most part, and C# is much more supported in Mono (and other locations) than VB or VB.NET. Plus, as one teacher put it, C# is made to be comfortable for Java developers in a bid to try and move from from Java to C#.

The people at [[COLOR="Blue"]NetBeans [/COLOR]]("http://www.netbeans.org/")(for Java) are sending out [[COLOR="Blue"]free CDs [/COLOR]]("http://www.netbeans.org/about/cd-form.html")with their IDE (for Windows, Mac, Solaris and Linux on 1 CD).  Of course you have to download and install JRE (Java Runtime Environment) and JDK (Java Development Kit) before you can install the IDE.  It looks like an interesting IDE with a GUI builder similar to Visual Studio.

I do like the Winforms integration in Visual Studio.  That's one thing that keeps me going back to VS.

---

