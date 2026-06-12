---
title: "GPL linking exception"
date: 2009-05-14
forum: The Cafe
---

### Post by Ebuntor on 2009-05-14
Hello everyone,

I've been reading on Wikipedia about the [GPL linking exception]("http://en.wikipedia.org/wiki/GPL_linking_exception") and the differences between the GNU [GPL]("http://en.wikipedia.org/wiki/GNU_General_Public_License") and the [LGPL]("http://en.wikipedia.org/wiki/GNU_LGPL"). Stated on Wikipedia: > The LGPL places copyleft restrictions on the program itself but does not apply these restrictions to other software that merely links with the program.As I understand it the GPL does apply those  restrictions, but what I do not understand is what do they mean by a "link"? According to the linking exception it has to do with "software projects which provide 'library' code, that is software code which is designed to be used by (in technical terms, 'linked to') other software". Could someone give me an example of what library code is? 

The LGPL exists because there are open source applications which use non-free libraries, right? Why would that be nessasry? Would it not be possible to just make free libraries along with your application?

Thanks in advance :)

---

### Post by saulgoode on 2009-05-14
> **Ebuntor said:**
> ...what do they mean by a "link"?
:
:
Could someone give me an example of what library code is?
Imagine that you've written various programs to draw shapes on the screen: a circle, a square, and a triangle. Since you are a good citizen of the Free Software community -- and because you hope that others might provide feedback on how to improve your programs -- you release your source code to the public. How you license your code will determine how people are allowed to use it. 

If the license permits, they could just copy the source code from your files and insert it into their own source. In this case, your code would not be considered a "library" in the programming sense.

Alternately, your code could be compiled as a library which includes the the three shape-creating programs as subroutines. Then the application program could just contain a reference to the appropriate subroutine in your library whenever it is needed; for example, "create_circle(x, y, radius)". When the program is executed, the loader will see that 'create_circle' is required, load your library into memory, and then modify the program so that the reference to 'create_circle' is replaced by a call to the subroutine's location in memory (see FOOTNOTE below). Such a program would be said to "link" to your library. More specifically, this is called "dynamic linking" because the program gets modified when it is executed.

There is another kind of linking, called "static linking" which will compile a version of the program that includes a compiled copy of your library subroutines hard-coded into the executable program (rather than resolve the library calls at runtime). From a copyright licensing standpoint, static linking typically involves the same restrictions and limitations as if your source code were physically copied to the program's source code (if they don't have permission to copy your source, they probably won't have permission to copy a compiled version of it).

> **Ebuntor said:**
> The LGPL exists because there are open source applications which use non-free libraries, right?
It is more typical that the LGPL is used to license open source libraries so that non-free applications can use them (though the scenario you present is also a possibility). 

> **Ebuntor said:**
> Why would that be nessasry? Would it not be possible to just make free libraries along with your application?
The main idea behind libraries, whether free or non-free, is that programmers don't have to spend the time re-writing code that already exists (they are also useful for fixing bugs in the code without having to update all the programs that might use the code). So what you describe is possible, but requires more effort from the application programmer.

The LGPL is often used because the programmer wants to know when his code is modified/improved, but doesn't particularly mind if it gets used by non-free projects. 


FOOTNOTE: With most Unix-type operating systems, a linked subroutine is not loaded into memory until that subroutine gets called during execution (though the option of "pre-loading" subroutines at startup is available).

---

### Post by glotz on 2009-05-14
Here's the reasoning behind the LGPL.
[quote="[http://www.gnu.org/licenses/why-not-lgpl.html](http://www.gnu.org/licenses/why-not-lgpl.html)"]
Using the ordinary GPL is not advantageous for every library. There are reasons that can make it better to use the Lesser GPL in certain cases. The most common case is when a free library's features are readily available for proprietary software through other alternative libraries. In that case, the library cannot give free software any particular advantage, so it is better to use the Lesser GPL for that library.

This is why we used the Lesser GPL for the GNU C library. After all, there are plenty of other C libraries; using the GPL for ours would have driven proprietary software developers to use another&#8212;no problem for them, only for us.
[/quote]

---

