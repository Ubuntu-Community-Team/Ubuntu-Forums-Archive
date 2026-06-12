---
title: "How to install NMIS on Hardy"
date: 2008-06-12
forum: Server Platforms
---

### Post by dre024 on 2008-06-12
Hi everyone,

I am new to Ubuntu. I am trying to install NMIS on Hardy. This task seems/is extremely difficult. I have read the installation instructions but since it’s command line driven, this is where I get lost. I have found some help on this but it way over my head. What I am trying to do with NMIS is monitor some firewalls and also use NMIS for syslogging purposes.  I know that I can use a windows based app to do this for me. However, my goal is to be able to use Linux. Any help/guidance is greatly appreciated. 

Thanks,
Dre

---

### Post by ajmorris on 2008-06-13
hi there,
i have never looked into NMIS, but, what is the issue you are having? is it actually compiling and installing it, or is it the running of the application itself?

AJ

---

### Post by dre024 on 2008-06-16
Hi AJ,

Well - it's actually all. I am following the installation notes from [http://sins.com.au/nmis/](http://sins.com.au/nmis/) and although it's done in RH, I assumed that it should work with Ubuntu. I have never done any sort of installation on ubuntu that would require using the shell, I have used the synaptic package manager to install apps. This is over my head but I want to learn how to do installations. 

Many thanks

---

### Post by bodhi.zazen on 2008-06-17
NMIS looks somewhat complicated to install, but not too bad. I have no idea if it works on Ubuntu but I do not see any obvious issue.

Detailed instructions are here :

[http://nmis.mric.net/nmis-install.html](http://nmis.mric.net/nmis-install.html)

Other then that you will need to be more specific. What step are you having problems with exactly ?

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by dre024 on 2008-06-18
When I type  ./configure all seems well. It's when I do the "make" command that I get the following info.

CONFIG_FILES="" CONFIG_HEADERS=config.h ./config.status
creating config.h
config.h is unchanged
date > stamp-h
gcc -c  -DHAVE_CONFIG_H -I. -I. -O alloc.c
In file included from alloc.c:5:
sh.h:18:19: error: stdio.h: No such file or directory
sh.h:19:23: error: sys/types.h: No such file or directory
sh.h:20:20: error: setjmp.h: No such file or directory
In file included from alloc.c:5:
sh.h:33: warning: conflicting types for built-in function â&#8364;&#732;exitâ&#8364;&#8482;
sh.h:82:22: error: strings.h: No such file or directory
sh.h:118:19: error: errno.h: No such file or directory
sh.h:124:23: error: sys/file.h: No such file or directory
sh.h:156:20: error: signal.h: No such file or directory
sh.h:254:5: error: #error cannot find 32 bit type...
In file included from alloc.c:5:
sh.h:351: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;Tflagâ&#8364;&#8482;
sh.h:417: error: expected specifier-qualifier-list before â&#8364;&#732;jmp_bufâ&#8364;&#8482;
sh.h:670: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;Coproc_idâ&#8364;&#8482;
sh.h:675: error: expected specifier-qualifier-list before â&#8364;&#732;Coproc_idâ&#8364;&#8482;
sh.h:691: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;builtin_flagâ&#8364;&#8482;
In file included from sh.h:733,
                 from alloc.c:5:
table.h:14: error: expected specifier-qualifier-list before â&#8364;&#732;Tflagâ&#8364;&#8482;
In file included from sh.h:737,
                 from alloc.c:5:
proto.h:265: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;Tflagâ&#8364;&#8482;
proto.h:265: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;Tflagâ&#8364;&#8482;
alloc.c: In function â&#8364;&#732;aresizeâ&#8364;&#8482;:
alloc.c:391: warning: incompatible implicit declaration of built-in function â&#8364;&#732;bcopyâ&#8364;&#8482;
make: *** [alloc.o] Error 1

I don't know what to make of this.  I have been using the instructions from the first link you provided. I hope this is clear for you, if not please let me know. 

Thanks. 
Dre

---

### Post by bodhi.zazen on 2008-06-18
First, install as much as you can from the Ubuntu repositories. No need to compile everything from source unless it is not in the repositories.

Second, please, what package are you trying to compile? Most errors occur due to unmet dependencies. If a package is listed as a dependency that almost always means you need the -dev package.

Third, do you know how to compile from source ? did you install build-essential ? do you know how to use checkinstall ???

---

### Post by dre024 on 2008-06-18
I am trying to compile (then again don't know if that's what I am trying to do) pdksh-5.2.14, rrdtool-1.2.27 and snmp_sessioin-1.12. I don't know what -dev package is and I have no clue how to compile from source, it's just what I have been reading on the net. Never heard of install build-essential or checkinstall. Sorry, but this is all new to me.

---

### Post by bodhi.zazen on 2008-06-19
Sorry for the long delay. To be honest, this is then a large project and you do not have the knowledge.

It is not impossible, it is just that you will need to do a fair amount of reading is all.

First, is there not an alternate solution, one that does not require you to install applications outside the ubuntu repositories ?

Second start here :

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

Then for a how to compile :

[http://ubuntuforums.org/showpost.php?p=67109&postcount=6](http://ubuntuforums.org/showpost.php?p=67109&postcount=6)

OK, so now, start by installing as much as possible from the ubuntu repositories.

If something is not in the repositories you will need to install the dependencies as well, so 

pdksh does not appear in the repositories, what else needs to be installed, what are the dependencies ? Install those first ...

[http://freshmeat.net/projects/pdksh/](http://freshmeat.net/projects/pdksh/)

Ok, no dependencies, try installing it, and on down the line.

---

### Post by dre024 on 2008-06-19
Thanks for taking the time. I will see what I can do from here. I will read the links you have provided. Once I get this thing going, I will let you know. Thanks again!

---

