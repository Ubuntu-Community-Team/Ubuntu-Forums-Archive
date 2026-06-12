---
title: "Why use Linux over Windows: A document"
date: 2007-01-14
forum: The Cafe
---

### Post by Pobega on 2007-01-14
I'm writing a document to convert my friends from Windows to Linux, and I need the community's help: I've documented some of the most commonly asked things, but I'm looking to expand the essay even more. Or if you have no more ideas, even just feedback would be helpful :D

[http://girafarig.digital-haze.net/miniwiki/](http://girafarig.digital-haze.net/miniwiki/)
(Note: This URL is subject to heavy downtime since it is hosted on my laptop. I will mirror it when it's done, but for now it will stay on my local server)

---

### Post by prizrak on 2007-01-14
One thing jumps out right away. Torvalds is not from Eastern Europe, his from Finland. Eastern Europe is concidered to be Slavic countries.

---

### Post by Pobega on 2007-01-14
> **prizrak said:**
> One thing jumps out right away. Torvalds is not from Eastern Europe, his from Finland. Eastern Europe is concidered to be Slavic countries.

Woops, sorry. I'm horrible at Geography, I'll just remove that right away.

---

### Post by nalmeth on 2007-01-14
In your first paragraph you attribute everything to linus. GNU was around and making software before linus finished his kernel, which is all he is responsible for. The OS we're using isn't his brain child. And he never thought much about 'liberated' philosophy, he just chose the GPL for his kernel. 

Paragraph 2, you might convince them with that, but they will ask questions and you will have to be honest for them you believe you.

P3, I'm pretty sure MS does have customer support, but regular people usually don't get it. They go to their local computer repair center, or call a trusted geek. Its good to tout the community, but don't lead off with IRC, this forum is as far as any regular person would want to go for help. And its more friendly, moderated, and helpful than IRC.

P4, I hope your friends are already terminal minded, because otherwise they will probably scoff at that, as cool as it is. Why not tout the graphical package managers, and point out they are front ends to a very powerful package manager called APT, and find some creative way to describe it. 
> Now that Linux looks good I bet you're thinking "But I still
won't be able to do what I do in Windows in Linux!".After reading this, they are going to expect that the GIMP is Photoshop for linux, but free. They will be severely discouraged when they find out it isn't. And Cedega isn't free, they will use this against you if the conversion doesn't work.
> The last thing on your mind might be your external devices, like
cameras/microphones, and how they don't have drivers in Linux. Well you
might like to know that it probably <i>does</i> have drivers in Linux, 
and even if it doesn't you can use your Windows drivers using a program
called <b>ndiswrapper</b>.You mislead them with this statement, ndiswrapper is only for wireless. If their camera/phone is not supported by the kernel, they won't be able to use their windows drivers. 
> In Linux, when
something goes wrong you can recompile the kernel (If that is too advanced
for you, it basically means "reinstall" but without losing your data).

This might be the best way to discourage them completely. You tell them that in Windows you would have to reinstall, and then you say something pretty geeky, and say in linux you have reinstall, sort of. 
I've never had to recompile the kernel, I don't understand why you would tout this as an advantage. 

> and if you still don't feel 100% secure you can create a partition
on your hard drive to just hold your data for you (Which doesn't work
in Windows, mind you)
But they can use FAT32 just fine for that.

In the essay you never once mentioned the ability to dual-boot. For any first-timer, this is a must. They NEED to have their familiar environment to fall back on, if they are brave enough to let you do anything to their computer to begin with. 

The very last paragraph (maybe minus the first sentence) is very reasonable and friendly, you should try to use more of that sentiment, and in my personal opinion, you should explain in more detail what freedom means in terms of the GPL, and why adopting free software is a smart, and rewarding thing..

---

### Post by Hendrixski on 2007-01-14
There's probably ton of propaganda literature out there.  Have you read any books about Open Source? They would be a good place to start: "The Cathedral and the Bazaar" by Eric Raymond is probably the most famous.

Also check out the Wikipedia article "Comparison of Windows and Linux"... and contribute to it if you can, it needs constant updating because things change so fast.

---

### Post by zerhacke on 2007-01-14
> Because of Linux's security, it is a virus free operating system. It is also completely free of spyware, malware, and adware.

This is just not so.  There are viruses for Linux, though nearly all of them are/were just proof of concept code that were in itself demonstrations on why the kernel/userland needed patched or modified for those very reasons.  Nevertheless, there ARE Linux viruses in the wild.  They're just exceedingly rare.

More dangerous to Linux than viruses, spyware, whatever are exploits against uninformed users.  You can bind a shell to a port just like you can do in Windows if you don't know what you're doing.  Not knowing what you're doing when that "please enter your password to invoke sudo/apt/network services/whatever" is just as dangerous in Linux as it is in Windows.  While most think it's a security feature to ask for your password every time you need to do something as root, it's really not.  Just because it asks for your password does not mean it's safe.

Case in point, if you don't know what you're doing and you turn on... say, Samba with a poor configuration, you're just asking for problems.  Running remote x displays, installing binary software from untrusted sources... all these can be more dangerous to a Linux user than Windows exploits who mainly anymore just display advertising windows.

Linux is not the security powerhouse most believe it is.  When you're INFORMED it can be, but it's not an automatic thing.  You can still be attacked on Linux.

> Downloading programs in Linux is easy and simple compared to Windows.
In Windows, if you wanted to download a program you would have to use google
to find the website, download and install the exe. In Linux, you have
something called a package manager.   For example, if I wanted to look for 
something to manage my phone, I would run this line on my terminal:

	apt-cache search phone

My results would be as follows:

	p gnome-phone-manager  -Manage your cell phone from Gnome

As easy as it was to find your package, it's even easier to install it. All
you would have to do is run

	apt-get install gnome-phone-manager

And the package manager does the rest of the work for you! Beats Windows
for speed, doesn't it? Also like I said before, everything is free on
Linux. As opposed to Windows, which charges you for most of it's programs.


Windows pundits are going to ask you what Windows Update does.  Sure, it's not a direct analogy, but you can get Windows software with it without having to google for it.  And, Windows Update doesn't charge you to use it.

Also, apt-get commandline probably isn't the best way to tout package management, as Synaptic is going to be the easier way to propose a switch in OS.  Considering that they're coming from a Windows background and are used to graphical install methods I think you would be better served showing off the graphical install method.

Most Windows users I have shown Ubuntu to are impressed with Synaptic, the descriptions of what the software does, and the huge list of software for it; They are thoroughly unimpressed with long lines of text scrolling by in a "DOS prompt".

> installing Wine is simple!

user@computer~$: apt-get install wine

And you're done!

This is a little oversimplified.  There's a little configuration needed most of the time, and teaching them to use WINE after install is something you need to do as well.  Sure, using it is dead simple to us, but most Windows users have never used an emulator before.  Yeah, I know, it's not really an emulator, it's a compatiblity layer.

Other than that, your essay looks great so far!  I'd like to be kept up on updates to this project and I'm sure I can offer assistance and write up bits for you too.

---

### Post by Pobega on 2007-01-14
I updated the page, but I'm having trouble thinking of a way to explain GPL; Any help would be appreciated.

Edit: Also, I'll add an entry about the Synaptic package manager but I think for textual purposes it would be easier to keep the flow going using the terminal apt commands

---

### Post by IYY on 2007-01-14
I am writing a "book", or rather a short introduction to Ubuntu, which has a section about advantages of free software. Maybe it could be of help:

> **_1.4       Advantages of Free Software_**

So, why would you use Free Software as opposed to other types of software?
You are not a programmer, so you cannot make any modifications of your
own to the code.

    It turns out that Free Software has many advantages, even for the non-
technical user. Here are some of the advantages:

**Price**

Despite the fact that Free Software means Freedom and not price, most
pieces of Free Software are indeed also free of charge, or at least significantly
cheaper than the closed-source alternatives. The reason for the low price is
simple: when the code is freely available, hundreds of programmers around
the globe develop it on their spare time.

    Why? Many see programming as an art, and programmers often do it
because they enjoy the process and result, and not for the money. Many
programmers find that creating Free software allows much more flexibility,
and "artistic freedom".

    Creating high-quality Free Software is also seen as an act of good faith.
Many programmers enjoy using Free Software and want to give back to the
community. Such donations of code greatly increase the fame and popularity
of the programmer in the digital community.

    So, surprising as it may seem, you can get quality Free Software for
absolutely no cost.

**Security**

If you are a user of software like Microsoft Windows, you are surely famil-
iar with various malicious software: viruses, spyware and hacking attempts.
Interestingly, Free Software tends to be far more secure than the alterna-
tives. In fact, users of Free operating systems do not even need an antivirus

or firewall! This may seem counter-intuitive, but has several very specific
reasons:

    The first reason is very simple. Recall that a closed-source software is
like a cake without a recipe. When you are given such a cake, can you be
sure that one of the ingredients is not, in fact, arsenic? If you bought the
cake from a reputable and expensive bakery, chances are that you are safe.
However, if you bought it from a shady character in the middle of the street
(this is analogous to downloading a closed-source program on the internet),
I doubt you can trust it.

    Some users may become suspicious at this point and say, "All this is
good and well for a programmer, but even if I see the source-code, how can
I be sure that it is not harmful?" The answer is simple. You never have to
do any of this tedious and complicated work yourself because with the code
being freely available on the Internet, hundreds of experienced programmers
carefully audit it for security flaws.

    The second reason is that Free operating systems like Ubuntu tend to
be designed for security. This is because these operating systems have been
originally designed not for the desktop, but for large servers. In fact, Linux
runs most of the world's servers today, including those in huge companies
like Google. Operating systems like Mac OS and Microsoft Windows, on
the other hand, have been originally designed for people without an internet
connection, at a time when security was not an issue.

    A third reason is that the users of Free Software tend to love and respect
their operating system and their fellow users. While this may change in the
future, with the rising popularity of Free Software, the good intentions of the
developers add greatly to your security.

    A fourth reason is that Free Software users tend to get their software from
a trusted source. Operating systems like Ubuntu have their own repositories
of programs that can be trusted completely. This is described in more detail
later in this book.

**Stability**

Free software tends to be more stable (that is, crash less frequently) than
closed-source software. The reason for this is the that Free software runs
on many servers, as mentioned earlier, and servers need to run for months
without crashing or rebooting.

Another reason is that Free Software is often written as art, whereas
closed-source software is written as a product. When writing software as art,
programmers try to make it to be praised by other programmers. Stability
is a measure of quality software, so an emphasis is made on it.

**Support**

Some people believe that when using a Free operating system or software,
they will be getting less technical support because it is not released by a
large corporation. Nothing could be further from the truth! In fact, support
for Free software is often far superior to that of closed-source software. In
general, there are two types of support you can get:

    The first is commercial support. This is the way companies that sell Free
software make their money. If you plan to install Linux on an important
server or for a large office, it may be a wise choice to buy it from an official
vendor. Companies like RedHat, Novell and Canonical (the company behind
Ubuntu) provide such support at affordable rates.

    If you are installing the Free Software on your home computer, a small
server or a small business, you don't need to spend any money on support.
Excellent online forums exist where questions are answered quickly and in a
friendly manner. These forums are very active; at the time of writing this
book, the Ubuntu Forums have 220,912 registered users, and two million
posts. In fact, 4118 users are online at this very moment! There are also
chatrooms for live support, as well as Linux Users Groups (LUGs). A LUG
is a local group that meets once every week or two to discuss Free Software,
and help each other with problems. New members are always welcome, no
matter how technically skilled.


> I updated the page, but I'm having trouble thinking of a way to explain GPL; Any help would be appreciated.

There's also quite a lot in the book about the GPL. I find that a metaphor that works very well is the cook and the recipe:
> 
**_1.1      Free Software?_**

Free Software is a term you may find confusing at this point. Why would
anyone in their right mind create free programs for you to install on your
computer? Is it true that there is no such thing as a free lunch? The answers
may surprise you.

    The first surprise is that when we talk about Free Software, we don't talk
about its price. Free Software can and is currently being sold, making for
an interesting but profitable business-model. In the Charter of Rights and
Freedoms, the Freedom of Speech does imply that speech costs zero dollars.
The hippies of the sixties did not mean that you didn't have to pay for their
Free Love (as far as I know, paying for love is illegal). So what does Free
Software mean? It means liberated software; software without an owner,
without restrictions.

    In order to understand what it means for software to be Free, we must
first understand what software is. Software is a computer program written
by the programmer. Examples of software you may be familiar with are
Microsoft Windows, Microsoft Office and Mozilla Firefox. But just as a cook
can't create a cake atom-by-atom, the programmer can't create a complex
piece of software in the language of the computer (a long sequence of ones
and zeroes). Just like the cook's recipe, the programmer has her code.

    The program code describes a piece of software in a way a well-trained
human can understand, just like a well trained cook can understand a recipe.
The process of converting this code to the ones and zeroes computers under-
stand, it needs to be compiled. Compiling a program is exactly like baking
the cake. Once the program is compiled, the result can be executed on your
computer, but can no longer be understood by humans, just as the recipe for
the cake cannot be derived from the finished cake itself.

    Once upon a time, nearly all software came with a copy of the source
code, allowing the programmers to modify it to better suit their needs. At
some point, however, people realized that software could be sold for profit
as a product. Since then, software has been distributed in what we call a
closed-source format. This means that you only get the cake, not the recipe.

    At that time, a man by the name of Richard Stallman has come to the re-
alization that software distributed in this closed-source format is imprisoned
by the company that owns it. Software, Stallman says, should not be owned
by anyone, but rather should be Free; modified, redistributed and used by
anyone. With the goal to liberate software, he created the project called the
GNU.

    But the liberation of software is easier said than done! Even if you do
own a piece of software, how can you release it to the world without the fear
of it being captured and enslaved yet again? The answer came in the form
of a legal mechanism called the GNU Public License; the GPL. When one
licenses his piece of software under the GPL, it means that the code must
be freely available, and any person must have the right to take that code,
make modifications to it and redistribute it (sometimes even making profit).
But the GPL also places a restriction on software that was modified in such
a manner: it must also be licensed under the GPL.

    So, the technical definition of Free Software is software licensed under the
GPL.

---

### Post by Pobega on 2007-01-14
Thank you! I've scanned through that all now, and I'll add ideas from it to my page when I get the chance.

---

### Post by jbysmith on 2007-01-15
Great writeup... you got me convinced.  Just finished backing up my XP system and installing Ubuntu now.

The only thing I'm worried about really is the "I don't need antivirus and firewalls" statements, which I've been seeing a lot.  Just how serious is that?  I've been weened as a kid on DOS 2.10 and have been a MS user since forever, and the though of not having a firewall or antivirus scanner running at all.. well... the image that comes to mind is me being dropped into a warzone, with nothing but a squirt gun, and my pants around my ankles.

---

### Post by Tomosaur on 2007-01-15
A lot of this is pretty misleading. Not all linux versions use synaptic, or have aptitude. Wine is not a windows emulator (the name even means 'Wine Is Not an Emulator'). I can understand you were going for simplicity, but even still. 

The are viruses and spyware for linux too - they're just not as common - and they're really only likely to affect you if you do something obviously stupid.

---

### Post by Down8ve on 2007-01-15
I'll tell you what would make me use Linux over Windows... if the developers would turn their attention to creating a set of terrific, high-quality applications for the Average Joe, much like Apple's iLife suite.

I mean here we are, with a terrific OS, and half-baked applications to do the fun things we like best.  Why keep updating an OS when folks want to do neat things with applications on it?

I think the iLife suite is a great target.  We already have OpenOffice, even some good media players.  Now, how about a way-cool movie editor/DVD maker, a GarageBand clone that integrates with whatever music player we decide on, etc.

Just my opinion, but an honest assesment of why I don't/can't use Ubuntu more.

-DSM

---

### Post by Pobega on 2007-01-15
> **Down8ve said:**
> I'll tell you what would make me use Linux over Windows... if the developers would turn their attention to creating a set of terrific, high-quality applications for the Average Joe, much like Apple's iLife suite.

I mean here we are, with a terrific OS, and half-baked applications to do the fun things we like best.  Why keep updating an OS when folks want to do neat things with applications on it?

I think the iLife suite is a great target.  We already have OpenOffice, even some good media players.  Now, how about a way-cool movie editor/DVD maker, a GarageBand clone that integrates with whatever music player we decide on, etc.

Just my opinion, but an honest assesment of why I don't/can't use Ubuntu more.

-DSM

Most programs written for Macs are made to work with one another, kind of like how KDE is; If you want an environment where everything works together, you should try out KDE. The learning curve is steep but it's a very powerful desktop environment if used correctly.


> **Tomosaur said:**
> A lot of this is pretty misleading. Not all linux versions use synaptic, or have aptitude. Wine is not a windows emulator (the name even means 'Wine Is Not an Emulator'). I can understand you were going for simplicity, but even still. 

The are viruses and spyware for linux too - they're just not as common - and they're really only likely to affect you if you do something obviously stupid.

I know Wine isn't an emulator, but going into specifics will just turn people off

And this was written specifically to move my friends from Windows to Ubuntu, so I based it on apt-get; It's not like this was written for school, or about Linux in general.

> **jbysmith said:**
> Great writeup... you got me convinced.  Just finished backing up my XP system and installing Ubuntu now.

The only thing I'm worried about really is the "I don't need antivirus and firewalls" statements, which I've been seeing a lot.  Just how serious is that?  I've been weened as a kid on DOS 2.10 and have been a MS user since forever, and the though of not having a firewall or antivirus scanner running at all.. well... the image that comes to mind is me being dropped into a warzone, with nothing but a squirt gun, and my pants around my ankles.

An antivirus you really don't need, since Linux viruses are one in a thousand; And Firewalls you still do need, I'm not sure if I specifically wrote firewalls but I will take that out (Anyone who is smart enough to work their way into your computer can probably cause havoc, especially if you don't have a firewall)

**Edit:** No, I said nothing about firewalls now that I look through it, just antivirus.

**Edit2:** I'm going to change it to be more direct in that I'm talking about Ubuntu specifically, I wasn't thinking when I first wrote this.

**Edit3:** Updated

---

### Post by aysiu on 2007-01-15
This is a well-intentioned effort, but I agree with nalmeth--it's too misleadingly positive.

If you set the migration expectations unreasonably high, you're bound to disappoint users who think GIMP is a free version of Photoshop, that OpenOffice has 100% compatibility with MS Office, that all applications are installable via *apt-get*, and that any Windows application can be run successfully in Wine.

Temper your enthusiasm with some examples of obstacles they will probably encounter and have to overcome, and you're more likely to get people who switch to Ubuntu and **stay** with Ubuntu.

---

### Post by Pobega on 2007-01-15
> **aysiu said:**
> This is a well-intentioned effort, but I agree with nalmeth--it's too misleadingly positive.

If you set the migration expectations unreasonably high, you're bound to disappoint users who think GIMP is a free version of Photoshop, that OpenOffice has 100% compatibility with MS Office, that all applications are installable via *apt-get*, and that any Windows application can be run successfully in Wine.

Temper your enthusiasm with some examples of obstacles they will probably encounter and have to overcome, and you're more likely to get people who switch to Ubuntu and **stay** with Ubuntu.

Okay, I added a few negatives:

> Instead of Photoshop, Linux has the Gimp. Instead of Microsoft Office, 
Linux has OpenOffice.org or Abiword. **These programs are alternatives for Windows programs mind you, and they are in no way intended to be complete replacements of their Windows brothers.** And if you don't like the Linux alternatives, **some** Windows programs will still run in Linux (Through a program called Wine). **Wine is a windows compatability layer which lets you run a fair amount of Windows-based programs in Linux.** Oh, and like I said before, installing Wine in Ubuntu is simple!

> Synaptic is a graphical interface that lets you search through and install packages, it is generally easier to use than the apt commands. **You might want to note though, that not _everything_ is available through your package manager, and even some things that are available aren't the current version.**

---

### Post by timpino on 2007-01-15
I think it would be nice if you pointed out that one should _NOT_ count on games working in wine/cedega/Crossover, so if one is a hardcore gamer, one should look that up before leaving Windows completely.

You did touch this in the final paragraph or something, but not deep enough imho, must people who do try linux, (at least I think) are somewhat younger, and younger people means more gaming :)

Otherwise it's really nice, very propaganda stylish, but I like it! If the other OSs brag about their stuff so can we! :)

EDIT: made it more politically correct :)

---

### Post by Pobega on 2007-01-15
> **timpino said:**
> I think it would be nice if you pointed out that one should _NOT_ count on games working in wine/cedega/Crossover, so if one is a hardcore gamer, one should look that up before leaving Windows completely.

You did touch this in the final paragraph or something, but not deep enough imho, must people who do try linux, (at least I think) are somewhat younger, and younger people means more gaming :)

Otherwise it's really nice, very propaganda stylish, but I like it! If the other OSs brag about their stuff so can we! :)

EDIT: made it more politically correct :)

Thanks for the idea, I was thinking about that too. I can't believe a year ago I was using computers for nothing more than games! I'll throw this in right after Wine, thanks.

**Edit:** Okay, I threw it in there.

---

### Post by SuperMike on 2007-01-15
Pobega, who's your audience? I don't think a large document will be read by "friends" and "relatives" on why they should switch. I think it will be counter-productive. However, be my guest -- I don't know your particular situation. I mean, this sort of document works great when you want to sell the boss, but not with friends, relatives, or customers/clients.

I think the best thing I've heard on the psychology of this kind of persuasion is that you need to sell people initially on the idea of a new kind of desktop, not of "Linux" or "Ubuntu". When they ask what it is, just calmly say "They call it Ubuntu and it's a new international thing that's taking off." 

Give them a USB memory stick that let's them boot up on it to try it out. Leave them with an Ubuntu CD. Be patient with them when they're stuck and help them along. And when they *really* want to convert to it and perhaps you might not have the time to help them on their more serious problems, point them to a forum. And if the forum isn't a big help, then Ubuntu's pay tech support is extremely affordable -- more so than Microsoft's.

Think about the top 15 reasons (3 sentences or less) on why you converted to it and leave that in bulleted form on a piece of paper you hand them with the CD.

---

### Post by Pobega on 2007-01-15
> **SuperMike said:**
> Pobega, who's your audience? I don't think a large document will be read by "friends" and "relatives" on why they should switch. I think it will be counter-productive. However, be my guest -- I don't know your particular situation. I mean, this sort of document works great when you want to sell the boss, but not with friends, relatives, or customers/clients.

I think the best thing I've heard on the psychology of this kind of persuasion is that you need to sell people initially on the idea of a new kind of desktop, not of "Linux" or "Ubuntu". When they ask what it is, just calmly say "They call it Ubuntu and it's a new international thing that's taking off." 

Give them a USB memory stick that let's them boot up on it to try it out. Leave them with an Ubuntu CD. Be patient with them when they're stuck and help them along. And when they *really* want to convert to it and perhaps you might not have the time to help them on their more serious problems, point them to a forum. And if the forum isn't a big help, then Ubuntu's pay tech support is extremely affordable -- more so than Microsoft's.

Think about the top 15 reasons (3 sentences or less) on why you converted to it and leave that in bulleted form on a piece of paper you hand them with the CD.

Well the initial reason I am writing this is because my friend Adam is on punishment, and he is supposed to buy a laptop; He wants a System76 but his mom wants him to buy a Dell. Obviously he can just install Linux onto the Dell, but I'm trying to persuade his mom into just letting him get the System76 because everything is guaranteed to be compatible out of the box and give him way less trouble than a Dell. And there is only one way to reach his mom (Since he's on punishment): Writing up a document. 

It actually did originally begin as a bulletin, but it's not easy to explain in bulletin form. Maybe if I get more free time I'll make a bulletin form alternative, but probably not tonight. 

I personally don't think that the document is too overbearing though, considering if someone is in any way thinking about switching operating systems they'd read up on it. But with something like this essay available, we can bring together all of the reasons to use Linux over Windows in one simple, organized document rather than scattered across forums or wikis.

---

### Post by SuperMike on 2007-01-15
I have an extremely important antedote about why Linux is better than Windows, no matter what version of either one.

Last night my daughter's Abiword processor crashed on her. Unfortunately she has this habit of typing the thing up before she saves it. Well, every word processor can crash, and some more than others. Abiword may not have all its bugs fixed, but darn it works well for me and is fast. So, anyway, she came to me in a panic. I asked if she had saved her file at least once because Abiword will automatically save every 5 minutes. Unfortunately she said she had not. Okay, I did the following trick to help her recover most of the text for her biology paper on dinosaur eggs. This trick will *NOT* work on Windows, and that's the point.

$ sudo strings /dev/mem | grep -i dinosaur > $HOME/Desktop/output1.txt
$ sudo strings /dev/mem | grep -i egg > $HOME/Desktop/output2.txt

She could then use gedit to open the text files, cut and paste the text back into Abiword, and edit it back to the way it was.

On Windows, they don't have an unlimited memory scan tool, nor a way to pull out just the text of it without the binary characters, nor a way to filter on that memory for certain keywords. On Windows, about the only thing you have are orphaned files in %TEMP% that you can inspect with a binary file editor and hope you can get what you need.

---

### Post by meng on 2007-01-15
> **Tomosaur said:**
> A lot of this is pretty misleading. Not all linux versions use synaptic, or have aptitude. Wine is not a windows emulator (the name even means 'Wine Is Not an Emulator'). I can understand you were going for simplicity, but even still. 
The are viruses and spyware for linux too - they're just not as common - and they're really only likely to affect you if you do something obviously stupid.
For the most part, I consider the original statements to be true, and Tomosaur's comments **more true** but largely irrelevant. As far as the average end-user is concerned, wine IS a Windows emulator (just not a very good one), and lame IS an mp3 encoder. Similarly, malware for Linux is mostly proof-of-concept rather than actual stuff released into the wild.

You have to describe things simply, because for most computer users this is a complete paradigm shift. I agree with most of the other comments, and that it is wrong to oversell Linux. That would just be a guaranteed method of causing disappointment and even emotional scarring to would-be users.

---

### Post by meng on 2007-01-15
> **SuperMike said:**
> Well, every word processor can crash, and some more than others. Abiword may not have all its bugs fixed, but darn it works well for me and is fast.
;)

---

### Post by Pobega on 2007-01-15
New URL located at: [http://pobega.ath.cx:1020/LinuxDoc/?page=Linux%20Transition&view=True](http://pobega.ath.cx:1020/LinuxDoc/?page=Linux%20Transition&view=True)

I'm currently working on the script for editing the page, and hopefully we can turn this into a community document.

---

### Post by MkfIbK7a on 2007-01-15
>    From this point on I won't be talking about Linux in general, but instead I'll be
focusing on the specific **Ubuntu distribution of _[COLOR="Red"]Windows[/COLOR]_** ([http://ubuntu.com/)](http://ubuntu.com/)). The following
apt commands are specific to the Debian Linux package manager, which Ubuntu Linux is
based off of.

WHAT?
shouldnt that say linux?

---

### Post by MkfIbK7a on 2007-01-15
> Most of the software in Linux is open source, which means that anyone can go in **_andedit_** the program. But since you're (most likely) not a computer scientist, you figure **_thathaving_** the source code won't effect you, right? Wrong. Since the code is open source **_thereare_**

every bold underlined piece of text needs editing...

---

### Post by Pobega on 2007-01-15
Oh crap, I must not have been thinking. Hahaha. Oh wow.

Edit: @wert: It's from the translation from txt to html, I must have missed a few of those.

---

### Post by MkfIbK7a on 2007-01-15
i understand lol:D

---

### Post by Pobega on 2007-01-16
Okay, now the whole script is functional; Feel free to edit it everyone!

Also, I put this on my FTP so it can have a static host: [http://girafarig.digital-haze.net/miniwiki/](http://girafarig.digital-haze.net/miniwiki/)

---

### Post by spinflick on 2007-01-23
> **Down8ve said:**
> I'll tell you what would make me use Linux over Windows... if the developers would turn their attention to creating a set of terrific, high-quality applications for the Average Joe, much like Apple's iLife suite.

I mean here we are, with a terrific OS, and half-baked applications to do the fun things we like best.  Why keep updating an OS when folks want to do neat things with applications on it?

I think the iLife suite is a great target.  We already have OpenOffice, even some good media players.  Now, how about a way-cool movie editor/DVD maker, a GarageBand clone that integrates with whatever music player we decide on, etc.

Just my opinion, but an honest assesment of why I don't/can't use Ubuntu more.

-DSM

Something like [this]("http://ubuntustudio.org/") you mean? :biggrin:

---

### Post by Unterseeboot_234 on 2007-01-23
Really, comes up often on the wife's XP box...

---

### Post by FrankVdb on 2007-01-23
Although the document is well-intentioned, I think it misses a crucial point.

You're trying to convert people for the sake of conversion. That doesn't make sense. You can only convert people if you know what they use their Windows PC for and what Linux has to offer in terms of improving that experience. 

Wine certainly isn't going to contribute to a good Linux experience. Wine is difficult to configure and highly user-unfriendly. It's basically a last-resort solution. People won't convert to Linux for the sake of attempting to use their Windows stuff under Linux. That wouldn't make sense, does it?

I think it's better to concentrate on non power users, i.e. on people using their system for basic stuff surfing, e-mailing, viewing multimedia, listening to music, etc.).

Converting power users is much more difficult and depends entirely on what they are using their system for.

---

### Post by Pobega on 2007-01-23
> **FrankVdb said:**
> Although the document is well-intentioned, I think it misses a crucial point.

You're trying to convert people for the sake of conversion. That doesn't make sense. You can only convert people if you know what they use their Windows PC for and what Linux has to offer in terms of improving that experience. 

Wine certainly isn't going to contribute to a good Linux experience. Wine is difficult to configure and highly user-unfriendly. It's basically a last-resort solution. People won't convert to Linux for the sake of attempting to use their Windows stuff under Linux. That wouldn't make sense, does it?

I think it's better to concentrate on non power users, i.e. on people using their system for basic stuff surfing, e-mailing, viewing multimedia, listening to music, etc.).

Converting power users is much more difficult and depends entirely on what they are using their system for.

So edit the document if you'd like, that's what I wiki'fied it for. You're probably right, telling someone that this will run everything Windows does is probably a bad idea.

---

### Post by old_geekster on 2007-01-23
As a long time Windows, short-time Ubuntu user, I have to say that, in many cases, the GUI interface is about on a par with the Windows 3.1 or early OSX.  Okay, this may be one person's opinion, but you can't convince Window's users look or ease of use is a reason to switch.  Also, I am a gamer.  Therefore, I am sure that I will never eliminate Windows from my computer.

What does this mean?  This means that I will always have a dual-boot system.  For now it is fun, because I am learning a complete new way of doing things.  However, will it become more of a hassle once I know Linux, as well as, I know Windows?  I don't know.

Don't get me wrong, as I said, I am enjoying Ubuntu.  You have to be realistic when attempting to convert people from one OS to another.  Price is a probably the best reason for most to convert.

---

### Post by whitefort on 2007-01-23
Hi,

As a Windows user who would dearly love to switch 100% to Linux, I read your article with interest.

I think it's a good article, but I would take issue with how it creates an overall feeling that Linux is like windows, only better/free.

In fairness, you don't say that outright.  You DO point out that Linux applications are not direct equivalents for their Windows equivalents -  and you also mention that getting Linux working properly may take a little 'prodding.'  But I feel that these issues really need to be spelt out very, VERY clearly to anyone thinking of quitting Windows for Linux.

.  In every Linux forum I've looked at, I've found messages from disillusioned Windows users who have been disappointed by their Linux experience - often they get quite harsh replies, and perhaps sometimes they deserve it - but the problem (IMO) is that when Linux is presented as being just like Windows, but better/free, it creates certain expectations, which often lead to frustration and disappointment.

I'm one of those who are finding the move to Linux to be extremely difficult, and I'm still not sure I'm going to manage it at all - there's some essential stuff that I just haven't been able to get working after weeks of trying - stuff that works 'out of the box' with Windows - I apologise for saying that, because I know Linux users hate to hear it, but it's true.

Messing around with the terminal and digging into conf files may be second-nature for the average Linux user, but for the newbie trying to switch from Windows, it's NOT easy, and it's certainly not intuitive.  Even Ubuntu is still a bit lacking in the GUI department.

In short, I'm all for encouraging people to try Linux, but I think there would be less frustration all round if it was spelt out more clearly in advance that the transition, while ultimately worth it, may be far from easy.

---

### Post by Pobega on 2007-01-23
Thanks for your feedback.

I'll edit the page now, to include some of these ideas; It should be done in an hour or so.

---

### Post by aysiu on 2007-01-23
> **whitefort said:**
> 
In short, I'm all for encouraging people to try Linux, but I think there would be less frustration all round if it was spelt out more clearly in advance that the transition, while ultimately worth it, may be far from easy. That's why I wrote [Is Ubuntu for You?](http://www.ubuntuforums.org/showthread.php?t=63315).

The response to more realistic expectations seems to be pretty good, given the replies to my original post. It's much better to undersell than oversell Ubuntu and/or desktop Linux.

---

### Post by Pobega on 2007-01-23
Okay, I edited the page except I couldn't think of anything to write for the last bit. Any help would be appreciated, feel free to just edit the page.

aysiu: Your document is very good and well put together, and it reminded me of one thing I forgot to include; The LiveCD!

---

