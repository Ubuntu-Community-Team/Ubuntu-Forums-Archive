---
title: "Problems compiling JamVM"
date: 2009-04-22
forum: Virtualisation
---

### Post by blink0 on 2009-04-22
Hey all.

I don't know if this is the place to post this, but I guess it is, so here it goes:

I have been having trouble compiling JamVM 1.5.3 on my Ubuntu 8.04... Well, it does compile (with the usual "./configure", "make" and "make install" combo) but I can't get it to run any class, I always get this error:

root@shell:/home/blink/Desktop/jamvm-1.5.3/src# ./jamvm lala
Exception occurred while VM initialising.
java/lang/NoClassDefFoundError: jamvm/java/lang/VMClassLoaderData

Specifying the boot classpath location yields the same:

root@shell:/home/blink/Desktop/jamvm-1.5.3/src# ./jamvm -Xbootclasspath:/usr/local/jamvm/share/jamvm/classes.zip:/usr/share/classpath/glibj.zip lala
Exception occurred while VM initialising.
java/lang/NoClassDefFoundError: jamvm/java/lang/VMClassLoaderData

Both .zip files do exist, but actually:

root@shell:/home/blink/Desktop/jamvm-1.5.3/src# unzip -l /usr/share/classpath/glibj.zip | grep VMClassLoaderData
root@shell:/home/blink/Desktop/jamvm-1.5.3/src# unzip -l /usr/local/jamvm/share/jamvm/classes.zip | grep VMClassLoaderData
root@shell:/home/blink/Desktop/jamvm-1.5.3/src#

That VMClassLoaderData doesn't seem to be on the .zip files :\ classpath is the newest version, what else can be missing?
Note: -verbose doesn't output anything else.
Note 2: Forgot to mention before, "apt-get install jamvm" is not an option, as I need to compile it manually, since I'll be modifying the source code and re-compiling it for a University project.

Thanks in advance,
Daniel

---

