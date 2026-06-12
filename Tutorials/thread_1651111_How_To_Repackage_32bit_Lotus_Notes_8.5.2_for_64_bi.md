---
title: "How To Repackage 32bit Lotus Notes 8.5.2 for 64 bit systems"
date: 2010-12-22
forum: Tutorials
---

### Post by kxmas on 2010-12-22
I repackaged Lotus Notes 8.5.2 for my 64bit install for myself and decided to share.  My motivation was that I dislike using the "--force-arch" option with dpkg.  I also wanted to create deb files that I could send to my coworkers.

To make a no-fuss package that installs, we need to automate the getlibs part of the install, create a symlink after the package is installed, and replace the 'i386' value with 'amd64' in the control file.

Assumptions: You have the ibm-lotus-notes-8.5.2.i586.deb file, along with getlibs and dpkg installed on your system.  You'll also need to grab the attached lotus-notes-8.5.2.patch.txt.  The instructions assume that the patch file and the deb file are in the same directory.

Note: Using 'sudo' so permissions don't get hosed.

[LIST=1]
[*]Extract package contents ```
sudo dpkg-deb -x ibm-lotus-notes-8.5.2.i586.deb ibm-lotus-notes-8.5.2
```
[*]Extract package the debian control files ```
sudo dpkg-deb -e ibm-lotus-notes-8.5.2.i586.deb ibm-lotus-notes-8.5.2/DEBIAN
```
[*]Patch package files ```
sudo patch -p0 -i lotus-notes-8.5.2.patch.txt
```
[*]Rebuild deb file  ```
sudo dpkg-deb -b ibm-lotus-notes-8.5.2 ibm-lotus-notes-8.5.2.amd64.deb
```
[/LIST]

Now, when you install the package, getlibs will automatically download the needed 32bit libraries.

Credits: [Marcus Khoo's blog post which had great info on the needed libraries]("http://metkhoo.blogspot.com/2010/10/lotus-notes-853-on-ubuntu-meerkat-1010.html")

---

### Post by mrguga on 2011-01-25
Thanks for sharing this! Very useful.

For the other .deb's that come along, do i need to change only the i568 to amd64 in the control file? (like ibm-lotus-feedreader-8.5.2.i586.deb, ibm-lotus-notes-nl1-8.5.2.i586.deb, ibm-lotus-notes-core-ptbr-8.5.2.i586.deb, ibm-lotus-feedreader-nl1-8.5.2.i586.deb, ibm-lotus-activities-8.5.2.i586.deb and some more...)

Maybe some files are only present in the brazilian portuguese version.

Hugs from Brazil =)

---

### Post by caligari2k on 2011-02-02
Has getlibs found a new home or been deprecated by another package.  There is a 404 on the freehostia.com site that is located in the forums now.

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

I've packaged up my lotus notes deb but looking for a "valid" copy of getlibs-all.deb.  I can't wait to test the new package.

---

### Post by nutznboltz on 2011-02-20
> **caligari2k said:**
> Has getlibs found a new home or been deprecated by another package.  There is a 404 on the freehostia.com site that is located in the forums now.

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

I've packaged up my lotus notes deb but looking for a "valid" copy of getlibs-all.deb.  I can't wait to test the new package.

You can get getlibs from this PPA:

[https://launchpad.net/~jcollins/+archive/jaminppa](https://launchpad.net/~jcollins/+archive/jaminppa)

I respun the getlibs for 10.10 Maverick in a PPA by itself.

[https://launchpad.net/~nutznboltz/+archive/cappy-getlibs-all](https://launchpad.net/~nutznboltz/+archive/cappy-getlibs-all)

---

### Post by zorg2 on 2011-02-23
> the "--force-arch" option with dpkg.
What force-arch option!?

```

# dpkg -i --force-arch ibm-lotus-notes-8.5.2.i586.deb
dpkg: unknown force/refuse option `arch'

```

---

### Post by zorg2 on 2011-02-23
> **zorg2 said:**
> > the "--force-arch" option with dpkg.
What force-arch option!?

```

# dpkg -i --force-arch ibm-lotus-notes-8.5.2.i586.deb
dpkg: unknown force/refuse option `arch'

```

Ahh, its :-

dpkg --force-architecture -i <package>

---

### Post by zorg2 on 2011-02-23
Did anyone get past this message:
/opt/ibm/lotus/notes/notes: error while loading shared libraries: libgnomeprint-2-2.so.0: cannot open shared object file: No such file or directory


I have installed these packages:
# dpkg -l | grep libgnomeprint
ii  libgnomeprint2.2-0                    2.18.6-1build2                                  The GNOME 2.2 print architecture - runtime files
ii  libgnomeprint2.2-data                 2.18.6-1build2                                  The GNOME 2.2 print architecture - data files
ii  libgnomeprintui2.2-0                  2.18.4-1build1                                  GNOME 2.2 print architecture User Interface - runtime f
ii  libgnomeprintui2.2-common             2.18.4-1build1                                  GNOME 2.2 print architecture User Interface - common fi

---

### Post by kxmas on 2011-02-28
> **zorg2 said:**
> Did anyone get past this message:
/opt/ibm/lotus/notes/notes: error while loading shared libraries: libgnomeprint-2-2.so.0: cannot open shared object file: No such file or directory

It's part of libgnomeprint2.2-0.  If getlibs didn't install it for some reason, you can extract it out of the 32bit version and copy libgnomeprint-2-2.so.0.1.0 to /usr/lib32.  Symlink /usr/lib32/libgnomeprint-2-2.so.0 to it.

---

### Post by buckmaster60 on 2011-05-03
The top post works along with this post:
[http://usablesoftware.wordpress.com/2011/04/05/lotus-notes-8-5-2-fp2-in-ubuntu-11-04-natty-narwhal-64bit-beta-1/](http://usablesoftware.wordpress.com/2011/04/05/lotus-notes-8-5-2-fp2-in-ubuntu-11-04-natty-narwhal-64bit-beta-1/)

fyi

---

### Post by buckmaster60 on 2011-05-03
mrguga did you ever figure out how to add the other packages such as the service pack and sametime?

Thanks

---

### Post by nutznboltz on 2011-05-20
> **nutznboltz said:**
> You can get getlibs from this PPA:

[https://launchpad.net/~jcollins/+archive/jaminppa](https://launchpad.net/~jcollins/+archive/jaminppa)

I respun the getlibs for 10.10 Maverick in a PPA by itself.

[https://launchpad.net/~nutznboltz/+archive/cappy-getlibs-all](https://launchpad.net/~nutznboltz/+archive/cappy-getlibs-all)

I just rebuilt my getlibs PPA for Natty so I can run Tweetdeck eventually.

[http://kb2.adobe.com/cps/521/cpsid_52132.html](http://kb2.adobe.com/cps/521/cpsid_52132.html)

Update:
Heh, just found out how this approach is not needed.  There are things like this:
[https://launchpad.net/~thopiekar/+archive/natty-dev/+build/2285473](https://launchpad.net/~thopiekar/+archive/natty-dev/+build/2285473)

---

### Post by corrinado_swam on 2011-07-12
thanks for the tutorial. this lotus notes install went smooth. here is the link where i found getlibs: [http://ubuntuforums.org/showthread.php?t=1680819](http://ubuntuforums.org/showthread.php?t=1680819)

I still need more information about installing Lotus Sametime. Is it advised to use the --force-architecture option or to repackage the .deb file (ibm-lotus-sametime-8.5.2.i586.deb)

cheers

---

### Post by matsbekman on 2013-08-04
Just installed Notes 9 on Ubuntu 64 without problems.
Installing it completely with no errors in the operating system


[http://wp.me/p1CuQM-hQ](http://wp.me/p1CuQM-hQ)


For reading on how to

---

