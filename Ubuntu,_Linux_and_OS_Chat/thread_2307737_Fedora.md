---
title: "Fedora"
date: 2015-12-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Sigord on 2015-12-28
Please is what appears to be the massive Fedora already installed in Ubunto? If not what is the URL to safely install the 32 bit version?

---

### Post by QIII on 2015-12-28
*Moved to **Ubuntu, Linux and OS Chat***

Fedora is a Linux Distribution -- a completely different OS -- that is distinct from Ubuntu.

So you cannot install it in Ubuntu.

You may wish to view their website [here]("https://getfedora.org/").

---

### Post by Sigord on 2015-12-28
Thnaks. So it is a Windows software. Someone is confusing me claiming he used it run code of [http://www.bbcbasic.co.uk/bbcbasic.html](http://www.bbcbasic.co.uk/bbcbasic.html) to create software for a Linux such as Ubuntu/

Gordon

I'm using SDL (actually SDL2) as I've said.  On Fedora I found that it
was installed by default, but on the others I had to install it before
BBC BASIC
would run:

  [https://en.wikipedia.org/wiki/Simple_DirectMedia_Layer]("wlmailhtml:%7bAAE4883F-D51D-40DB-BBD4-CD9FBDE454DF%7dmid://00000000/!x-usc:https://en.wikipedia.org/wiki/Simple_DirectMedia_Layer")

It was SDL that turned porting BBC BASIC from a major task, that would
probably have taken months, into something I was able to do in about
three weeks.  It has its limitations, but it's simple (as its name implies).

---

### Post by QIII on 2015-12-28
No.  Fedora is a completely different OS from Windows as well.  It cannot be installed in Windows.  Whoever you are talking about may be using some development environment on a machine running the OS called Fedora to develop some software.

I must admit to some confusion myself with regard to what you are trying to say here.

---

### Post by lisati on 2015-12-28
I have no idea what the equivalent is if you're using Fedora, but there is an Ubuntu-friendly BASIC compiler called "FREEBASIC" available in the software centre. No need to mess around with SDL. There's also a BBC Basic interpreter available through the software centre as well.

---

### Post by Sigord on 2015-12-28
Thanks again. If I am allowed to mention it here I havealready developed FreeBasic versions of some of my Freeware as at [http://www.sigord.co.uk/SubmitsLinux/LinuxSoftware.htm]("http://www.sigord.co.uk/SubmitsLinux/LinuxSoftware.htm") for Ubuntu and Mint
But unlike BBC Basic for Windows FB cannot even produce hardly anysounds apart from playing such as MP3 / MID files. Also BBC4W has many moreeasy to use useful functions. So it would be nice if like FB I could easily createBBC4W versions to run under Ubuntu etc. Even with FB I have to resort to using [http://fbc.deltalabs.de/]("http://fbc.deltalabs.de/") rather that riskinserting loads of UNIX code in Ubuntu.
Gordon

---

### Post by lisati on 2015-12-28
Just to clarify, which OS are you running. Fedora or Ubuntu? Have you checked the version of the BBC Basic interpreter for Ubuntu?

By the way, Ubuntu is based on Linux, not Unix.

---

### Post by Sigord on 2015-12-28
I have not tried using BBC4W code in anything new yet. It seems those on the BBC4W forum are using Fedora, but I understand Fedora is massive to install or how that helps running BBC4W code with Ubuntu.

---

### Post by buzzingrobot on 2015-12-28
Sigord, Fedora is another Linux distribution. You would install it to replace your current OS or set up a dual boot environment.

BBC Basic is a programming language created 30+ years ago for the 6502-based Acorn BBC Micro computer that was on the market then, primarily in the UK.

I don't see any BBCBasic package in the Fedora repos.  It might be available from a third party.  

SDL is a "cross-platform multimedia library", so it's conceivable it's used by developers working with BBCBasic on Linux, however they do that. And it is part of a standard Fedora install. "sdlbasic" is in the Ubuntu repos tagged as a "BASIC interpreter for game development".

---

### Post by The Cog on 2015-12-28
According to the web page linked in #3, "BBC BASIC For Windows" is for Windows.
Both Ubuntu and Fedora are versions of Linux, not Windows. 
The web site does mention Brandy Basic which seems to be for many  *nix type OSs, including Linux.
There is a package called brandy in the Ubuntu repositories, which has the following description:
> Brandy is an interpreter for BBC Basic. It is source code compatible with the
BASIC V interpreter in RISC OS and runs under a number of different
operating systems.
Note that it is not possible to make operating system calls from within a
program except under RISC OS..

---

