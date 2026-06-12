---
title: "Linux &amp; performance in multy core processors ;compared to windows 7"
date: 2009-05-22
forum: The Cafe
---

### Post by praveesh on 2009-05-22
Hi,
I came to know that in windows 7 there is performance improvement in multy core processors . Is there any such performance improvement in linux? (does such a technology implemented in linux?). Do any one know how such performance improvement is made(or implemented . What is this technology?). When I went through the added features of win 7 ,other than this performance improvement & improved booting and shutting down speed , all the visual effects seems nothing in front of the brand new kde 4.x . By around the releasing date of windows 7, kde 4.4 will be released with rocking features & improved performance and stability .But there is one important fact that in 7 the widgets are executed in a seperate process which improves stability. On the other hand , in kde  the plasmoids are parts of plasma and executed in a single process (when one plasmoid crash the whole desktop will hang)

---

### Post by binbash on 2009-05-23
If you say linux, it is linux kernel not applications run on linux.But you are talking about KDE and its plasmoids.

---

### Post by praveesh on 2009-05-25
> **binbash said:**
> If you say linux, it is linux kernel not applications run on linux.But you are talking about KDE and its plasmoids.

Iam sorry about that . By the word linux , I meant the complete GNU/linux operating system which consists of a desktop environment . In my opinion KDE is the only desktop environment capable of competing with the desktop of windows . Thats why I spoke about that .

---

### Post by 3rdalbum on 2009-05-25
> **praveesh said:**
> Hi,
I came to know that in windows 7 there is performance improvement in multy core processors . Is there any such performance improvement in linux? (does such a technology implemented in linux?).

The Windows multi-core performance improvement is not a specific technology. It's just a better-designed SMP mechanism. When I say "better", I mean "better than the one in Vista".

Linux not only has a well-designed SMP mechanism to begin with, but it has the choice of several others depending on what you're doing with the computer! Ubuntu generally ships with the best one for general-purpose computing, and in my experience it's a lot better than the one in Vista. For me, at least.

There is always work going into scheduling and multi-core support on Linux. This is one area where I don't think Linux will fall behind.

---

### Post by fballem on 2009-05-25
> **praveesh said:**
> Iam sorry about that . By the word linux , I meant the complete GNU/linux operating system which consists of a desktop environment . In my opinion KDE is the only desktop environment capable of competing with the desktop of windows . Thats why I spoke about that .

Just some small points that I have learned, sometimes painfully, over the past year or so that I have been using ubuntu:

[LIST=1]
[*]One of the key advantages in GNU/Linux is that one can choose a specific desktop. Two of the more popular ones are KDE and GNOME, but there are a lot of others. People who have been using Linux for a long time will be quick to remind you that Linux does not include a desktop.
[*]Glad that you are enjoying your KDE experience. If you don't mind a different point of view, I found KDE to be cumbersome. GNOME, for me, is much less cumbersome, and is one of the key reasons that I switched from Vista to ubuntu. Each desktop has their strengths and challenges and there is no one desktop that is perfect for all people.
[*]Since there are many distributions, and many desktops, it is generally helpful to avoid lumping them in all together - especially when providing opinions. Many flamewars have started with the simple words, "... in my opinion.", usually as part of a statement saying "Linux is ...", when one really means specific aspects of GNU/Linux.
[*]As another poster pointed out, Linux has been doing multi-core processing for years and does it very well.
[*]Vista was the first version of Windows that implemented multi-core processing, and is the first version of Windows that provided a 64-bit version. Windows XP has a version that implements 64-bit using add-ons, but this was built later, and Windows XP is still a 32-bit operating system. It will take them a while to catch up with Linux, but I agree that Windows 7 appears to be better than Vista.
[/LIST]

---

### Post by HavocXphere on 2009-05-25
I recall reading something about MS making lots of changes to make Win7 scale better with many cores (Many being 8-32). Currently I think linux and windows use the cores to a similar degree of effectiveness but I reckon win7 will gain more from 32 cores than linux does.

Most of the gains are made in how each process gets allocated a "slice" of the available processor time. With XP the slices are pretty much the same for all processes while with Vista/Win7 the OS tries to allocate them more "intelligently"...whatever that means.

EDIT: Scheduling...thats the correct word. thx 3rdalbum.

That being said, its based mostly on what I've read & I'm not familiar with the exact details.

With the whole multicore business its also important to keep in mind that the major gains will come not from changes in the OS, but rather from the way in which the applications themselves are coded. i.e. the app developer needs to write his app in such a way that it can easily be split into tasks/threads for each core.

---

