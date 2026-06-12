---
title: "if something is Mac compatible, is it more likely to work in Linux?"
date: 2012-01-07
forum: The Cafe
---

### Post by u-noob-tu on 2012-01-07
I was just thinking about this the other day; if some hardware or software is Mac compatible, is it more likely to work well in Linux? Since MacOS and Linux are both *nix based, i would think that would be the case. can anyone elaborate?

---

### Post by Bachstelze on 2012-01-07
Hardware: No.
Software: If it is POSIX-compatible it will work on anything POSIX, so Linux and others. Otherwise the chances are very thin.

*EDIT:* Also for software we are talking at the source level. An OS X binary will definitely not work on anything other than OS X.

---

### Post by u-noob-tu on 2012-01-07
> **Bachstelze said:**
> Hardware: No.
Software: If it is POSIX-compatible it will work on anything POSIX, so Linux and others. Otherwise the chances are very thin.

*EDIT:* Also for software we are talking at the source level. An OS X binary will definitely not work on anything other than OS X.
Is there a lot of POSIX compliant software available?

---

### Post by Bachstelze on 2012-01-07
Most "Linux" software is in fact POSIX software and will run on anything POSIX, so in particular on OS X. The converse is not true, however, because most OS X software relies on things Apple has added on top of the POSIX base of OS X, and that are specific to it. Such software will of course not run on anything else.

So to answer your question, no, the typical OS X program will not run on Linux. If it were POSIX-compatible, it would be distributed as such, not as an OS X program.

---

### Post by Paqman on 2012-01-07
> **u-noob-tu said:**
> Since MacOS and Linux are both *nix based, i would think that would be the case.

Not really. OS X uses a lot of different stuff on top of its BSD-based kernel (the whole display manager is different, for example).

So it's a different kernel with a load of different componants and a few that are the same. You'll find some familiar things on a Mac (eg: CUPS, a BASH shell) but that doesn't mean you can chop and change between them.

---

### Post by jjex22 on 2012-01-07
In a real world practical situation - no. As a mac user I have virtually no carry over from OSX to linux or BSD in terms of support - as the others have said the other way round is a different matter, but since you're really talking about printers and osx programs like iLife, just no. 


With my last mac I realised one day that I was running a windows version of itunes on wine on Linux on a mac machine with leopard installed... a mixture of linux love and itunes tying itself to the environment it's in!

for example I have a very stroppy wifi printer that I can't get any drivers to work with on linux or pc-bsd - I print by emailing to it, on OSX it has a driver from Kodak that works just fine, but of course this driver won't work on linux or freebsd.

I think as Linux users it's easy to forget that whilst linux stuff works across linux distros as a standard, this is not the same in the BSD world - freebsd, netbsd, openbsd - their binaries are not compatible, and OSX is proprietary - it also uses a hybrid kernel. Apple also deliberately make it easier to get linux and BSD stuff running by including the X11 app.

I also kind of wish we had a "Cocoa Is Definately  Emulated Reliably", or Cider, that could run osx apps ;) but I don't have the faintest Idea how and the demand just isn't really there as far as I know at the moment - becuase Apple doesn't make it's software for windows, most people that want to use it already have a mac to use it on.

---

### Post by dmoconnell on 2012-01-07
tbh I hate OSX (as well as the 3 I's) I used in OSX (in middle school) and I hated it. out of the ~30 macbooks that our class was using, 10 wouldn't start, 5 wouldn't log in,and  5 wouldn't start the software we needed to use and to top it off none of the teachers knew how to fix it :/ being the only available nerd, I was able to fix enough of them that we could continue (3 of the macs that couldn't start had dead batteries and and broken cords and the 5 that wouldn't start the program had bonked installs)
on the matter of windows, I would routinely do a factory restore (not quite a flatting and reinstall, but does similar thing) every 6 months or so (liked doing it in between semesters (then I don't have to restore everything, just pics, music and programs) 
Linux I don't need to do that, it just works, the best way to sum up linux is "It doesn't get happy, it doesn't get sad, it just runs programs" 
That's my 2 cents
Dm

---

### Post by MG&amp;TL on 2012-01-07
> **dmoconnell said:**
> 
Linux I don't need to do that, it just works, the best way to sum up linux is "It doesn't get happy, it doesn't get sad, it just runs programs" 
That's my 2 cents
Dm

My Linux gets happy if you tickle it in the right places. nice new conky or desktop background makes it purr nicely. :)

I see your point though.

On topic: Well, if your program just reads/writes files, then you're good, 'cos they're in roughly the same places (i.e "/" not C:/. If not, then you're not so good.

---

### Post by jjex22 on 2012-01-07
> **dmoconnell said:**
> tbh I hate OSX (as well as the 3 I's) I used in OSX (in middle school) and I hated it. out of the ~30 macbooks that our class was using, 10 wouldn't start, 5 wouldn't log in,and  5 wouldn't start the software we needed to use and to top it off none of the teachers knew how to fix it :/ being the only available nerd, I was able to fix enough of them that we could continue (3 of the macs that couldn't start had dead batteries and and broken cords and the 5 that wouldn't start the program had bonked installs)
on the matter of windows, I would routinely do a factory restore (not quite a flatting and reinstall, but does similar thing) every 6 months or so (liked doing it in between semesters (then I don't have to restore everything, just pics, music and programs) 
Linux I don't need to do that, it just works, the best way to sum up linux is "It doesn't get happy, it doesn't get sad, it just runs programs" 
That's my 2 cents
Dm

I suspect the relevant info here is "in middle school" - this is like my Windows 7 install - it's been installed for coming up 2 years, with no problems - i had to remove IE9 and reinstall it once but that's about it, but my brother in law and step sister seem to have this problem where "it just goes wrong every 6 months" am I the lucky one? the exception? it seems unlikely - they fiddle!

I have tiger leopard and lion running and I only have to reinstall/reset/time machine them when I mess something up usually adding distro's to my drives! OSX also benifits from the OS manufacturer and Hardware manufacturer being the same - I've only had one update that went wrong for me that I can think of - not the case for Ubuntu. Ubuntu is also linux - so you can configure it a lot more than OSX... stick it in a middle school full of experimental teens and give them root account access... I can almost guarantee the machines would end up in worse shape!

---

### Post by Link1275 on 2012-01-07
> **jjex22 said:**
> I suspect the relevant info here is "in middle school" - this is like my Windows 7 install - it's been installed for coming up 2 years, with no problems - i had to remove IE9 and reinstall it once but that's about it, but my brother in law and step sister seem to have this problem where "it just goes wrong every 6 months" am I the lucky one? the exception? it seems unlikely - they fiddle!

I have tiger leopard and lion running and I only have to reinstall/reset/time machine them when I mess something up usually adding distro's to my drives! OSX also benifits from the OS manufacturer and Hardware manufacturer being the same - I've only had one update that went wrong for me that I can think of - not the case for Ubuntu. Ubuntu is also linux - so you can configure it a lot more than OSX... stick it in a middle school full of experimental teens and give them root account access... I can almost guarantee the machines would end up in worse shape!
That's why you don't give them root access by password protecting the root account and giving them a student account(the teacher would have to have, and probably would have the password of course).

---

### Post by jjex22 on 2012-01-07
> **Link1275 said:**
> That's why you don't give them root access by password protecting the root account and giving them a student account(the teacher would have to have, and probably would have the password of course).

Quite, same goes for Windows, OSX, pretty much any multi user OS. I was just trying to highlight that the problems most likely arose from poorly set up accounts and/or week passwords than the OS - i'd like to think that ICT teachers know more now than when I was at school; the admin account password for our apple newton emates was username- teacher, password - teacher1, and everyone in the class new it!

I didn't mean it as a slur on Linux - it's just that old spiderman thing... something about power and responsability ;)

---

### Post by Lucradia on 2012-01-08
Just remember that OSX =/= OS Classic (OS9 and previous). This means games that have yet to be ported to full OSX (IE: Bolo or Escape Velocity) are not probably going to work with other UNIX Systems.

That said, OSX is based on UNIX, and UNIX is not Linux. Similarly, BSD is not Linux nor UNIX.

However, all of them "Stem" from UNIX, so did DOS and OS/2. However, it should be noted that, while DOS shares a lot of similarities to UNIX, they are not based on each other (As all Linux people seem to say, even though I have my doubts), they were even built at the same time.

---

### Post by Bachstelze on 2012-01-08
> **Lucradia said:**
> 
That said, OSX is based on UNIX, and UNIX is not Linux. Similarly, BSD is not Linux nor UNIX.

Define "UNIX".

*EDIT:* OS X is based on Mach and BSD. Mach is defintely not UNIX, so if you do not consider BSD to be UNIX either, how can OS X be based on UNIX?

> However, all of them "Stem" from UNIX, so did DOS.

No, DOS has nothing in common with UNIX (whatever you mean by that) besides being command-driven.

---

### Post by aysiu on 2012-01-08
I use Mac, Ubuntu, and Windows.

Generally speaking, I've found that for hardware if it's compatible with Mac, it's also compatible with Linux. The one exception might be certain printers. Yes, Mac uses CUPS and so does Linux, but sometimes there are proprietary drivers for certain printers available for Mac and not for Linux.

For software, Mac and Windows have far more in common than Mac and Linux. Adobe Creative Suite? Mac and Windows. Netflix streaming? Mac and Windows. Microsoft Office? Mac and Windows. iTunes? Mac and Windows.

In fact, for software, it's better to see if something is Windows-compatible because sometimes you can run Windows software in Linux using Wine.

---

### Post by dpny on 2012-01-08
> **Lucradia said:**
> That said, OSX is based on UNIX, and UNIX is not Linux. Similarly, BSD is not Linux nor UNIX.

OS X is Mach kernel + BSD + Apple's stuff. BSD is most definitely Unix.

> However, all of them "Stem" from UNIX, so did DOS and OS/2.

DOS and OS/2 have nothing to do with Unix whatsoever. DOS is based on CP/M. OS/2 was new from the ground up.

The first version of DOS was 1981. This history of Unix can be traced to the late '60s.

---

### Post by Lucradia on 2012-01-09
> **dpny said:**
> The first version of DOS was 1981. This history of Unix can be traced to the late '60s.

Glad someone didn't read wikipedia ;) (DOS origins don't state the years it first started on Wikipedia.)

---

### Post by dpny on 2012-01-09
> **Lucradia said:**
> Glad someone didn't read wikipedia ;) (DOS origins don't state the years it first started on Wikipedia.)

Huh? I said DOS was inspired by CP/M, which it was, and the first version of DOS was '81, which it was. What do you mean?

---

### Post by mips on 2012-01-09
Never mind.

---

### Post by szymon_g on 2012-01-09
> **Bachstelze said:**
> 
Software: If it is POSIX-compatible it will work on anything POSIX, so Linux and others.

Linux isn't POSIX-compatible

> **Bachstelze said:**
> 
EDIT: OS X is based on Mach and BSD. Mach is defintely not UNIX, so if you do not consider BSD to be UNIX either, how can OS X be based on UNIX?

... and yet MacOSX is a Unix operating system- it complies to Singl Unix specifications (and again- Linux isn't :P)

> **Bachstelze said:**
> 
If it were POSIX-compatible, it would be distributed as such, not as an OS X program.

... unless it's multiplatform (like most of programs you can find in repositories).

---

### Post by Bachstelze on 2012-01-10
> **szymon_g said:**
> Linux isn't POSIX-compatible

It's close enough for any reasonable person.

---

### Post by DoubleClicker on 2012-01-10
Getting back to the OP's question. 

As far as hardware goes, I'ts been my experience that Mac OSX compatible hardware is more compatible with Linux, than non-MacOSX compatible hardware.  But it really has nothing to do with any similarities with the 2 OS's.  

Being Mac compatible, is an indicator that the hardware manufacturers recognize that MS Windows is not the only platform they need to be concerned with, and so they are more likely to  do to the effort to be Linux compatible.   Companies that don't support  Mac OSX, are more likely to have a "Windows only" corporate mentality, and thus won't take the effort to facilitate LInux compatibility.  

Only in the server market, are you likely to find manufacturers that care more about compatibility with  Linux, than Mac OSX.

---

### Post by aysiu on 2012-01-10
Generally speaking, I've found what DoubleClicker says to be the case. If a company says it's compatible with Windows only, that generally means they've included some kind of proprietary firmware or software that you need to run the device instead of complying to any kind of universal standards (just plug and play USB).

---

