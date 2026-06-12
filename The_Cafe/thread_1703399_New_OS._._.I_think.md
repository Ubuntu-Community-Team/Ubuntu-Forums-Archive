---
title: "New OS. . .I think?"
date: 2011-03-09
forum: The Cafe
---

### Post by ki4jgt on 2011-03-09
I'm thinking of creating a new OS. I was wondering:

A) Is FreeDOS open sourced?
B) Can Python be installed on FreeDOS?

If the answer to both of these questions is yes, then I was thinking of making the OS completely out of Python. All games and or utilities and even the UI (If such a thing is possible) would all be made from python scripts with the FreeDOS base system.

---

### Post by Sean Moran on 2011-03-09
> **ki4jgt said:**
> I'm thinking of creating a new OS. I was wondering:

A) Is FreeDOS open sourced?
B) Can Python be installed on FreeDOS?

If the answer to both of these questions is yes, then I was thinking of making the OS completely out of Python. All games and or utilities and even the UI (If such a thing is possible) would all be made from python scripts with the FreeDOS base system.

> 
**FreeDOS** (formerly **Free-DOS** and **PD-DOS**) is an [operating system]("http://en.wikipedia.org/wiki/Operating_system") for [IBM PC compatible]("http://en.wikipedia.org/wiki/IBM_PC_compatible") computers. FreeDOS is made up of many different, separate programs that act as "packages" to the overall FreeDOS Project.[[1]]("http://en.wikipedia.org/wiki/FreeDOS#cite_note-SF-0") As a member of the [DOS]("http://en.wikipedia.org/wiki/DOS") family, it provides mainly disk access through its [kernel]("http://en.wikipedia.org/wiki/Kernel_%28computer_science%29"), and partial [memory management]("http://en.wikipedia.org/wiki/Memory_management"), but no default [GUI]("http://en.wikipedia.org/wiki/Graphical_user_interface") (although [OpenGEM]("http://en.wikipedia.org/wiki/OpenGEM") is listed on the official FreeDOS website). FreeDOS is currently at version 1.0, released on September 3, 2006.[[4]]("http://en.wikipedia.org/wiki/FreeDOS#cite_note-freedos-3")

FreeDOS supports vintage hardware IBM PC as well as modern ones, in addition to [embedded computers]("http://en.wikipedia.org/wiki/Embedded_computer"). **Unlike [MS-DOS]("http://en.wikipedia.org/wiki/MS-DOS"), it is composed of [free and open source software]("http://en.wikipedia.org/wiki/Free_and_open_source_software"), licensed under the terms of the [GNU General Public License]("http://en.wikipedia.org/wiki/GNU_General_Public_License") (GPL). **It does not require license fees or royalties and creation of custom distributions is permitted.[[1]]("http://en.wikipedia.org/wiki/FreeDOS#cite_note-SF-0") However, in its "util" section, it includes non-GPL software such as [4DOS]("http://en.wikipedia.org/wiki/4DOS").[[2]]("http://en.wikipedia.org/wiki/FreeDOS#cite_note-4DOS-1")

[http://en.wikipedia.org/wiki/FreeDOS](http://en.wikipedia.org/wiki/FreeDOS)


---o0o---

I am no expert on python, but it sounds like a lot of work unless you can port python smoothly, and get something UNIX-based to run on it.

Big job at first glance, but I don't mean to be pessimistic about things I don't know about.
.

---

### Post by ki4jgt on 2011-03-09
> **Sean Moran said:**
> [http://en.wikipedia.org/wiki/FreeDOS](http://en.wikipedia.org/wiki/FreeDOS)


---o0o---

I am no expert on python, but it sounds like a lot of work unless you can port python smoothly, and get something UNIX-based to run on it.

Big job at first glance, but I don't mean to be pessimistic about things I don't know about.
.

I've been googling. It sounds like one big headache, but I still want to attempt it :-( O well, hopefully it'll only take a couple of hours on Google. FreeDOS does networking, so if I can get this right, I may actually be able to make an OS with Internet capabilities. Mind you it'll all be in command prompt unless someone wants to contribute a GUI of some sort.

---

### Post by ki4jgt on 2011-03-09
Found a website which tells how to port Python to FreeDOS.

---

### Post by Joe of loath on 2011-03-09
> **ki4jgt said:**
> unless someone wants to contribute a GUI of some sort.

OpenGEM?

---

### Post by ki4jgt on 2011-03-09
> **Joe of loath said:**
> OpenGEM?

Now that I actually see that's part of the FreeDOS website. . . I wonder who all has attempted making an OS out of FreeDOS before :-(

---

### Post by Joe of loath on 2011-03-09
I think most people running FreeDOS are using it on old machines, or to run old programs. People can correct me if I'm wrong, but I've not heard of any serious applications for FreeDOS beyond BIOS flashing and such.

(Off Topic, I wonder if you can get FAMP - FreeDOS, Apache, MySQL and PHP? :lol:)

---

### Post by RiceMonster on 2011-03-09
> **Joe of loath said:**
> 
(Off Topic, I wonder if you can get FAMP - FreeDOS, Apache, MySQL and PHP? :lol:)

It would definitely work well on a non multitasking OS!

---

### Post by Joe of loath on 2011-03-09
Exactly! Where's the challenge in doing it on *nix?

---

### Post by Spice Weasel on 2011-03-09
I used to have the source code of a DOS webserver. I can dig it out if anyone is interested. :P

(although you would have to be insane to host things on DOS, it has the worst security of any operating system EVER)

DOS GUIs

[img]http://zelmanov.ptep-online.com/stuff/fd-o3-1.jpg[/img]

[http://ozonegui.sourceforge.net/](http://ozonegui.sourceforge.net/) (Wow.)

OpenGEM (Part of FreeDOS)

[IMG]http://zelmanov.ptep-online.com/stuff/fd-gem-1.jpg[/IMG]

SEAL

[IMG]http://sealsystem.sourceforge.net/images/screenshots/seal-2.00.11-ss1.png[/IMG]

[http://sealsystem.sourceforge.net/about.php](http://sealsystem.sourceforge.net/about.php)

---

### Post by ki4jgt on 2011-03-09
> **Joe of loath said:**
> I think most people running FreeDOS are using it on old machines, or to run old programs. People can correct me if I'm wrong, but I've not heard of any serious applications for FreeDOS beyond BIOS flashing and such.

(Off Topic, I wonder if you can get FAMP - FreeDOS, Apache, MySQL and PHP? :lol:)

Would you want to program a Python app for it? I'm planning on hosting repositories. If you add your program we may be able to pull an old system up to speed. I'm wondering if it can get to the point of running like a normal OS. Of course it won't all be in Python. It can't be, but I'm wanting a good 90-95% of it to be in pure python.

---

### Post by ki4jgt on 2011-03-09
> **Spice Weasel said:**
> I used to have the source code of a DOS webserver. I can dig it out if anyone is interested. :P

(although you would have to be insane to host things on DOS, it has the worst security of any operating system EVER)

DOS GUIs

[img]http://zelmanov.ptep-online.com/stuff/fd-o3-1.jpg[/img]

[http://ozonegui.sourceforge.net/](http://ozonegui.sourceforge.net/) (Wow.)

OpenGEM (Part of FreeDOS)

[IMG]http://zelmanov.ptep-online.com/stuff/fd-gem-1.jpg[/IMG]

SEAL

[IMG]http://sealsystem.sourceforge.net/images/screenshots/seal-2.00.11-ss1.png[/IMG]

[http://sealsystem.sourceforge.net/about.php](http://sealsystem.sourceforge.net/about.php)

Wow is right!

Since it's open sourced, maybe we can fix the security issues.

---

### Post by Joe of loath on 2011-03-09
> **ki4jgt said:**
> Would you want to program a Python app for it? I'm planning on hosting repositories. If you add your program we may be able to pull an old system up to speed. I'm wondering if it can get to the point of running like a normal OS. Of course it won't all be in Python. It can't be, but I'm wanting a good 90-95% of it to be in pure python.

I can't program more than simple maths in python :lol: I simply find interesting uses for existing programs.

---

### Post by RiceMonster on 2011-03-09
> **ki4jgt said:**
> Wow is right!

Since it's open sourced, maybe we can fix the security issues.

You mean like it being single user and having no concept of access permissions? Have fun.

---

### Post by ki4jgt on 2011-03-09
Why can't a multigroup user interface be implimented?

---

### Post by Spice Weasel on 2011-03-09
Also - it's bad enough that Windows still uses the DOS filestructure. Let it die. Let the goddamn backspaces die. Please take away the backspaces if you do this.

---

### Post by ki4jgt on 2011-03-09
Sorry haven't used DOS since HS. What backspaces are we talking about "~"

---

### Post by Spice Weasel on 2011-03-09
C:\Windows\setup.exe

^ those backslashes. No idea why I said backspaces.

---

### Post by t0p on 2011-03-09
> **Spice Weasel said:**
> C:\Windows\setup.exe

^ those backslashes. No idea why I said backspaces.

Oh goddess yes those flipping back-slashes!!  I hate hate but I also hate back-slashes!  If it wasn't against the CoC of this site I'd suggest giving Gates a couple of back-slashes!  (But he didn't actually invent them, did he?  He just stole them from someone else with no conception of right and wrong.)

---

### Post by kaldor on 2011-03-09
Port GNOME to it like all the cool distros do.

Do it!

Or, if you want to attempt a FOSS Windows clone, start helping out with ReactOS. It'd be awesome to see ReactOS get better. Sadly, it's still stuck in 1995.

---

### Post by forrestcupp on 2011-03-09
The thing is, if you're wanting to take a bunch of things that are already made and throw them together, you won't be using Python at all. I really doubt if there are any OS-level things that are programmed in Python.

---

### Post by jerenept on 2011-03-09
> **ki4jgt said:**
> Why can't a multigroup user interface be implimented?

The main developer decided to abandon that idea a long time ago.

---

### Post by ki4jgt on 2011-03-09
> **jerenept said:**
> The main developer decided to abandon that idea a long time ago.

Yeah, well, it's time to redo it.

---

### Post by jerenept on 2011-03-09
> **ki4jgt said:**
> Yeah, well, it's time to redo it.

I'm talking about Microsoft, about 20 years ago (could be more)

---

### Post by ki4jgt on 2011-03-09
> **jerenept said:**
> I'm talking about Microsoft, about 20 years ago (could be more)

I'm talking about the Open Source program FreeDOS which is kind of like DOS back in the day. If the problem lies in DOS' multiuser interface, then the problem can be corrected in FreeDOS especially since it's open.

---

### Post by Simon17 on 2011-03-09
> **Spice Weasel said:**
> Also - it's bad enough that Windows still uses the DOS filestructure. Let it die. Let the goddamn backspaces die. Please take away the backspaces if you do this.

Oh my God, I can't believe what a pile crap Windows is. Still using FAT filesystem, and *backslashes*. Unix has been using forward slashes for the past 40 years! When will Windows ever catch up? (hint: NEVER)

---

### Post by ki4jgt on 2011-03-09
> **Simon17 said:**
> Oh my God, I can't believe what a pile crap Windows is. Still using FAT filesystem, and *backslashes*. Unix has been using forward slashes for the past 40 years! When will Windows ever catch up? (hint: NEVER)

The original idea wasn't to fix DOS, but like I said, it's open sourced, I'm not familiar with anything besides Python, but if some others want to help me find the answer to this. I would be glad to accept anyone wishing to recode it. FreeDOS does provide a copy of it's self which has all applications and source code for around 200 megs.

---

### Post by Quadunit404 on 2011-03-09
> **Simon17 said:**
> Still using FAT filesystem

> **Simon17 said:**
> [SIZE="3"]Still using FAT filesystem[/SIZE]

> **Simon17 said:**
> [SIZE="4"]Still using FAT filesystem[/SIZE]

> **Simon17 said:**
> [SIZE="5"]Still using FAT filesystem[/SIZE]

> **Simon17 said:**
> [SIZE="6"]Still using FAT filesystem[/SIZE]

What rock have you been under for the past 10 years? Windows has been using NTFS as its default file system since 2001. NTFS &#8800; FAT.

---

### Post by ki4jgt on 2011-03-09
> **Quadunit404 said:**
> What rock have you been under for the past 10 years? Windows has been using NTFS as its default file system since 2001. NTFS &#8800; FAT.

OK??? Point [SIZE="2"]Point[/SIZE] [SIZE="3"]Point[/SIZE] [SIZE="4"]Point[/SIZE]

---

### Post by kevin11951 on 2011-03-10
There is an easier option, use FreeBSD as the base...

FreeBSD is very simple, integrated with itself, and CLI just like FreeDOS, except it can actually do stuff...

---

### Post by ki4jgt on 2011-03-10
> **kevin11951 said:**
> There is an easier option, use FreeBSD as the base...

FreeBSD is very simple, integrated with itself, and CLI just like FreeDOS, except it can actually do stuff...

Also includes Python :-) Need to know do I do the boot only CD?

---

### Post by ki4jgt on 2011-03-10
> **ki4jgt said:**
> Also includes Python :-) Need to know do I do the boot only CD?

Nah, I'm sticking with FreeDOS.

---

### Post by NightwishFan on 2011-03-10
I think BSD/Linux is more wise. :/

---

### Post by koleoptero on 2011-03-10
I think it'll be better to do something else, like cooking or pottery.

---

### Post by Spice Weasel on 2011-03-10
> **koleoptero said:**
> I think it'll be better to do something else, like cooking or pottery.

Or painting. With rat blood.

---

### Post by Tristam Green on 2011-03-10
> **koleoptero said:**
> I think it'll be better to do something else, like cooking or pottery.

I agree.  Or knitting.  Knitting is a nice hobby.

Maybe I could get a kickstarter fund going to extract genetic material from the OP, dragos240, and Kenny Strawn to create the perfect trifecta of how not to do Open Source?

---

### Post by koenn on 2011-03-10
> **Tristam Green said:**
> I agree.  Or knitting.  Knitting is a nice hobby.
yeah. knitting is nice.
but i think we'd pretty soon get threads asking for help on knitting a GUI with DNS cache, or something. 
No thanks.

---

### Post by Tristam Green on 2011-03-10
> **koenn said:**
> yeah. knitting is nice.
but i think we'd pretty soon get threads asking for help on knitting a GUI with DNS cache, or something. 
No thanks.

crud, i almost forgot about my Gosalia knit.

---

### Post by RiceMonster on 2011-03-10
> **Tristam Green said:**
> crud, i almost forgot about my Gosalia knit.

"Gosalia enterprise fast and easy to use knitting needles"

---

### Post by KiwiNZ on 2011-03-10
I have thought and thought and thought and thought and sat down and gave it some good old thinking time. And ......Why?

HP, Dell Lenovo and ET Al bash it on PC's because they feel they must put at least some OS on a piece of hardware so that makes a modicum of sense, but with respect.........Why?

MS dropped DOS for a reason, they moved on from Win3X for a reason, they moved on Win9X for similar so I am thinking again .........Why?

For a Historical project ...I can live with that , cool.
A hobby, again cool.
Going to try and release it, hmmmmm, surely you can think of a better project.

---

### Post by unknownPoster on 2011-03-10
@OP,

what kind of programming experience do you have?

---

### Post by ki4jgt on 2011-03-10
> **koleoptero said:**
> I think it'll be better to do something else, like cooking or pottery.
LOL, maybe. I'm not planning on doing it anytime soon, but will get to it
> **Tristam Green said:**
> I agree.  Or knitting.  Knitting is a nice hobby.

Maybe I could get a kickstarter fund going to extract genetic material from the OP, dragos240, and Kenny Strawn to create the perfect trifecta of how not to do Open Source?
Why? Because I choose to use an old MS product :-) Sorry, it was placed into open source so why not show microsoft how to make an OS, using one of their first OSs (Of all things)
> **KiwiNZ said:**
> I have thought and thought and thought and thought and sat down and gave it some good old thinking time. And ......Why?

HP, Dell Lenovo and ET Al bash it on PC's because they feel they must put at least some OS on a piece of hardware so that makes a modicum of sense, but with respect.........Why?

MS dropped DOS for a reason, they moved on from Win3X for a reason, they moved on Win9X for similar so I am thinking again .........Why?

For a Historical project ...I can live with that , cool.
A hobby, again cool.
Going to try and release it, hmmmmm, surely you can think of a better project.
I'm not doing it for the release. I'm doing it for all the things you have stated.
> **unknownPoster said:**
> @OP,

what kind of programming experience do you have?
Unfortunately I'm a beginner at Python and am fluent in BASIC

---

### Post by RiceMonster on 2011-03-10
> **ki4jgt said:**
> Why? Because I choose to use an old MS product :-) Sorry, it was placed into open source so why not show microsoft how to make an OS, using one of their first OSs (Of all things)

...

Unfortunately I'm a beginner at Python and am fluent in BASIC

I'm so very confident you'll be able to pull this off.

---

### Post by ki4jgt on 2011-03-10
> **RiceMonster said:**
> I'm so very confident you'll be able to pull this off.

LOL, it doesn't look good does it? :-)

---

### Post by NightwishFan on 2011-03-10
I am not going to be one to discourage you much, do have fun with this. :KS Still I think you are better off with something that has a team of people writing the c and assembly for you like Linux. :D

---

### Post by earthpigg on 2011-03-10
I would write off this ever being secure from the get-go. DOS was designed to be a single user system, wherein the primary means of security was preventing bad guys from having physical access to the computer running the system. Leave it at that.

I see the potential merit in your project, but it looks like you will be biting off more than you can chew if you attempt to make it a full desktop operating system the way Windows 7 or Ubuntu is.

Aim a little bit lower, and walk into this ready to take it as nothing more than a learning experience. There is no shame in that. Remember, Linus didn't plan for Linux to be what it became -- it was just supposed to be an interesting academic expeeriment created for his own uses.

Let me outline a model for you, and you tell me what you think:

A FreeDOS based platform with a package manager and collection of packages that perform routine calculations and tasks. Make it multiplatform, since python and BASIC run on pretty much everything. The LiveCD could be FreeDOS based, and the other versions downloaded as packages for various other operating systems.

there is a lot of really simple stuff that can be done with basic and python. stick to that stuff, and do it really well. I'll share with you something that took me all of five minutes to do, and that has genuine use (to me, at least, in my econ class and on my TI-83 that runs BASIC):

```
Disp "ELASTCAL"
Disp "C MASON"
Disp "PUBLIC DOMAIN"
Disp " "
Input "OLD QUANT-",A
Input "NEW QUANT-",B
Input "OLD PRICE-",C
Input "NEW PRICE-",D
Disp " "
Disp "ELASTICITY"
Disp "COEFFICIENT-"
Disp abs(((A-B)/((A+B)/2)/(C-D)/((C+D)/2)))
```

(what it finds: [http://www.sparknotes.com/economics/micro/elasticity/section1.html](http://www.sparknotes.com/economics/micro/elasticity/section1.html) )

I'm sure a virtually identical little app has been written thousands of times  before that does the exact same thing in the exact same way, but i guestemated that making it over again from scratch would be easier than finding it on google. 

A LiveCD or LiveUSB, in addition to downloadable software (exe, deb, apk, dmg, etc), and included set of software packages that will turn any computer temporarily into a $100 calculator might have some genuine value. Students taking online math classes, for example, are often required to have a TI-83/86 or a TI-83/86 emulator. No such emulator that will run purely on Free Software exists. yet. Make one, and make it have package management.

broad educational-centered categories could be created. for example, first semester of college algebra is pretty much identical across the United States. wouldn't it be nice for a very simple collection of software that would help you check your homework? the last year or two of high school seems to be where edubuntu leaves off. fill that gap, and move into university level stuff.

That's a project that is well within your skill level, and similar to what you wish to do, if you are up to it.

---

### Post by ki4jgt on 2011-03-10
> **earthpigg said:**
> I would write off this ever being secure from the get-go. DOS was designed to be a single user system, wherein the primary means of security was preventing bad guys from having physical access to the computer running the system. Leave it at that.

I see the potential merit in your project, but it looks like you will be biting off more than you can chew if you attempt to make it a full desktop operating system the way Windows 7 or Ubuntu is.

Aim a little bit lower, and walk into this ready to take it as nothing more than a learning experience. There is no shame in that. Remember, Linus didn't plan for Linux to be what it became -- it was just supposed to be an interesting academic expeeriment created for his own uses.

Let me outline a model for you, and you tell me what you think:

A FreeDOS based platform with a package manager and collection of packages that perform routine calculations and tasks. Make it multiplatform, since python and BASIC run on pretty much everything. The LiveCD could be FreeDOS based, and the other versions downloaded as packages for various other operating systems.

there is a lot of really simple stuff that can be done with basic and python. stick to that stuff, and do it really well. I'll share with you something that took me all of five minutes to do, and that has genuine use (to me, at least, in my econ class and on my TI-83 that runs BASIC):

```
Disp "ELASTCAL"
Disp "C MASON"
Disp "PUBLIC DOMAIN"
Disp " "
Input "OLD QUANT-",A
Input "NEW QUANT-",B
Input "OLD PRICE-",C
Input "NEW PRICE-",D
Disp " "
Disp "ELASTICITY"
Disp "COEFFICIENT-"
Disp abs(((A-B)/((A+B)/2)/(C-D)/((C+D)/2)))
```

(what it finds: [http://www.sparknotes.com/economics/micro/elasticity/section1.html](http://www.sparknotes.com/economics/micro/elasticity/section1.html) )

I'm sure a virtually identical little app has been written thousands of times  before that does the exact same thing in the exact same way, but i guestemated that making it over again from scratch would be easier than finding it on google. 

A LiveCD or LiveUSB, in addition to downloadable software (exe, deb, apk, dmg, etc), and included set of software packages that will turn any computer temporarily into a $100 calculator might have some genuine value. Students taking online math classes, for example, are often required to have a TI-83/86 or a TI-83/86 emulator. No such emulator that will run purely on Free Software exists. yet. Make one, and make it have package management.

That's a project that is well within your skill level, and similar to what you wish to do, if you are up to it.

Thanks, and like I said, I have no plan to do it any time soon, but I think that would take the challenge out of it. It may get annoying sometimes but that's how I learn. I set challenges (really high) and then learn all I can about them. I sort of aim for the stars so if I don't reach them, I will at least fall somewhere in between them and the earth.

---

### Post by KiwiNZ on 2011-03-10
> **ki4jgt said:**
> LOL, maybe. I'm not planning on doing it anytime soon, but will get to it

Why? Because I choose to use an old MS product :-) Sorry, it was placed into open source so why not show microsoft how to make an OS, using one of their first OSs (Of all things)

I'm not doing it for the release. I'm doing it for all the things you have stated.

Unfortunately I'm a beginner at Python and am fluent in BASIC

You are a beginner and you are going to show Microsoft how to make an OS, hmmmm whats that saying, 'God loves a trier'. I wish you best of luck with your endeavours .

---

### Post by unknownPoster on 2011-03-10
> **ki4jgt said:**
> 

Unfortunately I'm a beginner at Python and am fluent in BASIC

And with that, I'm fairly certain this project is a pipe-dream.

Good Luck getting this off the ground. You'll need a lot of it.

---

### Post by ki4jgt on 2011-03-10
> **unknownPoster said:**
> And with that, I'm fairly certain this project is a pipe-dream.

Good Luck getting this off the ground. You'll need a lot of it.

I've never had a shortage of it before. Sagittarius and a dragon. LOL. . .

---

### Post by Tristam Green on 2011-03-11
> **ki4jgt said:**
> I've never had a shortage of it before. Sagittarius and a dragon. LOL. . .

[Hokey religions]("http://en.wikipedia.org/wiki/Astrology") and [ancient weapons]("http://en.wikipedia.org/wiki/DOS") are no match for a good blaster at your side, kid.

---

### Post by rowland on 2011-03-11
I think its confusing enough for the people having in linux so many distributions and versions.
Even i dont know whats going on...

For personal use and experience do it. Otherwise consider it twice.

---

### Post by ki4jgt on 2011-03-11
> **Tristam Green said:**
> [Hokey religions]("http://en.wikipedia.org/wiki/Astrology") and [ancient weapons]("http://en.wikipedia.org/wiki/DOS") are no match for a good blaster at your side, kid.

Understood. . . :-) Just saying, I personally don't believe in luck.

---

### Post by koleoptero on 2011-03-11
Whatever you decide to do with this project, I hope it goes well, if only for being so good natured throughout all this thread. :)

---

### Post by forrestcupp on 2011-03-14
To sum up everyone's smart remarks, there's no way in the world it would ever be possible to create an OS in Python and BASIC. You can dream all you want, but it's an impossible dream. That doesn't mean you can't dream of someday being involved in the creation of an OS, just not using Python and BASIC. And you can't expect to assemble a team of experienced C or Assembly programmers to create your dream for you just because that's what you want. You'll have to end up being the driving force and prove that you have something worth people donating their time to. Python and BASIC just aren't going to make that happen for an OS.

What you need to do is come up with some good apps you can create using Python. Maybe learn PyGTK and come up with a decent GUI app or simple game. That's something that *is* possible to reach, and you will feel a sense of achievement, motivating you to reach a little higher. Then at some point, maybe you'll be ready to move to C/C++, with which you can create some other modest apps, and eventually start learning how lower level things are designed.

You can't just aim for the ultimate goal without setting a road map to get there. But if you get a good road map and take one step at a time, you can do whatever you set your mind to. Just keep in mind that if you're a beginner like you are, it will take a very long time to get to the point that you can even begin working on your ultimate goal. But you'll never get there if you don't start taking your baby steps now.

> **koleoptero said:**
> Whatever you decide to do with this project, I hope it goes well, if only for being so good natured throughout all this thread. :)

Good point. :)

---

### Post by ki4jgt on 2011-03-14
> **forrestcupp said:**
> To sum up everyone's smart remarks, there's no way in the world it would ever be possible to create an OS in Python and BASIC. You can dream all you want, but it's an impossible dream. That doesn't mean you can't dream of someday being involved in the creation of an OS, just not using Python and BASIC. And you can't expect to assemble a team of experienced C or Assembly programmers to create your dream for you just because that's what you want. You'll have to end up being the driving force and prove that you have something worth people donating their time to. Python and BASIC just aren't going to make that happen for an OS.

What you need to do is come up with some good apps you can create using Python. Maybe learn PyGTK and come up with a decent GUI app or simple game. That's something that *is* possible to reach, and you will feel a sense of achievement, motivating you to reach a little higher. Then at some point, maybe you'll be ready to move to C/C++, with which you can create some other modest apps, and eventually start learning how lower level things are designed.

You can't just aim for the ultimate goal without setting a road map to get there. But if you get a good road map and take one step at a time, you can do whatever you set your mind to. Just keep in mind that if you're a beginner like you are, it will take a very long time to get to the point that you can even begin working on your ultimate goal. But you'll never get there if you don't start taking your baby steps now.



Good point. :)

I understand it will take some low level programming. Thanks for the "Support" in mapping out my future, obviously you're not a fan of the whole good programmer over night idea. I didn't call for developers or a team of them. I just suggested an OS. O I also like how you suggested I should be PART of an OS and not in anyway able to create my own. (Sounding like I was incapable)

Look, I understand programming is a complicated task. It requires a lot of learning (Whether you consider that learning work or fun is up to you) I understand almost every project today requires some sort of road map to keep it up. What ever happened to the old days of programming, where you weren't as much focused on the map as you were focused on enjoying the ride?
I don't doubt your years of experience and wisdom (Depending on how old you are), but I'd appreciate it if you didn't limit my capabilities simply, b/c I am not experienced and then try to give me a road map based on my inability to program.
Current computing standards once started out as nothing more than a dream/idea. They were nothing more than neurons firing off in the brain. They did not start with a road map, but rather developed it later, AFTER the initial project was started. Anyone can have a good idea, and anyone can learn to program (Just like or as good as anyone else)
Again, I respect your wisdom and experience, but I'd appreciate it greatly if you didn't imply that I couldn't accomplish something simply because I was inexperienced. We all have to learn as we go along. Have a great day.

---

### Post by koenn on 2011-03-14
I like the way you dismiss good advice.
Looking forward to see your code.

---

### Post by forrestcupp on 2011-03-14
> **ki4jgt said:**
> I also like how you suggested I should be PART of an OS and not in anyway able to create my own. (Sounding like I was incapable)

> **ki4jgt said:**
> Again, I respect your wisdom and experience, but I'd appreciate it greatly if you didn't imply that I couldn't accomplish something simply because I was inexperienced. We all have to learn as we go along. Have a great day.
Obviously, you didn't read my post very well.

First of all, there's no one person in the entire world, no matter how experienced, that is capable of creating an entire OS on his own that is a viable option. It takes a "team" of people who are all a "part" of it. If you had read what I wrote, you would see that I also said that you are going to have to spearhead it and be the one to lead this thing and get it to the point that other people think it's worth "being a part of".

Secondly, I didn't once even hint that you, personally, can't accomplish anything. I did say you can't accomplish it using Python or BASIC, but I believe I actually said that "you can do whatever you set your mind to." A lot of people just dismissed your dream as a pipe dream, but I actually tried to give you a little support and show you that it can be done if you go about things the right way.

But if you're an overnight achiever, go for it. ;)

---

### Post by unknownPoster on 2011-03-14
> **ki4jgt said:**
>  I'd appreciate it greatly if you didn't imply that I couldn't accomplish something simply because I was inexperienced. 

Except for the fact that your posts in the programming talk subforum have indicated otherwise.

> 
They did not start with a road map, but rather developed it later, AFTER the initial project was started.

You also have no proof of that. Computer Science was a field even before computers as we know them were viable. The first computer scientists such as Turing, knew exactly what they were doing.

---

### Post by KiwiNZ on 2011-03-14
> **ki4jgt said:**
> I understand it will take some low level programming. Thanks for the "Support" in mapping out my future, obviously you're not a fan of the whole good programmer over night idea. I didn't call for developers or a team of them. I just suggested an OS. O I also like how you suggested I should be PART of an OS and not in anyway able to create my own. (Sounding like I was incapable)

Look, I understand programming is a complicated task. It requires a lot of learning (Whether you consider that learning work or fun is up to you) I understand almost every project today requires some sort of road map to keep it up. What ever happened to the old days of programming, where you weren't as much focused on the map as you were focused on enjoying the ride?
I don't doubt your years of experience and wisdom (Depending on how old you are), but I'd appreciate it if you didn't limit my capabilities simply, b/c I am not experienced and then try to give me a road map based on my inability to program.
Current computing standards once started out as nothing more than a dream/idea. They were nothing more than neurons firing off in the brain. They did not start with a road map, but rather developed it later, AFTER the initial project was started. Anyone can have a good idea, and anyone can learn to program (Just like or as good as anyone else)
Again, I respect your wisdom and experience, but I'd appreciate it greatly if you didn't imply that I couldn't accomplish something simply because I was inexperienced. We all have to learn as we go along. Have a great day.

A project without a plan or road map is like air released from a bottle. If you cannot follow that you have failed before you have begun.

---

### Post by ki4jgt on 2011-03-15
> **forrestcupp said:**
> To sum up everyone's smart remarks, there's no way in the world it would ever be possible to create an OS in Python and BASIC. You can dream all you want, but it's an impossible dream. That doesn't mean you can't dream of someday being involved in the creation of an OS, just not using Python and BASIC. And you can't expect to assemble a team of experienced C or Assembly programmers to create your dream for you just because that's what you want. You'll have to end up being the driving force and prove that you have something worth people donating their time to. Python and BASIC just aren't going to make that happen for an OS.

What you need to do is come up with some good apps you can create using Python. Maybe learn PyGTK and come up with a decent GUI app or simple game. That's something that *is* possible to reach, and you will feel a sense of achievement, motivating you to reach a little higher. Then at some point, maybe you'll be ready to move to C/C++, with which you can create some other modest apps, and eventually start learning how lower level things are designed.

You can't just aim for the ultimate goal without setting a road map to get there. But if you get a good road map and take one step at a time, you can do whatever you set your mind to. Just keep in mind that if you're a beginner like you are, it will take a very long time to get to the point that you can even begin working on your ultimate goal. But you'll never get there if you don't start taking your baby steps now.



Good point. :)

If I misinterpreted I'm sorry. I've been a little defensive here lately. You wouldn't believe how many people tell you to just give up on everything. In all honesty, I'm just tired of all the negative that's going around (Where I'm living not on here). It's been giving me migraines for the last year. I can't even think to try and program anymore because I started to question if they were all right (Programming's no longer fun anymore) So again, sorry if I misinterpreted. I'm just tired of everyone trying to shoot everyone else down.

---

### Post by NightwishFan on 2011-03-15
Do not give up. I think everyone is just saying to pick more reasonable goals. I will work with you on the browser after the SF album is out if you would like. :)

---

### Post by ki4jgt on 2011-03-15
> **NightwishFan said:**
> Do not give up. I think everyone is just saying to pick more reasonable goals. I will work with you on the browser after the SF album is out if you would like. :)

I'm not planning on giving up. Thanks for the encouragement. I was talking about everyone at home. Not here. . . Here it's fine, but I misread some of Forestcupp's statements.

> That doesn't mean you can't dream of someday being involved in the creation of an OS, just not using Python and BASIC. And you can't expect to assemble a team of experienced C or Assembly programmers to create your dream for you just because that's what you want.
> What you need to do is come up with some good apps you can create using Python. Maybe learn PyGTK and come up with a decent GUI app or simple game. That's something that is possible to reach
> You can't just aim for the ultimate goal without setting a road map to get there.

Yeah, in my ignorance I may have said some things which were inappropriate. I'm sorry Forest. . . When someone has tunnel vision and only sees what they want to see and not the entire text. It is hard to remain in the wise section of life.

---

