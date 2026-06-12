---
title: "Philosophical question about wine"
date: 2009-05-17
forum: Wine
---

### Post by tazdzioch on 2009-05-17
Hi there everyone!

I know that very often it is very cool and useful to run windows aplications on linux, but isn't wine our biggest threat in some way? 

What if windows-environement viruses, spyware could run under wine?

---

### Post by NightMKoder on 2009-05-17
It's not that simple. For one, wine doesn't allow start-up applications, so spyware/malware is limited to what the user does in one session. Furthermore, since wine runs in user mode, viruses/malware can do very limited things (touch your files, but your system will still run).

In a way, the only way that wine can cause damage to your computer is if you try to run shady windows programs. It's nearly impossible for someone to start wine from, say, within firefox.

---

### Post by asdfoo on 2009-05-17
It all comes down to the point that Ubuntu isn't any more secure than Windows is, it's about being a smart user.  The user is the biggest threat.

---

### Post by rolandixor on 2009-05-18
Bwahaha!

---

### Post by butnmashr on 2009-05-18
It's possible to compute using 100% open source software and have a complete experience of it. But I like Counterstrike. The slim chance that Ubuntu would make my old rambus winME junkhunk run it was the main reason that I gave Ubuntu a chance in the first place.

There seems to be a place for free software and a place for nonfree software. Operating systems, desktops, web browsers, all the standard stuff should definetly be accessible to everyone regardles of finance, ability, or fluency. But video games, AutoCAD, all that medical software and stuff... if important programs that are frequently used by professionals (there are professional gamers) can't integrate flawlessly (or at least better than windoze) into Linux then they won't use it. They'll keep using their C:/ drives and their Start buttons. I think more people would use Linux if they knew they could use their expensive designer software on it.

And that expensive designer software isn't going anywhere. The $4,000 you drop on AutoCAD goes into someones pocket, and being as how they would like to keep having that sweet sweet scrill a flowin', they're going to make extra sure you can design the football stadium with the absolute least chance of riot induced bleacher collapse.

I spent $30 on CS 1.6 years ago, and I don't think that decisions like that are destructive to the movement. You need to make a living somehow, and if you can provide me with a ton of entertainment at a reasonable price I'm totally willing to help you pay the mortgage. A lot of folks are willing to sell software for the price of their name being recognized and to contribute to society. Thus, open source. There will probably always be both in one way or another.

To me, Ubuntu represents the ultimate in transparent interaction with computer technology. Open source and proprietary, across platforms from the Atari up to Vista. Doesn't seem to matter what it is... some one has, is, or will figure out how to make it work. And it will work. Way better. No more windows. Ever.

Beyond that, Ubuntu wouldn't be as big as it is now even without some money behind it. Shuttleworth has toured space, after all...

---

### Post by lightstream on 2009-05-18
> **butnmashr said:**
> Shuttleworth has toured space, after all...

I don't think he's the only one buddy ......

---

### Post by cogadh on 2009-05-18
Linux is about offering people a choice. The fact that some people choose to use closed source software or run Windows software does not make that choice bad (no matter what Richard Stallman says), it just means that they have chosen something that others might not. If Ubuntu (or any other distro) has the ability give people more choices through the use of Wine, then that is only a good thing for the future of Linux as it makes the OS more appealing to a wider range of users. A greater market share for Linux, regardless of how it is achieved, is only a good thing for the future development of the OS and applications for it.

---

### Post by u235sentinel on 2009-05-18
> **tazdzioch said:**
> Hi there everyone!

I know that very often it is very cool and useful to run windows aplications on linux, but isn't wine our biggest threat in some way? 

What if windows-environement viruses, spyware could run under wine?

I heard that WINE runs windows viri quite well so I tell my friends just don't pirate and you'll generally be fine ;-)

Ok that's a bit over simplistic.  But overall I'm thinking things are better running under WINE as other's have mentioned several thoughts already.

Plus when browsing the internet, I have things like noscript and flashblock running with firefox anyway.  So there are some measures put into place to protect yourself.

You can never be 100% protected IMO.  You can only reduce the risks.

---

### Post by butnmashr on 2009-05-20
> **lightstream said:**
> I don't think he's the only one buddy ......

Oh thanks. Had no idea. I bet I could learn more about that kind of stuff if I had the internet.

Would you have been more satisfied if I said he was the second? And there have been six.

---

### Post by rcayea on 2009-05-20
I agree with posters who speak of choice. For me, WINE is another choice and that is fine. Take it or leave it. No need to trash it.

---

### Post by Tibuda on 2009-05-20
I like what Shuttleworth said in the [OpenWeek]("https://wiki.ubuntu.com/MeetingLogs/openweekJaunty/AskMark").
> (12:24:03 PM) jcastro: <rabbit251> jcastro: QUESTION: Do you see Wine (and Windows-compatibilty in general) or native Linux ports as the more important ingredient in the success of Ubuntu, or do they each play an important role?
(12:24:18 PM) sabdfl: they both play an important role
(12:24:30 PM) sabdfl: but fundamentally, the free software ecosystem needs to thrive on its own rules
(12:24:41 PM) sabdfl: it is *different* to the proprietary software universe
(12:24:54 PM) sabdfl: we need to make a success of our own platform on our own terms
(12:25:08 PM) sabdfl: **if Linux is just another way to run Windows apps, we can't win**
(12:25:13 PM) sabdfl: OS/2 tried that
(12:25:15 PM) sabdfl: next?


---

### Post by alex.rayu on 2009-05-21
Yeah, that was some good talk - I wish I could tell who was who there - their nicks dont tell much.

---

### Post by Tibuda on 2009-05-21
> **alex.rayu said:**
> Yeah, that was some good talk - I wish I could tell who was who there - their nicks dont tell much.

[sabdfl = Mark Shuttleworth]("https://launchpad.net/~sabdfl"), but I don't know what sabdfl means.

---

### Post by oldrocker99 on 2009-05-21
From the Official Wine Wiki FAQ:

NEVER run Wine as root! Doing so gives Windows programs (and viruses) full access to your computer and every piece of media attached to it. Running with sudo also has these same risks but with the added bonus of breaking the permission on the user's ~/.wine folder in the process. If you have run Wine with sudo you need to fix the permission errors as described in the next question, and then run winecfg to set Wine up again. You should always run Wine as the normal user you use to login.

For Linux Systems, all ideas that Wine needs root can be solved through Posix Capabilities ([http://www.linuxjournal.com/article/5737](http://www.linuxjournal.com/article/5737)) or Posix File Capabilities ([http://www.ibm.com/developerworks/library/l-posixcap.html](http://www.ibm.com/developerworks/library/l-posixcap.html)) or correcting other security settings.

As far as Windows programs are concerned, you are running with administrator privileges. If an application complains about a lack of administrator privileges, file a bug; running Wine as root probably won't help.

---

### Post by YokoZar on 2009-05-21
If Wine didn't work then none of those former Windows users running those viruses you're worried about would be Ubuntu users in the first place.  I'd say we're better off with 100 million new users using 95% free apps, even if a million of them turn out to get just as many viruses in Ubuntu as they did Windows.

---

### Post by TheHolm on 2009-05-23
Just do not make Wine too good. Otherwise Linux can repeat OS/2.
OS/2 can run Win 3.1 application much better than Windows itself. As result there are very limited number of Native OS/2 application. They just not need, win 3.1 versions works just fine.

---

