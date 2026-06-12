---
title: "What's the diff between Win95 and Win98/ME/2K/XP/Vista"
date: 2008-11-04
forum: Windows
---

### Post by HungryMan on 2008-11-04
Let me get one point straight, I do not mean the difference in aesthetics. Many software/drivers/hardware have the very common phrase:
For Windows 98/NT/ME/2000/XP/Vista

What is the difference with them that makes programs written for 98 binary compatible with the others?

On a side note, why is CABAL Online only for XP and Vista? What is the difference between XP/Vista and 98/NT/ME/2K?

---

### Post by scragar on 2008-11-04
If I'm not mistaken 95 was still a 16bit OS at the core, rather than the entirely 32 bit arch of later releases.

---

### Post by Antman on 2008-11-04
If I recall correctly, Win95,98,ME were all layers built ontop of the [MS-DOS Operating system]("http://en.wikipedia.org/wiki/MS-DOS"). NT,XP,VISTA are built ontop of the [NT system]("http://en.wikipedia.org/wiki/Windows_NT").

---

### Post by Newuser1111 on 2008-11-04
> **Antman said:**
> If I recall correctly, Win95,98,ME were all layers built ontop of the [MS-DOS Operating system]("http://en.wikipedia.org/wiki/MS-DOS"). NT,XP,VISTA are built ontop of the [NT system]("http://en.wikipedia.org/wiki/Windows_NT"). I think Windows 2000 (2K) is also NT.

---

### Post by Antman on 2008-11-04
> **Newuser1111 said:**
> I think Windows 2000 (2K) is also NT.Yes, forgot that one. :oops:

---

### Post by SunnyRabbiera on 2008-11-04
Right, windows 95, 98 and ME are all based on DOS
with 2000, XP and Vista all based on NT.
Also there were many revisions between versions, 95 was more fine tuned for the older 16bit systems that were on the way out at the time of 98.
98 had improved hardware detection, improved stability (even with the infamous BSOD video 98 was far more stable for me)
But ME, it was more of a downgrade... it was VERY unstable, bluescreened every time you sneezed (and yes I had that happen to me) and it ran like molasses.
2000 was the first NT version of windows targeted at the home/desktop user, it was perhaps the most stable windows I have ever had (only one bluescreen but thank goodness it was not a BSOD) it also had one heck of a security model and was very popular at the office (I really miss windows 2000 sometimes)
XP was Microsofts big desktop boost system, built mainly for ease of use and ease of functionality XP was the second best in the NT line.
However XP security wise is a joke, with IE tied right into the kernel, with the system itself making people administrator by default made XP a very insecure OS.
Granted a smart user can probably make XP quite secure, with antivirus, spyware, addware and firewalls a good deal of the issues of XP can be taken care of but it needs constant maintenance.
Vista is of course the latest evolution of the NT kernel operating systems but truth be told under the hood it is still XP.
Vista is a big double edged sword, on one hand yes it has much better security tools then XP but on the other I feel it bloated and rather unusable.
I have used vista off and on and I never really liked it, Microsoft sacrificed stability for flash and that does not do well for the everyday user in my mind.
Vista actually seems to support less hardware then Ubuntu does sometimes, with XP driver no longer working in Vista good luck on it... you might have better luck hacking xorg on linux.

---

### Post by HungryMan on 2008-11-04
> **Antman said:**
> If I recall correctly, Win95,98,ME were all layers built ontop of the [MS-DOS Operating system]("http://en.wikipedia.org/wiki/MS-DOS"). NT,XP,VISTA are built ontop of the [NT system]("http://en.wikipedia.org/wiki/Windows_NT").
Reminded me that ME/2K/NT/XP/Vista don't have true DOS.
So anyway, you guys said 95-ME were built off DOS and 2K-Vista were built off NT. I could understand the 2K/XP/Vista (forgot about NT, sorry) in the OP, but why is it that software/hardware for 98 works with XP.
The reason of this thread is that I was curious if 90% of the software for future Windows will still work with 98 (or XP) as it is now.
Cuz if they kept on writing software like this, software/hardware for Windows 10 years from now might still be compatible with 98.

---

### Post by Thelasko on 2008-11-04
> **HungryMan said:**
> So anyway, you guys said 95-ME were built off DOS and 2K-Vista were built off NT. I could understand the 2K/XP/Vista (forgot about NT, sorry) in the OP, but why is it that software/hardware for 98 works with XP.

The reason software from 98 works with XP is because Microsoft designed XP that way.  They didn't want users complaining that they had to go out and buy new hardware and software so they went out of their way to make sure XP (and others) are backwards compatible.

I should add, that not all hardware and software is compatible between the 9x family and the NT family.  I ran into some issues with this when I spent the summer upgrading a company's computer system back in college.

With each new version of Windows, Microsoft drops compatibility with some of their older software.  Most people don't notice because they have long since upgraded.  Vista actually dropped quite a bit of compatibility with older software due to security concerns.

---

### Post by K.Mandla on 2008-11-04
Moved to Windows Discussions.

In my own little world, I usually assume that software checks the Windows version to be sure that people have paid their tithe to Redmond, and aren't trying to run new games on old operating systems. But that's not necessarily true. Just sometimes. :twisted:

---

### Post by Vince4Amy on 2008-11-04
NT based releases are as follows:

NT 3.x
NT 4.0
NT 5.0 (2k)
NT 5.1 (XP) (Which Is why some software specifically for XP can be forced to run on 2k)
NT 5.2 (2003, XP x64)
NT 6.0 (Vista)
NT 6.1 (2008 )

Windows 9x releases were running MS-DOS at the core. Which is why some NT Based apps won't run on 9x. Normally NT apps are compatible between NT releases but not 9x releases. Most new software is made for the NT Codebase which has functions which the 9x kernel doesn't support. NT Based releases more so from XP Onwards are usually fine at running 9x based applications. 

> In my own little world, I usually assume that software checks the Windows version to be sure that people have paid their tithe to Redmond, and aren't trying to run new games on old operating systems. But that's not necessarily true. Just sometimes.

Some software applications do this, for example you can actually install Vista SDKs on Windows 95 if you really want to. This is also how some applications for XP can be installed on 2k. Using tools to edit the MSIs to fool the installer to thinking it's on a new version of Windows.

---

### Post by HungryMan on 2008-11-05
hmm... i do remember that XP has the option to make programs "run in compatibility mode".

---

### Post by smoker on 2008-11-05
> **HungryMan said:**
> hmm... i do remember that XP has the option to make programs "run in compatibility mode".

vista also has this, though how well it works i haven't a clue!

[http://windowshelp.microsoft.com/Windows/en-US/Help/bf416877-c83f-4476-a3da-8ec98dcf5f101033.mspx](http://windowshelp.microsoft.com/Windows/en-US/Help/bf416877-c83f-4476-a3da-8ec98dcf5f101033.mspx)

---

### Post by Thelasko on 2008-11-05
> **smoker said:**
> vista also has this, though how well it works i haven't a clue!

[http://windowshelp.microsoft.com/Windows/en-US/Help/bf416877-c83f-4476-a3da-8ec98dcf5f101033.mspx](http://windowshelp.microsoft.com/Windows/en-US/Help/bf416877-c83f-4476-a3da-8ec98dcf5f101033.mspx)

In the small time I use Vista, I have found the compatibility mode to work very well.  Many people complain about software not working in Vista, but it's usually because they didn't try compatibility mode.

---

### Post by cmat on 2008-11-05
> **smoker said:**
> vista also has this, though how well it works i haven't a clue!

[http://windowshelp.microsoft.com/Windows/en-US/Help/bf416877-c83f-4476-a3da-8ec98dcf5f101033.mspx](http://windowshelp.microsoft.com/Windows/en-US/Help/bf416877-c83f-4476-a3da-8ec98dcf5f101033.mspx)

Doesn't work in all cases. Most of the time older apps don't work because MS depreciated DLLs they need to run in newer Windows versions.

---

### Post by HungryMan on 2008-11-06
like DOS games on XP :(
the glory of retro games.

---

### Post by Battie on 2008-11-07
> **K.Mandla said:**
> Moved to Windows Discussions.

In my own little world, I usually assume that software checks the Windows version to be sure that people have paid their tithe to Redmond, and aren't trying to run new games on old operating systems. But that's not necessarily true. Just sometimes. :twisted:

Heh.  I think it's just that some program developers know their application works on one OS but have not tested it on others, and would rather have it fail on installation than crap out later.  But I have a tendency, which comes back to bite me sometimes, to assume the best of people before the worst.

We have a least one such application at work that I install frequently.  It will complain that the OS is not XP.  I just copy the installation files the local machine and run setup in XP compatibility mode, and it goes just fine.

We have another app (a terribly written one IMHO, but some employees love it because its function is useful) that will not run in Vista, or even XP, unless you copy an old .ocx file into System32 and run regsvr32 on it.  Then the program works just fine.

100% success is unlikely, of course, but I've yet to run into an unsurmountable compatibility issue.

---

### Post by RoyalShrubber on 2008-11-09
> **HungryMan said:**
> Let me get one point straight, I do not mean the difference in aesthetics. Many software/drivers/hardware have the very common phrase:
For Windows 98/NT/ME/2000/XP/Vista

What is the difference with them that makes programs written for 98 binary compatible with the others?

On a side note, why is CABAL Online only for XP and Vista? What is the difference between XP/Vista and 98/NT/ME/2K?

Win32 is the interface that regular applications use in Windows. (Posix is Unix/Linux equivalent). 
Win32 is composed of many functions and these functions continue to accomplish the same work in newer versions of Windows (even if the way how this work is accomplished gets changed). 

Example:
CopyFile() function that is in win32 is available in all programs since Windows95. Windows 98,NT,2000,XP and Vista all have this function and if program calls it Windows will copy a file.
CopyFileEx() came in Windows NT 4 I think and does few things more (it informs program of progress of copy operation). So since Windows NT 4 you have available CopyFile() and CopyFileEx(). 
Since Windows 95 don't have CopyFileEx() a program that uses this function can't run on Windows 95. CopyFileTransacted() came with Vista and will work only in Vista and versions after Vista.

Every new version of Windows brings few new functions, but the old ones stay. 
In your example CABAL Online uses few functions that were not available in Windows 95/98/ME/2000 - they first came with XP, and because few people still use these old systems programmers do not feel they need to support these old systems by restricting themselves to only old functions.

Drivers are different - every few versions architecture of kernel functions change and hardware makers have to rewrite their drivers. That's why Windows 95/98 drivers won't work in XP. Windows XP and 2000 have pretty similar driver model, few drivers from XP will work even under Vista, but most will not. Good news is Vista and Windows 7 will share the same driver model, so there won't be any problem with drivers when 7 ships, in windows 7 we will just use old drivers from Vista. :)

---

### Post by RoyalShrubber on 2008-11-09
> **scragar said:**
> If I'm not mistaken 95 was still a 16bit OS at the core, rather than the entirely 32 bit arch of later releases.

Windows 95 was fully 32 bit. The difference with NT systems was that Windows 95 started with DOS that was 16 bit, but once DOS loaded Windows would change processor mode (x86 processors have this property that they can change modes dynamically) from 16-bit mode to full 32-bit mode, that you could see in other more advances systems of that time (like NT/Linux) with virtual memory and everything. 

Interesting thing - when you boot your Linux machine, did you know it first starts in 16-bit real mode and then jumps to 32-bit protected mode, just like Windows 95 used to? (except real mode part of x86/x64 Linux isn't whole OS like DOS was) :)

---

### Post by starcannon on 2008-11-10
ME was the first release utilizing virtual dos.
windows for a long time was just 3.1 being turned over and over in the compost heap.
3.1 through 98se was just rehashes of rehashes, wasn't until ME that any real change happened.
2k to present has been building on the superior NT technology.

XP was supposed to be "The Windows Experience", and was going to try selling upgrades and extras on line, a good idea, though maybe just a little bit ahead of Microsoft's market, the consumer just wasn't ready yet; I think they are softening towards the idea a bit now though.

Vista, well, its just been a wash; with one of the most turbulent releases ever, and nothing really working well until after SP1, it even made the XP release look good (and I remember it was pretty bad, indeed XP was still pretty rotten until SP2 by my standards). Anyway MS is still persuing Online riches, and I'd bet a little bit that "cloud computing" will be making its way into Vista, and if successful will probably be a big key in 7 (pure speculation on my part).

Anyway, check out the wiki for a bit more fun trivia: [http://en.wikipedia.org/wiki/Microsoft_Windows](http://en.wikipedia.org/wiki/Microsoft_Windows)

---

### Post by HungryMan on 2008-11-10
hmm... off topic:
I always thought Vista was released as a desperate attempt because Windows 7 was taking too long to complete, I was wrong. And I only noticed now, "Longhorn"?, reminds me of GNU! hahaha

---

### Post by RoyalShrubber on 2008-11-10
> **starcannon said:**
> ME was the first release utilizing virtual dos.
windows for a long time was just 3.1 being turned over and over in the compost heap.
3.1 through 98se was just rehashes of rehashes, wasn't until ME that any real change happened.
2k to present has been building on the superior NT technology.

XP was supposed to be "The Windows Experience", and was going to try selling upgrades and extras on line, a good idea, though maybe just a little bit ahead of Microsoft's market, the consumer just wasn't ready yet; I think they are softening towards the idea a bit now though.

Vista, well, its just been a wash; with one of the most turbulent releases ever, and nothing really working well until after SP1, it even made the XP release look good (and I remember it was pretty bad, indeed XP was still pretty rotten until SP2 by my standards). Anyway MS is still persuing Online riches, and I'd bet a little bit that "cloud computing" will be making its way into Vista, and if successful will probably be a big key in 7 (pure speculation on my part).

Anyway, check out the wiki for a bit more fun trivia: [http://en.wikipedia.org/wiki/Microsoft_Windows](http://en.wikipedia.org/wiki/Microsoft_Windows)

Yeah, before you enter links, why don't you maybe read them?
From Wikipedia: *Leveraging this, Windows 95 introduced Long File Names, reducing the 8.3 filename DOS environment to the role of a _boot loader_.*.
Which kinda contradicts your Win 9x being a rehash of Win 3.1..

---

