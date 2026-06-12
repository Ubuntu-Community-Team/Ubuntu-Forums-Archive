---
title: "Gutsy dazuko + apparmor"
date: 2007-10-24
forum: Server Platforms
---

### Post by d0nster on 2007-10-24
I'm trying to install dazuko and clamav on a new file server running Gutsy.  My problem is that I have to remove apparmor to insert dazuko into the kernel, but then I can't get apparmor to load again.  My error message is:

FATAL: Error inserting apparmor (/lib/modules/2.6.22-14-server/ubuntu/security/apparmor/apparmor.ko): Resource temporarily unavailable

If anyone has any ideas about how to get these two to work together, I would appreciate the help.

---

### Post by RT236 on 2007-10-24
> **d0nster said:**
> I'm trying to install dazuko and clamav on a new file server running Gutsy.  My problem is that I have to remove apparmor to insert dazuko into the kernel, but then I can't get apparmor to load again.  My error message is:

FATAL: Error inserting apparmor (/lib/modules/2.6.22-14-server/ubuntu/security/apparmor/apparmor.ko): Resource temporarily unavailable

If anyone has any ideas about how to get these two to work together, I would appreciate the help.

I have the same problem now since I just upgraded from Feisty to Gusty.  I also had it with SuSE 10.2, although there I could eventually insert dazuko into the kernel, but then it was kicked out on reboot.  I noticed in Feisty apparmor was not pre-loaded and you had to install it from Universe.  For Gusty it's already loaded in the release, of course, as part of the build.

I posted on dazuko.org the problem and a solution I used leveraging off the dazuko.org FAQ.  I had to leave apparmor uninstalled also with the other things I posted over there for SuSE 10.2.  I suspect for Gusty similar will need to be done by John Ogness, the dazuko developer.

You might want to post this problem over in the support forum at dazuko.org.  Eventually I will post something there after I experiment some more here, although, I suspect my solution will be similar to yours in leaving apparmor uninstalled, maybe.

On the dazuko.org site John Ogness, the dazuko developer, discusses this problem, at least for SuSE at this time.  If I hear something on a real solution I'll post it here, but I don't have high hopes of that being really soon.

---

### Post by DaneM on 2007-10-29
Hello.  I'm trying to install Dazuko, but I'm having trouble compiling it.  I get this error:

```

/usr/src/modules/dazuko/dazuko_linux26_lsm.c:576: error: too few arguments to function ‘dazuko_security_default_ops.inode_removexattr’
make[2]: *** [/usr/src/modules/dazuko/dazuko_linux26_lsm.o] Error 1
make[1]: *** [_module_/usr/src/modules/dazuko] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [dummy_rule] Error 2

```

How did you manage to compile it?

Thanks.

--Dane

---

### Post by DaneM on 2007-10-29
A few hours after posting the last message, I realized that I wasn't using the latest version of the dazuko source.  I downloaded version 2.3.4 from [www.dazuko.org](www.dazuko.org), removed apparmor, and was able to compile and install it with no problems.  

I'm now running AntiVir ([www.free-av.com](www.free-av.com)) with no problems, and verified its on-demand scanning with the eircar test file ([www.eicar.com](www.eicar.com)).

Have a good one.

--Dane

---

### Post by almodovaris on 2008-04-03
Using Ubuntu 7.10 Gutsy Gibbon, everything therein updated to the versions available on April 3, 2008, I've run into similar problems.

Searching the internet for help, I've found a way to run dazuko together with apparmor. Of course, the credits go to those who found this solution. I only state it here concisely:

**Dazuko 2.3.4 for Gutsy Gibbon cookbook**

1. Download dazuko 2.3.4 from [http://dazuko.org](http://dazuko.org) 

2. Extract the tarred gunzip archive to a folder.

3. Run the following commands in the folder containing dazuko source:

$ gedit dazuko_linux.c

In gedit, remove the lines from 88 to 92 (starting from the line containing WITH_LOCAL_DPATH till two times # endif)

4. Run the following commands in the folder containing dazuko source (particularized for a 2.6.22-14-generic kernel):

$ ./configure --mapfile=/boot/System.map-2.6.22-14-generic --disable-local-dpath --disable-chroot-support --enable-syscalls
$ sudo make
$ sudo make install

5. Run the following commands:

$ sudo gedit /etc/modprobe.d/dazuko

In gedit, save the file dazuko with the following contents:

install dazuko /sbin/modprobe -r apparmor; /sbin/modprobe --ignore-install dazuko; /sbin/modprobe -i apparmor

6. Run the following command:

$ sudo gedit /etc/modules

In gedit, append the following line at the end of the file modules:

dazuko

7. Test the installation with the following commands:

$ sudo modprobe dazuko
$ sudo modprobe apparmor
$ sudo depmod -ae

8. Reboot and you're done.

(My answer assumes you already have installed the packages mentioned upon [http://www.linux.com/feature/60383](http://www.linux.com/feature/60383) )

It is a good idea to remove the backup files made by gedit.

---

### Post by DaneM on 2008-04-03
Thank you very much for posting the solution!  I'll give this a try next chance I get.

Have a good one. :)

--Dane

---

### Post by almodovaris on 2008-04-04
Perhaps it could be needed that one surfs to the dazuko.ko folder and run the insmod command (between step 6 and step 7):

$ cd /lib/modules/2*/extra
$ sudo rmmod apparmor
$ sudo insmod ./dazuko.ko

But, I don't know if that's really needed.

---

### Post by almodovaris on 2008-04-07
> **almodovaris said:**
> Perhaps it could be needed that one surfs to the dazuko.ko folder and run the insmod command (between step 6 and step 7):

$ cd /lib/modules/2*/extra
$ sudo rmmod apparmor
$ sudo insmod ./dazuko.ko

But, I don't know if that's really needed.

Nope, you don't need to run the code mentioned above.

I followed the dazuko cookbook on a new Gutsy Gibbon (with all security updates installed after the installation) installation, and it worked like a charm.

But, you do need to install the packages mentioned in the Build Debian packages article:

$ sudo apt-get update
$ sudo apt-get install checkinstall build-essential dh-make devscripts fakeroot patch diff patchutils linda lintian

---

