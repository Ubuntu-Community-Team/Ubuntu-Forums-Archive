---
title: "ap computer science"
date: 2009-08-19
forum: The Cafe
---

### Post by nathang1392 on 2009-08-19
im in my junior year of  high school and i took a distance learning class called ap computer science. it has some easy stuff, but the main objective is to become fluent in the java programming language. i was wondering if anyone knows any good books or techniques to grasp it quickly.

---

### Post by Maheriano on 2009-08-19
I learned Java in university, it was the programming language that every other programming course was based on. All my assignments were done in Java.

To be honest I haven't really used it in a business environment, or even at home for that matter. There are many more programming languages I feel are better suited for learning if you're not concerned with the cross platform offerings of Java.

However, having said that, I feel it is an easier language to learn and teaches you a lot about the fundamentals so you can easily pick up other languages. I started with Java and have since them picked up other languages (.NET) in a matter of a week.

On to your question, the book we used in university was Java 2 by........Haanson......or Christian Han........or something. Can't remember. A much easier way is to find simple programming questions online, download Eclipse and try to do them. If you want, I can even create a few simple programming essays for you to do. That's really the best way to learn.

---

### Post by NovaAesa on 2009-08-19
I would recommend Java Programming: From Problem Analysis to Program Design by Malik. I used it for one of my first year uni subjects (it was a reaaasy easy subject, basically just taught us the basics of java). The book is really easy to read and has lots of diagrams. It is pretty expensive though if your school library doesn't have it (cost me about 130 AUD I think).

If you want the cheaper option, Sun has a pretty good Java tutorial on their site.

---

### Post by nathang1392 on 2009-08-20
another question, at school we use xp and a program called bluej as our ide. what all software would i need to be productive in ubuntu with java?

---

### Post by Maheriano on 2009-08-20
Eclipse

---

### Post by majamba on 2009-08-20
The book that we used was Big Java by Cay Horstman good book

---

### Post by &#32 Greg on 2009-08-20
Eclipse and Netbeans are the two main Java IDEs. But Emacs FTW.

---

### Post by doas777 on 2009-08-20
> **nathang1392 said:**
> another question, at school we use xp and a program called bluej as our ide. what all software would i need to be productive in ubuntu with java?


you can install bluej in ubuntu, though it will be the Kent State version. google "ubuntu bluej" to find instructions. 

I use Eclipse for CLI stuff and Netbeans swing guis in java. in the classes I've taken that require bluej, i write and debug in eclipse, and then pasted it into blueJ for final testing and submission.

bluej is an instructional tool and from that perspective, it works, but I already had one degree in CS, and was programming C# professionally when they made me start using it, so it seemed more of a toy than anything useful. the object workbench is kinda kewl though.


good luck.

---

### Post by nathang1392 on 2009-08-20
wow. eclipse is intimidating. im sorry, im on noob level.

---

### Post by nathang1392 on 2009-08-20
i downloaded bluej for ubuntu and it is a .jar file, i open with java runtime but i have to specify a directory for jdk. im not sure where i have to install it but it gives me an error if i try to install it just anywhere.

---

### Post by doas777 on 2009-08-20
ok, since I just cleaned up my home dir and rebuilt my laptop so, I'll reinstall bluej. heres what i did:

[LIST=1]
[*]install sun java with:
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-source
sudo update-java-alternatives -s java-6-sun

```I got a couple errors on the second line, but they should not affect development (they are about web browser plugins).
[*]downloaded the bluej "all other systems" jar from [http://www.bluej.org/download/download.html](http://www.bluej.org/download/download.html) to ~/Downloads/bluej-251.jar
[*]in terminal:
```

cd ~/Downloads
chmod u+x bluej-251.jar
java -jar ./bluej-251.jar

```
[*]that last line opens the bluej installer screen. see the attached image. ensure that the "JDK Directory" is filled in. mine is:
```
/usr/lib/jvm/java-6-sun-1.6.0.14
```
[*]change the install path to point to wherever you want. I recommend just installing to your home dir (~/bluej)
[*]click install, and then done after the installer has done it's job.
[*]now bluej is installed, so lets start it up. hit alt+f2 to open the run bar. enter
```

bluej/bluej

```you can create a launcher for it if you like.
[*]open your project, and go.
[/LIST]

if your looking for total beginner tutorials for eclipse, check this out
[http://eclipsetutorial.sourceforge.net/totalbeginner.html](http://eclipsetutorial.sourceforge.net/totalbeginner.html)
eclipse looks rather intimidating at first, but you can ignore most of it, until your ready to give any given feature a try. 

Initially, most people are confused by the concept of "projects" at first (I sure was). most IDEs (integrated development environments, like eclipse, bluej, or visual studio) use projects to contain the sorce code documents that get compiled into an executable. it's really just a folder, with a little info on what classes to compile and where to put them and whatnot. 

all you really need to do to get started is to set a working directory (the place where your project folders go) and then create a java project. next next next finish... 
when your done, you can add a class to the project and start writing code. if it doesn;t do what you expect just delete it and try again.

have fun and good luck,
franklin

---

### Post by pissedoffdude on 2009-08-20
> **nathang1392 said:**
> im in my junior year of  high school and i took a distance learning class called ap computer science. it has some easy stuff, but the main objective is to become fluent in the java programming language. i was wondering if anyone knows any good books or techniques to grasp it quickly.

We used Java Concepts by Cay Horstmann, and it did a fairly decent job of explaining the java programming language.  The barron's review book for ap computer science is an excellent resource to use for the ap test as well.

If your class is using bluej, I suggest you stick with bluej.  It can run on ubuntu, but be sure you have the sun java jdk set as the default java as opposed to the openjdk, as I always had issues with bluej trying to use openjdk.

Also, try not to get too dependent on your ide.   You will not be allowed to use any ide, or even a computer, on the ap test.  I suggest you get comfortable writing code down on paper

---

### Post by nathang1392 on 2009-08-20
> **doas777 said:**
> ok, since I just cleaned up my home dir and rebuilt my laptop so, I'll reinstall bluej. heres what i did:

[LIST=1]
[*]install sun java with:
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-source
sudo update-java-alternatives -s java-6-sun

```I got a couple errors on the second line, but they should not affect development (they are about web browser plugins).
[*]downloaded the bluej "all other systems" jar from [http://www.bluej.org/download/download.html](http://www.bluej.org/download/download.html) to ~/Downloads/bluej-251.jar
[*]in terminal:
```

cd ~/Downloads
chmod u+x bluej-251.jar
java -jar ./bluej-251.jar

```
[*]that last line opens the bluej installer screen. see the attached image. ensure that the "JDK Directory" is filled in. mine is:
```
/usr/lib/jvm/java-6-sun-1.6.0.14
```
[*]change the install path to point to wherever you want. I recommend just installing to your home dir (~/bluej)
[*]click install, and then done after the installer has done it's job.
[*]now bluej is installed, so lets start it up. hit alt+f2 to open the run bar. enter
```

bluej/bluej

```you can create a launcher for it if you like.
[*]open your project, and go.
[/LIST]

if your looking for total beginner tutorials for eclipse, check this out
[http://eclipsetutorial.sourceforge.net/totalbeginner.html](http://eclipsetutorial.sourceforge.net/totalbeginner.html)
eclipse looks rather intimidating at first, but you can ignore most of it, until your ready to give any given feature a try. 

Initially, most people are confused by the concept of "projects" at first (I sure was). most IDEs (integrated development environments, like eclipse, bluej, or visual studio) use projects to contain the sorce code documents that get compiled into an executable. it's really just a folder, with a little info on what classes to compile and where to put them and whatnot. 

all you really need to do to get started is to set a working directory (the place where your project folders go) and then create a java project. next next next finish... 
when your done, you can add a class to the project and start writing code. if it doesn;t do what you expect just delete it and try again.

have fun and good luck,
franklin

thank you!

---

### Post by Chatoyer on 2009-08-21
I'd a similar question, as the OP, and never found a very satisfying answer, although previous posters mention some textbooks I'd like, still, to see.

The idea occurs to me, though, to ask whether the forum members might care to post programming exercises, and their solutions in source code, and/or examine the solutions of others, whether more, or less experienced in Java.   If it sounds as good to anyone else, please post a link to a new thread, or if such a forum exists elsewhere, I'd like to know where it might be found.

---

### Post by Mighty_Joe on 2009-08-21
> **nathang1392 said:**
> wow. eclipse is intimidating. im sorry, im on noob level.

Hoo ya.  I'm a professional Java developer who started with JDK 1.0, and for my smaller projects, I use [JEdit]("http://www.jedit.org/").  Eclipse is a great IDE for developing and managing applications and I use it every day, but it's overkill if you just want to play around and learn.  You'd spend more time wrestling with the IDE than working on your problem.
[This forum]("http://www.coderanch.com/forums") is a good place for a new Java programmer to get help (and experienced ones too, it's the first place I go).

---

### Post by Maheriano on 2009-08-21
> **pissedoffdude said:**
> We used Java Concepts by Cay Horstmann...r
That's the guy I was trying to think of!

---

### Post by doas777 on 2009-08-22
> **Chatoyer said:**
> I'd a similar question, as the OP, and never found a very satisfying answer, although previous posters mention some textbooks I'd like, still, to see.

The idea occurs to me, though, to ask whether the forum members might care to post programming exercises, and their solutions in source code, and/or examine the solutions of others, whether more, or less experienced in Java.   If it sounds as good to anyone else, please post a link to a new thread, or if such a forum exists elsewhere, I'd like to know where it might be found.


well, check out the beginners challenges in the programming talk area. they've had some good ones. just search and ye shall find.

---

### Post by stwschool on 2009-08-22
Books: The Sams series of programming books are fantastic, I've given them to a number of my (school) students to work with and they've all managed to make excellent progress with them. They're also the books I started out with for most of my languages while I was on the n00b curve, before I hit advanced and simply used google from there.

---

### Post by Chatoyer on 2009-08-25
Thank you for the directions!  And thank you too, OP.

---

