---
title: "New Crossplatform Virus"
date: 2006-04-09
forum: The Cafe
---

### Post by OffHand on 2006-04-09
I was surfing the web and came across this article.
It seems there's a new virus that can infect both Windows and Linux machines.
Maybe a virusscanner isn't such a bad idea after all.

[http://www.viruslist.com/en/weblog](http://www.viruslist.com/en/weblog)

---

### Post by bjweeks on 2006-04-09
It's a POC not a virus.

---

### Post by OffHand on 2006-04-09
The virus doesn’t have any practical application - it’s classic Proof of Concept code, written to show that it is possible to create a cross platform virus.
However, our experience shows that once proof of concept code is released, virus writers are usually quick to take the code, and adapt it for their own use.

---

### Post by bjweeks on 2006-04-09
It's wrote in assembly so it will be a little harder this time also there are many issues with the virus.

[http://computerworld.com/securitytopics/security/virus/story/0,10801,110330,00.html](http://computerworld.com/securitytopics/security/virus/story/0,10801,110330,00.html)

---

### Post by Kimm on 2006-04-09
In assembly?
How does that work? Does it recompile before it spreads to a new OS... or is it completely OS independant?? :confused:

---

### Post by bjweeks on 2006-04-09
[QUOTE=Kimm]In assembly?
How does that work? Does it recompile before it spreads to a new OS... or is it completely OS independant?? :confused:[/QUOTE]

If I understand right assembly will run in any OS but assembly only works on 1 processer type. So it would be a "x86" virus not a windows virus.

---

### Post by MakubeX on 2006-04-09
[QUOTE=bjweeks]If I understand right assembly will run in any OS but assembly only works on 1 processer type. So it would be a "x86" virus not a windows virus.[/QUOTE]

So should be we afraid of this? Does this mean a 'red alert' on the Linux platform?

---

### Post by bjweeks on 2006-04-09
[QUOTE=MakubeX]So should be we afraid of this? Does this mean a 'red alert' on the Linux platform?[/QUOTE]

No.... Not at all.

It isn't even a virus and it still has to be run by a user or exploit a hole when it becomes a virus.

---

### Post by GeneralZod on 2006-04-09
[QUOTE=MakubeX]Does this mean a 'red alert' on the Linux platform?[/QUOTE]

Only if there's always been one before :).  Linux viruses have been around for ages, so this announcement doesn't really change anything from the point of view of Linux security.

---

### Post by NeghVar on 2006-04-09
This has already been posted 2 seperate times within the past few days...

---

### Post by OffHand on 2006-04-09
[QUOTE=NeghVar]This has already been posted 2 seperate times within the past few days...[/QUOTE]
Lighten up

---

### Post by bjweeks on 2006-04-09
[QUOTE=NeghVar]This has already been posted 2 seperate times within the past few days...[/QUOTE]

You mean that thread that fot taken over by a spammer?

---

### Post by briancurtin on 2006-04-09
[QUOTE=subsonic_shadow]Lighten up[/QUOTE]
search

---

### Post by OffHand on 2006-04-10
[QUOTE=briancurtin]search[/QUOTE]
Sorry for replying again but I just have to. This is the Ubuntu Cafe part of the forums. Not technical support or whatever. It's to chat about Ubuntu/Linux related stuff as far as I know. I don't feel the need to search the whole forum before posting something interesting I found, in the Cafe part of the forum. Too bad if it has been posted before.... No harm done. If you don't like it just move along and stop whining. Why are you so uptight? Maybe it's time to get some fresh air...

---

### Post by mdsmedia on 2006-04-10
I guess the question is, still, WHY don't we have to worry about this or any other virus written for Linux? I don't feel threatened, but is that a false sense of security?

---

### Post by nocturn on 2006-04-10
If I read the article correct, it can't infect system binaries on Linux (only the directory of the user that executed it).  Which is one of the points that make it much harder to write *NIX malware over win32.

---

### Post by nocturn on 2006-04-10
[QUOTE=mdsmedia]I guess the question is, still, WHY don't we have to worry about this or any other virus written for Linux? I don't feel threatened, but is that a false sense of security?[/QUOTE]

Because it doesn't work.  It's not even a virus by the real definition because it cannot automatically spread.

The point remains that it needs to get root on Linux to actually infect and spread, and even then, spreading is not so easy.

---

### Post by angkor on 2006-04-10
[QUOTE=nocturn]The point remains that it needs to get root on Linux to actually infect and spread, and even then, spreading is not so easy.[/QUOTE]

Yes, plus the fact that for example an Ubuntu user can choose to only install software from a trusted source (the repositories). It's highly unlikely, not to say impossible, to get malicious code in there.

Still, it's been known *nix is not invulnerable to virus attacks, so it's just common sense to be careful.

---

