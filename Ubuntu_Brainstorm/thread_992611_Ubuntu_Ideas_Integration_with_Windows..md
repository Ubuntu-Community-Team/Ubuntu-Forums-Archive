---
title: "Ubuntu Ideas: Integration with Windows."
date: 2008-11-24
forum: Ubuntu Brainstorm
---

### Post by neogarv on 2008-11-24
Ubuntu, or any other distro for that matter, needs to seamlessly integrate with Windows. Let me elaborate on that. I mean that Ubuntu would be able to open Windows programs (without Wine or a virtual machine). It would be Windows, but Ubuntu.

Now, I know that that would be completely destroying Linux's idea. And I know it is almost impossible. But this section is about ideas, so I'm just ruminating.

In the future, I see a computer that integrates completely with anyone else's. All computers run extremely similarly, with an extreme level of an ability to customize.

I dream, OK.

---

### Post by aysiu on 2008-11-24
There are two ways to accomplish this:

1. ReactOS somehow becomes usable

2. "Cloud computing" actually comes about, so people use only "internet applications" and not applications tied to a particular operating system

---

### Post by Sorivenul on 2008-11-24
> **aysiu said:**
> 1. ReactOS somehow becomes usable

2. "Cloud computing" actually comes about, so people use only "internet applications" and not applications tied to a particular operating system

I doubt #1 will happen any time in the near future, though I could be gravely mistaken.

If #2 ever truly happens, at this moment, I'm prepared to go back to a typewriter and solar-powered calculator.

---

### Post by cdbitesky on 2008-11-25
Nothing involving windows will be seamless and making ubuntu able to open windows be able to operate windows programs without a third-party interval such as wine would make ubuntu vulnerable to similar issues to which windows already has.
    I haven't checked out cloud computer much because it sounds too much like a hackers paradise, but i hope to see something like this soon to drag more of the windows shares to Linux based OSes.

---

### Post by lisati on 2008-11-25
Ditto with the comments so far. I suspect that because the underlying APIs are different, there will need to make platform-independent applications, possibly using some kind of compatibility layer such as Wine.

---

### Post by Sorivenul on 2008-11-26
Did a bit more thinking about this.  I still don't care for the idea.
However, in some ways, [Ulteo]("http://www.ulteo.com") seems to be headed a bit this way.

---

### Post by jpeddicord on 2008-11-26
> **neogarv said:**
> In the future, I see a computer that integrates completely with anyone else's. All computers run extremely similarly, with an extreme level of an ability to customize.

Wasn't this what the UNIX ELF exec format was supposed to accomplish? I mean, nearly every operating system and device uses the ELF format except for Windows.

---

### Post by Bibek on 2008-12-01
why not just improve wine ?

---

### Post by OzzyFrank on 2008-12-03
Well, Wine could work better, but from where I am standing, it does get better all the time. Like apps I couldn't install 6 months ago I now can. But I think new Linux users should be more interested in breaking away from commercial software for the Windows world and using free software for Linux. There are only a couple of apps I run in Wine, and only a couple of apps I have to boot into Windows for (like ebay software).

If Linux could do all that is asked in the first post here, then Windows would surely be in trouble, as that would mean Ubuntu is a better Windows than Windows!!! Microsoft would then probably be forced to buy Ubuntu, hehe.

I would say that Linux being able to run many Windows apps and have no trouble accessing the files is much better than Windows' nonexistent of support for Linux apps and the filesystem.

Once you move away from that dependence on Microsoft and the world of Windows, you will often find better apps than you are used to.

As for "In the future, I see a computer that integrates completely with anyone else's"... OK, I won't ask if you're actually serious about this, because I assume you are, but for many of us that is a BAD idea... I certainly wouldn't want that! (Some of us still care about "privacy" and "security").

---

### Post by jkristheking on 2008-12-13
... ok 1st no yes use wine but why would i want ubuntu to use windows apps?
i only use wine for games.

thats like saying why dosn't osx use windows apps or linux apps? thats just the way it is

i think ubuntu should have it's own BETTER versions of windows software...wouldn't that be the best thing to do? be better?? better than osx or windowS??

---

### Post by k_aneda on 2008-12-14
I guess the real answer to the OT's idea is:  Why not add the Wine package to the default installed applications?  This way it would appear as 'out-of-the-box' to most users?

---

### Post by k_aneda on 2008-12-14
I just ran a couple of searches through Brainstorm, and the ideas have already been lodged:

[INDENT][Idea 762: Better WINE Integration]("http://brainstorm.ubuntu.com/idea/762/")
[Idea 6177: Include Wine-doors in the repositories ]("http://brainstorm.ubuntu.com/idea/6177/")
[/INDENT]

Follow the link and vote it up :)

---

### Post by Sorivenul on 2008-12-14
> **k_aneda said:**
> I guess the real answer to the OT's idea is:  Why not add the Wine package to the default installed applications?  This way it would appear as 'out-of-the-box' to most users?
Technically, this is another question, I think. ;)
I don't want Wine in my default install or to be prompted to install Wine if a Windows executable is found on my machine.  It would just add unneeded bloat to a default many already find bloated.

> **k_aneda said:**
> I just ran a couple of searches through Brainstorm, and the ideas have already been lodged:
Follow the link and vote it up :)
Linux is not Windows - see the link in my signature. If users want Windows integration it needs to be their responsibility.  Just my two cents.

Cheers!

---

### Post by neogarv on 2008-12-19
> **Bibek said:**
> why not just improve wine ?

Yeah, that's kind of what I was thinking. Improve Wine to the level where all applications seem like they were made for Ubuntu.

I did some thinking, and came to the decision of a Wine-type idea. After downloading a program, you run it in this ideal program (Let's call it ReCompiler). All the commands that the programs has to give are parsed through the ReCompiler, giving you a Linux executable.

For example, say you downloaded a Flash trial from Adobe's website. After the download completed, you'd run it through the ReCompiler. ReCompiler would run the program inside, then spit out a Linux version of Flash. It would just add to the download and install time, but wouldn't need to be interpreted again.

If built like Wine, it wouldn't compromise safety from viruses, because it'd really hard to get out of Wine's virtual C folder and into program files.

I'm only suggesting this because important programs, like Dreamweaver and Flash, do not have as great alternatives.

> **OzzyFrank said:**
>  As for "In the future, I see a computer that integrates completely with anyone else's"... OK, I won't ask if you're actually serious about this, because I assume you are, but for many of us that is a BAD idea... I certainly wouldn't want that! (Some of us still care about "privacy" and "security"). 

By integrating computers, I meant that you'd be able to share your files with whoever *you* want, not worrying if their computer supports what you're giving them. I was only saying this because, as a developer, it is time-consuming and inefficient to recompile for any other OS.

And sorry that I replied this late.

---

### Post by neogarv on 2008-12-19
> **aysiu said:**
> There are two ways to accomplish this:
2. "Cloud computing" actually comes about, so people use only "internet applications" and not applications tied to a particular operating system

This is a great solution, except the only problems I see with it are, as cdbitesky said:

> **cdbitesky said:**
> 
    I haven't checked out cloud computer much because it sounds too much like a hackers paradise...

Also, advertisements will be everywhere you look. Google is supposedly working on cloud-computing in their little basement as well. And, as we all know, Google makes almost all of its revenue from ads. I don't want an ad-ridden OS.

---

### Post by y@w on 2008-12-19
Personally, I'd rather see Linux binaries running on Windows like you can with Cygwin rather than the other way around. I guess I like my Linux/UNIX :) of course Windows Vista did change the location of user profiles to C:/Users which is slightly more "UNIXy". Now if we can just get rid of those stupid drive letters...

---

### Post by innovati on 2009-01-04
> **neogarv said:**
> I did some thinking, and came to the decision of a Wine-type idea. After downloading a program, you run it in this ideal program (Let's call it ReCompiler). All the commands that the programs has to give are parsed through the ReCompiler, giving you a Linux executable.

For example, say you downloaded a Flash trial from Adobe's website. After the download completed, you'd run it through the ReCompiler. ReCompiler would run the program inside, then spit out a Linux version of Flash. It would just add to the download and install time, but wouldn't need to be interpreted again.

If built like Wine, it wouldn't compromise safety from viruses, because it'd really hard to get out of Wine's virtual C folder and into program files.

I'm only suggesting this because important programs, like Dreamweaver and Flash, do not have as great alternatives.

This functionality, although it seems wonderful, would violate most EULA's for proprietary software, which would be the main reason people would use them.  You're not only making copies of the software, but you're running it on platforms you're not supposed to.  Who do you go to if the program doesn't work correctly?  They won't support it.

What I'd recommend instead is the improvement and funding of WINE.

---

### Post by blazemore on 2009-01-05
So what you're saying is that Ubuntu should have support for Windows apps... Without using Wine?
What's the point of that? Surely Wine would be best, since it's been around for years.
I don't think you understand the implementation issues of doing that.

The fact that Linux doesn't run Windows apps isn't an arbitrary restriction places by developers. Put an Xbox game in your Playstation... Damn those developers, why won't it play!?

I agree with Innovati though: Canonical should fund Wine and make Wine an official part of the Ubuntu project. That would be awesome.

---

### Post by smartboyathome on 2009-01-05
> **blazemore said:**
> I agree with Innovati though: Canonical should fund Wine and make Wine an official part of the Ubuntu project. That would be awesome.

I disagree about that. Canonical should fund open source projects which are alternatives to their Windows counterparts rather than funding Wine. It will be better in the long run.

---

