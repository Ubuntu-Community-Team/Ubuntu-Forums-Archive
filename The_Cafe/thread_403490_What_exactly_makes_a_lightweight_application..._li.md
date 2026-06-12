---
title: "What exactly makes a lightweight application... lightweight"
date: 2007-04-07
forum: The Cafe
---

### Post by aysiu on 2007-04-07
I'm not a programmer. I don't understand how programs work. So if someone can explain this in plain English (layman's terms), that'd be great.

I have a slightly older laptop, and I use IceWM on it. I've found some of the lighter-weight applications (like Leafpad and XTerm) load up immediately (literally one second after I press the keyboard shortcuts for them) but normal-weight (not even that heavy) applications (like Gedit and Gnome-Terminal) take as long as 12 seconds to load up.

What exactly makes lightweight applications lighter and able to load up more quickly? Just curious.

---

### Post by vf514 on 2007-04-07
AFAIK:

[LIST]
[*]If you don't have a lot of memory, the program doesn't have as much room to store its data. Logically, the longer a program has wait for memory to be freed, the slower it will run.
[*]If you have a slow processor, the "instructions" of the program will take longer to process and carry out.
[/LIST]

So a program dealing with large amounts of data or a lot of instructions to carry out will run slower on a computer with smaller amounts of memory or processing capabilities.

---

### Post by 23meg on 2007-04-07
Any combination of the below often can, but not necessarily does in every case:

- Having less features (as your text editor examples illustrate)
- Being written in a language that suits the task
- Being written in a language that has a fast execution speed
- Being compiled optimally
- Code being optimized

---

### Post by EdThaSlayer on 2007-04-07
With lightweight the programmers probably mean:
1.It uses less libraries, so less memory is used (libraries are the "tools" that the programmer uses to make a program)
2.Uses less variables, and global variables are rarely used(global variables use far more memory and isn't that efficient)
3.Probably re-uses code, so overall there is less code(Object Oriented Programming can do this)

I only know some Python programming, so there could be more ways to make a program lightweight with other languages. :popcorn:

Also, depending on which language you use, the program will run faster. For example, the C language runs 1000x faster than Python or so I have heard.

---

### Post by rai4shu2 on 2007-04-07
It's usually the number of libraries and add-ons (plugins/extensions) that makes most programs bloat. A classic example is Office apps.

Programs that do everything internally with low-level coding are generally much lighter, but they are of course less modular and flexible.

---

### Post by RAV TUX on 2007-04-07
> **aysiu said:**
> I'm not a programmer. I don't understand how programs work. So if someone can explain this in plain English (layman's terms), that'd be great.

I have a slightly older laptop, and I use IceWM on it. I've found some of the lighter-weight applications (like Leafpad and XTerm) load up immediately (literally one second after I press the keyboard shortcuts for them) but normal-weight (not even that heavy) applications (like Gedit and Gnome-Terminal) take as long as 12 seconds to load up.

What exactly makes lightweight applications lighter and able to load up more quickly? Just curious.

Start by reading this book for a bit more understanding:

[LFS-BOOK-6.2.pdf]("http://www.linuxfromscratch.org/lfs/downloads/stable/LFS-BOOK-6.2.pdf")


[img]http://skins.hotbar.com/skins/mailskins/em/google_emoticons/emoti_356.gif[/img]

---

### Post by aysiu on 2007-04-07
Thanks for all the replies.

So I'm gathering that the lightweight applications load up more quickly because they use fewer libraries, and the time it takes a heavier application to load is the time it takes to load up all the extra libraries?

---

### Post by rai4shu2 on 2007-04-07
For load time, there's also the matter of sessions/profiles, and whether you have to load large amounts of data by default for a particular application. Some programs are good about loading only what they need for a particular view, and others simply dump everything in memory and count on you having tons of it (which typically takes longer to load, as well).

---

### Post by koenn on 2007-04-07
> So I'm gathering that the lightweight applications load up more quickly because they use fewer libraries, and the time it takes a heavier application to load is the time it takes to load up all the extra libraries?
that's only part of it. 
the bigger picture :
programs are run from memory but stored on disk. so when you start an apllication, it has to be read from the disk and stored in RAM before it starts executing.
Therefore :
- a large program will take longer to load (disk access is relatively slow)
- a program the uses lots of libraries needs to load these libraries as well

apart from size (which affects load time and amount of memory occupied by the application), lightweight can also refer to memory usage during execution. If the memory used to eg. store values in variables, is not released again when it's not needed anymore, the memory usage builds up. ("memory leaks")

And then there's programming style. For every given problem, the programmer chooses a sollution. Some algoritms (sollutions to a given problem) are more efficient than others so they take less CPU cycles or les memory usage or less disk I/O and make the application run smoother and less "resource hungry"

That, and a combination of other factors (eg 23meg's list).

---

### Post by aysiu on 2007-04-07
Thanks. I think I'm beginning to get a better understanding of the issue.

---

### Post by diskotek on 2007-04-07
ti think less dependenicies are also makes it lightweight. as i am an xubuntu user, i don't istall programs written in Qt. because i normally use xfce & gnome compatible softwares .. so it dont install Qt libraries.

hehe is that right thought?

---

### Post by SishGupta on 2007-04-07
I am sure you have heard about the OLPC (one laptop per child)

In order to be able to provide laptops for cheap, they must be minimal machines, which require very light software.

Read this page to see how they plan to make the software as light as possible:
[http://wiki.laptop.org/go/Development_issues](http://wiki.laptop.org/go/Development_issues)

---

### Post by Bloodfen Razormaw on 2007-04-07
> It's usually the number of libraries and add-ons (plugins/extensions) that makes most programs bloat. A classic example is Office apps.
 
 Programs that do everything internally with low-level coding are generally much lighter, but they are of course less modular and flexible.
This is the complete opposite of the truth.  Using existing libraries makes an application far, far lighter.  Reinventing the wheel bloats your code, and that extra code is useless to everyone else.  A shared library can be reused by multiple programs, not only saving disk space, but saving memory and improving performance as well.  If I have a spell checker library in memory, why should I still have to wait for some idiot's code to load its own?  Why should I have to page out spell check code from memory in order to page in different spell check code?

Office apps are "bloated" only because they *don't* use shared libraries.  They roll their own code instead of using existing Windows libraries, in order to create their own interfaces and functionality entirely separate from other applications.

---

### Post by reacocard on 2007-04-07
> **Bloodfen Razormaw said:**
> This is the complete opposite of the truth.  Using existing libraries makes an application far, far lighter.  Reinventing the wheel bloats your code, and that extra code is useless to everyone else.  A shared library can be reused by multiple programs, not only saving disk space, but saving memory and improving performance as well.  If I have a spell checker library in memory, why should I still have to wait for some idiot's code to load its own?  Why should I have to page out spell check code from memory in order to page in different spell check code?

Office apps are "bloated" only because they *don't* use shared libraries.  They roll their own code instead of using existing libraries, in order to create their own interfaces and functionality entirely separate from other applications.

You're only half correct. While reusing libraries is a great way to save on code specific to your program, the fact remains that whether the libraries are shared or internal, they still have to be loaded into RAM at runtime. That's what costs you speed. So if you use 10MB of internal libraries, then switch to 10MB of shared libraries, load time probably won't change, because you still have to read that 10MB into RAM. Now, when several applications need the same 10MB, that 10MB only has to be loaded once, because it's shared, but most apps rely on different libraries for most things, so that advantage is largely negated.  Usually, you only have one app that needs a spell checker, or one app that needs a cd-writer. It's mostly really common libraries like GTK that get the biggest advantage from this.

In conclusion, fewer *total* libraries used (internal or shared) means much more lightness, but using shared instead of internal has much less benefit in terms of lightness.

---

### Post by Lster on 2007-04-07
It's hard to say really...

I would define it as being especially fast in one or more areas like:

[LIST]
[*]Processing efficiency
[*]Memory efficiency
[*]Network efficiency
[*]Hard-disk efficiency
[*]And more :)
[/LIST]

That's just my definition though :)...

---

### Post by Bloodfen Razormaw on 2007-04-07
> You're only half correct. While reusing libraries is a great way to save on code specific to your program, the fact remains that whether the libraries are shared or internal, they still have to be loaded into RAM at runtime. That's what costs you speed. So if you use 10MB of internal libraries, then switch to 10MB of shared libraries, load time probably won't change, because you still have to read that 10MB into RAM
If I use a 10mb shared library, load time will be reduced if another application has already loaded it.  You don't need to load a library into memory twice unless you statically linked it or wrote your own code.  You also need to remember that Linux, like most operating systems today, uses demand paging.  If I am using a shared library, all applications that use it use the same memory pages.  If I use my own code, I have to page in new code to do the same things I already could do with code in memory.  If every application were to use their own Qt or GTK+, the system would slow to a crawl paging code out just so it can page the same code in.

> but most apps rely on different libraries for most things, so that advantage is largely negated
That is just an admission that I am correct.  If you don't use shared libraries, your application is less lightweight.  And actually, its not that rare for applications to use the same libraries.  If you use a KDE desktop, every KDE application shares an incredible amount of functionality from kdelibs, which ensures that the libraries that it, in turn, uses are shared.  This is why its so funny when people here call kdelibs bloat, when in fact it performs better in speed and memory use than using arbitrary libraries for each application.

---

### Post by reacocard on 2007-04-07
> **Bloodfen Razormaw said:**
> If I use a 10mb shared library, load time will be reduced if another application has already loaded it.  You don't need to load a library into memory twice unless you statically linked it or wrote your own code. 
Absolutely.

> You also need to remember that Linux, like most operating systems today, uses demand paging.  If I am using a shared library, all applications that use it use the same memory pages.  If I use my own code, I have to page in new code to do the same things I already could do with code in memory.  If every application were to use their own Qt or GTK+, the system would slow to a crawl paging code out just so it can page the same code in.
Again, absolutely true. Major shared libraries like GTK/QT get huge benefits from sharing.

> If you don't use shared libraries, your application is less lightweight.  And actually, its not that rare for applications to use the same libraries.  If you use a KDE desktop, every KDE application shares an incredible amount of functionality from kdelibs, which ensures that the libraries that it, in turn, uses are shared.  This is why its so funny when people here call kdelibs bloat, when in fact it performs better in speed and memory use than using arbitrary libraries for each application.
My point wasn't that big libraries like kdelibs don't get reused (they do, a lot), but that other libraries don't, because only one application needs the functionality that library provides. Also, if you're not running a big DE like GNOME or KDE where most apps share the same libraries, the increase in load time for an app that does use them can be immense. Try running Amarok under GNOME sometime. Thus my point stands: fewer total libraries is the lightest. However, if you must use a library, shared libraries are the way to go, because they increase lightness *when more than one app needs that library*.

---

### Post by Bloodfen Razormaw on 2007-04-07
> My point wasn't that big libraries like kdelibs don't get reused (they do, a lot), but that other libraries don't, because only one application needs the functionality that library provides.
When you have large libraries like that, the smaller libraries they use propagate through them.  For example, consider that GNOME historically lacked a spell checking library, so several came into use, whereas kdelibs had spell checking through a single library, and thus only one library got used.  Also its quite common to see shared libraries used outside of desktop environments.  Take a look in at all the libraries you have.  Scrolling through the list I have in aptitude on my KDE desktop machine, official KDE libraries actually are only a small part.

>  Try running Amarok under GNOME sometime. Thus my point stands: fewer total libraries is the lightest.
No, it doesn't.  If Amarok didn't use kdelibs, and instead implemented that functionality on its own, you would still have to load that code just the same.  The code is going to be loaded either way; you can either load it once for all apps that need it, or once per application that needs it.  In the worst case, when only one application uses a library, performance is still equivalent to, not worse than, rolling your own code.

---

### Post by saulgoode on 2007-04-07
> **Bloodfen Razormaw said:**
> No, it doesn't.  If Amarok didn't use kdelibs, and instead implemented that functionality on its own, you would still have to load that code just the same.  The code is going to be loaded either way; you can either load it once for all apps that need it, or once per application that needs it.  In the worst case, when only one application uses a library, performance is still equivalent to, not worse than, rolling your own code.

What you describe would be accurate if my program used **all** of the functionality of the shared library; however, if I only need just a few functions from the library than there is certainly a difference between loading my potentially redundant fraction versus loading the entire library.

The same thing applies to static linking of libraries: for example, if my program needs to use the WAV file loading functionality of LIBSNDFILE and I staticly link that library, **only** the loading function is included in my code; the other 300K of functions which might save WAVs or convert other formats is not included and does not have to be loaded at runtime (which it would if I dynamically linked the library). 

Granted, if there is a good chance that the shared library will already be loaded into memory then having a duplicate of it in my program will be a waste. Nonetheless, there is no hard and fast rule that shared libraries are always better and, in fact, staticly linking libraries can often help in producing "lightweight" applications.

---

### Post by Bloodfen Razormaw on 2007-04-07
> What you describe would be accurate if my program used all of the functionality of the shared library; however, if I only need just a few functions from the library than there is certainly a difference between loading my potentially redundant fraction versus loading the entire library.
Incorrect.  Linux uses demand paging.  It is a myth that the OS loads the entire contents of an executable into physical memory.  Every executable is divided into pages, which are 4096 bytes by default in Linux.  Each page is only loaded when necessary.  Unnecessary portions of the library are never loaded into memory.  Parts of the library that are not used will not be paged into memory.

---

### Post by reacocard on 2007-04-07
> **Bloodfen Razormaw said:**
> When you have large libraries like that, the smaller libraries they use propagate through them.  For example, consider that GNOME historically lacked a spell checking library, so several came into use, whereas kdelibs had spell checking through a single library, and thus only one library got used.  Also its quite common to see shared libraries used outside of desktop environments.  Take a look in at all the libraries you have.  Scrolling through the list I have in aptitude on my KDE desktop machine, official KDE libraries actually are only a small part.


No, it doesn't.  If Amarok didn't use kdelibs, and instead implemented that functionality on its own, you would still have to load that code just the same.  The code is going to be loaded either way; you can either load it once for all apps that need it, or once per application that needs it.  In the worst case, when only one application uses a library, performance is still equivalent to, not worse than, rolling your own code.

I think we're both right, just not seeing the other's point because we're not quite talking about the same thing. My point is that Amarok on GNOME has to load all those extra libraries, because it's not using that same ones as the rest of GNOME. However, in KDE, Amarok would be more lightweight than say, Rhythmbox, because those KDE libraries are all shared by many apps, and the GNOME libs would be the odd ones out. However, if you have an application that doesn't rely on major DE-specific libraries and services, it will act lighter *everywhere*, simply because it doesn't have to load those additional libraries, period. Of course, this lightness comes at a cost, usually functionality or integration. An app using the GNOME libraries has many functions available to it, but if it only uses 3% of that, it would be 'lighter' to simply use a smaller library, at the cost of integration with the rest of GNOME and making it harder to expand the functionality.

---

### Post by hardyn on 2007-04-07
in a protected memory eviroment, is there any sharing of libraries?  or does the library get loaded, or at least copied to a different segment?  if we are truly sharing memory resident libs, a fault in one program could cause a failure in all other programs using using that lib.

am i way off on this?

---

### Post by reacocard on 2007-04-07
> **Bloodfen Razormaw said:**
> Incorrect.  Linux uses demand paging.  It is a myth that the OS loads the entire contents of an executable into physical memory.  Every executable is divided into pages, which are 4096 bytes by default in Linux.  Each page is only loaded when necessary.  Unnecessary portions of the library are never loaded into memory.  Parts of the library that are not used will not be paged into memory.

Interesting. I hadn't heard that, but the there are still other factors. Some apps need DE-specific services. For example, if you start up Amarok or k3b under GNOME you'll see several additional daemons start up, for KDE services. These eat the same memory and CPU, regardless of how many apps are using them. Also, large libraries need lots of diskspace as well, which people with really small harddrives would like to avoid.

---

### Post by saulgoode on 2007-04-07
> **Bloodfen Razormaw said:**
> Incorrect.  Linux uses demand paging.  It is a myth that the OS loads the entire contents of an executable into physical memory.  Every executable is divided into pages, which are 4096 bytes by default in Linux.  Each page is only loaded when necessary.  Unnecessary portions of the library are never loaded into memory.  Parts of the library that are not used will not be paged into memory.

I stand corrected and thank you.

---

### Post by rai4shu2 on 2007-04-07
No matter how you spin it, the fact remains: bloated programs are the ones that use tons of libraries. In theory, you *could* be sharing all that code memory with other apps, but the reality is that this is never the case.

---

### Post by IYY on 2007-04-07
I think it's more about the type of libraries than the quantity. If you use GTK2, you're pretty much guaranteed to have a heavyweight app.

---

### Post by reacocard on 2007-04-07
> **IYY said:**
> I think it's more about the type of libraries than the quantity. If you use GTK2, you're pretty much guaranteed to have a heavyweight app.

Not really. As we've said, the big libraries, like GTK tend to be shared by many apps, so that library only needs to exist once for all the apps. So, while GTK itself is big, when that large library is spread across a few dozen applications, it's not that big anymore. Having GTK for one application is heavyweight, having it for almost all of your apps is light. OpenOffice uses it's own version of GTK (and other libraries), which is part of why it's so bloated. Most linux-native apps are built with system libraries which are shared by many apps, thus reducing the bloat.

---

### Post by Bloodfen Razormaw on 2007-04-07
> No matter how you spin it, the fact remains: bloated programs are the ones that use tons of libraries.
The fact that you couldn't find an example to back that up makes me think it is as obvious to you as it is to anyone that apps that roll their own code instead of using existing code are the heavy ones.  The biggest offenders you see are nothing but apps that try to do everything themselves: Firefox, OpenOffice.org, Microsoft Office, etc.

---

