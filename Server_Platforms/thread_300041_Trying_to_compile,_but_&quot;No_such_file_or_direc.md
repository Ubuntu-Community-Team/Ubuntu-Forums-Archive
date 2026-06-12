---
title: "Trying to compile, but &quot;No such file or directory&quot;"
date: 2006-11-15
forum: Server Platforms
---

### Post by roobarb! on 2006-11-15
Hi all,

Having some troubles with my Ubuntu Edgy server install. There are some issues I've come up against with the PWC webcam driver, so I downloaded the latest source, installed build-essentials with aptitude and went to compile the source with 'make'. But all I get is:

```
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/usr/src/pwc-10.0.11 modules
make: *** /lib/modules/2.6.17-10-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
```

So, I did some searching and based on some articles I found I used aptitude to install 'linux-image-server' and 'linux-image-2.6.17-10-server'. But still no beans.

I've searched my fingers off now, but I can't find a solution to this one. I know I'm trying to get the kernel source into /usr/src (or at least I believe that's the aim!) and I may have to make a symbolic link in /lib/modules, but that's where I reach the end of the line...

Please, any help would be much appreciated! Also, a HOWTO on setting up an Ubuntu box for compiling would be great, if one exists anywhere.

Cheers!

   Andy.

---

### Post by EatMorePie on 2006-11-19
I had the same problem.  The pwc makefile seems to assume that the build symlink has been set up for you when you installed the headers, but apparently the apt install doesn't do that.  You can create this symlink yourself and the build will work.  For your version of the kernel, just type (as root)

ln -s /usr/src/kernel-headers/kernel-headers-2.6.17-10-386 /lib/modules/2.6.17-10-386/build

And then try your build again.

---

### Post by EatMorePie on 2006-11-19
Sorry, I put an extra "kernel-headers" in there.  It should read:

ln -s /usr/src/kernel-headers-2.6.17-10-386 /lib/modules/2.6.17-10-386/build

But verify that these directories are right for you.

---

### Post by roobarb! on 2006-11-21
Thank you very much for the pointer - I'll give that a try this evening and report back!

Thanks again,

   Andy.

---

### Post by roobarb! on 2006-11-22
Righty! In my case I popped in the following symbolic link:

```
ln -s /usr/src/linux-headers-2.6.17-10-server /lib/modules/2.6.17-10-386/build
```

After that everything seemed to compile properly. :)

Now I've just got to solve the new problem with the webcam, but that's a different story... ;)

Thanks for your help,

   Andy.

---

### Post by jolene on 2006-12-27
Even with the symbolic link, I still get a 

```

jo@humbug:~/pwc-10.0.12-rc1$ make
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/jo/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/lib/modules/2.6.15-27-386/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-27-386/build'
make: *** [all] Error 2

```

message when I try to compile. My problem, as you can see, is with PWC and all things webcam...

---

### Post by az on 2006-12-27
> **jolene said:**
> Even with the symbolic link, I still get a 

```

jo@humbug:~/pwc-10.0.12-rc1$ make
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/jo/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/lib/modules/2.6.15-27-386/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-27-386/build'
make: *** [all] Error 2

```

message when I try to compile. My problem, as you can see, is with PWC and all things webcam...

Do you have the headers installed?  You need the linux-headers package which corresponds to your kernel to compile an extra module.  You don't need the whole source.

If you are running the server kernel, install

sudo apt-get install linux-headers-server

For a desktop system, use the linux-headers-generic (Edgy) or linux-headers-386 (Dapper).

---

### Post by jolene on 2007-01-22
Yep, I definitely, definitely, definitely have the correct headers:

```
jo@humbug:~$ sudo apt-get install linux-headers-386
Reading package lists... Done
Building dependency tree... Done
linux-headers-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

As you see. Still no cigar.

J

---

### Post by roobarb! on 2007-05-10
I know this was a while ago now, but you may want to give this a shot:

```
apt-get install linux-headers-`uname -r` build-essential
```

That will install the headers specific for your kernel, plus the essential build tools. If it starts shouting about the location of your 'includes' directory, it's hiding inside the /usr/src/linux-headers-*your-kernel-here* directory.

To find out the kernel you're running, just issue a:

```
uname -r
```

from the command prompt.

Hope that helps you. Or somebody! :)

---

