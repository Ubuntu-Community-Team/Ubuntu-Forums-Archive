---
title: "I wish Ubuntu installation offered the choice to rebuild source..."
date: 2009-08-27
forum: The Cafe
---

### Post by Sporkman on 2009-08-27
Ubuntu offers ease of installation, very good hardware detection and compatibility, and general quality that we've all come to enjoy.

However, I can't help but wonder if we could get better results if the system were compiled from scratch on our own machines.

Sure there are other distros where this is included in the installation methodology, but they may not measure up to Ubuntu in the qualities I mentioned above.

I wish we could go through the usual Ubuntu installation process, except near the end it asks "would you like to rebuild the system from source?", and if you answer "yes" it will rebuild the system with -march=native. All you need to do is come back a couple of days later & your ubuntu installation is custom compiled for your hardware. I don't mind waiting a couple of days, I just don't want to have to do anything or make difficult decisions (unlike, for example, in Gentoo installation).

What do you guys think?

---

### Post by BackwardsDown on 2009-08-27
> I just don't want to have to do anything or make difficult decisions (unlike, for example, in Gentoo installation).

If you are not willing to do that, I don't you can expect any significant improvement in speed or reliability after compiling.

---

### Post by Sporkman on 2009-08-27
> **BackwardsDown said:**
> If you are not willing to do that, I don't you can expect any significant improvement in speed or reliability after compiling.

Wouldn't the mere addition of -march=native make a significant improvement?

---

### Post by dragos240 on 2009-08-27
Also, I wonder what the 'deb-src" repos are, do they contain the source?

---

### Post by BackwardsDown on 2009-08-27
> **Sporkman said:**
> Wouldn't the mere addition of -march=native make a significant improvement?

Its hard to say but here is a quote on the Gentoo wiki ([http://www.gentoo.org/doc/en/gcc-optimization.xml](http://www.gentoo.org/doc/en/gcc-optimization.xml))

[quote=Gentoo wiki]Despite the bragging you'll find on the internet, aggressive CFLAGS and CXXFLAGS are far more likely to harm your programs than do them any good. Keep in mind that the reason the flags exist in the first place is because they are designed to be used at specific places for specific purposes. Just because one particular CFLAG is good for one bit of code doesn't mean that it is suited to compiling everything you will ever install on your machine![/quote]

---

### Post by RiceMonster on 2009-08-27
> **Sporkman said:**
> Wouldn't the mere addition of -march=native make a significant improvement?

not really.

---

### Post by Sporkman on 2009-08-27
> **BackwardsDown said:**
> Its hard to say but here is a quote on the Gentoo wiki ([http://www.gentoo.org/doc/en/gcc-optimization.xml](http://www.gentoo.org/doc/en/gcc-optimization.xml))

They're talking about -O3, etc. -march=native isn't an aggressive optimization, it just ensures that the instruction set generated is specific to your processor.

What I'm proposing is the installer rebuild with the exact same settings that the repo binaries are built with, except with the addition of -march=native.

---

### Post by v8YKxgHe on 2009-08-27
Firstly, Ubuntu isn't really targeted towards that userbase and secondly - there would not be enough space on the disk.

---

### Post by RiceMonster on 2009-08-27
> **AlexC_ said:**
> Firstly, Ubuntu isn't really targeted towards that userbase and secondly - there would not be enough space on the disk.

You could have it download all the packages, so then you could wait 2.5 days instead of simply 2 days :)

---

### Post by Simian Man on 2009-08-27
> **Sporkman said:**
> They're talking about -O3, etc. -march=native isn't an aggressive optimization, it just ensures that the instruction set generated is specific to your processor.

What I'm proposing is the installer rebuild with the exact same settings that the repo binaries are built with, except with the addition of -march=native.

If you're using the i386 version it may make some difference, but if you're using the x86-64 version it wouldn't do much of anything.

---

### Post by juancarlospaco on 2009-08-27
**Use minimal install and compile...**
:)

---

### Post by Sporkman on 2009-08-27
> **juancarlospaco said:**
> **Use minimal install and compile...**
:)

That's a lot more work than what I'm proposing. :)

Plus the minimal part would be pre-compiled binaries.

---

### Post by Sporkman on 2009-08-27
> **Simian Man said:**
> If you're using the i386 version it may make some difference, but if you're using the x86-64 version it wouldn't do much of anything.

Are x86-64 processors that standardized these days? What about all the different caching architectures - does the compiler take those into account, or is that transparent (i.e. the processor itself makes caching decisions)..?

---

### Post by Simian Man on 2009-08-27
> **Sporkman said:**
> Are x86-64 processors that standardized these days? What about all the different caching architectures - does the compiler take those into account, or is that transparent (i.e. the processor itself makes caching decisions)..?

It's just that there is a difference between the i386 architecture and the actual capabilities of the 32 bit architectures most people.  The x86-64 architecture is much more advanced, however, and is much more representative of the actual capabilities of your processor.

Caching has very little to do with it. A bigger cache is better, but the cache size is transparent from the actual architecture.  The only time the knowing the size of the cache will get you significant improvement is when blocking up numerical calculations such as very large matrix multiplications.

---

