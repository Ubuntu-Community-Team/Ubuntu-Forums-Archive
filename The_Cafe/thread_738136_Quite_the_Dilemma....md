---
title: "Quite the Dilemma..."
date: 2008-03-28
forum: The Cafe
---

### Post by klange on 2008-03-28
Coming up on April 15th is the Baldwin Wallace Association for Computing Machinery [Programming Contest](http://acmcontest.bw.edu/contest/). Each year the contest takes students in teams of three from various high schools in northern Ohio to compete by solving fairly simple problem sets. Unfortunately, they require you to program in a strict set of four languages: VC++, VC#, J# and VB - and also require you to use the Microsoft Visual Studio forms of these languages. (They do accept the Express editions)

Clearly, this is a bit *problematic* for me. Theoretically, I could use Mono and write my programs in C# or VB, but I'm not sure they would be accepted (and I have yet to find a safe way to install Mono without destroying my entire database of libraries). And why do they limit it to J# in the Java realm? Why not allow straight Java?
And none of that compares to the complete lack of acceptance for C, straight C++, or languages like Python or Perl.

It's a little too late to send them a formal complaint, and would have been too late when I was first notified that I would be participating.

Discuss.

---

### Post by cprofitt on 2008-03-28
This life.

Get VirtualBox, install Windows, install Express Edition

or 

Get VirtualBox, install Linux, Install Mono and see if they will accept your code... if they are console apps I do not see why they would not, but... perhaps there would be differences.

---

### Post by klange on 2008-03-28
> **PrivateVoid said:**
> This life.

Get VirtualBox, install Windows, install Express Edition

or 

Get VirtualBox, install Linux, Install Mono and see if they will accept your code... if they are console apps I do not see why they would not, but... perhaps there would be differences.

Option A doesn't work as I don't have a Windows disc and I'm not going to break the law. I also don't have the hard disk space to create a 6GB image. I'll probably take a mini distro and install Monodev on it and hope for the best.

---

### Post by phrostbyte on 2008-03-28
That just isn't right. This is ACM doing this competition? Something isn't right here. ACM shouldn't be forcing you to use Microsoft products to compete. That's just disingenuous.

---

### Post by klange on 2008-03-28
> **phrostbyte said:**
> That just isn't right. This is ACM doing this competition? Something isn't right here. ACM shouldn't be forcing you to use Microsoft products to compete. That's just disingenuous.
You'd think that, but it says right on their page

On a side note, my USB stick's X server won't start... (faulty glx library, "deleted" it, good to go, installing mono right now)

---

### Post by Dragonbite on 2008-03-28
Are they trying to use languages that can be compiled down to the CRL and that's why they limit J# instead of including Java?  Do they want to make the interface similar at least to WinForms?

What format do they want to receive it in? If  they want a full .NET solution then they may not want to bother with other IDEs like Eclipse, NetBeans, etc., and instead use ONE IDE which allows them to open, complie and maybe benchmark using the same tools so as to be able to compare apples-to-apples.

If you want to participate then do whatever you need. It isn't going to kill you or taint your soul to use Microsfot products.  I use .NET at work and I am still using Linux at home, so it isn't going to taint your soul (much). ;)

---

### Post by klange on 2008-03-28
> **Dragonbite said:**
> Are they trying to use languages that can be compiled down to the CRL and that's why they limit J# instead of including Java?  Do they want to make the interface similar at least to WinForms?
They're all console-based, so it's definitely not interface restrictions. I don't think it's as complicated as that, as long as it's code that can be executed (and on that topic, Java can be made into separate binaries, albeit large ones. GCJ has no problem turning my .java's into binaries)

> What format do they want to receive it in? If  they want a full .NET solution then they may not want to bother with other IDEs like Eclipse, NetBeans, etc., and instead use ONE IDE which allows them to open, complie and maybe benchmark using the same tools so as to be able to compare apples-to-apples.
I believe they just want the code, they're fairly short little things (one of my teammates and I just did all of last years problem sets in 3 hours, which the teams competing then couldn't even do)

> If you want to participate then do whatever you need. It isn't going to kill you or taint your soul to use Microsfot products.  I use .NET at work and I am still using Linux at home, so it isn't going to taint your soul (much). ;)
I've decided to boot to my "USBuntu", which I slapped MonoDevelop on.

Anyway, it's more the ethical dilemma of forcing us to use the languages, not the difficulty in doing it.

---

### Post by macogw on 2008-03-28
ACM here uses normal Java for their programming competitions, I believe.  At least, the training class we have for it is always Java.

---

### Post by klange on 2008-03-28
> **macogw said:**
> ACM here uses normal Java for their programming competitions, I believe.  At least, the training class we have for it is always Java.
Java seems to be the educational standard right now, but I'm sure that will soon shift to C#.

I should have no problem using C#. Before I become a Linux user I did a lot of programming in C#, and I did complete the [4 "hardest" problems from last years problem set](http://home.ogunderground.com/forum.php?do=viewforum&id=9) in the given time (one of which no one did last year, and it was surprisingly simple, albeit the longest and last on the list)

---

