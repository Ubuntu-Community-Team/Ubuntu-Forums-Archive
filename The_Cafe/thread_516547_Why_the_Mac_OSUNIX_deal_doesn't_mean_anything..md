---
title: "Why the Mac OS/UNIX deal doesn't mean anything."
date: 2007-08-03
forum: The Cafe
---

### Post by izanbardprince on 2007-08-03
With all the press about Mac OS now being UNIX certified, I thought I'd spell out exactly what that means for the typical Mac user.

In one word: Nothing.

In two words: Absolutely Nothing.

UNIX is not an operating system anymore, it's not any code in particular, it's a set of guidelines to guarantee interoperability with any other system that is UNIX-certified, to boil it down further, Microsoft could incorporate those guidelines into their next version of Windows, pay the money to get it reviewed, and Windows would qualify for UNIX certification.

As for the connection between OS X and Bell UNIX, they're like third cousins twice removed, OSX is based on modular chunks of FreeBSD kernel code running on top of the Mach microkernel, incidentally this allows Apple to market Mac OS as having a hybrid kernel, which in theory would have the stability of a microkernel (Mach) with the performance and features of a monolithic kernel (FreeBSD), but that doesn't help the user if the FreeBSD section crashes...."Well, I have no graphical, sound, or TCP-IP subsystems, but Mach is still up and kicking".

If you get to digging at the guts of Mac OS, or even playing around with the Terminal a bit, you'll see where it behaves similiarly to FreeBSD, but if someone wanted to run FreeBSD they would have just downloaded it, slapped it on a whitebox PC and left it at that, the point of Mac OS is to shield the average Joe from having to deal with the inner workings of a UNIX-like system, at the very top level, the operating system is 100% Apple, when a developer builds an application for Mac OS, you can't run it on other UNIX certified systems, or Linux, or BSD, or what have you, but when you design an app for a plain-jane UNIX or UNIX work-alike it will compile and run on Mac OS.

The point I'm trying to make here is that the UNIX standards that Mac OS adheres to don't mean anything unless you're a corporation that is switching over to Mac OS servers, and want to keep using "program x", and with the hardware and licensing fees being more than triple the cost of what you would get out of PC hardware and Red Hat Enterprise Linux or Sun Solaris, I don't think we're going to be seeing a stampede to Mac OS anytime soon, unless Apple graciously allows OS X to run on PC hardware or Sun SPARC.

All this means to the rest of us however, is now we'll undoubtedly be seeing Mac adverts and obnoxious fanboys jumping up and down about "UNIX this!" and "UNIX that!", where it's obvious that if you plopped them down in front of an AIX, IRIX, UnixWare, or Solaris system, who are also UNIX certified, but come with the bonus of actually working more like the traditional UNIX concept, they'd be drooling all over themselves.

---

### Post by DeadSuperHero on 2007-08-03
While it's true that it doesn't mean much for the end user, don't forget than Unix and Unix-like Operating Systems are indeed very powerful.
Actually, the irony here is amazing. Back in 1984, Apple ran an ad that had an Anti-Unix type of message in it. They fought against huge corporations.
Then came Microsoft, who challenged both of them.
And finally, Mac OSX is Apple with Unix parts, and it's preparing to take down Vista.
Oh, the irony. :)
Though, I'm seriously going to have to try OSX one of these days, to see how it measures up to Ubuntu, BSD, and all that. So long as it's more stable and better than Windows, and can run Photoshop natively.

---

### Post by igknighted on 2007-08-03
> **Mr. Psychopath said:**
> While it's true that it doesn't mean much for the end user, don't forget than Unix and Unix-like Operating Systems are indeed very powerful.
Actually, the irony here is amazing. Back in 1984, Apple ran an ad that had an Anti-Unix type of message in it. They fought against huge corporations.
Then came Microsoft, who challenged both of them.
And finally, Mac OSX is Apple with Unix parts, and it's preparing to take down Vista.
Oh, the irony. :)
Though, I'm seriously going to have to try OSX one of these days, to see how it measures up to Ubuntu, BSD, and all that. So long as it's more stable and better than Windows, and can run Photoshop natively.

OSX in a nutshell: All the licensing restrictions of windows and then some, packaged together to look pretty so the user is content that the computer pretty much tells the user what to do rather than the other way round, and there is even less software available for Mac than linux.  Sure you could argue that there is stuff like Adobe MS Office, and it's good software, don't get me wrong... but having adobe != 20,000+ packages in a repo.  The choice of software you have on OSX software is very small, its Mac software or a few (very few) alternatives.

If they opened OSX up for other hardware, loosened some of the licensing restrictions, and did less "it just works like this, don't do it any other way" programming I would give it a shot.  Underneath it is a very stable and capable OS.  My issues with it are surface, not structural.  The things that make mac users rave about it just do no appeal to me.  If there was a geekier version I would probably love the OS, but alas there is not.

---

### Post by izanbardprince on 2007-08-03
Well, OS X does have BSD compatibility and the Linux compatibility layer, so technically you could run most Linux software on Mac OS anyway, they even have KDE and GNOME packages for Mac OS.

---

### Post by FyreBrand on 2007-08-03
> **izanbardprince said:**
> With all the press about Mac OS now being UNIX certified, I thought I'd spell out exactly what that means for the typical Mac user.

In one word: Nothing.

In two words: Absolutely Nothing.

UNIX is not an operating system anymore, it's not any code in particular, it's a set of guidelines to guarantee interoperability with any other system that is UNIX-certified, to boil it down further, Microsoft could incorporate those guidelines into their next version of Windows, pay the money to get it reviewed, and Windows would qualify for UNIX certification.

As for the connection between OS X and Bell UNIX, they're like third cousins twice removed, OSX is based on modular chunks of FreeBSD kernel code running on top of the Mach microkernel, incidentally this allows Apple to market Mac OS as having a hybrid kernel, which in theory would have the stability of a microkernel (Mach) with the performance and features of a monolithic kernel (FreeBSD), but that doesn't help the user if the FreeBSD section crashes...."Well, I have no graphical, sound, or TCP-IP subsystems, but Mach is still up and kicking".

If you get to digging at the guts of Mac OS, or even playing around with the Terminal a bit, you'll see where it behaves similiarly to FreeBSD, but if someone wanted to run FreeBSD they would have just downloaded it, slapped it on a whitebox PC and left it at that, the point of Mac OS is to shield the average Joe from having to deal with the inner workings of a UNIX-like system, at the very top level, the operating system is 100% Apple, when a developer builds an application for Mac OS, you can't run it on other UNIX certified systems, or Linux, or BSD, or what have you, but when you design an app for a plain-jane UNIX or UNIX work-alike it will compile and run on Mac OS.

The point I'm trying to make here is that the UNIX standards that Mac OS adheres to don't mean anything unless you're a corporation that is switching over to Mac OS servers, and want to keep using "program x", and with the hardware and licensing fees being more than triple the cost of what you would get out of PC hardware and Red Hat Enterprise Linux or Sun Solaris, I don't think we're going to be seeing a stampede to Mac OS anytime soon, unless Apple graciously allows OS X to run on PC hardware or Sun SPARC.

All this means to the rest of us however, is now we'll undoubtedly be seeing Mac adverts and obnoxious fanboys jumping up and down about "UNIX this!" and "UNIX that!", where it's obvious that if you plopped them down in front of an AIX, IRIX, UnixWare, or Solaris system, who are also UNIX certified, but come with the bonus of actually working more like the traditional UNIX concept, they'd be drooling all over themselves.While I do mostly agree I don't think UNIX certification is as trivial as you're putting forth.  Many researchers use Macs and having application compatibility could be very important.

I agree for a home user or artist it probably means nothing at all so in that light you are right.  I would also say that is generally true for any platform and any certification; the trivial user just doesn't care about it.

I also don't think the concept of UNIX certification should be over trivialized.  It seems like the Linux standards group is taking this concept seriously.  Being able to run an application and not worry about if the OS is Fedora, Kubuntu, SUSE, Debian, etc would really be an achievement.  Being able to tag a distribution with a standards and compatibility certification, I think, would only help strengthen the entire Linux platform.

---

### Post by igknighted on 2007-08-03
> **FyreBrand said:**
> While I do mostly agree I don't think UNIX certification is as trivial as you're putting forth.  Many researchers use Macs and having application compatibility could be very important.

I agree for a home user or artist it probably means nothing at all so in that light you are right.  I would also say that is generally true for any platform and any certification; the trivial user just doesn't care about it.

I also don't think the concept of UNIX certification should be over trivialized.  It seems like the Linux standards group is taking this concept seriously.  Being able to run an application and not worry about if the OS is Fedora, Kubuntu, SUSE, Debian, etc would really be an achievement.  Being able to tag a distribution with a standards and compatibility certification, I think, would only help strengthen the entire Linux platform.

Standards and compatability are great... but any "standard" that you have to pay an inordinate amount of money to get certified for is, well, rather useless for free linux distros.  If more of the structure was built into the LSB (a common package format, for example, which is supposedly in the works) and distro's could be labeled (by a distro independant community panel) as linux certified or not, and not have to pay for it, then we could get somewhere.  But this "unix certification" as far as I am concerned means that apple had extra money to spend and not much else.  Linux distros could benefit a lot from being more consistant, but unix certification is not any part of the answer.

---

### Post by FyreBrand on 2007-08-03
> **igknighted said:**
> Standards and compatability are great... but any "standard" that you have to pay an inordinate amount of money to get certified for is, well, rather useless for free linux distros.  If more of the structure was built into the LSB (a common package format, for example, which is supposedly in the works) and distro's could be labeled (by a distro independant community panel) as linux certified or not, and not have to pay for it, then we could get somewhere.  But this "unix certification" as far as I am concerned means that apple had extra money to spend and not much else.  Linux distros could benefit a lot from being more consistant, but unix certification is not any part of the answer.I agree that most free distros wouldn't benefit or even be able to pay for branded certification, however the commercial distros and those seeking a commercial market through enterprise support might.  Businesses like consistency and compatibility.

I don't think Apple paid all that money for nothing.  I do believe they are trying to gain a foothold in a certain sector of the business and research sector.  It could be for this market they are certifying the OS.  Since it is an expensive certification there would have to be a justified return on the expense.

I like how this group is approaching the idea: [http://www.linux-foundation.org/en/Main_Page](http://www.linux-foundation.org/en/Main_Page)

---

### Post by darksidedude on 2007-08-03
>  UNIX is not an operating system anymore

well what is solaris 10 then? out of curiosity, isnt Sun the only UNIX company around?

---

### Post by izanbardprince on 2007-08-04
> **darksidedude said:**
> well what is solaris 10 then? out of curiosity, isnt Sun the only UNIX company around?

UNIX is just a trademark term owned by The Open Group, legally they have the right to call anything they want "UNIX", or license the use of the term to others, as they did with Apple, the UNIX certification specifications change over time, and so when you say something is UNIX certified, you really mean to say that it's certified  as whatever The Open Group is calling UNIX these days.

UNIX the source code is owned by SCO, they have to license the UNIX name from The Open Group to use on their products, interestingly you have to go all the way back to UNIX '95 for SCO  UNIXWare to qualify, it really doesn't mean anything other than thats the last certification they felt like paying for, but they still get to use "UNIX" in the name, SCO is the group that was suing IBM and Linux vendors (and their customers) for "stealing" a "significant portion of SCO's UNIX code" for use in the Linux kernel, in the end it was just a few lines in some header files here and there, that could have been there without the IBM Linux Engineers having ever even seen any of the UNIX code, the lawsuit was frivolous and SCO did it to increase their stock long enough so that the head honchos could sell it and get out.

Anyway, back to point, Solaris is UNIX '03 certified, as is Mac OS Leopard now, which means they conform to arbitrary standards of whatever The Open Group calls UNIX these days, and have paid The Open Group to be cerrtified and to license the UNIX name.

If, theoretically, I bought The Open Group and acquired their patents, I could declare that Linux was now a UNIX, that BSD was now a UNIX, and that the planet Mars was UNIX certified, I could even make a flavor of ice cream and call it UNIX "The ice cream where all the chocolate chips are represented by files".

---

