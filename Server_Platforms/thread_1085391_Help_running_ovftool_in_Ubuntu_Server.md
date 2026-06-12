---
title: "Help running ovftool in Ubuntu Server"
date: 2009-03-03
forum: Server Platforms
---

### Post by shebangs on 2009-03-03
Using vmbuilder, Im spitting out a nice ESXi Image.

I now want to create an additional 'OVF' Compliant Image.   


I went to [VMWares]("http://www.vmware.com/download/eula/ovf_eula.html") site, downloaded it and extracted it.   

However, it doesn't want to run.  Any ideas?


```

# uname -a
Linux emp1hudsonpin02 2.6.27-7-server #1 SMP Fri Oct 24 07:20:47 UTC 2008 x86_64 GNU/Linux
# 
# ./ovftool
./ovftool: line 29: ./ovftool.bin: No such file or directory
# 
# ./ovftool.bin 
-su: ./ovftool.bin: No such file or directory
# 
# ls -l
total 50176
drwxr-xr-x 2 root root     4096 2008-09-16 00:23 env
-rw-rw---- 1 root root  1092496 2008-09-16 00:23 libcrypto.so.0.9.7
-rw-rw---- 1 root root  2406896 2008-09-16 00:23 libovfConverter.so.1.0
-rw-rw---- 1 root root   199840 2008-09-16 00:23 libssl.so.0.9.7
-rw-rw---- 1 root root 38107256 2008-09-16 00:23 libtypes.so
-rw-rw---- 1 root root  1202980 2008-09-16 00:23 libvixDiskLib.so.1
-rw-rw---- 1 root root  4557228 2008-09-16 00:23 libvmacore.so
-rw-rw---- 1 root root  2951580 2008-09-16 00:23 libvmomi.so
-rwxr-xr-x 1 root root      549 2008-09-16 00:23 ovftool
-rwxr-xr-x 1 root root    39288 2008-09-16 00:23 ovftool.bin
-r--r--r-- 1 root root   712709 2008-09-16 00:23 ovftool.pdf
-r--r--r-- 1 root root     1267 2008-09-16 00:23 README.txt

```

---

### Post by shebangs on 2009-03-10
The problem was that I was running it on a 64bit version of Ubuntu.  I needed to install the 32bit libs.

---

