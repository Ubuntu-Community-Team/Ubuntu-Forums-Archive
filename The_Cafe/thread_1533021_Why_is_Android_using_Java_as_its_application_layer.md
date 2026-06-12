---
title: "Why is Android using Java as its application layer environment"
date: 2010-07-17
forum: The Cafe
---

### Post by mercury80 on 2010-07-17
I am puzzled as to why google what to use java in stead of something like C++ for Apps. I understand Dalvik Virtual Machine is very good, but for something so sensitive to power consumption as hand held units... Can someone enlighten me?

Here is a speed comparison i saw almost a year ago:
[http://www.youtube.com/watch?v=It8xPqkKxis](http://www.youtube.com/watch?v=It8xPqkKxis)

---

### Post by gnomeuser on 2010-07-17
ease of development, latching on to an already established modern language, faster development for applications, modern features such as garbage collection.

Android plays other tricks to save power, such as very aggressive suspending and an approach to multitasking where applications are largely also "suspended" when not in use.

---

### Post by Shining Arcanine on 2010-07-17
> **mercury80 said:**
> I am puzzled as to why google what to use java in stead of something like C++ for Apps. I understand Dalvik Virtual Machine is very good, but for something so sensitive to power consumption as hand held units... Can someone enlighten me?

Here is a speed comparison i saw almost a year ago:
[http://www.youtube.com/watch?v=It8xPqkKxis](http://www.youtube.com/watch?v=It8xPqkKxis)

Google supports programming in C/C++ on Android. It is just not well known:

[http://developer.android.com/sdk/ndk/index.html](http://developer.android.com/sdk/ndk/index.html)

> **gnomeuser said:**
> ease of development, latching on to an already established modern language, faster development for applications, modern features such as garbage collection.

Android plays other tricks to save power, such as very aggressive suspending and an approach to multitasking where applications are largely also "suspended" when not in use.

Garbage collection is not a modern feature because LISP had it in 1958. Historically speaking, people have been against doing serious programming in garbage collected languages because they are slow.

Also, C++ is a modern programming language. I believe that languages including and more recent than ALGOL 68 are all considered to be modern.

---

### Post by BuffaloX on 2010-07-17
Even the Commodore 64 Microsoft Basic Interpreter had garbage collection.
It sucks.

---

