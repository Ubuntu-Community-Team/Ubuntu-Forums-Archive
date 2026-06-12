---
title: "llvm-gcc in Intrepid?"
date: 2008-06-25
forum: Ubuntu Brainstorm
---

### Post by ycason on 2008-06-25
Well, please excuse my naivety on the subject of compilers and such but I was reading this article extolling the benefits of llvm and the llvm-gcc blended compiler.  One quote from the article states that "Sources report that LLVM-GCC 'compiles code that consistently runs 33% faster' than code output from GCC."  

Now my question is, if we could have a drop in replacement for gcc that instantly gains us 33% better performance, why aren't we doing this?  I'm intrigued by the possibilities.

:guitar:

P.S. link to article [http://www.appleinsider.com/articles/08/06/20/apples_other_open_secret_the_llvm_complier.html&page=1](http://www.appleinsider.com/articles/08/06/20/apples_other_open_secret_the_llvm_complier.html&page=1)

---

### Post by GeneralZod on 2008-06-27
The journalist who wrote the article was confused about the "33% faster" figure; here is the reply from Chris Lattner, one of the core LLVM software engineers:

> 
The article was confused. llvm-gcc consistently compiles code 30-40% faster than GCC does when the optimizer is enabled (e.g. at) -O2. The generated code is usually 5-10% faster than GCC generated code, but obviously YMMV.


[http://www.osnews.com/thread?319426](http://www.osnews.com/thread?319426)

So we're looking at a much more modest 5-10% speedup (but, as Chris notes, it could be more or less than this, depending on the application - or part of the application - being compiled.)

I'm also not sure to what extent LLVM is a drop-in replacement for gcc - can it compile all of Firefox, Open Office, Qt and KDE (over 10 million lines of complex C++ code)? Does it use the same C++ ABI as gcc? etc (these aren't rhetorical questions, by the way - I have no idea what the answers are :)).  

LLVM is certainly exciting, though - it looks like a "Software Project Done Right(TM)" and will probably be a lot more maintainable and flexible than the aging gcc codebase.  Definitely one to watch :)

---

### Post by ycason on 2008-06-27
Well, that's a shame about the confusion with 33%, but 5-10% sounds pretty good to me also.  I'm not so sure about the ABI, but it would seem to me that they're using the best parts of GCC and LLVM which would mean the parser of GCC and optimizer in LLVM.  Wouldn't this mean a consistent ABI between the two?

I am always excited to see a speed improvement on the same hardware(which is also why I like to watch the ATI developments lately), and I'm sure no one would complain ;)

---

### Post by aaron-haviland on 2008-07-06
llvm-gcc uses a slightly different version of gcc... it's based off of Apple's fork/modifications, so there's a potential for issues there.

As far as everything else, though, I've modified llvm-gcc to use libgcc-llvm_s.so instead of libgcc_s.so and other similar file and path modifications, so it seemingly can be installed and used alongside a normal gcc, and I am in the process of attempting to rebuild hardy with it.

No, it's not going well. Yet...

Setting up a buildd is actually harder than it seems.

---

### Post by Nullack on 2008-07-06
Very nice - keen to see some benches once yo sort it

Please keeup us informed

---

### Post by pioa on 2008-09-17
Any news on this?

---

### Post by gnomeuser on 2008-09-18
> **pioa said:**
> Any news on this?

currently such a move makes no sense. You replace the existing compiler with a completely different design. Who knows how much this will break, where it will introduce regressions. 

Not to mention does it have the same security features as GCC proper and is the performance increase even interesting when measured against a newer GCC (4.4.0 e.g. has some interesting additions). Also does the performance of the benchmark suites actually translate into a measurable difference on a whole distribution as it's run on a day to day basis. Other unanswered questions would include such things as does this approach introduce a uniform performance increase or are there platforms/hardware combinations where we see a performance hit.

There's also the problem of support, gcc is well supported, with a very active upstream. Many developers working full time, we can be relatively sure bugs get addressed and we can be sure given the fact that gcc is being used by every distro under the sun that the test coverage is really good.

All in all this is to much work even to evaluate at present, it's an interesting research project to recompile an entire Ubuntu setup using this and collecting data. I doubt the pain is ultimately worth the gain but feel free to surprise me.

---

### Post by pioa on 2008-09-18
I was hoping someone done a research and knows the answers on all that questions. :)

If llvm can be used as a jump in replacement and if it's 100 % compatible then it would be very interesting. But is it?

Someone successfully build a bigger Open Source project such as Firefox with llvm?

Maybe we can just test a normal compile instruction first with gcc/g++. If it's working we twist all calls to gcc/g++/... to their respective clones (llvm-gcc and so on). Could this work?

How to intercept a call for some binary (gcc) and relay it to another binary (llvm-gcc)? Going this way could prevent us from manually modifying any makefiles.

---

### Post by aaron-haviland on 2009-03-11
I never said it was a *good* idea, just an interesting one. I agree, it definitely isn't worth the pain... unless you happen to like pain!

As far as being a drop-in replacement... No. Not at all. At least not llvm-2.4, because it couldn't even compile glibc properly. I'm working my way up to that point with llvm-2.5 right now, so we'll see.

---

