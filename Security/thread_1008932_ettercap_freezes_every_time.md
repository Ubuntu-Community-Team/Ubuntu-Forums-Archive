---
title: "ettercap freezes every time"
date: 2008-12-12
forum: Security
---

### Post by go_beep_yourself on 2008-12-12
I have ettercap-gtk installed from the repositories in ubuntu ibex 64-bit. Each time I run it, go to unified sniffing and choose eth0, it locks up. Since that didn't work, I tried to compile it from source, but that gave me errors when running make. Running the configure script didn't give me any errors. Any ideas how to get it working?

errors from running make:
```
ces.Po"; else rm -f ".deps/ettercap-ec_interfaces.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include    -O2 -funroll-loops -fomit-frame-pointer -Wall      -g -O2 -MT ettercap-ec_log.o -MD -MP -MF ".deps/ettercap-ec_log.Tpo" -c -o ettercap-ec_log.o `test -f 'ec_log.c' || echo './'`ec_log.c; \
	then mv -f ".deps/ettercap-ec_log.Tpo" ".deps/ettercap-ec_log.Po"; else rm -f ".deps/ettercap-ec_log.Tpo"; exit 1; fi
ec_log.c: In function ‘log_packet’:
ec_log.c:248: warning: pointer targets in passing argument 2 of ‘regexec’ differ in signedness
ec_log.c: In function ‘log_write_info’:
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
ec_log.c:491: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
In function ‘open’,
    inlined from ‘log_open’ at ec_log.c:193:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[2]: *** [ettercap-ec_log.o] Error 1
make[2]: Leaving directory `/tmp/ettercap-NG-0.7.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/ettercap-NG-0.7.3/src'
make: *** [all-recursive] Error 1
```

ettercap-gtk package from repo freezing each time I use it:
[IMG]http://img525.imageshack.us/img525/5272/screenshotettercapng073gt1.png[/IMG]

---

### Post by Cocoabean on 2009-02-06
This fixed it for me
[http://www.hacktoolrepository.com/tool/31/Ettercap](http://www.hacktoolrepository.com/tool/31/Ettercap)

---

### Post by Eviltechie on 2009-02-22
I tried that, and it still locks up.

---

### Post by forgewire on 2010-07-14
same problem

---

### Post by yeleek on 2010-07-14
Depends what you want it for...

Could run ettercap from BT4 via a VM?

or if you just want to arpspoof try dsniff?

---

### Post by forgewire on 2010-07-15
> **yeleek said:**
> Depends what you want it for...

Could run ettercap from BT4 via a VM?

or if you just want to arpspoof try dsniff?

I never knew that to run Ettercap on Ubuntu I need BT4 and VM.
arpspoof is very noisy and can bring whole network down because you can't exit it gracefully
I just use ettercap in a text mode because its GUI doesn't work

---

### Post by yeleek on 2010-07-15
You don't need to run it in BT4, but if you can't get it to work in ubuntu, try running it in BT4 in a vm.  

I've done this previously and its worked fine.

---

### Post by forgewire on 2010-07-15
How VM supposed to emulate my PCMCIA wifi card?
It's better to run BT from live CD then

---

### Post by yeleek on 2010-07-15
Neither Vmware or Vbox OSE support PCMCIA natively.

Guess you'll have to stick with cmd line or use a cd then won't you.

---

### Post by forgewire on 2010-07-15
> **yeleek said:**
> Neither Vmware or Vbox OSE support PCMCIA natively.

Guess you'll have to stick with cmd line or use a cd then won't you.

Great! Whats the point then?

---

### Post by bumr055 on 2010-07-18
I seem to be having the same problem.. I don't know why all of a sudden it's freezing up... Has always worked fine up until a couple days ago.  Freezes after I confirm my NIC(eth1) when going to Sniff>Unified.  I can get it to run with BT4 on my other PC but I would like to have it working again with this machine under Ubuntu, as it's always up and running.

Reinstall didn't do anything, So it's probably my machine.

EDIT: Must be a problem with my GTK, Curses works fine.

---

