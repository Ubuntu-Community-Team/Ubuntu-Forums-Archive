---
title: "We are all indebted to Unix"
date: 2007-06-23
forum: The Cafe
---

### Post by ess0 on 2007-06-23
When asked about the *technical* advantages of Linux, many of its users will quickly point out that it offers a secure and stable platform for computation to take place. Personally, I certainly agree; I use Debian myself as a server to store my backup files, and it is perhaps the most reliable system I have had the pleasure to use.

What I wish to emphasize, however, is the *reason* that Linux has these technical advantages. Though it is extremely likely that users of Linux already know the origin of many of Linux's design philosophies, perhaps they have not thought about the importance and great effect the influences of Linux have had on its development.

The reason is Unix.

Linux, in fact, *inherited* the security of Unix, just as it inherited the multiuser interface, its emphasis on text files, its infrastructure, its core and its foundation. When we think of the elegance and simplicity of Linux, we what we are really thinking of is the design and ideas of a predecessor, a predecessor which implemented these ideas at a full scale before the Linux kernel ever reached its infancy, and a predecessor which undoubtedly inspired and lead to the growth of many open source operating systems today. The sheer influence that Unix has on Linux leads to a great irony: the GNU project, an organization which heavily advocates the development of free software, was heavily inspired by a proprietary operating system (Unix) when it developed many of the core utilities that are required by Linux in order to operate.

Let us consider this with greater depth. Many users of Linux use essential utilities like bash, gcc, make, and various text editors (such as Vim and GNU Emacs) on a regular basis. The next time you make use of these applications, however, I would like you to consider *what* inspired the creation of these applications. Each one of these applications do have a predecessor (in manner very similar to that of Linux), a predecessor that of course *ran on Unix*. sh, cc, make, vi, and emacs **all** were designed and written before the GNU project was even conceived, and the X Window System once ran on Unix long before the formation of X.org even took place.

It is of course quite acceptable to discuss the ingeniousness of the design of Linux to a friend or a colleague; but one should never forget the origin of these ideas, or the operating system that undoubtedly contributed significantly to birth of open source computer operating environments as we know them today. Indeed, we have in recent years added to the core functionality that Unix once provided, but in order to discover the origins of the true technical philosophies of Linux, we are forced to look further into the past...

---

### Post by jrusso2 on 2007-06-23
I have heard talks by Richard M Stallman about the reasons why they went with the Unix model.  It was the most portable operating system and they wanted an OS that would run on a lot of different platforms was his explanation.

It was also well proven and reliable.  The effort required to write a completely new operating system according to Stallman would have doubled the development time and in his mind it would have been obsolete before it was completed was the explanation he gave.

On the other hand if it was not for Unix's high cost and licensing issues we would not have had to develop gnu/linux

---

### Post by SunnyRabbiera on 2007-06-23
Oh yes, unix was a big gift to computer programmers.
However as jrusso2 pointed out its because of Unix's costs that we got linux.

---

### Post by blah blah blah on 2007-06-23
I disagree unix sucks. It started out okay but then it turned into crap.

---

### Post by darkog on 2007-06-23
I personally think we go GNU/Linux because of the personal computer revolution. Back in the day, based on things I have read (obviously I wasn't there) -- the AT&T's and IBM's didn't really think that everyone was going to one day have a personal computer *in their house*. 

When that did happen, quite a few people wanted to open it all up and play with it -- but the Apple's and the Microsoftie's weren't really interested in letting that happen back then -- so, what a computer hobbyist had to do was find a way to work on his hobby.

---

### Post by blah blah blah on 2007-06-23
> **darkog said:**
> I personally think we go GNU/Linux because of the personal computer revolution. Back in the day, based on things I have read (obviously I wasn't there) -- the AT&T's and IBM's didn't really think that everyone was going to one day have a personal computer *in their house*. 

When that did happen, quite a few people wanted to open it all up and play with it -- but the Apple's and the Microsoftie's weren't really interested in letting that happen back then -- so, what a computer hobbyist had to do was find a way to work on his hobby.

That's not true.
> **ess0 said:**
> ....of course *ran on Unix*. sh, cc, make, vi, and emacs **all** were designed and written before the GNU project was even conceived...
I can't believe I missed that, that's totally untrue.

---

### Post by arvevans on 2007-06-23
As an ex AT&T Bell Labs employee, I can say that "I was there" and may be able to shed a little more light on how this evolved.

[INDENT]When the UNIX system came into common use at Bell and at many universities, the computing platforms required to run it included things like PDP-11/70, VAX-7800, and other multi-rackmount processing engines.  At that time commonly available home computer hardware included TRS-80's Radio Shack Coco, and the early Apple 6502 based machines.  There just was not enough power there to even consider running a UNIX system on home based hardware.

In the first part of the 1980's an effort was made to capture the essence of UNIX in a standards document.  This became known as the POSIX standards.  Many persons took that as a guideline for writing shell interpreters and shell scripts that ran on then available mini-versions of the UNIX kernel.  Minix was the dominant one of these, but there were also shell interpreters and shell commands written for CP/M, PC-DOS, and so forth.  

By the mid-1980's Berkley Unix was becoming available at reasonable prices but still required heavy hardware to run it effectively.  AT&T had started building the first almost-desktop computers that ran UNIX on a 68020 processor.  SCO came out with Zenix for the IBM PC, and Apple's Macintosh had a kernel and scripting language that was almost POSIX compliant.  Apple's system included a graphical user interface and a mouse.

The Linux kernel, and later addition of shell interpreter, shell commands and X-windowing came along several years later.

I suspect that the POSIX document has contributed immensely to development of modern day operating systems, including LINUX, because it provides a set of how-to guidelines for interfacing between a multi-tasking kernel and rudimentary command interpreters, and shows what these commands should do, and how they should do it.

X-windows came out of an MIT group in the early to mid 1980's almost in parallel with windowing system development at Xerox's PARC.  It appears that the PARC effort went on to become the Apple graphical user interface on their Macintosh and on it's short-lived Lisa predecessor.  The mouse that we use for today's window navigation came out of PARC at about the same time.
[/INDENT]

OK.  That is how I remember it, but I'm getting old and admittedly some details are just not worth remembering any more.  It doesn't pay to look back, because something might be gaining on you!  ;)
_._

---

### Post by arvevans on 2007-06-23
[I][INDENT]Quote:
Originally Posted by ess0 View Post
....of course ran on Unix. sh, cc, make, vi, and emacs all were designed and written before the GNU project was even conceived...
I can't believe I missed that, that's totally untrue.[/INDENT][/I]


It is true.  I was using almost all of today's Linux based CLI commands on SVR3 UNIX at Bell Labs in 1982, including all those listed in the above quote.  They have changed little in all these years...probably attesting to their well thought out design.
_._

---

### Post by blah blah blah on 2007-06-23
> **arvevans@earthlink.net said:**
> [I][INDENT]Quote:
Originally Posted by ess0 View Post
....of course ran on Unix. sh, cc, make, vi, and emacs all were designed and written before the GNU project was even conceived...
I can't believe I missed that, that's totally untrue.[/INDENT][/I]


It is true.  I was using almost all of today's Linux based CLI commands on SVR3 UNIX at Bell Labs in 1982, including all those listed in the above quote.  They have changed little in all these years...probably attesting to their well thought out design.
_._

No it's not.

---

### Post by saulgoode on 2007-06-24
> **lKyPN8xZQG said:**
> No it's not.

You are wrong.

---

### Post by blah blah blah on 2007-06-24
> **saulgoode said:**
> You are wrong.

What? did rms go back in time just to make emacs?

---

### Post by saulgoode on 2007-06-24
> **lKyPN8xZQG said:**
> What? did rms go back in time just to make emacs?

RMS wrote Emacs while working for MITLABs. He conceived of the GNU Project after years of working on Emacs.

---

### Post by blah blah blah on 2007-06-24
> **saulgoode said:**
> RMS wrote Emacs while working for MITLABs. He conceived of the GNU Project after years of working on Emacs.

I just checked, you are right.

---

### Post by arvevans on 2007-06-24
[INDENT][I]
Quote:
Originally Posted by saulgoode View Post
RMS wrote Emacs while working for MITLABs. He conceived of the GNU Project after years of working on Emacs.
I just checked, you are right.[/I][/INDENT]

Apology accepted.  ;)
_._

---

### Post by matthew on 2007-06-24
> **lKyPN8xZQG said:**
> I disagree unix sucks. It started out okay but then it turned into crap.No reasoning stated. No supporting evidence. I call troll.

> **arvevans@earthlink.net said:**
> As an ex AT&T Bell Labs employee, I can say that "I was there" and may be able to shed a little more light on how this evolved.
Thank you for a couple of interesting and informative posts!

---

### Post by darkog on 2007-06-24
yup. thanks arvevans. you took a potentially downward spiraling thread and turned it into a very interesting one.

---

### Post by mips on 2007-06-25
> **matthew said:**
> No reasoning stated. No supporting evidence. I call troll.


Troll +1 and I have the proof ;)  [http://ubuntuforums.org/showthread.php?t=480063](http://ubuntuforums.org/showthread.php?t=480063)

---

