---
title: "Python is generally slow compared to compiled languages- how much slower?"
date: 2011-06-09
forum: The Cafe
---

### Post by Dustin2128 on 2011-06-09
I've been doing a lot of work in python lately and I though of a project I'd like to work on- a web browser. Yeah, I know, plenty of those already right? But it's still what I'd like to do. It's designed to fight chrome syndrome anti-featurism without actually being bloated, using an interface resembling the firefox 3.5.x or 3.6.x series, and have an excellent framework for writing plugins and extensions. Anyway, enough about my project. I started programming with python a while back, and I'm fairly comfortable with it- but I've heard it is comparatively slow as opposed to, say, C. Will this matter quite as much with a web browser? I'm going a fast web browsing experience, and I want to know if I should do the whole thing in C.

---

### Post by juancarlospaco on 2011-06-09
Im using [http://code.google.com/p/devicenzo/](http://code.google.com/p/devicenzo/)  
"fully functional web browser, based on PyQt, that aims to never be more than 128 lines long."

Plz xcus my brvity

---

### Post by BrokenKingpin on 2011-06-09
It is true, C is faster, but for an application like this I think it should be just fine. Assuming you are just going to use webkit, coding the rest of the interface in python shouldn't slow things down much.

---

### Post by Dustin2128 on 2011-06-09
> **BrokenKingpin said:**
> It is true, C is faster, but for an application like this I think it should be just fine. Assuming you are just going to use webkit, coding the rest of the interface in python shouldn't slow things down much.
Either webkit or gecko, haven't decided yet.

---

### Post by Thewhistlingwind on 2011-06-09
You can compile python to bytecode to give it a bit of a speedboost.

Still won't give you even close to C performance. (Of course C may as well be assembly language.)

---

### Post by earthpigg on 2011-06-09
> **juancarlospaco said:**
> Im using [http://code.google.com/p/devicenzo/](http://code.google.com/p/devicenzo/)  
"fully functional web browser, based on PyQt, that aims to never be more than 128 lines long."

Plz xcus my brvity

that is super cool.

a bit off topic, but still python-ey: how would something like this fare up to the big-boy benchmarking tests? security, etc?

(had to replace the first line with this to make it work on 10.10, btw: #!/usr/bin/python )

---

### Post by Bandit on 2011-06-09
I general rule of thumb is that ALL scripting langs are slower then a compiled application. Reason being is one is already compiled and the other has to convert/compile it on the fly. But something thats already been compiled cant be adjusted on the fly either, where as scripts can.

Now LUA claims to be the fastest scripting language out and is picking up usage within the linux community and popular games like World of Warcraft.

LUA may actually be fast enough to make wanting something natively compiled a marginal decision. 

[http://www.lua.org/](http://www.lua.org/)

---

### Post by NovaAesa on 2011-06-09
My under standing is that interpreted Python is about 2 orders of magnitude slower than C or C++ (i.e. 100 times slower). I doubt this will make much of a difference for a web browser though, Python should be just fine.

---

### Post by Dustin2128 on 2011-06-09
> **NovaAesa said:**
> My under standing is that interpreted Python is about 2 orders of magnitude slower than C or C++ (i.e. 100 times slower). I doubt this will make much of a difference for a web browser though, Python should be just fine.
In my experience, it's nowhere near that much slower. Maybe 10 times, but nowhere near 100.

---

### Post by jhonan on 2011-06-09
'Interpreted' versus 'compiled' performance only really matters for certain applications e.g. games, audio/video processing, processing large datasets.

And even in these cases, the python libraries you link to are compiled, giving a speed boost (correct me if I'm wrong on this point)

---

### Post by user1397 on 2011-06-09
I wonder if anyone's attempted to build an entire OS in just python, or at least a desktop environment...would be cool hehe

---

### Post by PhillyPhil on 2011-06-09
> **Dustin2128 said:**
> In my experience, it's nowhere near that much slower. Maybe 10 times, but nowhere near 100.

What does your experience consist of?  Unless you mean you've actually measured the milliseconds for equivalent pieces of code I don't think it'll hold much water.

Two orders of magnitude doesn't sound at all excessive to me.  It's going to depend on the what the code is doing (for this reason it's better to write test code yourself, rather than asking for public opinion).  I doubt it'll matter too much for a browser.

---

### Post by Dustin2128 on 2011-06-09
> **PhillyPhil said:**
> What does your experience consist of?  Unless you mean you've actually measured the milliseconds for equivalent pieces of code I don't think it'll hold much water.

Two orders of magnitude doesn't sound at all excessive to me.  It's going to depend on the what the code is doing (for this reason it's better to write test code yourself, rather than asking for public opinion).  I doubt it'll matter too much for a browser.
I haven't done it in miliseconds- but when I replicate small programs I've written in python in C, performance is basically unchanged.

---

### Post by PhillyPhil on 2011-06-09
> **Dustin2128 said:**
> I haven't done it in miliseconds- but when I replicate small programs I've written in python in C, performance is basically unchanged.

The smaller the program, the smaller the difference, and a human is no judge of a small number of milliseconds.  I don't think your claim of '10 times' is justifiable.

Anyway, like I said, the difference will depend on what the code is doing.

---

### Post by Queue29 on 2011-06-10
I'm surprised no one has posted a link to the classic computer language benchmarks game:

[http://shootout.alioth.debian.org/u64q/benchmark.php?test=all&lang=python3&lang2=gcc](http://shootout.alioth.debian.org/u64q/benchmark.php?test=all&lang=python3&lang2=gcc)

As the sight says, it's bad to jump to conclusions, but I do believe this is about the most fair benchmark one could come up with.

---

### Post by jhonan on 2011-06-10
> **Queue29 said:**
> I'm surprised no one has posted a link to the classic computer language benchmarks game:

[http://shootout.alioth.debian.org/u64q/benchmark.php?test=all&lang=python3&lang2=gcc](http://shootout.alioth.debian.org/u64q/benchmark.php?test=all&lang=python3&lang2=gcc)

Interesting to see how the higher-level languages like Ruby and Python have much more concise code. But you pay for it with the performance/memory hit.

The other benefit of course is higher abstraction means less code means faster development time. And no need to worry about strong typing or garbage collection, as you would in the lower-level languages.

---

### Post by FreeTheBee on 2011-06-10
As jhonan pointed out, although python is interpreted the use of compiled libraries can speed things up. Here is an example from the scipy website, showing a speed comparison for a numerical calculation.

[www.scipy.org/PerformancePython]("http://www.scipy.org/PerformancePython")

The comparison is shown at the bottom of the page. Of course this is a very different application than a webbrowser, but I think it nicely shows how one can improve speed using the right libraries.

---

### Post by 3rdalbum on 2011-06-10
> **ubuntuman001 said:**
> I wonder if anyone's attempted to build an entire OS in just python?

There's been a couple of attempts. Probably the best known was
Unununium.

Python itself isn't slow. The main "CPython" implementation is. There's always been talk about being able to write a Python interpreter in Python and apply its famous introspection to itself to figure out how to increase the speed of CPython. There's also been various projects to get Python programs to compile down to machine code or otherwise get it running really fast; the best known is Psyco.

---

### Post by BrokenKingpin on 2011-06-10
> **Dustin2128 said:**
> In my experience, it's nowhere near that much slower. Maybe 10 times, but nowhere near 100.
It really depends on what you are doing. In a gui app where the application basically sits and waits for user input you would not notice much of a difference. When doing complex calculations, you will notice a huge difference.

But as I said above, python should be just fine for a web browser, even if the goal is to be light and fast.

---

### Post by igouy on 2011-06-10
> **3rdalbum said:**
> There's also been various projects to get Python programs to compile down to machine code or otherwise get it running really fast; the best known is Psyco.Pysco begat [[COLOR="Blue"]PyPy[/COLOR]]("http://pypy.org/").

[[COLOR="Blue"]http://speed.pypy.org/[/COLOR]]("http://speed.pypy.org/")

---

### Post by juancarlospaco on 2011-06-10
FYI Python can use C directly too...

---

### Post by juancarlospaco on 2011-06-10
> **earthpigg said:**
> that is super cool.
(had to replace the first line with this to make it work on 10.10, btw: #!/usr/bin/python )

Try the " -pretty " version, its nice

---

