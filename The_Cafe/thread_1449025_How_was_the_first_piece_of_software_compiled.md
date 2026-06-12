---
title: "How was the first piece of software compiled?"
date: 2010-04-07
forum: The Cafe
---

### Post by tica vun on 2010-04-07
I just realised this problem when I was reading about the history of GNU and Linux just now: The Linux kernel wasn't self-hosted (ie, couldn't be compiled from Linux itself) until version 0.11 - until then, it could only be built from another operating system. This kind of problem can be traced back to the first universal computing devices. So what compiled the first compiler? :|

---

### Post by Phrea on 2010-04-07
In the beginning there were no compilers or languages to speak of, there was machine language, I think it just evolved from there.

Post helpful? Doubt it, but you could look up machine language and go from there.

---

### Post by Maheriano on 2010-04-07
1s and 0s with punch cards I would say.

---

### Post by undecim on 2010-04-07
First, it was stuff like punchcards and everything that had to handle those was completely hardware-based.

When they had the first x86 computer like we have today, they just had to write machine code directly.

---

### Post by doas777 on 2010-04-07
well, unix was special because it was portable from system to system. all you needed was a C compiler with a small amount of code written in the platforms native assembler language, which was converted to machine code (raw binary). before that, each platform (MIPS, Alpha, and later x88/86), had it's own assembly and machine code dialect, so to write code for the platform you had to use the write assembler.
with unix however, only the very bottom layer of the compiler is written in a platform specific way, so that that little bit of code was all you needed to change to port unix to an new platform. the rest could be compiled up.  

hth

---

### Post by whoop on 2010-04-07
Before punch card's, you had to "program" the actual circuit boards. So you basically had to build a motherboard to make a specific program. 
Insects would crawl into the (hot) circuitry and short circuit the system (stuff was not as stable then). This was the first actual occurrence of a "bug", probably why it is called a "bug" :)

Stuff just evolves, the first C++ compiler was written in and compiled with C, it had to be (the chicken and the egg). The first C compiler was possibly written in assembler or something. Also think about managed code, the compiler for C# is (now) managed code; how is that possible? Same logic, the first C# compiler was a bit code program (not managed at all). :)

---

### Post by fatality_uk on 2010-04-07
[http://en.wikipedia.org/wiki/Compiler](http://en.wikipedia.org/wiki/Compiler)

Compilers have been around a long time. I remember even punch card systems even had a sort of compiler, from what I was told by Brian Drinkell, a former colleague who worked at IBM in the 60's

---

### Post by steveneddy on 2010-04-07
You either wired the "computer" for a specific function or actually flipped a few switches to perform a task - probably only one of just a few tasks possible on an early computer.

Don't forget to let the tubes warm up.

---

### Post by fatality_uk on 2010-04-07
> **steveneddy said:**
> You either wired the "computer" for a specific function or actually flipped a few switches to perform a task - probably only one of just a few tasks possible on an early computer.

Don't forget to let the tubes warm up.

Tubes, YIKES!!!

Mind boggling the progress since the 60's!!! Multi core 32nm processors

---

### Post by phrostbyte on 2010-04-07
> **whoop said:**
> Before punch card's, you had to "program" the actual circuit boards. So you basically had to build a motherboard to make a specific program. 
Insects would crawl into the (hot) circuitry and short circuit the system (stuff was not as stable then). This was the first actual occurrence of a "bug", probably why it is called a "bug" :)

Stuff just evolves, the first C++ compiler was written in and compiled with C, it had to be (the chicken and the egg). The first C compiler was possibly written in assembler or something. Also think about managed code, the compiler for C# is (now) managed code; how is that possible? Same logic, the first C# compiler was a bit code program (not managed at all). :)

The Mono people got away without having to ever write an unmanaged compiler by bootstrapping on Microsoft's compiler. :P

---

### Post by Khakilang on 2010-04-07
Once upon a time they have all those tube and valve that connect together that cover the entire floor and they have only 2 keys that is 0 and 1 in a set of 8 that make a character. And this character was made into a programming language. At first they don't know what to call it so they say its a language from a machine and so the term machine language.

---

### Post by whoop on 2010-04-07
> **phrostbyte said:**
> The Mono people got away without having to ever write an unmanaged compiler by bootstrapping on Microsoft's compiler. :P
Probably.... That's cheating ;)

---

### Post by J V on 2010-04-07
> **whoop said:**
> Before punch card's, you had to "program" the actual circuit boards. So you basically had to build a motherboard to make a specific program. 
Insects would crawl into the (hot) circuitry and short circuit the system (stuff was not as stable then). This was the first actual occurrence of a "bug", probably why it is called a "bug" :)

Stuff just evolves, the first C++ compiler was written in and compiled with C, it had to be (the chicken and the egg). The first C compiler was possibly written in assembler or something. Also think about managed code, the compiler for C# is (now) managed code; how is that possible? Same logic, the first C# compiler was a bit code program (not managed at all). :)
Discovery says fireants percieve the electrical signals from equipment as sweetness and eat equipment so this type if bug still exists... But who believes discovery anywho? xD

---

### Post by doas777 on 2010-04-07
> **whoop said:**
> Probably.... That's cheating ;)
mono uses a virtual runtime just like java does, so the runtime is written against the msvcr but takes ms Intermediary Language (a high level assembler). the coder writes in c#, but the compiler builds to MSIL. the virtual machine runtime (the clr) is then jit compiled/interpreted by the crl into win32 executable code.

its no more cheating than anything java or python or scheme do.

---

### Post by phrostbyte on 2010-04-07
> **doas777 said:**
> mono uses a virtual runtime just like java does, so the runtime is written against the msvcr but takes ms Intermediary Language (a high level assembler). the coder writes in c#, but the compiler builds to MSIL. the virtual machine runtime (the clr) is then jit compiled/interpreted by the crl into win32 executable code.

its no more cheating than anything java or python or scheme do.

He means they are cheating because they got to use Microsoft's already existent C# compiler to bootstrap their own C# compiler. 

Mono's C# compiler is fully written in C#. Microsoft's is not by virtue of being the first C# compiler. 

Sucks for them. An interesting consequence of Mono's compiler being in C# is they can create an .NET API for controlling it. And that's how the "csharp" command was created. :P

---

### Post by tom66 on 2010-04-07
Many compilers started off as assembly or binary code, hand translated from C or another language. They were created sufficiently such that they could compile a basic version of themselves in C (or another language). For example gcc can compile itself.

---

### Post by phrostbyte on 2010-04-07
> **tom66 said:**
> Many compilers started off as assembly or binary code, hand translated from C or another language. They were created sufficiently such that they could compile a basic version of themselves in C (or another language). For example gcc can compile itself.

When you aren't the first compiler for a language, you often gain the ability to bootstrap off another compiler thus bypassing that mess. Since GCC wasn't the first C compiler they could have done something like:

Write GCC (in C) -> Compile GCC in some other C compiler -> Use the compiled GCC to compile itself

---

### Post by doas777 on 2010-04-07
> **phrostbyte said:**
> He means they are cheating because they got to use Microsoft's already existent C# compiler to bootstrap their own C# compiler. 

Mono's C# compiler is fully written in C#. Microsoft's is not by virtue of being the first C# compiler. 

Sucks for them. An interesting consequence of Mono's compiler being in C# is they can create an .NET API for controlling it. And that's how the "csharp" command was created. :P

that is a most kewl factiod. thanks.

---

### Post by cguy on 2010-04-07
What if you want to build a new operating system? Do you have to write your own C compiler in order to create programs for that kernel?
(or whatever language you choose, not necessarily C)

---

### Post by whoop on 2010-04-07
> **phrostbyte said:**
> He means they are cheating because they got to use Microsoft's already existent C# compiler to bootstrap their own C# compiler.

You sir, are right:guitar:

---

### Post by tica vun on 2010-04-07
> **cguy said:**
> What if you want to build a new operating system? Do you have to write your own C compiler in order to create programs for that kernel?
(or whatever language you choose, not necessarily C)

Or you could just port gcc (or another free compiler) to it, or set it up to compile stuff compatible with your OS from Linux.

---

### Post by blur xc on 2010-04-07
This question has been bugging me for some time as well, and it's great to know I'm not the only one-

Let me ask it this way - If I build a new pc from scratch, blank HDD and all- woud it be theoretically possible to "program" it to do something useful without using a single piece of pre-written and/or compiled code?  I suppose that's not exactly fair either, since the mobo will already have its bios written...

BM

---

### Post by doas777 on 2010-04-07
> **cguy said:**
> What if you want to build a new operating system? Do you have to write your own C compiler in order to create programs for that kernel?
(or whatever language you choose, not necessarily C)
not really, unless you are using a new cpu platform (ie: x86, x86_64, DEC Alpha, Mips, etc),

your cpu runs what are called "Instructions", based on mathematical operations in hardware binary, meaning each bit is actually an electrical signal. each cpu platform has it;s own instruction set specific to  the way its circuits are designed. instructions are very very simple things so you need to string many of them together to do anything worthwhile. machine code is binary code that calls a series of instructions from the set.
a compiler converts high level program langagues into machine code that is right for that cpu, so a good compiler for an x86 cpu should be able to compile a kernel and and applications to run on an x86 cpu.

this is all about abstraction, and ease of use. binary is cumbersome, so we look at low level stuff in hex. hex is still clumbsy so we enumerate everything. common tasks call for common algorithms, so we encapsulate functionality in modules, routines, objects, and libraries. 

 for each line of assembler code, many machine code operations can be performed. for each line of cobol we can perform hundreds or thousands of lines of assembler. for each line of C/C++ we can execute many more operations than can cobol and for each line of C#/java/python we can execute many more ops than C/C++. 
with each layer of abstraction, we gain usability, but often at the cost of control. this is cost is most of why C programmers like to make fun of C# programmers like myself, and why the assembler programmers like to make fun of all the rest of us.

it's taken me years to complete my vision of the answer to this question. I remember the night i posed it to my computing mentor, many years ago. I hope it makes sense, 'cause I'm certian that my mentor tried to give me a simillar answer, but I was just not ready for it at the time...

---

### Post by Keith1212 on 2010-04-07
I don't know about how the very first software was compiled but i do know a movie that involve the punch cards mentioned here. 

[http://www.imdb.com/title/tt0168122/](http://www.imdb.com/title/tt0168122/)

That's a move called "The Pirates of Silicon Valley" if you haven't seen it. It an awesome movie and shows some of the first personal computers and the use of punch cards.

---

### Post by lisati on 2010-04-07
> **phrostbyte said:**
> When you aren't the first compiler for a language, you often gain the ability to bootstrap off another compiler thus bypassing that mess. Since GCC wasn't the first C compiler they could have done something like:

Write GCC (in C) -> Compile GCC in some other C compiler -> Use the compiled GCC to compile itself

That's kind of how the BCX dialect of BASIC works: write the translator in BCX, run it through an existing version of itself, and then pass the output through your favourite C compiler, and, voila, you have a new version of BCX. Yes, it's Windows software, and I haven't used it for a while.

I've actually used machines which use punched cards - there are a handful of forum users who have. Great fun if you drop the deck of cards and it gets out of sequence!


p.s. To the script kiddy and/or malware in Ohio who has been trying to hack my email server: bad luck, you've been spotted, blocked and reported. (As far as I can make out, it's not a current registered user of the forums.)

---

### Post by whoop on 2010-04-07
> **blur xc said:**
> This question has been bugging me for some time as well, and it's great to know I'm not the only one-

Let me ask it this way - If I build a new pc from scratch, blank HDD and all- woud it be theoretically possible to "program" it to do something useful without using a single piece of pre-written and/or compiled code?  I suppose that's not exactly fair either, since the mobo will already have its bios written...

BM
No, I'm guessing the end result should be a program on disk. You need software to be able to write to that disk. Now a punch card on the other hand ;)

---

### Post by Lightstar on 2010-04-07
The aliens did it!!1!!11!!!one!111

AHHHHHHHHHHHHHHHHHHHHHHHHHHHHH!

---

### Post by swoll1980 on 2010-04-07
The guys that wrote C wrote the C compiler in assembly, then wrote it in C, then compiled the C version of the C compiler on the the assembly version of the C compiler.

---

### Post by chillicampari on 2010-04-07
It might be in one of the Grace Hopper papers, but I'm not finding full text online.

---

### Post by samjh on 2010-04-08
> **swoll1980 said:**
> The guys that wrote C wrote the C compiler in assembly, then wrote it in C, then compiled the C version of the C compiler on the the assembly version of the C compiler.

Alliteration FTW! :P

How fast can you say it? ;)

---

