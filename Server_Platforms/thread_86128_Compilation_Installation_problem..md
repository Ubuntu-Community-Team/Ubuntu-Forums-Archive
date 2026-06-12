---
title: "Compilation Installation problem."
date: 2005-11-04
forum: Server Platforms
---

### Post by orly on 2005-11-04
Hello all,
First I would like to say that I'm a newbie in Linux-related topics, although I have searched and searched again the Internet before posting this subject.
The fact is that I installed Ubuntu 5.10 from the server CD download distribution, and I want to use Webmin from the server, but it didn't installed any GUI and while trying:
apt-get install x-system-core
it wasn't found, my PC has no connection to Internet yet, so I had 2 options:

1) My PC has a motorola sm56 winmodem, I found a linux driver for it, but didn't know how to compile it, after days and days....
apt-get install gcc gcc-4.0 make etc etc etc, but still unsuccessfully, here is the Makefile:
... 
all: 
	echo "Writing Version.c"
	echo "#define UTS_RELEASE \""`uname -r`"\"" >version.c
	echo "const char __module_kernel_version[] __attribute__((section(\".modinfo\" ))) = \"kernel_version=\"UTS_RELEASE;">>version.c
	echo "#ifdef MODVERSIONS" >>version.c
	echo "const char __module_using_checksums[] __attribute__((section(\".modinfo\"))) = \"using_checksums=1\";" >>version.c
	echo "#endif">>version.c
	echo Compiling version.c
	gcc -DLINUX -D__KERNEL__ -DMODULE -Wall -O -fomit-frame-pointer -o version.a  -c version.c
	echo Linking output version.a with Motorola proprietary sm56.lib 
	ld -r -o sm56.a  version.a sm56.lib
	echo Updating kernel symbols in output sm56.a
	objcopy --redefine-sym kmalloc=kmalloc_hack --redefine-sym __vmalloc=vmalloc_hack sm56.a sm56_h.a
	echo Compiling kmhack.o from input kludge.c
	gcc -DLINUX -D__KERNEL__ -DMODULE -Wall -O -I/usr/src/linux-2.4/include -fomit-frame-pointer -o kmhack.o -c kludge.c 
	echo Linking kmhack.o with sm56_h.a to generate sm56.o
	ld -r -o sm56.o sm56_h.a kmhack.o
	echo "Please Run \"make install\" "
	
clean:
	rm -f *.a
	rm -f *~
	rm -f *.o
	rm -f version.c 
	rm -f *.oo
install:
	make all
#Took From Original Sm56setup
	chmod u+x ./sminst.sh
	./sminst.sh

now, the all label calls:
gcc -DLINUX -D__KERNEL__ -DMODULE -Wall -O -I/usr/src/linux-2.4/include -fomit-frame-pointer -o kmhack.o -c kludge.c 
I know Ubuntu doesn't use that Kernel, I know it's 2.6.12.9 or something similar that:
uname -r
could give me.
but I haven't found anything under /usr/src

2) On the other hand I downloaded at work:
X.org, fvwm, wdm, xterm, fonts, firefox, openssl and ssleay and while trying to compile X.org I'm getting errors because there are compilation packages that are not shipped with the server installation CD as bison, and some of this:
binutils cpp cpp-4.0 fetchmail flex gcc gcc-4.0 libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev linux-kernel-headers lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev
While runing ./configure of fvwm, it depends on X

My questions are:
_ Supposing you could help me to use the winmodem, is it factible to get all compilation packages from universal repositories using dial-up?
_ What compilation packages am I missing in order to compile X besides bison?
_ How can I get those packages <> than apt-get?
I have Kubuntu installation CD, can I use it to include X.org and compilation packages in a PC that get installed using the Server-specific distribution CD? and if it could be done, how? what the sources.list will look like?

Any help will be appreciated,
Regards,
Orlando Otero

---

