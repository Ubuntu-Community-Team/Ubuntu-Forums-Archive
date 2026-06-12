---
title: "Configuring AppArmor and adding ability to bind to &lt; 1024 port for non-root user"
date: 2011-05-18
forum: Security
---

### Post by denis077 on 2011-05-18
Hello all,

Could you pleas help me to solve the following problem:
A create an application which has to bind to port less than 1024 and must be launched under non-root user. OS: Ubuntu 10.04.

Decision 1: Using a firewall to redirect packets.
Problem:    This decision is not good for me. I need simple way to solve the problem.

Decision 2: Use CAP_NET_BIN_SERVICE.
Problem:    My execution file has 2,7G size. It is very big application with a lot of debug info. setcat command return an error:
**setcap cap_net_bind_service+ep ./test.x**
[I]Failed to set capabilities on file `./test.x' (Value too large for defined data type)
usage: setcap [-q] [-v] (-r|-|<caps>) <filename> [ ... (-r|-|<capsN>) <filenameN> ]

 Note <filename> must be a regular (non-symlink) file. [/I]
**ll test.x**
*-rwxr-xr-x 1 root root 2717254066 Apr 13 12:25 test.x*

Decision 3: Use AppArmor.
Problem: I've create profile for my program and add capability net_bind_service to config file, but my application cannot bind.

Could you please help me to configure AppArmor?

Thanks,
Denis

---

### Post by denis077 on 2011-05-18
Is it possible to add ability to bind to port<1024 for non-root user using AppArmor?

---

