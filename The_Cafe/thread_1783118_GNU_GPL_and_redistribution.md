---
title: "GNU GPL and redistribution"
date: 2011-06-15
forum: The Cafe
---

### Post by mogeb on 2011-06-15
Hi everyone,
i am developping an application that i want to sell. But in order to make my application work properly, it has to install a small program that is under GNU GPL. 
So my question is, how can I do this without violating the GPL?
I should specify that my application is totally independant from this other software that is GPL'd.
Thank you

---

### Post by prodigy_ on 2011-06-15
> **mogeb said:**
> Hi everyone,
i am developping an application that i want to sell. But in order to make my application work properly, it has to install a small program that is under GNU GPL.
GPL doesn't prohibit bundling:
[http://en.wikipedia.org/wiki/GNU_General_Public_License#Communicating_and_bundling_with_non-GPL_programs](http://en.wikipedia.org/wiki/GNU_General_Public_License#Communicating_and_bundling_with_non-GPL_programs)

---

### Post by mogeb on 2011-06-15
Thanks for your reply. I understand it doesn't prohibit bundling but do I have to include the GPL as well (in a text file) in the CD? Or do I have to write anything that says that this software on the side is under GPL? And do i have to distribute the source code as well?

---

### Post by Chronon on 2011-06-15
Yes.  According to my understanding, you must declare the GPL software as such and make the source code available upon request.

---

### Post by 3Miro on 2011-06-15
GNU wants you to include GPL with the package, but I don't. I have a 100 lines program and I am not going to bundle it with 20 pages of legal documentation. I just make it clear that I am distributing this under GPL and I give a web-link.

---

### Post by mips on 2011-06-15
[http://www.gnu.org/licenses/gpl-2.0.html](http://www.gnu.org/licenses/gpl-2.0.html) See point 3.

[http://en.wikipedia.org/wiki/GNU_General_Public_License#Communicating_and_bundling_with_non-GPL_programs](http://en.wikipedia.org/wiki/GNU_General_Public_License#Communicating_and_bundling_with_non-GPL_programs)
> Communicating and bundling with non-GPL programs
The mere act of communicating with other programs does not, by itself, require all software to be GPL; nor does distributing GPL software with non-GPL software. However, minor conditions must be followed that ensures the rights of GPL software is not restricted. The following is a quote from the gnu.org GPL FAQ, which describes to what extent software is allowed communicate with and be-bundled-with GPL programs:
'What is the difference between an &#8220;aggregate&#8221; and other kinds of &#8220;modified versions&#8221;?
An &#8220;aggregate&#8221; consists of a number of separate programs, distributed together on the same CD-ROM or other media. The GPL permits you to create and distribute an aggregate, even when the licenses of the other software are non-free or GPL-incompatible. The only condition is that you cannot release the aggregate under a license that prohibits users from exercising rights that each program's individual license would grant them.
Where's the line between two separate programs, and one program with two parts? This is a legal question, which ultimately judges will decide. We believe that a proper criterion depends both on the mechanism of communication (exec, pipes, rpc, function calls within a shared address space, etc.) and the semantics of the communication (what kinds of information are interchanged).
If the modules are included in the same executable file, they are definitely combined in one program. If modules are designed to run linked together in a shared address space, that almost surely means combining them into one program.
By contrast, pipes, sockets and command-line arguments are communication mechanisms normally used between two separate programs. So when they are used for communication, the modules normally are separate programs. But if the semantics of the communication are intimate enough, exchanging complex internal data structures, that too could be a basis to consider the two parts as combined into a larger program.
The FSF thus draws the line between "library" and "other program" via 1) "complexity" and "intimacy" of information exchange, and 2) mechanism (rather than semantics), but resigns that the question is not clear-cut and that in complex situations, case law will need to decide.

You could always contact the FSF & SFLC for clarification and assistance.

---

### Post by juancarlospaco on 2011-06-15
GPL doesn't prohibit selling

---

### Post by mogeb on 2011-06-15
The GPL doesn't prohibit selling, but anyways I'm not making selling the GPL'd software, the price of the CD is entirely for the code I have written myself.

Thanks for your answers. So I guess i have to include in a text file on the CD, that I am distributing a GPL'd software, and that the users can find it's source code on the web (and I could provide the web-link). Am I right?

---

### Post by koenn on 2011-06-15
> **mogeb said:**
> The GPL doesn't prohibit selling, but anyways I'm not making selling the GPL'd software, the price of the CD is entirely for the code I have written myself.

Thanks for your answers. So I guess i have to include in a text file on the CD, that I am distributing a GPL'd software, and that the users can find it's source code on the web (and I could provide the web-link). Am I right?

you should also include (a link to) the GPL itself, so the users of the GPL'd program are aware of their rights. 

And re the source code, IIRC, merely linking to someone elses repo isn't always sufficient, because the responsibility to provide the source code lies with the distributor of the binary - that is you, so you have to be in a position to guarantee that the users have (now and in the future) access to the source code. When just pointing to someone elses repo, you have no means of guaranteeing that. 
(I could be mistaking, but you might want to check this if you're going to sell big)

---

### Post by mogeb on 2011-06-15
> **koenn said:**
> you should also include (a link to) the GPL itself, so the users of the GPL'd program are aware of their rights. 

And re the source code, IIRC, merely linking to someone elses repo isn't always sufficient, because the responsibility to provide the source code lies with the distributor of the binary - that is you, so you have to be in a position to guarantee that the users have (now and in the future) access to the source code. When just pointing to someone elses repo, you have no means of guaranteeing that. 
(I could be mistaking, but you might want to check this if you're going to sell big)

Great thanks for your help.

---

### Post by forrestcupp on 2011-06-15
> **koenn said:**
> And re the source code, IIRC, merely linking to someone elses repo isn't always sufficient, because the responsibility to provide the source code lies with the distributor of the binary - that is you, so you have to be in a position to guarantee that the users have (now and in the future) access to the source code. When just pointing to someone elses repo, you have no means of guaranteeing that. 
(I could be mistaking, but you might want to check this if you're going to sell big)
I'm pretty sure it's common and accepted practice to link to the original source code repos. If not, then the hundreds of custom Ubuntu-based distros out there that use the Ubuntu repos are in trouble.

---

### Post by koenn on 2011-06-16
> **forrestcupp said:**
> I'm pretty sure it's common and accepted practice to link to the original source code repos. If not, then the hundreds of custom Ubuntu-based distros out there that use the Ubuntu repos are in trouble.

It depends. If these hundreds of custom Ubuntu-based distros are using ubuntu binaries and just offer a different software selection, custom config files, or some additional themes, and especially if they are using Ubuntu repos for the binaries as well, they're probably in compliance with the GPL as the offer source code from the same site and by the same method as they are offering the binaries. See eg section 6 of GPL v3

Other than that, I thought it'd be better to let the OP know what to look out for and let him make an informed decision. 

The exact rule also vary with the different versions of the GPL.

Lastly, the GNU project maintains a FAQ that addresses these issues : 
[http://www.gnu.org/licenses/gpl-faq.html#UnchangedJustBinary](http://www.gnu.org/licenses/gpl-faq.html#UnchangedJustBinary)
[http://www.gnu.org/licenses/gpl-faq.html#WhyMustIInclude](http://www.gnu.org/licenses/gpl-faq.html#WhyMustIInclude)
[http://www.gnu.org/licenses/gpl-faq.html#WhatIfWorkIsShort](http://www.gnu.org/licenses/gpl-faq.html#WhatIfWorkIsShort)

---

### Post by forrestcupp on 2011-06-16
> **koenn said:**
> 
Other than that, I thought it'd be better to let the OP know what to look out for and let him make an informed decision. 


Good point. 

If it's not too huge of a project, and you're using physical media, it might be easier just to include all of the GPLed source code in a folder on the CD/DVD instead of having to maintain a repository indefinitely.

---

