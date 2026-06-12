---
title: "HOW TO install through .rpm files ?"
date: 2009-06-04
forum: Tips &amp; Tutorials Team
---

### Post by aravindc26 on 2009-06-04
[CENTER][SIZE=6][COLOR=Navy]HOW TO install applications through .rpm file
[/COLOR][/SIZE][LEFT][SIZE=6]
[/SIZE][SIZE=3]I know this is a very simple ***[COLOR=Red]how to[/COLOR] ***but for beginers its daunting task to find how to install through .rpm file for a beginer, so experts this is not your place.
[/SIZE] [SIZE=3]
***What is [COLOR=Red]_.rpm_[/COLOR] file ?***

[/SIZE]  [SIZE=3]**RPM Package Manager** is a ***[COLOR=Red]package management system[/COLOR]***. The name RPM refers to two things: a software package file format, and software packaged in this format. RPM was intended primarily for Linux distributions; the file format *RPM* is the baseline package format of the Linux Standard Base.
[/SIZE]  [SIZE=3]Originally developed by Red Hat for Red Hat Linux, RPM is now used by many Linux distributions. It has also been ported to some other operating systems, such as Novell NetWare (as of version 6.5 SP3) and IBM's AIX as of version 4.
[/SIZE]  [SIZE=3]RPM stands for "[COLOR=Red]***RPM Package Manage***r[/COLOR]," which is a recursive acronym. (***[COLOR=Red]Source[/COLOR]***: [***Wikipedia***]("http://en.wikipedia.org/wiki/RPM_Package_Manager"))




***[B]Advantages and disadvantages of the format :***[/B]


[/SIZE]        [SIZE=3]Package managers have many advantages over relying on manual installation such as:
[/SIZE]  
[LIST]
[*][SIZE=3]They present a uniform, clean way for users to install and remove programs with a single command.[/SIZE]
[*][SIZE=3]There are many popular interfaces, both command-line and graphical.[/SIZE]
[*][SIZE=3]Non-interactive installation makes it easy to automate.[/SIZE]
[/LIST]
 [SIZE=3]RPM also has a few advantages over some other package managers:
[/SIZE]  
[LIST]
[*][SIZE=3]It is the Linux (LSB) standard format.[/SIZE]
[*][SIZE=3]It is popular: the typical rpm repository (the place where the packages are made available publicly) contains thousands of free applications.[/SIZE]
[*][SIZE=3]RPM packages can be cryptographically verified with GPG and MD5[/SIZE]
[*][SIZE=3]Original source archive (e.g. .tar.gz, .tar.bz2) are included in SRPMs, making verification easier (for security-critical packages like OpenSSH it is possible to check with md5sum that the sources were not modified).[/SIZE]
[*][SIZE=3]DeltaRPMs, the RPM equivalent of a patch file, can incrementally update RPM-installed software without needing the original package.[/SIZE]
[/LIST]
[SIZE=3]
***So how to install using .rpm file ?***

[/SIZE]   [SIZE=3]To install .rpm files we need an other application called [COLOR=Red]***alien***[/COLOR]. [/SIZE][SIZE=3]You can ***[COLOR=Red]alien  [/COLOR]***Using the Terminal, for that go through **Applications &#8594; Accessories  &#8594; Terminal** and type the following code in the terminal :

```
sudo apt-get install alien
```**[COLOR=Red]OR [/COLOR]**you can use synaptic packet manager to download and install alien, for that go through **System  &#8594; Administration &#8594; Synaptic Packet Manager**, press ***ctrl+f*** and type [/SIZE]  [SIZE=3][COLOR=Red]***alien***[/COLOR][/SIZE][SIZE=3] in the search box and hit enter. When you see the results tick the check box where you see[/SIZE][SIZE=3][COLOR=Red] ***alien***[/COLOR][/SIZE][SIZE=3] and click apply and exit **Synaptic Packet Manager.**

Now I want to install  RealPlayer11GOLD from [RealPlayer11GOLD.rpm]("http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.rpm") (<--- Click  to download RealPlayer11GOLD.rpm). Here is the method:

open the **Terminal**,  [B]Applications &#8594; Accessories  &#8594; Terminal.
[/B] if downloaded the the .rpm file in Desktop type the following code (after each line hit enter) : 
```
cd ~/Desktop
sudo alien RealPlayer11GOLD.rpm

```The purpose of this command is to convert .rpm file to .deb file. You will notice a new file will be created in the Desktop.

Now the final step of the installation just double click the .deb file , you will notice that a window pops out click install package ***or ***type the following code in the **Terminal.** ```
sudo dpkg -i RealPlayer11GOLD.deb
```***[COLOR=Indigo]Mission accomplished:KS[/COLOR]***




[/SIZE]        [SIZE=3]



[/SIZE]
[/LEFT]
[/CENTER]

---

### Post by frodon on 2009-06-04
When i saw "Advantages and disadvantages of the format" i thought it would be mentioned at least one of the known disadvantages of this method.
Presented like this it is not clear at all why installing from RPM files is not recommended.

Anyway this information is already on the forum so i would reject this one.

Opinion ?

---

### Post by cariboo on 2009-06-04
+1, it needs some work, like you say it doesn't state any of the disadvantages of .rpm, like dependency hell. :)

---

### Post by frodon on 2009-06-05
Thanks,

User PMed and tutorial rejected.

---

