---
title: "Ever have someone compare Linux to DOS?"
date: 2007-02-05
forum: The Cafe
---

### Post by Crashmaxx on 2007-02-05
Any of you get this silliness? Seems like everytime someone sees me working in CLI, whether its a server that only has that interface, or just a virtual console window, they say the same thing, "Hey, that looks just like DOS." and if you try to explain the difference, they seem stuck on the idea that Linux is truly comparable to MS-DOS.

Now am I off base here in thinking that the Linux kernel and MS-DOS are so in different classes that its like comparing apples and oranges? Or do you think that its really a fair comparison?

My logic is, even just comparing the Linux kernel to MS-DOS, that Linux is so much more powerful and capable, that when compared to the simplicity of DOS, there just is no comparison. DOS could only run one app at a time and only had the most basic commands built in. Without running Windows on top of it, DOS is less of an OS in the modern sense then it is a simple hardware abstraction layer. Linux, on the other hand, has so much stuff built just into the kernel that it can do most things you would need an OS to do, directly in it with nothing on top. And if you take GNU along with Linux, it becomes a complete and seamlessly integrated OS with all the features one could ask for.

And when you take DOS in the context of Windows running on top of it, then it really is just a hardware abstraction layer and little more. Windows does everything separately, even running DOS within it multiple times to achive multi-tasking. And Windows requires separate drivers that bypass DOS all together to control most things. So maybe hardware abstraction layer is the wrong term, maybe it is just more of a software running enviroment.

Semantics aside, DOS does almost nothing compared to Linux. The Linux kernel is pretty much the entire guts of GNU/Linux, it does everything. Pretty much all apps run individually on the kernel, independent of each other for the most part. Nearly all hardware is controlled by the kernel. Any sort of GUI you run is pretty much just another app as far as the kernel is concerned.

My point is, that Linux is so radically different then MS-DOS, that to say they are similar just because they both use CLI is such a gross oversimplification, that it annoys me and just about offends me.

Thoughts?

---

### Post by KaroSHiv0n on 2007-02-05
Well as much as i would say it is like comparing apples and oranges most windows users only know command line as DOS so im not sure they mean it in a bad way just that its sort of like something they know.

---

### Post by manmower on 2007-02-05
Crashmaxx, just a tiny remark. You seem to have a misconception about what the kernel is. The shell and its commands such as ls etc. are tools that run on top of the kernel. I'm not sure you could really do more than DOS with the kernel itself. :)

---

### Post by Crashmaxx on 2007-02-05
> **manmower said:**
> Crashmaxx, just a tiny remark. You seem to have a misconception about what the kernel is. The shell and its commands such as ls etc. are tools that run on top of the kernel. I'm not sure you could really do more than DOS with the kernel itself. :)

Oops, yeah you're right. You'll have to excuse my stupidity in my rambling. Its early here still, I am not a morning person. I can't think straight pretty much anytime in the AM. Stuff was falling apart while I typed that so just ignore the blatantly incorrect remarks.

---

### Post by Brunellus on 2007-02-05
> **Crashmaxx said:**
> Any of you get this silliness? Seems like everytime someone sees me working in CLI, whether its a server that only has that interface, or just a virtual console window, they say the same thing, "Hey, that looks just like DOS." and if you try to explain the difference, they seem stuck on the idea that Linux is truly comparable to MS-DOS.

Now am I off base here in thinking that the Linux kernel and MS-DOS are so in different classes that its like comparing apples and oranges? Or do you think that its really a fair comparison?

My logic is, even just comparing the Linux kernel to MS-DOS, that Linux is so much more powerful and capable, that when compared to the simplicity of DOS, there just is no comparison. DOS could only run one app at a time and only had the most basic commands built in. Without running Windows on top of it, DOS is less of an OS in the modern sense then it is a simple hardware abstraction layer. Linux, on the other hand, has so much stuff built just into the kernel that it can do most things you would need an OS to do, directly in it with nothing on top. And if you take GNU along with Linux, it becomes a complete and seamlessly integrated OS with all the features one could ask for.

And when you take DOS in the context of Windows running on top of it, then it really is just a hardware abstraction layer and little more. Windows does everything separately, even running DOS within it multiple times to achive multi-tasking. And Windows requires separate drivers that bypass DOS all together to control most things. So maybe hardware abstraction layer is the wrong term, maybe it is just more of a software running enviroment.

Semantics aside, DOS does almost nothing compared to Linux. The Linux kernel is pretty much the entire guts of GNU/Linux, it does everything. Pretty much all apps run individually on the kernel, independent of each other for the most part. Nearly all hardware is controlled by the kernel. Any sort of GUI you run is pretty much just another app as far as the kernel is concerned.

My point is, that Linux is so radically different then MS-DOS, that to say they are similar just because they both use CLI is such a gross oversimplification, that it annoys me and just about offends me.

Thoughts?
windows hasn't run on top of DOS since MSFT moved to the NT kernel for Windows 2000.   

Patiently, I usually explain to them that, yes, a linux system is a lot like the DOS systems I learned to use.  It has a scary, black and white command line and (if you like) a shiny graphical interface on top.  

Any other technical comparisons are complete rubbish, and anyone making them can be thought to be poorly-informed.

I did a poll on these forums a while back (I should bump it) that seemed to suggest that most of us forums regulars were MS-DOS kids.   My other hypothesis is that most of the "not ready for the desktop" posters only started using computers after 1995.

---

### Post by bastiegast on 2007-02-05
From what I heard practically Win9x == DOS
Linux versus DOS is a very uneven battle. Even if you took linux from 1994 it would still be far more advanced than DOS (multitasking, multiusers, secure stable). I even think MS has caught up on linux a lot since the DOS days.

---

### Post by Brunellus on 2007-02-05
> **bastiegast said:**
> From what I heard practically Win9x == DOS
Linux versus DOS is a very uneven battle. Even if you took linux from 1994 it would still be far more advanced than DOS (multitasking, multiusers, secure stable). I even think MS has caught up on linux a lot since the DOS days.
. . . and now let us praise MS-DOS.

It was small (640k should be enough for anybody!), simple, and eminently suited to the task.  Sure, it had no networking stack, but none of the computers on which it was designed to run initially had network connectivity, so it wasn't a big deal.

It was also cheap and incredibly quick to spread:  hooray for boot floppies.

Cheap, dirty, widespread:  MS-DOS put computers everywhere, and then, when those computers started getting networked, there was a critical mass of users out there to create Linux and accelerate Free Software Development.  RMS had been working on GNU for something like 20 years to no avail;  but with cheap x86 machines everywhere, Linus had a kernel ready in almost record time.

So respect MS-DOS, the booster rocket without which our spaceship might never have left the pad.

---

### Post by sloggerkhan on 2007-02-05
> **Brunellus said:**
> windows hasn't run on top of DOS since MSFT moved to the NT kernel for Windows 2000.   

Patiently, I usually explain to them that, yes, a linux system is a lot like the DOS systems I learned to use.  It has a scary, black and white command line and (if you like) a shiny graphical interface on top.  

Any other technical comparisons are complete rubbish, and anyone making them can be thought to be poorly-informed.

I did a poll on these forums a while back (I should bump it) that seemed to suggest that most of us forums regulars were MS-DOS kids.   My other hypothesis is that most of the "not ready for the desktop" posters only started using computers after 1995.

Hey! I spent most of my life using system 7-9 macs (probably after or starting around '95) 'cause that's what my family had. Most of my life my parents used an outdated system 8 mac that my dad got cheap somewhere.

And even coming from the least CLI based mainstream OS, I still think linux is just as desktop ready as windows, especially if preinstalled.

---

### Post by happy-and-lost on 2007-02-05
I don't think you can compare Bash to DOS.

DOS would have to have some features in order for a comparison to even be drawn up ;)

---

### Post by G Morgan on 2007-02-05
DOS wasn't even a protected mode OS. You could directly access memory from outside a processes segment by simple ASM calls. This led to all sorts of hacks as viruses hooked the IVT.

This is without going into functionality.

---

### Post by Hendrixski on 2007-02-05
I assume that the people who say this kind of thing don't know the specifics.  I'm sure that to them they see a command terminal and think of the command prompt in Windows and think DOS.

It's kind of like word associations where one person says "Porsche" and another thinks "Ford" because they're both cars.

---

### Post by H.E. Pennypacker on 2007-02-05
What's the real difference?  Lots of Linux users use the command line as often as DOS users use the CLI (but, of course, DOS doesn't have GUI).  I feel these people are holding us (the Linux/Open Source movement) back by making us out to be archaic, and doing things people used to do way back (using the CLI).

---

### Post by Crashmaxx on 2007-02-05
> **Brunellus said:**
> . . . and now let us praise MS-DOS.

It was small (640k should be enough for anybody!), simple, and eminently suited to the task.  Sure, it had no networking stack, but none of the computers on which it was designed to run initially had network connectivity, so it wasn't a big deal.

It was also cheap and incredibly quick to spread:  hooray for boot floppies.

Cheap, dirty, widespread:  MS-DOS put computers everywhere, and then, when those computers started getting networked, there was a critical mass of users out there to create Linux and accelerate Free Software Development.  RMS had been working on GNU for something like 20 years to no avail;  but with cheap x86 machines everywhere, Linus had a kernel ready in almost record time.

So respect MS-DOS, the booster rocket without which our spaceship might never have left the pad.

Yeah, I agree that it was good for its original purpose. It was cheap and simple and a great first OS for computers of the age.

Now it wasn't the *worst* idea ever to build Windows on top of it. But in retrospect, the sloppy evolution of Windows and the legacy of its DOS base have made it the disaster it is today. Even after the switch away from DOS for NT, the amount of bad ideas that remained unchanged are immense.

[quote=H.E. Pennypacker]What's the real difference? Lots of Linux users use the command line as often as DOS users use the CLI (but, of course, DOS doesn't have GUI). I feel these people are holding us (the Linux/Open Source movement) back by making us out to be archaic, and doing things people used to do way back (using the CLI).[/QUOTE]
That's the whole problem right there. That "because DOS used CLI it is an archaic idea that should be abandoned" idea. The CLI is very, very powerful and Linux is only better for keeping it and not trying to think we all need are hands' held and lead though a million retarded "wizards". That only makes Windows all the worse, cause even if I know exactly what setting I want to change or whatever, I still have to through 50 menus to change it. This is where CLI shines.

But I agree the average user shouldn't need to use CLI and there should be a GUI for most anything the user would have genuine ability to set properly.

---

### Post by EmilyRose on 2007-02-05
Comparing linux to dos is what I did when I first installed mandrake 6.5 years back in like 2000. Because I knew DOS having used DOS/Windows 3.1 for a couple of years before we got a copy of 95'. DOS is the only reason that I had any idea what to do when given a blank, black screen with a prompt. The CLI is what people are comparing dos to linux for. Sure, the similarities probably stop there, but DOS is the only CLI that most poeple have ever seen/heard of (and I'm sure theres quite a few out there who have never even seen DOS today!!).  Thanks to my having used dos I at least knew how to get around directories in linux, which is probably not true of a lot of other folks today. So, I think its a semi-fair comparison in some ways to think of linux today as at least semi-similar to the dos/win 95' combo that I grew up with - you can use the gui for most things, but still need that command line for a few random things.

---

### Post by Brainfart on 2007-02-05
Comparing the shell (a userspace app) between the two is almost as unfair as comparing the kernels between them.  While I'll agree that the Linux kernel probably has been superior to the DOS kernel, I don't know enough of the history of the Linux kernel to say what faults it might have had.  Either way, comparing the Linux kernel of today to the DOS kernel of yester-decade (or possibly even before... when was the last substantial change made to it?) is just not fair.  Similarly, comparing the shells it somewhat difficult without putting them into perspective.  I'd only tend to pay attention to someone who'd had experience in both, concurrently, for a comparison.

Now the main problem is that the average user knows none of this.  Nor do they care, really.  They tend to judge things based on appearance, and yes, the CLI interface for both look quite similar.

---

### Post by Sepp1 on 2007-02-05
I really do most of my Ubuntu`ing from GUI, so i really don´t see much difference between a dos-prompt, and a Linux-prompt. Hopefully i will, when my "skills" improve;)

However the Gnome Desktop strikes me as so much more intuitive as a windowns desktop, *even thoug im used to it*.
That says a lot about the "windowns user freindliness"

---

### Post by Brainfart on 2007-02-05
> **Sepp1 said:**
> However the Gnome Desktop strikes me as so much more intuitive as a windowns desktop, *even thoug im used to it*.
That says a lot about the "windowns user freindliness"
The concept of user-friendliness is extremely subjective.  Everyone used to say (some still do) that Macs are very user-friendly.  If that's the case, why do I feel so lost everytime I use one?  People say Windows is user-friendly, but they forget about the time it takes to become a friend.  One reason Linux desktops are becoming increasingly popular, IMHO, is because they are similar to what people already know, so the learning curve is much lower.  And for people who don't know anything else, this is the bar to which they compare everything else.

---

### Post by koenn on 2007-02-05
> **H.E. Pennypacker said:**
> Lots of Linux users use the command line as often as DOS users use the CLI .  I feel these people are holding us (the Linux/Open Source movement) back by making us out to be archaic, and doing things people used to do way back (using the CLI).
Yes, and because it's so archaic and holding us back, Microsoft is now beginning to pay some attention to it  : [http://www.microsoft.com/windowsserver2003/technologies/management/powershell/default.mspx](http://www.microsoft.com/windowsserver2003/technologies/management/powershell/default.mspx)
 - yes, that's NEW in Windows Server 2003. 

Or could it be that they feel the need to compete with Linux because they see to many system administrators who want a powerfull command line interface so they can get some productive work done without the endless mindnumbing point-and-clicking ?

---

### Post by Brunellus on 2007-02-05
> **koenn said:**
> Yes, and because it's so archaic and holding us back, Microsoft is now beginning to pay some attention to it  : [http://www.microsoft.com/windowsserver2003/technologies/management/powershell/default.mspx](http://www.microsoft.com/windowsserver2003/technologies/management/powershell/default.mspx)
 - yes, that's NEW in Windows Server 2003. 

Or could it be that they feel the need to compete with Linux because they see to many system administrators who want a powerfull command line interface so they can get some productive work done without the endless mindnumbing point-and-clicking ?
as I recall the monad shell was supposed to make an appearance on longhor....er, Vista.

---

### Post by koenn on 2007-02-05
> **Brunellus said:**
> as I recall the monad shell was supposed to make an appearance on longhor....er, Vista.
possibly - It wasn't in Server 2003 but is compatible with it and offered as download, and I think it was/is supposed to be in 2003 Service Release 2  - anyway, brand new & trying to catch up.

update : looked it up : Powershell 1.0 : released november 2006

---

### Post by G Morgan on 2007-02-05
> **H.E. Pennypacker said:**
> What's the real difference?  Lots of Linux users use the command line as often as DOS users use the CLI (but, of course, DOS doesn't have GUI).  I feel these people are holding us (the Linux/Open Source movement) back by making us out to be archaic, and doing things people used to do way back (using the CLI).

All Linux servers are still CLI only for a very good reason. Also once you know what you are doing the CLI is regularly much faster than a GUI. I personally will not sacrifice productivity just to avoid scaring a few people.

---

### Post by G Morgan on 2007-02-05
> **Brunellus said:**
> as I recall the monad shell was supposed to make an appearance on longhor....er, Vista.

The way the server market is going, Longwait server might not even appear. IBM reckon only 24% of companies considering new server solutions are considering Windows while 80%+ are considering Linux (before anyone attacks my maths you can have mixed environments).

---

### Post by deanlinkous on 2007-02-06
> **Crashmaxx said:**
> 
Thoughts?

free vs. non-free would be a good point to bring up IMO

---

### Post by IYY on 2007-02-06
I've installed FreeDOS on a spare machine for retro gaming purposes and let me tell you... Nothing Like Linux. I can't understand how people could use that shell.

---

### Post by Brunellus on 2007-02-06
> **deanlinkous said:**
> free vs. non-free would be a good point to bring up IMO
Not relevant, surely.  If someone is comparing them on the basis that they both have scary black command lines, then the entire idea of free software is lost on them

---

### Post by macogw on 2007-02-07
> **Brunellus said:**
> windows hasn't run on top of DOS since MSFT moved to the NT kernel for Windows 2000.   

I did a poll on these forums a while back (I should bump it) that seemed to suggest that most of us forums regulars were MS-DOS kids.   My other hypothesis is that most of the "not ready for the desktop" posters only started using computers after 1995.

right about nt

I never used DOS.  I knew one thing:
cd temp
del *.*
to clear temporary internet files on Win95.  I know ifconfig = ipconfig now.  Um, that's it.  Windows is all-GUI for me.  I've noticed I know how to fix things on here a lot better than on Windows too now.  Bash can do enough stuff that DOS can't and that takes too many clicks in Windows that it's much more efficient for me.

---

### Post by deanlinkous on 2007-02-07
> **Brunellus said:**
> Not relevant, surely.  If someone is comparing them on the basis that they both have scary black command lines, then the entire idea of free software is lost on them

But that is the ONE thing that would make them totally different. Both are scary black terminals, both have commands and syntax, and so forth... 

So hit them with something that is truly different. Introduce the idea of free software, explain the control held by proprietary software...and so forth.

(hey I look for any good reason to preach GNU) :)

---

### Post by Brunellus on 2007-02-07
> **deanlinkous said:**
> But that is the ONE thing that would make them totally different. Both are scary black terminals, both have commands and syntax, and so forth... 

So hit them with something that is truly different. Introduce the idea of free software, explain the control held by proprietary software...and so forth.

(hey I look for any good reason to preach GNU) :)
Software Freedom is irrelevant to most users.  It's relevant to all users, yes, but it's more important to producers (developers) and those genuinely interested in software as a thing-in-itself.  

The vast mass of users can't be bothered with the intricacies of IP law that GNU represents--witness the huge warez/pirate scene.

Hauling this back on-topic:  Again, my usual reaction when I get "oh, that's a DOS prompt!" is "yeah, kind of.  In all computers, this is what happens underneath your shiny windows.  I prefer dealing with this for some things."

---

### Post by deanlinkous on 2007-02-07
bothered????
I would hope that anyone interested in GNU+Linux does not conisder it a bother...

---

### Post by SunnyRabbiera on 2007-02-07
I have to admit:
I miss dos/msdos.
dos was versitile, easy, very friendly...
and FSM bless oregon trail! :D
that and wordmunchers!

---

### Post by Brunellus on 2007-02-07
> **deanlinkous said:**
> bothered????
I would hope that anyone interested in GNU+Linux does not conisder it a bother...
it is possible to be a user and not to be interested.  Software freedom, copyright reform, and the patent system are pointy-headed academic topics.  Users would sooner discuss the flouridation of the water supply with you.

Water flouridation (and software freedom) aren't unimportant--they're just not universally relevant to all conversations.  Someone observing "oh, look, a DOS prompt!" is not likely to know or care enough about the pointy-headed WHYS of software to even listen to your chapter-and-verse quotations of the documents on GNU.org.

---

### Post by aysiu on 2007-02-08
I had my wife use the terminal last night to troubleshoot a widget/Dashboard problem on her Powerbook.

She said it was "just like DOS." Funny thing--she tried editing a system file and couldn't, so I had her do ```
sudo nano -B *nameoffile*
``` and she had fun editing it with Nano.

P.S. Anyone know if there's the equivalent of *gksudo nautilus* for Mac OS X's Finder?

---

### Post by Zyphrexi on 2007-02-08
yeah... Occasionally i try to explain, but the majority of the time they are so rock solid in their belief I just grunt. "grunt-grunt"

Oh yeah, and I remember this guy who tried to argue against linux security by telling me that someone could use a floppy to boot into linux...

yeah...

---

### Post by Efros on 2007-04-17
DOS was just CP/M rejigged and spruced up a bit, and I dont think linux is anything like it, I may find it easier if it was!

---

