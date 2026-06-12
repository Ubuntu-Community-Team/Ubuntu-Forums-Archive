---
title: "Question about command line commands"
date: 2011-08-13
forum: The Cafe
---

### Post by skytreader on 2011-08-13
Well, not really a help question so I decided to take this to the Community Cafe...here goes...

Are command line commands Lunix (Linux/Unix) standard? Like, will sudo apt-get install x work in, say, Red Hat provided that RH has a package repo and that x is a package in RH*?

Or are they shell-dependent? Like, I can create my own shell, but finds the sound of "sudo" awkward so I have a command "pika" instead which does everything sudo does.

*Okay, so I've really never tried RH so pardon me if this sounds nonsense.

---

### Post by vehemoth on 2011-08-14
I think the shell is actually comprised of a set of applications, so long as the other distros have all the programs then the commands will work.
However some have different programs to do the same things such as yum instead of apt in redhat.

---

### Post by cariboo on 2011-08-14
Redhat is based on rpm, so apt-get won't work, although PCLOS also uses rpm, but also uses apt and synpatic.

Otherwise, except for package management, the basic commands are the same for almost all distributions.

---

### Post by whatthefunk on 2011-08-14
A lot of commands are standard.  cp, mkdir, mv etc. will probably be found in most distros.  However, as vehemoth said, commands are actually programs so it depends on what you have installed on your system.  Not all distros use the aptitude/apt-get programs so trying to run apt-get on another distro might not work.  Same with sudo.  Sudo is not a universal Linux program.

---

### Post by kaldor on 2011-08-14
Think of the commands as text-based applications instead of codes/commands.

---

### Post by Bachstelze on 2011-08-14
You need to differentiate between two things: commands that are built into the shell (also called "builtins") and commands that run external programs. For a builtin to work, you just need to install (and use) the shell in question. For a command that runs an external program to work, you must install any shell, plus the program in question. Both apt-get and sudo are external programs, so in order to use them you must install a shell of your choice, plus the programs apt-get or sudo. In Ubuntu, both are installed by default.

To be able to use a command (be it a builtin or an external program) under another name, you can use an alias, most if not all shells suport this. For an external program, you can also just rename the executable...

---

