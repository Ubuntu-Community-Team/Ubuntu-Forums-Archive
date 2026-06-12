---
title: "Working with debugging libstdc++"
date: 2011-10-20
forum: Ubuntu Dev Link Forum
---

### Post by delcypher on 2011-10-20
Hi I have just installed the libstdc++6-4.5-dbg package and I wondering how am I supposed to convince gdb to use the correct libraries

The libstdc++ library with nodebugging symbols is installed at

/usr/lib/x86_64-linux-gnu/libstdc++.so.6

and the debugging version is at /usr/lib/x86_64-linux-gnu/debug/libstdc++.so.6


When I run a compiled program built with debugging symbols like so
```
gdb a.out
(gdb) b main
(gdb) info sharedlibrary
From                To                  Syms Read   Shared Object Library
0x00007ffff7ddcaf0  0x00007ffff7df5a66  Yes (*)     /lib64/ld-linux-x86-64.so.2
0x00007ffff7b2dd60  0x00007ffff7b98906  Yes (*)     /usr/lib/x86_64-linux-gnu/libstdc++.so.6
0x00007ffff7854ef0  0x00007ffff7895a18  Yes         /lib/x86_64-linux-gnu/libm.so.6
0x00007ffff763d8b0  0x00007ffff764cf78  Yes         /lib/x86_64-linux-gnu/libgcc_s.so.1
0x00007ffff72c5c00  0x00007ffff73e27ec  Yes         /lib/x86_64-linux-gnu/libc.so.6
(*): Shared library is missing debugging information.
(gdb) show debug-file-directory 
The directory where separate debug symbols are searched for is "/usr/lib/debug".

```

I can see gdb hasn't loaded the debugging library. But the directory that symbols are searched for is seems set correctly because if I change it to
```
(gdb) set debug-file-directory usr/lib/x86_64-linux-gnu/debug/
```

then gdb can't find the symbols
```

(gdb) info sharedlibrary 
From                To                  Syms Read   Shared Object Library
0x00007ffff7ddcaf0  0x00007ffff7df5a66  Yes (*)     /lib64/ld-linux-x86-64.so.2
0x00007ffff7b2dd60  0x00007ffff7b98906  Yes (*)     /usr/lib/x86_64-linux-gnu/libstdc++.so.6
0x00007ffff7854ef0  0x00007ffff7895a18  Yes (*)     /lib/x86_64-linux-gnu/libm.so.6
0x00007ffff763d8b0  0x00007ffff764cf78  Yes (*)     /lib/x86_64-linux-gnu/libgcc_s.so.1
0x00007ffff72c5c00  0x00007ffff73e27ec  Yes (*)     /lib/x86_64-linux-gnu/libc.so.6

```

The only way I've got this to work is to do
```

LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu/debug/ gdb a.out
(gdb) b main
Breakpoint 1 at 0x40086c: file test.cpp, line 6.
(gdb) run
Starting program: /homes/dsl11/exercises/a.out 

Breakpoint 1, main () at test.cpp:6
6		ostream& myCout = cout;
(gdb) info sharedlibrary 
From                To                  Syms Read   Shared Object Library
0x00007ffff7ddcaf0  0x00007ffff7df5a66  Yes (*)     /lib64/ld-linux-x86-64.so.2
0x00007ffff7b0fbb0  0x00007ffff7b90096  Yes         /usr/lib/x86_64-linux-gnu/debug/libstdc++.so.6
0x00007ffff782def0  0x00007ffff786ea18  Yes         /lib/x86_64-linux-gnu/libm.so.6
0x00007ffff76168b0  0x00007ffff7625f78  Yes         /lib/x86_64-linux-gnu/libgcc_s.so.1
0x00007ffff729ec00  0x00007ffff73bb7ec  Yes         /lib/x86_64-linux-gnu/libc.so.6
(*): Shared library is missing debugging information.

```

Is it intentional that in order to be able to use debugging versions of the libstdc++ that I use the LD_LIBRARY_PATH environmental variable or am I missing something?

---

