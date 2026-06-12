---
title: "Programming In Linux"
date: 2009-12-30
forum: The Cafe
---

### Post by srinat on 2009-12-30
Hi(I need some expert help on this one),
    I'm a undergraduate student in a university and next semester I have a paper on Programming in unix .The reference book is
"The Unix Programming environment" 
by Brian Kerningham and Rob Pike(Prentice Hall).
The syllabus covers 
*Unix File system
*Shell
*Filter(grep,awk)
*System Calls
*Shell and I/O Programming

My Question is "Does this syllabus comprehensively cover the topics needed to learn programming in linux?"
 Also are there any "classical or standard books" on these topics?     
   Thanks in advance for the answers..

31/12/09
Thank you all for the suggestions..

---

### Post by ZeroSpawn on 2009-12-30
Those covers the bases of Linux/Unix. Don;t expect to be making huge money making programs. The class will get you started in the right track.

---

### Post by Xbehave on 2009-12-30
It looks to me that it only covers shell programming, while it is the most important part of unix, there are other aspects (e.g GUI programming, c,c++,python,dbus,etc)

---

### Post by LeifAndersen on 2009-12-30
Agreed, pick up a good copy of QT Creator, and follow those tutorials.  You will learn a bit about making GUI applications in linux.

---

### Post by BrokenKingpin on 2009-12-30
You will want to get a book that covers the GCC/G++ C/C++ compiler. I wouldn't wory too much on GUI sdks like QT until you have covered that off. Although GUI development is an important topic to probably cover, you need to learn the basics well before getting to the GUI stuff.

Edit: The book you mentioned sounds like a great book for learning the basics of a UNIX system, which is a very good thing to know before really diving into UNIX development.

---

### Post by Bölvaður on 2009-12-30
My Question is "Does this syllabus comprehensively cover the topics needed to learn programming in linux?"

I would say no.


But then I'd change my mind and say yes.
It's not going to be as easy as it could be, because it's not linux based, but then again, it will help you by being difficult.

---

### Post by lostinxlation on 2009-12-30
That's the first book I picked when I started using Unix 19 years ago. Very well known book in Unix community and it's a good one to start learning shell programming with, however, it won't cover the detailed system programming using higher level language. 
It's a book for starters. not for someone about to be experts.
And  this book is written based on Borne shell, so that if you are on B shell derivatives, it's good, but if you are a C-shell fan, you might be annoyed(like I did).

---

### Post by jbrown96 on 2009-12-30
That looks like a tremendous syllabus. I'm a CS student graduating this Spring, so I know the cirriculums. We use all Linux systems at my school, so all classes are centered around Linux.

In my Operating Systems class, we covered the file system and system call stuff. This is probably what I would call Linux programming, although Unix programming is probably a more correct term. 

Then there's the shell and language processing (awk, grep, sed) stuff. We covered that in a separate class, but it's also Linux programming, but again it's more accurate to call it Unix. 

That's a very ambitious class! 
For the system calls, all you need are the man pages (I think you will need to install manpages-dev or something similar to get all of them). Ask your professor about how to use them. On the first day of my OS class, my professor made the comment that this class is about learning how to use/understand man pages. 
Tennanbaum, who made Minix (of which Linus was very critical), wrote a very good OS book called Modern Operating Systems. I highly recommend it, and although he made Minix, the book uses Linux for all teaching points (except when making comparisons between OSes).

Regular expressions are also very important, and are the lifeblood of Unix admins, so be sure to learn them. I never really found or needed particular books for shell programming and regexen. 

Good luck; that looks like a lot to cover in a semester.

---

### Post by 3Miro on 2009-12-30
The book looks like a "Linux system Administration" or "Basic Linux System Scripting" than "complete" programing guide.

C/C++ is a system independent subject, but most of Linux is written in C/C++ and I would say good knowledge in it is a must. Add custom Makefiles to that.

Understanding of either GTK or QT (the underlying library tools for Gnome and KDE), is also requires for a "complete" course.

File system, compiling and installing apps as well as basic system scripting is another subject (it seems to be covered by the book).

This leaves more advanced topics of the details of Bash, Python and Perl scripting.

I would call the above complete,however, it should be covered in at least 3 separate courses (except for the C/C++, that is 2-3 courses by itself, I am only counting the Linux specific stuff).

---

### Post by jbrown96 on 2009-12-31
> **3Miro said:**
> The book looks like a "Linux system Administration" or "Basic Linux System Scripting" than "complete" programing guide.

C/C++ is a system independent subject, but most of Linux is written in C/C++ and I would say good knowledge in it is a must. Add custom Makefiles to that.

Understanding of either GTK or QT (the underlying library tools for Gnome and KDE), is also requires for a "complete" course.

File system, compiling and installing apps as well as basic system scripting is another subject (it seems to be covered by the book).

This leaves more advanced topics of the details of Bash, Python and Perl scripting.

I would call the above complete,however, it should be covered in at least 3 separate courses (except for the C/C++, that is 2-3 courses by itself, I am only counting the Linux specific stuff).

I strongly disagree that GTK and QT knowledge is part of Linux programming. CS programs rarely do anything with GUI programming. It's certainly interesting, but most Linux programming is not GUI-based, especially the stuff you will learn in CS.
There's simply no way that all that stuff can be covered in a single course. I think the OP's syllabus already had way to much to cover in a semester. There's very little use in having a cursory coverage of those topics, and adding GUI programming to that is way too much.

---

