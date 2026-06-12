---
title: "Where's my GPL'd Java?"
date: 2007-05-09
forum: The Cafe
---

### Post by CSMatt on 2007-05-09
Sun announced in November that they would release the source code to their Java Runtime under the GPL, did they not?  I remember Sun setting a March deadline.  Well it's now May, and I don't see a GPL JRE in either Ubuntu's repositories or on the Java homepage.  What gives?

I'm not blaming you guys, I'm just tired of waiting around for a free Java.  It already bothers me that I have to use the non-free Flash, and that I can't legally hear my iTunes purchases.

---

### Post by Tomosaur on 2007-05-09
It's being GPLd slowly but surely. If you download netbeans, you can get access to all of the GPLd java stuff through the developer network.

But you're right, it's taking it's time.

---

### Post by CSMatt on 2007-05-09
I remember trying GNU Classpath and GCJ, but neither of them seem to give me a functional JRE replacement, as neither of them will run my Java programs.

---

### Post by igknighted on 2007-05-09
> **CSMatt said:**
> Sun announced in November that they would release the source code to their Java Runtime under the GPL, did they not?  I remember Sun setting a March deadline.  Well it's now May, and I don't see a GPL JRE in either Ubuntu's repositories or on the Java homepage.  What gives?

I'm not blaming you guys, I'm just tired of waiting around for a free Java.  It already bothers me that I have to use the non-free Flash, and that I can't legally hear my iTunes purchases.

The source code has been opened up, but it was too late for java6 to be released as GPL... I think that java7 is supposed to be the first release that is fully GPL.

---

### Post by tageiru on 2007-05-09
It's right [here](http://openjdk.java.net)

Well, partially...

---

### Post by CSMatt on 2007-05-09
Here's something unusual.  In the [source code download page](http://download.java.net/openjdk/40ec4ed263a6dfce13b8cf18fa046058/jdk7/), it says that you need non-free binaries to compile the source, but they're in jar files.  How am I supposed to run the jar files without a previous Java installed?  And how am I supposed to install Java without them?

I don't see why Sun couldn't just release the source code for the current Java and release a minor binary revision where the only change is the new GPL licensing.  Yes, I've heard that there are some parts of Java that aren't owned by Sun, but one would assume that most of it is.

---

### Post by jrusso2 on 2007-05-09
> **CSMatt said:**
> Sun announced in November that they would release the source code to their Java Runtime under the GPL, did they not?  I remember Sun setting a March deadline.  Well it's now May, and I don't see a GPL JRE in either Ubuntu's repositories or on the Java homepage.  What gives?

I'm not blaming you guys, I'm just tired of waiting around for a free Java.  It already bothers me that I have to use the non-free Flash, and that I can't legally hear my iTunes purchases.



You know there already is a Open Jave JRE the Blackdown Java.

---

### Post by jiminycricket on 2007-05-09
There was an article on Slashdot about this issue; don't know if you saw it: [http://it.slashdot.org/it/07/05/08/151257.shtml](http://it.slashdot.org/it/07/05/08/151257.shtml)

[http://planetjdk.org/](http://planetjdk.org/) also has some interesting posts about it.

---

### Post by CSMatt on 2007-05-09
> **jrusso2 said:**
> You know there already is a Open Jave JRE the Blackdown Java.
Really?  Are you sure that those are the free versions?  And if they are a reliable replacement, why aren't they in the repositories?
> **jiminycricket said:**
> There was an article on Slashdot about this issue; don't know if you saw it: [http://it.slashdot.org/it/07/05/08/151257.shtml](http://it.slashdot.org/it/07/05/08/151257.shtml)

[http://planetjdk.org/](http://planetjdk.org/) also has some interesting posts about it.
Yeah, I did see that article.  I still don't see any downloads of J2SE yet, though.  They may be finished with the transition, but I have yet to see an official release.

I'm not trying to sound ungrateful here, I'm just wondering why it's taking so long.

On a related note, I was able to install Azureus-gcj from the repositories and it runs just fine.  Isn't Azureus dependent on Java being installed?

---

### Post by Polygon on 2007-05-09
blackdown java is a third party port of java to linux (which came out before the offical port)... and in my experiences it sucks compared to the offical version

[http://en.wikipedia.org/wiki/Blackdown_Java](http://en.wikipedia.org/wiki/Blackdown_Java)

version 6 is too late to be gpl'ed, starting with version 7 java will be open source and hopefully included with ubuntu ;)

---

### Post by maniacmusician on 2007-05-09
> **Polygon said:**
> blackdown java is a third party port of java to linux (which came out before the offical port)... and in my experiences it sucks compared to the offical version

[http://en.wikipedia.org/wiki/Blackdown_Java](http://en.wikipedia.org/wiki/Blackdown_Java)

version 6 is too late to be gpl'ed, starting with version 7 java will be open source and hopefully included with ubuntu ;)
what's their release cycle like? is there a time expectency for version 7? Just curious.

---

### Post by Polygon on 2007-05-09
according to wikipedia:

> 
Java SE 7 (1.7.0) (Dolphin) anticipated for 2008


also something interestering:

> 
Following their promise, Sun released the complete source code under GPL on May 8, 2007, except some limited parts that were licensed by Sun from 3rd parties who did not want their code to be released under an open-source license [15]. Sun's goal is to replace the parts that remain closed with alternative implementations and make the class library completely open.


so now 99.9% of the code is gpled (except for some third party stuff that has to be re-written)... and it just got completely open sourced yesterday. didnt know that

---

### Post by CSMatt on 2007-05-10
Dang.

Anyone know why Azureus seems to work just fine then without Java?

---

### Post by gnudoc on 2008-01-26
> [Danny Coward]("http://blogs.sun.com/dannycoward/"), who will be the spec lead for the Java 7 JSR, now says that they're aiming for a release in January 2009.
From [http://today.java.net/pub/a/today/2007/08/09/looking-ahead-to-java-7.html](http://today.java.net/pub/a/today/2007/08/09/looking-ahead-to-java-7.html)

That's almost a year later than the 18month release cycle would require.

So maybe we'll have it in hardy+2, if we're lucky.

---

