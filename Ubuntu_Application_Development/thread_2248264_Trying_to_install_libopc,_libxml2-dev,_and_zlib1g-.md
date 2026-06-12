---
title: "Trying to install libopc, libxml2-dev, and zlib1g-dev"
date: 2014-10-13
forum: Ubuntu Application Development
---

### Post by mich5 on 2014-10-13
I'm trying to install the above in Ubuntu.  When I tried following instructions at [https://libopc.codeplex.com/wikipage?title=linux_ubuntu](https://libopc.codeplex.com/wikipage?title=linux_ubuntu) by typing sudo command at step 3 at linux command prompt, it said I'm missing libxml2-dev and zlib1g-dev. (I used 0.0.3 version of libopc because that's what was there).

When I downloaded libxml2-dev from  [libxml2]("http://packages.ubuntu.com/lucid/libxml2"), the i386 version, and ran following command:sudo dpkg -i libxml2-dev_2.7.6.dfsg-1ubuntu1.13_i386.deb
It said libxml2-dev:i386 depends on libxml2 ubuntu1.13, however libxml2:i386 on system is 2.7.8.dfsg-5.1ubuntu4.6. It says libxml2-dev:i386 depends on zlib1g-dev | libz-dev.
It seems like a tangled mess!  Am I installing the wrong version of libxml2?  Is there a better package to install to get libopc for Linux?  
I don't have a lot of experience with installing with sudo or downloading/unzipping in Ubuntu.  If you have links of where to install everything from that will work with my version of Ubuntu, that would be great.

I have Ubuntu 12.04 LTS.

---

### Post by steeldriver on 2014-10-13
Hello and welcome to the forums

What is your end goal here? Unless you have a very good reason for doing otherwise, you should probably be installing the versions of libxml2-dev and zlib1g-dev from the standard repositories using apt-get (or your favourite GUI package manager such as synaptic or Software Center)

---

### Post by mich5 on 2014-10-14
My end goal is to run libopc.  It turns out it's a 64 bit system.  I'm not sure what you're referring to about the standard repositories?  Do you mean to avoid the deb files and using a method other than the sudo?  Can you give an example and links?  When I tried installing the deb file through Software Center it got stuck/error'd out like it does at the command line, just took longer.

---

### Post by mich5 on 2014-10-14
I can run 32 bit version, but as long as I have all the pieces working together ok.  So far, I can't install the deb files for libxml2-dev 386 version because it's missing it's dependencies.

---

