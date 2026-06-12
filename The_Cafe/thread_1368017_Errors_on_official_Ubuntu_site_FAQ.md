---
title: "Errors on official Ubuntu site FAQ"
date: 2009-12-30
forum: The Cafe
---

### Post by Fri13 on 2009-12-30
Hi! 

The humanity is that we try to preserve the truth and protect it from lies. Isn't it? We do not lie to each other, we do not try to use those who do not know complex technology as advantage for us? It is sad that some companies can hide the real truth behind nice curtains about humanity if they do not even follow it themself. 

I have now years watched the Ubuntu site of [https://help.ubuntu.com/8.04/installation-guide/powerpc/what-is-linux.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/what-is-linux.html) and I have waited that being fixed. But now I want to ask is it going to be fixed, but I dont think so because two things. 1) Ubuntu people does not see problems at it (because 2). 2) The Ubuntu people are fans of GNU and does not care about technical correctness but simplicity.

Move this to correct subforum if needed, but this is about improving forum and the Ubuntu community itself! 

This is only about technology and history of operating systems, not about ideology, fame hunting etc. Simply, it is about humanity to next generations to preserve the truth.

**[SIZE="5"]Basic reading[/SIZE]**

[http://www.usenix.org/publications/login/2006-04/openpdfs/herder.pdf](http://www.usenix.org/publications/login/2006-04/openpdfs/herder.pdf)

[http://www.amazon.com/gp/reader/0130313580/ref=sib_dp_pt#reader-link](http://www.amazon.com/gp/reader/0130313580/ref=sib_dp_pt#reader-link)

[http://www.gridbus.org/~raj/microkernel/chap2.pdf](http://www.gridbus.org/~raj/microkernel/chap2.pdf)

[http://www.topology.org/linux/lingl.html](http://www.topology.org/linux/lingl.html)

[SIZE="4"]+ The Attachments[/SIZE] 

**[SIZE="5"]The common errors by the people and on the Ubuntu site[/SIZE]**

[B][LIST=1]
[*]Linux is an operating system: a series of programs that let you interact with your computer and run other programs.
[/LIST][/B]

Linux kernel is the operating system in _the software system_. The operating system _is not_ a series of programs and user does not interact the hardware (like CPU, Memory, Harddrives) or the operating system but the system programs and application programs. 

[B][LIST=2]
[*]An operating system consists of various fundamental programs which are needed by your computer so that it can communicate and receive instructions from users; read and write data to hard disks, tapes, and printers; control the use of memory; and run other software.
[/LIST][/B]

The operating system _does not_ consist from various programs. None of the *system programs*, *software libraries* or *application programs* could work on the hardware _without the operating system_, if those softwares does not include the operating codes of hardware what the operating system does. 
The operating system does not get commands from the user straight. The user interact with the system programs like command interpreters (bash etc) or window managers and application programs (Xorg+Windowmaker+Firefox) and those softwares interact through other softwares to the operating system what controls all them. The operating system only task is to operate the hardware and software; memory, filesystems, processes, networking and so on. And Offer them to the each others.  

[B][LIST=3]
[*]The most important part of an operating system is the kernel. In a GNU/Linux system, Linux is the kernel component. The rest of the system consists of other programs, many of which were written by or for the GNU Project.
[/LIST][/B]

That is assumption what is based to server-client architecture. There are different architectures for operating systems. 1. Monolithic 2. Server-Client 3. Layered.

**The monolithic** operating system is a kernel alone. The kernel has all the operating system features inside of it. The monolithic was first a single binary running in kernel space. But later they got modular structure where some functions of the operating system can be de-attached when not needed and attached back when needed. The mechanism is in the binary level and not architecture level. 
The mounted module works like it would never be de-attached. None of the other softwares in the software system does not belong to the operating system. Monolithic kernel is the *original* way to build the operating system and offers all system calls alone to the other sofware (system call wrappers are not part of the operating system). 
The Monolithic kernel runs alone in *supervisor mode*. _***The operating system is the monolithic kernel***_ (example monolithic operating systems are *Linux, FreeBSD, NetBSD, OpenBSD, DragonBSD, SunOS, HP-UX, AIX, PARAS*).

**Server-Client** operating system is kernel + servers/modules. The reason to develop this architecture was to build up a secure, stable and easier developed operating system, it being still slower than monolithic. The monolithic operating system was sliced to pieces. There was left a tiny kernel what only included basic features of the OS. And every other OS part (device drivers, filesystems, networking etc) were modules what were running alone and offered the system calls for system libraries, system programs and application programs, for all the other software on the software system. The original (pure) idea of server-client architecture was that every module is moved to other address space in supervisor mode like the kernel, and every module is running in protected process thread as the client to the microkernel acting like the server. _***The operating system is microkernel + modules.***_ (example of server-client operating systems are *Hurd* (microkerne is GNU Mach), *XNU* (Microkernel is Mach), *NT*, *Minix*, *MkLinux* (Microkernel is Mach 3.0), *KFreeBSD*)

**The Layered** operating system is like a server-client but every module is top of each other. Every layer offers own services to one on top of them and ask functions from one under them. The microkernel running bottom of all OS parts.

The _marketing propaganda_ of **Hybrid kernel** is actually a Server-Client operating system. But it does not have a the original structure of it, but some (or all) modules are moved back to the same address space where the microkernel is running. Idea was to have a as fast OS as the monolithic was but still secure and stable as the original server-client had. The operating system *still has the microkernel* and the kernel is *not changed at all* to be such it would gain a new architecture.
One point MS and Apple marketed their OS's NT and XNU as hybrid kernels but at least MS has stopped it and says NT has a microkernel. Apple still continues calling XNU as hybrid, even that the XNU has the Mach 3.0 microkernel.    

[B][LIST=4]
[*]Because the Linux kernel alone does not form a working operating system, we prefer to use the term “GNU/Linux” to refer to systems that many people casually refer to as “Linux”.
[/LIST][/B]

Wrong assumption! The linux is *a monolithic kernel* and _not microkernel_. The Linux **is** whole operating system **alone**. It does not need any software and especially from the GNU project. The GNU Project has their own OS under development, called Hurd. The Hurd is not a kernel but the operating system whats kernel is GNU Mach and it is a microkernel. The Linux is the name of the operating system what is monolithic kernel. And by GNU/Linux propaganda what Canonical continues to spread, the Linux has needed to get a synonym "Linux kernel" what really still is same as Linux.

[B][LIST=5]
[*]Linux is modelled on the Unix operating system. From the start, Linux was designed to be a multi-tasking, multi-user system. These facts are enough to make Linux different from other well-known operating systems. However, Linux is even more different than you might imagine. In contrast to other operating systems, nobody owns Linux. Much of its development is done by unpaid volunteers.
[/LIST][/B]

Linux is monolithic kernel what is the original way to build up a operating system. And it is 4th Generation Unix-like operating system. And most of the development of the Linux operating system (it is still the kernel) is done by corporations like RedHat and Novell. Only few % comes from unpaid volunteers. It still does not change that Linux is the operating system who no one owns. Because GPL license is protecting it. **Kudos for that**. 

[B][LIST=6]
[*]Linux is also less likely to crash, better able to run more than one program at the same time, and more secure than many operating systems. With these advantages, Linux is the fastest growing operating system in the server market. More recently, Linux has begun to be popular among home and business users as well.
[/LIST][/B]

Linux really is secure operating system but there is a more secure version of it, called SELinux (it is Linux but to be accurate, it is SELinux). And Linux has gained very strong support for supercomputers and normal servers because of it's stability and speed. 
The speed is very important feature of the operating systems for supercomputers and thats why the monolithic operating system still is best choice to the supercomputer. 

Thats why GNU has not got their own OS Hurd to be developed because it is much slower on servers because it has a server-client architecture and even has bad choice to use Mach 3.0 as their microkernel (RMS has said so) because they did not get own kernel working.

And Linux has got foot between door on cellphone markets as well. Linux is the operating system powering the Android and Maemo and many other cellphone *software platforms*. That makes Linux one of the greatest OS of the time.
And thing what GNU project has done helping it to happend, is the GPLv2 license what Linus Torvalds used instead his own.

   But that is not a reason to call it GNU/Linux at all, because the GPL license does not make purpose for it. Otherwise we should call softwares like Firefox and OpenOffice as GNU/Firefox and GNU/OpenOffice etc.

The whole GNU/Linux is biased only about GNU's unlogical ethics and fame hunting for operating system what the project itself couldn't develop. The computer science is very clear about the operating system functions, it is pure science and mathematic, no ideological about freedom and licensed etc. It is software what humans has developed and what they teach on universities (like the one where Linus Torvalds got his degree or where Andrew S.Tanenbaum teaches the operating systems functions).

And some people tries to make it easier to understand by calling all kernels as "only the kernel" without actually understanding that there is big difference between microkernel and monolithic kernel. 
And some of the same people have tried to show that what you see in the screen, is the operating system. They try to keep everything so simple that the truth is hided behind assumptions and assumptions turns as truth and it overrules the technology and science. It is very difficult for normal user to understand the software because they can not touch it, they can not see it how it works and they do not understand the software meaning.

Maybe the biggest fight about GNU/Linux vs Linux has gone about how popular the name is among normal people and technical people. And about the stupid unlogical reasons how the Linux needs GNU software because other sofware does not run without GNU software. It is like saying that every GNU software should be Intel/GNU or AMD/GNU or x86/GNU and PPC/GNU because GNU software does not run without CPU. Or that the GNU software should be called as ElectricityCompany/GNU because the computer does not run without electricity. 
     And in the end we just would end up to situation calling it Electricity/COmputerManufacturer/Linux/GNU/Xorg/KDE/ because without those you could not run the Kmail or Kopete. The GNU project is important, but it has nothing to do with the operating system. As far Ubuntu is not ran by GNU's own operating system Hurd, the operating system has nothing to do with the GNU project. 

This just _does not make it less important_ how great softwares the GNU project has developed. Even that software *was libre before* the GNU project existed or RMS studied on MIT. It is just great how GNU project has kept the software as libre and did not allow it to be fallen in total control of big corporations. Kudos from THAT!

If Canonical wants to follow their own Code of Conduct and offer humanity to everyone one, without being biased. They need to stop using the GNU/Linux -term. It is pure lie and _lies are not good base for the freedom_ and especially for the truth. 

    So give the credit for them who deservers it and for what they have done. 
That means Linus Torvalds is the founder of the Linux operating system and Richard Stallman is the founder of GNU Project to protect libre software. 
And Canonical to *package* the Linux operating system, GNU software and other open source softwares so we can have such software system that is easy to use.

---

### Post by Bachstelze on 2009-12-30
[img]http://upnextinsports.com/wp-content/uploads/2009/09/128925836006849814.jpg[/img]

---

### Post by Mighty_Joe on 2009-12-30
[IMG]http://drunkenachura.files.wordpress.com/2009/05/dude-wait-what.jpg[/IMG]

---

### Post by anantshri on 2009-12-30
I would just ask you to think it this way.

Linux Kernel and litrally mean kernel can't do anything or rather a user can't do anything in case they don't get atleast a shell.

and ya for your pretty reference that shell is a GNU project.


GNU project HURD was working on creating an OS and it still is but that OS lacked just the kernel and Linux project just had the kernel and nothing else.

hence the two projects (two different projects with OS development in mind) were combined and hence GNU / Linux was formed.

hoep this helps solving your query.

---

### Post by wojox on 2009-12-30
So why don't you join the documentation team ? I'm posting this from my new Wii gaming system. Santa loves me cause I don't bitch about stupid sh¡t.

---

### Post by The Real Dave on 2009-12-30
Ubuntu - Linux for Human Beings.

Were trying to attract people to this OS for its simplicity.....

---

### Post by hessiess on 2009-12-30
Check you definitions because they are flawed, an operating system is a collection of programs consisting of a kernel that handles the lowest level abstraction, and a number of programs which run on top of in providing higher levels of abstraction and allowing the user to interact with the system.

GNU/Linux is correct, the OS is a combination of the GNU userland and the Linux kernel.

---

### Post by Methuselah on 2009-12-30
**Linux** is an operating system.
**Distributions** of linux are more often than not GNU linux distributions.
IMO, Ubuntu is quite correct in saying they are offering a GNU/Linux distribution.

Though I also agree with the arguments that say everyone could have some attribution (GNU/Linux/Mozilla/Xorg distribution and I still left people out).
However, the GNU people seem to care and no-one else really does so we have GNU/Linux.

People often imgine that Linux is EVERYTHING they install and Torvalds wrote EVERYTHING which is IMO, more incorrect than saying distributions are GNU/Linux.
Linux would not be usable as a desktop operating system without contributions from GNU or BSD or somewhere.

---

### Post by Bachstelze on 2009-12-30
[img]http://img138.imageshack.us/img138/4206/seriouslyo.jpg[/img]

---

### Post by Hyporeal on 2009-12-30
The statements from the Ubuntu documentation are based on widely accepted definitions. The use of the term "operating system" to refer to a kernel (monolithic or not) along with a collection of programs is decades old. I do not think the Ubuntu documentation is a good place to reform the English language, no matter how compelling the argument may be.

Also, the poll is utterly incomprehensible.

---

### Post by Paqman on 2009-12-30
Any chance we could we get a 50-word bullet point version of the OP? Eschew gratuitous obfuscation, I implore you.

---

### Post by Fri13 on 2009-12-30
> **anantshri said:**
> I would just ask you to think it this way.

Linux Kernel and litrally mean kernel can't do anything or rather a user can't do anything in case they don't get atleast a shell.


Without operating system, you can not run the shell. Bash does not work without operating system. The INIT is first system program what gets started what is not part of the operating system. Linux offers you the login screen and from that you can login and OS starts the corresponding shell for your account. When booting in single mode, the login is not needed because your OS is ordered to start the shell with root rights. 

> 
and ya for your pretty reference that shell is a GNU project.


Bash is GNU project, but bash is not part of the operating system. Bash is still just normal system program what is running top of the operating system.

> 
GNU project HURD was working on creating an OS and it still is but that OS lacked just the kernel and Linux project just had the kernel and nothing else.


Wrong. Hurd is a operating system of server-client architecture. Hurd use a microkernel called GNU Mach. You can not replace the microkernel with the monolithic kernel because monolithic already has all the OS functions in itself. Microkernel only has few basic functions and all other OS functios are on modules.  

> 
hence the two projects (two different projects with OS development in mind) were combined and hence GNU / Linux was formed.


That is just pure propaganda. GNU has nothing to do with the Linux operating system, unless you count that GPL license is enough to call Linux as GNU/Linux. With same logic it is GNU/Firefox, GNU/OpenOffice, GNU/F-Spot, GNU/Amarok and so on. Seems you did not even understand that Linux is not a microkernel but a monolithic kernel what makes it a complete operating system alone, without any code from GNU project.

> hoep this helps solving your query.

Not truth, but just spreading more GNU propaganda ;)
Technology is very clear, Linux kernel is the operating system because Linux is not a microkernel (or Exo- or Nano-kernel)

---

### Post by RiceMonster on 2009-12-30
tl;dr

---

### Post by Exodist on 2009-12-30
> **Hyporeal said:**
> The statements from the Ubuntu documentation are based on widely accepted definitions. The use of the term "operating system" to refer to a kernel (monolithic or not) along with a collection of programs is decades old. I do not think the Ubuntu documentation is a good place to reform the English language, no matter how compelling the argument may be.

Also, the poll is utterly incomprehensible.


Most people call the engine in a vehicle a motor which is technically wrong.
A motor gets its power from an external source, a engine creates its own power.
Though many say both, calling a car engine a motor is looked down upon by professionals and those who are more knowledgeable. 

Same can be said about that documentation, its very unprofessional.

So the question at hand is, does ubuntu wish to look professional or look like a handful of nubs has thrown it together? Not saying anything bad about anyone here, this is just a little constructive criticism.

Now the poll above is irrelevant to the topic and does not make any sense. 

- Exo

---

### Post by Fri13 on 2009-12-30
> **hessiess said:**
> Check you definitions because they are flawed, an operating system is a collection of programs consisting of a kernel that handles the lowest level abstraction, and a number of programs which run on top of in providing higher levels of abstraction and allowing the user to interact with the system.

GNU/Linux is correct, the OS is a combination of the GNU userland and the Linux kernel.

Sorry but you are making full mistake there. You are talking about microkernel, not about monolithic kernel.

You are making huge assumptions about GNU. The monolithic kernel is the complete operating system alone. It has all the OS features what microkernel does not have. 

The border between operating system and the system is the system calls. You can even extend the system calls what OS offers by writing own system call wrapper what captures the wanted commands from programs and pass them with own commands to the operating system. 

The Linux is not a microkernel, if it would be, what you say would be correct. But there is huge difference between monolithic and microkernel. If you even would go to basic computer science lessons about operating systems on the university, you would get information from basic study books like "Modern Operating Systems" that monolithic kernel like Linux, is the operating system and it should not be mistaken to microkernel what is just a most important part of the operating system, the lowest level of the operating system.

There is a link what you can check out. Use your logic and skills to read them. You only find out that Linux kernel is the operating system and GNU has nothing to do it.

If you can not open PDF files, here is one quote from computer science article (these defines the computer science as well)

> In our view, the only way to improve operating system reliability is to get rid of the model of the operating system as one gigantic program running in kernel mode, with every line of code capable of compromising or bringing down the system. Nearly all the operating system functionality, and especially all the device drivers, have to be moved to user-mode processes,
leaving only a tiny microkernel running in kernel mode. Moving the entire operating system to a single user-mode process as in L4Linux [4] makes rebooting the operating system after a crash faster, but does not address the fundamental problem of every line of code being critical. What is required is splitting the core of the operating system functionality—including
the file system, process management, and graphics—into multiple
processes, putting each device driver in a separate process, and very tightly controlling what each component can do. Only with such an architecture do we have a chance to improve system reliability.

The reasons that such a modular, multiserver design is better than a monolithic one are threefold. First, by moving most of the code from kernel mode to user mode, we are not reducing the number of bugs but we are reducing the power of each bug to cause damage. Bugs in user-mode processes have much less opportunity to trash critical kernel data structures
and cannot touch hardware devices they have no business touching. The crash of a user-mode process is rarely fatal, whereas a crash of the kernel always is. By moving most of the code out of the kernel, we are moving most of the bugs out as well. 

Second, by breaking the operating system into many processes, each in its own address space, we greatly restrict the propagation of faults. A bug in the audio driver may turn the sound off, but it cannot wipe out the file system by accident. In a monolithic system, in contrast, bugs in any function
can destroy code and data structures in unrelated and much more critical functions. Third, by constructing the system as a collection of user-mode processes, the functionality of each module can be clearly determined, making the entire system much easier to understand and simpler to implement. In addition, the operating system’s maintainability will improve, because the
modules can be maintained independently from each other, as long as interfaces and shared data structures are respected.


Do you understand anything about that? Linux is the monolithic operating system what is the architecture what many believes to be flawed. There are multiple different architectures for the operating systems and they build up the operating system different ways. The kernel is not always just a kernel and operating system is not always a kernel + something else.

That is one biggest propaganda what GNU has got people to believe same time as the 90's most OS's were basing the Server-Client architecture.

Here is other quotation what you can find out, even that I dont believe you can understand it because you say that Linux is just a kernel and GNU/Linux is the operating system:

> 
On top of the operating system is the rest of the system software. Here we find the command interpreter (*shell*), compilers, editors and similar application independent programs. It is important to realize that these programs are definitely not part of the operating system, even though they are typically supplied by the computer manufacturer. This is crucial, but subtle, point. The operating system is that portion of the software what runs in **kernel mode** or **supervisor mode**. It is protected from user tampering by the hardware (ignoring for the moment some of the older microprocessors that do not have hardware protection at all). Compilers and editors run in **user mode**. If a user does not like particular compiler, he is free to write his own if he so chooses; he is not free to write his own disk interrupt handler, which is part of the operating system and is normally protected by hardware against attempts by users to modify it.
     Finally, above the system programs come the application programs. These programs are written by the user to solve their particular problems, such as commercial data processing, engineering calculations, or game playing.


Can you tell me how (maybe) the most respected computer science professor who has wrote over 125 scientific articles, few dozen books for teaching purposes for universities about operating systems and developed even own operating system (what Linus Torvalds used as example and reason to start the Linux operating system project) and helped to develop few other operating systems and still teach and writes books and articles and develops operating systems (he even got now about 5 million euros payment from EU to develop more secure operating system from Minix) is so badly wrong that the stuff what he writes, is not true in computer science? Even that many operating system lessons and theories are based to his work? :confused:

Only true GNU fan can denied that Linux kernel is the operating system while passing the computer science and continue saying that GNU/Linux is the operating system while Linux is just kernel for it. :)

---

### Post by Fri13 on 2009-12-30
> **Exodist said:**
> Most people call the engine in a vehicle a motor which is technically wrong.
A motor gets its power from an external source, a engine creates its own power.

Actually Motor generates the physical motion of any other energy source (was it on any other form, gasoline, sun, wind, heat etc). If following the latin "motor = to set in motion". The engine is a synonym for the motor, but at least wiktionary says that engine was used for motors what were moving the vehicles and are moving itself as well. So in the car/boat/train it is the engine, but on factory and other places where it is stationary it is the motor.

> 
Same can be said about that documentation, its very unprofessional.


The documentation tries to please GNU and Debian people but fails totally about the technical correctness being against the computer science. It just makes it harder for new users to actually starting to read or study computer science when the biased and used "operating system" definition is used on ubuntu does not fit at all to the science books. 

> So the question at hand is, does ubuntu wish to look professional or look like a handful of nubs has thrown it together?

It is not about just look, but about the correctness for later use and to understand the history as well. As example (it is bad but it is just a example) the documentation now is like saying "5+5=25" They want to mean * with the + but they have very small error right there. And even that the mistake is very small and it does not matter so much when doing just basic calculations with few numbers. But think about how impossible it comes to learn calculating when talking about astronomy or theoretical physics? Without forgetting how difficult it would be understand the calculations what others have made in the past? 

> 
Now the poll above is irrelevant to the topic and does not make any sense. 


The idea in the poll is not about asking straight, but asking just what it is asking. Should we try to pursue the truth or not? We are now talking about computer science, it is basicly mathematics and electricity engineering where every thing can be explained. And especially because we are talking now about stuff what humans have build, not some kind mystical device what is black box and we do not know how it works or stuff happening lightyears away from earth.

For normal user the software is totally mystical thing. It is like magic how you can just edit photos, play music, browse the Internet and so on. But none of those are real reasons why we should use wrong way the terms of the technology what is still 100% valid as it was 50 years ago and what is still used and developed right now and in future!

I, do not care what is the public opinion about operating system because it is opinion based marketing. And their idea is to sell stuff and gain better fame among their users. They do not care about truth but that they can exist and people remembers them when doing next shopping. For normal user it is just same thing is the Ubuntu called as software system or as the web browser. They just want to get the stuff done.

But does it matter for people who actually develops the technology for them how the technology is used? Yes! Does it matter for next generations to understand the past so they can work in the future? Yes!

This is now the situation where the marketing and fame hunting has got us to situation where technology and logic does not exist. And because most users would need to relearn and admit the truth how the technology really works, the propaganda what they have thought as the truth, becomes such big obstacle for them that they need to denied the truth totally.

For many it might be a shock that Ubuntu is using same OS as any other linux distribution. The ubuntu is not a special OS out there but it use same OS as Fedora or Debian or Gentoo! Thats why we have the term "distribution" what is explaining the idea of the open source and libre operating system running all those softwares in the software system what allows us to make all kind nifty things on the computer.

---

### Post by Exodist on 2009-12-30
> **Fri13 said:**
> Actually Motor generates the physical motion of any other energy source (was it on any other form, gasoline, sun, wind, heat etc). If following the latin "motor = to set in motion". The engine is a synonym for the motor, but at least wiktionary says that engine was used for motors what were moving the vehicles and are moving itself as well. So in the car/boat/train it is the engine, but on factory and other places where it is stationary it is the motor.
TO clarify, engines generate their own motion from other inert material. Such as gas or diesel in the automotive world. A motor is thrown into motion from a volatile energy source like electricity.

---

### Post by Fri13 on 2009-12-31
> **Exodist said:**
> TO clarify, engines generate their own motion from other inert material. Such as gas or diesel in the automotive world. A motor is thrown into motion from a volatile energy source like electricity.

Motors generates physical motion from other energy sources, like gasoline, electricity, heated water etc. Just like engines does as well. But motor does not move from it's place, engine moves itself. 

That is at least what wikipedia, wictionary and my old dictionarys says (from 1952's and 1993). They are same but reason for differences in terms does come if the machine what generates the motion, move or not itself.

And on many other languages than english, there is no different words for engine and motor but they are both used with same word.

---

### Post by anantshri on 2010-01-17
Hi Fri13

I appreciate your effort, knowledge and understanding of the basic concepts and habbit of providing proves of your talks.

But i think of just few things

1. If you actually want to focus on this specific piece of discussion then i would suggest placing your talk on a wider and more knowledgable community such as wikipedia
[http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy](http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy)

regarding tanenbaum and torvolds i would suggest you to read (which i can assume you have already read)
[http://en.wikipedia.org/wiki/Tanenbaum-Torvalds_debate](http://en.wikipedia.org/wiki/Tanenbaum-Torvalds_debate)


2. On a side not i would like to ask the whole ubuntu forum, making one software name change to something else, might make a lot of difference to someone but not to the whole community.


and what i would like to request is avoid going into flame wars and secondly if you want to make an impact go for a widest reach possible. such as wikipedia discussion or go directly on blog and contact every big player to contribute on that.

---

