---
title: "Newbie looking for Java IDE tips"
date: 2011-04-26
forum: The Cafe
---

### Post by sprocket10 on 2011-04-26
Hello all,

I'm interested in learning Java to create some GUI-based programs.  I like the thought of Java being cross-platform AND graphical.  I have learned the basics of C, but want to create GUIs, which I understand C is not good for.

What IDE(s) do you recommend for getting started? I've heard Eclipse is good and another friend uses Dr. Java.

:popcorn:

---

### Post by Majorix on 2011-04-26
I prefer Netbeans. v7.0 is just out. Might want to try, it is close to what you are looking for.

---

### Post by forrestcupp on 2011-04-26
Netbeans for straight Java. If you're going to do Android, then Eclipse is a must.

But it's not true that C/C++ isn't good for GUIs. GTK+, Qt, and wxWidgets are all based on C or C++, and they are all cross platform and easy to learn. The benefit of these over Java is that you can compile them natively and not need any runtime virtual machine.

---

### Post by andamaru on 2011-04-26
C is cross platform as well, if you want a graphical toolkit that's cross platform you can use [QT]("http://qt.nokia.com/")

For Java [Eclipse]("http://www.eclipse.org/") or [Netbeans]("http://netbeans.org/") is what I've worked with. 

I'm with Majorix, Netbeans is my favourite

---

### Post by sprocket10 on 2011-04-26
> **forrestcupp said:**
> Netbeans for straight Java. If you're going to do Android, then Eclipse is a must.

But it's not true that C/C++ isn't good for GUIs. GTK+, Qt, and wxWidgets are all based on C or C++, and they are all cross platform and easy to learn. The benefit of these over Java is that you can compile them natively and not need any runtime virtual machine.

How do I get started using GTK+ and/or Qt (which I hear is going into future Ubuntu releases?) with C, because I'm decently comfortable with C?  I can run these graphical C programs (using GTK or Qt) in windows 7 and ubuntu, correct?

---

### Post by EarthMind on 2011-04-26
I strongly recommend BlueJ as "IDE" to start with. Netbeans and Eclipse come with too many feature that are meant to make your life easier by doing a lot of stuff automatically. That is not a good way to learn a language from scratch. BlueJ just provides basic text editor features like syntax colouring. You can also compile and easily run your Java programs from within the software.

As soon as you have a lot of understanding of the language, you can move on to a feature-rich IDE like Netbeans or Eclipse. I personally recommend Netbeans because its GUI designer and profiler are top! ON the other side, Eclipse has **_A LOT_** of available plugins.

---

### Post by EarthMind on 2011-04-26
> **sprocket10 said:**
> How do I get started using GTK+ and/or Qt (which I hear is going into future Ubuntu releases?) with C, because I'm decently comfortable with C?  I can run these graphical C programs (using GTK or Qt) in windows 7 and ubuntu, correct?

Qt uses C++, not C. GTK can be used for C and C++.

---

### Post by sprocket10 on 2011-04-27
Thanks to all for the response.  Perhaps I'll look into C++ so I can try both Qt and GTK+

In general, how does one "code/program" a GUI using GTK or Qt? Do I need to install some third party GTK/Qt compiler? I have never explored GUIs before, so it's all 100% new to me :confused:

---

### Post by RiceMonster on 2011-04-27
I suggest netbeans as well. I found the layout very straightforward, and it had all the features I wanted. It's the IDE I learned Java in.

---

### Post by forrestcupp on 2011-04-27
> **sprocket10 said:**
> Thanks to all for the response.  Perhaps I'll look into C++ so I can try both Qt and GTK+

In general, how does one "code/program" a GUI using GTK or Qt? Do I need to install some third party GTK/Qt compiler? I have never explored GUIs before, so it's all 100% new to me :confused:

You just have to download the dev libraries and set your IDE up to use those libraries. You should be able to use any IDE, but they're all set up differently. The web sites for GTK+ and Qt should have plenty of tutorials to teach you how to do things, and the libraries should come with a lot of sample code to look at, also.

C++ is a lot like C, only you'll have to learn object oriented programming concepts. It may take some effort to learn that, but it's not really that complicated. Once you learn the concepts, they are easily translated to other object oriented languages. Java is an object oriented language, so if you're going to learn it, you may as well just learn C++. Just remember that the only downside of C++ instead of Java is that you'll have to compile your program for each platform.

Also, you can find a lot more help here in the Programming subforum than in the Cafe.

---

### Post by RiceMonster on 2011-04-27
> **forrestcupp said:**
> Just remember that the only downside of C++ instead of Java is that you'll have to compile your program for each platform.

Considering all the libraries you get included with Java that cover a lot of stuff you have to do yourself in C++, and the garbage collector, I would say that's not the only downside.

---

### Post by forrestcupp on 2011-04-27
> **RiceMonster said:**
> Considering all the libraries you get included with Java that cover a lot of stuff you have to do yourself in C++, and the garbage collector, I would say that's not the only downside.

Very true. But one downside of Java is that the GUI looks like butt.

---

### Post by RiceMonster on 2011-04-27
> **forrestcupp said:**
> Very true. But one downside of Java is that the GUI looks like butt.

Can't argue with that. Swing is one awful looking toolkit. Though, it's very easy to have it follow your Windows, Mac, or GTK theme. It actually supports Motif as well.

---

