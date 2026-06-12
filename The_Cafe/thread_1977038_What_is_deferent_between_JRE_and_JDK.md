---
title: "What is deferent between JRE and JDK"
date: 2012-05-09
forum: The Cafe
---

### Post by woxuxow on 2012-05-09
excuse me i did not find a good place to ask my question

I'm confused. what do jre and jdk do ?

on win i had installed jre to executed java software but on GNU/Linux i'have installed jdk (openjdk) to execute java program !

What is deferent between JRE and JDK ?

---

### Post by qamelian on 2012-05-09
The JRE is just the runtime environment that lets you run programs written in java. If you don't actually program in java yourself, this is usually all you need. The JDK is the Java Developer Kit that contains all the stuff you need to develop/complie your own java applications. It also includes the JRE. 
 
So, if you want to write java programs, get the JDK. If you only need to run java programs, all you need is the JRE. :)

---

### Post by woxuxow on 2012-05-10
> **qamelian said:**
> The JRE is just the runtime environment that lets you run programs written in java. If you don't actually program in java yourself, this is usually all you need. The JDK is the Java Developer Kit that contains all the stuff you need to develop/complie your own java applications. It also includes the JRE. 
 
So, if you want to write java programs, get the JDK. If you only need to run java programs, all you need is the JRE. :)

thank you 
it was helpful but another questions

what does jvm do. what is that
can i program in java just by installing openjdk 
is there any open source and free jre for ubuntu (openjdk is not in ubuntu repositories anymore)

---

### Post by qamelian on 2012-05-10
> **MustafaJF said:**
> thank you 
it was helpful but another questions
 
what does jvm do. what is that
can i program in java just by installing openjdk 
is there any open source and free jre for ubuntu (openjdk is not in ubuntu repositories anymore)
When you program in java, the programs compile to something called "byte-code". This is sort of an intermediate step between source code and native machine code. This is what makes java portable. The byte-code can be interpreted on any operating system that has a jvm (java virtual machine), provided the program hasn't been written to use any OS-specific classes. 
 
Once a JDK is installed, the only other tool you really need is a text editor for writing your source code. OpenJDK is still in the Ubuntu repositories:
[http://packages.ubuntu.com/precise/devel/openjdk-6-jdk](http://packages.ubuntu.com/precise/devel/openjdk-6-jdk)

---

### Post by forrestcupp on 2012-05-10
After you install JDK, you may want to look into Eclipse, which is a great IDE (Integrated Development Environment) for entering your code. [Oracle's web site for Java](http://docs.oracle.com/javase/tutorial/) is about the best source for tutorials to learn Java. Their tutorials are called Trails because they lead you through the steps of learning the language.

---

### Post by woxuxow on 2012-05-10
> **qamelian said:**
> When you program in java, the programs compile to something called "byte-code". This is sort of an intermediate step between source code and native machine code. This is what makes java portable. The byte-code can be interpreted on any operating system that has a jvm (java virtual machine), provided the program hasn't been written to use any OS-specific classes. 
 
Once a JDK is installed, the only other tool you really need is a text editor for writing your source code. OpenJDK is still in the Ubuntu repositories:
[http://packages.ubuntu.com/precise/devel/openjdk-6-jdk](http://packages.ubuntu.com/precise/devel/openjdk-6-jdk)

thanks
so jvm is just part of jdk or jre.

thank you i found it
what jre do you recommend me to install
i dont want to program i just want to run some java program like netbeans for c++ programming
fsf is too important for me

---

### Post by woxuxow on 2012-05-10
> **forrestcupp said:**
> After you install JDK, you may want to look into Eclipse, which is a great IDE (Integrated Development Environment) for entering your code. [Oracle's web site for Java](http://docs.oracle.com/javase/tutorial/) is about the best source for tutorials to learn Java. Their tutorials are called Trails because they lead you through the steps of learning the language.

thank you guy

---

### Post by Majorix on 2012-05-10
For C++ programming use Gedit, Geany, or some other lightweight IDE. You don't need a full-blown Java-based IDE to just write your Hello World in C++.

---

### Post by forrestcupp on 2012-05-10
> **MustafaJF said:**
> thanks
so jvm is just part of jdk or jre.

thank you i found it
what jre do you recommend me to install
i dont want to program i just want to run some java program like netbeans for c++ programming
fsf is too important for me

Netbeans is not the best IDE for C++. Check out Eclipse. It will do it, and it won't require JRE or JDK for C++.

---

### Post by EnGorDiaz on 2012-05-10
jre is the java enviroment 

jdk is the development enviroment

---

### Post by woxuxow on 2012-05-11
> **Majorix said:**
> For C++ programming use Gedit, Geany, or some other lightweight IDE. You don't need a full-blown Java-based IDE to just write your Hello World in C++.

your right the best ide to programming c++ is gedit
but i need something special 
code::block - netbeans and eclips are 3 good ide
eclips is a little weired to me
i'm deciding to choose one of code::blosh and netbeans
but not sure yet

---

### Post by woxuxow on 2012-05-11
> **forrestcupp said:**
> Netbeans is not the best IDE for C++. Check out Eclipse. It will do it, and it won't require JRE or JDK for C++.

but eclips need jre to execute, doesn't it
it is written in java

---

### Post by forrestcupp on 2012-05-11
> **MustafaJF said:**
> 
i'm deciding to choose one of code::blosh and netbeans
but not sure yet
I would definitely choose code::blocks out of those two. Netbeans was made for Java development, and C++ is an afterthought. I don't even like Netbeans as much as Eclipse for Java development, even though it's supposed to be the official Java IDE.

Code::Blocks is pretty top of the line for Linux capable IDEs, and it's much better than Netbeans, in my opinion.

---

### Post by forrestcupp on 2012-05-11
> **MustafaJF said:**
> but eclips need jre to execute, doesn't it
it is written in java

Yeah, I guess you're right.

---

### Post by Majorix on 2012-05-11
Eclipse and NetBeans DO require JRE, and they are heavy anyway. If you HAVE TO use an IDE don't think anymore and pick Code::Blocks. I use it myself and can say it is one of the - wait it is THE best IDE.

---

### Post by woxuxow on 2012-05-12
> **forrestcupp said:**
> I would definitely choose code::blocks out of those two. Netbeans was made for Java development, and C++ is an afterthought. I don't even like Netbeans as much as Eclipse for Java development, even though it's supposed to be the official Java IDE.

Code::Blocks is pretty top of the line for Linux capable IDEs, and it's much better than Netbeans, in my opinion.

it was written code::blash but code::blocks is correct. it was my fault
code::blocks is a little messy and not good arranged 
thank you

---

### Post by woxuxow on 2012-05-12
> **Majorix said:**
> Eclipse and NetBeans DO require JRE, and they are heavy anyway. If you HAVE TO use an IDE don't think anymore and pick Code::Blocks. I use it myself and can say it is one of the - wait it is THE best IDE.

thank you
i`ll pick code::blocks up

---

### Post by woxuxow on 2012-05-13
I got the difference between jre and jdk
now how can i append SOLVED to the subject

---

### Post by zombifier25 on 2012-05-13
Get to the top of the thread, choose "Thread Tools" > "Mark this thread as Solved"

---

