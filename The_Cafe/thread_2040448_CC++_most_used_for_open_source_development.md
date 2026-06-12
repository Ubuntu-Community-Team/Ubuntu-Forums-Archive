---
title: "C/C++ most used for open source development"
date: 2012-08-11
forum: The Cafe
---

### Post by tech291083 on 2012-08-11
Hi,

I hope this is the right place/forum for my query. If not, then I request the forum admin to move it to the right place, thanks.

I have often read on the net that many of the open source software are written in C and C++. Some also are written in Perl and Python. this is interesting to me. Can you please elaborate as to the wide use of C and C++ in creation of open source software? Thanks.

---

### Post by MG&amp;TL on 2012-08-11
A wide range of programming languages are used in open-source development. It used to be that you used scripting languages for quick programs, and compiled languages for larger projects, but that's not the case these days. However, C (and sometimes C++) is commonly used for libraries and many old, tried and tested programs, such as the kernel, X.org, and many others.

---

### Post by tech291083 on 2012-08-11
> **MG&TL said:**
>  C (and sometimes C++) is commonly used for libraries and many old, tried and tested programs, such as the kernel, X.org, and many others.

Yes, you are right. Thanks.

---

### Post by shubham1 on 2012-08-13
Also c++ is the best easy(ok you may say python is easy but only for easy projects) and very powerfull flexible you can use qt with c++

---

### Post by vexorian on 2012-08-13
> **tech291083 said:**
> Hi,

I hope this is the right place/forum for my query. If not, then I request the forum admin to move it to the right place, thanks.

I have often read on the net that many of the open source software are written in C and C++. Some also are written in Perl and Python. this is interesting to me. Can you please elaborate as to the wide use of C and C++ in creation of open source software? Thanks.
There are far more development tools and libraries in this FOSS world that work well with the Cs.

---

### Post by forrestcupp on 2012-08-13
> **vexorian said:**
> There are far more development tools and libraries in this FOSS world that work well with the Cs.

That's absolutely right, but it seems like that's changing. A lot of the big libraries and frameworks have bindings for a lot of different languages.

But C/C++ is pretty low level, and unless you jack up your code, they are the next best thing to assembly language, as far as speed and efficiency go. If you use some of the good libraries, frameworks, and engines for C++, it's really not as hard as people make it out to be.

C++ is where my heart is.

---

### Post by Primefalcon on 2012-08-13
Mr Linux torvalds.... your opinion on C++ please

Quote from Linus
> C++ is a horrible language.

I won't post the rest here due to Linus's colorful language choice, and I'll resist linking to the page where he's talking about it for the same reason

---

### Post by snip3r8 on 2012-08-13
> **forrestcupp said:**
> 
C++ is where my heart is.

Amen to that! +1:guitar:

---

### Post by MG&amp;TL on 2012-08-13
> **shubham1 said:**
> Also c++ is the best easy(ok you may say python is easy but only for easy projects) and very powerfull flexible you can use qt with c++

Sorry, but this is untrue. Especially the python part.

There's many easy language choices (IMHO, most are quite easy to learn, after the first), of which C++ is one of the slightly more difficult.

Python is also extremely fast, powerful and flexible. Several big projects have been made with python. And yes, you can use Qt with python, although that's just one toolkit from many. If you mean that python doesn't have bindings for library X, then most projects have python bindings these days, and if not, there's nothing stopping you making your own.

Hope I wasn't too unfair, no offence was intended. :)

---

### Post by Mr.Plex on 2012-08-13
Because C/C++ has a WOCA philosophy
W: Write
O: One
C: Compile
A: Anywhere

that is if the C/C++ programs are designed to be used on all OS. If you make a python script you have to pray that the end user has the correct version of the interpreter installed on their computer.  C/C++ is widely used also because it has been a standard.  If you are an aspiring programmer and you hear that the people who made linux used C. Your going to try to also use that language. It is also a great low-level programming language.  People gain full control using it, in every aspect. Sometimes its overwhelming and therefore most people who start out write python and wonder why others don't use it over their monolithic languages.

I love python and C. I usually use Python instead of writing PSUEDO code because its so ez and efficient. But for a release I would definitely want to use C/C++ because people likes them some binaries.

---

### Post by Primefalcon on 2012-08-13
I think you mean 

O: Once

---

### Post by vexorian on 2012-08-13
> **Primefalcon said:**
> Mr Linux torvalds.... your opinion on C++ please

Quote from Linus


I won't post the rest here due to Linus's colorful language choice, and I'll resist linking to the page where he's talking about it for the same reason
C++ is a horrible language. That's what makes it so good, flexible and suitable for many projects. The people behind C++ wanted a useful language rather than win the "who gets liked the most by Linus" contest.

---

### Post by forrestcupp on 2012-08-14
> **Mr.Plex said:**
> Because C/C++ has a WOCA philosophy
W: Write
O: One
C: Compile
A: Anywhere

Unless you're writing it using winAPI. ;)

---

### Post by ssam on 2012-08-14
There are various surveys like
[http://langpop.com/](http://langpop.com/)

but its also interesting to look at which languages are used by specific important projects. for example
[http://www.ohloh.net/p/firefox/analyses/latest/languages_summary](http://www.ohloh.net/p/firefox/analyses/latest/languages_summary)
firefox is mix of C++, C, javascript and others.

---

### Post by forrestcupp on 2012-08-14
> **Primefalcon said:**
> Mr Linux torvalds.... your opinion on C++ please

Quote from Linus


I won't post the rest here due to Linus's colorful language choice, and I'll resist linking to the page where he's talking about it for the same reason

I love Linus, but this just shows how narrow minded he is. Of course C++ is a horrible language for developing a kernel. That doesn't mean it's horrible for everything, though. For apps, I wouldn't want to do without object-oriented programming.

---

### Post by NovaAesa on 2012-08-14
> **MG&TL said:**
> 
Python is also extremely fast, powerful and flexible. Several big projects have been made with python. And yes, you can use Qt with python, although that's just one toolkit from many. If you mean that python doesn't have bindings for library X, then most projects have python bindings these days, and if not, there's nothing stopping you making your own.

Hope I wasn't too unfair, no offence was intended. :)

Powerful and flexible - yes. But to say Python is "extremely fast" is misleading. It might be fast in comparison to doing calculations by hand, but it is at least one (and sometimes two) orders of magnitude slower than most compiled languages such as C++, C, etc.

---

### Post by MG&amp;TL on 2012-08-17
> **NovaAesa said:**
> Powerful and flexible - yes. But to say Python is "extremely fast" is misleading. It might be fast in comparison to doing calculations by hand, but it is at least one (and sometimes two) orders of magnitude slower than most compiled languages such as C++, C, etc.

Okay-I shall qualify, it is 'extremely fast' for an interpreted language, and unless you're doing a lot of hard computation, speed differences are negligible.

---

### Post by Deepak J on 2012-08-17
C is still used in writing the main basics of the syst like the kernel,HAL etc....

It's because of the fact that it is fast,flexible and also it closer to the assembly languages still using more meaningful keywords..

And C++ - the only major change is that C++ supports the OOP concepts better than C

---

### Post by tech291083 on 2012-08-17
> **ssam said:**
> There are various surveys like
[http://langpop.com/](http://langpop.com/)

but its also interesting to look at which languages are used by specific important projects. for example
[http://www.ohloh.net/p/firefox/analyses/latest/languages_summary](http://www.ohloh.net/p/firefox/analyses/latest/languages_summary)
firefox is mix of C++, C, javascript and others.

Great links. thanks.

---

### Post by mehaga on 2012-08-18
> **ssam said:**
> There are various surveys like
[http://langpop.com/](http://langpop.com/)

but its also interesting to look at which languages are used by specific important projects. for example
[http://www.ohloh.net/p/firefox/analyses/latest/languages_summary](http://www.ohloh.net/p/firefox/analyses/latest/languages_summary)
firefox is mix of C++, C, javascript and others.

Hm, this is interesting:
[http://www.ohloh.net/p/ubuntu/analyses/latest/languages_summary](http://www.ohloh.net/p/ubuntu/analyses/latest/languages_summary)

---

### Post by BrokenKingpin on 2012-08-21
I work in both C++ and C#, depending on the product my company currently has me working on. I use to hate on C# for dealing with memory management and all that stuff under the hood, but after working with it for a few years I have to say it is pretty damn awesome. With all the extra libraries already included you can spend more time on the actual business logic of your application.

C++ is still awesome though, and will have a place in the development world for a long time.

---

### Post by mehaga on 2012-08-22
> **BrokenKingpin said:**
> I work in both C++ and C#, depending on the product my company currently has me working on. I use to hate on C# for dealing with memory management and all that stuff under the hood, but after working with it for a few years I have to say it is pretty damn awesome. With all the extra libraries already included you can spend more time on the actual business logic of your application.

C++ is still awesome though, and will have a place in the development world for a long time.

C# is awesome, they got the language just right. But I think it's strange that most Ubuntu code is written in it.

---

