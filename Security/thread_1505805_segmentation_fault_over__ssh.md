---
title: "segmentation fault over  ssh"
date: 2010-06-09
forum: Security
---

### Post by eotakos on 2010-06-09
Hello everyone!,

I'm trying to run a program of mine remotely on a ubuntu system over ssh, and I get a segmentation fault... there must be some kind of restrictions to memory usage over ssh (or something similar), because some other programs that I ran over ssh and execute on the gpu worked just fine.

Is there a certain group that I should put myself into so that I can get past these restrictions?

Any advice or suggestions are very welcome,

thank you in advance

---

### Post by anomie on 2010-06-09
What program? Does it require X11? (If so, have you forwarded X11 over ssh?) 

If push comes to shove, you can observe where it's bombing with strace(1).

---

### Post by eotakos on 2010-06-09
it is a g++ program, all it does is write to a file, and display 2 lines of output on the console

>  If push comes to shove, you can observe where it's bombing with strace(1) 
I lost you there....

EDIT: ok, my english weren't ready for this... it took me some time, but ... yeah!

thanks for replying

---

### Post by anomie on 2010-06-09
Did you write the program? I'm not super well versed in [gdb](http://www.gnu.org/software/gdb/), but it may be worth your while to familiarize yourself if you're going to be doing some development. 

For a sufficiently simple program, I'd probably just build in my own "debugging", though. :) (e.g. Different values to stdout to indicate where my program was when it croaked.) 

More about strace: [http://people.gnome.org/~newren/tutorials/developing-with-gnome/html/ch03s02.html](http://people.gnome.org/~newren/tutorials/developing-with-gnome/html/ch03s02.html)

---

### Post by eotakos on 2010-06-09
> For a sufficiently simple program, I'd probably just build in my own "debugging", though.  (e.g. Different values to stdout to indicate where my program was when it croaked.) 
Thanks for the tip! I never thought about debugging because it works... you know, locally - it is a great idea to see where exactly things go wrong... 

I will do that - thanks again!

---

### Post by eotakos on 2010-06-10
well, I tried strace, and as it seems, there are libraries that the program is looking for and it can't find!, that's odd, because the .cpp file is compiled on that same system!(through ssh)

...and I wouldn't say that something about path is going wrong through ssh, because as i've already mentioned, other programs are running just fine!](*,)

I just include the output of strace in case I misunderstood something about it...

```
execve("./a.out", ["./a.out"], [/* 21 vars */]) = 0
brk(0)                                  = 0x19d7000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f041dea2000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f041dea0000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/usr/local/lib/tls/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/tls/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib/tls/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/tls", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/local/lib64/tls/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64/tls/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/tls/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64/tls", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/lib64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/tls/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/cuda/lib64/tls/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/tls/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/cuda/lib64/tls", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/cuda/lib64/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/local/cuda/lib64", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/tls/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/tls", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/x86_64/libstdc++.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64", 0x7fff1954b8b0) = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240h\5\0\0\0\0\0@"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1023448, ...}) = 0
mmap(NULL, 3195704, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f041d977000
mprotect(0x7f041da68000, 2097152, PROT_NONE) = 0
mmap(0x7f041dc68000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf1000) = 0x7f041dc68000
mmap(0x7f041dc71000, 74552, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f041dc71000
close(3)                                = 0
open("/usr/local/lib/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libm.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/usr/lib64/tls/x86_64/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib64/tls/x86_64", 0x7fff1954b880) = -1 ENOENT (No such file or directory)
open("/usr/lib64/tls/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib64/tls", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib64/x86_64/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib64/x86_64", 0x7fff1954b880) = -1 ENOENT (No such file or directory)
open("/usr/lib64/libm.so.6", O_RDONLY)  = -1 ENOENT (No such file or directory)
stat("/usr/lib64", {st_mode=S_IFDIR|0755, st_size=65536, ...}) = 0
open("tls/x86_64/libm.so.6", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/libm.so.6", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("x86_64/libm.so.6", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("libm.so.6", O_RDONLY)             = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=91618, ...}) = 0
mmap(NULL, 91618, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f041de89000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libm.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P>\0\0\0\0\0\0@"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=542928, ...}) = 0
mmap(NULL, 2638040, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f041d6f2000
mprotect(0x7f041d776000, 2093056, PROT_NONE) = 0
mmap(0x7f041d975000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x83000) = 0x7f041d975000
close(3)                                = 0
open("/usr/local/lib/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib64/tls/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib64/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/x86_64/libgcc_s.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/libgcc_s.so.1", O_RDONLY)     = -1 ENOENT (No such file or directory)
open("x86_64/libgcc_s.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("libgcc_s.so.1", O_RDONLY)         = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`,\0\0\0\0\0\0@"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=96560, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f041de88000
mmap(NULL, 2192376, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f041d4da000
mprotect(0x7f041d4f0000, 2097152, PROT_NONE) = 0
mmap(0x7f041d6f0000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7f041d6f0000
close(3)                                = 0
open("/usr/local/lib/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/local/cuda/lib64/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libc.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/usr/lib64/tls/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib64/libc.so.6", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/x86_64/libc.so.6", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/libc.so.6", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("x86_64/libc.so.6", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("libc.so.6", O_RDONLY)             = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\346\1\0\0\0\0\0@"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1502512, ...}) = 0
mmap(NULL, 3609240, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f041d168000
mprotect(0x7f041d2d0000, 2097152, PROT_NONE) = 0
mmap(0x7f041d4d0000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x168000) = 0x7f041d4d0000
mmap(0x7f041d4d5000, 17048, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f041d4d5000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f041de87000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f041de86000
arch_prctl(ARCH_SET_FS, 0x7f041de86700) = 0
open("/dev/urandom", O_RDONLY)          = 3
read(3, "\325_\351\367\364\250\334"..., 7) = 7
close(3)                                = 0
mprotect(0x7f041d4d0000, 16384, PROT_READ) = 0
mprotect(0x7f041d6f0000, 4096, PROT_READ) = 0
mprotect(0x7f041d975000, 4096, PROT_READ) = 0
mprotect(0x7f041dc68000, 28672, PROT_READ) = 0
mprotect(0x608000, 4096, PROT_READ)     = 0
mprotect(0x7f041dea3000, 4096, PROT_READ) = 0
munmap(0x7f041de89000, 91618)           = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
```


any ideas?...


EDIT: well this got out of the context of "security discussion"... but what should i do(?)...

---

### Post by Peter09 on 2010-06-10
One of the things that should be checked when a program works in one context but not another is environment variables. It is most likly that when logging in with ssh you have a different environment setup that when you are logged in locally.

---

### Post by anomie on 2010-06-10
Just for grins, I'd be curious to see output from: 

**Log in locally (i.e. physically at the host)**
```
$ env > local.env
```

**Log in over ssh**
```
$ env > ssh.env
$ diff -u local.env ssh.env
```

-------

P.S. If you're seeing different strace output related to libraries, you may want to examine LD_LIBRARY_PATH in particular.

---

### Post by eotakos on 2010-06-10
Thank you very much for your responses!...

Tomorrow I'll be going locally to the pc in question, so I'll post the output then.

Even more strange is that (over ssh) the output of ```
echo $LD_LIBRARY_PATH
``` is as expected...

while the output of ```
echo $PATH
``` is even more enhanced than when local. what I mean is: this is the output oven ssh:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/cuda/bin:/home/panag/bin:/usr/local/pgplot/:/opt/intel/Compiler/11.1/059/bin/:/usr/local/cuda/bin:/opt/intel/Compiler/11.1/059/bin/intel64/

```

while this is the content of the file /etc/environment
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/cuda/bin"

```


fancy that!

---

### Post by eotakos on 2010-06-11
I am truly sorry for wasting your time, I feel such a jerk...

it turns out that the minor changes I did to my program resulted into failure to allocate the extra static memory, and that was it. The program wouldn't run locally either.

I usually get a stack overflow message or something like that in cases like this... and even strace's messages were completely irrelevant..

I don't know what to say -

---

### Post by Peter09 on 2010-06-12
It gets us all occasionally :p

---

