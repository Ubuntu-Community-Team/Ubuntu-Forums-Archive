---
title: "What is the difference between GPL and FreeBSD"
date: 2007-09-04
forum: The Cafe
---

### Post by blithen on 2007-09-04
Yes obviously I don't know what the difference, and please be gentle to a noob. 
GPL obviously means General Public License, but if you search FreeBSD, on google, it comes up with an operating system. (That is an assumption, I actually type in 'BSD' I don't know if that would make a difference.) So what is the difference, I've seen the two compared but to my knowledge one is an Operating System, and one is a license.

---

### Post by ryno519 on 2007-09-04
BSD is a software license, I happen to still have the wording of it in my clipboard coincidentally enough.

> 
* Copyright (c) 1982, 1986, 1990, 1991, 1993
 *      The Regents of the University of California.  All rights reserved.
 *
 * Redistribution and use in source and binary forms, with or without
 * modification, are permitted provided that the following conditions
 * are met:
 * 1. Redistributions of source code must retain the above copyright
 *    notice, this list of conditions and the following disclaimer.
 * 2. Redistributions in binary form must reproduce the above copyright
 *    notice, this list of conditions and the following disclaimer in the
 *    documentation and/or other materials provided with the distribution.
 * 3. All advertising materials mentioning features or use of this software
 *    must display the following acknowledgement:
 *      This product includes software developed by the University of
 *      California, Berkeley and its contributors.
 * 4. Neither the name of the University nor the names of its contributors
 *    may be used to endorse or promote products derived from this software
 *    without specific prior written permission.
 *
 * THIS SOFTWARE IS PROVIDED BY THE REGENTS AND CONTRIBUTORS ``AS IS'' AND
 * ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
 * IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
 * ARE DISCLAIMED.  IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE
 * FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
 * DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS
 * OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
 * HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
 * LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY
 * OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF
 * SUCH DAMAGE.
 *


Clauses 3 and 4 are not in every copy of the BSD license, however.

---

### Post by blithen on 2007-09-04
So...in what ways are they different? They are very basically the same. Both allow the modification of a program, and to use it as your own. Unless FBSD is a distributing purposes, and GPL is well general use of the program, and modifying it yourself without distributing it.

---

### Post by ryno519 on 2007-09-04
> **blithen said:**
> So...in what ways are they different? They are very basically the same. Both allow the modification of a program, and to use it as your own. Unless FBSD is a distributing purposes, and GPL is well general use of the program, and modifying it yourself without distributing it.

FreeBSD is an operating system. The BSD license is what you're talking about. No F. :P

The main difference is that code derived from BSD code can be distributed in any form as long as the copyright remains in tact, the GPL must be distributed with the source code with the copyright remaining in tact.

The other main difference is the GPL is about six miles longer than the BSD. :lolflag:

---

### Post by Bachstelze on 2007-09-04
@ryno519 > There are actually many variants of the BSD licence. The one you quoted is the "four-clause" one, which is not used anymore except in NetBSD. Most people today use a two-clause licence, which goes like this :

```
# Copyright 2007 Firas Kraiem <fkraiem@enib.fr>. All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met :
#
#    1.	Redistributions of source code must retain the above copyright
#	notice, this list of conditions and the following disclaimer.
#    2.	Redistributions in binary form must reproduce the above copyright
#	notice, this list of conditions and the following disclaimer in the
#	documentation and/or other materials provided with the distribution.
#
# THIS SOFTWARE IS PROVIDED "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES,
# INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY
# AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL
# THE AUTHOR BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY,
# OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
# SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
# CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
# ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF
# THE POSSIBILITY OF SUCH DAMAGE.
```

Occasionnally, they add a third clause, which is the same as the fourth one in the version you posted. The third one, better known as the "advertising clause", has been removed to make the licence GPL-compatible.

---

### Post by blithen on 2007-09-04
Gah! Finally. Thank you. I understand now. :D

---

### Post by southernman on 2007-09-04
> **ryno519 said:**
> 
The other main difference is the GPL is about six miles longer than the BSD. :lolflag:I was going to ask... where is the rest of the license. I tried reading the GPL a few nights ago and wound up cracking my head open on the keyboard when falling asleep!

That thing should come in a split-html format... geeeeesh!

---

### Post by Dr. C on 2007-09-04
> **blithen said:**
> So...in what ways are they different? They are very basically the same. Both allow the modification of a program, and to use it as your own. Unless FBSD is a distributing purposes, and GPL is well general use of the program, and modifying it yourself without distributing it.

The big difference between that GPL and FreeBSD licenses comes if you distribute the code or a derived work based on the code. The GPL is known as a copyleft license and is designed so that Free (as in speech) software remains Free when it or a derived work based on it is distributed. The idea is that everyone who gets GPL code also gets as Free Software. On the other hand code licensed under a FreeBSD license can be incorporated into a propriety application.

A good starting place to learn about Free Software and copyleft licenses such as the GPL is the Free Software Foundation [http://www.fsf.org]("http://www.fsf.org")

---

