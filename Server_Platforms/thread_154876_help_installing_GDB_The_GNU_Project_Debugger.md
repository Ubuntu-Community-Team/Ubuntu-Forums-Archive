---
title: "help installing GDB: The GNU Project Debugger"
date: 2006-04-04
forum: Server Platforms
---

### Post by wgregori on 2006-04-04
I've been requested to run gdb and capture some debugging information regarding a mailserver that I'm running Ubuntu but I can't figure out how to install gdb.  I've ftped the package from GNU but I've never installed a package without using apt-get. Any help would be appreciated.




Thanks,
Wayne Gregori

---

### Post by karthik085 on 2006-04-04
I believe gdb as a debs package is in the respository. If you want to compile from source, you can read the installation instructions more on GNU's GDB project page. Search online too.

---

### Post by wgregori on 2006-04-04
[QUOTE=karthik085]I believe gdb as a debs package is in the respository. If you want to compile from source, you can read the installation instructions more on GNU's GDB project page. Search online too.[/QUOTE]

Thank you for the reply. Although i've made huge strides with Ubuntu server there are still some rather large holes in my Linux knowledge.

When you say "in the repository" are speaking at the Debian repository or the GNU?  I've gone to the GNU site and the file that I grabbed is  gdb-6.4.tar.gz.  Would that have the debs package?... is there a particular file extention that I'm looking for.  Sorry to be so....???? 

Wayne

---

### Post by karthik085 on 2006-04-04
apt-cache search gdb gives me:
evolution-data-server-dbg - evolution database backend server
evolution-dbg - The groupware suite
gdb - The GNU Debugger
.
.
.
and so on.

If this does not list gdb on your computer, check my sources.list
It has links to universe, multiverse respository, etc. You may have to update your /etc/apt/sources.list. (Also, you can ignore anything after DeCSS in my list, as it may not be useful to you)

to install:
sudo apt-get install gdb

You may be able to do this with synaptic and Software Porperties (System->Administration)

Files you grabbed from GNU website are probably sources files. 
You probably don't need that, unless you want to install from source.
If you want to install a debian package, it ends with .deb

[QUOTE=wgregori]Thank you for the reply. Although i've made huge strides with Ubuntu server there are still some rather large holes in my Linux knowledge.

When you say "in the repository" are speaking at the Debian repository or the GNU?  I've gone to the GNU site and the file that I grabbed is  gdb-6.4.tar.gz.  Would that have the debs package?... is there a particular file extention that I'm looking for.  Sorry to be so....???? 

Wayne[/QUOTE]

---

### Post by wgregori on 2006-04-05
Thank you so much karthik,

That worked... I have two questions that I'm sure many people have:

1) I copied your sources.list to my system and then did an apt-get update to update my database of applications.  Do you maintain your own sources.list?  How do you find out about new sources?

2) I found the gdb package on the Debian site.  If I wanted to load it (gdb_6.3-6_i386.deb) what command would I use?

Thanks again,
Wayne

---

### Post by karthik085 on 2006-04-05
1. Just by reading what other people have posted their sources.list on forums, online, wiki, etc.
If you are a beginner, you should read ubuntu starter guide. It will solve many of your problems.

2. sudo dpkg -i <Package Names>

---

