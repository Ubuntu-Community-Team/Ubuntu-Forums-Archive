---
title: "gpl question"
date: 2008-04-14
forum: The Cafe
---

### Post by vano512 on 2008-04-14
Can company produce program under GPL license if it used some non GPL  licensed DLLs(Case 1: DLL is produced by the company. Case 2: DLL is produced by some other company) while creating the program?

---

### Post by heartburnkid on 2008-04-14
As I understand it, the program can still be produced under the GPL as long as the library code is dynamically linked, and not statically linked (i.e. integrated into the program).  Since we're talking about separate DLL files, I think it's OK.

IANAL, though, and I'm also not a Free Software expert.

---

### Post by Ozor Mox on 2008-04-14
I could be wrong here, but I think the software can use the LGPL if it links to non-free libraries.

---

### Post by saulgoode on 2008-04-14
> **vano512 said:**
> Can company produce program under GPL license if it used some non GPL  licensed DLLs(Case 1: DLL is produced by the company. Case 2: DLL is produced by some other company) while creating the program?

There is, from a GPL standpoint, no difference between your two cases. It does not matter whether the source of the software is from a different company or not.

Second, GPL software can link with non-GPL software, as long as the non-GPL license is compatible (in general, this means a Free license but without copyleft terms). 

I will assume that you mean the DLL is licensed using a non-Free license which is incompatible with the GPL. In this case, the short answer is "no", you may not link them. 

There is an exception made for "system" libraries: GPLv2 says the following, near the end of section 3

> [I]    However, as a special exception, the source code distributed need not include anything that is normally distributed (in either source or binary form) with the major components (compiler, kernel, and so on) of the operating system on which the executable runs, unless that component itself accompanies the executable. 
[/I]

Of course, the author of the program may grant an exception to the GPL permitting such linking; but that is effectively dual licensing with the exception not being GPL.

As pointed out, the LGPL (Lesser General Public License) does permit such linking. 

[http://www.gnu.org/licenses/gpl-faq.html]("http://www.gnu.org/licenses/gpl-faq.html#GPLIncompatibleLibs")

---

### Post by vano512 on 2008-04-16
> Second, GPL software can link with non-GPL software, as long as the non-GPL license is compatible (in general, this means a Free license but without copyleft terms).

So as I see if the DLL is licensed under free(Free usage and Free redistribution) license(not open source), there is no problem?

Also, are there any licenses which are widely used and compatible for the situation: when the DLL(s) is closed source but free to use and redistribute(As I'm not licensing expert it would be helpful :) )?

---

