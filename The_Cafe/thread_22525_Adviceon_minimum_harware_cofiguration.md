---
title: "Adviceon minimum harware cofiguration"
date: 2005-03-28
forum: The Cafe
---

### Post by derykddb on 2005-03-28
Hi,
I am new to Lynex. My interest in the operating system is that, because of what I have read, It would be an ideal system for use by churches etc. Transfers of programs and operating systems to sister organisations can be done without fear of working illegally.
However there seem to be some serious problems when changing from MS windows to lynex with desktop facilities.
For example, my understanding is:
One would need a VGA card of at least 8 megs, windows works happily on 4 megs
It seems that some sound cards because of conflicts cannot be used on lynex.
On the other hand the group that developed the church system say that the system was developed on a 486. I must be missing something somewhere! 
What I need to know is the minimum configuration that could have a desktop facility using lynex with a reasonable word processor,  spreadsheet and accounting package. Alternatively a reasonable user friendly arrangement that could be used by users who are not computer fundies.
The church system can be found on &#8220;infocentral.org&#8221; so the only stumbling block is what hardware to use, especially considering that most churches if they have computers at all are likely to have old p1 or equivalent.
Can any one help 

Deryk.

---

### Post by moopere on 2005-03-28
>I am new to Lynex.

I don't want to come across as overly nit picky, but you'll get a lot less people laughing at you if you spell linux correctly.  

As I recall, Linus (of Linux kernel fame) says that the way to say Linux is...lin-ux (the "in" bit as "whats _in_ the box").  I could be wrong on this last however.


> My interest in the operating system is that, because of what I have read, It would 
> be an ideal system for use by churches etc. Transfers of programs and operating 
> systems to sister organisations can be done without fear of working illegally.

Yep, sounds good.


>However there seem to be some serious problems when changing from MS
> windows to lynex with desktop facilities.
>For example, my understanding is:
>One would need a VGA card of at least 8 megs, windows works happily on 4 megs
>It seems that some sound cards because of conflicts cannot be used on lynex.

Who told you this stuff?  The software developer?  I'd say they don't have a clue how to program for Linux and want to keep you away from the idea.  Seriously, I'd find out what their real objection is before going ahead with the project as forcing their hand might not get you where you want to go.

As for the so called 'problems' - I'm running Linux successfully on a 256K ISA Trident VGA card, also have an old 386sx with a mono (hercules) card in it, though you won't get a modern graphical display on that one I'll admit.

So out with the FUD on that one.   Speaking seriously now though, if you need a good modern graphical interface, which is probably why you are looking at ubuntu in the first place there probably are some minimum standards your hardware would need to meet, to that end I can inform you that I'm running ubuntu on a Pentium (1) 100Mhz with a 2MB S3 PCI VGA card in it at 1024x768 resolution 16 bit colour.  Gnome is not a performance demon under these conditions of course, but its a server and serves my network (37 machines) quite well.

As for sound cards...I'd say theres a reasonable chance that Linux now supports many more sound cards then recent versions of MS Windows does.  For instance, most ISA based cards will still work in Linux (even 8 bit SoundBlasters), however I don't think any ISA cards will work at all in Windows XP.  Theres very likely a compatability lag at the newest end of the market, but reading your email tells me that you are unlikely to be installing on hardware < 6 months old anyway so this should not present a problem.


>On the other hand the group that developed the church system say that the
> system was developed on a 486. I must be missing something somewhere!

Yep, something fishy here.  Unless of course the software was developed under Windows 3.1 or Windows 95

 
>What I need to know is the minimum configuration that could have a desktop
> facility using lynex with a reasonable word processor,  spreadsheet and
> accounting package. Alternatively a reasonable user friendly arrangement that
> could be used by users who are not computer fundies.

This is totally subjective.  A computer geek might well answer that the minimum system he could stand working with is a P4/3GHz and nothing less is worth having.  Neverthless, I'll give you my impression as I run a quite large variety of hardware and have some insight as a result (I hope).

Whilst Linux will run on almost anything (yep, even 386's), as you say above, you want to use a spreadsheet, word processor, etc etc, all within a graphic user interface...probably gnome (because you're here with ubuntu) - I've got a P1 (or Pentium Classic as they are known nowadays) with 96MB RAM and 5GB hard disk, 2MB PCI VGA graphics, 16 bit ISA sound blaster with a CDROM.  I'd suggest to you, and to the wider reading audience that this is about as low a system spec as you'd want to go to get the mythical 'usable' desktop.  

Its pretty slow, but only takes 10's of seconds not minutes to load up applications like Openoffice or Firefox.  Anything better than this is going to make you a lot happier.  By the time you get to 1GHz or better you'll be really pleased indeed.  I'm writing this from a 700MHz Dell laptop right now...Ubuntu is snappy and responsive.

Now, onto your software...


>The church system can be found on “infocentral.org” so the only stumbling
> block is what hardware to use, especially considering that most churches
> if they have computers at all are likely to have old p1 or equivalent.
> Can any one help 

You do of course realise that with a couple of no-so-easy-to-use exceptions, you can't ordinarily use Windows based software directly under Linux don't you?

I know nothing about the Chruch software you are dealing with of course - unless its pretty generic if its been written for Windows and particularly 'old' windows (Win3.1, 95, 98 etc) you might have a world of trouble trying to get it to work under anything other than the system for which it was written - even getting old Windows software to work under new versions of Windows does not always go smoothly.

My advice would be to contact a Linux geek from your church, outside the realm of the software writer, and see if they can get the software to work under a Linux emulation system like "Wine" or similar.

regards,
Craig

---

### Post by ubuntu_demon on 2005-03-28
[QUOTE=derykddb]Hi,
I am new to Lynex. My interest in the operating system is that, because of what I have read, It would be an ideal system for use by churches etc. Transfers of programs and operating systems to sister organisations can be done without fear of working illegally.
However there seem to be some serious problems when changing from MS windows to lynex with desktop facilities.
For example, my understanding is:
One would need a VGA card of at least 8 megs, windows works happily on 4 megs
It seems that some sound cards because of conflicts cannot be used on lynex.
On the other hand the group that developed the church system say that the system was developed on a 486. I must be missing something somewhere! 
What I need to know is the minimum configuration that could have a desktop facility using lynex with a reasonable word processor,  spreadsheet and accounting package. Alternatively a reasonable user friendly arrangement that could be used by users who are not computer fundies.
The church system can be found on &#8220;infocentral.org&#8221; so the only stumbling block is what hardware to use, especially considering that most churches if they have computers at all are likely to have old p1 or equivalent.
Can any one help 

Deryk.[/QUOTE]
 beatrix (based on ubuntu). Runs with 64 mb ram and a pentium class machine (or maybe a fast 486)

[http://www.watsky.net](http://www.watsky.net)

standard Ubuntu install needs more than this. I don't know how much more.

---

### Post by az on 2005-03-28
You had also started this thread here:

[http://ubuntuforums.org/showthread.php?t=22172&highlight=church](http://ubuntuforums.org/showthread.php?t=22172&highlight=church)

And I had answered you there.

---

### Post by totalshredder on 2005-03-29
[QUOTE=derykddb]Hi,
I am new to Lynex. My interest in the operating system is that, because of what I have read, It would be an ideal system for use by churches etc. Transfers of programs and operating systems to sister organisations can be done without fear of working illegally.
However there seem to be some serious problems when changing from MS windows to lynex with desktop facilities.
For example, my understanding is:
One would need a VGA card of at least 8 megs, windows works happily on 4 megs
It seems that some sound cards because of conflicts cannot be used on lynex.
On the other hand the group that developed the church system say that the system was developed on a 486. I must be missing something somewhere! 
What I need to know is the minimum configuration that could have a desktop facility using lynex with a reasonable word processor,  spreadsheet and accounting package. Alternatively a reasonable user friendly arrangement that could be used by users who are not computer fundies.
The church system can be found on “infocentral.org” so the only stumbling block is what hardware to use, especially considering that most churches if they have computers at all are likely to have old p1 or equivalent.
Can any one help 

Deryk.[/QUOTE]

VGA card is no big problem at all. I got a pentium 75 running with DamnSmallLinux (wow that'd work great in a church) and was able to get abi-word running slowly, but functionaly. Heck I could do a lot on that machine! I would suggest Feather Linux, it's got more stuff on it; but same basic functionality. Tip on speeding it up: Don't use desktop icons, or the slit. I got 100% **more** speed after doing that.

You could have just bumped your old thread though  :lol:

---

