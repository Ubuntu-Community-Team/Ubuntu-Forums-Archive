---
title: "Source Code"
date: 2007-05-14
forum: The Cafe
---

### Post by doom_fan on 2007-05-14
Where can I find all of,or most of Ubuntu's source code?Is there anyway that I can download or request the source code on a disc?

I am also curious as to the complier that was used for the development of Ubuntu.If I am breaking any rules by this request I apologize in advance.Thanks for any help.

---

### Post by Cypher on 2007-05-14
You're not breaking any rules. Linux is free, and that includes the source code.

You can find the Kernel sources at [http://kernel.org](http://kernel.org) and many of the applications are GNU versions available at [http://gnu.org](http://gnu.org). The C/C++ compiler is most likely GCC/G++ also available at the GNU website.

---

### Post by doom_fan on 2007-05-14
> **Cypher said:**
> You're not breaking any rules. Linux is free, and that includes the source code.

You can find the Kernel sources at [http://kernel.org](http://kernel.org) and many of the applications are GNU versions available at [http://gnu.org](http://gnu.org). The C/C++ compiler is most likely GCC/G++ also available at the GNU website.
Thanks a lot however the GNU is only the applications isn't is?

---

### Post by JT673 on 2007-05-14
No problem...That's while we have the OSI and GPL...And kind of why SCO is suing us...

Just install packages "linux-source" and "linux-source-2.6.20", and a /usr/src/linux-source-2.6.20.tar.bz2 will magically appear :)...It's 45.5 MB though, so make some room.

---

### Post by Nikron on 2007-05-14
Also,

apt-get source [package]

---

### Post by doom_fan on 2007-05-14
Is this the FULL source code or are pieces missing?Can I recompile the Linux Kernel into something else or is the code a proof of concept only?

---

### Post by yatt on 2007-05-14
> **doom_fan said:**
> Is this the FULL source code or are pieces missing?Can I recompile the Linux Kernel into something else or is the code a proof of concept only?

Its is the full source. The license that most of the OS is licensed under mandates that you have to provide the full source.

---

### Post by saulgoode on 2007-05-14
I would recommend fetching your source code from the Ubuntu repositories (if you use Ubuntu). The source code that is available directly from kernel.org may cause problems if you replace your current Ubuntu kernel with it. 

The Ubuntu developers will sometimes add features to the "vanilla" kernel provided by kernel.org -- these features are often minor (support a graphical boot screen, re-order some hot-plug events on startup, etc) but occasionally they make a difference. 


(NOTE: I would suspect that Ubuntu starts with a Debian kernel as a baseline, not a vanilla kernel from kernel.org. The same principle holds though, you are better off with the source from the Ubuntu repositories than from the Debian repositories. The Ubuntu source will have any modifications specific to Ubuntu.)

---

### Post by hanzomon4 on 2007-05-14
Yeah depending on hardware rolling a vanilla kernel may cause issues, I've never had any. Try some of the patch sets floating around if you go vanilla, [beyond]("http://iphitus.loudas.com/index.html") is pretty neat. Can I ask what you want the source for? I know some people believe that all linux users are developers... I don't and I'm not a developer.

---

### Post by Anthem on 2007-05-15
Just so we're clear:  the code is all open, but you're not able to use it in your own project unless you also release the code to your project under the same license agreement.

---

### Post by Cypher on 2007-05-15
> **doom_fan said:**
> Thanks a lot however the GNU is only the applications isn't is?
I think it might help your understanding if you saw how a Linux distribution was put together. All of them, first and foremost, involve the Linux Kernel. This is a distribution independent piece managed by Linus (2.6 tree) and Andrew Morton (2.4 tree).

Once you have the Kernel, you need the file system. This basically involves all of the applications that are needed to make a worthwhile OS. These applications include simple things like "cp", "ls" and their brethren from the "coreutils" package to more complicated applications like the X Server (X-Org) and more.

You could just as easily build a VERY compact distribution with a Kernel and a file system based on [Busybox]("http://busybox.net/").

Now a key portion of Linux are the compilers used to generate all these applications. The GNU Compiler is usually the default. GNU is not one application, but rather an umbrella encompassing many applications.

---

### Post by ssam on 2007-05-15
from [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) you can get source code to all versions of all the opensource packages in ubuntu.

everything is compiled with GCC (there might be a few exceptions)

---

### Post by doom_fan on 2007-05-16
> **Anthem said:**
> Just so we're clear:  the code is all open, but you're not able to use it in your own project unless you also release the code to your project under the same license agreement.

Yeah I know I plan on if I release any thing to do so under the open source license agreement.


> **ssam said:**
> from [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) you can get source code to all versions of all the opensource packages in ubuntu.

everything is compiled with GCC (there might be a few exceptions)

Thank you this was most helpful.

---

### Post by mech7 on 2007-05-16
> **JT673 said:**
> No problem...That's while we have the OSI and GPL...And kind of why SCO is suing us...

Just install packages "linux-source" and "linux-source-2.6.20", and a /usr/src/linux-source-2.6.20.tar.bz2 will magically appear :)...It's 45.5 MB though, so make some room.

Yes cause god may know where we will store 45 mb on our 500 gb hdd's :lolflag:

---

### Post by JT673 on 2007-05-16
> **mech7 said:**
> Yes cause god may know where we will store 45 mb on our 500 gb hdd's :lolflag:

Just checking if you were listening or not :)...

---

