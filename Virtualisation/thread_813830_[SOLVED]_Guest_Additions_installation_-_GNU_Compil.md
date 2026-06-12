---
title: "[SOLVED] Guest Additions installation - GNU Compiler Question"
date: 2008-05-31
forum: Virtualisation
---

### Post by animefan82 on 2008-05-31
```

VirtualBox 1.6.0 Guest Additions installation
Please install the GNU compiler.

```

Which GNU Compiler is it talking aboot? I can do it the fast way and install every GNU Compilier in synaptic, but what an overkill that is...

So, what has to be searched for/marked in Synaptic for Guest Additions to install?

Much appreciated.

---

### Post by bradmkjr on 2008-05-31
Assuming you are on Ubuntu this may help. It may be overkill, but pretty sure it will do any compiling you will need:

apt-get install linux-headers-`uname -r` build-essential

apt-get install gcc binutils-doc cpp-doc make manpages-dev autoconf automake1.9 libtool flex bison gdb libc6-dev-amd64 lib64gcc1

copied from: [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

Good Luck,
Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

### Post by animefan82 on 2008-06-01
And so, now I know which compiler Guest installation was talking about.

it was gcc - in full it's "The GNU C Compiler" - something that isn't entirely obvious, since there are a LOT of different GNU Compilers... C, C++, C#, Java and so on. I'll still overkill the guest system with the different compilers, in case I'll need them.

---

