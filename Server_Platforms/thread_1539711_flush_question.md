---
title: "flush question"
date: 2010-07-26
forum: Server Platforms
---

### Post by disturbednny89 on 2010-07-26
hey all,
this weekend I decided to upgrade my file server to 10.04 and it was running great up until yesterday. I noticed when I did a top that there was a bunch of flush processes after booting and most of them go away except for a flush-8:0 process. I have already tried to look in the forums to see if this has happened to anyone else and noticed there was a bug reported for mountall and plymouthd. after looking at the bug report i checked my version of mountall and it is at the version that has the fix. 

is there a way to find out what is calling flush during boot?

---

### Post by richardjh on 2010-07-27
Yes it definitely happens to other people

```

richardjh@ubuntu:~$ ps -ef | grep flush
root          2329     2           0   Jul26 ?          00:00:00 [flush-8:0]
richardjh  26729   26590   0   22:48 pts/0    00:00:00 grep --color=auto flush

```I found this snippet in a IRC log at [https://wiki.ubuntu.com/MeetingLogs/openweekLucid/KernelQA](https://wiki.ubuntu.com/MeetingLogs/openweekLucid/KernelQA) which suggests this process is normal and this is expected behaviour.

I have corrected spelling here for readability:

> (11:11:07 AM) ClassBot: bullgard4 asked: '~$ ps -ef | grep flush; 
root       252     2  0 May05 ?        00:00:00 [flush-8:0]' 
What process spawns this process? 
Where is described the function of this process?
(11:11:58 AM) apw: those processes are spawned by the kernel itself to handle flushing of block devices within the kernel, they are there to provide process
(11:12:35 AM) apw: contexts where needed.  they are tripped by fsync and similar calls to perform data-writes.  they are relatively new and may not appear before lucid

The reason for the 8:0 in the flush-8:0 is that it is flushing disk /dev/sda.
You can see this agrees by listing like this

```

richardjh@ubuntu:~$ ls -l /dev/sda
brw-rw---- 1 root disk **8**, **0** 2010-07-26 20:43 /dev/sda

```

---

