---
title: "looking for tool to install from source"
date: 2006-07-09
forum: The Cafe
---

### Post by reacocard on 2006-07-09
I'm looking for a tool to automatically install packages from a source .tar.gz. anybody know of one that works in ubuntu? preferably command-line, but anything will do.

---

### Post by tonyr on 2006-07-09
Look into [**checkinstall**]("http://asic-linux.com.mx/~izto/checkinstall/")

---

### Post by fluffington on 2006-07-09
Check out dpkg-buildpackage (Ubuntu package dpkg-dev) and [this chapter](http://www.debian.org/doc/maint-guide/ch-build.en.html) of the [Debian New Maintainers' Guide](http://www.debian.org/doc/maint-guide/). It makes .deb packages from source, which you can later upgrade or uninstall.

Edit: CheckInstall, mentioned by the previous poster, is probably a better option.

---

### Post by reacocard on 2006-07-09
none of these tools are automatic enough. I want something that takes a .tar.gz archive as an argument, and either installs it or produces a .deb.

---

### Post by xXx 0wn3d xXx on 2006-07-09
> **reacocard said:**
> none of these tools are automatic enough. I want something that takes a .tar.gz archive as an argument, and either installs it or produces a .deb.

That's not possible without a package manager especially for Ubuntu that would do that, besides is it that hard to type this in terminal after unzipping a source program.

> ./configure
make
sudo make install

---

### Post by fluffington on 2006-07-09
> **reacocard said:**
> none of these tools are automatic enough. I want something that takes a .tar.gz archive as an argument, and either installs it or produces a .deb.

Why not just write a simple script yourself? Something similar to the following aught to do the job:

```

#!/bin/sh
cd `dirname $1`/`tar xvzf $1 | head -n1`  &&\
./configure && make && sudo make install  &&\
thisdir=`pwd` && cd ..  &&\
rm -ri $thisdir

```

That'll unpack the archive, cd into the created directory,  install it, and then delete the directory. The rm -i will probably be irritating, but it's there becuse I don't entirely trust this to not attempt to delete / or do something else that's just as stupid.

Edit: forgot the sudo

---

### Post by aysiu on 2006-07-09
How would the script fetch all the dependencies?

P.S. Have you considered using Gentoo?

---

### Post by reacocard on 2006-07-09
i'm looking for something for ubuntu, not gentoo (ugh, install everything from source? crazy.). That shell script looks good. i'll give it a go, with a few modifications. something like this:
```
#!/bin/sh
cd `dirname $1`/`tar xvzf $1 | head -n1`  &&\
auto-apt run ./configure && make && checkinstall  &&\
thisdir=`pwd` && cd ..  &&\
rm -ri $thisdir
```

the auto-apt will get dependencies, and checkinstall will create a .deb for easy removal.

EDIT: when i run the script, it gives me this error:
```
/home/aren/downloads/installsource.sh: line 2: cd: /home/aren/downloads/gnome-sudoku-0.5.0/: No such file or directory
```
I think this means it's attempting to cd into the directory before it untars it. how do i fix this? i know nothing about bash scripting.

---

### Post by fluffington on 2006-07-09
> **reacocard said:**
> the auto-apt will get dependencies

I didn't know that. I'll have to remember it for the next time I'm trying to compile stuff.

---

### Post by reacocard on 2006-07-09
yeah. it's really nice. any ideas on how to fix the error? or just point me to a bash scripting guide and i'll figure it out myself.

---

### Post by fluffington on 2006-07-09
> **reacocard said:**
> yeah. it's really nice. any ideas on how to fix the error? or just point me to a bash scripting guide and i'll figure it out myself.

It's a silly error that I would have caught had I actually tested before posting. It assumes that you're extracting to the same place as the archive, which isn't always true. If you replace `dirname $1` with `pwd`, it should work (or at least get a little further before stopping).

And here's a [Bash guide](http://www.faqs.org/docs/abs/HTML/).

Edit: Noticed that gnome-sudoku is in universe and that there's a .deb on SourceForge. Not that this isn't a useful learning exercise.

---

### Post by reacocard on 2006-07-10
yeah, i know gnome-sudoku is in the repos. just needed something to test the script with. will try the modification, and post my results later.

---

