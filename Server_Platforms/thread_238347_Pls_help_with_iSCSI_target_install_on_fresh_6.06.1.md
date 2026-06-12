---
title: "Pls help with iSCSI target install on fresh 6.06.1 ubuntu server installation"
date: 2006-08-17
forum: Server Platforms
---

### Post by si285 on 2006-08-17
I hope this is the right place to post this.

Ihave been trying to get an iSCSI target installed on a fresh Ubuntu 6.06.1 server install without any luck.  I have been using the directions posted at 

[http://www.ubuntuforums.org/showthread.php?t=213545&highlight=iscsi](http://www.ubuntuforums.org/showthread.php?t=213545&highlight=iscsi)

but encounter this error when I try to install using them;

The problems start when I issue the command

sudo make KERNELSRC=/usr/src/linux

Here is the output with error

make -C usr
make[1]: Entering directory `/home/adam/Desktop/iscsi/usr'
cc -O2 -fno-inline -Wall -Wstrict-prototypes -g -I../include -c -o ietd.o ietd.c
make[1]: cc: Command not found
make[1]: *** [ietd.o] Error 127
make[1]: Leaving directory `/home/adam/Desktop/iscsi/usr'
make: *** [progs] Error 2


I'm using a fresh install of Ubuntu 6.06.1 and installed
make
libssl-dev
linux-headers-2.6.15-26-386
gcc -- I used gcc4 since it did not specify which version...


I must be missing something simple (or maybe not)...

I would prefer to use a Ubuntu based solution but I only have a week or so  to get it working before I'm forced to find another solution so any help would be greatly appreciated.

Thanks

---

### Post by ghstridr on 2006-09-02
> **si285 said:**
> I hope this is the right place to post this.

Ihave been trying to get an iSCSI target installed on a fresh Ubuntu 6.06.1 server install without any luck.  I have been using the directions posted at 

[http://www.ubuntuforums.org/showthread.php?t=213545&highlight=iscsi](http://www.ubuntuforums.org/showthread.php?t=213545&highlight=iscsi)

but encounter this error when I try to install using them;

The problems start when I issue the command

sudo make KERNELSRC=/usr/src/linux

Here is the output with error

make -C usr
make[1]: Entering directory `/home/adam/Desktop/iscsi/usr'
cc -O2 -fno-inline -Wall -Wstrict-prototypes -g -I../include -c -o ietd.o ietd.c
make[1]: cc: Command not found
make[1]: *** [ietd.o] Error 127
make[1]: Leaving directory `/home/adam/Desktop/iscsi/usr'
make: *** [progs] Error 2


I'm using a fresh install of Ubuntu 6.06.1 and installed
make
libssl-dev
linux-headers-2.6.15-26-386
gcc -- I used gcc4 since it did not specify which version...


I must be missing something simple (or maybe not)...

I would prefer to use a Ubuntu based solution but I only have a week or so  to get it working before I'm forced to find another solution so any help would be greatly appreciated.

Thanks

First, do an apt-get for 'build-essential' to make sure you have all the needed tools.  It looks like you have the needed headers.
Do a 'which gcc' and 'which cc'.  If either fail to return anything, there is your problem.  You will need to make sure your $PATH includes /usr/bin if you installed to the default locations.
Easiest way to make sure the pathing is correct:
export $PATH=PATH:/usr/bin
If you are still getting the 'cc not found', do this:
find /usr -name cc -print
or 
locate cc (this will probably show more results that needed)

---

