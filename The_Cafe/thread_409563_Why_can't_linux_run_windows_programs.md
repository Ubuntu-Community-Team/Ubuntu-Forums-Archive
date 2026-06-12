---
title: "Why can't linux run windows programs?"
date: 2007-04-14
forum: The Cafe
---

### Post by mthakur2006 on 2007-04-14
Why? I want to know....after all its all text which can be converted to bianry code and used by the machine.....I am intrigued..
any ideas?

---

### Post by DoctorMO on 2007-04-14
why can't a dishwaster cook bread.

---

### Post by Ireclan on 2007-04-14
I belive it all has to do with the SYNTAX of the binary code...

Why can't a Russian understand Greek? Don't both languages use sounds and letters?

---

### Post by koshatnik on 2007-04-14
> **mthakur2006 said:**
> Why? I want to know....after all its all text which can be converted to bianry code and used by the machine.....I am intrigued..
any ideas?

Candygram for mongo.

---

### Post by Compucore on 2007-04-14
Linux in gneneral was based off of Unix or unix like OS that runs on larger systems like Minicomputers, Mainframe, and supercomputers. So trying to run windows based software on a unix based environment would be fruitless since the development of unix/linux s completely different than what Dos and windows are based from. I don't want to go into grat details exactly without opening a Pandora's box of this that and the other thing is. Unix/linux will be different than windows on how it interacts with the hardware, and software related items. I wish I culd compile some really good games that were orignally in windows that I love playing with. But they never really release a version of that to be worked on so that it could be used wihin the unix/linux environment. I know there are a couple of games that are alerady set for use with Linux/unix environment. Since they wanted to share the experience with everyone who wanted to play theri game like unreal tournament for example. Not many software vendors that are out there in the general public will make games for the unix/linux family. Only for the windows or OSX family of computers. Due to they are more popular to use than is the linux community base OS.

Compucore

P.S. I am sure if they wanted to they could easily have ported it over to the unix/linux environment. But they never understood in general Some programmers don't really use Linux. And others here within the forums of Ubuntu and myself do some programming under ubuntu for the sheer pleasure of programming something different within another OS. It is always good to learn on how to program under different environments. Since it might lead to better jobs later on since they might be able to use your services elsewhere within the company.  that is unix/linux based.

---

### Post by Nils Olav on 2007-04-14
Windows programs uses windows's system resource.

---

### Post by DoubleQuadword on 2007-04-14
> **Ireclan said:**
> I belive it all has to do with the SYNTAX of the binary code...

Syntax? I don't think so. Programs are compiled to binary data, a programming language (anyone) helps you telling the compiler (and human beings) what you want the program to do. Compilers are the ones which builds the application itself, you just make the program readable. Those binary symbols you see are processor opcodes (pseudo-acronym for Operation Codes), one byte or a group of bytes may correspond to one or more opcodes, there's no such 'syntax' thing.

Anyway, regarding the main question, it's not true that Linux cannot actually 'run' Windows applications, it's that Windows applications normally uses Windows API calls, for example, among other system-dependent resources. Nevertheless, I could extend myself indefinitely but I think it's better to stop here, hoping this extremely brief comment was, at least, a bit helpful.

Regards.

---

### Post by Auria on 2007-04-14
As you pointed out, programs are made of code.

Now ask Microsoft to release their code... ask the big corporations to release the source code to their app... when you get their answer you'll understand why its not possible :D

you said "all programs are made of text that can be recompiled"... only if this code is made available by its makers

there is the Wine project though, that tries to make from scratch an entirely open-source windows environment

---

### Post by rai4shu2 on 2007-04-14
Square peg, meet round hole.

---

### Post by rocknrolf77 on 2007-04-14
> **koshatnik said:**
> Candygram for mongo.

Gotta love that movie :D Thank's for reminding me of blazing saddles. Comedy masterpiece. :guitar:

---

### Post by Extreme Coder on 2007-04-14
Because it's not Windows. That's whats all about it. You can't make a NES run a SMS game and you can't play a PS2 game on an XBox.

To be more specific, Linux can't run Windows programs because Microsoft closes its API so that it's so hard to run or reverse-engineer Windows programs. 
Windows programs use things not available on a Linux system, and also Linux programs use things not available on a Windows system.
Projects like Wine, Cedega and CrossOver try to create a suitable environment for a Windows program to run, but it's not that easy, because as I said before, it's all closed information.

I hope this post has been helpful.

Extreme Coder

---

### Post by DoubleQuadword on 2007-04-14
> **Auria said:**
> Now ask Microsoft to release their code... ask the big corporations to release the source code to their app... when you get their answer you'll understand why its not possible

I understand that, and in fact, when you release an executable you're releasing the source code written in binary data, the source is the executable itself. Obviously reading 1 MB of pure binary data translated to processor opcodes is really painful (is it?).

> **Auria said:**
> you said "all programs are made of text that can be recompiled"... only if this code is made available by its makers

I didn't say that, what I tried to explain is that programming languages provide a common basis for application development. And as I exposed above you actually have the source code, the code goes wherever the executable goes.

> **Auria said:**
> there is the Wine project though, that tries to make from scratch an entirely open-source windows environment

Yes I know Wine exists, and in fact, you're agreeing with me, that Linux is able (as any other OS) to run any program as long as anyone can provide a workaround for system-dependent issues.

> **rai4shu2 said:**
> Square peg, meet round hole.

What's that supposed to mean?

Regards.

---

### Post by DoctorMO on 2007-04-14
I don't think Linux should support the windows API, windows has enough trouble with keeping backwards compatibility with it's self and all the security breaches that entails.

Any programmer can port his application to Linux; that should be enough. if a product isn't available for Linux then don't buy it.

---

### Post by Somenoob on 2007-04-14
Because it's developed for Windows. You have to have the knowledge to comprehend a certain language, the same applies for machines.

---

### Post by DoubleQuadword on 2007-04-14
> **DoctorMO said:**
> I don't think Linux should support the windows API, windows has enough trouble with keeping backwards compatibility with it's self and all the security breaches that entails.

Any programmer can port his application to Linux; that should be enough. if a product isn't available for Linux then don't buy it.

Me too, and to be honest, I only use Linux (more precisely Ubuntu v6.10 - Edgy). I've never bought Windows (and, by the way, I'm not planning to do so). I, always, recommend everyone not only to use Linux but also completely remove Windows from their computers.

I'm just saying that Linux *can* support windows applications as long as anyone can provide a workaround for system-dependent related issues. Don't forget that most people still need to use windows applications in their home computers.

Regards.

---

### Post by DoubleQuadword on 2007-04-14
Auria I apologize for the post, I actually thought you were saying that to me. :)

Regards.

---

### Post by rai4shu2 on 2007-04-14
> **DoubleQuadword said:**
> What's that supposed to mean?

I can't answer that without sounding pedantic, so suffice it to say:

Windows programs = square peg
Linux = round hole

---

### Post by Adamant1988 on 2007-04-14
Windows programs are not compatible with Linux because they are written with Windows in mind.  They will make calls to DLLs that Windows has, make use of windows only software (DirectX anyone?), or make system calls.   What Wine attempts to do is create an open-source compatibility layer that mimics a windows install and tricks applications into "thinking" they're running in a really poorly done Windows install.

---

### Post by Anthem on 2007-04-14
> **DoctorMO said:**
> why can't a dishwaster cook bread.
I thought this summed it up pretty well.  Other possible editions include:

- Why don't my TV's rabbit ears pick up digital cable?
- Why can't I use wood shavings to flavor my food?
- Why doesn't my refrigerator run on diesel?

---

### Post by DoctorMO on 2007-04-15
> I'm just saying that Linux can support windows applications as long as anyone can provide a workaround for system-dependent related issues.

As someone who's programmed for both linux and windows I think this is a rather over simplification. you might as well have just said "We can win the war in Iraq as long as someone can provide a workaround for insurgent-dependant related issues."

Lets be honest, the windows API is horse manure and I wouldn't want support for it in gnu/linux by default. too dangerous. it isn't the fact that it's complex, has many bugs by design, has about 15 ways to call any of the hundreds of thousands of methods and dll functions it's that we're dealing with a moving target and a moving target that has malicious intentions against our community. we don't stand a chance of offering full support as good as we are as a community at offering the options people want.

Wait and we shall have adobe and eventually even microsoft developing for the gnu api directly.

> Don't forget that most people still need to use windows applications in their home computers.

No **most** people do not. Some people do; the odd, sad person who sold out on proprietory formats or programs without the will to demand proper support for their operating system of choice. what kind of sympathy should I have for them that they offer support for these products and formats (through use) and yet place all the blame for their not working on floss. I don't think there is a kind of sympathy, only sorrow.

---

### Post by PatrickMay16 on 2007-04-15
It's weird how some of you guys make the whole free software thing like it's a war or something. 
There's a particular windows app I use which has the source code released, but no linux version has been written. Now I could port it myself, but I don't know anything about programming, so that won't work. So I run it using wine. Are you going to regard me as scum for that?

---

### Post by Adamant1988 on 2007-04-15
> **PatrickMay16 said:**
> **It's weird how some of you guys make the whole free software thing like it's a war or something. **
There's a particular windows app I use which has the source code released, but no linux version has been written. Now I could port it myself, but I don't know anything about programming, so that won't work. So I run it using wine. Are you going to regard me as scum for that?

Uhm, you're getting awfully defensive there Mr. peacekeeper.   No one in this thread bashed windows at all (which is a small miracle in and of it self) yet you're acting like we're 'all up in your territory'.  

I give your post an 7 out of 10 for creative use of irony.

---

### Post by PatrickMay16 on 2007-04-15
> **Adamant1988 said:**
> Uhm, you're getting awfully defensive there Mr. peacekeeper.   No one in this thread bashed windows at all (which is a small miracle in and of it self) yet you're acting like we're 'all up in your territory'.  

I give your post an 7 out of 10 for creative use of irony.

Yeah, I'll give you 10/10 for being ridiculous. My post was aimed at Doctormo who was saying something about 'sad pathetic people' who use proprietary software.

You've got a lot to learn before you can beat me. Try again kiddo heh heh heh heh heh

---

### Post by cantormath on 2007-04-15
> **mthakur2006 said:**
> Why? I want to know....after all its all text which can be converted to bianry code and used by the machine.....I am intrigued..
any ideas?

These are the questions that keep me coming back again and again........Thank you for saying this......It has made my day! :popcorn:

---

### Post by DoctorMO on 2007-04-15
> There's a particular windows app I use which has the source code released, but no linux version has been written. Now I could port it myself, but I don't know anything about programming, so that won't work. So I run it using wine. Are you going to regard me as scum for that?

If the source code is available how is it proprietory or what private formats does it use that isn't in the available source code? I hardly see that what I way saying applies to you; since not only is the source code available but you've never felt like whining about the availability in these forums anyway.

As for wine, you will use the tools that you can and you will also accept the risks those tools come with. I'm saying wine will never be complete and it's better to port, it seems like you can't port so you'll have to ask the original developers or get someone else interested.

At least if you push at it you'll open up a new application to everyone else on these forums.

As for scum, well I fear you've read to much into it, I don't intent to insult people who depend on windows only proprietory programs, but I feel a great deal of sorrow for them; like children who won't take their hand out of the fire, it's not their fault really.

---

### Post by mthakur2006 on 2007-04-15
Yes thanks, I know why now... a happy camper now.
Regards,

---

### Post by EdThaSlayer on 2007-04-15
Linux can't run Windows programs because its Linux. Linux and Windows do things differently and use different types of libraries to do the same thing. If you did want a program to run on all systems you would have to do a lot of "if" statements which would probably double the amount of code needed by the program and as a result probably slow it down.

---

### Post by mech7 on 2007-04-15
> **EdThaSlayer said:**
> Linux can't run Windows programs because its Linux. Linux and Windows do things differently and use different types of libraries to do the same thing. If you did want a program to run on all systems you would have to do a lot of "if" statements which would probably double the amount of code needed by the program and as a result probably slow it down.

Umm that would not really matter ;) as you only need 1 if / switch statement in the beginning to check for aobut 2 of the major os linux / os x / windows..

[SIZE="1"]wish i could run windows apps on linux especially photoshop :([/SIZE]

---

### Post by ssam on 2007-04-15
there is the system calls issues. programs need to ask the kernel to do things. (windows does actually have all the POSIX system calls)

library differences. if you want to display a window on the screen you use a GUI library (rather than trying to specify what colour each pixel should be). windows has its APIs, linux has GTK, Qt etc. same issues for sound, networking, 3d etc. you could include all this code in your program instead of using libraries, but that would waste of a lot of effort.

cross platform programming. if you assume that code will only be run on a certain type of computer you might be tempted to make assumptions out of lazyness. eg assume that the directory separator is a '/' or a '\' or a ':', that line endings are '\c\f' or '\c' or '\f', that certain files should be in certain places. it does not take to much effort to make a dir_sep variable, and use that, but people don't always.

binary executable formats. there are different types. eg ELF, a.out, PE, .com etc.

WINE does a pretty good job of dealing with all these issues. you could always donate 50% of how much you would pay if you had to buy vista to them, to help them out.

---

### Post by Tundro Walker on 2007-04-15
See, everyone missed the opportunity on this thread.  Nobody should have actually answered his question...we should have all just answered in analogous questions like the first few posters did...

Why can't Linux run Windows programs?!?!?!

Why can't penguins fly when other birds can?

Why do hot dog buns come in packages of 8 when hot dogs come in packages of 10?  (Oh, wait, that was from Bullet Proof Monk, and I beleive the answer was, "sometimes things just work out that way...")

---

### Post by rai4shu2 on 2007-04-15
Okay, I didn't want to do this but here's the REAL reason:

[http://www.catb.org/%7Eesr/halloween/](http://www.catb.org/%7Eesr/halloween/)

---

### Post by 3rdalbum on 2007-04-15
> **Tundro Walker said:**
> Why do hot dog buns come in packages of 8 when hot dogs come in packages of 10?  (Oh, wait, that was from Bullet Proof Monk, and I beleive the answer was, "sometimes things just work out that way...")

That was actually from Father Of The Bride, and the answer was "It's a conspiracy between the bun manufacturers and the hot-dog makers to get you to buy 5 packets of buns and 4 packets of dogs!" :-)

---

### Post by mech7 on 2007-04-15
Ok so now it is clear that windows app can't run on linux.. but what does wonder me is why don't Apple OS apps run under linux? They are both based on the same code right :confused:

---

### Post by Adamant1988 on 2007-04-15
> **PatrickMay16 said:**
> Yeah, I'll give you 10/10 for being ridiculous. My post was aimed at Doctormo who was saying something about 'sad pathetic people' who use proprietary software.

You've got a lot to learn before you can beat me. Try again kiddo heh heh heh heh heh
If you're going to correct me and fire back, get your quotes right. 

> Some people do; the odd, sad person who sold out on proprietory formats or programs **without the will to demand proper support for their operating system of choice**

He's basically judging people who claim to "need" software from Windows, etc but have never bothered to vote with their wallet, or use another form of action, to see it happen.  Although I think what he said is an over-simplification as most companies will tell you to shove off unless you're in mass it seems like people have no problem demanding to the Linux community that their Windows programs and formats work in Linux, but they won't bother going to the people who can actually change that.   On that point, he's completely right.

---

### Post by cantormath on 2007-04-15
This is still one of the most awesomely funny questions of all time.

---

### Post by DoctorMO on 2007-04-15
> Why do hot dog buns come in packages of 8 when hot dogs come in packages of 10? 

Dogs are canine animals, I believe you meant to say hot dogs or "reformed, non meat based sausages" either way the bun couldn't be a bunn since that's a sweet bread with icing, perhaps you meant soft roll?.

I wish Americans could write in compatible English, could someone give them some wine?

P.S. The anwser is that bread has always been sold in dozens (12) and bakers dozens (13), sausages have always been sold in packs of 8 as 8 should equate to 1 pound, these are you historical mismatches, no one expected you to put sausages on bread directly.

---

### Post by moeFinley on 2007-04-15
You're all being a little harsh.  It's not such a stupid question.

The real answer which nobody has yet pointed out is that it would be a copyright infringement for another OS to copy what Windows is doing.

I'm sure the source code for all the Windows operating systems has been stolen/leaked at one point or another and Apple, Sun even Linux would like to run Windows applications to increase the number of users.  However it would be illegal, but not impossible.

They want to make a dishwasher that can cook bread but the breadmaker company wont let them :P

---

### Post by DoctorMO on 2007-04-15
> it would be a copyright infringement for another OS to copy what Windows is doing.

Nope, your confusing copyrights with patents. patents protect what something does, copyrights protect what something is. since wine doesn't copy windows only what windows is doing it's not copyright infringement.

---

### Post by ceil420 on 2007-04-15
> **DoctorMO said:**
> Dogs are canine animals, I believe you meant to say hot dogs or "reformed, non meat based sausages" either way the bun couldn't be a bunn since that's a sweet bread with icing, perhaps you meant soft roll?.

I wish Americans could write in compatible English, could someone give them some wine?

Epic.

---

### Post by skirkpatrick on 2007-04-15
First, trying to compare running Windows programs on Linux is not like comparing running PS2 games on an XBox.  A PS2 and an XBox have different processors, hence the binary code from one will not run on the other.  The same as why a Linux x86 binary will not run on a Linux PowerPC machine.  The binary code is different and has absolutely nothing to do with the source code.

If you were to write a simple "hello world" console-based application in either Windows or Linux, the binary would run under either system with the following exceptions: executable loader format and system library calls.  The binary executable format helps to dictate to the OS how the program is to be loaded and how to dereference jumps to different places in the code depending on where in memory the program is actually loaded.  The standard C libraries have the same functionality whether they are for Windows or Linux.  How that library actually interacts with the OS is different depending on the system.  And this is just for a simple console program.  Something as complex as a GUI program depends on even more libraries.  You can't run a KDE application on a Gnome system without having the KDE libraries.

These are the things that programs such as WINE try to deal with.  As stated, WINE Is Not and Emulator.  The binary Windows code runs directly on the processor just like any other Linux program.  WINE knows how to load a Windows EXE file properly into memory so that it can execute and it also provides all the system libraries that a Windows program would need to run.  If WINE could provide perfect replication of the behavior of the Windows system libraries and at the same execution speed, you would be able to run Windows programs on Linux as well as you can on Windows.

---

### Post by Lucifiel on 2007-04-15
The reason why people need to run certain Windows programs on Wine because usually:

a) There's no Linux program with equivalent features.

This could happen if you're working on some project which uses custom software that's not open-source or where porting the software over is going to be a pure nightmare.

b) There's a Linux program with equivalent features but the extensions/features you use or need are not supported.

Especially if you're working on a project with a few different people and the Linux program can only read a certain format but cannot save in it or work with files saved in that format.

Anyways, sometimes there are workarounds but they are not always feasible or require a certain level of expertise and familiarity with Linux or in this case, Ubuntu. Imagine spending 30 to 60 hours trying to find a fix or an equivalent Linux software when your Windows software is completely supported by Wine.

---

### Post by ceil420 on 2007-04-15
Like GIMP not having brushes with Scatter -_-

---

### Post by moeFinley on 2007-04-15
> **DoctorMO said:**
> Nope, your confusing copyrights with patents. patents protect what something does, copyrights protect what something is. since wine doesn't copy windows only what windows is doing it's not copyright infringement.

Talk about picky!  Even so either would do.  The code itself can be copyrighted and what it does can be patented.  Have you nothing better to do :D 

Also, I never mentioned WINE.  I know how it differs.

---

### Post by AndyCooll on 2007-04-15
> **moeFinley said:**
> Talk about picky!  Even so either would do.  The code itself can be copyrighted and what it does can be patented.  Have you nothing better to do :D .

Not entirely true. "What it does can be patented" ...only in certain countries.

:cool:

---

### Post by moeFinley on 2007-04-15
What?!  Are you all lawyers? :D 

/me attempts to drag everyone back to the point

Seeing as you are all lawyers can you tell me how ReactOS get away with it?  How does their system work?

---

### Post by Adamant1988 on 2007-04-15
> **moeFinley said:**
> What?!  Are you all lawyers? :D 

/me attempts to drag everyone back to the point

Seeing as you are all lawyers can you tell me how ReactOS get away with it?  How does their system work?

Theirs is a lot like WINE except they're building an entire operating system that mimics windows, even has a different kernel and everything.

---

### Post by viciouslime on 2007-04-15
> **Adamant1988 said:**
> Theirs is a lot like WINE except they're building an entire operating system that mimics windows, even has a different kernel and everything.

Quite why someone would ever want a clone of an already dreadful OS is beyond me... but good for them! There work also helps the wine project so better still!

---

### Post by DoctorMO on 2007-04-15
> Talk about picky! Even so either would do. The code itself can be copyrighted and what it does can be patented.

Nope, you can't patent formats, nor can you copyright them; you can only patent how a program reads those formats or decodes the protocols; so you get a lot of scope to work with, not to mention the fact that patents only apply when there are alternative ways to do the same thing, if there is only one way then the patent is invalid.

> Have you nothing better to do

Yes, thanks for reminding me.

---

### Post by macogw on 2007-04-15
> **DoubleQuadword said:**
> I understand that, and in fact, when you release an executable you're releasing the source code written in binary data, the source is the executable itself. Obviously reading 1 MB of pure binary data translated to processor opcodes is really painful (is it?).

You're wrong.  Binary is not source code.  Source code is human readable.  Humans can't read binary.  You can disassemble the binary, and that's called reverse engineering, but there are extremely few people in the world that can read disassembled code and reproduce equivalent source for that code.  Even the ones who can then have to find equivalent system calls in Linux to the ones in Windows or add more stuff to the original to recreate what that system call would do.  If you have the actual, human-readable source code and all the libraries, it can be recompiled.  Proprietary software does not have source code available though, so we can't recompile for our computers.

---

### Post by DoubleQuadword on 2007-04-15
Oh dear God...here I go again...

I encourage you to read before posting, it really bothers me when someone replies without taking a single minute to properly read previous posts. Do I have to explain everything every time I post something? I think you're smart enough to read between lines and to properly understand what I'm saying...anyway, just to be sure I'll explain it once more; I hope you understand this time:

> **macogw said:**
> You're wrong.  Binary is not source code.  Source code is human readable.  Humans can't read binary.  You can disassemble the binary, and that's called reverse engineering, but there are extremely few people in the world that can read disassembled code and reproduce equivalent source for that code.

I know that Binary isn't source code (it represents processor opcodes) which leads me to say that I also know what's called reverse-engineering. (Again, read my previous posts before posting).

> **macogw said:**
> Even the ones who can then have to find equivalent system calls in Linux to the ones in Windows or add more stuff to the original to recreate what that system call would do.

I really don't need (and care actually) Linux to support Windows API, I'm just saying that *is* possible, which doesn't mean it's easy, efficient, or whatever you want it to be.

> **macogw said:**
> If you have the actual, human-readable source code and all the libraries, it can be recompiled.  Proprietary software does not have source code available though, so we can't recompile for our computers.

Oh really? I didn't know that! (yes it's pure sarcasm). It's obvious you need the application dependencies to run it, but what I'm trying to say is that you can actually get the source code by performing the 'reverse-engineering' technique on the executable/library/etc. The code goes wherever the executable/library/etc goes.

Now, I really don't care at all if you can or can't understand (or even read) the source code in processor opcodes (or assembly), being able to do so doesn't make you a better or worse programmer. Think the fact you can actually debug a compiled application by disassembling it previously. I did that with several Microsoft buggy applications.

Please read what I posted and don't take it literally. I know source code is human readable (see my first post), but as you well said, anyone can reverse-engineer any library/executable/etc, and get it's source code in processor opcodes. Finally, (expecting this will avoid any other confusion) I repeat, if you don't know how to handle assembly (or processor opcodes) it's not a problem, but don't say you can't actually get the source, because you can, but obviously you won't get it to look the way you want or need.

Best regards.

---

### Post by Tomosaur on 2007-04-15
Answer:

Because Linux isn't Windows.

---

### Post by aysiu on 2007-04-15
What's the point of this thread, exactly?

---

### Post by Quillz on 2007-04-15
Even if Linux could run Windows programs, there's always some legal issue holding it back.

---

### Post by macogw on 2007-04-15
> **DoubleQuadword said:**
> Oh dear God...here I go again...

I encourage you to read before posting, it really bothers me when someone replies without taking a single minute to properly read previous posts. Do I have to explain everything every time I post something? I think you're smart enough to read between lines and to properly understand what I'm saying...anyway I'll explain it once more; I hope you understand this time:



I know that Binary isn't source code (it represents processor opcodes) which leads me to say that I also know what's called reverse-engineering. (Again, read my previous posts before posting).



I really don't need (and care actually) Linux to support Windows API, I'm just saying that *is* possible, which doesn't mean it's easy, efficient, or whatever you want it to be.



Oh really? I didn't know that! (yes it's pure sarcasm). It's obvious you need the application dependencies to run it, but what I'm trying to say is that you can actually get the source code by performing the 'reverse-engineering' technique on the executable/library/etc. The code goes wherever the executable/library/etc goes.

Now, I really don't care at all if you can or can't understand (or even read) the source code in processor opcodes (or assembly), being able to do so doesn't make you a better or worse programmer. Think the fact you can actually debug a compiled application by disassembling it previously. I did that with several Microsoft buggy applications.

Please read what I posted and don't take it literally. I know source code is human readable (see my first post), but as you well said, anyone can reverse-engineer any library/executable/etc, and get it's source code in processor opcodes. Finally, (expecting this will avoid any other confusion) I repeat, if you don't know how to handle assembly (or processor opcodes) it's not a problem, but don't say you can't actually get the source, because you can, but obviously you won't get it to look the way you want or need.

Best regards.

It's not exactly *easy* to reverse engineer, though.  Very few people can do it.  And reverse engineering isn't always exact.  You get an equivalency, yes, but depending on what compiler was used and what disassembler was used, there can be differences.

---

### Post by mthakur2006 on 2007-04-16
> **aysiu said:**
> What's the point of this thread, exactly?

Hi aysiu,
The point of my thread is to find out why exactly can't linux run windows programs. I have googled it, but didn't find anything regarding that so I thought that my go-to people might have an answer, and sure enough, they do! (no sarcasm intended).

Thanks,
M Thakur:KS

---

### Post by rai4shu2 on 2007-04-16
A lot of people have been chiming in on the "how" it doesn't work, but not much focus has been given to the "why" aspect. It's an important distinction, IMHO.

---

### Post by Tomosaur on 2007-04-16
> **rai4shu2 said:**
> A lot of people have been chiming in on the "how" it doesn't work, but not much focus has been given to the "why" aspect. It's an important distinction, IMHO.

The 'why' is that Linux isn't windows. Why doesn't your car run on coal? Why can't you live on petroleum? Why do your breathe oxygen, and not, say, carbon dioxide?

---

### Post by Adamant1988 on 2007-04-16
> **rai4shu2 said:**
> A lot of people have been chiming in on the "how" it doesn't work, but not much focus has been given to the "why" aspect. It's an important distinction, IMHO.

The "why" part of the statement is fairly obvious.  Applications were developed with Windows in mind, Microsoft keeps the code and everything associated locked down as tightly as possible to make sure that software isn't going to run cross-platform without being altered for each OS, etc.

---

### Post by rai4shu2 on 2007-04-16
@Tomosaur:

But that's just circular reasoning. It doesn't really answer the question.

---

### Post by ArtificialSynapse on 2007-04-16
Hmmm. . . class is ending, so I didn't get to finish all of this thread; but to be vauge, what exactly is involved in porting somthing from windows to linux over, provided all the source code is avaliable?

---

### Post by Tomosaur on 2007-04-16
> **rai4shu2 said:**
> @Tomosaur:

But that's just circular reasoning. It doesn't really answer the question.

It *does* answer the question. It is precisely the same as asking why we don't breathe carbon dioxide. Oxygen and hydrogen are both gases, but they're different chemicals. It's the same with software. A Linux program and a Windows program are both pieces of software, but they're both different, regardless of whether they do different things. Windows programs are written for Windows. Linux programs are written for Linux. It is **possible** to get programs from either to work on both, through platform-independent coding, or by emulating the platform in some way - either through producing a compatible API (Wine), or by virutalizing the operating system. Windows uses an API (which is a set of functions and procedures to perform many different operations), and thus Windows programs tend to only work on Windows. It is possible to ignore this API, but this MAY mean writing more code than is strictly necessary, and your code will not meet certain Windows development standards. By sticking to the Windows API, you have a kind of guarantee that your program will work in many different environments - but at the same time, you rely on the API being as efficient and secure as possible. Linux does not have such an API. It is more 'universal standards' based, and prefers toolkits and modules rather than an all-encompassing API. There is no 'Linux' GUI management code, for example. You can use any of a number of toolkits to manage your GUI, or you can just remove all GUI-specific stuff from your kernel if you so wish, and use only the terminal.

The two platforms are fundamentally different, and this is why Windows programs do not work on Linux natively, and vice versa. Software is not just instructions to the hardware - it is instructions to the Operating System too. Since the two operating systems understand different instructions, regardless of whether they perform the same task, code is platform dependent. It is possible to make programs from either platform work on the other. It is easier, however, to make Windows executable files work on Linux, because Linux is completely open and anyone can change the underlying code. For example, you can make Linux understand what to do with .exe files fairly easily. You cannot do the same thing easily in Windows - ie - make Windows understand files with no extension - because it is impossible to change how the operating system works. The easiest method then, is to cross-compile. This means you write your program ONCE, and then compile it once for Windows, and once for Linux. The end result is two different binary files compile from the SAME source code. The Linux one will only work on Linux, and the Windows one will only work on Windows (unless you use Wine or some other method to allow it to run on Linux).

Some programs are platform independent in the sense that the compiled file will run on either Linux or Windows. Java programs and Python programs, for example, will run on both, provided you have the virtual machine and the interpretor installed, respectively. Java programs are compiled into Java Bytecode, which is instructions for a 'pretend' machine (the Java Virtual Machine). This virtual machine takes the form of a platform specific program, which is why the Java website offers a Linux version, and a Windows version of the JVM. When you run a Java program, the Java Bytecode is compiled into 'real' machine code, so that it runs correctly through the operating system. This is known as JIT (Just In Time) Compilation. Python uses a similar method.

So you see - the reason Windows programs do not run on Linux is because Linux is not Windows. The two are fundamentally different, and you may aswell ask why you can't survive on petroleum. The executable file for Firefox is DIFFERENT to the executable file for Firefox on Linux, but they both perform the exact same functions. Oxygen is DIFFERENT to Hydrogen, but they're both gases.

---

### Post by mthakur2006 on 2007-04-16
that answers the question perfectly ;)

---

### Post by surfjdh on 2007-04-18
EVERYONE here has missed the simplest, and most obvious reason the translation of exe syntax is not possible/probable.   you ready? ... Windows stores information on your hard drive, dd-ram/sdram, and peripherals the same way as Linux, with a bunch of characters eg: 0begin12345678example12345678end0, 
Linux does something similar, but it has one subtle difference- begin12345678example1234567812345678end, this extra amt of blank space allows for editing without the need to make a new copy in a different area
(which is what windows does)eg:0begin12345678example(add a letter and BAM)-0begin12345678example12345678rev12345678example**s**12345678end0, 
now in Linux-begin12345678examples123456781234567end.  
note that the last line where "8" was removed and replaced with the"s" at the end of the word "examples".  This fundamental difference in the two file systems(ntfs/fat32 and ext2/ext3) makes for a near impasse between programs on windows and Linux.  sorry to be the bearer of bad news.  

p.s.each time i wrote 12345678 it was to represent 8 zeros; I figured that would be very hard to read/understand

---

### Post by mips on 2007-04-18
> **mthakur2006 said:**
> Why? I want to know....after all its all text which can be converted to bianry code and used by the machine.....I am intrigued..
any ideas?

Not really. The OS runs on the hardware. The applications run on the OS & not the hardware.

---

### Post by Nils Olav on 2007-04-18
> **mips said:**
> Not really. The OS runs on the hardware. The applications run on the OS & not the hardware.

No, in that aspect he is right.

---

### Post by mips on 2007-04-18
> **Nils Olav said:**
> No, in that aspect he is right.

What do you mean ?

You need an OS to interface to the hardware. The applications are OS dependent and will only run on that OS. Yes, it still ends up at the cpu but that is not the be all and end all.

If applications are not OS dependent then why have an OS at all ?

---

### Post by Nils Olav on 2007-04-18
> **mips said:**
> What do you mean ?

You need an OS to interface to the hardware. The applications are OS dependent and will only run on that OS. Yes, it still ends up at the cpu but that is not the be all and end all.

If applications are not OS dependent then why have an OS at all ?

You made it seem like an OS was absolutely necessary.

---

### Post by mips on 2007-04-18
> **Nils Olav said:**
> You made it seem like an OS was absolutely necessary.

No its not absolutely necessary, was not aware I created that impression. If you can get an OS to run on hardware then you can also get a application to run on hardware without an OS.
His question was "Why can't linux run windows programs?" and I dealt with it on that level, which is the OS level.

I should know as I have coded directly to 6502, z80, 68000, 8051 & PIC which had **no** OS ;)

---

### Post by skirkpatrick on 2007-04-19
Yes, in fact your BIOS runs on the CPU before the OS is even loaded into memory.  Code runs on the processor and programs written to run on an x86 processor will run regardless of the OS.  This is not the same as Java byte-code that runs on a Java Virtual Machine.  The OS is nothing more than code that runs on the CPU.  This is why Linux will run on a x86 CPU just like Windows.

What an OS does provide are all the niceties of a system.  The kernel portion of the OS provides basic functionality to run multiple programs and have them communicate with other sub-systems.  The OS also provides the ability to read/write to the filesystem (and no, filesystem difference DO NOT prevent Windows programs from running on Linux.  Linux will run happily from a FAT filesystem), communication channels, etc.  It used to be that the BIOS (Basic Input Output System) provided simple disk and video functions but it is mostly used to boot an OS now.  An OS doesn't even have to provide any graphical capability (look at Linux as a normal server install) but the program has to know how to interact with it to get things done.

To answer another question, there are several ways to make sure that your program will run on both Windows and Linux (or Mac or anything else).  You either write it in a language that is not compiled (like Java or Python) or you write it to use a helper library that has already been ported to those OS's.  A good case is GAIM.  It is written to use the Gtk user interface library.  When you install GAIM on Windows, you also have to install the Windows version of the Gtk library.

If you are writing some intensive graphics program like a video game, then you want to use the openGL graphics API instead of DirectX as there is an openGL library for both Windows and Linux.

---

