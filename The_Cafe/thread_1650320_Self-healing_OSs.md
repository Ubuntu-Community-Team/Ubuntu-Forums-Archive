---
title: "Self-healing OSs"
date: 2010-12-21
forum: The Cafe
---

### Post by Lynx Phoenix on 2010-12-21
I was web-crawling around and cought a wiff of the kernel debate thing. i saw some mention of MINIX being self-healing, so i ran a search to see what it is.

didnt get a clear explanation but i didnt search a lot because one of first things that caught my eye was that windows 7 is lauded as the "first self-healing OS". now, have i understood things the wrong way, or is this simply a big lie? from that quick search i can say that at least MINIX and Solaris 10 were mentioned to have this feature (though i could be wrong). is MS still doing the classic propaganda attack?

---

### Post by zekopeko on 2010-12-21
> **Lynx Phoenix said:**
> I was web-crawling around and cought a wiff of the kernel debate thing. i saw some mention of MINIX being self-healing, so i ran a search to see what it is.

didnt get a clear explanation but i didnt search a lot because one of first things that caught my eye was that windows 7 is lauded as the "first self-healing OS". now, have i understood things the wrong way, or is this simply a big lie? from that quick search i can say that at least MINIX and Solaris 10 were mentioned to have this feature (though i could be wrong). is M$ still doing the classic propaganda attack?

I don't know if they are the first but I'm pretty sure they are the best one in this regard. They have a lot of tools to fix common problem people might have or to troubleshoot the problem and present you with a solution or at least a starting point.

---

### Post by sydbat on 2010-12-21
> **Lynx Phoenix said:**
> I was web-crawling around and cought a wiff of the kernel debate thing. i saw some mention of MINIX being self-healing, so i ran a search to see what it is.

didnt get a clear explanation but i didnt search a lot because one of first things that caught my eye was that windows 7 is lauded as the "first self-healing OS". now, have i understood things the wrong way, or is this simply a big lie? from that quick search i can say that at least MINIX and Solaris 10 were mentioned to have this feature (though i could be wrong). is M$ still doing the classic propaganda attack?I'd like to know what MS stands for?

> **zekopeko said:**
> I don't know if they are the first but **I'm pretty sure they are the best one in this regard**. They have a lot of tools to fix common problem people might have or to troubleshoot the problem and present you with a solution or at least a starting point.I highly doubt this. Please come over and tell my neighbour, who tried to use that feature in their (relatively) new 7 laptop and could no longer boot, that this is the case. Yes, they did bring it back under warranty for "repairs", which ended up being a full reinstall.

---

### Post by betrunkenaffe on 2010-12-21
> **sydbat said:**
> Yes, they did bring it back under warranty for "repairs", which ended up being a full reinstall.


See, all healed

---

### Post by zekopeko on 2010-12-21
> **sydbat said:**
> I highly doubt this. Please come over and tell my neighbour, who tried to use that feature in their (relatively) new 7 laptop and could no longer boot, that this is the case. Yes, they did bring it back under warranty for "repairs", which ended up being a full reinstall.

I never said it doesn't have bugs.

---

### Post by madjr on 2010-12-23
linux will get this feature with Btrfs

---

### Post by ki4jgt on 2010-12-23
> **betrunkenaffe said:**
> See, all healed

ChromeOS was rumored to get this feature. At least that's what they said on one of their videos on Youtube. Basically, the OS would take care of itself while the user was free to do what ever they wanted.

---

### Post by julio_cortez on 2010-12-23
> **sydbat said:**
> I highly doubt this. Please come over and tell my neighbour, who tried to use that feature in their (relatively) new 7 laptop and could no longer bootStartup repair can't ever solve the problem, it just gives chances to. But of course the result may vary depending on the conditions.

> **sydbat said:**
> which ended up being a full reinstall.Well, if everything suggested by startup repair fails, I don't see many other better alternatives to be honest.

---

### Post by Grenage on 2010-12-23
For an average user (read: nobody here), I think that Windows 7 probably is the OS that best allows one to get their machine running again.

---

### Post by julio_cortez on 2010-12-23
> **Grenage said:**
> For an average user (read: nobody here), I think that Windows 7 probably is the OS that best allows one to get their machine running again.Well, not only average users have been helped..
I've to say that I've been saved a couple of times by startup repair myself (some system files borked by some Starforce driver while trying to install an old game) so it IS useful.

Anyway I agree, it helps the standard user a lot as it's, all in all, just a *wizard*. I like the idea, they tried to keep it simple yet kind of powerful.

---

### Post by alaukikyo on 2010-12-23
> **sydbat said:**
> I'd like to know what M$ stands for?


microsoft started off by selling basic interpreter and basic had a $ after the variable and only 2 characters were allowed so m$ tries to mock that up.

---

### Post by Lynx Phoenix on 2010-12-23
> **alaukikyo said:**
> microsoft started off by selling basic interpreter and basic had a $ after the variable and only 2 characters were allowed so m$ tries to mock that up.

was going to make a variable name joke myself, but tbh, i intended it as a plain old dollar sign :P

> **julio_cortez said:**
> Well, not only average users have been helped..
I've to say that I've been saved a couple of times by startup repair  myself (some system files borked by some Starforce driver while trying  to install an old game) so it IS useful.


-_- starforce... those guys should be outlawed. 

however, i feel this is getting a bit off topic - for the sake of getting back on rails, could anyone define the "self-healing" aspect of an OS or provide a link? wikipedia isnt helpful on this and search engines dont seem to provide much help either, seems to be a rarely discussed topic.

---

### Post by Spice Weasel on 2010-12-23
> **alaukikyo said:**
> microsoft started off by selling basic interpreter and basic had a $ after the variable and only 2 characters were allowed so m$ tries to mock that up.

Nah, that was just a problem with Microsoft's version. It was very limited.

---

### Post by Termana on 2010-12-23
Everyone is way off base with what exactly self-healing is.

Self-healing is where the OS constantly looks for and detects a fault with one of the components of the OS, for example drivers, certain microkernel servers in MINIX's case, and then it will fix that fault.

For example - MINIX is able to completely replace the file system driver daemon on the fly.

Edit: Windows 7 seems to do some of this (eg. you can crash it's graphics stack and it is able to reload it), but it definitely wasn't the first to my knowledge.

---

### Post by koenn on 2010-12-23
> **Lynx Phoenix said:**
> I was web-crawling around and cought a wiff of the kernel debate thing. i saw some mention of MINIX being self-healing, so i ran a search to see what it is.

didnt get a clear explanation but i didnt search a lot because one of first things that caught my eye was that windows 7 is lauded as the "first self-healing OS". now, have i understood things the wrong way, or is this simply a big lie? from that quick search i can say that at least MINIX and Solaris 10 were mentioned to have this feature (though i could be wrong). is MS still doing the classic propaganda attack?

Well, I did a quick search myself. 

Microsoft doesn't say much more than "Windows Vista detects and resolves many known problems, and if it can't fix itself, it'll give you tools" --  [http://www.microsoft.com/india/windows/windows-vista/features/self-healing.aspx](http://www.microsoft.com/india/windows/windows-vista/features/self-healing.aspx)
"detects and resolves many known problems" is the definition of a self-healing OS, so apparently, yes, Win7 is self healing. (Solaris indeed makes similar claims)


[This]("http://forum.thewindowsclub.com/windows-7-management-support/29293-windows-7-only-self-healing-operating-system.html"), otoh, claims "Windows 7is the only &#8220;Self-Healing&#8221; Operating System" and supports that claim by listing a couple of tools for system restore and/or repair (including "a command prompt"  and "reinstall").
This microsoft most valued professional seems to have missed to point  that "self-healing" means that the OS  recovers from faults (in stead of just halt/crash), and does that "transparently"  -- the moment the user needs to use these tools, the self-healing has already failed.

So yes, there seems to be quite a bit of fanboism / marketing speak /  lies there.


This looks a bit more serious : 
[http://choices.cs.uiuc.edu/selfhealing.pdf](http://choices.cs.uiuc.edu/selfhealing.pdf)

---

### Post by madjr on 2010-12-23
my gnome panel applets self heal (or at least ask me to) ;)

---

