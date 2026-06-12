---
title: "Find new files?"
date: 2011-09-12
forum: Server Platforms
---

### Post by ehime on 2011-09-12
I'm about to install a new module (contains php, xml, etc) into our server and would like to find out which files are installed. I believe that this package also installs into mysql and if I can would like to figure out what tables/rows it installs into. Is there an easy(ish) way to do this? Thanks guys and gals you're the best.

---

### Post by ubudog on 2011-09-13
Moved to Server Platforms, hopefully you get some more responses there.

---

### Post by ubudog on 2011-09-13
Could you provide some more info?  What module?

---

### Post by zackwasa on 2011-09-14
You can use AIDE and make a snapshot of current files then install whatever you want and then run AIDE again and compare with the previous results.

---

### Post by Lars Noodén on 2011-09-14
```

# make an arbitrary file and set the date
touch -t 20110911 /tmp/x;

# find all files that are newer than an arbitrary file
find /some/path -newer /tmp/x -print

```

---

### Post by Lars Noodén on 2011-09-14
To find with packages (rather than files) you have installed, 

```

[dpkg](http://manpages.ubuntu.com/manpages/natty/en/man1/dpkg.1.html) -l | [awk](http://manpages.ubuntu.com/manpages/natty/en/man1/awk.1posix.html) '/ii/ { print $2 }' | [sort](http://manpages.ubuntu.com/manpages/natty/en/man1/sort.1.html) > packages.txt

```

That will list all installed packages in the text file.

---

### Post by Doug S on 2011-09-14
My method is a little more brute force.
I take a before picture: "ls -l -R /* >dir01" or "sudo ls -l -R /* >dir01"
do whatever.
Then take an after picture: "ls -l -R /* >dir02"
Then look at the differences, noting that there will be be several that are just logs updating and such: "diff dir01 dir02"
 
Lars: it is not clear to me that the "find newer" method will work because are not many files installed with older dates? (Note: I also tested my method and the "find newer" method with an update just now, and the "find newer" method missed many files that changed (they had older dates))

---

