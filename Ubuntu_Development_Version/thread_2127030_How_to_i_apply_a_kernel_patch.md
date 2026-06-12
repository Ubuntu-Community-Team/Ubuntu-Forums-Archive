---
title: "How to i apply a kernel patch"
date: 2013-03-18
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-03-18
bug:
[https://bugzilla.kernel.org/show_bug.cgi?id=55161](https://bugzilla.kernel.org/show_bug.cgi?id=55161)
patches:
[https://patchwork.kernel.org/patch/2254211/](https://patchwork.kernel.org/patch/2254211/)
[https://patchwork.kernel.org/patch/2254221/](https://patchwork.kernel.org/patch/2254221/)

how do i apply these patches?

---

### Post by Doug S on 2013-03-18
Have a look at the "patch" command (i.e. "man patch"). My own experience hasn't been to good, and I seem to end up editing the source file, manually applying the patch. (However, I was trying to backport patchs and things had simply changed to much for "patch" to be able to figure it out. Maybe it will work better for you.) You will have to compile, which your bugzilla notes mentioned "compiling hates me".

---

### Post by pqwoerituytrueiwoq on 2013-03-18
i think i will need .tar.xz here [https://www.kernel.org/](https://www.kernel.org/)
what packages are required for compiling the kernel? (i have never compiled a kernel, how will i get deb files?)

better idea, can someone here compile it for me with those patches and drop the debs in a online file host?

will those patches be here tomorrow?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/current/)

---

### Post by Kow on 2013-03-19
How to apply a kernel patch
patch -p1 < ../patch-x.y.z will usually work
sometimes patch -p0 < ../patch-x.y.z
depends on how the patch was created (basically the -p command tells patch to strip X levels of directories)
[https://www.kernel.org/doc/Documentation/applying-patches.txt](https://www.kernel.org/doc/Documentation/applying-patches.txt) was one of my very first bookmarks.

---

### Post by meteorrock on 2013-03-19
I go over how patches work and the switches used with them in my blog thread over in cyanogenmod here. Check it over. The man patch help file in your terminal covers some of the aspects of how patches work, without going over too much on how path variables and switches work. For how to use the patch command correctly check this link here, note box 52. [http://forum.cyanogenmod.org/topic/50994-follow-along-with-me-trying-to-learn-how-to-code/page__st__40](http://forum.cyanogenmod.org/topic/50994-follow-along-with-me-trying-to-learn-how-to-code/page__st__40)

The link above also goes over how the git and github along with its bash commands work for any project you are looking into on modifying kernels. Android is a good case study for kernel work right now with projects up in XDA developers forums for different android devices. They use linux kernels, just not generic kernels on the main branches for ubuntu or other linux builds.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Here is a copy paste of the patch commands I use on patching kernels on my project on the nook color device from box 52 of the link above.

The following is the most commonly used. 

  ```
patch -p1 <  [/path/to/patch/file]
```

 Lets go over how these switches work.

 -p=num or --strip=num
 Strip the smallest prefix containing "num" leading slashes from each file name found in the patch file. A sequence of one or more adjacent slashes is counted as a single slash. This controls how file names found in the patch file are treated, in case you keep your files in a different directory than the person who sent out the patch. For example, supposing the file name in the patch file was, 

 /meteorrock/usr/bin/nookcolor/encore.c 

 ~~~~~~~~~~~~~~~~~~~~

 Setting -p0 gives the entire file name unmodified, -p1 gives, 

 /usr/bin/nookcolor/encore.c 

 ~~~~~~~~~~~~~~~~~~~~

 Without the leading slash, -p4 gives, 

 /nookcolor/encore.c 

 ~~~~~~~~~~~~

 And not specifying -p at all just gives you /encore.c/. Whatever you end up with is looked for either in the current directory, or the directory specified by the "-d" option.

 This option is used above for the smallest subdirectory you are working in. 

 ```
patch < [filename.patch]
```

 ~~~~~~~~~~~~~~~~~~

 See how those switches are pointing to either a full PATH directory or a sub directory at a time? Kind of cool huh?

 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 
 ~~~~~~~~~~~~~~~~~~~~~~~~~

 Patches can be undone or reversed, with the '-R' option also on your linux or android custom ROM builds like this:


 ```
patch -R < [/path/to/file]
```

 Do not forget the (<) symbol in that code above. Its a "POINTER" pointing the path to your switch, its part of your syntax, or code. 

  
Hope this helps you. Patching kernels is tricky. Keep trying. :)

---

### Post by schragge on 2013-03-19
A good source of information about how to patch kernels the Debian way is the [Debian Linux Kernel Handbook]("http://kernel-handbook.alioth.debian.org/ch-common-tasks.html#s-common-official"), particularly *4.2.2 Simple patching and building* and *4.2.3 Applying patches and configuration changes*.

---

### Post by pqwoerituytrueiwoq on 2013-03-19
given i patched the kernel and have all the dependences (hopefully) needed to compile and i am using [https://www.kernel.org/pub/linux/kernel/v3.x/testing/linux-3.9-rc3.tar.xz](https://www.kernel.org/pub/linux/kernel/v3.x/testing/linux-3.9-rc3.tar.xz) for source code, what do i do next, i assume i need some config files to go somewhere telling it i want deb files in the amd64 architecture

```
test@A54C-NB91:~/linux-3.9-rc3$ patch -p1 < ../kernel-patch1 
patching file drivers/gpu/drm/i915/intel_panel.c
test@A54C-NB91:~/linux-3.9-rc3$ patch -p1 < ../kernel-patch2
patching file drivers/gpu/drm/i915/intel_panel.c
test@A54C-NB91:~/linux-3.9-rc3$ ls 
arch     Documentation  init     lib          README          sound
block    drivers        ipc      MAINTAINERS  REPORTING-BUGS  tools
COPYING  firmware       Kbuild   Makefile     samples         usr
CREDITS  fs             Kconfig  mm           scripts         virt
crypto   include        kernel   net          security
```
hopefully being these packages
```
sudo apt-get install patch build-essential fakeroot;sudo apt-get build-dep linux
sudo apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge
sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev
```

i found this:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)
this really all there is to it?, was expecting [this]("http://xkcd.com/456/")
```
cd ~
wget https://www.kernel.org/pub/linux/kernel/v3.x/testing/linux-3.9-rc3.tar.xz
tar -xvf ./linux-3.9-rc3.tar.xz
cd linux-3.9-rc3
cp /boot/config-3.9.0-030900rc3-generic .config
make oldconfig
make clean
make -j `getconf _NPROCESSORS_ONLN` deb-pkg LOCALVERSION=-custom
sudo dpkg -i ../linux-*.deb
```

would this compile the same if i used my desktop?
my desktop's AMD Phenom II 965 x4 @ 3.7GHz is faster than a Intel Pentium Dual Core B970 2.3GHz
edit looks like i need more disk space...

---

