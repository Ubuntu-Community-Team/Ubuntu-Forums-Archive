---
title: "If linux is open source why so hard to create a linux version"
date: 2011-10-30
forum: The Cafe
---

### Post by polardude1983 on 2011-10-30
One thing I don't understand is if Linux is so open source. Why is it so difficult for companies to create a version of their app for linux?

---

### Post by dpny on 2011-10-30
One reason is because developers can't count on the same software being in every distro. The real reason isn't about difficulty, though. It's about not being able to recoup their investment.

---

### Post by Thewhistlingwind on 2011-10-31
1. Support (Ongoing cost of)

2.  Incentive. Not enough market share (money)

3. Most programs that can't be ported are written with Microsoft tools that require the windows .ddl files to run. Linux does not have these files. 

4. Obscurity, it doesn't cross most Project Managers minds.

There are other reasons. Including packaging and release cycles, but I won't elaborate on those.

If you have a half an hour, this will help your understanding:

[http://www.youtube.com/watch?v=GT5fUcMUfYg](http://www.youtube.com/watch?v=GT5fUcMUfYg)

---

### Post by Legendary_Bibo on 2011-10-31
It doesn't have a stable API. You'd have at least 3 to 4 major distros each with about 3 current versions for an OS that takes around ~1% of the desktop marketshare.

It'd be a lot of work.

However, I've been messing around with Mono these past couple of weeks, and it seems to address those issues, by keeping most of your application as a self contained executable.

---

### Post by wolfen69 on 2011-10-31
It's cold in Connecticut. I never remember it snowing before Halloween. But it did, go figure.

---

### Post by Thewhistlingwind on 2011-10-31
> **wolfen69 said:**
> It's cold in Connecticut. I never remember it snowing before Halloween. But it did, go figure.

Whats that got to do with this thread?

Also, I WISH it was snowing right now!

---

### Post by gsmanners on 2011-10-31
> **polardude1983 said:**
> One thing I don't understand is if Linux is so open source. Why is it so difficult for companies to create a version of their app for linux?

I'm not seeing how the one logically follows the other. Hardware drivers, yes. Generic software? I don't think so.

You ever try to develop a hardware driver for Windows, by the way? What a nightmare. It's a wonder they can get them to work at all.

---

### Post by ssam on 2011-10-31
the main blocker is that if you write a piece of software for windows, it will not 'just work' on linux. programmers use libraries and APIs to save them writing everything from scratch. If you program uses windows specific libraries then you need to replace those bits of code to port it.

multi-distro work is i guess confusing but not too difficult. things like the linux standards base and freedesktop.org make most common distros look the same. if you write something good and opensource then the distros will do all the packaging for you. if you do something popular and closed source then the distros will do the packaging for you.

---

### Post by forrestcupp on 2011-10-31
You can create an app that will work on any distro. All you have to do is install it to /home and include all of the dependency libs.

The problem is that no one is trained on Linux programming and no one cares.

Also, open source doesn't equal easy.

---

### Post by fatality_uk on 2011-10-31
> **forrestcupp said:**
> You can create an app that will work on any distro. All you have to do is install it to /home and include all of the dependency libs.

The problem is that no one is trained on Linux programming and no one cares.

Also, open source doesn't equal easy.

What he said :D

---

### Post by 3rdalbum on 2011-10-31
> **polardude1983 said:**
> One thing I don't understand is if Linux is so open source. Why is it so difficult for companies to create a version of their app for linux?

Mostly, it's not that difficult. Modern distros tend to have very similar software, so it's not difficult to write something that will work on all sorts of different distributions.

Laziness is definitely one thing that makes it more difficult for a company to write for Linux. But to be fair, some companies just don't expect to see a return on their Linux investment, so they never make that attempt in the first place because they believe they'll lose money.

---

### Post by saphil on 2011-10-31
It seems as if most small apps for Linux were developed because a specific developer had an itch to scratch.   To that developer, it was not "hard" to make the app for Linux, it was "necessary."  
There are a few large projects that have been ported to Linux (or really, from any one OS to any other) but AFAIK they have strong corporate backing.

---

### Post by Merk42 on 2011-10-31
"if linux is open source why so hard to create a linux version"
That's like saying:
"If I have a dictionary, why so hard to write a novel"

---

### Post by forrestcupp on 2011-10-31
> **Merk42 said:**
> "if linux is open source why so hard to create a linux version"
That's like saying:
"If I have a dictionary, why so hard to write a novel"

Lol. Exactly!

---

### Post by 3Miro on 2011-10-31
The arguments that the Linux API is "unstable" is nonsense. There are plenty of commercial applications developed and distributed for Linux that work on all major distros regardless of Kernel versions, Xorg versions, DE versions and so on.

The problem is that the company needs to hire people with Linux training. Then a good chuck of a windows program would be useless under Linux so they have to do a lot of work from scratch. Then there is the small market-share and so on ...

---

### Post by fuduntu on 2011-10-31
> **polardude1983 said:**
> One thing I don't understand is if Linux is so open source. Why is it so difficult for companies to create a version of their app for linux?

It's very difficult because the [kernel ABI is unstable](http://www.kroah.com/log/linux/stable_api_nonsense.html) by nature making it difficult to build static hooks for proprietary software.

In addition, library versions change from distribution to distribution making dynamically linked binary distribution near impossible.

There are methods to deliver statically linked blobs to multiple distributions, but it's kludgy at best.

Linux distributions by design work best with open source software.

---

### Post by jwbrase on 2011-10-31
> **fuduntu said:**
> It's very difficult because the [kernel ABI is unstable](http://www.kroah.com/log/linux/stable_api_nonsense.html) by nature making it difficult to build static hooks for proprietary software.

In addition, library versions change from distribution to distribution making dynamically linked binary distribution near impossible.

There are methods to deliver statically linked blobs to multiple distributions, but it's kludgy at best.

Linux distributions by design work best with open source software.

From your link:

> Please realize that this article describes the _in kernel_ interfaces, not the kernel to userspace interfaces. The kernel to userspace interface is the one that application programs use, the syscall interface. That interface is _very_ stable over time, and will not break. I have old programs that were built on a pre 0.9something kernel that still works just fine on the latest 2.6 kernel release. This interface is the one that users and application programmers can count on being stable.

We're discussing application programming here, not driver programming.

---

### Post by Devi1903 on 2011-10-31
Market Share is what it is all about! Why would Adobe bother putting all the money and time into making a linux version of Dreamweaver which will increase their market by nothing measurable. The perception is still very much that Linux is for geeks and we geeks are quite happy to use basic applications that still require us to do a lot in code.

My feeling is that this is a very short term view, but who can blame them. Linux is clearly on its way up in terms of Desktop usage, especially when you look at what has happened with the Linux Desktop in the last 5 years.

---

### Post by scitron on 2011-10-31
> **fuduntu said:**
> 
Linux distributions by design work best with open source software.

True,  there's little motivation for companies.

Often besides the technical issues they also have to consider involved legal questions that don't have clear answers.

Also Linux culture is unfriendly toward closed source apps.

---

### Post by juancarlospaco on 2011-10-31
Sometimes they simply cant do that, despite if they want, ...or not,
some time ago i contacted a company that sells HW with Linux and Mac OsX drivers, 
it was hard, but i get passed on the phone to a Manager, 
he explained to me that they dont even have the sources of their Drivers, for real,
they build the HW, and buy canned Binary (and Support) to an Asian Software Development company.

---

### Post by fuduntu on 2011-10-31
> **jwbrase said:**
> From your link:



We're discussing application programming here, not driver programming.

Really though, you are talking about both.

---

### Post by donkyhotay on 2011-10-31
> **Devi1903 said:**
> Market Share is what it is all about! Why would Adobe bother putting all the money and time into making a linux version of Dreamweaver which will increase their market by nothing measurable. The perception is still very much that Linux is for geeks and we geeks are quite happy to use basic applications that still require us to do a lot in code.

My feeling is that this is a very short term view, but who can blame them. Linux is clearly on its way up in terms of Desktop usage, especially when you look at what has happened with the Linux Desktop in the last 5 years.

Personally I really don't think the big companies avoid linux because of market share, thats just an excuse. I think it's because if they did then random people would be more likely to use linux. When a person uses linux long enough you eventually get used to the power of FOSS and being able to easily edit/modify programs, either yourself directly (if you're a coder) or patches/edits from other people online. Eventually the people using those programs would start demanding more openness from their software (even if not fully FOSS) and they don't want to do that. By not porting to linux they encourage people to stick with apple or windows which helps keep them blissfully ignorant of other ways of using software.

---

### Post by Thewhistlingwind on 2011-10-31
> **donkyhotay said:**
> Personally I really don't think the big companies avoid linux because of market share, thats just an excuse. 

**No, really, thats the reason.**

I think it's because if they did then random people would be more likely to use linux.

**Not until OEM's ship it.**

 When a person uses linux long enough you eventually get used to the power of FOSS and being able to easily edit/modify programs, either yourself directly (if you're a coder) or patches/edits from other people online.

**Most people have no interest in doing this.**

 Eventually the people using those programs would start demanding more openness from their software (even if not fully FOSS) and they don't want to do that.

**No, they don't.**

 By not porting to linux they encourage people to stick with apple or windows which helps keep them blissfully ignorant of other ways of using software.

**I WISH companies thought through their decisions that thoroughly. The reality is that Linux is still seen as 1%.**



My responses in bold.

---

### Post by BrokenKingpin on 2011-11-01
It isn't hard, there around over 10 thousand apps in the repos. For commercial software it just might not be worth the extra dev cost if the market isn't there.

---

### Post by dpny on 2011-11-01
> **Devi1903 said:**
> Linux is clearly on its way up in terms of Desktop usage, especially when you look at what has happened with the Linux Desktop in the last 5 years.

You mean the way it's held steady at about 1%?

---

### Post by WinterMadness on 2011-11-01
This is why I like Java.

---

### Post by Lucradia on 2011-11-01
You also need to convince them that DRM can be enforced the same way as it is on Windows.

> **dpny said:**
> You mean the way it's held steady at about 1%?

1. That's internet-connected devices only.

2. It doesn't count Android Unless you switch over to mobile market share.

3. It's 1.19% specifically right now./

---

### Post by dpny on 2011-11-01
> **Lucradia said:**
> 1. That's internet-connected devices only.

Find me a computer which isn't connected to the internet.

> 2. It doesn't count Android Unless you switch over to mobile market share.

The OP specifically said "desktop".

> 3. It's 1.19% specifically right now./

My point.

I'm actually not trying to start a market share fight. I just think people shouldn't throw easily disproved stats into arguments.

---

### Post by Lucradia on 2011-11-01
> **dpny said:**
> The OP specifically said "desktop".

Linux is not an OS. You MUST count Android in the market share of all linux kernel devices.

You also MUST count Windows phones into the Windows OS market share, unless it's a completely different kernel. The linux kernel is practically the same across all devices.

ChromeOS also counts toward linux too, but Google is finicky about that. Since it's a cloud-based OS, which, can easily be turned into one that isn't.

---

### Post by dpny on 2011-11-01
> **Lucradia said:**
> Linux is not an OS. You MUST count Android in the market share of all linux kernel devices.

For the sake of this thread, Linux is an operating system: no one creates an application for a kernel. The OP asked about the difficulty of creating Linux versions of software, using Linux as the common metonym for operating systems based on the Linux kernel.

And, while Android is based on Linux, no one is talking about the difficulty of making Android apps. There's thousands of 'em.

---

### Post by gsmanners on 2011-11-02
> **polardude1983 said:**
> Why is it so difficult for companies to create a version of their app for linux?

I don't suppose you have some particular companies in mind? I can't honestly think of any Windows-focused companies that do really high quality software, but maybe that's just my experience.

---

