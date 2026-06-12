---
title: "What is the suspicious pre-string: rsh wolf ?"
date: 2015-08-20
forum: Ubuntu Application Development
---

### Post by ruwan2 on 2015-08-20
Hi, 

When I read book linux device driver. there is an example memory map display. 
See below dot line please. 
The first command is:   
#cat /proc/1/maps 


The second line after a '#' sign puzzles me a lot. 

# rsh wolf cat /proc/self/maps #### x86-64 (trimmed) 

This line is a similar to the first command line?  
What is the first two words: 'rsh wolf' mean? 
That example is on: 
Page 438/630 
[http://free-electrons.com/doc/books/ldd3.pdf](http://free-electrons.com/doc/books/ldd3.pdf) 

Thanks, 
............. 
#cat /proc/1/maps 
08048000-0804e000 r-xp 00000000 03:01 64652 /sbin/init text 
0804e000-0804f000 rw-p 00006000 03:01 64652 /sbin/init data 
0804f000-08053000 rwxp 00000000 00:00 0     zero-mapped BSS 
40000000-40015000 r-xp 00000000 03:01 96278 /lib/[ld-2.3.2.so]("http://ld-2.3.2.so") text 
40015000-40016000 rw-p 00014000 03:01 96278 /lib/[ld-2.3.2.so]("http://ld-2.3.2.so") data 
40016000-40017000 rw-p 00000000 00:00 0     BSS for ld.so 
42000000-4212e000 r-xp 00000000 03:01 80290 /lib/tls/[libc-2.3.2.so]("http://libc-2.3.2.so") text 
4212e000-42131000 rw-p 0012e000 03:01 80290 /lib/tls/[libc-2.3.2.so]("http://libc-2.3.2.so") data 
42131000-42133000 rw-p 00000000 00:00 0     BSS for libc 
bffff000-c0000000 rwxp 00000000 00:00 0     Stack segment 
ffffe000-fffff000 ---p 00000000 00:00 0     vsyscall page 
# rsh wolf cat /proc/self/maps #### x86-64 (trimmed) 
00400000-00405000 r-xp 00000000 03:01 1596291 /bin/cat  text 
00504000-00505000 rw-p 00004000 03:01 1596291 /bin/cat  data 
00505000-00526000 rwxp 00505000 00:00 0     bss 
3252200000-3252214000 r-xp 00000000 03:01 1237890 /lib64/[ld-2.3.3.so]("http://ld-2.3.3.so") 
3252300000-3252301000 r--p 00100000 03:01 1237890 /lib64/[ld-2.3.3.so]("http://ld-2.3.3.so") 
3252301000-3252302000 rw-p 00101000 03:01 1237890 /lib64/[ld-2.3.3.so]("http://ld-2.3.3.so") 
7fbfffe000-7fc0000000 rw-p 7fbfffe000 00:00 0            stack 
ffffffffff600000-ffffffffffe00000 ---p 00000000 00:00 0  vsyscal

---

### Post by TheFu on 2015-08-20
rsh is the insecure remote-shell command that hasn't been used since 1992-ish.  These days, we would use ssh instead.

rsh, rlogin, rcp and ftp all died back then and have been replaced by ssh, scp, sftp.

BTW - teaching you to fish - manpages for commands like this are easily found through any web search.  "man rsh" will provide it and answer what each option means.

---

