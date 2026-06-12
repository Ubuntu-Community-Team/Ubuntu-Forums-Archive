---
title: "Learning Java or C ?"
date: 2010-03-29
forum: The Cafe
---

### Post by derekeverett on 2010-03-29
I'm interested in making contact with anybody learning Java or C that might want to pass some emails back and forth helping each other with questions and challenges.. that kind of thing.

It's not that I intend to take anything away from the forums, I was just thinking it would be nice to be in regular contact with a couple people of a similar mind frame.

I should make clear that I mean Java and/or C, not C++, for the time being anyway.

Anyway, hopefully there is somebody out there.

---

### Post by iRiUX on 2010-03-29
In my opinion, go with C++.

---

### Post by derekeverett on 2010-03-29
> **iRiUX said:**
> In my opinion, go with C++.

lol opinions are awesome, thank you.

---

### Post by falconindy on 2010-03-29
I'm currently learning both. Java in school, C in my free time. Having way more fun with C.

---

### Post by derekeverett on 2010-03-29
> **falconindy said:**
> I'm currently learning both. Java in school, C in my free time. Having way more fun with C.

I'm torn.. C seems like more fun up til now.. but I'm just starting to figure my way around the Java API.. you could spend a lifetime in there and never get to see it all!

---

### Post by falconindy on 2010-03-29
I feel as though languages like Java write themselves. I get no joy out of grazing the API and finding the right import to do the job. The lack of control over things such as memory management bothers me as well, **especially** in Java where the GC is atrocious.

C, on the other hand, is like writing sweet poetry. It may take a little more attention to detail and patience, but it's comforting to know that when you run into a problem, you have amazing tools like valgrind and gdb to lead you in the right direction.

---

### Post by derekeverett on 2010-03-29
> **falconindy said:**
> I feel as though languages like Java write themselves. I get no joy out of grazing the API and finding the right import to do the job. The lack of control over things such as memory management bothers me as well, **especially** in Java where the GC is atrocious.

C, on the other hand, is like writing sweet poetry. It may take a little more attention to detail and patience, but it's comforting to know that when you run into a problem, you have amazing tools like valgrind and gdb to lead you in the right direction.

Sounds like your certainly further along with C then I am. But I'm not sure memory management is as important in todays world, especially with the trivial programs I'm writing! Seems to me most of us have more memory than we know what to do with most times.

I'm not even familiar with valgrind or gdb.. what are those?

---

### Post by mickie.kext on 2010-03-29
> **derekeverett said:**
> 
I'm not even familiar with valgrind or gdb.. what are those?

Those are debuggers, they are used to detect memory leaks and similar glitches in C programs. There is also program called Electric Fence (efence) which also can help.

---

### Post by falconindy on 2010-03-29
> **derekeverett said:**
> Sounds like your certainly further along with C then I am. But I'm not sure memory management is as important in todays world, especially with the trivial programs I'm writing! Seems to me most of us have more memory than we know what to do with most times.

I'm not even familiar with valgrind or gdb.. what are those?
Writing C is about creating fast and efficient software. There's not much else reason to use C other than for self-interest. Memory management (matching a free() for every malloc()) is just as important today as it was in 1972.

gdb is the GNU debugger. If you compile your code with the '-g' flag, you'll have debugging symbols inserted and you'll be able to step through your code and easily identify where you're having problems. valgrind is a memory checker (and a debugger of sorts) which helps identify memory leaks.

---

### Post by derekeverett on 2010-03-29
> **falconindy said:**
> Writing C is about creating fast and efficient software. There's not much else reason to use C other than for self-interest. Memory management (matching a free() for every malloc()) is just as important today as it was in 1972.

gdb is the GNU debugger. If you compile your code with the '-g' flag, you'll have debugging symbols inserted and you'll be able to step through your code and easily identify where you're having problems. valgrind is a memory checker (and a debugger of sorts) which helps identify memory leaks.

Cool thanks. I'm gonna try those!

---

### Post by Simian Man on 2010-03-29
> **falconindy said:**
> I feel as though languages like Java write themselves. I get no joy out of grazing the API and finding the right import to do the job. The lack of control over things such as memory management bothers me as well, **especially** in Java where the GC is atrocious.
With any language/standard library combination, there is an invisible line where trivial programs stop and significant problems begin.  Trivial problems are those which can be solved with very little complexity in your own code.  You just call a few library functions with the right inputs and move on.  Significant problems, on the other hand, require you to implement real algorithms in your code directly.

In C, pretty much everything beyond "guess the number" falls in the category of significant problems.  In Java, the line is a lot higher due to the memory management and exhaustive standard library.  But the line is still there!  For you to imply that all Java programming consists grazing the APIS and importing whatever you need just makes me think you haven't reached that line yet.

And the garbage collection in Java is actually quite sophisticated.  Don't judge the language purely based on the software that is written in it, because Java has more inept programmers working in it than any other language.

> **falconindy said:**
> Writing C is about creating fast and efficient software. There's not much else reason to use C other than for self-interest. Memory management (matching a free() for every malloc()) is just as important today as it was in 1972.
No it isn't.  In 1972 to write a decent text-based RPG you absolutely needed to write tight, efficient code and programmers had many tricks for doing this such as overlays which nobody in their right mind would employ today.

Nowadays, however, there are very few areas where C is needed for efficiency reasons.  Embedded systems, the kernel and perhaps a few others are just about it.

Now don't get me wrong, there are many reasons to learn C.  There is an absolute ton of legacy software written in for starters.  It is also an extremely elegant language, especially when compared to atrocities like Java and C++.  But the reasons you gave for learning C are absolutely incorrect.

---

### Post by gnomeuser on 2010-03-29
I think if you are learning programming I would snatch a copy of Greenfoot (and be sure to fetch the draft of the Greenfoot book as well it should be free). Then fetch a copy of BlueJ and get the Objects First with BlueJ book. This will give you an introduction to programming that is fun and will get you working on some fairly advanced subjects within 7-8 weeks provided you put a good couple of hours into it a week.

This is Java but you will learn the tenants of object oriented programming rather than language syntax which I personally having tried both the classic (hello world and onwards) and this approach find more useful. 

After you master the basics I would switch to C#, it has far nicer solutions to some of the nastier problems you will face later on in addition to some great functionality. Finally the bindings for the standard Ubuntu desktop are in a much better shape for C# and the existing community of developers in this sphere is much larger.

---

### Post by falconindy on 2010-03-29
> **Simian Man said:**
> For you to imply that all Java programming consists grazing the APIS and importing whatever you need just makes me think you haven't reached that line yet.
Sure, if you find that you need a BFS algorithm, it's likely that your language isn't going to provide it for you, as binary searches are far more common as the "default" search implementation. I have experience writing Java, Python, and Ruby at a high level. These languages **do not interest me**. I realize their appeal for solving more complex problems quickly, but given the **choice**, I will opt for something else.

> **Simian Man said:**
> And the garbage collection in Java is actually quite sophisticated.  Don't judge the language purely based on the software that is written in it, because Java has more inept programmers working in it than any other language.
I'll judge it based on the fact that Java's GC is lazy by design. You can only be sure that an object is marked as eligible for collection when you remove all the references to it. There's no guarantee that the object will be GC'd immediately. Furthermore, I could easily show you an example using a linked list where a node is inaccessible but **not** marked for collection. It's better than the GC implementation going back to say, 1.2, but it's still poor.

> **Simian Man said:**
> No it isn't.  In 1972 to write a decent text-based RPG you absolutely needed to write tight, efficient code and programmers had many tricks for doing this such as overlays which nobody in their right mind would employ today.

Nowadays, however, there are very few areas where C is needed for efficiency reasons.  Embedded systems, the kernel and perhaps a few others are just about it.

Now don't get me wrong, there are many reasons to learn C.  There is an absolute ton of legacy software written in for starters.  It is also an extremely elegant language, especially when compared to atrocities like Java and C++.  But the reasons you gave for learning C are absolutely incorrect.
You've taken my post entirely out of context (possibly misinterpreting), and stretched my logic across purposes that it was not meant to be. The reasons to learn a language (to an educational end) are **not** the same as the reasons to use a language (to a practical end).

---

### Post by Simian Man on 2010-03-29
> **falconindy said:**
> Sure, if you find that you need a BFS algorithm, it's likely that your language isn't going to provide it for you, as binary searches are far more common as the "default" search implementation. I have experience writing Java, Python, and Ruby at a high level. These languages **do not interest me**. I realize their appeal for solving more complex problems quickly, but given the **choice**, I will opt for something else.

That's kind of a weird example since BFS and Binary Search are each valid in a totally different domain.  You can't BFS an array and you can't binary search a graph.

And if you are so experienced, then you will know that there are tons of interesting problems to solve no matter what language you use and what libraries you employ.  In fact with higher level languages, you will spend more time solving interesting problems because you don't have to implement basic functionality over and over again.

Have fun implementing a linked list for the hundredth time, but don't pretend that you are writing better code than someone using a library, or that they are taking an easy out.  Because neither of those things are true.

> **falconindy said:**
> I'll judge it based on the fact that Java's GC is lazy by design. You can only be sure that an object is marked as eligible for collection when you remove all the references to it. There's no guarantee that the object will be GC'd immediately. Furthermore, I could easily show you an example using a linked list where a node is inaccessible but **not** marked for collection. It's better than the GC implementation going back to say, 1.2, but it's still poor.

It's a *good thing* that there is no guarantee that any given object will be garbage collected at any given time.  That gives the implementation latitude to perform it in a more efficient manner.  Would you want the GC constantly invoked as soon as a few bytes are ready to be reclaimed?

> **falconindy said:**
> You've taken my post entirely out of context (possibly misinterpreting), and stretched my logic across purposes that it was not meant to be. The reasons to learn a language (to an educational end) are **not** the same as the reasons to use a language (to a practical end).

I understand that.  I even said in my post that C is a great language to learn.  However the reasons for doing so have little to do with the efficiency of the code you write and they don't really apply to people learning their first language.

---

### Post by chappajar on 2010-03-29
> **falconindy said:**
> I feel as though languages like Java write themselves. I get no joy out of grazing the API and finding the right import to do the job. The lack of control over things such as memory management bothers me as well, **especially** in Java where the GC is atrocious.

Later you will be thankful that you don't have to rewrite code that has been written many times by many people, some of whom are as good as or better coders than yourself.

---

### Post by szymon_g on 2010-03-29
why not Go or Python? both seems more logical and easier to me than C/C++/Java (although i'm not really a programmer ;p)

---

### Post by Jimleko211 on 2010-03-29
Damn, this thread got wayyyy off of topic.  In answer to the OP's original query, I have experience in Java, and would like to start learning C.  If you'd like to start a correspondence, send me a PM requesting so, and we'll see how it plays along :)

---

### Post by JDShu on 2010-03-29
I had a C++ base for undergrad, but I'm self learning both C and Java right now. I've been playing with the allegro library to write a game, plus I want to be able to make sense of the Linux driver code. I'm learning Java because the operating systems syllabus that the University of Wisconsin [hosts]("http://pages.cs.wisc.edu/%7Esolomon/cs537-old/last/notes.html") requires it.

---

### Post by derekeverett on 2010-03-29
> **Jimleko211 said:**
> Damn, this thread got wayyyy off of topic.  In answer to the OP's original query, I have experience in Java, and would like to start learning C.  If you'd like to start a correspondence, send me a PM requesting so, and we'll see how it plays along :)

Thank you for that. While this thread is an interesting read for me - it strayed from my question from the very first reply lol.

I will send you a little "introducing myself" pm later tonight and include my email address. (I'm just waking up here - I'm a graveyard shift worker).

My intention is just to have at least semi-regular contact with people that are learning/interested in some of this stuff as well. I don't personally know anybody that could care less.

---

### Post by Jimleko211 on 2010-03-29
> **derekeverett said:**
> 

My intention is just to have at least semi-regular contact with people that are learning/interested in some of this stuff as well. I don't personally know anybody that could care less.
Excellent, same with me.  My old computer science teacher is a sub now, so I can't ask him for exercises or anything.  Luckily, spring break is coming up for me (I'm a sophomore) so I can spend some good time coding.

---

