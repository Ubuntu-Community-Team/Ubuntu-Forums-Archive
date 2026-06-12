---
title: "Windows Powershell"
date: 2009-09-20
forum: The Cafe
---

### Post by tlarkin on 2009-09-20
So,

On my Vista box I just downloaded the new (new to me as I am just now dabbling with it) Windows PowerShell add on.  It basically adds a bunch of command line binaries for more robust command line work.  A lot of Unix-like binaries are present (ls, echo, pwd, rm, and so forth) and from what I have read you can develop with it.  Scripts for automation and so forth.

Has anyone tried any of the powershell stuff out?  Here is a link to the main site:

[http://www.microsoft.com/windowsserver2003/technologies/management/powershell/default.mspx](http://www.microsoft.com/windowsserver2003/technologies/management/powershell/default.mspx)


I am curious as to how well the powershell works with non Microsoft systems, as I would love to start integrating Windows scripts that could talk and be robust enough with some Linux servers. 

Sounds interesting to me.

Thoughts?

---

### Post by jrusso2 on 2009-09-20
Pretty sure its Windows only.

---

### Post by tlarkin on 2009-09-20
> **jrusso2 said:**
> Pretty sure its Windows only.

Oh, it is totally 100% Windows only, but it is Microsoft's answer to a lousy command line binary system, which Linux/Unix has.  For example, if I wrote log in hook shell scripts for my Macs/Linux boxes that would search for strings of information and then update a database for a specific task, I could write scripts for that.

I would like to write powershell scripts to do the same thing and update that same database on the Windows side.

I am just asking if anyone has developed for powershell yet, and if so what do they think about it is all.

Sorry, guess I should have been more clear.

---

### Post by toupeiro on 2009-09-21
Windows powershell is basically a CLI frontend to .NET framework.

Those unix-like binaries that were referenced are not binaries at all.  Their aliases, or as Microsoft calls them, cmdlets...  they are shortcuts to Powershell commands that have a common UNIX equivalent function, which is why they provide them by default.  I have several custom defined cmdlets in my powershell environment.  Powershell is very powerful.  One of the great things about it is powershell's ability to interpret other shell environments and languages, including bash, korn, java, and perl.  It is a microsoft-only environment, and if you work and support microsoft environments, I recommend getting very familiar with it, as it will save you tons of work!

I've done some pretty amazing things with DOS batch, vbs and wmi, so I would hardly call Microsofts OS commandline power lousy.  Cryptic, maybe, but not lousy.  Powershell did, however, make it more intuitive, less limiting, and .. for lack of a better description, more UNIX-like.  Its a great step for them.

The middle-ground for integrating powershell for linux is virtualizing.  If you are running something like ESXi, with a vCenter, then you can run powershell scripts against the vCenter to get, and manipulate information in your virtual environments.  Even, your linux ones!  In fact, VMWare offers a free powershell API which you can download off of their site.

---

### Post by purgatori on 2009-09-21
I gave it a shot awhile back and found it extremely lacking. It has a fraction of the functionality of the Unix console.

---

### Post by juancarlospaco on 2009-09-21
Windows CLI is not user friendly or easy to use...

---

### Post by cunawarit on 2009-09-21
I've used it, but admittedly I haven't given it a serious go due to lack of time... But I'll do so sometime.

Right now I use it in conjunction with Bash (Running on Cygwin), so I create Bash scripts that run PowerShell scripts occasionally when need be. 

Given my limited experience I find it hard to give it my full endorsement, but certainly interesting and gives more options to Windows users. 

As for using it on a non-Windows system, there's PASH: [http://pash.sourceforge.net/](http://pash.sourceforge.net/) . I have no idea at all how good it is.

---

### Post by &#32 Greg on 2009-09-21
It's basically C# over a REPL. That makes it great for anyone who already knows how to code C#, makes it pretty powerful, but also means that it's more a programming language than a shell. While the UNIX shells rely on the less advanced method of parsing, Powershell passes objects. The UNIX method is far easier when it comes to every day use, but where the core use of Powershell is, it's closer to say python's in the *nix community.

---

### Post by szymon_g on 2009-09-21
/me is curious how does it look compared to python

does python have any bindings with .NET framework?

---

### Post by tlarkin on 2009-09-21
Thanks for the replies...

I am working on a few web based applications for my job (I am an OS X Administrator) and most of them are using bash under the hood to get the job done.  We also have several thousand windows clients as well which I would like to accomplish some of the same things and saw powershell and thought I'd give it a go.

I am not a programmer though, but I can write scripts in shell and perl.

---

