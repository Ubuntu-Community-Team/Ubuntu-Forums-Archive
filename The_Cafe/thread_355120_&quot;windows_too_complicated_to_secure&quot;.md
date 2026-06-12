---
title: "&quot;windows too complicated to secure&quot;"
date: 2007-02-06
forum: The Cafe
---

### Post by TheRingmaster on 2007-02-06
[Slashdot | Graph of Linux Vs. Windows System Calls]("http://it.slashdot.org/article.pl?sid=07/02/06/1713214&from=rss")

I thought this article on /. was interesting and thought I would share it with you guys/girls. It shows a cool graphic comparing windows and linux (kernel) system calls.

---

### Post by BarfBag on 2007-02-06
That's a pretty cool article.  Like he said - a picture speaks a thousand words.

---

### Post by RAV TUX on 2007-02-06
> **TheRingmaster said:**
> [Slashdot | Graph of Linux Vs. Windows System Calls]("http://it.slashdot.org/article.pl?sid=07/02/06/1713214&from=rss")

I thought this article on /. was interesting and thought I would share it with you guys/girls. It shows a cool graphic comparing windows and linux (kernel) system calls.
> 

Windows is inherently harder to secure than Linux.   There I said it. The simple truth.    
 Many millions of words have been written and said on this topic. I have a couple of pictures. The basic argument goes like this. In its long evolution, Windows has grown so complicated that it is harder to secure. Well these images make the point very well. Both images are a complete map of the system calls that occur when a web server serves up a single page of html with a single picture. The same page and picture. A system call is an opportunity to address memory. A hacker investigates each memory access to see if it is vulnerable to a buffer overflow attack. The developer must do QA on each of these entry points. The more system calls, the greater potential for vulnerability, the more effort needed to create secure applications. 
 The first picture is of the system calls that occur on a Linux server running Apache.      
  [IMG]http://blogs.zdnet.com/images/SysCallApachesmall.jpg[/IMG]
 See larger image [here]("http://blogs.zdnet.com/images/SysCallApache.jpg"). 
 This second image is of a Windows Server running IIS.    
  [IMG]http://blogs.zdnet.com/images/SysCallIISsmall.jpg[/IMG]
 See larger image [here.]("http://blogs.zdnet.com/images/SysCallIIS.jpg") A picture is worth millions of words.
[http://blogs.zdnet.com/threatchaos/?p=311](http://blogs.zdnet.com/threatchaos/?p=311)

Classic.

---

### Post by BarfBag on 2007-02-06
I'm curious to see what a BSD server does.  Or even better - a Mac (which is a heavily modified version of BSD).

---

### Post by rai4shu2 on 2007-02-06
Seeing how this is really just comparing Apache and IIS, I imagine the Mac would look the same as Linux.

---

### Post by rabid emu on 2007-02-06
I don't know if I've ever heard of macs being used as servers.  OS X = desktop OS.  Am I wrong?

---

### Post by rai4shu2 on 2007-02-06
Actually, Mac OSX comes with Apache installed out of box.

---

### Post by steven8 on 2007-02-06
As Scotty, the Chief Engineer said, "The more complicated you make the plumbing, the easier it is to stop up the drain." :-)

---

### Post by Hendrixski on 2007-02-06
Wow, that almost looks like a joke, except it's too intricate.  It has to be real.

Working on a model like that is a nightmare.  I've worked with systems just as convoluted (if not worse) in projects I've done for the defense department.

---

### Post by Choad on 2007-02-06
its apples to oranges

compaing win+apache to lin+apache would be fairer

this is more proof that IIS is easier to exploit

---

### Post by Brainfart on 2007-02-06
rofl
this is the third of [these](http://ubuntuforums.org/showthread.php?p=2098285) [threads](http://ubuntuforums.org/showthread.php?t=354830)

---

