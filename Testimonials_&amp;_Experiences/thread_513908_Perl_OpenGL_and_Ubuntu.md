---
title: "Perl OpenGL and Ubuntu"
date: 2007-07-31
forum: Testimonials &amp; Experiences
---

### Post by bfree on 2007-07-31
I've been a Windows developer for most of my career, and began using Linux for online service development during the late 90's.

In general, I've found that performance between Windows and Linux for online services is essentally the same (Apache, MySQL, mod-perl, etc).

However, when I took over CPAN's Perl OpenGL (POGL) module earlier this year, I was flabergasted at the performance difference between OpenGL on Windows and Linux - using the same dual-boot machine, same GPU and same generation OpenGL drivers - OpenGL was significantly faster on Linux than Windows.

On some [benchmarks]("http://graphcomp.com/opengl/benchmarks"), Ubuntu was inexplicably faster than Fedora.  Other benchmarks demonstrate that POGL performance is comparable to C.

Since then, I've been using Ubuntu as my primary OpenGL development OS, and have released the following CPAN modules, tested on Linux (Ubuntu,Fedora,Gentoo), Windows and MacOS:

[INDENT]
[LIST]
[*][OpenGL 0.56]("http://graphcomp.com/opengl/downloads") - supports FBOs, VBOs, ARB, Cg and GLSL shaders
[*][OpenGL::Image]("http://graphcomp.com/opengl/imaging") - supports ImageMagick integration
[*][OpenGL::Shader]("http://graphcomp.com/opengl/shaders") - abstracts ARB, Cg and GLSL APIs
[/LIST]
[/INDENT]

[POGL Developer's Site]("http://graphcomp.com/opengl")

---

### Post by loell on 2007-07-31
wow, you're a CPAN module maintainer?  :)

i'm not into perl , but i could imagine the difficulty binding opengl into perl,

is it still through swig? sorry for my ignorance.


but nevertheless, i applaud you =D>

---

### Post by bfree on 2007-07-31
Thanks for the kudos! :)

> **loell said:**
> i could imagine the difficulty binding opengl into perl

[POGL]("http://graphcomp.com/opengl") does not use swig - it uses XC, which is Perl's standard method for interfacing with C components.  XC is essentially a set of C macros that handle Perl call stacks.

Python's OpenGL binding (PyOpenGL v2) was rewritten to use swig, however benchmarks demonstrate that PyOpenGL is about 20% slower than POGL.  Some of that is due to PyOpenGL's implementation; some of it  due to Python's inherent performance issues related to large arrays.  You can read PyOpenGL author's [comments]("http://graphcomp.com/opengl/index.cgi?v=0111s3B2") on this.

One might reasonably ask why would anyone want to do OpenGL in Perl?  A number of reasons:
[INDENT][LIST]
[*] Portable; no compiling; easy/fast to prototype 3D shaders
[*] Performance is [comparable to C]("http://graphcomp.com/opengl/benchmarks")
[*] Faster than any other server side scripting language (at least for OpenGL)
[/LIST][/INDENT]

In addition, POGL provides:
[INDENT][LIST]
[*] Optimized C arrays for very fast GPU transfers
[*] Tight integration with ImageMagick for loading/processing/saving textures
[*] Shader abstractions to simplify use of multiple shading languages
[/LIST][/INDENT]

Sorry about the promotional - but if you are planning to do server-side OpenGL - or are a mathematics/physics researcher - Ubuntu and Perl OpenGL really are the best way to go. :D

---

### Post by khughitt on 2008-01-01
I was curious to see how POGL worked, so I tried installing libopengl-perl, and compiling some of the examples from the samples section of [http://graphcomp.com/opengl/]("http://graphcomp.com/opengl/index.cgi"), however I am getting error messages along the lines of:

```
Desktop:~$ ./ogl_bench.pl 
Bareword "GL_VERTEX_PROGRAM_ARB" not allowed while "strict subs" in use at ./ogl_bench.pl line 184.
Bareword "GL_VERTEX_PROGRAM_ARB" not allowed while "strict subs" in use at ./ogl_bench.pl line 185.
Bareword "GL_FRAGMENT_PROGRAM_ARB" not allowed while "strict subs" in use at ./ogl_bench.pl line 188.
Bareword "GL_FRAGMENT_PROGRAM_ARB" not allowed while "strict subs" in use at ./ogl_bench.pl line 189.
Execution of ./ogl_bench.pl aborted due to compilation errors.

```

I'm still just learning perl, and haven't quite figured out compilation errors. Can you tell me where I am going wrong?

Any advice would be greatly appreciated :)

Thanks!
Keith

---

### Post by Xyem on 2008-02-13
If you haven't learned what those errors mean, I can explain them.

In this particular instance, those are meant to be the names of constants that are implemented as subroutines:
```
sub GL_VERTEX_PROGRAM_ARB { 1; }
```
( I believe they are meant to be checking the capabilities of your 3D drivers and/or hardware )

Subroutines, when used like this as optimised away during compilation so this:
```
print GL_VERTEX_PROGRAM_ARB + 100;
``` would become:
```
print 1 + 100;
```
at runtime.

They are referred to as barewords because there is no syntax telling perl what it is ( prefixed with $, %, @, * or & for example  ).

Because you are running in strict mode, perl is regarding this as a compilation error.

I imagine that the OpenGL module ( or the benchmark code? ) isn't exporting/importing/defining these constants.

I can look at this for you later and see where it may be going wrong. The computer I'm on right now gives me this error when I try to run it -.-
```
Extension not available: EXT_framebuffer_object
```

Questions for you:

Have you made any modifications to the ogl_bench.pl code?
What version of the OpenGL modules do you have?
Do you have all three modules: OpenGL, OpenGL::Shader and OpenGL::Image?

---

