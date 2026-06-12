---
title: "Five Features Operating Systems Should Have"
date: 2005-03-17
forum: The Cafe
---

### Post by bored2k on 2005-03-17
[http://frogboy.joeuser.com/index.asp?c=1&AID=66798](http://frogboy.joeuser.com/index.asp?c=1&AID=66798)

What do you guys think ?
Page is crappy, but i got the text right here :
>  	
Five Features Operating Systems Should Have
Getting things to the next level...

By Brad Wardell
Posted Monday, February 28, 2005 on Skinning the frog
Discussion: OS Wars

My friend Eugenia over at OSNews.com was lamenting how boring operating systems have become. And I agree. How far we've fallen from the exciting times of 1991 when pre-emptive multitasking, protected applications, flat memory, and object oriented interfaces were about to be delivered to the masses.

Since then, improvements to operating systems have been incremental. Or in some cases, we've actually regressed (largely thanks to jerks taking advantage of open systems to create viruses and spyware).  IBM's OS/2 was well on its way to providing an OS in which users from around the world could seamlessly integrate new functionality into the operating system via SOM and OpenDoc.  Of course, had that occurred, it would have been the mother of all opportunities for spyware vendors and the creeps who make viruses. The 90s could be looked back upon as a time of naiveté and idealism. It was in that environment that ActiveX and VB Script and Internet Explorer Outlook Express were designed that we now rue because of the exploitative nature of malicious people.

And so in the past few years the two major OS vendors, Microsoft and Apple have largely taken on the role of tossing in features into the OS that third parties had already provided or that the other had managed to come up with on its own. And then after that the Linux vendors then try to mimic that (there, I've offended all 3 camps!).

With MacOS X, Apple finally managed to put together a stable operating system with preemptive multitasking and memory protection. The first release was slow and buggy but subsequent versions got better and better. MacOS X Tiger looks to be a refinement on what has come before along with Apple's usual innovative twists on existing concepts (ex: Dashboard).  Apple's "innovation" with MacOS X has been very very gradual --  a far cry from the heady days of "Pink", "Taligent", and "OpenDoc". This is particularly true when one considers its ancestor, NeXTStep was released in the late 80s.

Meanwhile, Microsoft has contented itself with lifting shareware programs and throwing it into the OS.  WinZip sure looks popular, let's put ZIP into the OS.  Hey, AOL is annoying us, let's tweak them by making our media player skinnable and tossing that in.  Hey, let's put in a basic movie editing program too.  Ooh, WindowBlinds sure looks nice, let's make our OS have its own skin too.  Meanwhile, in areas that there's little third party innovation (or at least competition) things haven't progressed very much.  Outlook Express hasn't changed much since 1998. Internet Explorer is still roughly the same today as it was in 1998.  Now before any Windows zealots get on me, I'm not saying that users haven't benefited some from Microsoft tossing in home grown (or contracted out) copies of third party programs. I like being able to work with ZIP files "natively".  But bundling more content with the OS is not the same as innovation. To be fair, Microsoft's Longhorn project is very ambitious and Avalon promises to, at the very least, pave the way to really control how large things appear on our monitors without giving up resolution.

Yea yea, talk is cheap. So what should the OS vendors be doing?  I can think of five things that operating system developers should look at having part of the OS.

[b]
#1 Seamless Distributed Computing
[/b]
In an age of gigabit internal networks, it is striking that I can't simply tell my operating system that I have "access" to Machine A, B, and C on my network and to use their memory, their CPU, and other resources to ensure that my local computer remains always responsive.  Instead Windows users are quietly bumping up against the "User Handle" limit (which most people don't even know about yet, they just discover their programs start to crash) of Windows XP.  So if I felt my machine was getting slow, I'd just bump up more machines on my LAN to use or toss another machine under my desk or even (gasp) throw some tasks at my home machine via the Internet (where the OS would be smart enough on what tasks it farmed out based on the connection speed). This sort of thing should be built into the OS, today.

[b]
#2 Seamless Distributed File System Databases
[/b]
To be fair to Microsoft, WinFS has the potential to become this but it keeps being delayed. I should be able to create "cabinets" on my desktop (or anywhere else) in which I set a few parameters and from then on, files show up there as if they were any other folder.  I should be able to set the scope of my cabinets -- local, network, worldwide.  The physical location of files should be irrelevant. I should be able to arrange things however I want without it affecting anything.  Instead, move something from c: \program files\ and you're asking for trouble.  Why? I should be able to organize things however I want without it affecting anything.  This should be part of the operating system, today.
[b]
#3 Global User Management
[/b]
When I activate Windows (or MacOS) I should be given a unique account global account where my preferences and other key settings are stored along with any data I would choose to store there for an additional fee. There should be a Bwardell.Microsoft.net (or Bwardell.Mac.com).  I shouldn't be forced to use it so that the privacy nuts are kept happy. But if I choose to use it, all my preferences, email, favorites, and other system specific "stuff" could be kept there and synchronized and accessible from any machine I'm on.  Moreover, it would also act as a re-director between machines. If Machine A has my spread sheets and I'm on Machine B then I would be able to get to those files through my Microsoft.net account re-directing my files from Machine A to Machine B. The system would need to be plugin-able so that Microsoft could avoid any DOJ issues. So a Yahoo or Google or even Apple could provide alternative Network cordinators (i.e. use Bwardell.Google.net instead of Microsoft.net). (DWL: I'm not talking about a domain controller here, we're talking about a global system that's seamlessly part of the OS).
[b]
#4 Universal environments
[/b]
Following #3, I should be able to have a universal user environment. If I go to a public machine, type in my UserID and password, it should then be able to pull my environment from Bwardell.Microsoft.net so that my program settings, etc. are there.  If the local machine is missing a program, it would simply be grayed out. But if the local machine does have it, then I would be able to launch it from the normal place in the Start menu.  All my files would be accessible here through the re-direction of Microsoft.net. What machine my files are physically located on should be immaterial as long as as they are safe and secure and backed up (all handled by the OS without me messing with it).

[b]
#5 Component Based operating systems
[/b]
Part of the problem with Windows and MacOS is that the OS vendors make it hard for third parties to enhance the OS with their own code.  Rather than worrying about locking everyone out for security reasons, they should come up with a secure way for legitimate software developers to be able to enhance or replace components of the OS.  For instance, in Windows I  get 5 choices on how to view a folder (icon, tile, thumbnails, details, and list).  Third parties should be able to extend this (I can think of a dozen ways I might want to display data in a folder).  There should be APIs so that developers can replace major or minor components to the OS. The web browser engine, parts of the shell, the display rendering engine, the built in search, and dozens of other things.  The OS should be broken down into parts that the OS vendor bundles their parts and third parties can try to innovate those areas. In that way, everyone wins, including the OS vendor (particularly closed-source vendors). Windows has "API hooking" but what we need is something more robust and secure to make use of that is well documented and accessible to developers.

The closed source vendors should be looking at Linux. It has managed to keep up on a tiny fraction of the resources. It does this through open-source.  Anyone can update any part of the OS and if it's a good thing, it can be put as part of a distribution. If the major closed-source OS vendors started providing documented ways for third parties to easily extend virtually any part of the OS without a lot of pain, they could harness their considerable third party developer base.  OS/2 was working in this direction with SOM where OS features could be "inherited" by app developers, extended and then updated.  Object Desktop on OS/2 was coded entirely by a single individual because he could inherit the base features of the OS and then start from there. And then other developers could go from there. (DWL: I know COM can do some of this but it's not what I am talking about, if you've done any serious OS extension development, COM doesn't apply here much).

...

Now you might be thinking, "Well if you think these ideas are so great, why don't you do them?"  The answer is, only the OS vendor can, as a practical matter, do this.  If a third party makes these things and it's successful, it's only a matter of time (probably one version) before the OS vendor puts in one of these on their own, wiping out the "low hanging fruit" part of the market.  As soon as some third party, for instance, put out a really good distributed computing product that "did it right" and started to make good business that targets consumers (DWL: Armtech is not a consumer product and isn't what I'm talking about), you could be assured that the next version of the OS would have some basic implementation of this put in.  And the OS vendor's fans would chime in, "That should be part of the OS anyway!"  In short, there's no business case for a third party to invest the money to develop these things because the pay-off isn't there.

But if these features were part of the OS, you could imagine how it might lead to dramatic changes in the way we use and think about computers. And to add to that, imagine the kinds of additional innovations that would present themselves if these things were already taken as a given?


---

### Post by telmo on 2005-03-17
I think the page cannot be displayed! LOL
I don't want that feature on my pc! thx anyway.. :)

---

### Post by bored2k on 2005-03-17
Stupid joeuser.com is more unstable than Win ME :@

this sucks ... :-# :-$

---

### Post by telmo on 2005-03-17
=d>

---

### Post by bored2k on 2005-03-17
[QUOTE=telmo]=d>[/QUOTE]
 Added the text now [thanks google cache!] .

---

### Post by telmo on 2005-03-17
nice work.
oh boy... that's big... i'm sleepy... 8-[

---

### Post by bored2k on 2005-03-17
[QUOTE=telmo]nice work.
oh boy... that's big... i'm sleepy... 8-[[/QUOTE]
 lol

---

