---
title: "So I finally decide to remove java after this one..."
date: 2012-09-25
forum: The Cafe
---

### Post by sefs on 2012-09-25
Researchers have discovered a Java flaw that would let hackers bypass critical security measures in all recent versions of the software. The flaw was announced today by Security Explorations, the same team that recently found a security flaw in Java SE 7 letting attackers take complete control of PCs. But this latest exploit affects Java SE 5, 6, and 7—the last eight years worth of Java software.

[Above taken from [arstechnica.com]("http://arstechnica.com") full story below]

[Yet another Java flaw allows “complete” bypass of security sandbox]("http://arstechnica.com/security/2012/09/yet-another-java-flaw-allows-complete-bypass-of-security-sandbox/")

---

### Post by bootedguy on 2012-09-25
I believe that is/was the Oracle Java (the programming language, not the scripting language). The default Ubuntu install uses a different version that is not a problem.

---

### Post by QIII on 2012-09-25
By default, Ubuntu uses OpenJDK 7 which is the open source reference implementation for Oracle Java 7.  It typically lags just slightly behind Oracle Java 7.  

No.  It's not immune, any more than it was immune to the last big hole.  Everyone thought so, but Red Hat confirmed its research found OpenJDK to be equally vulnerable.

You can't just say "I'm running Ubuntu so I'm safe."

Create an apparmor profile for Java.

This has gotten so bad I think I am going to get out of the OTN.

---

### Post by sefs on 2012-09-26
> **QIII said:**
> 

Create an apparmor profile for Java.

the OTN.

I didn't know about that :)

A link about it...

[One guy's AppArmor implementation for Java]("https://insanitybit.wordpress.com/2012/08/27/apparmor-and-java/")

---

### Post by Erik1984 on 2012-09-26
I'm glad that by default, 
Java is not installed. 

(rimes somewhat depending on pronunciation :P)

---

### Post by Ji Ruo on 2012-09-26
Another day, another critical Java exploit

---

### Post by exploder on 2012-09-26
I use the open source java packages and I figure that no one has tried to take over my pc for all these years so I am not going to worry about it.

---

### Post by synaptix on 2012-09-26
People still use Java?

---

### Post by Ji Ruo on 2012-09-27
> **exploder said:**
> I use the open source java packages and I figure that no one has tried to take over my pc for all these years so I am not going to worry about it.

Same vulnerabilities, but take longer to patch

---

### Post by BrokenKingpin on 2012-09-28
meh, all software can have major security bugs, some more than others (i.e Adobe products).

---

### Post by akoskm on 2012-09-28
> **synaptix said:**
> People still use Java?

lol'd

---

### Post by Gremlinzzz on 2012-09-28
> **synaptix said:**
> People still use Java?

What do you do when the site requires Java?
like
[http://www.pogo.com/](http://www.pogo.com/)
no java cant play games.
:popcorn:

---

### Post by Ji Ruo on 2012-09-29
> **BrokenKingpin said:**
> meh, all software can have major security bugs, some more than others (i.e Adobe products).

Oracle seems to be as least as bad as Adobe at the moment.

---

### Post by angryfirelord on 2012-09-29
> **synaptix said:**
> People still use Java?
Certainly. Java is still #1 in programming demand. It's even larger once you factor in Android development and all of the web frameworks that are built off of JSPs. I'd say the only obsolete part of Java are applets, which aren't widely used anymore.

---

### Post by tjeremiah on 2012-10-02
i need my jdownloader.

---

### Post by 1clue on 2012-10-02
Yes, people still use Java.  In Enterprise and industry probably more than anywhere.  Java on the client (web browser) not so much, but you still find some of that.

Java isn't just a programming language.  It's a portable virtual machine (JVM).  It's installed on more than a billion devices if you believe the propaganda.

If you have a Blu-Ray player then you use Java.  If you have a smart phone then you probably use Java.  If you use Oracle Financials then you use Java.  Actually I'm not sure if there exists an Enterprise accounting package which does not use Java in some fashion, so probably every fortune 500 company either uses Java in their accounting or they write their own.

Java is more pervasive than Windows ever was, and it runs on platforms that Windows has never run on.  It was designed as an embedded controller language and is still heavily used that way.

Last I heard there are over 200 programming languages that run on the JVM.  Once the app is loaded into the JVM it runs pretty much as fast as any other compiled language.

The thing that Java has going for it is that it has always been based on virtual hardware.  It is therefore extremely portable, all you need to do is make the virtual machine implementation and it works on your OS.  Anything from a refrigerator or a wrist watch to a supercomputer.

It also has a security implementation for allowing access to the physical environment that has been standard from day one, which is critical.

Most languages have different characteristics that need to be taken into account.  For example, with C and related languages there isn't even a standard size for an integer, and no truly standard windowing API.

Java certainly has its share of flaws, but it's gonna be around for awhile, like it or not.

---

### Post by orange2k on 2012-10-02
:confused::shock:[-o<

---

### Post by DogMatix on 2012-10-02
> **synaptix said:**
> People still use Java?

Formula 1 live timings :redface:

---

### Post by mr john on 2012-10-02
> People still use Java?

It's used on a majority of mobile devices. So yes, people still use it.

---

### Post by Ji Ruo on 2012-10-03
> **DogMatix said:**
> Formula 1 live timings :redface:

That explains a lot...

---

### Post by litiform on 2012-10-12
I dumped JAVA while ago. I'm surprised people still use it at all.

---

