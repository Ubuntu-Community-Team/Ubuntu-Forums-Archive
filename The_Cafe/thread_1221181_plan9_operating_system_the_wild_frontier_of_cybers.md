---
title: "plan9 operating system: the wild frontier of cyberspace"
date: 2009-07-23
forum: The Cafe
---

### Post by user sam on 2009-07-23
Hi y'all. I got bored so I thought I would inform you of something that anyone who finds this post probably already knows (because they would be looking for it). There is an operating system called plan9 from Bell Labs. It is similar to Unix and Linux in many aspects, but it is completely independent. (Well, aside from having the same birthplace as Unix) I thought it was quite interesting.
This is the website: [http://plan9.bell-labs.com/plan9]("http://plan9.bell-labs.com/plan9/")
It comes as a livecd. I have been unable to get it to work in virtualbox, but it works pretty darned well in qemu. I don't know about other virtual machines. It requires 32 MB ram, the file manager is called acme (it doubles as a text editor); easy to use once you figure it out. Instead of X, it uses a window system called rio. It's got a couple of simple games like sokoban and juggle. It has a few derivatives: octopus: [http://plan9.escet.urjc.es/ls/octopus.html]("http://plan9.escet.urjc.es/ls/octopus.html"), plan B: [http://lsub.org/ls/planb.html]("http://lsub.org/ls/planb.html"), and Inferno: [http://www.vitanuova.com/inferno/]("http://www.vitanuova.com/inferno/"). 
I personally prefer the original plan9 to the derivatives. Um, also, I probably wouldn't install this one on an actual hard drive (as opposed to a virtual hard drive) until you know (a lot) more about it.
And the mascot is really cute.
Oh! One more thing. In qemu when you run the livecd you can accept all the defaults. If you install it though, you have to tell it you have a vga screen instead of the default xga or it drops you into a shell and you can't run rio. 
Here is a unix to plan9 command "translation" page: [http://plan9.bell-labs.com/wiki/plan9/Unix_to_Plan_9_command_translation/]("http://plan9.bell-labs.com/wiki/plan9/Unix_to_Plan_9_command_translation/") in case anyone is interested.
The title of this thread is "the wild frontier of cyberspace" just because plan9 is used by so few. well, I thought this was interesting, anyway.

---

### Post by praveesh on 2009-07-24
I don't find any thing interesting in it . What's the need of too many unix clones?

---

### Post by kdetech on 2009-07-24
Then you haven't seen this open source clone of Microsoft Windows 
NOT BASED ON UNIX
[http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)

---

### Post by Methuselah on 2009-07-24
It's not really a Unix clone.
It's the successor to Unix.
It's really the Unix philosophy taken to the next level.
[IIRC, Linux's proc file system is a concept from Plan9]

It never really caught on the way Unix did though.
Maybe Unix was already 'good enough'.

---

### Post by UKBB on 2009-07-24
It looks awful. I would rather use Ubuntu out of the box than this.
 
[IMG]http://plan9.bell-labs.com/plan9/img/screenshot.gif[/IMG]

---

### Post by kk0sse54 on 2009-07-24
@OP check out [Glendix]("http://www.glendix.org/"), 

> This is the website of the Glendix project, an attempt at porting ideas from the Plan 9 operating system to Linux. Our ultimate goal is to create a minimalist Linux distribution that contains a Plan 9 userspace, instead of the GNU software that is usually provided by most distributions.

---

### Post by decoherence on 2009-07-24
I think I'll hold off upgrading my UNIX systems to Plan 9 for another decade. I'm sure by then Plan 9 will be mopping the floor with these silly OSes and their silly non-files.

I love Glenda!

ADD: I love Glenda so much, she's my new avatar! :D

---

### Post by raronson on 2009-07-24
Plan9 has been in work for years and years.  The intended goal was to build a better UNIX, but really, what's the point now?  It started too late and didn't make an impact outside of /proc.  It's 1980's origin just makes it... dated.

---

### Post by collinp on 2009-07-24
In the mindset of this thread, Linux, BSD, and the like are all also just Unix clones.
Positive, eh?

On topic, I believe they cloned the wm used in Plan 9 to run on Linux. ...w9wm?

---

### Post by LowSky on 2009-07-24
kinda like Hurd replacing Linux for GNU... just a waste of resources that have little if any  comparitive following.

---

### Post by decoherence on 2009-07-24
> **LowSky said:**
> just a waste of resources that have little if any  comparitive following.

like unix in the early 70s ;)

---

### Post by Viva on 2009-07-24
I love Plan 9 from outer space. Never understood why Edward Wood gets so much stick:)

---

### Post by chucky chuckaluck on 2009-07-24
looks interesting, but i'm not sure my equipment is old enough to run it.

---

### Post by ViperChief on 2009-07-24
> **praveesh said:**
> I don't find any thing interesting in it . What's the need of too many unix clones?

What's the point of having too many Linux distros? If a bunch of people thought like that a few years ago, Ubuntu wouldn't exist.

Having all the different clones/distros/etc. is good. Gives a variety of things to use, not to mention some people are just really interested in operating systems, like myself.

---

### Post by mmix on 2009-07-24
you can try plan9 on your ubuntu.

[http://ubuntuforums.org/showthread.php?t=1157431&highlight=plan9port](http://ubuntuforums.org/showthread.php?t=1157431&highlight=plan9port)

IMHO, ppl don't understand plan9, because, it is second system effect.

---

### Post by xuCGC002 on 2009-07-24
Isn't Plan 9 the name of a really awful b-movie?

Anyway, it's another UNIX variant. Interesting, but I don't feel like trying it out.

---

### Post by MaxIBoy on 2009-07-24
It's not a UNIX variant, it was intended to replace UNIX altogether (keep in mind that UNIX was invented at Bell Labs in the first place.) There are a lot of architectural differences. Some of these have been successfully re-integrated into UNIX-likes. Other ones are too "deep" in the architecture to be transferred effectively. (Plan 9 from User Space is an admirable effort to port a lot of Plan 9's utilities to Linux, but it's still not Plan 9.)

For example, Plan 9 has no special "root" user. Each user has its own permissions, and authorizations for specific tasks are handled by a daemon called "factotum."

Plan 9's window manager, "rio," simply provides a virtual screen, mouse, and keyboard to each program, which makes it a lot easier to write graphical programs. (Although I think this has been ported to Linux?)

Plan 9 has a "namespace" feature. Basically, each user logged in at a given time sees the system in a whole different way. The files, partitions, even devices are different, and there's no way to see into another user's namespace without permission. This has not been successfully re-integrated into Linux.

Plan 9 is a distributed OS, meaning that a single "copy" of it can run across many, not-necessarily-identical computers, with new ones constantly being added or removed. You could have a program using the CPU in one computer, the graphics card and monitor in a second computer, the sound card in a third computer, files stored on a fourth computer, the keyboard on a fifth computer, the mouse on an sixth computer, and the printer on a seventh computer. This is accomplished through merging the namespaces on multiple computers. Plan 9 resource sharing on Linux is still experimental, I don't know how successful it's been because I haven't tried it. I know for sure that the Linux version involves running a separate kernel on each machine though.

Plan 9 also made a made a return in force to the old "everything is a file" philosophy which had been left behind. You know that /proc directory? That originally showed up in Plan 9.


Plan 9 really would have made a better choice than Linux. My dream is that someday, Plan 9 will be able to use Linux device drivers, or that Linux would switch to the Plan 9 driver format (probably never going to happen, but a man can dream.) If that happened, I'd switch to Plan 9 in an instant.

---

### Post by user sam on 2009-07-25
Gee, I thought I made it quite clear that plan9 is not a unix (or linux, or gnu, or anything else) derivative. When I first began using Linux, I thought that it was interesting, not because it was useful or powerful, but because it was different from everything else I had seen. I didn't care about the complicated, at least to me, command line interface or getting the X windows system working beyond the basics. At the time I had only known of Macintosh (which I had used since OS 6) and Windows (and perhaps Amiga). After some time I grew bored with linux and hungered for something new. I discovered Reactos and BeOS/Haiku, but they failed to hold my interest. I soon, however, discovered plan9. To me, this was a unique operating system even by linux standards. And to those who argue that plan9 is old, keep in mind that Windows began in the eighties, Macintosh in the seventies, and UNIX in the sixties. Stable, popular systems are old, old, old.

Also someone mentioned their computer wasn't old enough for Plan9? I'm not quite sure what you mean, but Plan9 works on every architecture I can think of and is a live cd, meaning you don't have to install to try it. I agree that plan9 could use a little refinement, and that is why I am trying to spread the word about its existence.
 Oh, and I am rather fond of a program called plan9 from user space which ports plan9 programs to various unix-like operating systems including OS X. My favorite plan9 program is still Acme!:D

ONCE MORE: PLAN9 IS NOT A UNIX VARIANT!!!!!!!!!

---

### Post by rkirk on 2009-07-25
It's also worth mentioning that we can thank Plan 9 for UTF-8, without which, representing text beyond the basic ASCII characters would either be impossible or drastically different from how we recognize it today.

And, as a person with an interest in both linguistics *and* programming, I've definitely learned to appreciate how simpler my life is thanks to UTF-8 encoding.

---

