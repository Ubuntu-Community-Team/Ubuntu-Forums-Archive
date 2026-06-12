---
title: "I feel lost in the file hierarchy"
date: 2013-02-06
forum: The Cafe
---

### Post by Hulkiedulkie on 2013-02-06
I've been working with Ubuntu server for some 3 years now. The learning curve is steep at times, but I've managed to cross many hurdles.

Today (again) I was unable to locate a certain library to link to. I ended up doing it with find (again). 


This is a recurring pattern. After 3 years of frequent use of Ubuntu I still feel lost in the folder structure. Binaries, headers, libraries, config files seem to be all over the place. This is really offputting and makes me think I will never "master" linux. 

This seems like a very big flaw of Ubuntu (perhaps Unix more widely). Can't the devs get together and just force everyone to use standard directories? Or perhaps make a /programs directory to put standalone apps entirely in their own folder?

Discuss.

---

### Post by SeijiSensei on 2013-02-06
I recommend you start with this: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

A quick overview:

/bin, /sbin - contain binaries that can be run in single-user mode before the system goes multi-user; sbin contains binaries that usually require root privileges ("supervisor bin")

/usr/bin, /usr/sbin - binaries that are available in multi-user mode; most regular applications reside in /usr/bin, but things like server daemons that require root privileges to start are in /usr/sbin.

The /programs directory you seek is generally /usr/bin.

/lib, /usr/lib - same relationship to each other as /bin and /usr/bin; the kernel libraries are in /lib, for instance, since they are needed at boot and in single-user mode

/etc contains nearly all the configuration files that matter.  Some are at the root of that directory; others are in program-specific folders like /etc/apache2. 

/usr/share has auxiliary files like fonts, documentation, etc.

/usr/local - hierarchy for software installed manually outside of the package system; compiled applications that are installed with "sudo make install" typically end up here.  Configuration files are in /usr/local/etc/, libraries in /usr/local/lib, etc.

---

### Post by iponeverything on 2013-02-06
locate is good command.. 

because it is working from prebuilt db's it is fast.

---

### Post by Hulkiedulkie on 2013-02-06
@SeijiSensei

Why do we need 4+ directories for binaries? Sure one could say that /usr  is generally more higher level. But really it's not that clear-cut. Can  you tell without looking where "cat" is? Or "du"?

And if it only  yours were the whole story. There is /usr/share/lib, plus a lib64  variant, plus /var/lib which is some sort of dumping ground. And when I am looking for that C++ library I just installed  the structure inside them makes no obvious sense to me. Is it in the main folder, or under "cpp", or "gcc" or "x86_64-linux-gnu"?

I guess /etc is one of the better organized directories, but still configs can be found in other places like the home directories, /var, or /usr/shared

Your attempt at a tutorial is friendly, but really not of any practical help.


@iponeverything

Sure one can search. If the name hasn't been cut down to some meaningless acronym. But shouldn't finding a file be more accessable than that? Shouldn't it just make sense where to find it?

---

### Post by iponeverything on 2013-02-07
> **Hulkiedulkie said:**
> 

@iponeverything

Sure one can search. If the name hasn't been cut down to some meaningless acronym. But shouldn't finding a file be more accessable than that? Shouldn't it just make sense where to find it?

meaningless acronym? -- not quite. Every discipline has its "language".  Should UNIX geeks conform the non UNIX geeks sense of order? 

It a bit like congress thinking that they legislate a solution to earthquakes..  

It rarely takes me more that few minutes to locate any system file in the file system.

---

### Post by SeijiSensei on 2013-02-07
> **Hulkiedulkie said:**
> @SeijiSensei

Why do we need 4+ directories for binaries? Sure one could say that /usr  is generally more higher level. But really it's not that clear-cut. Can  you tell without looking where "cat" is? Or "du"?

I don't think you understand the different "[runlevels]("http://en.wikipedia.org/wiki/Runlevel")" in Unix.

A Unix box can run in single-user mode without needing anything in /usr, /var, or /home.  So binaries like ls and du, which are pretty much required at all levels, reside in /bin.  Similarly fdisk resides in /sbin.  Only when the machine is in multi-user mode are binaries in /usr/bin, etc., available.  In fact, they can reside on a separate partition or network share that isn't mounted until the machine goes multi-user.  

As to locating where they reside, most times it doesn't matter since the default PATH includes all the various combinations of /bin, /usr/bin, /usr/local/bin, etc.  If you want to find the location of a particular binary, use "which filename". It will search through your path and identify all files with that name, and any aliases you might have defined as well.  To find an arbitrary file, use "locate string".  That relies on a database that is updated nightly with updatedb.  You can give locate any arbitrary string, and it will return all files that include the string somewhere in the file's full path.

---

### Post by montag dp on 2013-02-07
Try figuring out the Windows system file hierarchy and then reevaluate whether it's really that disorganized in Linux.  Wow, that is such a mess.

---

### Post by Hulkiedulkie on 2013-02-09
> **SeijiSensei said:**
> I don't think you understand the different "[runlevels]("http://en.wikipedia.org/wiki/Runlevel")" in Unix.

A Unix box can run in single-user mode without needing anything in /usr, /var, or /home.  So binaries like ls and du, which are pretty much required at all levels, reside in /bin.  Similarly fdisk resides in /sbin.  Only when the machine is in multi-user mode are binaries in /usr/bin, etc., available.  In fact, they can reside on a separate partition or network share that isn't mounted until the machine goes multi-user.  

This just seems like an obscure reason to excuse a status-quo which is past its expiration date. I can think of many more bad reasons to spread the same type of files over different directories. 

Even if you did want to mount a directory with binaries later you can always use symlinks or mount it inside the "binaries" directory.

> As to locating where they reside, most times it doesn't matter since the default PATH includes all the various combinations of /bin, /usr/bin, /usr/local/bin, etc.  If you want to find the location of a particular binary, use "which filename". It will search through your path and identify all files with that name, and any aliases you might have defined as well.  To find an arbitrary file, use "locate string".  That relies on a database that is updated nightly with updatedb.  You can give locate any arbitrary string, and it will return all files that include the string somewhere in the file's full path.I think a clean hierarchy is a good thing in itself. I don't like to put my files anywhere and rely on search.

Besides, if you like search so much, wouldn't it be better to have a single binaries directory? And then have different (overlapping) categories to index them into? 


> **montag dp said:**
> Try figuring out the Windows system file  hierarchy and then reevaluate whether it's really that disorganized in  Linux.  Wow, that is such a mess.

Irrelevant to this discussion. I'm suggesting an improvement to Ubuntu. Has nothing to do with Windows.

---

### Post by SeijiSensei on 2013-02-09
Considering that the filesystem structure is based on negotiated agreements among Linux developers and distribution maintainers, there is no chance that Ubuntu will adopt a unique hierarchy.  You would need to take up the matter with the [Linux Foundation](http://en.wikipedia.org/wiki/Linux_Foundation).

> **Hulkiedulkie said:**
> Besides, if you like search so much, wouldn't it be better to have a single binaries directory? And then have different (overlapping) categories to index them into?

I rarely search at all for binaries.  I let the PATH take care of that for me.

You seem rather surly in these discussions so I'm done with this thread now.  Others can pick up the ball if they choose.

---

### Post by Hulkiedulkie on 2013-02-09
> **SeijiSensei said:**
> Considering that the filesystem structure is based on negotiated agreements among Linux developers and distribution maintainers, there is no chance that Ubuntu will adopt a unique hierarchy.  You would need to take up the matter with the [Linux Foundation]("http://en.wikipedia.org/wiki/Linux_Foundation").

If it was really negotiated with care then there wouldn't be so many discrepancies between different packages.

And Ubuntu seems to have no problem overthrowing decisions made upstream. Apache2 comes to mind but there's many more examples.


> I rarely search at all for binaries.  I let the PATH take care of that for me.

You seem rather surly in these discussions so I'm done with this thread now.  Others can pick up the ball if they choose.I don't mean to be. From my standpoint it seems you are more interested in making excuses for the status quo rather than debating stuff on its merits.

---

### Post by F.G. on 2013-02-09
Hi folks, just thought i'd add (as no-one seems to have mentioned this), that there is in fact a manual page for the hierarchy. And if you type:
```
man hier
```
you'll see it, this basically explains the hierarchy.

Also, as SeijiSensei pointed out the 'which' command is really useful for finding those built in and generic commands, which aren't sourced in some wierd way.

for what it's worth don't think the linux directories are at all obscure, and they are consistent across most distros, (and the windows one terrifies me). and for the system to be organised by file type, eg 'so, right guys, stick all your elf 32 files in here, and all your .h files in there.... oh, so now we have 50 remote boxes and 30 devs, and it's a mess you say?', would clearly not be scalable. one of the most best things that i have learned by using linux is how to find things out, (and how to find things). precisely so i don't have to remember where anything is. 
i just have a pointer to 'which', which seems to work fine.

---

