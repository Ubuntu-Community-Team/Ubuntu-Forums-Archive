---
title: "Mono and Beagle"
date: 2006-03-08
forum: The Cafe
---

### Post by JackDog on 2006-03-08
So does anyone else find it disappointing that Beagle is written in Mono? Seriously.  Its a proprietary dead end language. Sure it works but so does COBOL. Mono will never be completely cross platform and offer the same feature set as C#. 

I fired up beagle today and watched it take up 80MB of RAM before it even started to search. It made me sad. Its a great concept, but sorry to say poorly implemented. Sounds like the main reason Mono even exists is because of Novell. 

This isn't a troll. Just an open question.

---

### Post by bjweeks on 2006-03-08
Don't use it.

---

### Post by DrFunkenstein on 2006-03-08
No. Beagle works great for me (using Dapper) and mono seems to be a great language.

Anyway, you might want to check out [Tracker]("http://freedesktop.org/wiki/Software/Tracker")

---

### Post by JackDog on 2006-03-08
[QUOTE=DrFunkenstein]No. Beagle works great for me (using Dapper) and mono seems to be a great language.

Anyway, you might want to check out [Tracker]("http://freedesktop.org/wiki/Software/Tracker")[/QUOTE]


Well actually I would have just used Java and Lucene personally. But my question really is, is it in the best interests of Gnome to literally force Mono to be the standard JIT language? Seems like the more obvious solution would be to use Java, since its proven and has a very defined future. There are many companies that use Java for 1M trans/day applications.

---

### Post by DrFunkenstein on 2006-03-08
[QUOTE=JackDog] But my question really is, is it in the best interests of Gnome to literally force Mono to be the standard JIT language? [/QUOTE]
Please, let's not get into this stupid discussion again. This subject has been debated (if you want to call the usual flamefest that errupt when the issue is mono and Gnome a debate) to death. And no, nobody is forcing mono to be the standard JIT language for Gnome. It's just an other option, as is Java.

---

### Post by JackDog on 2006-03-08
[QUOTE=DrFunkenstein]Please, let's not get into this stupid discussion again. This subject has been debated (if you want to call the usual flamefest that errupt when the issue is mono and Gnome a debate) to death. And no, nobody is forcing mono to be the standard JIT language for Gnome. It's just an other option, as is Java.[/QUOTE]

Actually, I believe you are completely wrong. If Beagle becomes a standard component, Mono has just been forced on the user. What you could debate is whether you want to install Mono or not but its moot. "Standards" have a sneaky way of evolving, and I think Beagle/Mono is a prime example. I am not convinced Mono is viable in the long term. It would be shame to depend on an application such as beagle in 5 years and see Mono die, effectively destroying Beagle. Where would we be then? If I could name one negative attribute of OSS, its lack of forsight.

---

### Post by mostwanted on 2006-03-08
[QUOTE=DrFunkenstein]No. Beagle works great for me (using Dapper) and mono seems to be a great language.

Anyway, you might want to check out [Tracker]("http://freedesktop.org/wiki/Software/Tracker")[/QUOTE]

Mono is not a language, it's a runtime for CIL (.NET bytecode) programs which can be written in any language with a CIL compiler (like C#, Boo, Nemerle, IronPython, PHP.NET, etc.).

---

### Post by kaamos on 2006-03-08
Java would be even worse than mono.. Say you have azureus that needs the Sun jre and Beagle that would be designed for blackdown or gnu Java (since no one will be waving flags for including a propietary java vm). Solution: beagle will ship with it's own Java libraries wich makes the package quite huge.

---

### Post by DrFunkenstein on 2006-03-08
[QUOTE=JackDog] If Beagle becomes a standard component, Mono has just been forced on the user.[/QUOTE]
But beagle isn't going to be a standard component. Look at the link I provided again. Really, there's no point to this debate and I'm out of here.

@mostwanted:
You are of course right.

---

### Post by JackDog on 2006-03-08
[QUOTE=kaamos]Java would be even worse than mono.. Say you have azureus that needs the Sun jre and Beagle that would be designed for blackdown or gnu Java (since no one will be waving flags for including a propietary java wm). Solution: beagle will ship with it's own Java libraries wich makes the package quite huge.[/QUOTE]


Actually Blackdown, IBM and Sun Java have very few compatibility issues. GNU Java on the other hand is very incompatible with all three unless you are paying attention. But yes, a single JRE version would have to be shipped that all apps would need to properly support. That definitely would cause some development issues.

---

### Post by JackDog on 2006-03-08
[QUOTE=DrFunkenstein]But beagle isn't going to be a standard component. Look at the link I provided again. Really, there's no point to this debate and I'm out of here.[/QUOTE]

Later. Well if all the developers in gnome share your view on long term software viability, then I fear gnome is in for a rough ride.  Stumbling blindly through development usually does not ensure a quality product. JITs platforms are becoming more and more popular with software vendors. Its a matter of time before one emerges are the standard. That is one reason why MS is pushing Vista/.Net so hard now.  They know if they don't get the lead soon, they never will.

---

### Post by mdmarmer on 2006-03-08
Please, refrain from abusing COBOL

It's still a vital and important language

Australian Tax Office Chooses Dead Language
[http://australianit.news.com.au/articles/0,7204,18312624%5E15425%5E%5Enbv=%5E15309,00.html](http://australianit.news.com.au/articles/0,7204,18312624%5E15425%5E%5Enbv=%5E15309,00.html)

;-)
-- Mike

---

### Post by JackDog on 2006-03-08
[QUOTE=mdmarmer]Please, refrain from abusing COBOL[/QUOTE]


I use it. But you wont see COBOL servlets or opengl support coming any time soon either ;)

Most companies utilize more modern platforms for new implementations though.

---

