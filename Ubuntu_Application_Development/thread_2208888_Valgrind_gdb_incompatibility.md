---
title: "Valgrind gdb incompatibility"
date: 2014-03-02
forum: Ubuntu Application Development
---

### Post by nibal on 2014-03-02
I have installed valgrind to Ubuntu 12.04 x64. Also have gcc and gdb. My .valgrinrc file is:

```


--leak-check=full
--malloc-fill=AB
--free-fill=CD
--show-below-main=yes
--db-attach=yes
--read-var-info=yes
--num-callers=40
--track-origins=yes


```

I clearly state to attach gdb. When I run it, though, It prompts for "Attach to debugger?", but never really stops or raises gdb and continues till the end :-(
In valgrind forums i have read that it could be a kernel problem, but before taking any drastic measures, I would like to ask here as well.

TIA,
Nikos

---

### Post by Toliot on 2014-03-13
If your using ubuntu all you need to do is "sudo apt-get install build-essential" to get gcc(I believe, please correct me if I'm wrong) as well as a bunch of other compilers designed for software development.

If your pressed on using valgrind(the way I use it at least), I recommend you compile the file and then run through valgrind. ex. ```
"make ex1" "valgrind ./ex1"
```

Sorry on late reply from the forums, I wanted to jump start your thread(because I might be wrong).

---

### Post by nibal on 2014-03-13
> **Toliot said:**
> If your using ubuntu all you need to do is "sudo apt-get install build-essential" to get gcc(I believe, please correct me if I'm wrong) as well as a bunch of other compilers designed for software development.

If your pressed on using valgrind(the way I use it at least), I recommend you compile the file and then run through valgrind. ex. 

As already mentioned, I already have gcc. gdb, flex, bison, runlib and several other assemblers ;-). I am also an experienced valgrind user,
having successfully attached gdb to it in the past many times. Unfortunately not this time :-( I have also made valgrind from sources, to no result.

 > Sorry on late reply from the forums, I wanted to jump start your thread(because I might be wrong).

Much appreciated ;-) I have also asked valgrind forums, they seem to say that it may be a kernel problem. Just wanted to xcheck here, too.

---

### Post by nibal on 2014-07-19
It turns out that after many failed attempts of valgrind to attach gdb, it just started actually trying to do it. I got no gdb yet, but at least i have some warnings and progress.

It turns this is another Ubuntu hack... Missdirected security...:-( 
And well documented, too. It took me 4 mos to discover it and i only did so by accident.

Anyway, to attach a debugger to a valgrind session, you need to relax kernel.yama.ptrace_scope from "1" to "0" in /etc/sysctl.d/ptrace_scope.conf.
I did that. Now I am getting:

> 
Failed to read a valid object file image from memory.
81	../sysdeps/unix/syscall-template.S: No such file or directory.


Anyone knows where can i get this image from?

TIA

---

