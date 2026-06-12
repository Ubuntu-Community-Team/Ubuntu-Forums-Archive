---
title: "How to disable NX? /proc/sys/kernel/exec-shield gone and execstack -s not working"
date: 2012-03-23
forum: Security
---

### Post by evdk on 2012-03-23
Dear all,

I'm teaching a course where students learn security by doing hacks in a protected environment, including shellcode injection. This means I have to disable some of the security features in Ubuntu.

Last year I was using Ubuntu 10.10 Server (32-bit) and the following (along with some compiler switches) did the trick:

echo 0 | sudo tee /proc/sys/kernel/randomize_va_space
echo 0 | sudo tee /proc/sys/kernel/exec-shield

Now I'm using Ubuntu 11.10 Server (32-bit) and the exec-shield file no longer exists, which means I can't disable NX system-wide. Does anyone know the replacement? Is it still possible to disable it? Or do I need to recompile the kernel? In the latter case, what would be the best way to disable it.

I've also tried specifically disabling no-execute on the binaries that need to be exploited using "execstack -s", which does not give any error messages but doesn't fix the problem either. I can see in GDB that the correct shellcode has been injected and jumped to, but the first instruction there causes a segfault.

Thanks for any answers!

---

### Post by evdk on 2012-03-23
It turns out I posted a bit too early, with some more experimentation I did find the solution. It turns out "-z execstack" is also needed as a compiler switch nowadays (it wasn't on 10.10).

If anyone needs it, use these compiler switches (in addition to disabling ASLR as described in the original post) to create an easily exploitable binary:

-fno-stack-protector -z execstack -mpreferred-stack-boundary=2

---

