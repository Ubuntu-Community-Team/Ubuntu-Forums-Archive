---
title: "The 'bit' architectures"
date: 2011-05-02
forum: The Cafe
---

### Post by Colo2 on 2011-05-02
I was wondering if someone could explain to me why:

64 bit is written as 64 only.

However, 32 bit can be written:

x86, i386 and 32

Do they all mean the same thing?

---

### Post by An Sanct on 2011-05-02
x86, i386 and 32 are the same architectures and are also known as IA-3**2** ([Intel Architecture 32]("http://en.wikipedia.org/wiki/IA-32")), from the early 8086 (in 1978), 80286, 80386, 80486, first Pentiums - 80586,... until today

64bit, also found under the code AMD64 or x64, started with an AMD opteron, being the first, the name just stuck.

---

### Post by aaaantoine on 2011-05-02
In Ubuntu / Debian packaging, 64-bit is referred to as "amd64" while in Arch Linux it's referred to as "x86_64".

In the same way, Ubuntu calls 32-bit "i386" while Arch calls it "i686".  The Arch packages most likely won't work on 386, 486, or Pentium I CPUs.  Then again, the people who are using these computers should be grateful for the ability to run Linux at all.

Both have to specify x86 in some capacity (instead of 32bit / 64bit) because it refers to the processor type. ARM, the *other* commonly used processor (though rarely on desktops), is not compatible with x86.  ARM doesn't distinguish between 32-bit and 64-bit for whatever reason, probably having to do with a fundamental difference between the way that x86 and ARM each work.

---

### Post by ssam on 2011-05-02
when people just say 32bit or 64bit you can often imply that they mean the x86-32 or x86-64. but there are lots of other architectures like sparc and powerpc that have 32 and 64 bit variants.

there is no 64bit ARM yet.

---

### Post by Lucradia on 2011-05-02
IA-64 also exists: [http://en.wikipedia.org/wiki/Itanium](http://en.wikipedia.org/wiki/Itanium)

---

### Post by RiceMonster on 2011-05-02
x86 refers to 32 bit intel architectures. i386 is a specific, and very old 32 bit intel architecture. There is also i486, i586, and i686.

---

