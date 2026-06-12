---
title: "lol , I always come back to Ubuntu."
date: 2007-06-21
forum: The Cafe
---

### Post by Wiebelhaus on 2007-06-21
PCLOS , SUSE , Mandrake , Sabayon , Redhat........

always gravitate back to Ubuntu.

---

### Post by lukeisthecoolest on 2007-06-21
this is my first open source OS and i think it is fantastic!

---

### Post by Wiebelhaus on 2007-06-21
> **lukeisthecoolest said:**
> this is my first open source OS and i think it is fantastic!

I don't feel it's perfect yet , but it certainly is setting the standards.

---

### Post by yatt on 2007-06-22
I did that for a while, then I got enough experience with Ubuntu to set up Debian (ie setting up usplash, configuring wireless, etc) and I prefer it to Ubuntu. Although, I had to give Debian a shot about 3 or 4 times. lol

---

### Post by kevinlyfellow on 2007-06-22
I've been trying different distros lately too.  It started when I found out fedora 7 (the decedent of my first distro, Red Hat) came to a live cd.  It was so beautiful I decided to install it.  Since then I've had an extra partition so I can waste time trying out different distros.

Fedora a beautiful os, but I felt lost in the package manager and thought that building all my apps would have been just as easy.  Now I'm giving good ol' Debian a run (I went with a bare-bones net install and built it up from there... it was too easy though :-( ).  Neither have given me sufficient reason to switch from Ubuntu (they both are very usable though).  Ubuntu is designed very well for the desktop user and its going to be tough to beat.  But I'd be persuaded if I can get something really fun (even if it doesn't work perfect or requires a little bit more work).

I'm going to be trying GoboLinux soon.  This one is an experimental distro that has played around with the directory tree.  It makes it easier to install multiple versions of a piece of software at the same time.  This is actually something I think linux could benefit on, but I'm not really sure, so I'm going to give it a try.  They say that their tree makes package managers unnecessary...

---

### Post by FuturePilot on 2007-06-22
Lol. Same here. Like you said, it's not perfect, but it sure does seem to be on the leading edge when it comes to a lot of things.:D

---

### Post by Adamant1988 on 2007-06-22
The only thing that really keeps me using Ubuntu over another distro (not another OS, I have no problems using other OSes) is that the repos strike a strong middle ground between free and non-free.  They don't include everything OOTB but they don't make it difficult to get.  That's hard to find in a distro right now.

---

### Post by thisllub on 2007-06-22
I first tried Ubuntu  Dapper.
I didn't see how it was any better than the SUSE I was using at the time.
By Edgy that had changed and now Ubuntu is the easiest Linux to maintain.

I am currently running a Fedora 7 and 2 Feisty machines.
I estimate that Debian / Ubuntu systems take about half the time to maintain that Fedora does maybe less.

My next  comparison will be Debian Etch with  Feisty.
I will probably have a good look at SUSE 10.3 as well.

---

### Post by Quillz on 2007-06-22
I've just tried PCLinuxOS, I didn't really like it. The only Linux distro I can stand to use are openSUSE and Ubuntu, and even then, I just stronger prefer Ubuntu.

---

### Post by simonn on 2007-06-22
> **kevinlyfellow said:**
> I'm going to be trying GoboLinux soon.  This one is an experimental distro that has played around with the directory tree.  It makes it easier to install multiple versions of a piece of software at the same time.  This is actually something I think linux could benefit on, but I'm not really sure, so I'm going to give it a try.  They say that their tree makes package managers unnecessary...

The same can be done with any distro, even Ubuntu. All they do is install each bit of software into it's own directory and then sym-link whatever needs to be sym-linked to {,/usr{,/local}}/{bin,lib} etc etc.

It would be painfull setting up the symlinks without a package manager!

I, and I am sure many others, do this kind of stuff all the time when developing stuff/writing patches against the CVS version of software when I have the stable version installed.

At, runtime an application will always use the first executable and library it comes across which matches the name it has been told to use. This is where PATH and LD_LIBRARY_PATH come in. If you want to use /testing/bin/myprog instead of /usr/bin/myprog and want it to use /testing/lib/mylib.so.0.0.0 instead of /usr/lib/mylib.so.0.0.0 and /testing/bin/myotherprog instead of /usr/bin/myotherprog simply run:

$ PATH="/testing/bin:$PATH" LD_LIBRARY_PATH="/testing/lib:$LD_LIBRARY_PATH" /testing/bin/myprog

Alternatively:

$ export PATH="/testing/bin:$PATH" 
$ export LD_LIBRARY_PATH="/testing/lib:$LD_LIBRARY_PATH"
# myprog

Will have the same effect, for the entire session in the terminal it is entered into.

---

### Post by fuscia on 2007-06-22
i've installed sabayon twice, but each time, the package management sent me back. i've lost my enthusiasm for trying out other distros' live cds, as well. i think what i really wish for is new window managers coming out all the time. but then, i'd probably just keep ending up back with openbox.

---

### Post by kevinlyfellow on 2007-06-22
> **simonn said:**
> The same can be done with any distro, even Ubuntu. All they do is install each bit of software into it's own directory and then sym-link whatever needs to be sym-linked to {,/usr{,/local}}/{bin,lib} etc etc.

It would be painfull setting up the symlinks without a package manager!

I, and I am sure many others, do this kind of stuff all the time when developing stuff/writing patches against the CVS version of software when I have the stable version installed.

At, runtime an application will always use the first executable and library it comes across which matches the name it has been told to use. This is where PATH and LD_LIBRARY_PATH come in. If you want to use /testing/bin/myprog instead of /usr/bin/myprog and want it to use /testing/lib/mylib.so.0.0.0 instead of /usr/lib/mylib.so.0.0.0 and /testing/bin/myotherprog instead of /usr/bin/myotherprog simply run:

$ PATH="/testing/bin:$PATH" LD_LIBRARY_PATH="/testing/lib:$LD_LIBRARY_PATH" /testing/bin/myprog

Alternatively:

$ export PATH="/testing/bin:$PATH" 
$ export LD_LIBRARY_PATH="/testing/lib:$LD_LIBRARY_PATH"
# myprog

Will have the same effect, for the entire session in the terminal it is entered into.

It has tools to help you do that.  I tried it out a bit last night, but I need to get wireless up and running before I do anything.  Thanks for the advice.

---

### Post by init1 on 2007-06-22
> **sx66gns said:**
> PCLOS , SUSE , Mandrake , Sabayon , Redhat........

always gravitate back to Ubuntu.
Yeah, I find that Ubuntu is reliable and I usually keep it on my hard drive.

---

