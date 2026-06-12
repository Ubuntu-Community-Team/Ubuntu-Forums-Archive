---
title: "Programming in Linux"
date: 2006-08-19
forum: The Cafe
---

### Post by magnoliablossom on 2006-08-19
I've been trying to teach myself Java 2 programming.  I initially decided to do this about a year ago, but got a little side tracked after about the 3rd or 4th chapter.  But since I've started trying to learn my way around in Linux, I decided to dust the book off (Learn Java2 in 24 Hours) and try it again.

All of the programs I wrote in Windows for Java work with the exact same source in Linux....So why aren't there more programs of equal quality in Linux as there are in Windows???  I mean you write it to a text file and compile it...Why can't they just compile the same text file in both???

Are other languages not like that?  Is writing a program different in other languages between Windows and Linux?

---

### Post by bjweeks on 2006-08-19
Thats how java works... It's portablity is the only reason people use it.

---

### Post by magnoliablossom on 2006-08-19
well dang....the back of the book made it sound like it was the next best thing to sliced bread...so that's why i chose java. lol

---

### Post by daniel of sarnia on 2006-08-19
Yeah from what I understand it is more the lower level languages that are harder to port like C. languages like python or java have almost no issues with portting.

---

### Post by The Noble on 2006-08-19
Yes, way different. Java was meant to be a cross-platform interpreter. Every program you run requires the java runtime environment right? Sun is compiling the runtime environ for as many operating systems as possible, so any program you write will work on almost any computer that has java. The java runtime environ (jre) is dynamically recompiling your programs while they run. The bad thing about java is it is slooooooooow. Look at things like azureus. It is a memory hog and is not exactly a quick program.

Other languages like C, C++, Basic, etc depend on system calls to run. For example, C makes a call to windows dependencies for asking for the time, etc. The calls are different in Linux, and Linux calls are different that BSD calls, so each program must be recompiled with modifications. The entire Wine project is basically a supplier of windows dependencies by redirecting to Linux system calls. In the end, C is MUCH faster than Java for the fact that it is tailored for the system.

With programs that are several thousand lines of code, it would be a pain to have to redeclare and change a whole slew of system calls for another operating system that isn't popular, isn't it? That is why we don't have many games, as we don't have DirectX, nor the quality of drivers, nor the amount of people that Windows has. For that matter, OSX is quite a bit ahead of us in the driver department.

---

### Post by magnoliablossom on 2006-08-19
Ahh k, the jre makes sense now....As for Python...How is it then that it is as portable as Java?

---

### Post by bjweeks on 2006-08-19
> **magnoliablossom said:**
> Ahh k, the jre makes sense now....As for Python...How is it then that it is as portable as Java?

Yes...

---

### Post by tribaal on 2006-08-19
Well python uses the same trick.

Actually python is a scipting language that is "compiled on the fly" by your runtime program: if you go to CLI and type "python" you'll lauch the interpreter (which has basically the same purpose than the jre).

- trib'

---

### Post by G Morgan on 2006-08-21
Also Python can kind of run in Java via Jython but thats just confusing things.

---

### Post by 3rdalbum on 2006-08-21
Be aware though; not all Java programs written on Windows will run on Linux. There aren't even any guarantees that programs will work properly from one Windows computer to the next. Sun can't write a decent Java implementation to save its life.

Make sure you test programs on as many differently-configured computers as possible before distributing them.

---

### Post by samir85 on 2006-08-21
Actually, there's another reason why java isn't popular on linux. Since java has its own GUI libary, java applications doesn't look like the other apllications who use GTK/QT (well, there are GTK/QT bindings for java, but they are rarely used).

Concerning java and cpu usage. I think nowadays it's not that important anymore, because in these the bottleneck of the most applications is the harddisc and not the cpu anymore. So you can programm applications in java without worrying about perfomance (of course there're a few exceptions like perfomance critical system applications).

---

