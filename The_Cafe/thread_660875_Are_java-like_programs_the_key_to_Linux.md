---
title: "Are java-like programs the key to Linux"
date: 2008-01-07
forum: The Cafe
---

### Post by Bannor on 2008-01-07
So I was walking the dog thinking of way to make millions and retire young.   

I have been thinking about the state of software Open, Closed and specifically what is a business model for linux that encourages closed source companies to write for it, and how to make money selling an operating system that can be downloaded for free. 

The latter I have not figured out (which is why I am writing this from work).  the former however,  can be solved with programs likes java.  Getting a company to spend large somes of money converting software to rund on an OS that makes up less than 1% of the desktop market is unlikely.   However encouraging companies to build programs on a platform that by default is compatable with 100% of the market share, just makes sence. 

Anyway it was late, but it seemed pretty revolutionary the more universal platforms that are out there the more software linux will have access too, and when a free operating system will run the software people want why would they pay $200 for windows or much more for a mac. 

I was interested in what the community thought.

---

### Post by popch on 2008-01-07
That's pretty close to what the people at sun thought. Of course, I do not know if they were walking their dogs, too. In fact, the coined the phrase 'code once, run anywhere' to describe what you can archieve with Java.

Part of that promise has been fulfilled. You can run programs written in Java on Windows, Mac OS X, Linux and presumably several other PC systems. Theoretically, you could run the same programs on your pda, cell phone or vacuum cleaner. Well, not the vacuum cleaner, because there's no JRE for vacuum cleaners yet, I believe. Of course, the size of the screen woult limit your choice of environment somewhat, as would the available processing power and storage capacity.

Unfortunately, using Java has not caught on as much as sun had hoped for.

In practice, system development in Java is not for the novice. In fact, it requires quite some professional discipline. Also, the API is overwhelmingly large. I have been known to have called Java for that reason an 'ungainly monster' or worse. Lastly, some Java programs are notable for their speed of execution. By 'notable' I mean rather 'notorious'.

You can see what I mean by visiting a well stocked book shop. Have a look at the length of the shelf where the Java API documentation is stored. The documentation is 'a bit bulky' because the API provides a great many functions. But that's not the only reason for its bulk.

Many software developers prefer smaller and more nimble environments.

Afterthought, in keeping with your signature: Is that thread already long enough to mention that the US ... ?

---

### Post by GMU_DodgyHodgy on 2008-01-07
I would have to say yes.  Everybody keeps asking the question when is linux (as an OS) ready for the desktop.  It is - Dell offering Ubuntu installed is evidence of that.  However, what does hold linux adoption back is quality applications.  particularly those applications that home users use - iLife replacements that are full featured and a Quicken/Money replacements.  

JGnash (I know I talked about this on another thread) was the first app on linux with which I repaced my 10 years of MS Money data.  It is written in Java and does great.  Runs on everything.  

For desktop applications - Java is not the complicated.  The problem is java developers try to include all the APIs and classes where they are not needed.  A developer should only leverage those classes that are needed - and for rich client apps - its not much - especially when developing home finance, iPhoto or iMovie applications.  If a company can develop a quality app in Java and leverage over multiple systems - it will take off and benefit Linux.  More importantly, open source developers should use it to create apps for multiple OSes and thereby obtain input and code contributions from that larger community to enhance its functionality and quality.

---

### Post by Sporkman on 2008-01-07
You wouldn't even need generic bytecode for the whole application, just the UI, I'd think. The back-end source code should be easily compilable regardless of the OS.

---

### Post by happysmileman on 2008-01-07
Java-like programs are, but I don't consider it acceptable to run much programs in a runtime environment,  Java programs seem to go slow for me compared to non-java programs, you can show me all the studies and proof to the contrary, but they just respond slower...

I think companies should use toolkits such as QT or GTK though instead of using the WIndows API for their programs, personally I always wondered why programs weren't generally made with QT, but then I realised that you needed to buy a license to make proprietary programs.
So maybe GTK is the way to go. The majority of things can I'm assuming be done like that, QT allows you to do everything in a multiplatform way, including file IO and sockets, so I'm assuming GTK would also allow this, though i'm not sure.

Of course even if not, File IO and sockets and very similar and it would only take an extra couple of LoC to make it work multiplatform usually, GUI seems to be the main limitation for most multiplatform app.s

---

### Post by GMU_DodgyHodgy on 2008-01-07
> **happysmileman said:**
> Java-like programs are, but I don't consider it acceptable to run much programs in a runtime environment,  Java programs seem to go slow for me compared to non-java programs, you can show me all the studies and proof to the contrary, but they just respond slower...

I think companies should use toolkits such as QT or GTK though instead of using the WIndows API for their programs, personally I always wondered why programs weren't generally made with QT, but then I realised that you needed to buy a license to make proprietary programs.
So maybe GTK is the way to go. The majority of things can I'm assuming be done like that, QT allows you to do everything in a multiplatform way, including file IO and sockets, so I'm assuming GTK would also allow this, though i'm not sure.

Of course even if not, File IO and sockets and very similar and it would only take an extra couple of LoC to make it work multiplatform usually, GUI seems to be the main limitation for most multiplatform app.s

I can appreciate your point - although it does depend on the application your running regarding speed.  I have two rich client Java apps that I run and they are as fast as anything written in C++ - at least to my sense.  However, a few Java development environments allow you to compile apps to native code - Mono for example -so that is one available solution to that issue.

---

### Post by happysmileman on 2008-01-07
Personally I would just prefer to see more things nowadays written in C/C++, I don't really have a reason for it, I think I just kinda think of a binary executable (or code to make one) as more reliable and professional than something that requires a runtime environment to run in.

Of course I can't really comment on performance of natively compiled Java, I also think that having garbage collection as a language feature is just plain wrong, though I'm kinda obsessive about stuff like that, and to 99% of people it doesn't matter at all and my opinion I suppose doesn't really matter on this.

(I'm excluding scripting llanguages from these pet peeves of mine, because obviously they're just intended for small tasks or for quickly developing something.

---

### Post by lespaul_rentals on 2008-01-07
Just curious, but can't most programming languages run on all platforms?  When I think of C++, Python, etc. I'm pretty sure all kinds of OS'es will run them so long as they have support.  And no offense to any Java coders out there, but I've always found Java to be very clunky and slow.  It wouldn't be my first choice of programming language if I were to buy a program.

---

### Post by GMU_DodgyHodgy on 2008-01-07
> **happysmileman said:**
> Personally I would just prefer to see more things nowadays written in C/C++, I don't really have a reason for it, I think I just kinda think of a binary executable (or code to make one) as more reliable and professional than something that requires a runtime environment to run in.

Of course I can't really comment on performance of natively compiled Java, I also think that having garbage collection as a language feature is just plain wrong, though I'm kinda obsessive about stuff like that, and to 99% of people it doesn't matter at all and my opinion I suppose doesn't really matter on this.

(I'm excluding scripting llanguages from these pet peeves of mine, because obviously they're just intended for small tasks or for quickly developing something.

I would agree about a binary executable.  But likes I said - there are IDEs that allow Java apps to be compiled down to native code.  

I think the trend is towards platform languages like Java and .Net.  I have to say Java is not burdensome and garbage collection is something that is catching on.

---

### Post by PetePete on 2008-01-07
> **lespaul_rentals said:**
> Just curious, but can't most programming languages run on all platforms?  When I think of C++, Python, etc. I'm pretty sure all kinds of OS'es will run them so long as they have support.  And no offense to any Java coders out there, but I've always found Java to be very clunky and slow.  It wouldn't be my first choice of programming language if I were to buy a program.

yes c++ can run on different OSs but if you program and compile an app in linux it is different than writing it for windows, due to librarys and having to communicate iwth Windows API directly instead of through the JVM 'layer' ..

---

