---
title: "Why &quot;real&quot; UNIX vs. UNIX-like for servers"
date: 2010-08-20
forum: The Cafe
---

### Post by Cuddles McKitten on 2010-08-20
Can anyone direct me towards something that might explain why some organizations choose Solaris, AIX, HP-UX, etc. over Linux and the BSDs for production servers?  I know almost nil about the non-free Unices and can't seem to find some site that explains the basic strengths (and weaknesses) of each of them -- especially from a business or organizational standpoint.

---

### Post by Spice Weasel on 2010-08-20
[http://people.freebsd.org/~murray/bsd_flier.html](http://people.freebsd.org/~murray/bsd_flier.html)

[http://www.linuxquestions.org/linux/articles/Technical/UNIX_Vs_Linux?](http://www.linuxquestions.org/linux/articles/Technical/UNIX_Vs_Linux?)

A good place to learn about UNIX is here - [http://www.unix.com/](http://www.unix.com/)

Good luck! :D

---

### Post by oldfred on 2010-08-20
One of my business computer classes years ago explained that you do not choose a computer & operating system but choose the best software for your business. What system that runs on then determines what operating system & computer you need. Very large business' looked at accounting, ERP/MRP or other apps and they ran only on big iron or mainframes. Midsize business' would look at different smaller software systems  which ran on midsize computers. Many midsize computers were Unix based and the vendors also offered very good support.

Of course as Moore's Law took hold the computer power in your cell phone is about as much as those old mainframes, but does not have the channels to connect to many terminals.

Part of Linux's problem still is software. Open software is very good in many cases but companies want vendor support & reliability and are willing to pay for that. Redhat has made a good business on suppling support to Linux systems.

---

### Post by Sporkman on 2010-08-20
> **Spice Weasel said:**
> [http://people.freebsd.org/~murray/bsd_flier.html](http://people.freebsd.org/~murray/bsd_flier.html)


That link is out of date:

> Linux performs well for most applications, however the performance is not optimal under heavy network load. The network performance of Linux is 20-30% below the capacity of FreeBSD running on the same hardware 2. The situation has improved somewhat recently and **the 2.4 release of the Linux kernel will introduce** a new virutual memory system based on the same concepts as the FreeBSD VM system.

...and:

> There are several new journaling filesystems in development for Linux that will fix some of these issues, but these will not be ready for the 2.4 release of Linux.

:)

---

### Post by Spice Weasel on 2010-08-20
> **Sporkman said:**
> That link is out of date:



...and:



:)

Yeah, sorry, I found it after a quick google search. :p

The other links are probably worth it though.

---

### Post by Bachstelze on 2010-08-20
Because there is no entreprise-class Linux distribution available for HP/PA (hence HP-UX), PowerPC (hence AIX) and Sparc (hence Solaris) machines.

Not everyone uses x86/x86-64 toys.

---

### Post by RiceMonster on 2010-08-20
> **Bachstelze said:**
> Not everyone uses x86/x86-64 toys.

"toys"?

---

### Post by Bachstelze on 2010-08-20
> **RiceMonster said:**
> "toys"?

Yes.

---

### Post by Cuddles McKitten on 2010-08-20
> **Bachstelze said:**
> Because there is no entreprise-class Linux distribution available for HP/PA (hence HP-UX), PowerPC (hence AIX) and Sparc (hence Solaris) machines.

Not everyone uses x86/x86-64 toys.

Ah, so it's mostly an architectural thing.  That was my top guess!
Looks like I get to mark an off-topic post as solved.

---

### Post by RiceMonster on 2010-08-20
> **Bachstelze said:**
> Yes.

Perhaps I should have been more specific. Could you please explain why you're reffering to x86 CPUs as toys?

---

### Post by Bachstelze on 2010-08-20
> **Cuddles McKitten said:**
> Ah, so it's mostly an architectural thing.  That was my top guess!

Of course.  No one in their right mind would run HP-UX or AIX on an x86.  Solaris is a bit different because of some features like ZFS, which make it better for some purposes than Linux (until btrfs), even on x86.

---

### Post by MCVenom on 2010-08-20
> **RiceMonster said:**
> Perhaps I should have been more specific. Could you please explain why you're reffering to x86 CPUs as toys?
This.

---

### Post by Cuddles McKitten on 2010-08-20
I think he was just making the point that server processors are very different from desktop CPUs.  Desktop CPUs are meant for (mostly) doing one thing at a time by one user.  You use them for fun little tasks like playing games or an exciting spreadsheet session.  Server CPUs, on the other hand are for many, many users doing a number of low-level tasks like reading from/writing to databases at the same time.  They're also expected to run at full tilt 24/7 for years.  As a result, they're held to a much higher standard.

---

### Post by RiceMonster on 2010-08-20
> **Cuddles McKitten said:**
> I think he was just making the point that server processors are very different from desktop CPUs.  Desktop CPUs are meant for (mostly) doing one thing at a time by one user.  You use them for fun little tasks like playing games or an exciting spreadsheet session.  Server CPUs, on the other hand are for many, many users doing a number of low-level tasks like reading from/writing to databases at the same time.  They're also expected to run at full tilt 24/7 for years.  As a result, they're held to a much higher standard.

The majority of servers use x86, and models that are designed specifically for servers.

---

### Post by Sporkman on 2010-08-20
Perhaps he is steamed over the success of the flawed CISC model of x86, as opposed to the market failure of technically superior RISC model of other processors.

---

### Post by koenn on 2010-08-20
Historically, x86 processors were developed for microcomputers, i.e. small, underpowerd computers for home use, so toys for hobbyists really. Real computing was done on real computers such as main frames, with smaller jobs done on minicomputers and workstations. That was the low end : Unix on mini's and "workstations" like the ones SUN used to make - x86 were toys for geeks.
Besides that, the design of the x86 chip was considered flaky and inferior, but cheap. Unix ran on other CPU's than that.

Micro-Soft (notice the micro in the name ?) started developing for these micros, and  eventually the PC became powerful enough to become serious competitor at the low end of computing. And the rest is history.



so I'd say Bachstelmse either knows his history, or is trolling us.
Or both, of course 
:)

---

### Post by Crishna on 2010-08-20
> **Cuddles McKitten said:**
> Can anyone direct me towards something that might explain why some organizations choose Solaris, AIX, HP-UX, etc. over Linux and the BSDs for production servers? I know almost nil about the non-free Unices and can't seem to find some site that explains the basic strengths (and weaknesses) of each of them -- especially from a business or organizational standpoint.
 
simple... i am working in a company, as a hp-ux system administrator, that has several SAP systems, with hundreads of servers in high availlability, clustering and disaster recovery plan, spread on 2 server site accross canada.
 
main reasons we took hp-ux is:
 
1> support 7/24 from HP onsite, response time less than 1 hour for critical issues.
2> Oracle is best performance on hp-ux boxes rather than linux.
3> Unix kernels can run 20 000 process without a sweat.
4> highly performance end hardware (HP san, EMC, Robot library)
5> support from the vendor as well
6> more profesional components, we never reboot servers.
7> most important, is that in our business, if we didnt chosed the hardware that the software recommand, we wont get support... we are controling specialized equipment, accros the canada, in different industries ( like automated robots, shipping, printer, plotters, etc...) in which most of them, can't be controled by linux, because linux doesnt have these special software, and the company didnt wanted to pay for a developper team to work on this... so it just easier to go on unix, and we get our problem resolved by 70 % of the time by automated process within HP... they look at our servers, and they tell us when a drive is about to die, or they tell us if our kernels are badly configured for certain specific task, you know, things like that!
 
so by them doing this, we can concentrate more on our clients, and doing some more application administration, access rights, rahter than getting preoccupied by hardware issues and backup maintenance....
 
the bad side of this, is it costs millions of dollars to the company for all of this...

---

### Post by mips on 2010-08-21
The main difference between UNIX vs. UNIX-like is certification. The rest of the arguments above kinda fly out of the window.

In order for you to brand your product as UNIX it has to be certified by [The Open Group]("http://en.wikipedia.org/wiki/The_Open_Group") to conform to the [Single UNIX Specification]("Single UNIX Specification") after which it will be registered with the group and you can call it UNIX. Then there's also POSIX compliance.

I suspect most BSD's and probably Linux's would meet the registration criterions BUT the problem is money. It costs vast sums of money to have the certification done. It's not a once off procedure either, you have to jump through the hoops for each new release you bring out so you keep on paying. This is money open source projects simply can't waste and will be better spent else where. If OS X can get UNIX certified then FreeBSD etc have just as good a chance at being certified if they are willing to pay the $$$'s

[http://www.opengroup.org/certification/unix-home.html](http://www.opengroup.org/certification/unix-home.html)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://www.freebsd.org/projects/c99/index.html](http://www.freebsd.org/projects/c99/index.html)
[http://www.freebsd.org/cgi/search.cgi?max=25&source=www&words=Single+UNIX+Specification+&submit=Search](http://www.freebsd.org/cgi/search.cgi?max=25&source=www&words=Single+UNIX+Specification+&submit=Search)

So if you had enough money to burn and brought a bit of code up to date you should be able to call BSD etc UNIX. Actually, BSD was called BSD UNIX back in the day when they still licensed AT&T code. The money however ran out, they dropped the AT&T code, rewrote new code but had to drop the UNIX part of the name. The interesting thing is AT&T continued using BSD code( BSD extensions) which included things like the network stack etc.

---

### Post by Blue Beard on 2010-08-21
> **Cuddles McKitten said:**
> Can anyone direct me towards something that might explain why some organizations choose Solaris, AIX, HP-UX, etc. over Linux and the BSDs for production servers?  I know almost nil about the non-free Unices and can't seem to find some site that explains the basic strengths (and weaknesses) of each of them -- especially from a business or organizational standpoint.
Organizations typically must comply with Stock Market Rules which require kyac.  Any of the 'free' alternatives do not guarantee this requirement.

---

### Post by phrostbyte on 2010-08-21
There are machines out there in the finance and insurance industry still chugging on COBOL code which was first written over 40-50 years ago. That's probably the same place you'll find such OSes. Legacy operating systems really.

---

### Post by earthpigg on 2010-08-21
Very informative post, Crishna. Thank you for sharing.

---

### Post by lisati on 2010-08-21
> **phrostbyte said:**
> There are machines out there in the finance and insurance industry still chugging on COBOL code which was first written over 40-50 years ago. That's probably the same place you'll find such OSes. Legacy operating systems really.

Ah, COBOL. I've used that on a course back in the 1980s, but never really used it in a production environment. Other than its verbosity, I didn't like the way the version my colleagues used didn't have a proper way to die gracefully when a user forgot to put in the necessary commands to associate a program's file streams with real files. As well as this, it didn't really suit the programming tasks I was originally hired to do.

---

### Post by RiceMonster on 2010-08-21
> **phrostbyte said:**
> There are machines out there in the finance and insurance industry still chugging on COBOL code which was first written over 40-50 years ago. That's probably the same place you'll find such OSes. Legacy operating systems really.

All that legacy COBOL code is not run on UNIX systems, but on zSeries mainframes running z/OS or somethimes AS/400s.

---

### Post by Sporkman on 2010-08-21
What are the obstacles to years-long uptime in linux vs the years-long uptime of Unix? Besides of course kernel upgrades & hardware failure...

I'd think graceful & sustainable handling of memory fragmentation and destabilization via segmentation faults/stack faults would have been tackled by now in linux...

---

### Post by LightningCrash on 2010-08-21
> **RiceMonster said:**
> Perhaps I should have been more specific. Could you please explain why you're reffering to x86 CPUs as toys?

SPARC can hotplug physical CPUs, can x86?


That is one of **many** reasons...

---

### Post by phrostbyte on 2010-08-21
> **RiceMonster said:**
> All that legacy COBOL code is not run on UNIX systems, but on zSeries mainframes running z/OS or somethimes AS/400s.

Uh, z/OS _is_ a proprietary Unix.

---

### Post by phrostbyte on 2010-08-21
> **Bachstelze said:**
> Because there is no entreprise-class Linux distribution available for HP/PA (hence HP-UX), PowerPC (hence AIX) and Sparc (hence Solaris) machines.

Not everyone uses x86/x86-64 toys.


Not withstanding the useless adjective "enterprise-class", RHEL does in fact run on POWER supercomputers, and IBM even sells the machines in that configuration.

---

### Post by LightningCrash on 2010-08-21
> **phrostbyte said:**
> Uh, z/OS _is_ a proprietary Unix.

z/OS supports some Unix APIs, but it is a derivative of os/390.

---

