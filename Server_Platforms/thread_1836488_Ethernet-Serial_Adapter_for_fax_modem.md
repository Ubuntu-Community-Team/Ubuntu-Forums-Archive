---
title: "Ethernet-Serial Adapter for fax modem"
date: 2011-08-31
forum: Server Platforms
---

### Post by gnagnibu on 2011-08-31
Hi all!
I'm trying to configure this ethernet-serial adapter on a Ubuntu Server 10.04.3 : [http://www.lavalink.com/dev/index.php?id=156](http://www.lavalink.com/dev/index.php?id=156) 

Any ideas to get it working?

---

### Post by gnagnibu on 2011-08-31
I've installed with make install but modprobe fails to load kernel module; from dir where files are stored:

# make install
cp esl.ko /lib/modules/2.6.32-33-generic-pae/kernel/drivers/char
rm -f /dev/ttyES*
mknod /dev/ttyES0 c 247 0
mknod /dev/ttyES1 c 247 1	
mknod /dev/ttyES2 c 247 2	
mknod /dev/ttyES3 c 247 3	
mknod /dev/ttyES4 c 247 4	
mknod /dev/ttyES5 c 247 5	
mknod /dev/ttyES6 c 247 6
mknod /dev/ttyES7 c 247 7
chmod 666 /dev/ttyES*
depmod -a

# modprobe esl
FATAL: Error inserting esl (/lib/modules/2.6.32-33-generic-pae/kernel/drivers/char/esl.ko): Invalid module format

---

### Post by gnagnibu on 2011-08-31
I'm trying to recompile the sources, but it is NOT so easy:

I've modified esl.c at line 28 and 45:

```

#include <linux/autoconf.h> //#include <linux/config.h>

```

```

#include <linux/semaphore.h> //#include <asm/semaphore.h>

```

but it fails

# make
make -C /lib/modules/2.6.32-33-generic-pae/build SUBDIRS=/root/Ether-Serial_Link modules 2>error.log
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic-pae'
  CC [M]  /root/Ether-Serial_Link/esl.o
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic-pae'
make: *** [default] Error 2

# cat error.log
/root/Ether-Serial_Link/esl.c:99: error: expected ‘)’ before string constant
/root/Ether-Serial_Link/esl.c:100: error: expected ‘)’ before string constant
/root/Ether-Serial_Link/esl.c:101: error: expected ‘)’ before string constant
/root/Ether-Serial_Link/esl.c:103: error: expected ‘)’ before string constant
/root/Ether-Serial_Link/esl.c:105: error: expected ‘)’ before string constant
/root/Ether-Serial_Link/esl.c:359: warning: initialization from incompatible pointer type
/root/Ether-Serial_Link/esl.c:367: warning: initialization from incompatible pointer type
/root/Ether-Serial_Link/esl.c:371: error: unknown field ‘read_proc’ specified in initializer
/root/Ether-Serial_Link/esl.c:371: warning: initialization from incompatible pointer type
/root/Ether-Serial_Link/esl.c:372: warning: initialization from incompatible pointer type
/root/Ether-Serial_Link/esl.c: In function ‘ltp’:
/root/Ether-Serial_Link/esl.c:694: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:694: error: ‘TTY_FLIPBUF_SIZE’ undeclared (first use in this function)
/root/Ether-Serial_Link/esl.c:694: error: (Each undeclared identifier is reported only once
/root/Ether-Serial_Link/esl.c:694: error: for each function it appears in.)
/root/Ether-Serial_Link/esl.c:696: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:698: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:698: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:699: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:699: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:699: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:699: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:700: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:701: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:702: error: ‘struct tty_struct’ has no member named ‘flip’
/root/Ether-Serial_Link/esl.c:776: error: request for member ‘write_wakeup’ in something not a structure or union
/root/Ether-Serial_Link/esl.c:777: error: request for member ‘write_wakeup’ in something not a structure or union
/root/Ether-Serial_Link/esl.c:1072: error: request for member ‘write_wakeup’ in something not a structure or union
/root/Ether-Serial_Link/esl.c:1073: error: request for member ‘write_wakeup’ in something not a structure or union
/root/Ether-Serial_Link/esl.c: In function ‘lava_open’:
/root/Ether-Serial_Link/esl.c:1164: error: ‘struct task_struct’ has no member named ‘uid’
/root/Ether-Serial_Link/esl.c:1165: error: ‘struct task_struct’ has no member named ‘euid’
/root/Ether-Serial_Link/esl.c:1173: error: ‘struct task_struct’ has no member named ‘uid’
/root/Ether-Serial_Link/esl.c: In function ‘lava_close’:
/root/Ether-Serial_Link/esl.c:1232: error: request for member ‘flush_buffer’ in something not a structure or union
/root/Ether-Serial_Link/esl.c:1232: error: request for member ‘flush_buffer’ in something not a structure or union
/root/Ether-Serial_Link/esl.c: In function ‘lava_flush_buffer’:
/root/Ether-Serial_Link/esl.c:1367: error: request for member ‘write_wakeup’ in something not a structure or union
/root/Ether-Serial_Link/esl.c:1368: error: request for member ‘write_wakeup’ in something not a structure or union
/root/Ether-Serial_Link/esl.c: In function ‘lava_init’:
/root/Ether-Serial_Link/esl.c:1863: error: ‘TTY_DRIVER_NO_DEVFS’ undeclared (first use in this function)
/root/Ether-Serial_Link/esl.c:1866: warning: assignment from incompatible pointer type
/root/Ether-Serial_Link/esl.c:1867: warning: assignment from incompatible pointer type
make[2]: *** [/root/Ether-Serial_Link/esl.o] Error 1
make[1]: *** [_module_/root/Ether-Serial_Link] Error 2

---

