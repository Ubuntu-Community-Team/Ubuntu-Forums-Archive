---
title: "Request Tutorial on how to deal with tar files"
date: 2017-02-18
forum: The Cafe
---

### Post by afz12 on 2017-02-18
Hi all

I wonder if there would be any interest in establishing a series of tutorials or selecting a moderator specifically on the subject of tar files. So far, I have had little if any success getting tar files to work despite following any instructions I can find. Unfortunately, many Linux programs only come in tar file format, (e.g. SciLab, which I like and did find a deb file eventually). Having these available as the much easier deb format or as a ppa would be great but these aren't always available.

I am no whiz on Linux and find most Linux instructions to be cryptic and assume prior knowledge - perhaps to a level that would leave asking questions unwarranted anyway. When people suggest "place the file where you want to install it" - well many directory places reply "you don't have authority etc" so where is the preferred site to start from? I have no idea, but I assume there must be a standard directory for this and a standard installation methodology, albeit perhaps with variations. I have had very little success even following instructions verbatim - sometimes the terminal just gets half way and stops with an error message.

It doesn't matter what notebook I use nor any OS or version - so if there are others who struggle with tar files, would setting up a forum for dealing specifically with these seem appropriate? Unfortunately, as much as I wish they would evaporate away, it doesn't seem that this will ever eventuate:(

---

### Post by oldos2er on 2017-02-18
Which version of Ubuntu are you running?  Scilab is in the repositories,  at least for 16.10.

*.tar files are just archives, they can contain source code, precompiled binaries, or something else.  We'd need to know what exactly you're dealing with,  and the exact error messages you might be seeing.

---

### Post by wildmanne39 on 2017-02-18
*Thread moved to **The Cafe**.*
I am pretty sure the answer is no we have more then enough sub-forums already, we have a tutorial section already and all tutorials go there but they must meet strict criteria.

If you absolutely want to make a guide you can  use wiki it is what it was created for and that is the best place for guides, there is most likely already a guide for tar files in a wiki.

If you search I am sure you will find the information you need to install tar files or you can start a thread in New To Ubuntu or General Help they are well suited for this question already.

---

### Post by QIII on 2017-02-18
> selecting a moderator specifically on the subject of tar files

That's not what we do.

---

### Post by afz12 on 2017-02-18
Hi oldos2er

I use a number of OS say Ubuntu 16.04, 16.10, 17.04 alpha 2 and Mint 18.1and previous versions - none have worked with tar files on any occasion - i.e. I can't point to a specific case as I find other means or ignore.

SciLab is not on all versions of Linux, also the repository versions do not always present a proper console - just a terminal. An alternative Octave is OK for Mint but doesn't run on Ubuntu 17.04 as it complains about access authority. This is why I suggested a generic arrangement, not a specific problem.

---

### Post by afz12 on 2017-02-18
Thanks wildemanne39

I'll look into this

---

### Post by wildmanne39 on 2017-02-18
They are working on the snap apps look here:
[https://insights.ubuntu.com/2016/06/14/universal-snap-packages-launch-on-multiple-linux-distros/](https://insights.ubuntu.com/2016/06/14/universal-snap-packages-launch-on-multiple-linux-distros/)
and you can google for more information if you find this interesting.

---

### Post by sudodus on 2017-02-18
Getting the computer with linux installled and the program package included is the most convenient option.

Then there are options which are less convenient.

- Getting the program package with the iso file (pre-installed)
- Installing a program package
. from a standard repository
. from a PPA
. from a deb package 'manually'
. from a tarball or some other kind of package with 'ready to use code'
- Compiling a program from source code

It is more or less the opposite situation for the developer. More convenient for the end user often means more work for the developer. We can hope that the developer has time and energy to make things easy to use or at least explain how to install and use the software. Also tarballs can be different. The documents (README files and .doc files) may be easier or more difficult to understand and the shellscript files may be easier or more difficult to understand and use.

You can probably find tutorials via the internet, which explain using tarballs in general terms as well as specific tutorials for program packages.

-o-

"place the file where you want to install it": I suggest that you create a subdirectory in your home directory and work in that subdirectory, for example 'scilab' for that particular program.

```
cd
mkdir scilab
cd scilab
...
```

-o-

I can illustrate with mkusb. It is available for Ubuntu (and Ubuntu family flavours, Kubuntu, Lubuntu ... Xubuntu)) via a PPA.

[https://help.ubuntu.com/community/mkusb/](https://help.ubuntu.com/community/mkusb/)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

It is possible but a little more complicated to use the PPA in Debian,

[mkusb/install-to-debian](https://help.ubuntu.com/community/mkusb/install-to-debian)

There is also a tarball, to install into other linux distros. It is more complicated. I have tried to make it rather easy to understand, but the explanations assume some knowledge of using the command line. See this link,

[mkusb/gui/tarball](https://help.ubuntu.com/community/mkusb/gui/tarball)

You are welcome to compare installing mkusb from PPA with installing from tarball. Please tell me if there are things that need more or better explanations - and I can try to improve this particular tarball.

-o-

Finally, you are welcome to establish a series of tutorials for tarballs, that you find interesting and worthwhile to make easier to use. ***The linux community consists of many voluneers. Please become one of us*** :-)

There is an Ubunu subforum for tutorials, at this link: [The Ubuntu Forum Community - Other Discussion and Support - Tutorials](https://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by HermanAB on 2017-02-20
A tar file is an archive, same as a Windows zip file.  If you want to know how to compile a program from a tar file, then you need to untar and read the README and INSTALL files that you will find inside.

---

