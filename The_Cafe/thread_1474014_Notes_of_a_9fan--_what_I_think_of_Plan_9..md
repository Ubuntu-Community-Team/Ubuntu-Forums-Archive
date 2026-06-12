---
title: "Notes of a 9fan-- what I think of Plan 9."
date: 2010-05-05
forum: The Cafe
---

### Post by MaxIBoy on 2010-05-05
I got asked in [this thread]("http://ubuntuforums.org/showthread.php?t=1470879") what I though of Plan 9 from Bell Labs. It turned out to be big enough for a whole new thread.

For those who don't know, Plan 9 was created by the same people who made UNIX in the first place. It's very UNIX-like, but it's improved in a number of ways. In many ways, it took a "back-to-the-basics" approach. Compared to UNIX-like operating systems, such as most (all?) Linux distros, it's a much better design. Unfortunately, it never caught on, so it's relegated to enthusiasts only these days.

So how is it? It's really, really fun to use. Plan 9 C is better than than ANSI C and even better than C99. The RC shell is missing out on some stuff I'm used to with Bash, but its overall design is so much cleaner and more well thought-out. In fact, the whole thing is clean and well thought-out. Even the much-maligned UI really *clicks* somehow. Everything about it, at least at first, seems exactly as it should be. It's like taking a stroll through an alternate universe where everything really is perfect.

What it has is perfect, but it's woefully short on many types of software. For example, the recommended way to do Web browsing on Plan 9 is by VNCing into a Linux or Windows box. How lame is that? But Abaco is pretty good, and Links is also pretty good. There are some excellent text editors for it (Sam, which is a sequel to Ed, and ACME, which is a bit like Emacs.) But word processing? You use markup languages and the like. There is no 3D acceleration available, and only minimal 2D acceleration is used. The only way to watch video on Plan 9 is to install the (limited and outdated) Plan 9 X-server and then run Mplayer in that. But there's no hardware video decoding supported. 

What it has is perfect, but it's not without its quirks. There is no concept of "lines." The up-arrow scrolls up 1/3 of the screen without moving the cursor. This includes the text editor. The left-right arrow keys work as normal, but it's really designed for you to move the cursor around with the mouse. This includes the command-line. There is no command history feature. Instead, you scroll up and use the middle-click paste. Plan 9 does this very well. With practice, using the mouse with Plan 9 is faster than using the keyboard on any other OS I know of. But, lord, it takes some getting used to for a mere, imperfect mortal.

The window manager, Rio, has a really great design. While it's limited out of the box, it provides enough functionality that you can do workspaces and such with a minimum of RC scripting in your startup sequence. Window titles and stuff could be implemented by having each window contain two windows, one for the title and one for everything else (plus some C to tie it all together.) So overall, Rio gives you the tools you need to improve it. But applications are responsible for deciding on their own colors and font sizes, so theming could only be done by changing Rio itself.

I have never installed it on physical hardware. However, I do know that it works a LOT better in QEMU than in VirtualBox. 9VX is pretty cool, but I never got contrib (the advanced package manager) working on it.

---

### Post by dragos240 on 2010-05-05
Thanks! I was hoping for a response.

---

### Post by dragos240 on 2010-05-05
So what would be an advantage of using plan9 vs any other unix-like system.

---

### Post by szymon_g on 2010-05-05
@dragos240
why do you think there are any advantages (other that 'look, i'm cool, i'm using Plan9' or 'i'm interested in history, therefore- i'm running something that was cool in late eighties and didn't change alot from that time') ;)?

but seriously- it has close-to-non-existent driver support, you can't run most of software /without changing it's source code/, it has no commercial support.

---

### Post by MaxIBoy on 2010-05-05
> **szymon_g said:**
> @dragos240
why do you think there are any advantages (other that 'look, i'm cool, i'm using Plan9' or 'i'm interested in history, therefore- i'm running something that was cool in late eighties and didn't change alot from that time') ;)?Plan 9 wasn't released until 1992 (universities) or 1995 (public.) Also, in a lot of ways, Plan 9 is still more modern under the hood than most operating systems. It was the direct origin of that /proc filesystem you have in your Linux installation. Even now, ideas from Plan 9 are being merged into other operating systems (for example, Plan 9 resource sharing is being ported to the Linux kernel.) But in general, your point is valid. 

The one justifiable use-case for Plan 9 is distributed computing. Plan 9 was designed such that one single "copy" of the OS would be "spread out" over many computers. The original idea is that one computer would have all the hard drives, another would have a lot of CPU power, and then a bunch of people with smaller computers would be logged in, using them as terminals with displays, keyboards, and mice. At any time, any of these computers could be separated from the rest and run as its own entity. These computers could theoretically be on separate continents, it wouldn't really matter. While this is pretty amazing, it's not a setup which you are likely to find in the average home. Plus, PCs have become so powerful that this kind of setup isn't really needed anymore, except in some rare situations. 

Besides that, there isn't much that Plan 9 can do that other OSs won't do. However, you really can't beat the cool, alpha-geek factor. :)

> but seriously- it has close-to-non-existent driver support, you can't run most of software /without changing it's source code/, it has no commercial support.Plan 9 includes a whole entire POSIX implementation called "Ape," plus there are ports of many GNU tools as well, so right away there are plenty of command-line UNIX programs which you can compile on Plan 9 with little or no modification. Most of the really useful ones (IRC clients, torrent clients, text-based browsers, etc.) have already been compiled and are available in the contrib repo. Here's a listing:
[http://plan9.bell-labs.com/wiki/plan9/contrib_index/](http://plan9.bell-labs.com/wiki/plan9/contrib_index/)

As for commercial support:
[http://www.vitanuova.com/index.html](http://www.vitanuova.com/index.html)
Inferno sort of like a Plan 9 "distro." You can get it Open-Source or license it commercially. It's cool in that you can run it as a userspace application (like 9VX does for standard Plan 9 over Linux) or as an operating system.

---

### Post by Stuart Morrow on 2010-05-06
> **MaxIBoy said:**
> 
The one justifiable use-case for Plan 9 is distributed computing. Plan 9 was designed such that one single "copy" of the OS would be "spread out" over many computers.

No.  Plan 9 is not an SSI.

> **MaxIBoy said:**
> 
The original idea is that one computer would have all the hard drives, another would have a lot of CPU power, and then a bunch of people with smaller computers would be logged in, using them as terminals with displays, keyboards, and mice. At any time, any of these computers could be separated from the rest and run as its own entity. These computers could theoretically be on separate continents, it wouldn't really matter.

You didn't mention what the point of all that is, though.
What the Unix room wanted was something that gives the best of
both the dumb-terminals-into-server world (same files nomatter
what terminal you're at; same username and password on all
terminals; easy administration; stateless, replaceable
terminals) and the fast-workstations-of-the-80s world (things
like window systems and editors running locally and responsively
on your local "terminal"; less load on the cpu server).
And that's what the point of this design was, most else of it is
just a side effect.

[QUOTE=MaxIBoy]
 While this is pretty amazing, it's not a setup which you are likely to find in the average home. Plus, PCs have become so powerful that this kind of setup isn't really needed anymore, except in some rare situations.
[/QUOTE]
Yes and no.  A 2010 desktop is faster than a 2000 CPU server, but
an always-on CPU server is good for always-on tasks - IRC, cron
jobs, backups.
Also using a CPU server as an actual CPU server mostly transparently
extending your desktop/laptop still makes sense for, say, scientists:
[http://www.fastos2.org/projects/hare/publications/xcpu2.pdf](http://www.fastos2.org/projects/hare/publications/xcpu2.pdf)

[QUOTE=MaxIBoy]
Plan 9 includes a whole entire POSIX implementation called "Ape," plus there are ports of many GNU tools as well, so right away there are plenty of command line UNIX programs which you can compile on Plan 9 with little or no modification. Most of the really useful ones (IRC clients, torrent clients, text-based browsers, etc.) have already been compiled and are available in the contrib repo. Here's a listing:
[http://plan9.bell-labs.com/wiki/plan9/contrib_index/](http://plan9.bell-labs.com/wiki/plan9/contrib_index/)
[/QUOTE]
If you want to use Linux programs you may as well just use Linux.
If you use Linux programs on Plan 9 it won't look or feel like
Plan 9 - you'll have programs that don't plumb or produce plumbable
output, programs that require vt/curses and therefore don't use
the mouse, etc, etc.

[QUOTE=MaxIBoy]
As for commercial support:
[http://www.vitanuova.com/index.html](http://www.vitanuova.com/index.html)
Inferno sort of like a Plan 9 "distro." You can get it Open Source or license it commercially. It's cool in that you can run it as a userspace application (like 9VX does for standard Plan 9 over Linux) or as an operating system.[/QUOTE]
The difference between Inferno and Plan 9 isn't like the difference
between two Linux distros, it's more like the difference between
two BSDs - there's a common ancestor but they're _completely_
different systems.  It's a greater difference than that, even, since
programs written for one won't even compile on the other.


For me, the Plan 9 use case is that I can use it, read it, and understand
it without wanting to throw the computer out the window.  You can't
really read the Linux/GNU/BSD/X11/Gnome/KDE sources and understand
it.  Linux weenies might try to deny it, but Linux/GNU/etc is now every
bit as complex as Windows.
So I use Plan 9 (no I don't use Plan 9 exclusively) because it's a
system that can be understood by one person on their own, that matters
to me way more than distribution of resources or whatever.
Inferno was the first non-Linux OS running on the Sheevaplug, and the
port was done in I think two weeks by a guy with little experience
low-level programming and zero experience doing ports.
The Nintendo DS port was done by a computational linguist with no
experience kernel programming in the timespan of a GSoC project.

I udnerstand Plan 9 way better than Linux or Windows, but I've been
using Linux and Windows for years.

---

### Post by MaxIBoy on 2010-05-06
Well there you go, we've got a real actual expert opinion now. :)

And yes, the Plan 9 kernel source is very, very good. I'm not a kernel hacker by any stretch of the imagination, but I could understand it without too much trouble... It's just that some mental midget decided on two spaces for each indent level for some reason!

---

