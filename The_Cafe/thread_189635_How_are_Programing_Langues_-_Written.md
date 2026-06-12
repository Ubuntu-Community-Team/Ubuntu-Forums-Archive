---
title: "How are Programing Langues - Written?"
date: 2006-06-05
forum: The Cafe
---

### Post by v8YKxgHe on 2006-06-05
Hey,

Don't know if this is the right place, but i've always wondered how are programming languages written? 

As the CPU only reads binary ( Correct ? ) does that mean someone has had to convert the languages ( when compiled ) to binary? But then, how do they code a program to convert something to binary for the cpu to read? Would they have to code there program in binary? 

Geee i'm going mad - My explination/idea of it is most probaly complty wrong and so far off, so would someone enlighten me on how programming langues are written?

---

### Post by Kimm on 2006-06-05
I'm not quite sure how Programming languages are written, but I can assure you that the compilers arnt written in Binary :P
I belive a combination of C and Assembly is the most common, but I have seen compilers written in VB6

> 
As the CPU only reads binary ( Correct ? ) does that mean someone has had to convert the languages ( when compiled ) to binary?


The compiler translates the code to binary, yes.

Not all programming languages are binary though, some are byte-code compiled (sometimes also refered to as binary, although all files are in fact binary) and some scripting languages.

Some byte-code languages are Java and C# (used with Mono or .NET), Python can also be bytecode compiled using psycho. Python is normaly used as a scripting language (this means that the program is acctually a textfile that is then translated by another program)

---

### Post by Engnome on 2006-06-05
There is a programming section.

There is actually a way to code binary. Assembly language is like writing binary I think. In the begining all software was written in assembly type languages. Not really sure about all this as I only do more high level languages and havent been around that long.

Read more: [http://en.wikipedia.org/wiki/Assembly_language](http://en.wikipedia.org/wiki/Assembly_language)

---

### Post by G Morgan on 2006-06-05
Most languages are built upon a previous language. A lot modern languages are built using C++ including Java. Originally I suppose there must have been a language written directly in binary which then became assembler and was continually abstracted away over the years.

---

### Post by ComplexNumber on 2006-06-05
[quote=G Morgan]Most languages are built upon a previous language. A lot modern languages are built using C++ including Java. Originally I suppose there must have been a language written directly in binary which then became assembler and was continually abstracted away over the years.[/quote] and C++ was built upon C, and C was built from BCPL(i remember when acornsoft released it for the BBC micro in the mid 1980s), and BCPL was built from PL(i think), and PL was built from.....

---

### Post by ruhar on 2006-06-05
At the heart is the compiler.  The compiler lexically parses your code written in a high level language (e.g., Java, C/C++, etc.) and runs your code through its grammar rules to determine whether or not the high level code is syntactically correct.  Once verified as syntactically correct, the compiler will then translate the high level code into either an intermediary language (as is the case for Java byte code or C# IL ) or into object code.  Depending on the language/compiler, the next step could include dynamically library linking.  For C/C++ the next step is to generate machine instructions geared at a particular processor's instruction set (each compiler must know what processor it is targeting ahead of time.)  For Java and C# the next step in the translation comes when the code is actually executed by the runtime environment (e.g., JVM or CLR.)  In this case the JVM or CLR is geared towards a particular processor's instruction set.

---

### Post by G Morgan on 2006-06-05
[QUOTE=ComplexNumber]and C++ was built upon C, and C was built from BCPL(i remember when acornsoft released it for the BBC micro in the mid 1980s), and BCPL was built from PL(i think), and PL was built from.....[/QUOTE]

Exactly that was my point. I do wonder what would happen if all the code in the world was eliminated. How long would Micros~1 take to produce an OS if written in assembler.

---

### Post by v8YKxgHe on 2006-06-06
Thanks for the responses guys,

But my main confusion is still there, if the CPU only reads binary/byte-code - How the *beep* do you code a compiler ( for the lowest languages, ASM for example ) ?? It would have to be written in binary, surely? as it can't be higher than ASM. But then again, who programmed the CPU to understand what 0001 means?! 

lol, it's like what came first the chicken or the egg!!

---

### Post by Lux Perpetua on 2006-06-06
This sequence is hypothetical and not based on history, but hopefully it will clear up your confusion. 

1. You write an assembler - as simple and basic as possible - in machine code. 
2. You write a compiler - as simple and basic as possible - in assembly, using your assembler. (You're not even implementing C at this point; just a very simple language.)
3. You use your rudimentary compiler to write a good assembler. 
4. You use the good assembler and your basic compiler to write a real compiler, say, a C compiler. 
5. A C compiler is already powerful enough to allow you to implement a lot of interesting languages (many of which are, indeed, implemented in C). 

No step in that process is obscenely difficult because it is only a slight improvement on the previous steps.

---

### Post by Kimm on 2006-06-06
Lux Perpetua, your pretty close. You might even be spot on.

The fist langauge was indeed written in Binary (by a woman, hard to believe when the computer marked today is so male dominant).
The fist language was Assembly.
From assembly other languages grew and I do believe that you can acctually map languages in something similar to a "family tree"

> 
Assembly language is like writing binary I think


It is not, even though Assembly is very low level, its still far from binary.

Binary is a series of 1's and 0's while assembly can look something like this:

```
dosseg
.model small
.stack 100h

.data
hello_message db 'Hello, World!',0dh,0ah,'$'

.code
main  proc
      mov    ax,@data
      mov    ds,ax

      mov    ah,9
      mov    dx,offset hello_message
      int    21h

      mov    ax,4C00h
      int    21h
main  endp
end   main
```

That will display "hello world" on an x86 computer (Intel or AMD)

---

### Post by G Morgan on 2006-06-06
I don't think the first language was written by a Woman. It was called Ada because that was the name of the proposed operator for Babbages Difference Engine. It may have actually be written by a Woman as well but the Ada bit definately refers to Babbage.

//edit - turns out Ada was the first high level language as opposed to the first language and was named after Ada Lovelace who did indeed create the first programming language by creating the language to be used for the difference engine.//

---

### Post by ComplexNumber on 2006-06-06
[quote=G Morgan]I don't think the first language was written by a Woman. It was called Ada because that was the name of the proposed operator for Babbages Difference Engine. It may have actually be written by a Woman as well but the Ada bit definately refers to Babbage.[/quote] ada was named after ada lovelace (and who also happened to be the daughter of the poet, lord byron). she was meant to be the first programmer.

---

### Post by Kimm on 2006-06-06
> 
//edit - turns out Ada was the first high level language as opposed to the first language and was named after Ada Lovelace who did indeed create the first programming language by creating the language to be used for the difference engine.//


Correct. However it was not Ada Loverlace I was refering too. Atm I cant seem to find her name... but I do belive it was during the secund world war.

(This would be the first person to acctually create a language that would tell a computer what to do (Assembly). Ada never got to implement her ideas on her machine)

---

### Post by IYY on 2006-06-06
> It is not, even though Assembly is very low level, its still far from binary.


It's not *that *far from binary. It is possible for a human to translate assembly to hex (and binary) quite easily.

---

### Post by jdong on 2006-06-06
Programming languages are written in other programming languages. A new version of a compiler is typically written with an older version of the same compiler.

Trying to unwind that stack any more than what I just said just leads to spending intriguing hours over at Wikipedia... better spent not getting carpal tunnel or eye strain :)

---

### Post by pelle.k on 2006-06-06
> who programmed the CPU to understand what 0001 means?!
Now that's where programming ends really, because this is what AMD/intel and friends are resonsible for. This is what they design, circuits. You have a set of combinations in a stream, which the chip (CPU) acts on.
Laying out a circuit, actually feels a little bit like programming; if there is current through this wiring, the transistor opens the flow of electrons in another circuit, and so on - then you have if/else/endif conditianal sort of flow just like in a computer program...
Hardware (it's like a computer program, but you can't reprogram it. just replace the components)
Software (hey, i can change how it works... great)

---

### Post by SuperMike on 2006-06-06
I think I heard that Parrot is a common runtime library that other languages can be built upon, and some people are using Parrot and Perl, together, like an "alphalanguage" (a high-level programming language to make other scripting programming languages) to make new languages. Lua was an example of such a language.

Or am I wrong? Let me know.

---

### Post by yabbadabbadont on 2006-06-06
[QUOTE=Kimm]Correct. However it was not Ada Loverlace I was refering too. Atm I cant seem to find her name... but I do belive it was during the secund world war.

(This would be the first person to acctually create a language that would tell a computer what to do (Assembly). Ada never got to implement her ideas on her machine)[/QUOTE]
I believe you are thinking of Grace Hopper.

[http://en.wikipedia.org/wiki/Grace_Hopper](http://en.wikipedia.org/wiki/Grace_Hopper)

---

### Post by briancurtin on 2006-06-06
damn you beat me. grace hopper is correct

---

### Post by ComplexNumber on 2006-06-06
oops. <please delete>
[]("http://en.wikipedia.org/wiki/Ada_Lovelace")

---

### Post by ComplexNumber on 2006-06-06
[quote=yabbadabbadont]I believe you are thinking of Grace Hopper.

[http://en.wikipedia.org/wiki/Grace_Hopper]("http://en.wikipedia.org/wiki/Grace_Hopper")[/quote]
she wrote the first compiler. not the first language.

---

### Post by Kimm on 2006-06-07
ComplexNumber, without a compiler a language is pretty useless. Ada created the first language which made her the first programmer. But Grace created the first compiler which allowed people to program a computer using something besides pure Binary.

---

### Post by psychicdragon on 2006-06-07
Ada Lovelace actually did not create the first computer program. That distinction belongs to Charles Babbage the creator of the difference engine. Ada simply published some of Babbages programs and later took an interest in the machine. She may of at that time made some of her own programs.

The story of Babbage and his difference engine is quite fascinating. There's a very good book on it called (Shockingly) *The Difference Engine*. It's quite amazing that many of the ideas that still exist in computer science were first conceived in the 19th century.

Anyway, it's fairly safe to say that Babbage was the first programmer.

---

### Post by mips on 2006-06-07
Technically speaking the first person to flip a switch or open/close a gate was a programmer. This does not even have to be computer related.

---

### Post by ComplexNumber on 2006-06-07
[quote=Kimm]ComplexNumber, without a compiler a language is pretty useless. Ada created the first language which made her the first programmer. But Grace created the first compiler which allowed people to program a computer using something besides pure Binary.[/quote] thats rubbish. not every language requires a compiler. some languages are interpreted instead. ever heard of BASIC, python, etc?
ada lovelace didn't create the first language.

---

### Post by yabbadabbadont on 2006-06-07
[QUOTE=ComplexNumber]she wrote the first compiler. not the first language.[/QUOTE]
I never claimed that she did...  :roll: 

I was simply providing an answer to kimm's faulty memory.

> Originally Posted by Kimm
Correct. However it was not Ada Loverlace I was refering too. Atm I cant seem to find her name... but I do belive it was during the secund world war.

---

### Post by ComplexNumber on 2006-06-07
[quote=yabbadabbadont] I never claimed that she did...[/quote] i never said that you did. it was the post that you responded to that i was correcting.

---

