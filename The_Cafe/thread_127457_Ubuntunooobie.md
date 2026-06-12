---
title: "Ubuntunooobie"
date: 2006-02-09
forum: The Cafe
---

### Post by SoggyCornflake on 2006-02-09
Howdy  everybody,

Just a quick note to say hi.  I've landed here after a brief visit of a month or two in Debianville and a few years of being in Slackware land.

Since my primary use of my computer is as a desktop, Ubuntu or Kubuntu seems like the right place to be.   So far I've managed to figure out most of what I need to  - I just wish compiling a kernel would work for me.  (That's the one thing that I miss about Slackware.  I could get it to work there)

I'm pretty sure that I'm here to stay for a while.  Ubuntu does seem to be how Linux should be

---

### Post by chimera on 2006-02-09
Just curious, why do you need to compile a kernel?

---

### Post by SoggyCornflake on 2006-02-09
[QUOTE=chimera]Just curious, why do you need to compile a kernel?[/QUOTE]

I have a HD-3000 TV card that so far is not being detected correctly.  I  can see analog TV without sound but can't see or hear any HDTV.  The support CDROM that came with the card has drivers and instructions to work with Red hat's Fedora distro.  They didn't have instructions for other distros.

When I researched the card and Debian, I learned that the drivers for the card are included in the 2.6.8+ kernel, and compiling it seemed to make the most sense.  (As I said, I came from the Slackware world, so compiling a kernel isn't such a scary thing to me.)

---

### Post by kingsidy on 2006-02-09
ubuntu breezy uses the 2.6.12 kernel. it is certainly newer than 2.6.8. 
as far as compiling kernels, they have guide in the forums just look for it. pretty easy actually.

---

### Post by SoggyCornflake on 2006-02-09
[QUOTE=kingsidy]ubuntu breezy uses the 2.6.12 kernel. it is certainly newer than 2.6.8. 
as far as compiling kernels, they have guide in the forums just look for it. pretty easy actually.[/QUOTE]

I've followed them and I found them quite easy to follow, it's just I get errors in the process that keep things from working.

for example here's the latest:
[I]root@ubuntu:/usr/src/linux# dpkg-buildpackage -B -uc -us
dpkg-buildpackage: source package is linux-source-2.6.12
dpkg-buildpackage: source version is 2.6.12-10.26
dpkg-buildpackage: source changed by Ben Collins <bcollins@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: xmlto docbook-utils sharutils transfig dpatch
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
[/I]
If I try it with -d, then results are a bit more interesting:

dpkg-buildpackage: host architecture i386
 debian/rules clean
# if you need to change something, do it in the right place ;)
rm -rf TODO firmware modules kernel-versions package-list
cp -rp debian/d-i/i386/* .
mkdir -p modules/i386/shared/
cp -rp debian/d-i/shared/modules/* modules/i386/shared/
mkdir -p firmware/i386/shared/
cp -rp debian/d-i/shared/firmware/* firmware/i386/shared/
# ugly workaround from some fsck Makefile that removes all
# files called kernel-image, that is required by kernel-wedge to
# generate the kernel_*.udeb!
touch modules/i386/kernel-image
if [ -d modules/sparc64 ]; then \
        touch modules/sparc64/kernel-image && \
        cp -rp modules/sparc/shared modules/sparc64; \
fi
kernel-wedge gen-control > debian/control
Use of uninitialized value in split at /usr/share/kernel-wedge/commands/gen-control line 36, <KVERS> line 2.
dpatch unpatch-all[/I]
sh: dpatch: command not found
make: *** [dpatch-list] Error 127

---

### Post by emrys1 on 2006-02-09
Which version of Ubuntu are you using?

We have a lab here at BYU that we use Hoary Hedghog and I know that it has some problems with a couple of the drivers when you try to compile the new kernel.  We tried it with Breezy and it seemed to work fine

---

### Post by UbuWu on 2006-02-10
[QUOTE=SoggyCornflake]
dpkg-checkbuilddeps: Unmet build dependencies: xmlto docbook-utils sharutils transfig dpatch[/QUOTE]

This will probably solve your problems:

sudo apt-get install xmlto docbook-utils sharutils transfig dpatch

also apt-get can automatically install all dependencies of a package, but I don't remember the specific command for that right now.

---

### Post by Brunellus on 2006-02-10
[QUOTE=UbuWu]This will probably solve your problems:

sudo apt-get install xmlto docbook-utils sharutils transfig dpatch

also apt-get can automatically install all dependencies of a package, but I don't remember the specific command for that right now.[/QUOTE]
sudo apt-get install -f

will attempt to fix all unmet dependencies.

---

### Post by UbuWu on 2006-02-10
[QUOTE=Brunellus]sudo apt-get install -f

will attempt to fix all unmet dependencies.[/QUOTE]

Yes but you can avoid the error in the first place:

sudo apt-get build-dep linux-source-x.xx.xx

---

### Post by Brunellus on 2006-02-10
[QUOTE=UbuWu]Yes but you can avoid the error in the first place:

sudo apt-get build-dep linux-source-x.xx.xx[/QUOTE]
good point.

---

