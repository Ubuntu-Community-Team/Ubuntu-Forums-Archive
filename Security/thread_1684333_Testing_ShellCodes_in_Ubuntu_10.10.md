---
title: "Testing ShellCodes in Ubuntu 10.10"
date: 2011-02-09
forum: Security
---

### Post by lionaneesh on 2011-02-09
Hello all,

I am learning exploit development and learning some stuff about shellcodes now!!The shellcode is absolutely right and have tested it...

I am using the following code...(created by me) to run my shellcode..

```
// #include<stdio.h> we will not be needing this as we are not using any functions from the C library...Just basic logic of Pointers..

char shellcode[] = "\x31\xc0\xb0\x01\x31\xdb\xb3\x07\xcd\x80"; // basic exit shellcode
int main()
{
        int *ret; // a simple integer pointer pointing a address
        ret = (int *)&ret + 2; // change the address pointed by
        (*ret) = (int)shellcode;
}
```

Compiling :-

```

aneesh@aneesh-laptop:~/articles/C$ gcc test.c -o test -fno-stack-protector

```

Compiling gives no errors as expected..

Now the problem I am facing is that :-

As i run the program :-

```

aneesh@aneesh-laptop:~/articles/C$ ./test 
Segmentation fault

```

Strace output :-

```

aneesh@aneesh-laptop:~/articles/C$ strace ./test 
execve("./test", ["./test"], [/* 37 vars */]) = 0
brk(0)                                  = 0x9e3a000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7816000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=81274, ...}) = 0
mmap2(NULL, 81274, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7802000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000m\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1405508, ...}) = 0
mmap2(NULL, 1415592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xe0a000
mprotect(0xf5d000, 4096, PROT_NONE)     = 0
mmap2(0xf5e000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x153) = 0xf5e000
mmap2(0xf61000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xf61000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7801000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb78016c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xf5e000, 8192, PROT_READ)     = 0
mprotect(0x8049000, 4096, PROT_READ)    = 0
mprotect(0x15c000, 4096, PROT_READ)     = 0
munmap(0xb7802000, 81274)               = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Segmentation fault

```

I have some feeling that its because the program has no access to the memory containing the shellcode (May be???:p:p:p)..

I just want to know how to fix this...:confused::confused:

---

### Post by rookcifer on 2011-02-10
It's probably mmap ASLR in your way.  It could also be a number of other ASLR/PIE features.  See [this page]("https://wiki.kubuntu.org/Security/Features/Historical") for a list of built-in security features. Some you can disable at compile time, and some you cannot.

---

### Post by ryanfx on 2011-02-26
the NX bit is set and is disabling execution of data from the stack.  Compile your program with the -z execstack flag.

---

