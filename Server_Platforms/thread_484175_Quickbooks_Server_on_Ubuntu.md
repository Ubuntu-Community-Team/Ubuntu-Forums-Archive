---
title: "Quickbooks Server on Ubuntu?"
date: 2007-06-25
forum: Server Platforms
---

### Post by CarbineMonoxide on 2007-06-25
Hello, I'm trying to get my Ubuntu Server 7.04 to be the host for my Quickbooks file. I've tried to follow the guide found here: [http://http-download.intuit.com/http.intuit/CMO/qbes/resources/pdfs/LinuxInstallGuide.pdf](http://http-download.intuit.com/http.intuit/CMO/qbes/resources/pdfs/LinuxInstallGuide.pdf)

But I have run into a snag..

root@Medusa:/home/josh# rpm -ivh qbdbm-17.0-14.i386.rpm
error: Failed dependencies:
        /bin/sh is needed by qbdbm-17.0-14.i386
        libc.so.6 is needed by qbdbm-17.0-14.i386
        libc.so.6(GLIBC_2.0) is needed by qbdbm-17.0-14.i                                                                     386
        libc.so.6(GLIBC_2.1) is needed by qbdbm-17.0-14.i                                                                     386
        libc.so.6(GLIBC_2.1.2) is needed by qbdbm-17.0-14                                                                     .i386
        libc.so.6(GLIBC_2.1.3) is needed by qbdbm-17.0-14                                                                     .i386
        libc.so.6(GLIBC_2.2) is needed by qbdbm-17.0-14.i                                                                     386
        libc.so.6(GLIBC_2.4) is needed by qbdbm-17.0-14.i                                                                     386
        libdl.so.2 is needed by qbdbm-17.0-14.i386
        libdl.so.2(GLIBC_2.0) is needed by qbdbm-17.0-14.                                                                     i386
        libdl.so.2(GLIBC_2.1) is needed by qbdbm-17.0-14.                                                                     i386
        libfam.so.0 is needed by qbdbm-17.0-14.i386
        libgcc_s.so.1 is needed by qbdbm-17.0-14.i386
        libgcc_s.so.1(GCC_3.0) is needed by qbdbm-17.0-14                                                                     .i386
        libm.so.6 is needed by qbdbm-17.0-14.i386
        libm.so.6(GLIBC_2.0) is needed by qbdbm-17.0-14.i                                                                     386
        libpthread.so.0 is needed by qbdbm-17.0-14.i386
        libpthread.so.0(GLIBC_2.0) is needed by qbdbm-17.                                                                     0-14.i386
        libpthread.so.0(GLIBC_2.1) is needed by qbdbm-17.                                                                     0-14.i386
        libpthread.so.0(GLIBC_2.2) is needed by qbdbm-17.                                                                     0-14.i386
        libstdc++.so.6 is needed by qbdbm-17.0-14.i386
        libstdc++.so.6(CXXABI_1.3) is needed by qbdbm-17.                                                                     0-14.i386
        libstdc++.so.6(GLIBCXX_3.4) is needed by qbdbm-17                                                                     .0-14.i386


Any ideas?

---

### Post by amlucent23 on 2007-06-27
umm wait thats an rpm file, I think youll need alien to use it, that or see if they have a .deb or a compileable version available

---

### Post by ols on 2007-06-28
sudo apt-get install alien
sudo alien –k --scripts <pkg_name.rpm>
sudo dpkg -i <pkg_name>.deb

---

### Post by kubug on 2007-08-29
I know this is somewhat of an old post, but I wanted to get the Quickbooks server running on our ubuntu server as well.

If anybody has got the Quickbooks server install on their linux system (SuSE or Fedora or whatever), can you let us know if it is worth the trouble?  [-o<

There is only an RPM available, and the website indicates that it's only supported for SuSE and Fedora. Question is now, whether one can make it work on other distributions.

Oh, just as a side note: I am a noob!

**What I have so far:**

I already have it running through Samba, so this may not be critical, but I thought it may add some features/speed/reliability.

I have downloaded the manual and the RPM. I did the "alien" (albeit without the "-k" and the "-scripts") and installed the .deb. So far no errors, other than the warning about the key missing (I guess that's what the -k was for).

**What's no working:**

What seems to be missing in ubuntu is the syslog deamon, since I don't seem to be able to start it (or restart for that matter). I downloaded the syslog-ng, but I don't think Quickbooks Server is compatible with it.

I cannot follow the manual after install, since the commands are not working.

---

