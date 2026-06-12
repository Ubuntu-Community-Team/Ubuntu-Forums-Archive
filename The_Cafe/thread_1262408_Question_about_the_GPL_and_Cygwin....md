---
title: "Question about the GPL and Cygwin..."
date: 2009-09-09
forum: The Cafe
---

### Post by earthpigg on 2009-09-09
this is the only reading i have done pertaining to Cygwin:

[http://en.wikipedia.org/wiki/Cygwin](http://en.wikipedia.org/wiki/Cygwin)

exert:
> 
Cygwin (pronounced /&#712;s&#618;&#609;w&#618;n/[1]) is a Unix-like environment and command-line interface for Microsoft Windows.
...
License 	GPLv2
...
It is free and open source software, released under the GNU General Public License version 2. Today it is maintained by employees of Red Hat, NetApp ***_and many other volunteers._***
...
Red Hat also sells _***commercial licenses to those who wish to redistribute programs that use the Cygwin library under proprietary terms.***_

if Joe contributed code to the GPLv2 version of Cygwin, and that code was accepted and implemented, how does RH license it under other terms without seeking approval from each of the hundreds of "Joes" out there? Joe's code belongs to Joe and was contributed under the terms of the GPL.

Could Linus Torvalds also re-release the entire Linux project under the terms of the Microsoft EULA, even including the source code contributions of thousands and thousands of people *besides* Linus?

more general question:
Explain this to me, please?

i know you can *dual license*. ie: Google Chromium.... i can change it and either release it as GPL'd software, or as Proprietary software as allowed under the terms of the BSD license.

but Cygwin is GPL'd software. the GPL is very explicit on the fact that GPL'd software can not be re-licensed.

---

### Post by juancarlospaco on 2009-09-09
*Here comes the Bump...*
:)

---

### Post by Chronon on 2009-09-09
This: [http://www.cygwin.com/assign.txt](http://www.cygwin.com/assign.txt)

Contributors must assign copyright to Red Hat.  This allows them to dual license it.

---

### Post by juancarlospaco on 2009-09-09
Gpl + bsd ?

---

### Post by Chronon on 2009-09-09
I don't know any specifics but it sounds to me like it allows for packaging of, say, the Cygwin.dll in other projects.  I don't know whether there's any redistribution of the source under these terms or not.  You would have to ask Red Hat about that.  However, as copyright holders they are allowed to release the code (or resulting binaries) under whatever terms they want simultaneously.  

From the FSF:
> **I heard that someone got a copy of a GPL'ed program under another license. Is this possible?**

    The GNU GPL does not give users permission to attach other licenses to the program. But the copyright holder for a program can release it under several different licenses in parallel. One of them may be the GNU GPL.

    The license that comes in your copy, assuming it was put in by the copyright holder and that you got the copy legitimately, is the license that applies to your copy.


---

### Post by earthpigg on 2009-09-09
> **Chronon said:**
> This: [http://www.cygwin.com/assign.txt](http://www.cygwin.com/assign.txt)

Contributors must assign copyright to Red Hat.  This allows them to dual license it.

well, i guess that settles that.

*grumble grumble*

---

