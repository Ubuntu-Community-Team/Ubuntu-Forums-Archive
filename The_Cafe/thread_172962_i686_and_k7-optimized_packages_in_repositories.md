---
title: "i686 and k7-optimized packages in repositories"
date: 2006-05-09
forum: The Cafe
---

### Post by hermesrules on 2006-05-09
I've been following several threads about speed on both KDE and Gnome, as well as on other distributions. I am myself a user of an Athlon XP-M-powered laptop, and it seems to me like a waste of resources to run applications optimized for 486 at best. Even though I do understand that in this way more users, especially in places, where computers cannot be upgraded every six months, will be able to use the system I still think that a lot of users would benefit from multiple architecture support.

So I decided to start a poll to probe what other Ubuntu users think.

Please, vote! The question is:

WHAT DO YOU THINK ABOUT HAVING REPOSITORIES WITH i686 and k7-OPTIMIZED PACKAGES?

1) I will definitely switch to those to be able to use the full power of my processor.

2) I will be happy with i586, no need for i686 or k7.

3) I do not need optimized packages, and will not use them.


Please post your comments or thoughts too!

---

### Post by helpme on 2006-05-09
As in 99.99% of the cases it will make no difference whatsoever, I really can't see why developers should do this. This would only mean more work for devs for essentially nothing and confused noobs.

---

### Post by prizrak on 2006-05-09
We already have kernels that are optimized for different CPU's there is little need for other packages to be compiled in such a way as they all talk to the kernel anyway.
Also if you want high optimization you can get an optimized gcc for your system and compile all your packages. I must say that the speed difference is negligeable if there is any.

---

### Post by Technoviking on 2006-05-09
At one time I had Hoary and Gentoo both running on an AMD machine at home. Other than boot-up, which Gentoo was fastest since it loaded less, I found very little speed difference in Gnome or launch larger programs like Firefox or OpenOffice.

Gentoo was tweak for my machine settings, so in theory it should have been faster :)

---

### Post by endersshadow on 2006-05-09
Where's the option for, "I'm already taking advantage of this feature that has existed since the beginning of Ubuntu, so please quit it with these pseudomovements"?

---

### Post by briancurtin on 2006-05-09
[plug]just use arch, everything is optimized for i686[/plug]

---

### Post by hermesrules on 2006-05-09
[QUOTE=endersshadow]Where's the option for, "I'm already taking advantage of this feature that has existed since the beginning of Ubuntu, so please quit it with these pseudomovements"?[/QUOTE]

In fact, it would help if you explained where this option is, so that other can take advantage of it. This is just a POLL, not a petition, so please be considerate, and if you think that there are ignorant people on this forum, help them learn what they don't know, and you obviously do.

Thank you.

---

### Post by endersshadow on 2006-05-09
[QUOTE=hermesrules]In fact, it would help if you explained where this option is, so that other can take advantage of it. This is just a POLL, not a petition, so please be considerate, and if you think that there are ignorant people on this forum, help them learn what they don't know, and you obviously do.

Thank you.[/QUOTE]

In Syanptic, just search linux-image and voila.

---

### Post by Lovechild on 2006-05-09
Show me the data to undeniably prove that the performance increase is:

a) there at all
b) significant enough to justify the extra load on the buildsystem, system complication and user confusion
c) does not under any circumstances introduce harmful regressions of any kind

untill then, gather data, write me a whitepaper and shut up - ricerhood is nothing to be proud of, especially since we get this type of question at least once a month if not bi-weekly.

Ample evidence is the foundation of all good decisionmaking.

---

### Post by briancurtin on 2006-05-09
bahaha Lovechild is hilarious...

---

### Post by hermesrules on 2006-05-10
[QUOTE=Lovechild]Ample evidence is the foundation of all good decisionmaking.[/QUOTE]


Frankly, I don't quite understand what has triggered such a response on your side. Maybe me being relatively new to these forums, or the fact that I am just a user, who happens to like or dislike certain features, makes me in your eyes disrespectful in some way. I don't dispute the last line of your post, but who are you and who am I to write you a whitepaper, exactly? For now, the types of whitepapers I write, and I need assure you - they are all based on ample evidence and sometimes statistical modeling, and always on extensive research, have nothing to do with Linux or computers. The latter are my hobbie, and forgive me for feeling a little confused (to say the least) by your response.

One of the things I learned since I heretically started this poll 12 hours ago, is that optimization of every single package does not make sense, and is neither worth it, nor will it bring any performance boost (or so I am inclined to think because people who seem to oppose the purposefullness of this poll seem to be way more aggressive in their opinions). I GET IT. I also do understand that it would require a significant amount of work. But hey, there are 21 (as of now) other people, who must be just as confused about optimization as I am, since that's what the poll shows. If people are careful enough to read through all the comments, this number may not go higher.

Lastly, please read the poll and the introductory message carefully. I am not trying to start a petition, which I will then forward to the developers with an angry message that they absolutely need to do this. If you are among the developers, then you already have my respect, I need assure you I won't insist on optimizations. I did not start the poll to do any research either (as this would hardly even qualify as a purposive sample). As I said, I learned something though, and if you look at the poll results, you will probably learn something too, especially talking of ample evidence. There are 21 other people you would need to yell at.

If this poll annoys you so much, please ask the proper people to remove it. And keep posting.

---

### Post by bigdaddyjohn on 2006-05-10
First, why such negative responses to a Poll? If you don't think it's a good idea, simply vote against it. He is just asking for data. Relax. 

Second, I'd love the prepackaged version. I'm new to Ubuntu and appreciate the packaged form. For example, I tried to use the K7 kernel. It loaded faster, displayed menu's faster, etc. Tremendously fast, you ask? I can't say as of yet. However, I like the others before, discovered that it no longer had the wireless settings available, "Out of the Box". Pitty.

Hold the "read the previous posts and search the forum" banters. I do just that, as I have time. Working full time, new baby, older children, wife, money, house, etc (also known as a life), all prohibit day long searches and experiments. I do enjoy the challenges however some items working without tinkering are very helpful. As others have posted, the wireless support is key. Not everyone who is trying Linux is interested in recompiling packages, kernels, etc. If you believe they are, you are sadly mistaken and have not listened to what the masses have been saying since the mid 1980's.

Getting the most performance out of my older laptop is key. The less tinkering the better, at least for me. I don't have the extra money to buy the latest and greatest processors nor do I plan on replacing what I have. One of the touted advantages of Linux has been the ability to utilize a mediocre system that would compete with a new Windows machine. I fall into that category. So for me at least, yes I would gladly utilize a specific, customized format.

Remember, the Ubuntu Help file states the following:
"Ubuntu is available in flavours for the i386
                        (386/486/Pentium(II/III/IV) and Athlon/Duron/Sempron
                        processors), AMD64 (Athlon64, Opteron, and new 64-bit
                        Intel processors), and PowerPC (iBook/Powerbook, G4 and
                        G5) architectures."

I for one didn't expect the problems with lack of working wireless simply by looking for my particular "Flavour".

bigdaddyjohn

---

### Post by helpme on 2006-05-10
> Do you provide packages compiled with processor-specific optimisations?

And if so, where can I find them?

    *      Optimised kernels can be obtained by installing the linux-686, linux-k7, etc. packages. Search for "linux" with Synaptic, aptitude or apt-cache. (From the menu: System - Accessories - Synaptic Package Manager)
    *      An optimised C library is installed by default, in the libc6-i686 packages.
    *      Optimised cryptography routines for i586- and i686-class systems are included with the OpenSSL library and used automatically.
    *      Ubuntu packages are generally built with nearly all generic compile-time optimisations which do not involve increasing code size (gcc -O2), except where the package maintainer deviates from this (for example, packages intended for debugging are often less optimised, as this eases debugging). Smaller code allows better utilisation of cache memory.
    *      Ubuntu packages for the i386 architecture are compiled using the i486 instruction set (-march=i486), with instruction choices based on the Pentium 4 processor (-mcpu=pentium4). This combination provides benefits for modern processors without sacrificing compatibility with older and embedded devices. A comprehensive experiment to evaluate the effectiveness of more aggressive processor optimisations for all Ubuntu packages is a prerequisite for any global change in compiler optimisations.


[http://www.ubuntu.com/support/faq](http://www.ubuntu.com/support/faq)

You'll also find some interesting answers here:
[http://www.ubuntuforums.org/showthread.php?t=13753](http://www.ubuntuforums.org/showthread.php?t=13753)


Hope this clears things up a bit and guys, there really is no need for a flamewar over this.

---

### Post by woedend on 2006-05-10
lovechild makes a good point, even if in an over the top negative manner.  Seriously, you get tired of reading of everyone who has the uberest optimized tweaked system ever.  I don't take that out on the OP or any one person, and I don't mean any offense to you in particular, but the group as a whole.  686 optimized really doesn't make any difference a user would see, and that's been shown more than once.

---

### Post by Buffalo Soldier on 2006-05-10
I agree with lovechild. 686 optimized may sound enticing, but I don't think its worth the trouble. Eventhough Mark has the [cash to spare](http://news.zdnet.co.uk/0,39020330,39267955,00.htm), but I think it should focus on other stuff.

---

### Post by ubuntu_demon on 2006-05-10
[QUOTE=helpme]
Hope this clears things up a bit and guys, there really is no need for a flamewar over this.[/QUOTE]

I agree. You guys should be a bit more nice to eachother.

Here's also an older thread about this topic :
[http://ubuntuforums.org/showthread.php?t=26706&page=1](http://ubuntuforums.org/showthread.php?t=26706&page=1)

[QUOTE=helpme][http://www.ubuntu.com/support/faq](http://www.ubuntu.com/support/faq)

Ubuntu packages for the i386 architecture are compiled using the i486 instruction set (-march=i486), with instruction choices based on the Pentium 4 processor (-mcpu=pentium4). This combination provides benefits for modern processors without sacrificing compatibility with older and embedded devices. A comprehensive experiment to evaluate the effectiveness of more aggressive processor optimisations for all Ubuntu packages is a prerequisite for any global change in compiler optimisations
[/quote]

I wonder are there users running Ubuntu on i486 hardware ? How much memory is needed for a server install ? If it's 32 mb then the majority of the 486 machines won't even able be able to install ubuntu.

IMHO compiling with march=i586 and mcpu=pentium4 will only be a very small performance difference. But if it's true that there are almost no 486 computers running Ubuntu then it might be worth the effort (maybe).

Just My Opinion. Correct me if I'm wrong.

---

### Post by Lovechild on 2006-05-10
[QUOTE=Buffalo Soldier]I agree with lovechild. 686 optimized may sound enticing, but I don't think its worth the trouble. Eventhough Mark has the [cash to spare](http://news.zdnet.co.uk/0,39020330,39267955,00.htm), but I think it should focus on other stuff.[/QUOTE]

It is not that it's not worth it, it's just a completely irrelevant question - dropping support for pre i686 is on the plan not for speed reasons (because frankly every study shows that the increase is hardly meassurable) but for testing reasons. [1]

We get on this forum a question like this one maybe 2 times a month, by the same kind of bozos who do not do research before even proposing it. I'm appaled by the disregard of science in this whole deal, I see no numbers only an assertion that "this is faster" without considering the consequences.

[1] [http://people.ubuntu.com/~scott/20060131_dropping-pre-i686_jbailey-doko.ogg](http://people.ubuntu.com/~scott/20060131_dropping-pre-i686_jbailey-doko.ogg)

---

### Post by Lovechild on 2006-05-10
[QUOTE=ubuntu_demon]I agree. You guys should be a bit more nice to eachother.

Here's also an older thread about this topic :
[http://ubuntuforums.org/showthread.php?t=26706&page=1](http://ubuntuforums.org/showthread.php?t=26706&page=1)



I wonder are there users running Ubuntu on i486 hardware ? How much memory is needed for a server install ? If it's 32 mb then the majority of the 486 machines won't even able be able to install ubuntu.

IMHO compiling with march=i586 and mcpu=pentium4 will only be a very small performance difference. But if it's true that there are almost no 486 computers running Ubuntu then it might be worth the effort (maybe).

Just My Opinion. Correct me if I'm wrong.[/QUOTE]

Note if we use nptl, I believe the currency minimum required CPU is the Pentium

---

### Post by ubuntu_demon on 2006-05-10
[QUOTE=Lovechild]Note if we use nptl, I believe the currency minimum required CPU is the Pentium[/QUOTE]
I don't understand your remark. Please elaborate.

libc6 and my kernel (linux-686) already have NPTL support.

$getconf GNU_LIBPTHREAD_VERSION
NPTL 2.3.6

$ apt-cache show libc6-i686 | grep NPTL
 This package includes support for NPTL.

more about NPTL :
[http://en.wikipedia.org/wiki/NPTL](http://en.wikipedia.org/wiki/NPTL)

---

### Post by Kvark on 2006-05-10
The best way to optimize your system for speed is to choose the lightest program that can do the job for each task... Does Abiword have enough features for your word proccessing needs? Then use that instead of Open Office Writer... Does XFCE have enough features to be a usable desktop environment for you? Then use that instead of Gnome... And so on for each program, then you'll see a speed increase.

---

### Post by ubuntu_demon on 2006-05-10
[QUOTE=Kvark]The best way to optimize your system for speed is to choose the lightest program that can do the job for each task... Does Abiword have enough features for your word proccessing needs? Then use that instead of Open Office Writer... Does XFCE have enough features to be a usable desktop environment for you? Then use that instead of Gnome... And so on for each program, then you'll see a speed increase.[/QUOTE]
don't forget prelink and running the right kernel :)

or faster booting by disabling some services : [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by Lovechild on 2006-05-10
[QUOTE=ubuntu_demon]I don't understand your remark. Please elaborate.

libc6 and my kernel (linux-686) already have NPTL support.

$getconf GNU_LIBPTHREAD_VERSION
NPTL 2.3.6

$ apt-cache show libc6-i686 | grep NPTL
 This package includes support for NPTL.

more about NPTL :
[http://en.wikipedia.org/wiki/NPTL](http://en.wikipedia.org/wiki/NPTL)[/QUOTE]

This was pointed out to me in an earlier discussion:
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=103078](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=103078)

I don't know if Ubuntu uses NPTL is quite the same way as Fedora but it does seem quite clear that we naturally obsolete certain platforms just in the face of technological advances. NPTL being the only actively developed upstream solution, if we don't do it now we will have to eventually.

---

### Post by Lovechild on 2006-05-10
[QUOTE=Kvark]The best way to optimize your system for speed is to choose the lightest program that can do the job for each task... Does Abiword have enough features for your word proccessing needs? Then use that instead of Open Office Writer... Does XFCE have enough features to be a usable desktop environment for you? Then use that instead of Gnome... And so on for each program, then you'll see a speed increase.[/QUOTE]

That is actually not true, the absolute best way to optimize is neither removing heavy programs nor optimizing using the compiler (although those a fine choices as well)

The causes of slowdowns:

1) Excessive work
2) Excessive IO
3) Bad design

You'd be amazed at how much excessive work we do, Dave Jones did meassurements on the Fedora start up which showed that we mindlessly stat every thing that isn't nailed down as well as doing other simply stupid unintented stuff [1].

Then we can look at IO, the harddrive is the slowest thing in your system, compared to a register the factor is about a 1million on your average desktop machine - this means we have to think about how we layout files and take into account that IO is extremely latent. We are talking milliseconds often seconds of pure waiting for the harddrive to give us data so we can get on with life. The overhead for syscall is low but when 99% of them are IO requests and we have to wait it it becomes alarmingly close to 100% of our waittime.

Bad design relates to poorly scaling algoritms, design which doesn't do the intended job - take the GTK fileselector, it was hidiously slow namely because it did a lot of unintended stuff (like loading the entire ~ dir, rendered it, then switched to the dir the program specified - wasteful but that was how it worked)

Once we get to a point there the biggest increase in performance is gained by playing smart compiler tricks we are doing REALLY well.

But we can't do this job properly without the right tools to collect data, and get plentiful amounts of good data to work with. Luckily people are working on this, RedHat is doing SystemTap and Frysk which are two interesting projects for this kind of work. Sun has DTrace and we already have things like strace to aid us in finding performance bugs.

So please can we get back to solving the problem buttom up instead of top down?

[1] [http://kernelslacker.livejournal.com/35270.html](http://kernelslacker.livejournal.com/35270.html)

---

### Post by ubuntu_demon on 2006-05-10
[QUOTE=Lovechild]That is actually not true, the absolute best way to optimize is neither removing heavy programs nor optimizing using the compiler (although those a fine choices as well)

The causes of slowdowns:

1) Excessive work
2) Excessive IO
3) Bad design

You'd be amazed at how much excessive work we do, Dave Jones did meassurements on the Fedora start up which showed that we mindlessly stat every thing that isn't nailed down as well as doing other simply stupid unintented stuff [1].

Then we can look at IO, the harddrive is the slowest thing in your system, compared to a register the factor is about a 1million on your average desktop machine - this means we have to think about how we layout files and take into account that IO is extremely latent. We are talking milliseconds often seconds of pure waiting for the harddrive to give us data so we can get on with life. The overhead for syscall is low but when 99% of them are IO requests and we have to wait it it becomes alarmingly close to 100% of our waittime.

Bad design relates to poorly scaling algoritms, design which doesn't do the intended job - take the GTK fileselector, it was hidiously slow namely because it did a lot of unintended stuff (like loading the entire ~ dir, rendered it, then switched to the dir the program specified - wasteful but that was how it worked)

Once we get to a point there the biggest increase in performance is gained by playing smart compiler tricks we are doing REALLY well.

But we can't do this job properly without the right tools to collect data, and get plentiful amounts of good data to work with. Luckily people are working on this, RedHat is doing SystemTap and Frysk which are two interesting projects for this kind of work. Sun has DTrace and we already have things like strace to aid us in finding performance bugs.

So please can we get back to solving the problem buttom up instead of top down?

[1] [http://kernelslacker.livejournal.com/35270.html](http://kernelslacker.livejournal.com/35270.html)[/QUOTE]
interesting read.

IMHO it's good to increase performance both top-down and bottom-up. There are people on the kernel and glibc if it becomes faster : good for us. Unnecessary I/O is indeed very important to reduce. Also not all services have to be started during boot .. for example I don't have LVM as most desktop users but it's get started for everybody. And there are lighter environments such as xubuntu or even lighter fluxbox and icewm for people who can't run gnome. (this doesn't mean gnome shouldn't become faster ofcourse)

If software becomes more complex there's more unnecessary I/O and and more memory leaks IMHO software developers should have a bug fix/performance fix release once in a while without adding new features. (this doesn't go for distro's because a distro only bundles software)

---

### Post by Lovechild on 2006-05-10
[QUOTE=ubuntu_demon]interesting read.

IMHO it's good to increase performance both top-down and bottom-up.[/QUOTE]

I'm not saying it inherently evil, but that assumes that the GCC optimizers aren't broken.

Let's fix the compiler before applying it's brokenness in software we have to support.

---

### Post by ubuntu_demon on 2006-05-10
[QUOTE=Lovechild]I'm not saying it inherently evil, but that assumes that the GCC optimizers aren't broken.

Let's fix the compiler before applying it's brokenness in software we have to support.[/QUOTE]
I'm sure there are smart people working on GCC. Are you suggesting the GCC optimizers are broken or do I misinterpret your statement ?

---

### Post by Lovechild on 2006-05-10
[QUOTE=ubuntu_demon]I'm sure there are smart people working on GCC. Are you suggesting the GCC optimizers are broken or do I misinterpret your statement ?[/QUOTE]

I'm not only suggesting, I'm saying it proudly - but yes smart people are working on it.

Optimizers are really hard to write, if you try reading some of the GCC sourcecode you'll understand why - expecting them to be perfect and not introduce bugs and performance regressions is naive beyond all meassure, e.g. recently a bug in 4.1.x caused a 100 fold performance regression in a few cases which was only caught after the official stable release. This generally happens because nobody has a good testsuite to run on GCC after each changeset, we simply don't know what general impact any given change has on performance and generated code correctness.

---

### Post by truthfatal on 2006-05-10
Back to the poll at hand...

I'll use "optimized" packages if I notice them, but I'm not going to go looking for them and wouldn't particularly care if they weren't there.

---

### Post by prizrak on 2006-05-10
[QUOTE=bigdaddyjohn]First, why such negative responses to a Poll? If you don't think it's a good idea, simply vote against it. He is just asking for data. Relax. 

Second, I'd love the prepackaged version. I'm new to Ubuntu and appreciate the packaged form. For example, I tried to use the K7 kernel. It loaded faster, displayed menu's faster, etc. Tremendously fast, you ask? I can't say as of yet. However, I like the others before, discovered that it no longer had the wireless settings available, "Out of the Box". Pitty.

Hold the "read the previous posts and search the forum" banters. I do just that, as I have time. Working full time, new baby, older children, wife, money, house, etc (also known as a life), all prohibit day long searches and experiments. I do enjoy the challenges however some items working without tinkering are very helpful. As others have posted, the wireless support is key. Not everyone who is trying Linux is interested in recompiling packages, kernels, etc. If you believe they are, you are sadly mistaken and have not listened to what the masses have been saying since the mid 1980's.

Getting the most performance out of my older laptop is key. The less tinkering the better, at least for me. I don't have the extra money to buy the latest and greatest processors nor do I plan on replacing what I have. One of the touted advantages of Linux has been the ability to utilize a mediocre system that would compete with a new Windows machine. I fall into that category. So for me at least, yes I would gladly utilize a specific, customized format.

Remember, the Ubuntu Help file states the following:
"Ubuntu is available in flavours for the i386
                        (386/486/Pentium(II/III/IV) and Athlon/Duron/Sempron
                        processors), AMD64 (Athlon64, Opteron, and new 64-bit
                        Intel processors), and PowerPC (iBook/Powerbook, G4 and
                        G5) architectures."

I for one didn't expect the problems with lack of working wireless simply by looking for my particular "Flavour".

bigdaddyjohn[/QUOTE]
You must have not installed all the necessary packages. I switched both my machines to optimized kernels w/o anything being broken. You have to install the linux-k7 package which will install all the things you need.

---

### Post by tageiru on 2006-05-10
[QUOTE=Lovechild]The causes of slowdowns:

1) Excessive work
2) Excessive IO
3) Bad design[/QUOTE]
Well, applications spend most of the execution time waiting for user input, so optimizing the user will yield the most significant performance increase.

---

### Post by Lovechild on 2006-05-10
[QUOTE=ubuntu_demon]
If software becomes more complex there's more unnecessary I/O and and more memory leaks IMHO software developers should have a bug fix/performance fix release once in a while without adding new features. (this doesn't go for distro's because a distro only bundles software)[/QUOTE]

automated performance and regression testing would tells us how bad this is, I doubt that forcing a bugfixing session on people will gather as good results. Look at GStreamer for an idea of how this would work.

---

### Post by ubuntu_demon on 2006-05-11
[QUOTE=Lovechild]automated performance and regression testing would tells us how bad this is, I doubt that forcing a bugfixing session on people will gather as good results. Look at GStreamer for an idea of how this would work.[/QUOTE]
I'm sure automated testing can save a lot of time. I didn't suggested "forcing a bugfixing session" a merely suggested more bugfixing releases without new features might be a good idea (for example to find all big memory leaks in firefox).

Can you elaborate or give me a link on the gstreamer/automated testing thing ?

---

### Post by 23meg on 2006-05-11
I'm against any such effort being official, as it will yield little performance benefit if at all, introduce new bugs and take extra maintenance and bugspotting effort and extra CPU cycles, storage, bandwidth, you name it. 

The success of any major distro depends on compromises and tradeoffs, and here the gains don't justify the losses; it's just not a feasible tradeoff. Unofficial projects can experiment with i686 or any other arch optimization as they like; they have all the tools and material they need. I doubt they'll be able to come up with any benchmarkable performance gain that can be taken seriously.

---

### Post by Lovechild on 2006-05-11
[QUOTE=ubuntu_demon]I'm sure automated testing can save a lot of time. I didn't suggested "forcing a bugfixing session" a merely suggested more bugfixing releases without new features might be a good idea (for example to find all big memory leaks in firefox).

Can you elaborate or give me a link on the gstreamer/automated testing thing ?[/QUOTE]

With each change to CVS, the system builds the Gstreamer code on multiple platforms and tells the developers in the #gstreamer channel how it faired - it even insults the person responsible for breaking the build. They also run Valgrind automatically on each build to detect memory leaks.

What does this amount to, when GCC 4.1 came out, GStreamer was the only multimedia framework to compile without alternation, which speaks of their code quality and testing.

Now what GStreamer does is just a tiny bit of what we could do but it shows clearly how we can benefit from such methods of testing.

We'd need a system to do this in a flexible manner, we'd also need to be able to get performance and ressource usage metrics in an readable format. I know Mono offers a good unit testing framework which is easy to adapt to your project, maybe if Mono gets more widely used we'd see that as a means to add more automated testing.

---

### Post by LordHunter317 on 2006-05-11
> **hermesrules]Frankly, I don't quite understand what has triggered such a response on your side.[/quote]Because the poll should not be asked, really.

Packages that need to be compiled with specific GCC optimizations are already done so.  Most packages that need architecture-specific optimizations (e.g., audio/video codecs, X.org drivers, etc.) don't need to be compiled with any GCC flags.  Why?  Because they do the detection at runtime for the code that needs to run the fastest.

Everything that needs to have special compiler flags already gets it.  It's a tiny, stupidly insignificant minority of software.
 
> I don't dispute the last line of your post, but who are you and who am I to write you a whitepaper, exactly?You, even if you're not petitioning the develoeprs to do something, are try to see if there is support for a particular development choice.  But you haven't done the basic ground research (including benchmarking) to show if the choice is wortwhile.  This isn't a subjective thing.  It's very, very, very objective.

> I also do understand that it would require a significant amount of work. But hey, there are 21 (as of now) other people, who must be just as confused about optimization as I am, since that's what the poll shows.If you were confused, then why did you start *a poll*?  Why not just ask the question, probably in the programming forums: "Is this worthwhile?"

Your actions and your claimed intentions aren't really aligned here said:**
> wonder are there users running Ubuntu on i486 hardware ? How much memory is needed for a server install ? If it's 32 mb then the majority of the 486 machines won't even able be able to install ubuntu.

IMHO compiling with march=i586 and mcpu=pentium4 will only be a very small performance difference. But if it's true that there are almost no 486 computers running Ubuntu then it might be worth the effort (maybe).No, that will make performance worse for a sizableclass.  Any -mcpu selection beyond i686 is dumb for what little difference they make at all (not much).  And that's not a wise choice for K6 processors. 

> I'm sure there are smart people working on GCC. Are you suggesting the GCC optimizers are broken or do I misinterpret your statement ?The GCC arch and sub-arch specific optimizations are almost always broken in some way or another.

> I didn't suggested "forcing a bugfixing session" a merely suggested more bugfixing releases without new features might be a good idea (for example to find all big memory leaks in firefox).Which is forcing a bugfixing session.  It doesn't matter how you say it, that's what you're suggesting.

---

### Post by hermesrules on 2006-05-11
I really feel tempted to use your unmistakable style of replying to users less development-savvy than you on these forums, but I do not think this would help me make my point. Unlike you, and perhaps one other indididual on this forum, I did not insult anyone, I did not judge anyone, and even when such insults and judgments were thrown at me because of my poll idea, I tried to keep the good tone. I therefore refuse to behave on these forums the way other people act in court during a cross-examination.

I would only like to make a few short points though, and apologize for having to use such style. I do not intend to continue this one-on-one quasi-dialogue.

When you say:
[QUOTE=LordHunter317]Because the poll should not be asked, really.[/QUOTE]

you are being overly subjective. The poll is absolutely valid, it was not offending, nor did it contradict any guidelines. When I say I do not understand what triggered his response, I only meant his nearly aggressive tone. Several people pointed out on this forum that this should not be done, and I agree.
 
[QUOTE=LordHunter317]You, even if you're not petitioning the develoeprs to do something, are try to see if there is support for a particular development choice.  But you haven't done the basic ground research (including benchmarking) to show if the choice is wortwhile.  This isn't a subjective thing.  It's very, very, very objective.[/QUOTE]

I am NOT trying to see if there is support for a particular development choice. If I was trying to do that, I would have contacted the developers first, and I would have suggested a much more robust methodology to investigate whether such support exists among Ubuntu users at large. And no, I haven't done the basic ground research on that issue because **I am not a developer**, I have no way of forwarding the analysis I would have done had I conducted such research to the proper people, and lastly - because I do this in my spare time, which is not that much. As a user I do my basic (sometimes extensive) research on issues such as how to make my broadcom wireless to work. If you check my history, you will see I never asked, yet I was able to make it work thanks to the support available on this forum.

[QUOTE=LordHunter317]If you were confused, then why did you start *a poll*?  Why not just ask the question, probably in the programming forums: "Is this worthwhile?"[/QUOTE]

You can't really be serious with this first question... I did not start a poll because I was confused, I started a poll because I was CURIOUS. I was confused by the negativity in other people's responses, yet the poll is opened by 100 people/day, and despite the heated discussions that some people tried to start here, there are still people - every day - who keep voting for the optimized package repositories. Now this is where I am confused, because previous posts, even those, which tend to be a bit aggressive, have CLEARLY explained there is not much gain in doing so.

As with the second question, I agree.

[QUOTE=LordHunter317]Your actions and your claimed intentions aren't really aligned here; they're confused.[/QUOTE]

Man... What an interesting way of saying it... I suggest you read through all of my posts in this thread, and pay particular attention to the one where I say that I get it...

Lastly, I would like to say this to everyone, not to anyone in particular, as it is still my firm belief. If we (as in everyone, who uses Linux and (K)Ubuntu in particular) want Linux to be a great operating system, we need to make better effort to understand all of its users.

---

### Post by LordHunter317 on 2006-05-11
> **hermesrules] Unlike you, and perhaps one other indididual on this forum, I did not insult anyone,[/quote]I've done nothing of the sort.

>  I did not judge anyone,I haven't judged you either.  I've simply said your poll is without merit and your statements are contradictory.  That doesn't necessarily mean anything about you as a person.

> you are being overly subjective. The poll is absolutely valid,No, it isn't. If you did some research you'd see that the options make no difference.  It's valid in the sense you're free to take a poll, but it's not valid in any technical sense whatsoever.  Seeing as we're dealing with computers, the latter sense is infinitely more important that the former.

>  it was not offending, nor did it contradict any guidelines.I never said it was.  On that basis, you're free to poll about it.  From a technical basis, it's senseless because there is no clear technical advantage, which was my point.


> When I say I do not understand what triggered his response, I only meant his nearly aggressive tone.Because I suspect like myself, Lovechild is rather sick of dealing with these sorts of things.  They come up all the time and it gets rather tiring to here the same invalid arguments being raised time and time again.  I don't actually know, but that's my guess.


> I am NOT trying to see if there is support for a particular development choice.Then **why a poll?**  Your choice of thread type is contradictory with that claim.  I'm sorry.  Just because you're not petitioning for something doesn't mean you're not trying to find out if there is support.

I'm sorry, your actions don't match your statements.  What was your motive then?

> And no, I haven't done the basic ground research on that issue because **I am not a developer**,Nor do you need to be.  Basic software testing skills are all that are required, if that.

> You can't really be serious with this first question... I did not start a poll because I was confused, I started a poll because I was CURIOUS.I'm confused.  You knew before you started the poll that the choices don't matter, they all yield the same results, yet you polled anyway?  Why?  I can't see anyone being curious in something they know doesn't matter at all, unless they're doing research on the placebo effect.

> I was confused by the negativity in other people's responses,What responses?  Here?  That can't explain your motive said:**
> Man... What an interesting way of saying it... I suggest you read through all of my posts in this thread, and pay particular attention to the one where I say that I get it...No, no, you don't understand.

You can't refer to any posts made besides your OP.  **Why did you start this thread?**  That's what I want to know.  'Curious' isn't a sufficent answer.  If say, 'So and so replied saying this' that's a Post-hoc fallacy and therefore insufficent.

That's all I want to know.  Because I can't fathom any other reason then trying to figure out what kind of support there is for such a thing.  If you wanted to know whether optimizations really worked, I don't see why you started *a poll*.

---

### Post by LordHunter317 on 2006-05-11
[QUOTE=Lovechild]With each change to CVS, the system builds the Gstreamer code on multiple platforms and tells the developers in the #gstreamer channel how it faired - it even insults the person responsible for breaking the build. They also run Valgrind automatically on each build to detect memory leaks.[/quote]FWIW, this process is referred to as Continuous Integration (CI).  There are several OSS and commerical CI systems available.  The most well known (and one of the worse presently) is Tinderbox, which is used pretty much solely by the mozilla group.

CI is farily distinct from automated unit/regression testing, though running those tests can be part of a CI system.  But a CI system is focused mainly on catching compile-time errors and ensuring you have a tree that always builds.

---

### Post by prizrak on 2006-05-11
*Waits for LinuxSwede to jump in*

---

### Post by helpme on 2006-05-11
Jesue H. Christ, there really is no need at all to attack the OP like this.
Contrary to what some people seem to believe he does not have to justify himself because he simply decided to start a poll about something he was curious about.

To add insult to injury he even readily acknowledged that he didn't know to much about the subject, probably was wrong in thinking that what he proposed would make a difference and even thanked the people who posted information.

For crying out loud, what more can you ask?

Seriously, some people still seem to have some serious amount of growing up to do. :evil:

---

### Post by LordHunter317 on 2006-05-11
[QUOTE=helpme]Contrary to what some people seem to believe he does not have to justify himself because he simply decided to start a poll about something he was curious about.[/quote]He asked why he got the response he did.  And the answer is because his OP smells like every other 'OMG OPTIMALIZE!!!111ooneone' bit that's ever been posted.

As such, if that wasn't his intent, I'd honestly like to know what it is so we can have the dialogue he really wants.  But it's difficult when it's written exactly like a cookie-cutter 'Lets make XXXX into Gentoo or Arch' poll, of which I've seen probably a million.

> For crying out loud, what more can you ask?His intent, whch is very relevant here.

---

### Post by helpme on 2006-05-11
[QUOTE=LordHunter317]
His intent, whch is very relevant here.[/QUOTE]
No, that's where you are totally wrong.
The intent of someone posting some poll on the off topic forum of some linux forum is so incredibly irrelevant it defies description.

And as you obviously didn't recognize it, it's not only irrelevant, but acting as if you are entitled to know, or as if everyone posting some stupid little poll on some stupid little forum has to have a well thougth out intend he better is able to explain or else is really, really misguided. And that's putting it mildly.

---

### Post by hermesrules on 2006-05-11
[QUOTE=LordHunter317]
Because I suspect like myself, Lovechild is rather sick of dealing with these sorts of things.  They come up all the time and it gets rather tiring to here the same invalid arguments being raised time and time again.  I don't actually know, but that's my guess.

You can't refer to any posts made besides your OP.  **Why did you start this thread?**  That's what I want to know.  'Curious' isn't a sufficent answer.  If say, 'So and so replied saying this' that's a Post-hoc fallacy and therefore insufficent.

That's all I want to know.  Because I can't fathom any other reason then trying to figure out what kind of support there is for such a thing.  If you wanted to know whether optimizations really worked, I don't see why you started *a poll*.[/QUOTE]

LordHunter317 - This can go on forever. You obviously don't follow my reasoning, and frankly, reading through your last post entertains me. I am writing this to say there is ONE thing in it that I do agree with though, namely the first paragraph in the above quote. If you are really so curious about WHY I started the poll, read my first message. Also, read more carefully my statements in my previous post. I did indeed refer to my own posts only! If you don't understand my language, then I need to apologize as English is not my first language, and we are perhaps both at disadvantage. So, let's keep learning it, it generally facilitates communication better.

Yet, let me tell you this: whoever is sick of dealing with whatever it is you call 'this sort of things' is their own problem! If you are so sick of such a thread, don't open it, don't post pages of wisdom in it. A simple POLITE message with references to other threads discussing the issues would have sufficed. You have done more research than me, and I am sure you have those links.

You can probably start a sticky thread informing users about what NOT to post, if it causes you and others such sickness. I am sorry for any inconvenience I may have caused you.

You should also know (if you haven't learned it already) that reading through the forums, regardless of the topic, is oftentimes an excellent way to learn about one's character. Others have already noticed a lot about you too. So let's stay focused and continue to help people coming here to learn. Otherwise, I am afraid, you are turning into a bad teacher...

Thank you.

---

### Post by LordHunter317 on 2006-05-11
[QUOTE=helpme]No, that's where you are totally wrong.
The intent of someone posting some poll on the off topic forum of some linux forum is so incredibly irrelevant it defies description.[/quote]How so?  If that were true, can I start a poll entitled, 'Do you think Bush should be impeached because he's stupid'?  It's clear if I did so my intent is to only troll, but by your standard, that's acceptable.  However, in order to lock it, you need to be able to assume or know my intent was only to troll.

So no, intent is perfectly relevant.  It's absolutely silly to pretend it's not.

**NB:** I'm not accusing the OP of actually trolling, or Bush of actually being stupid.  I'm simply pointing out that intent is relevant when someone writes something and suggesting it's not is fundamentally fallacious.  Communication ceases to function without purpose.

> And as you obviously didn't recognize it, it's not only irrelevant, but acting as if you are entitled to know,If you were paying attention, the OP asked why he was getting dogpiled.  I pointed out the obvious answer: 'This is a cookie-cutter post with a cookie-cutter answer that has been answered a billion times, and those that know the answer are sick of answering it. If his real reason for posting was to foster some other kind of discussion, knowing his intent not only gets past the dogpiling, it lets us focus on the real discussion the OP desired, and possibly prevent this sort of dogpiling in the future.

>  or as if everyone posting some stupid little poll on some stupid little forum has to have a well thougth out intendOne would presume one has some measure of intent before writing something for the public venue.

[quote=hermesrules]You obviously don't follow my reasoning,[/quote]**Because it's not consistent**.  You''ve said, 'It wasn't to find out popular support', but you started the thread *as a poll* and you're going on about how you think it's a good thing in the OP.  Even if you didn't intend to petition the developers ever, the OP certainly looks like someone trying to figure out how much popular support there is for this.

So I'll repeat my question.  I'm genuinely curious and I'm sure you had a good reason.  I just simply cannot tell what it is.

> If you are really so curious about WHY I started the poll, read my first message.Which implies what you're claiming you're not trying to do: figure out how much support there is for optimized packages in Ubuntu.  You've said since then that's not your intent.  Telling me to refer to the OP when you've since contradicted yourself doesn't help a soul.

> Yet, let me tell you this: whoever is sick of dealing with whatever it is you call 'this sort of things' is their own problem!No, it isn't.  Education dies if the teachers stop teaching.  

> If you are so sick of such a thread, don't open it, don't post pages of wisdom in it. This is unacceptable if you hold the view that teaching others the truth is the most important thing when it comes to these sorts of matters.  Saying, 'Just don't post' when someone is wrong on *objective* technical matters isn't acceptable.  That's akin to saying, "You're right if you say '2+2=5'".  

Remember, this isn't "What is your favorite movie" or "what is your favorite pizza" or even a far more subjective "What priority do give factors X, Y, and Z in determining a products quality." If it were, 'stay out' would be a good answer.

This is a objective, measurable, deterministic property we're examining.  That means there's only one correct answer.  Saying, 'Don't post the correct answer because you don't like having to repeat yourself' flies in the face of science.  

> A simple POLITE message with references to other threads discussing the issues would have sufficed. You have done more research than me, and I am sure you have those links.If I had links that were to the quality I though people would read and understand, I would.  Suffice to say, my experience has been that even if I posted those links, I'd just end up explaining them over and over again.  I can point to countless threads on countless similiar topics on countless forums where that was the case.

> You can probably start a sticky thread informing users about what NOT to post, if it causes you and others such sickness. If I were a mod, I would.  I'm not, so I can't.

> I am sorry for any inconvenience I may have caused you.It's not an inconvenience, but the accepted norm is you do some basic research before asking such a question.  Even the most cursory research (say a forum search and a google search) would have shown:[list][*]This is a hotly contested issue[*]Everytime some claims advantages, they're asked for benchmarks they usually fail to provide[*]What benchmarks are out there don't show statistically meanigful gains.[/list]And look, you were told those things by Lovechild right out of the gate.

You then asked why the negative reaction, and that's the main reason why in my mind (I could be wrong, I'm not Lovechild).  My teachers expect me to come to class and not ask the same questions over and over again.  It's not unreasonable to make the same expectation here.  And yes, one could say Lovechild's response was impolite, but I certainly don't find it outside of human nature.  

And like I said, if you real reason was to find out why there wasn't a difference, if you had just started a discussion (not a poll) asking, 'Why isn't there a difference', then all this negativity could have been avoided to begin with.

---

### Post by Lovechild on 2006-05-11
"Lovechild might be an arsehole of some dimensions, but at least he's fair.. and right."

This ad was brought to you by "Nutcases for Lovechild"

Lovechild fully endorses extremely liberal use of the SEARCH functionality on these fine forums.

---

### Post by KiwiNZ on 2006-05-11
Lovechild and lordhunter317

If you dont like a thread ,poll, question or post .And you are sick of answering same then dont bother to respond or read them.

Do not flame ,attack or insult the originator.

Thankyou

---

### Post by Lovechild on 2006-05-11
[QUOTE=KiwiNZ]Lovechild and lordhunter317

If you dont like a thread ,poll, question or post .And you are sick of answering same then dont bother to respond or read them.

Do not flame ,attack or insult the originator.

Thankyou[/QUOTE]

When it comes to this kind of question it does demand an answer, ricerhood is harmful.

Now we were having a good technical debate now, so could you back off cluttering the technical stuff with politeness debates.

---

### Post by KiwiNZ on 2006-05-11
[quote=Lovechild]
Now we were having a good technical debate now, so could you back off cluttering the technical stuff with politeness debates.[/quote]

I remind you of the forum rules and code of conduct and ask that you abide by them.

Thankyou

---

### Post by Compucore on 2006-05-11
The only time that I think something should be optimizedx to the best of the application whether its Ubuntu or any apps that will benefit from it. Would be if you are using two or more actual processors. And I am not talking about the single chip with dual core in them. I am refering to the acrual two or more physical chips themselve. *Like on server with 2 or more CPU's on them.* Even if they two physical processor and those were dual core in them. Then I could understand doing it. But to optimize something just for the sake of optimization where it has been working fine on a wider variety of hardware. As the saying goes if it isn't broke don't fix it.

Compucore

---

### Post by prizrak on 2006-05-11
[QUOTE=Compucore]The only time that I think something should be optimizedx to the best of the application whether its Ubuntu or any apps that will benefit from it. Would be if you are using two or more actual processors. And I am not talking about the single chip with dual core in them. I am refering to the acrual two or more physical chips themselve. *Like on server with 2 or more CPU's on them.* Even if they two physical processor and those were dual core in them. Then I could understand doing it. But to optimize something just for the sake of optimization where it has been working fine on a wider variety of hardware. As the saying goes if it isn't broke don't fix it.

Compucore[/QUOTE]
Even then there is little point. There are SMP kernels that are optimized for multi CPU systems but I am not aware of any benchmarks that show it to be noticeably faster than a regular kernel. Simple truth of the matter is that very few applications need special instruction sets to run faster and those that do (A/V stuff, graphics, etc), as pointed out by LordHunter, tend to detect that at run time. The only customizations that I can see making a difference would be 64bit kernels for the x86-64 family as opposed to the 32bit. Even then I'm not exactly sure.

---

### Post by Lovechild on 2006-05-11
[QUOTE=prizrak]Even then there is little point. There are SMP kernels that are optimized for multi CPU systems but I am not aware of any benchmarks that show it to be noticeably faster than a regular kernel. Simple truth of the matter is that very few applications need special instruction sets to run faster and those that do (A/V stuff, graphics, etc), as pointed out by LordHunter, tend to detect that at run time. The only customizations that I can see making a difference would be 64bit kernels for the x86-64 family as opposed to the 32bit. Even then I'm not exactly sure.[/QUOTE]

For those application you could employ implementing inner loops using liboil, that would in runtime optimize the loop to take advantage of SSE, MMX, etc.

---

### Post by prizrak on 2006-05-11
[QUOTE=Lovechild]For those application you could employ implementing inner loops using liboil, that would in runtime optimize the loop to take advantage of SSE, MMX, etc.[/QUOTE]
So basically we go back to compile time optimization being utterly useless with only exception being 32 vs 64bit and even then it's not really optimization.

---

### Post by jdong on 2006-05-11
First off, let's try harder to be more respectful to each other. Please avoid stereotyping or direct insults that attack the person making a suggestion instead of addressing the suggestion itself.

With that said, I've played around quite a bit with optimization, and I've found:

* For the most part, blind application of CFLAGS (i.e. -O2 -funroll-loops -pipe -march=athlon64 -fomit-frame-pointer) does not yield faster code by any means. This goes for most of the desktop stuff (i.e. in the default install), meaning that just by "optimizing" everything for your processor you will not see significant or noticeable boosts in speed
* When comparing Ubuntu vs, say, Gentoo, the speed difference is typically due to differing source code than compile-time optimizations. There is usually a good reason why Ubuntu has some patch, but it costs in performance.
* Even optimized kernels yield very little difference in performance (i.e. i386 vs k7), so I'm not really convinced that compiler flags do much at all.

* Certain media related apps and other computationally intensive programs do benefit from -O2 and -fomit-frame-pointer, along with (_sometimes_, more on Intels than on AMD's) SSE/SSE2 enabling. Optimization can be, and for the most part is already, enabled on these select packages.

* Ubuntu packages are already -O2 and some are -fomit-frame-pointer, -mcpu=pentium4 and -march=i486. Stepping from this up to your specific processor usually means little difference (I think it opens up 2 specific optimizations) in performance, and my tinkering with it does reflect that.

* **Blind optimizing can lead to broken binaries**... I've come across several source packages that when applying my typical CFLAGS (as mentioned in first bullet) will yield binaries that behave erratically (SEGFAULTs, hangs, general instability), but taking off these CFLAGS reverts the programs to default behavior. Thus, just blindly bumping up CFLAGS on the entire package collection will yield lots of new bugs just from bad optimizing.

If you really want to play with optimizing your packages, see the "apt-build" package, which allows you to recompile your entire system (or any subset) from Ubuntu source packages with your own compiler options...

---

### Post by Lovechild on 2006-05-12
[QUOTE=prizrak]So basically we go back to compile time optimization being utterly useless with only exception being 32 vs 64bit and even then it's not really optimization.[/QUOTE]

In theory I guess you could do something like 64 bit optimization like this as well. If I understand correctly how this works it's basically a set of precoded loops and a some logic to decide your CPU set support. You could just add a set of precoded loops geared that the various 64bit implementations (Hell Intel and AMD are thankful to provide ASM examples for the best possible implementation for they new fangled archs) and extend the logic to detect your 64 bit arch.

I think we gain a lot with this approach, say the user gets a new CPU, the binaries will run at close to the maximum of the potential performance without a recompile or any sort of work - this means less code to support because we don't have to have seperate repos for every archtecture out there.

This isn't Linux specific as such, we could have optimized innerloops on every architecture and OS if implemented correctly.

Seperating out the optimized paths means that we get well tested and well understood code, hopefully leading to code with better performance and lower bugcount.

The con would be that this only works it's wonders on intense innerloops, overusing it could lead to overhead in the logic and thus lower performance.

For those who like numbers, there's an implementation of libtheora that uses liboil and it's roughly twice as fast as the already optimized libtheora code.  Though not as fast as handcrafted ASM to enable using MMX it dramatically increases performance[1].

[1] [http://lists.xiph.org/pipermail/theora-dev/2005-July/002820.html](http://lists.xiph.org/pipermail/theora-dev/2005-July/002820.html)

---

### Post by fuscia on 2006-05-12
[QUOTE=Lovechild]Ample evidence is the foundation of all good decisionmaking.[/QUOTE]

hm! i'll have to try that.

---

### Post by hermesrules on 2006-05-12
To everyone:
I really enjoyed following the technical discussion in this thread about optimizations and its (lack of) benefits, and would like to thank everyone who took the time to explain it. I now do understand that there is no value in optimizing the way I initially thought, and I certainly appreciate everyone's contribution.

To LordHunter:
You are right that if teaching stops, education is quick to die, perhaps. Learning, however, which I believe to be firmly embedded in human nature, will never stop. Then here comes the responsibility of the teacher, and as we all know, there are good, and there are bad teachers.

If you have noticed, LoveChild's initial posts in this threat might have been angry, but he made his point, and then continued the discussion of optimization with some really interesting and informing posts (thank you, LoveChild, I really respect that), and with sense of humor too. Unlike you, he focused on the issue in question, and did not attack me personally, questioning my reasoning capacity, my intentions, or anything.

Remember that being smart (which I have no doubt you are) is not enough if you do not act smart too. You may know everything about optimization, but, to tell you the truth, you failed to contribute this knowledge, which would have helped me, and many others, to avoid posting threads like this one.

As with whether or not you can start a poll about who needs to be impeached, you certainly can, but it would not be smart to post here. So, to say the least such an analogy, is highly irrelevant. The reason why I encouraged you not to 'post pages of wisdom' was only to point out that despite your disapproval of this thread, you went on posting irrelevant and highly-charged comments, which had nothing to do with optimization. If you try to put yourself in my shoes, you will probably see why this becomes offending aftfer the first post. On the other hand, thanks to your posts, this poll has been on the fist page of the Ubuntu Cafe for a whole week. And as you can see, more and more readers continue voting on the poll, even though there is now shared agreement that optimization is useless. Tell me, and tell the others in this thread, how was it that you were a good teacher in this case???

Now, please, contribute to this forum (and not just to this thread) by sharing your knowledge about Linux, and stop questioning my intentions.

---

### Post by GarethMB on 2006-05-12
i use the 686 kernel because otherwise hibernate and stuff dont work properly.

---

### Post by jdong on 2006-05-12
BTW, I'm not sure if everyone understood what LordHunter meant about i586 optimizations, but i586 code will run slower on all non-i586's (i.e. P2, P3, P4, P-M, Athlon K7, K8, and so on) than 486 or even 386 code. Another example that just applying blind optimization can actually be detrimental :)

---

### Post by Lovechild on 2006-05-12
[QUOTE=jdong]BTW, I'm not sure if everyone understood what LordHunter meant about i586 optimizations, but i586 code will run slower on all non-i586's (i.e. P2, P3, P4, P-M, Athlon K7, K8, and so on) than 486 or even 386 code. Another example that just applying blind optimization can actually be detrimental :)[/QUOTE]

You know evidence would be nice...

---

### Post by RAOF on 2006-05-26
[QUOTE=Lovechild]In theory I guess you could do something like 64 bit optimization like this as well. If I understand correctly how this works it's basically a set of precoded loops and a some logic to decide your CPU set support. You could just add a set of precoded loops geared that the various 64bit implementations (Hell Intel and AMD are thankful to provide ASM examples for the best possible implementation for they new fangled archs) and extend the logic to detect your 64 bit arch....[/QUOTE]
That's a really intriguing idea.  You'd want to be careful that the mode-switch time (I'm really not sure how significant this is) between 32 & 64bit mode doesn't swamp the perfomance benefit, but it would be a good way to get some of the [quite substantial]("http://www.anandtech.com/linux/showdoc.aspx?i=2213&p=1") performance gains from the x86_64 code into an otherwise 32bit program.

---

