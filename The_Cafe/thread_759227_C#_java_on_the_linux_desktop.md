---
title: "C# java on the linux desktop"
date: 2008-04-18
forum: The Cafe
---

### Post by ihavenoname on 2008-04-18
Well, this is more out of curiosity than anything. 

**Background**
See gnome apparently after getting sick of using C for everything started looking for alternate languages. Lately it's been Mono/C# well since java has no opensourced, and since there is less worry of your platform being sued to the ground using java I thought we'd see more java stuff replacing C#. That hasn't happened. Of course there is the other side that hate mono and C# and anything to do with Microsoft .NET.  Interestingly of the two largest Linux venders Novell seems to lean more towards mono and red hat seems to be more towards java (though we have no indication of what red hat prefers for the desktop). 

**Poll**
In any case I wanted to see where linux users stood on this. The choices in this poll above are:
1. I wouldn't use anything mono related.
2. I would rather they use java.
3. I would rather they use C#.
4. I wouldn't use anything java related.
5. I would rather they not use either of these languages.

please explain your position below. 

Discussions of the languages and things related to programming are fine, but I'm talking more from an end users perspective.

I know many of you feel this has been hashed out before but I think there have been some subtle changes to the situation. More importantly though, I am trying to decide which language to use for the things I want to make. Looking at the languages both provide the tools that I would need, I just want to see what end users think.

Thank you.

P.s. please let's keep this civilized.

---

### Post by LaRoza on 2008-04-18
> **ihavenoname said:**
> Well, this is more out of curiosity than anything. 

**Background**
See gnome apparently after getting sick of using C for everything started looking for alternate languages. Lately it's been Mono/C# well since java has no opensourced, and since there is less worry of your platform being sued to the ground using java I thought we'd see more java stuff replacing C#. That hasn't happened. Of course there is the other side that hate mono and C# and anything to do with Microsoft .NET.  Interestingly of the two largest Linux venders Novell seems to lean more towards mono and red hat seems to be more towards java (though we have no indication of what red hat prefers for the desktop). 


Java is GPl'd for the most part now. Mono is free. C# is now an ECMA standard.

I fail to see any issues with this. I personally don't use either language (although I know Java) as they are difficult to work with compared to other languages.

---

### Post by Redache on 2008-04-18
I think it depends really. Java is an ok language but the overhead from running a Virtual Machine would be a bit weird, although I think Solaris's desktop manager is Java (Wrong?, Right?) and that seems fairly snappy.

The problem with C# is due to it's association with Microsoft it's seen as a hacked and crap language, which might be the case but it's becoming more and more popular in the corporate world so its a necessary evil I guess.

I don't really have a preference, whatever works best. I personally find that most programs written in Java tend to be from developers who don't necessarily understand the overhead from the Virtual Machine so they do tend to be slower.

---

### Post by TeraDyne on 2008-04-18
I like JEdit and programming in Java, an I'm trying to learn C#, so I really have no preference.

My stance on the whole thing: "If it works, is efficient, can be used to create awesome applications, and there's no legal problem in using it, then I'll use it."

You should have a "No Preference"\"Don't Care Either Way" option in that poll.

---

### Post by Tomosaur on 2008-04-19
I tried C# on Windows a while back, and I just didn't like it that much. I've never tried using Mono on Linux. I'm pretty happy just using Java or any of the other languages I know. I have a soft spot for Java because it's one of the first languages I ever really spent any real amount of time with.

---

### Post by ihavenoname on 2008-04-19
Hmm, ok let me say it this way. Is there anyone that wouldn't use a program because it was made in java or using mono technology.

---

### Post by LaRoza on 2008-04-19
> **ihavenoname said:**
> Hmm, ok let me say it this way. Is there anyone that wouldn't use a program because it was made in java or using mono technology.

Anyone without Java or Mono installed.

---

### Post by Mr. Picklesworth on 2008-04-19
I don't care what VM a program uses, but I generally find desktop-oriented Java programs to be either slow, ugly, unintuitive or all three. Unsure whether the language is to blame at this point, but it has been my observation that Java tends to go with a "one size fits all" approach of cross-platform, aiming not just to work on all architectures but for one program to be identical on every operating system it is thrown at. The trick seems to be having a very ugly GUI toolkit that every Java program uses, which fits nowhere but "looks like Java" from a mile off.

Project Looking Glass is interesting, and that's Java, for some reason known only to them. Oh, wait, it's Sun; the reason is obvious! To make Java actually look useful for something.
That desktop environment could be rewritten in *Python* and run faster than it does now. Okay, it's still pretty cool; right now most applications and desktop computing metaphors are for two dimensional graphics, but I understand the concept there. Just starting from scratch, using 3D environments and futuristic input / output methods, could lead us to some very cool stuff.

A book I am reading uses a little hardware simulator written in Java. It is pretty tidy and quick, and while it feels completely ugly and out of place in my Ubuntu desktop, it does least work. It's pretty nifty that they can have just a single download for every platform that "just works". I guess there is something to be gained in having all the expected libraries packaged right with the VM.

I am certain that I use Java, or at least the output of Java, routinely as I browse the web. However, as a rule of thumb, I try to avoid Sun's stuff. They are very inconsistent when it comes to open-sourcing code. For example, Sun is beginning to close up parts of MySQL, which can't end well:
[http://developers.slashdot.org/article.pl?sid=08/04/16/2337224](http://developers.slashdot.org/article.pl?sid=08/04/16/2337224)

As for "Just Working", so does open source code distributed through repositories. Launchpad PPAs, for example, let us have just that without the torment and suffering associated with special runtime environments.

---

### Post by Spr0k3t on 2008-04-19
Personally I don't like Mono.  I don't have any mono applications installed on my system.  That said, I think the idea of the .net structure is brilliant in a programming aspect.

I'll use Java apps if no native app is available, but I'll hold out on C# apps until there is a native app or Java app that does the same.

Native > Java > > > > > > > > .Net

---

### Post by ihavenoname on 2008-04-21
I've read quite a bit of complaints (not just here) on java desktop applications. Let me just take a moment to explain that if an application has the "java look" it's using swing. Swing is incredible technology when you look at it, but as an end user it can be frustrating as it is prone to slow downs and such. If I were making a java program I would use a different toolkit that was also cross platform, like gtk, or qtjambi. 

 Interms of non-gui speed java is in general (depends on the libraries used and functions etc.) faster than mono ( actually faster .Net C# too).  Again there are too many things at play here so that is probably overly generalized. 

 If you want to see java running farely quickly, try the demo available here [http://dist.trolltech.com/developer/download/webstart/index.html](http://dist.trolltech.com/developer/download/webstart/index.html). Make sure that you have java webstart installed. I reccomend downloading the webstart file and then running it. These demos are also available in the qtjambi-demos file through synaptic.  The examples in the demo are all runing java + qt. Most of these demos show no difference from C++ applications. 

After reading more about the differenct technologies, I am finding that while mono as some interesting technology going on, I prefer the java technology but I don't want to get too much into that here.

---

### Post by GMU_DodgyHodgy on 2008-04-21
How java runs and looks depends a lot on the person coding it.

I use on Java Desktop app - religiously - its a personal finance app that runs as fast as any native Gnome desktop app and looks just fine - in fact it borrows the look and feel of the desktop its running on (in this case GTK+).  

I have no problem with either Mono or Java.  Just make a good, tight, solid application that does what users need.  The only problem with manages code languages like .Net (Mono) or Java is there are a ton of libraries - the programmer needs to be selective in only using those libraries needed build and run the app - some throw the kitchen sink in there.  In Java - if you use the base SDK and maybe JDBC and some object pooling - you can get a tight - fast - and nice application.

---

### Post by mehaga on 2008-04-21
hmmm...

For relatively simple desktop applications, I would use (both as a programmer and a user) QT. It is absolutely fantastic. But it doesn't offer  much in rapid app. development and I think it would be difficult to build large 'enterprise' apps with it. Java and C# both offer a lot more. For Ubuntu to be widely accepted, get in more offices, homes... it needs those enterprise apps and therefore something like Java or .NET.

Java apps used to be slow but they are not any more. They are still ugly, but mostly because of programmers who are too lazy to change the default look and feel, let alone spending time to design their GUIs. Last time I checked, Mono wasn't offering much. For what can be done with it, I'd rather use QT. 

As far as 'trouble' caused by installation of a VM, be it jvm, mono, .net... I can't see how several MB download could hurt anyone, and I can't think of any configuration needed for them to run.

What I think is more important than any of that stuff, is that we need more apps! :) Free, non-free, open source or closed... I don't really care what you use to make them, just keep them coming :D

---

### Post by angryfirelord on 2008-04-21
> **LaRoza said:**
> Mono is free. C# is now an ECMA standard.
OOXML is also an ISO standard and we all know how that turned out. The problem is that you don't know what certain "patented" Microsoft technologies goes into the development of mono. I'd rather not take the chance of an impending lawsuit if Microsoft gets its hands too deep within its development.

---

### Post by jdong on 2008-04-21
> **angryfirelord said:**
> OOXML is also an ISO standard and we all know how that turned out. The problem is that you don't know what certain "patented" Microsoft technologies goes into the development of mono. I'd rather not take the chance of an impending lawsuit if Microsoft gets its hands too deep within its development.

There are no patented Microsoft technologies or code that goes into Mono. Mono in fact has a very strict policy regarding cross-pollination of its codebase from Microsoft .NET.

Personally with to the original question, I don't care. I don't think it's possible or fair to pre-judge an application based on the language it's written in. I've used some very fast and efficient Java/.NET apps and also used some horrendously slow and difficult to set up C stuff too. A programmer should use whatever language he likes for the job.

---

### Post by jrusso2 on 2008-04-21
Personally I don't care what apps are coded in long as the work well.

I would prefer not to have to install mono if I don't have to but if allows me to run something like Paint.net which hopefully one day it will, I would gladly use it.

---

### Post by Tim Sharitt on 2008-04-21
I don't really have a preference. I use sometimes use java (I personally prefer C and python) for apps that I don't feel warrant coding from the ground up in C and all the extra overhead in debugging, especially pointers and memory management (I can barely remember what I did 5 minutes ago much less what the hell that pointer goes to). I can see how using either one most likely make the programmers job easier and (in theory) they can produce better applications more quickly. Still, I hate having to to install a VM or other framework to run my programs. It would be nice if everyone just used the best one (and if  just used the best os I could play all my games on linux:) ).

---

### Post by ihavenoname on 2008-04-22
> **vekaz said:**
> 

Java apps used to be slow but they are not any more. They are still ugly, but mostly because of programmers who are too lazy to change the default look and feel, let alone spending time to design their GUIs. Last time I checked, Mono wasn't offering much. For what can be done with it, I'd rather use QT. 

Have you looked into Qtjambi? It's java using qt. I think if your making linux specific apps with java, qt-jambi and java-gnome are the way to go. You might want to look into qtjambi at this address:[http://trolltech.com/products/qt/jambi](http://trolltech.com/products/qt/jambi)

> **GMU_DodgyHodgy said:**
> ...The only problem with manages code languages like .Net (Mono) or Java is there are a ton of libraries - the programmer needs to be selective in only using those libraries needed build and run the app - some throw the kitchen sink in there.  In Java - if you use the base SDK and maybe JDBC and some object pooling - you can get a tight - fast - and nice application.

Hmm...just a heads up, java does not import all of a library, just the parts that are used. For example, if you do something like


```
import javax.swing*
```

and all you use is a message box. Java will only import the parts of javax.swing that are used. Unused classes will not be compiled in. But you are correct you have to be careful what libraries you use, some might not be very good. Also, it's important to desgin the application correctly and then profile the code for bottlenecks, netbeans has a very nice gui profiling tool. Also, java itself has a built-in profiler launching the application/class with the following line will allow you to see where issues are occuring. You might want to send the output to a text file for easier viewing.

```
java -Xprof <class> 
``` 

> **Tim Sharitt said:**
> Still, I hate having to to install a VM or other framework to run my programs. It would be nice if everyone just used the best one (and if  just used the best os I could play all my games on linux:) ).

WIth current developments you might have the java vm installed by default. I think once openjdk finishes making a free version of java web start or sun releases the code, we are very likely to see java pre-installed on Ubuntu. The mono runtime is, if I am not mistaken currently installed by default in Ubuntu. (Tomboy is, so I assume so is mono).  


There are a lot of misconceptions that exist about java (and to some extent C#) that I feel should be correct and I think discussions like this tend to bring them out. Ximian & the mono co. have done a good job of delivering applications written in mono and sort of pushing them into gnome (for obvious reasons they have some sway there).  This serves to swing the momentum in C#'s direction. But I think java, and the java platform really have a lot to offer software in general.  There are already some games being ported to java, that is showing some promise for cross platform games (still java is probably not an ideal platform for most game developers since they tend to want to push performance  limits and C and C++ are the best tools for that). 

One thing this thread has reminded me of is that people who are not programming oriented couldn't care less about the technology behind their application they just want it to work. I forget this because am always trying to dig at what is behind my favorite applications.

---

### Post by jdong on 2008-04-22
ihavenoname  said a lot of the things I wanted to say about misconceptions regarding Java, Mono, and other runtime environments. They don't necessarily imply poor performance, heavy RAM usage, non-native integration, dependency hell, or any of the other reputations people tend to attach on these frameworks. At least no more than any other framework in any other language carries.

---

### Post by Trail on 2008-04-22
I'd rather NOT have a desktop environment written in Java. Granted, the real-time optimizers, garbage collectors etc have evolved a lot, but I will not betray my trust and love for C++. I feel a Java desktop would be slow and sluggish. Maybe prejudice, I don't know. But still. And I always liked compiling my stuff with -O2/3. -march=core2 etc, if you know what I mean...

And I also don't get the fact that "gnome developers got bored of C and want to use another language". Huh? ...

To tell the truth, I'm probably going to use KDE4.1+ in any case, just thought I'd share my thoughts.

---

### Post by jdong on 2008-04-22
> **Trail said:**
> I'd rather NOT have a desktop environment written in Java. Granted, the real-time optimizers, garbage collectors etc have evolved a lot, but I will not betray my trust and love for C++. I feel a Java desktop would be slow and sluggish. Maybe prejudice, I don't know. But still.

Prejudice. Dynamic programming paradigms are becoming increasingly popular and actually allow a JIT to optimize code BETTER than static compile-time heuristics.

> 
 And I always liked compiling my stuff with -O2/3. -march=core2 etc, if you know what I mean...


You know, most of the times that makes no difference, breaks code (i.e. strict aliasing), or makes code slower by fattening up binaries to use up more disk IO and not fit in L2 cache anymore, right? :)

---

### Post by jespdj on 2008-04-22
> **Redache said:**
> I think it depends really. Java is an ok language but the overhead from running a Virtual Machine would be a bit weird, although I think Solaris's desktop manager is Java (Wrong?, Right?) and that seems fairly snappy.
And the overhead of the Mono Virtual Machine is not weird? It's exactly the same as with Java. I don't know the exact technical details, but most likely Sun's Java VM is faster and more efficient than Mono's VM. Sun's JVM with the Hotspot just-in-time compiler is very sophisticated.

---

### Post by kripkenstein on 2008-04-22
Java, C#...? If there's a non-C language that is popular for coding Linux desktop apps, it would be Python. Given Python's rising popularity overall (as shown in Google App Engine, for example), this will probably continue.

A note regarding Mono:
> jdong:
There are no patented Microsoft technologies or code that goes into Mono

According to the [Mono FAQ]("http://www.mono-project.com/FAQ:_Licensing#Patents"), that isn't accurate:
> 
Mono implements the ECMA/ISO covered parts [...] The core of the .NET Framework, and what has been patented by Microsoft falls under the ECMA/ISO submission. Jim Miller at Microsoft has made a statement on the patents covering ISO/ECMA, (he is one of the inventors listed in the patent): here

Mono state clearly that they are implementing patented technology. The 'reassurance' is a mailing list message by an individual in Microsoft, that says the patents are available royalty-free. This is far from an official position.

That said, I'm not anti-Mono. I think it's an important FOSS project. But we need to be clear about the risks.

---

### Post by Trail on 2008-04-22
> **jdong said:**
> You know, most of the times that makes no difference, breaks code (i.e. strict aliasing), or makes code slower by fattening up binaries to use up more disk IO and not fit in L2 cache anymore, right? :)

Perhaps. Depends on the type of operations... you'd probably need to measure to tell the difference for each specific program. And Java certainly is faster on new/deletes due to its heap (and that it's a language optimised for that).

Still, more often than not, Java applications feel (to me) heavier that a native counterpart... and their visual presentation more often than not looks out-of-place (although that's improved a lot lately - but so did Qt4).

Prejudiced or not, I don't know, since I love C++ and find Java annoying (though admittedly Netbeans has plays a large factor in me hating it) but I would prefer not to have Java apps on the desktop :)

---

### Post by ihavenoname on 2008-04-22
> **Trail said:**
> 

And I also don't get the fact that "gnome developers got bored of C and want to use another language". Huh? ...

To tell the truth, I'm probably going to use KDE4.1+ in any case, just thought I'd share my thoughts.

Bored may not be the right word. They got frustrated with. That is C proper, not C++. It makes it very difficult to manage a project such as gnome.  There is an interview with Miguel De Icaza where he implies that this was one of the main issues behind the move towards C#. 

One thing to keep in mind, many desktop applications spend a lot of time just sitting there on idle, out right speed is not always a justification for the development time. Look at all the C# apps and how quickly they are being developed and compare that to some of the older, slower to move C apps. Don't get me wrong I love C++ just as much as the nice guy, it's just that sometimes going full blow C++ is not the way to go. Especially if you want to reach a wide audience, for that nothing beats java (well..unless you count web applictions) 

KDE 4 is very nice, though not yet feature complete. I have already started moving in the direction of kde, though this is mostly because of qt being nicer for me to use than gtk.

---

### Post by red_Marvin on 2008-04-22
I'm with Tim Sharitt on this one for stuff I need exact control I use C, and for more high level stuff python fits me better, java is somewhere in the middle as I see it and falls in between as something too cumbersome to bother with compared to the relative benefit. I haven't tried C# for much the same reasons.

I'm suspicious of MS involvement in OSS projects as they aren't exactly known to willingly benefit anybody except themselves, but I admit that I don't really have enough knowledge on the subject to add anything to the subject.

---

### Post by jdong on 2008-04-22
> **jespdj said:**
> And the overhead of the Mono Virtual Machine is not weird? It's exactly the same as with Java. I don't know the exact technical details, but most likely Sun's Java VM is faster and more efficient than Mono's VM. Sun's JVM with the Hotspot just-in-time compiler is very sophisticated.

Sun's HotSpot VM is the best there is. Everyone who cares about JIT performance licenses it -- including Microsoft's .NET Framework.


However, depending on your kind of work you might not ever feel this difference. If you're factoring large primes, sure, you will see this difference (and probably should not be using a high-level language), but if you are writing an average desktop app, you are highly unlikely to feel the overhead of the language runtime.

Heck most of the slow programs I've used (that I could see the source to) are due to poor programming -- poor choice of data structures, poor choice of algorithms, etc, NOT due to the limitations of their runtime. Some smart rewriting and profiling of the codebase could yield a much better speed improvement than blindly moving off to another language. Almost all of these "slow" languages (with the notable exception of Java) have extremely straightforward methods of allowing the programmer to break off expensive, slow code and reimplement it in C. That's exactly what the folks at bzr did to improve performance, and what the folks at Yum did to speed up metadata hashing.


Personally, I do most of my coding in Python and Ruby, which are SEVERAL orders of magnitude "slower" than Java/Mono. CPU and disk are cheap -- my time is not. Furthermore, the stuff I write is mostly a scripting interaction with other libraries primarily in C, so it's virtually all native code anyway.

---

### Post by haTem on 2008-04-23
The quality of a program depends as much on the programmer as on the language used. Developers should use what they're best at. That will make up for everything else the majority of the time.

If I had to choose between the two, I would probably pick Java. Java outperforms C# in almost every benchmark I have seen. In general though, I prefer C++/native applications.

In my personal experience, I don't think managed code provides as much productivity and portability as its proponents claim. The majority of my problems are due to algorithmic errors, errors in my logic, etc, which would happen in any language.

C++ portability can easily be achieved by using the correct libraries, and if you're developing on linux you're probably already using them (gtk, qt, boost, etc). The only caveat to this is that you will have to compile multiple binaries.

Also I find a lot of tasks easier to accomplish in C++ (one recent example is that I could not find a "multimap" equivalent in Java -- Java gurus help me out! :D). I'm sure there are some cases where the opposite is true.

This is probably due to me being more proficient in C++ than Java, so take this with a grain of salt :).

One problem with Java is that qtjambi/java-gnome are not very widespread distribution-wise, and everyone hates the swing "java look", leading to fewer desktop applications using Java. Mono and gtk# are now solidly integrated into gnome thanks to apps like tomboy. If a popular java-gnome app comes out, I think we will see the same thing happen, so this shouldn't be that big of a deal.

---

### Post by jespdj on 2008-04-23
> **jdong said:**
> Personally, I do most of my coding in Python and Ruby, which are SEVERAL orders of magnitude "slower" than Java/Mono. CPU and disk are cheap -- my time is not. Furthermore, the stuff I write is mostly a scripting interaction with other libraries primarily in C, so it's virtually all native code anyway.
You should try [JRuby](http://jruby.codehaus.org/). There's a new release (1.1) which includes a Ruby-to-bytecode compiler. The JRuby developers say that JRuby now runs faster than the original Ruby implementation.

There's also [Jython]("http://www.jython.org/Project/index.html"), but I don't know much about it.

---

### Post by jdong on 2008-04-23
> **jespdj said:**
> You should try [JRuby](http://jruby.codehaus.org/). There's a new release (1.1) which includes a Ruby-to-bytecode compiler. The JRuby developers say that JRuby now runs faster than the original Ruby implementation.

I will give it a shot, but the ability to refactor code out to native extensions IMO is more important than faster Ruby bytecode and the last time I checked, anything with Java in the name made it more difficult to do this.

> 

There's also [Jython]("http://www.jython.org/Project/index.html"), but I don't know much about it.
Jython is actually slower than CPython, but IronPython is faster for most tasks (Python on .NET/Mono) though both are subsets of Python 2.3-like syntax.

---

