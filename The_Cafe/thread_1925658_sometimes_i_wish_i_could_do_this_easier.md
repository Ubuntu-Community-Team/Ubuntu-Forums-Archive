---
title: "sometimes i wish i could do this easier"
date: 2012-02-14
forum: The Cafe
---

### Post by kitsuneclem on 2012-02-14
Ubuntu over the years has become pretty stable and quite easy to run, but alas theres a few things I a ubuntu Nubelet have yet to master May it be because of my peticulary bad leanrling skills from dyslexia (i read fine but ofter the words get jumbled up for me while reading) or just the learning curb from coming from a windows enviroment to the great linux that we have here

Yet still I cant figure some things out oh well

any ways i was hoping to find out from other ubuntu users what their trials over the years with linux is wand what they still have a hard time mastering

---

### Post by inobe on 2012-02-14
let's start with yours, this way we have an idea in which we can relate to.

---

### Post by kitsuneclem on 2012-02-15
> **inobe said:**
> let's start with yours, this way we have an idea in which we can relate to.
compiling files : / i just cant figure it out lol

---

### Post by cariboo on 2012-02-15
Aside from geek cred, you shouldn't have to compile almost anything from source. Most popular applications have ppa's or the authors have setup simple ways to install them, for example [Calibre]("http://calibre-ebook.com/download_linux") and [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-snapshots").

Both the above methods install the latest version of either program.

---

### Post by duncan12 on 2012-02-15
> **kitsuneclem said:**
> compiling files : / i just cant figure it out lol

You normally don't even need to get a PPA - just search the Software Centre. Or for stuff like Chrome, go to their website, download the .DEB and hit install.

---

### Post by aeiah on 2012-02-15
for compiling files, i usually unpack the .tar.gz / .tar.bz2 in my file manager (because i can never remember the tar command flags to do it in the terminal)

from there ill navigate to the directory i unpacked them to in a terminal, read the readme and install files to see if there's any dependencies i might need to install, and if not, run the configure script or whatever the instructions say
```

./configure
```

then i make the binary
```

make

```

then i install it in /usr/bin/ or wherever it decides it wants to go by default

```

sudo make install
```

if it needs dependencies ill use apt-get to install them first or fire up synaptic and do a search for them.


but yea, you don't usually need to compile things yourself. most of the time there's at least a ppa if it isn't in the main repositories. if an older version is in the repositories, ill install it first and see if it meets my expectations before deciding whether to compile the newest version from source.

---

### Post by kitsuneclem on 2012-02-15
> **aeiah said:**
> for compiling files, i usually unpack the .tar.gz / .tar.bz2 in my file manager (because i can never remember the tar command flags to do it in the terminal)

from there ill navigate to the directory i unpacked them to in a terminal, read the readme and install files to see if there's any dependencies i might need to install, and if not, run the configure script or whatever the instructions say
```

./configure
```then i make the binary
```

make

```then i install it in /usr/bin/ or wherever it decides it wants to go by default

```

sudo make install
```if it needs dependencies ill use apt-get to install them first or fire up synaptic and do a search for them.


but yea, you don't usually need to compile things yourself. most of the time there's at least a ppa if it isn't in the main repositories. if an older version is in the repositories, ill install it first and see if it meets my expectations before deciding whether to compile the newest version from source.

I useually download ready made files but of course theres the rare case that i'm trying a high end Linux native mmo that is set up as a bin file I just have not been able to figure out how to install them By the way im not sure if compile is the right term

---

### Post by chili555 on 2012-02-16
I usually download the .tar.gz to a convenient location; in my case Desktop. I right-click and select *Extract Here*. When the extracted folder appears, I open it and read the README. (duh!)

Sometimes the process is ./configure, sometimes make and make install and sometimes install.sh. Use the required procedure and you can hardly go wrong!

Compiling generally requires build-essential and linux-headers-gerneric:```
sudo apt-get install build-essential linux-headers-gerneric
```Finally, I try to be conscious of kernel/gcc and package mismatch. If I am running Ubuntu 11.10, a package built in 2006 is unlikely to compile. Likwise, if I am running 8.04, a 2012 package is unlikely to compile.

As others have said, 98% of everything you will ever need is in Software Center and requires no compiling.

On the other hand, compiling is kind of fun. Reading all the .c files helps me learn a bit more about how things work and sometimes how I might customize the package to my particular twisted needs.> theres a few things I a ubuntu Nubelet have yet to masterMost of us are very careful and patient with new Ubuntu users. Call on us at any time.

---

### Post by aeiah on 2012-02-16
> **kitsuneclem said:**
> I useually download ready made files but of course theres the rare case that i'm trying a high end Linux native mmo that is set up as a bin file I just have not been able to figure out how to install them By the way im not sure if compile is the right term

yea this isn't really compiling. as you say, the file is an executable binary - its already been compiled.

in this case, you'd want to set the file to be executible (either in a terminal or by right-clicking and going to properties) and then either double click it, or navigate to its location in a terminal and do:
```

./filename

```

---

