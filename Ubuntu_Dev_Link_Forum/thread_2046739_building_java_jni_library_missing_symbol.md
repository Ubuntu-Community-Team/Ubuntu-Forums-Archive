---
title: "building java jni library missing symbol"
date: 2012-08-23
forum: Ubuntu Dev Link Forum
---

### Post by pinan on 2012-08-23
Hi,
I am trying to build a program I found on the net to turn the lights on my alienware computer.  When I run it I get the error.

/usr/lib/jvm/java-7-oracle-1.7.0.5/bin/java: symbol lookup error: /home/dp42/workspace/jAlienFX/linuxLibSrc/libAlien64.so: undefined symbol: libusb_init

A quick check of the libAlien64.so library indicates a unlinked symbol libusb_init.  This symbol is from the libusb.so library.  An strace -fo of the running program indicates no attempt to access this library.
LD_LIBRARY_PATH includes /usr/lib/x86_64-linux-gnu
An ldd on the libAlien64.so shows a lib of dependencies, ie


ldd libAlien64.so
	linux-vdso.so.1 =>  (0x00007fff4b7ff000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f3c80af7000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f3c808e1000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f3c80523000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f3c80229000)

Now I assume that I need to see something like 
        libusb.so => /lib/x86_64-linux-gnu/libusb.so blah blah

Q.  How do I insert such a dependencies, my current build script is 


g++ -I/usr/include/libusb-1.0 -I/usr/lib/jvm/java-7-openjdk/include  -I/usr/lib/jvm/java-7-openjdk/include/linux  -g -fPIC -L/usr/lib/x86_64-linux-gnu -lusb -lpthread -shared -Wl,-soname,Alien64.so -o libAlien64.so main.cpp

---

### Post by tsenapathy on 2012-10-26
Use LD_PRELOAD as a workaroud.  I'm not sure this is a solution but it works for me.  I've given my answer [here]("http://stackoverflow.com/questions/9558909/jni-symbol-lookup-error-in-shared-library-on-linux/13086028#13086028")

---

