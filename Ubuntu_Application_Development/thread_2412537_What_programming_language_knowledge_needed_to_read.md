---
title: "What programming language knowledge needed to read most Ubuntu OS source code, ..."
date: 2019-02-14
forum: Ubuntu Application Development
---

### Post by lsepolis123 on 2019-02-14
I am Web Programmer[JS/PHP/HTML5/CSS3] with Linux/Python/C skills
May soon develop for Ubuntu but firstly I want try read code of FOSS for Linux/Ubuntu

What programming language knowledge needed to read most Ubuntu OS source code, and different FOSS like Gimp, Inkscape, Firefox, etc programs included in Ubuntu & Ubuntu Studio ???

eg mastering Linux & Shell-Scripting/C/C++/Python/Qt
I will be able read almost 98% of code of FOSS... and Ubuntu OS Source code itself?

---

### Post by TheFu on 2019-02-14
Every project selects their own tool-chain.  Which languages you need to know is completely dependent on the project you want to delve deeper into.

The kernel is C.
Most of the user commands we use in a shell are C, but some are other scripts and bash.
Qt has bindings available for many different languages. Same for GTK - could be C, C++, Python, Perl, Ruby, or a higher-level language that is a wrapper about GTK.

Don't get hung up on "ubuntu" or "ubuntu studio" - those are just specific combinations of programs that someone decided fit well together.  You can remove, replace, or add any other programs you like.  Ubuntu isn't like OSX or Windows. There are thousands of different teams building their project, which usually creates a few programs.

If you'd like more of an explanation for how F/LOSS works and Linux in specific, [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) might be helpful.  If you are really new to Linux, then this way of working might be surprising.

---

### Post by lsepolis123 on 2019-02-15
Can you say this?
if you are advanced user in C/C++/Python/Java/Perl/Shell-Scripting/PHP[as well Linux general knowledge] you can read Linux kernel source code [C] as well as most Linux FOSS because mostly are of these languages made... Approx. about ..... % of software [FOSS INCLUDED IN UBUNTU STUDIO AS AN EXAMPLE] are made using these languages??? [complete the %]

What is GTK ... ?

---

### Post by lsepolis123 on 2019-02-15
I aim as Linux become more familiar to me, to read most Linux FOSS generally [for adv my Linux & programming skills] ... at least in my studying/studied languages [COLOR=#000000]C/C++/Python/Java/Perl/Shell-Scripting/PHP...[/COLOR]

---

### Post by TheFu on 2019-02-19
> **lsepolis123 said:**
> Can you say this?
if you are advanced user in C/C++/Python/Java/Perl/Shell-Scripting/PHP[as well Linux general knowledge] you can read Linux kernel source code [C] as well as most Linux FOSS because mostly are of these languages made... Approx. about ..... % of software [FOSS INCLUDED IN UBUNTU STUDIO AS AN EXAMPLE] are made using these languages??? [complete the %]

What is GTK ... ?

2 major F/LOSS toolkits are GTK and Qt.  Gnome uses GTK and KDE uses Qt.  Different project teams will select the toolchain to be used in their different programs. If they are careful, it will be a minimal set. If they aren't, the project might end up with 50 different external dependencies and a mess.

Java and php devs might also have trouble, because of their training that the hardware isn't important.  Languages that stay far from hardware considerations, teach a different level of programming than C. If you want to read AND understand kernel code, then become an expert in C. Just my opinion from 25 yrs.

Lots of legwork will be needed to determine which languages are used by each project for a specific release.  If that interests you, start by making a list of all the installed packages (dpkg -l), then look up each project website (gitlab, github, gnu.org, gnome.org, kde.org, et al) and work your way through the 2,000+ packages, one at a time, keeping track of the different languages used.  Many will use multiple languages and tools, like lexx, yacc, bison, flex, along with the main languages. Some will be in languages you may never have heard of.

---

### Post by appsdevelop on 2019-11-29
Ubuntu can be coded with dotnet for more features, java will be best part as of now this app is developed with php.

---

