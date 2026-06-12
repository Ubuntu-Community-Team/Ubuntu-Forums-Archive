---
title: "Snort Install Problems"
date: 2009-02-04
forum: Security
---

### Post by eNdeRam on 2009-02-04
I have been trying to compile and install snort for the past couple hours but I'm getting some errors that I just don't know how to overcome. I keep getting stuck at the make portion of the install.

The lines of error I'm getting are as follows (copied and pasted from command line):

```
In function ‘open’,
    inlined from ‘server_stats_save’ at server_stats.c:349:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[4]: *** [server_stats.o] Error 1
make[4]: Leaving directory `/usr/local/src/snort-2.8.3.2/src/preprocessors/flow/portscan'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/usr/local/src/snort-2.8.3.2/src/preprocessors/flow'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/snort-2.8.3.2/src/preprocessors'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/snort-2.8.3.2/src'
make: *** [install-recursive] Error 1
```

I don't know if that would help anyone help me solve my problem but i just posted the "error message" just in case.

I can't seem to figure out whats wrong please help me.

---

### Post by The Tronyx on 2009-02-05
Hello,

Could you please provide us with the ./configure string you are using?  Are you using the Snort/BASE tutorial that is stickied in the forums?  Thanks!

---

### Post by eNdeRam on 2009-02-05
the ./configure string that i am using is:

```
./configure --with-mysql --enable-dynamicplugin
```

The version of ubuntu i am using is intrepid ibex and yes i am using the tutorial stickied in this forum

also i didn't extract the rules that i'm going to use yet
does it matter?

edit...
ok so i resolved this matter by myself

I think the problem laid in where I didn't use the sudo prefix when issuing the "make && make install" command

---

