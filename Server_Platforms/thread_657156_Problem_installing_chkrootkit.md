---
title: "Problem installing chkrootkit"
date: 2008-01-03
forum: Server Platforms
---

### Post by Ertai87 on 2008-01-03
So I tried installing chkrootkit yesterday, and I ran it, and everything looked OK, but something's been bugging me.  I did everything in the instructions, but I got a bunch of errors.  This is the error output:

chklastlog.c:37:19: error: stdio.h: No such file or directory
chklastlog.c:39:20: error: stdlib.h: No such file or directory
chklastlog.c:41:22: error: sys/stat.h: No such file or directory
chklastlog.c:42:20: error: unistd.h: No such file or directory
chklastlog.c:43:20: error: string.h: No such file or directory
chklastlog.c:44:20: error: signal.h: No such file or directory
chklastlog.c:45:17: error: pwd.h: No such file or directory
chklastlog.c:46:23: error: sys/types.h: No such file or directory
chklastlog.c:47:18: error: utmp.h: No such file or directory
chklastlog.c:49:21: error: lastlog.h: No such file or directory
chklastlog.c:51:22: error: sys/file.h: No such file or directory
chklastlog.c:75: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wtmp_file_size’
chklastlog.c:76: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
chklastlog.c:81: error: expected specifier-qualifier-list before ‘uid_t’
chklastlog.c:86: warning: ‘struct utmp’ declared inside parameter list
chklastlog.c:86: warning: its scope is only this definition or declaration, which is probably not what you want
chklastlog.c:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
chklastlog.c:91: error: expected declaration specifiers or ‘...’ before ‘uid_t’
chklastlog.c: In function ‘main’:
chklastlog.c:98: error: storage size of ‘lastlog_ent’ isn’t known
chklastlog.c:99: error: storage size of ‘utmp_ent’ isn’t known
chklastlog.c:104: error: storage size of ‘wtmp_stat’ isn’t known
chklastlog.c:106: error: ‘uid_t’ undeclared (first use in this function)
chklastlog.c:106: error: (Each undeclared identifier is reported only once
chklastlog.c:106: error: for each function it appears in.)
chklastlog.c:106: error: ‘uid’ undeclared (first use in this function)
chklastlog.c:109: warning: incompatible implicit declaration of built-in function ‘memcpy’
chklastlog.c:130: error: ‘SIGALRM’ undeclared (first use in this function)
chklastlog.c:135: error: ‘O_RDONLY’ undeclared (first use in this function)
chklastlog.c:136: warning: incompatible implicit declaration of built-in function ‘fprintf’
chklastlog.c:136: error: ‘stderr’ undeclared (first use in this function)
chklastlog.c:141: warning: incompatible implicit declaration of built-in function ‘fprintf’
chklastlog.c:151: error: ‘wtmp_file_size’ undeclared (first use in this function)
chklastlog.c:155: error: invalid application of ‘sizeof’ to incomplete type ‘struct utmp’ 
chklastlog.c:156: error: invalid application of ‘sizeof’ to incomplete type ‘struct utmp’ 
chklastlog.c:158: warning: incompatible implicit declaration of built-in function ‘fprintf’
chklastlog.c:162: error: type of formal parameter 1 is incomplete
chklastlog.c:163: error: ‘NULL’ undeclared (first use in this function)
chklastlog.c:167: warning: incompatible implicit declaration of built-in function ‘fprintf’
chklastlog.c:168: warning: incompatible implicit declaration of built-in function ‘exit’
chklastlog.c:173: error: invalid application of ‘sizeof’ to incomplete type ‘struct lastlog’ 
chklastlog.c:174: error: invalid application of ‘sizeof’ to incomplete type ‘struct lastlog’ 
chklastlog.c:176: error: invalid application of ‘sizeof’ to incomplete type ‘struct lastlog’ 
chklastlog.c:178: warning: incompatible implicit declaration of built-in function ‘fprintf’
chklastlog.c:183: error: too many arguments to function ‘getslot’
chklastlog.c:184: warning: incompatible implicit declaration of built-in function ‘printf’
chklastlog.c:185: error: ‘struct s_localpwd’ has no member named ‘uname’
chklastlog.c:186: error: ‘struct s_localpwd’ has no member named ‘uname’
chklastlog.c: At top level:
chklastlog.c:207: warning: ‘struct utmp’ declared inside parameter list
chklastlog.c:207: error: parameter 1 (‘utmp_ent’) has incomplete type
chklastlog.c: In function ‘read_status’:
chklastlog.c:220: error: ‘wtmp_file_size’ undeclared (first use in this function)
chklastlog.c:223: warning: incompatible implicit declaration of built-in function ‘printf’
chklastlog.c: In function ‘read_pwd’:
chklastlog.c:237: warning: assignment makes pointer from integer without a cast
chklastlog.c:241: warning: incompatible implicit declaration of built-in function ‘malloc’
chklastlog.c:241: error: ‘size_t’ undeclared (first use in this function)
chklastlog.c:241: error: expected ‘)’ before ‘sizeof’
chklastlog.c:243: error: ‘struct s_localpwd’ has no member named ‘uid’
chklastlog.c:243: error: ‘uid_t’ undeclared (first use in this function)
chklastlog.c:243: error: expected expression before ‘)’ token
chklastlog.c:244: error: ‘struct s_localpwd’ has no member named ‘uname’
chklastlog.c:244: error: expected ‘)’ before ‘numentries’
chklastlog.c:246: error: ‘struct s_localpwd’ has no member named ‘uname’
chklastlog.c:246: error: expected ‘)’ before numeric constant
chklastlog.c:250: warning: assignment makes pointer from integer without a cast
chklastlog.c:251: error: ‘struct s_localpwd’ has no member named ‘uid’
chklastlog.c:251: error: dereferencing pointer to incomplete type
chklastlog.c:252: warning: incompatible implicit declaration of built-in function ‘memcpy’
chklastlog.c:252: error: ‘struct s_localpwd’ has no member named ‘uname’
chklastlog.c:252: error: dereferencing pointer to incomplete type
chklastlog.c:252: warning: incompatible implicit declaration of built-in function ‘strlen’
chklastlog.c:252: error: dereferencing pointer to incomplete type
chklastlog.c:252: error: dereferencing pointer to incomplete type
chklastlog.c: In function ‘free_results’:
chklastlog.c:261: error: ‘struct s_localpwd’ has no member named ‘uid’
chklastlog.c:263: error: ‘struct s_localpwd’ has no member named ‘uname’
chklastlog.c:265: error: ‘struct s_localpwd’ has no member named ‘uname’
chklastlog.c: At top level:
chklastlog.c:269: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
chklastlog.c:282: error: expected declaration specifiers or ‘...’ before ‘uid_t’
chklastlog.c: In function ‘getslot’:
chklastlog.c:288: error: ‘struct s_localpwd’ has no member named ‘uid’
chklastlog.c:288: error: ‘uid’ undeclared (first use in this function)
make: *** [chklastlog] Error 1

Anyone know what the cause of these errors are and if I should fix it or be concerned?  Thanks.

---

### Post by Ertai87 on 2008-01-04
Bump.  Anyone know about this?

---

### Post by kevdog on 2008-01-04
Are you having problems compiling this program?? Take for example this line in your output:

chklastlog.c:37:19: error: stdio.h: No such file or directory

this would suggest your linux-header files package is not installed:

sudo aptitude install linux-headers-`uname -r`

---

### Post by Ertai87 on 2008-01-04
Should it be installed by default?  If not, I haven't installed it.  If so, I've had some other weird issues with my comp up till this point, so it would just add to the questions I already have about this install...

I asked a friend of mine about the problem and he told me I had to install a package called build-essential, which apparently I didn't have (I don't quite know why I wouldn't have it).  I installed it and now the output is:

gcc -DHAVE_LASTLOG_H -o chklastlog chklastlog.c
gcc -DHAVE_LASTLOG_H -o chkwtmp chkwtmp.c
chkwtmp.c: In function &#8216;main&#8217;:
chkwtmp.c:95: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
gcc -DHAVE_LASTLOG_H   -D_FILE_OFFSET_BITS=64 -o ifpromisc ifpromisc.c
gcc  -o chkproc chkproc.c
gcc  -o chkdirs chkdirs.c
gcc  -o check_wtmpx check_wtmpx.c
gcc -static  -o strings-static strings.c
gcc  -o chkutmp chkutmp.c

This looks normal, except for the warning.  Should I mark the thread solved, or am I still missing something?

---

### Post by kevdog on 2008-01-05
Im not familar with compiling this product, however if you do a 

./configure <whatever parameters you need here>
make clean
make 
make check

If there a checks in the package (many do not), it will basically tell you the product is functioning as expected.  If the author didnt include any make checks, then you are kind of stuck.  Just my general perspective however, Ive installed a lot of packages that gave me warnings without any problems.  As long as I didnt get any errors I went ahead and installed the package with sudo make install.  I haven't run into any problems with this philosophy, however I not really a programmer, so I cant tell you the repercussions of using this approach.  Your particular warning message seems fairly benign however.

---

