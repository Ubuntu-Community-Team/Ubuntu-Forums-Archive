---
title: "Viruses through MONO"
date: 2015-03-17
forum: Security
---

### Post by maisam2 on 2015-03-17
[COLOR=#333333][FONT=UbuntuRegular]Whole day i was reading about Viruses on Linux ( UBUNTU 14.04 LTS : my os ), so i got to this topic that viruses can effect your computer through WINE( which allows you to run windows app on linux) i understood it, but, 2 days ago i installed mono complete for C# development, and im using PINTA for small paint type things, when i went to PINTA folder, it had dll files and its launcher was in .exe format, after getting more deeper , i found out that its runned by mono, mono is running that .exe. i googled it and searched it everywhere, didnt find this topic being discussed on MONO, so i though i should ask it myself
so same question goes for mono, like wine can MONO help viruses to infect my Linux Machine ?


[/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-03-17
First, a virus that manages to get installed into Wine only affects Wine, and even if it did, there is nothing in the Linux OS that it could infect.  A Windows virus would not propagate beyond the Wine environment.  Moreover you can always blow away your Wine installation by deleting $HOME/.wine and starting over.

Mono is a [clone of Microsoft's .NET]("http://www.mono-project.com/").  If you open Pinta in Wine, I don't see how mono would play any role at all.  Mono also uses "[sandboxing](http://www.mono-project.com/docs/advanced/sandbox/)" to limit its effect on other parts of the system.

---

### Post by SeijiSensei on 2015-03-17
First, a virus that manages to get installed into Wine only affects Wine.  It doesn't propagate beyond the Wine enviroment.  Moreover you can always blow away your Wine installation by deleting $HOME/.wine and starting over.

Mono is a [clone of Microsoft's .NET]("http://www.mono-project.com/").  If you open Pinta in Wine, I don't see how mono would play any role at all.  Mono also uses a "[sandbox](http://www.mono-project.com/docs/advanced/sandbox/)" to limit its affect on other parts of the system.

If you're that worried about these issues, I'm guessing that you've spent a lot of time on Windows, but much less time on Linux.  Trust me, I've used Linux for two decades and never had any kind of malware installed on my system.

---

### Post by QIII on 2015-03-17
It is possible that an "infection" in Wine could have farther reaching effect.

The pipelite solution to Silverlight content was, and possibly still is, one of those situations.  There used to be a symbolic link from ~/.wine to one of the system subdirectories of /.  I don't remember just what it was/is.

However unlikely it may have been/may be that a process  would have appropriate rights to do anything nefarious, that is still frightening.

---

### Post by maisam2 on 2015-03-18
> **SeijiSensei said:**
> First, a virus that manages to get installed into Wine only affects Wine.  It doesn't propagate beyond the Wine enviroment.  Moreover you can always blow away your Wine installation by deleting $HOME/.wine and starting over.

Mono is a [clone of Microsoft's .NET]("http://www.mono-project.com/").  If you open Pinta in Wine, I don't see how mono would play any role at all.  Mono also uses a "[sandbox]("http://www.mono-project.com/docs/advanced/sandbox/")" to limit its affect on other parts of the system.

If you're that worried about these issues, I'm guessing that you've spent a lot of time on Windows, but much less time on Linux.  Trust me, I've used Linux for two decades and never had any kind of malware installed on my system.



thanks for your reply, yes, whole life i was under Microsoft's spell, i got sense and freed my self 10 days ago :) :p

---

### Post by maisam2 on 2015-03-19
thanks!

---

### Post by The Cog on 2015-03-19
Last time I looked, wine still mapped Z:\ to / by default, giving wine executables full user-level access to the entire system, including write access to ~/.bashrc etc.

---

### Post by HermanAB on 2015-03-19
Howdy,

There are no active viruses on Linux.  Once or twice a year, there a security scare that gets patched within a couple hours.

I have used Linux since 1996 and UNIX since 1985  and never had a virus problem.

So, relax and enjoy Linux, you don't need anti-virus anything, but don't ignore the security news completely - stay vigilant.

---

