---
title: "Skype not working after recent updates"
date: 2013-03-12
forum: Ubuntu Development Version
---

### Post by alphacrucis2 on 2013-03-12
I notice that raring updates over the last few days or so seemed to have killed skype stone dead (64bit raring). Running from terminal it immediately gets 

Segmentation fault (core dumped)

Does any one else see this?

---

### Post by geojorg on 2013-03-12
Yes.

Downgrade libqtwebkit4 to 2.2.1-4ubuntu1 to solve it.

---

### Post by Hells_Dark on 2013-03-13
Can someone post the exact command to solve it ?

---

### Post by vaskark on 2013-03-13
> **geojorg said:**
> Yes.

Downgrade libqtwebkit4 to 2.2.1-4ubuntu1 to solve it.
I'm having the same problem with Skype. But I can't seem to downgrade that package in synaptic - no other package is listed. I have all repos enabled except raring-proposed, which I had to disable to solve a kernel conflict.

---

### Post by Hells_Dark on 2013-03-13
> **vaskark said:**
> I'm having the same problem with Skype. But I can't seem to downgrade that package in synaptic - no other package is listed. I have all repos enabled except raring-proposed, which I had to disable to solve a kernel conflict.
Same issue here :(

maybe we can download the lib somewhere ?

trying here : [https://launchpad.net/ubuntu/raring/i386/libqtwebkit4/2.2.1-4ubuntu1](https://launchpad.net/ubuntu/raring/i386/libqtwebkit4/2.2.1-4ubuntu1) (32b)

It worked.

---

### Post by swex on 2013-03-16
Yesterday I found that skype stopped worling, I've got kubuntu 13.04 with latest updates.
```
execve("/usr/bin/skype", ["skype"], [/* 56 vars */]) = 0brk(0)                                  = 0xb7dd000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff7780000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=196987, ...}) = 0
mmap2(NULL, 196987, PROT_READ, MAP_PRIVATE, 3, 0) = 0xfffffffff774f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libasound.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200\261\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=985212, ...}) = 0
mmap2(NULL, 988080, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff765d000
mmap2(0xf774a000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xec) = 0xfffffffff774a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libXv.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\f\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=17964, ...}) = 0
mmap2(NULL, 20732, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff7657000
mmap2(0xf765b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xfffffffff765b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libXss.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200\t\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9688, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff7656000
mmap2(NULL, 12508, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff7652000
mmap2(0xf7654000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xfffffffff7654000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/librt.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\31\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=30696, ...}) = 0
mmap2(NULL, 33352, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff7649000
mmap2(0xf7650000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0xfffffffff7650000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=13856, ...}) = 0
mmap2(NULL, 16512, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff7644000
mmap2(0xf7647000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2) = 0xfffffffff7647000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libX11.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20D\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1268672, ...}) = 0
mmap2(NULL, 1268568, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff750e000
mmap2(0xf7640000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x132) = 0xfffffffff7640000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libXext.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200(\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=68240, ...}) = 0
mmap2(NULL, 71368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff74fc000
mmap2(0xf750c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf) = 0xfffffffff750c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libQtDBus.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\370\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=515008, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff74fb000
mmap2(NULL, 513956, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff747d000
mmap2(0xf74f9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7c) = 0xfffffffff74f9000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libQtWebKit.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\22\31\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=35238832, ...}) = 0
mmap2(NULL, 35340468, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff52c8000
mmap2(0xf737c000, 950272, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x20b3) = 0xfffffffff737c000
mmap2(0xf7464000, 98484, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff7464000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libQtXml.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360\273\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=259964, ...}) = 0
mmap2(NULL, 258540, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff5288000
mmap2(0xf52c6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3e) = 0xfffffffff52c6000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libQtGui.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240r\22\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=11325500, ...}) = 0
mmap2(NULL, 11334232, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff47b8000
mmap2(0xf525f000, 155648, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xaa7) = 0xfffffffff525f000
mmap2(0xf5285000, 8792, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff5285000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libQtNetwork.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\3604\2\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1318640, ...}) = 0
mmap2(NULL, 1322228, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff4675000
mmap2(0xf47b4000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13e) = 0xfffffffff47b4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libQtCore.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\346\5\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=3039312, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff4674000
mmap2(NULL, 3044116, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff438c000
mmap2(0xf466b000, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2de) = 0xfffffffff466b000
mmap2(0xf4673000, 788, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff4673000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320[\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=124637, ...}) = 0
mmap2(NULL, 107008, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff4371000
mmap2(0xf4388000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16) = 0xfffffffff4388000
mmap2(0xf438a000, 4608, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff438a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libstdc++.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300f\4\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=922208, ...}) = 0
mmap2(NULL, 951860, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff4288000
mprotect(0xf4364000, 4096, PROT_NONE)   = 0
mmap2(0xf4365000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xdc) = 0xfffffffff4365000
mmap2(0xf436a000, 26164, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff436a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libm.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`E\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=267816, ...}) = 0
mmap2(NULL, 270496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff4245000
mmap2(0xf4286000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x40) = 0xfffffffff4286000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libgcc_s.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@ \0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=112148, ...}) = 0
mmap2(NULL, 115248, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff4228000
mmap2(0xf4243000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1a) = 0xfffffffff4243000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\232\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1770984, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff4227000
mmap2(NULL, 1780508, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff4074000
mmap2(0xf4221000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1ad) = 0xfffffffff4221000
mmap2(0xf4224000, 11036, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff4224000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libxcb.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20|\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=132680, ...}) = 0
mmap2(NULL, 135468, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff4052000
mmap2(0xf4072000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1f) = 0xfffffffff4072000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libdbus-1.so.3", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0PP\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=296792, ...}) = 0
mmap2(NULL, 299836, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff4008000
mmap2(0xf4050000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x47) = 0xfffffffff4050000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libz.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\26\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=95764, ...}) = 0
mmap2(NULL, 98464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3fef000
mmap2(0xf4006000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16) = 0xfffffffff4006000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libXrender.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\23\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=34468, ...}) = 0
mmap2(NULL, 37288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3fe5000
mmap2(0xf3fed000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7) = 0xfffffffff3fed000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libjpeg.so.8", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`)\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=284392, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff3fe4000
mmap2(NULL, 352676, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3f8d000
mmap2(0xf3fd2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x44) = 0xfffffffff3fd2000
mmap2(0xf3fd4000, 61860, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff3fd4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libpng12.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\00000\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=161344, ...}) = 0
mmap2(NULL, 164092, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3f64000
mmap2(0xf3f8b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x26) = 0xfffffffff3f8b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libxslt.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0p\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=243152, ...}) = 0
mmap2(NULL, 247024, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3f27000
mmap2(0xf3f62000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3a) = 0xfffffffff3f62000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libgstapp-0.10.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0$\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=47048, ...}) = 0
mmap2(NULL, 49856, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3f1a000
mmap2(0xf3f25000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa) = 0xfffffffff3f25000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libgstinterfaces-0.10.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360:\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=67252, ...}) = 0
mmap2(NULL, 70160, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3f08000
mprotect(0xf3f17000, 4096, PROT_NONE)   = 0
mmap2(0xf3f18000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf) = 0xfffffffff3f18000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libgstpbutils-0.10.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320o\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=137684, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff3f07000
mmap2(NULL, 136464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3ee5000
mmap2(0xf3f05000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x20) = 0xfffffffff3f05000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libgstvideo-0.10.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260:\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=116652, ...}) = 0
mmap2(NULL, 119680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3ec7000
mmap2(0xf3ee3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b) = 0xfffffffff3ee3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libgstbase-0.10.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \214\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=391684, ...}) = 0
mmap2(NULL, 394540, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3e66000
mmap2(0xf3ec5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5e) = 0xfffffffff3ec5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \240\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=938976, ...}) = 0
mmap2(NULL, 945036, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3d7f000
mmap2(0xf3e61000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe1) = 0xfffffffff3e61000
mmap2(0xf3e65000, 2956, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff3e65000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libgobject-2.0.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\204\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=329608, ...}) = 0
mmap2(NULL, 333816, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3d2d000
mprotect(0xf3d7c000, 4096, PROT_NONE)   = 0
mmap2(0xf3d7d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4f) = 0xfffffffff3d7d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libxml2.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\307\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1396864, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff3d2c000
mmap2(NULL, 1403380, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3bd5000
mprotect(0xf3d25000, 4096, PROT_NONE)   = 0
mmap2(0xf3d26000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x150) = 0xfffffffff3d26000
mmap2(0xf3d2b000, 2548, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff3d2b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libglib-2.0.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260R\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1047464, ...}) = 0
mmap2(NULL, 1051872, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3ad4000
mmap2(0xf3bd3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xfe) = 0xfffffffff3bd3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libsqlite3.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360P\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=713564, ...}) = 0
mmap2(NULL, 713444, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3a25000
mmap2(0xf3ad1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xac) = 0xfffffffff3ad1000
mmap2(0xf3ad3000, 740, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff3ad3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libfontconfig.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20C\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=228108, ...}) = 0
mmap2(NULL, 232692, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff39ec000
mmap2(0xf3a23000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x36) = 0xfffffffff3a23000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libQtOpenGL.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\345\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1036212, ...}) = 0
mmap2(NULL, 1040932, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff38ed000
mmap2(0xf39e5000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf7) = 0xfffffffff39e5000
mmap2(0xf39eb000, 548, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff39eb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib32/nvidia-310/libGL.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@a\3\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=851204, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff38ec000
mmap2(NULL, 916896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff380c000
mmap2(0xf38bc000, 135168, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xaf) = 0xfffffffff38bc000
mmap2(0xf38dd000, 60832, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff38dd000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libaudio.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p8\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=95768, ...}) = 0
mmap2(NULL, 98908, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff37f3000
mmap2(0xf380a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16) = 0xfffffffff380a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libfreetype.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300i\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=628224, ...}) = 0
mmap2(NULL, 630948, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3758000
mmap2(0xf37ee000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x95) = 0xfffffffff37ee000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libSM.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\24\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=30120, ...}) = 0
mmap2(NULL, 32944, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff374f000
mmap2(0xf3756000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0xfffffffff3756000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libICE.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\3605\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=92596, ...}) = 0
mmap2(NULL, 102704, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3735000
mmap2(0xf374b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15) = 0xfffffffff374b000
mmap2(0xf374d000, 4400, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff374d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libXi.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360\30\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=58924, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff3734000
mmap2(NULL, 61856, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3724000
mmap2(0xf3732000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd) = 0xfffffffff3732000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libXau.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9608, ...}) = 0
mmap2(NULL, 12424, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3720000
mmap2(0xf3722000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xfffffffff3722000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libXdmcp.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\16\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=21888, ...}) = 0
mmap2(NULL, 24692, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3719000
mmap2(0xf371e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4) = 0xfffffffff371e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/liborc-0.4.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260x\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=599652, ...}) = 0
mmap2(NULL, 598648, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3686000
mmap2(0xf3714000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8e) = 0xfffffffff3714000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libgmodule-2.0.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\f\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=13756, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff3685000
mmap2(NULL, 16580, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3680000
mmap2(0xf3683000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2) = 0xfffffffff3683000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libffi.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\17\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=26060, ...}) = 0
mmap2(NULL, 25336, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3679000
mmap2(0xf367e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5) = 0xfffffffff367e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/liblzma.so.5", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\30\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=153048, ...}) = 0
mmap2(NULL, 155716, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3652000
mmap2(0xf3677000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x24) = 0xfffffffff3677000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libpcre.so.3", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\21\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=263628, ...}) = 0
mmap2(NULL, 262288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff3611000
mmap2(0xf3650000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3f) = 0xfffffffff3650000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libexpat.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220 \0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=161156, ...}) = 0
mmap2(NULL, 159812, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff35e9000
mmap2(0xf360e000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x25) = 0xfffffffff360e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib32/nvidia-310/tls/libnvidia-tls.so.310.32", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \v\0\0004\0\0\0"..., 512) = 512
lseek(3, 9080, SEEK_SET)                = 9080
read(3, "\4\0\0\0\20\0\0\0\1\0\0\0GNU\0\0\0\0\0\2\0\0\0\3\0\0\0c\0\0\0", 32) = 32
fstat64(3, {st_mode=S_IFREG|0644, st_size=10080, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff35e8000
mmap2(NULL, 13680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff35e4000
mmap2(0xf35e7000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2) = 0xfffffffff35e7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib32/nvidia-310/libnvidia-glcore.so.310.32", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\203I\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=30463572, ...}) = 0
mmap2(NULL, 30542912, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff18c3000
mmap2(0xf3574000, 385024, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1cb0) = 0xfffffffff3574000
mmap2(0xf35d2000, 72768, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xfffffffff35d2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libXt.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \272\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=376148, ...}) = 0
mmap2(NULL, 376532, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff1867000
mmap2(0xf18bf000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x58) = 0xfffffffff18bf000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libuuid.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \20\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=18036, ...}) = 0
mmap2(NULL, 20708, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfffffffff1861000
mmap2(0xf1865000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xfffffffff1865000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff1860000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff185f000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff185e000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff185d000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff185c000
set_thread_area(0xffc72330)             = 0
mprotect(0xf4221000, 8192, PROT_READ)   = 0
mprotect(0xf1865000, 4096, PROT_READ)   = 0
mprotect(0xf3722000, 4096, PROT_READ)   = 0
mprotect(0xf371e000, 4096, PROT_READ)   = 0
mprotect(0xf4072000, 4096, PROT_READ)   = 0
mprotect(0xf7647000, 4096, PROT_READ)   = 0
mprotect(0xf7640000, 4096, PROT_READ)   = 0
mprotect(0xf374b000, 4096, PROT_READ)   = 0
mprotect(0xf3756000, 4096, PROT_READ)   = 0
mprotect(0xf18bf000, 4096, PROT_READ)   = 0
mprotect(0xf4286000, 4096, PROT_READ)   = 0
mprotect(0xf18c3000, 30085120, PROT_READ|PROT_WRITE) = 0
mprotect(0xf18c3000, 30085120, PROT_READ|PROT_EXEC) = 0
mprotect(0xf35e4000, 12288, PROT_READ|PROT_WRITE) = 0
mprotect(0xf35e4000, 12288, PROT_READ|PROT_EXEC) = 0
mprotect(0xf360e000, 8192, PROT_READ)   = 0
mprotect(0xf3650000, 4096, PROT_READ)   = 0
mprotect(0xf3677000, 4096, PROT_READ)   = 0
mprotect(0xf367e000, 4096, PROT_READ)   = 0
mprotect(0xf4388000, 4096, PROT_READ)   = 0
mprotect(0xf3bd3000, 4096, PROT_READ)   = 0
mprotect(0xf3683000, 4096, PROT_READ)   = 0
mprotect(0xf3714000, 4096, PROT_READ)   = 0
mprotect(0xf750c000, 4096, PROT_READ)   = 0
mprotect(0xf3732000, 4096, PROT_READ)   = 0
mprotect(0xf4006000, 4096, PROT_READ)   = 0
mprotect(0xf37ee000, 16384, PROT_READ)  = 0
mprotect(0xf380a000, 4096, PROT_READ)   = 0
mprotect(0xf380c000, 720896, PROT_READ|PROT_WRITE) = 0
mprotect(0xf380c000, 720896, PROT_READ|PROT_EXEC) = 0
mprotect(0xf4243000, 4096, PROT_READ)   = 0
mprotect(0xf4365000, 16384, PROT_READ)  = 0
mprotect(0xf7650000, 4096, PROT_READ)   = 0
mprotect(0xf466b000, 28672, PROT_READ)  = 0
mprotect(0xf3fed000, 4096, PROT_READ)   = 0
mprotect(0xf3f8b000, 4096, PROT_READ)   = 0
mprotect(0xf3d7d000, 4096, PROT_READ)   = 0
mprotect(0xf3a23000, 4096, PROT_READ)   = 0
mprotect(0xf525f000, 139264, PROT_READ) = 0
mprotect(0xf39e5000, 8192, PROT_READ)   = 0
mprotect(0xf3ad1000, 4096, PROT_READ)   = 0
mprotect(0xf3d26000, 16384, PROT_READ)  = 0
mprotect(0xf3e61000, 12288, PROT_READ)  = 0
mprotect(0xf3ec5000, 4096, PROT_READ)   = 0
mprotect(0xf3ee3000, 4096, PROT_READ)   = 0
mprotect(0xf3f05000, 4096, PROT_READ)   = 0
mprotect(0xf3f18000, 4096, PROT_READ)   = 0
mprotect(0xf3f25000, 4096, PROT_READ)   = 0
mprotect(0xf3f62000, 4096, PROT_READ)   = 0
mprotect(0xf3fd2000, 4096, PROT_READ)   = 0
mprotect(0xf4050000, 4096, PROT_READ)   = 0
mprotect(0xf47b4000, 12288, PROT_READ)  = 0
mprotect(0xf52c6000, 4096, PROT_READ)   = 0
mprotect(0xf52c8000, 34291712, PROT_READ|PROT_WRITE) = 0
mprotect(0xf52c8000, 34291712, PROT_READ|PROT_EXEC) = 0
mprotect(0xf737c000, 884736, PROT_READ) = 0
mprotect(0xf74f9000, 4096, PROT_READ)   = 0
mprotect(0xf7654000, 4096, PROT_READ)   = 0
mprotect(0xf765b000, 4096, PROT_READ)   = 0
mprotect(0xf774a000, 16384, PROT_READ)  = 0
mprotect(0x9ac5000, 512000, PROT_READ)  = 0
mprotect(0xf77a3000, 4096, PROT_READ)   = 0
munmap(0xf774f000, 196987)              = 0
set_tid_address(0xf185db68)             = 13003
set_robust_list(0xf185db70, 0xc)        = 0
futex(0xffc721f4, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, f185db00) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0xf43765f0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xf4376680, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=-4286578688, rlim_max=-9223372032757504384}) = 0
uname({sys="Linux", node="spc", ...})   = 0
futex(0xf7648058, FUTEX_WAKE_PRIVATE, 2147483647) = 0
brk(0)                                  = 0xb7dd000
brk(0xb7fe000)                          = 0xb7fe000
clock_gettime(CLOCK_MONOTONIC, {63562, 839728552}) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
[ Process PID=13003 runs in 32 bit mode. ]



```

---

### Post by dino99 on 2013-03-16
dupe of an other thread opened 2 pages ago

---

### Post by victor9098 on 2013-03-16
The problem with Skype not running with me seems to have to do with the Nvidia drivers. If I use the standard Xorg drivers skype opens and runs as normal. If I use the 304/310/313 repo's then skype with crash when I try to open it.

---

### Post by Paddy Landau on 2013-03-16
If you're using Skype from the standard repositories, this should be raised as a bug.

---

### Post by victor9098 on 2013-03-16
> **Paddy Landau said:**
> If you're using Skype from the standard repositories, this should be raised as a bug.

Yes I submitted Bug #1155327 in launchpad a few days ago, but its still listed as 'undecided'

---

### Post by jfernyhough on 2013-03-16
> **victor9098 said:**
> The problem with Skype not running with me  seems to have to do with the Nvidia drivers. If I use the standard Xorg  drivers skype opens and runs as normal. If I use the 304/310/313 repo's  then skype with crash when I try to open it.

It's not just Nvidia, then. It segfaults with fglrx.

---

### Post by victor9098 on 2013-03-16
> **jfernyhough said:**
> It's not just Nvidia, then. It segfaults with fglrx.

I'm no expert, all I know right now is that if I 'need' to run Skype I need to switch back to the Xorg repo, then switch back to Nvidia for if I want to mess in Steam :D

---

### Post by Paddy Landau on 2013-03-16
> **victor9098 said:**
> Yes I submitted Bug #1155327 in launchpad a few days ago, but its still listed as 'undecided'
I cannot find that bug. It's best that you post the link here, so that other people with the problem can vote for it and comment on it. Otherwise it is likely to remain undecided.

---

### Post by victor9098 on 2013-03-16
> **Paddy Landau said:**
> I cannot find that bug. It's best that you post the link here, so that other people with the problem can vote for it and comment on it. Otherwise it is likely to remain undecided.

They still have it listed as private but here is the link I have if you want to try or keep an eye on the status; [Bug #1155327: skype crashed with SIGSEGV in malloc@plt()]("https://bugs.launchpad.net/ubuntu/+bug/1155327")

---

### Post by Paddy Landau on 2013-03-16
> **victor9098 said:**
> They still have it listed as private but here is the link I have if you want to try or keep an eye on the status; [Bug #1155327: skype crashed with SIGSEGV in malloc@plt()]("https://bugs.launchpad.net/ubuntu/+bug/1155327")
I cannot see private bugs. If you raised the bug, you can change its status from private to public. I would recommend that you do, as this is not a security bug.

---

### Post by victor9098 on 2013-03-16
> **Paddy Landau said:**
> I cannot see private bugs. If you raised the bug, you can change its status from private to public. I would recommend that you do, as this is not a security bug.

Right, give that a try now. Hopefully I do not live to regret...

---

### Post by cariboo on 2013-03-16
Merged two similar threads.

---

### Post by Paddy Landau on 2013-03-16
> **victor9098 said:**
> Right, give that a try now. Hopefully I do not live to regret...
Yes, it works now. People who have the same problem as you can vote and comment on the bug.

---

### Post by PRAEst76 on 2013-03-16
> **victor9098 said:**
> Yes I submitted Bug #1155327 in launchpad a few days ago, but its still listed as 'undecided'

Possibly a duplicate of #1002187 which has been open since May last year.

Sounds like the same issue. My Desktop and my SO's netbook are on the same version of Ubuntu using the same version of Skype. Hers runs fine while mine segfaults. I'm using the proprietary Nvidia drivers while she is using Xorg drivers.

---

### Post by victor9098 on 2013-03-16
> **PRAEst76 said:**
> Possibly a duplicate of #1002187 which has been open since May last year.

Sounds like the same issue. My Desktop and my SO's netbook are on the same version of Ubuntu using the same version of Skype. Hers runs fine while mine segfaults. I'm using the proprietary Nvidia drivers while she is using Xorg drivers.

It was never an issue for me in Ubuntu 12.10 using the 310 repo, this is a new issue for me since moving to 13.04

---

### Post by raspatan on 2013-03-17
My problem is perhaps really stupid. I open skype, put my credentials but it stays connecting for 5 minutes until it says "not possible to connect". I have not done any update in my PC. I am using a broadband internet now (a USB stick) and literally I am now at the other side of the world from where I was before. But I dont see the problem with either of them. In fact, When I use Skype on Windows I can connect!! I have Xubuntu 12.04. 

Thank you in advance

---

### Post by alphacrucis2 on 2013-03-17
Then open a new thread with the details in the beginners section. This thread is about skype seg faulting on the dev version (13.04) since a recent update. Please don't hijack threads that aren't related to your problem.

---

