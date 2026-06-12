---
title: "What we need is rewrite Linux in"
date: 2008-05-13
forum: The Cafe
---

### Post by chewearn on 2008-05-13
Ada.

[http://www.gcn.com/print/27_8/46116-1.html](http://www.gcn.com/print/27_8/46116-1.html)

---

### Post by Google Spider on 2008-05-13
That apparently is a very secure language.O:)

> What we need is rewrite Linux in...

Nah...Linux is secure already. What we need is to rewrite windows.:biggrin:

---

### Post by Tom Mann on 2008-05-13
I'm willing to re-write Linux using [Whitespace]("http://en.wikipedia.org/wiki/Whitespace_(programming_language)")

---

### Post by Sporkman on 2008-05-13
> **Tom Mann said:**
> I'm willing to re-write Linux using [Whitespace]("http://en.wikipedia.org/wiki/Whitespace_(programming_language)")

:lol: That's awesome.

---

### Post by chewearn on 2008-05-13
Oh, wow.  This is turning into community game.  You learn something new every other day:

[http://en.wikipedia.org/wiki/Brainfuck](http://en.wikipedia.org/wiki/Brainfuck)

---

### Post by Half-Left on 2008-05-13
I dont think Linus will let you somehow :lolflag:

---

### Post by chewearn on 2008-05-13
> **Half-Left said:**
> I dont think Linus will let you somehow :lolflag:

Linus has wife problem (see sig), he got enough to worry about. :mrgreen:

---

### Post by LaRoza on 2008-05-13
> **AstalaVista said:**
> Ada.

[http://www.gcn.com/print/27_8/46116-1.html](http://www.gcn.com/print/27_8/46116-1.html)

The advantages of Ada are also the cause of very bad bugs. The article from what I read seems to make Ada bug proof. It is not. It is a fine language when you need type safety, but it is slow to code because of it.

---

### Post by HermanAB on 2008-05-13
Ada is just Pascal with a shorter name.

If you want a challenge, then you should rewrite Linux in COBOL or Fortran.

---

### Post by Arkenzor on 2008-05-13
Let's step up for interoperability and rewrite Linux in Microsoft .NET :D.

---

### Post by Trail on 2008-05-13
I'll dare say it.

Lisp.

*runs away*

---

### Post by sixdrift on 2008-05-13
Prolog.

---

### Post by Half-Left on 2008-05-13
> **Arkenzor said:**
> Let's step up for interoperability and rewrite Linux in Microsoft .NET :D.

No thanks, then it would be slow and bloated like Vista. :popcorn:

---

### Post by red_Marvin on 2008-05-13
Why not apl?

---

### Post by Barrucadu on 2008-05-13
If we're on the topic of rewriting Linux for the hell of it... Why not pure, 100% ASM?

---

### Post by LaRoza on 2008-05-13
> **Barrucadu said:**
> If we're on the topic of rewriting Linux for the hell of it... Why not pure, 100% ASM?

That is easy. That is what GCC does anyway. One would just have to store the output of that stage and you have it all in ASM.

---

### Post by Barrucadu on 2008-05-13
> **LaRoza said:**
> That is easy. That is what GCC does anyway. One would just have to store the output of that stage and you have it all in ASM.
That's the easy way. I meant *hand-coded* in pure ASM, which would be a little more difficult for something of Linux's size.

---

### Post by LaRoza on 2008-05-13
> **Barrucadu said:**
> That's the easy way. I meant *hand-coded* in pure ASM, which would be a little more difficult for something of Linux's size.

It would be effectively impossible. Instead of different compilers, you'd have to write the entire OS over for each platform.

---

### Post by original_jamingrit on 2008-05-13
Assembly is not known for it's portability.  Although it is possible to take C code, break it into assembly, and optimize it by doing things gcc couldn't go about automatically.

Also, I suggest [ZOMBIE](http://www.dangermouse.net/esoteric/zombie.html), a language for evil necromancers.

---

### Post by Barrucadu on 2008-05-13
> **original_jamingrit said:**
> Assembly is not known for it's portability.

This needs to be remedied. I'll come up with a language spec, and I'm sure an assembler could be hacked to work with it. I'm thinking something like this:

Instead of :
```
mov ax, bx
xor bx, bx
int 21h
```

Something like:
```
int main(){
        int ax;
        int bx;

        ax = bx;
        bx = bx ^ bx;

        functionname();
}
```

As you can see, semicolons are used to separate commands, and the code is grouped into functions to be easier to maintain. Perhaps, the compiler could be told what architechture to compile the code for which would fix the problem of portability. Data should be given types, such as 'int' for integer, and functions too should be given a type depending on their return values.
We should call this new language "Ca" for "Centralised Assembly" since it could be used anywhere without rewriting the code, possibly even just "C" for short.

Hang on, this looks remarkably familiar to a language already in existence...

---

### Post by sefs on 2008-05-13
I feel foxpro would make a good candidate to use for the rewrite.

---

### Post by vambo on 2008-05-13
As I once read many moons ago:
Pascal is for children
C is for consenting adults
Ada is for convicted criminals

:)

---

### Post by Barrucadu on 2008-05-13
> **vambo said:**
> Pascal is for children
Not necessarily, it is simple but I managed to make a compiler in it. True, it was for a dialect of x86 ASM I invented (with if-statements and suchlike), and 'compiling' consisted of several hundred find and replace functions with a call to an external assembler, but it still compiled things.

---

