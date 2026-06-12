---
title: "Limit to number of processes/threads?"
date: 2016-02-16
forum: Ubuntu Development Version
---

### Post by donoregano on 2016-02-16
tl;dr: Something is stopping forks on my xenial vm, and it is not max-threads or ulimit. What else is there?

I've just installed a virtual machine with a minimal Xenial server, for checking whether a piece of software I am responsible will work properly on the newest Ubuntu.
One of our unit tests create lots of processes (for checking an IPC mechanism, an irrelevant detail, really), and this test fails. So I tried just running a bash script that causes a lot of forks, and this fails too:

```
xxx@xenial:~$ for i in {1..600}; do sleep 10000 & done
[500] 1730
[501] 1731
[502] 1732
[503] 1733
[504] 1734
[505] 1735
-bash: fork: retry: Resource temporarily unavailable
-bash: fork: retry: Resource temporarily unavailable
-bash: fork: retry: Resource temporarily unavailable
```

So, my first suspicion was ulimit/nproc, so I fiddled with that:
```
xxx@xenial:~$ ulimit -a
core file size          (blocks, -c) unlimited
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 100000
max locked memory       (kbytes, -l) 10000000
max memory size         (kbytes, -m) unlimited
open files                      (-n) 65536
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 100000
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

Same result. So I checked threads-max:
```
xxx@xenial:~$ cat /proc/sys/kernel/threads-max
31318

```

That can't be it. The vm is assigned two cpus and 4GB RAM. It is running under KVM.
The limit seems to be systemwide, since I cant start any more processes if I start some of them as root.
I also installed Vivid, in the same configuration, but I don't get this behaviour there.

Oh, and there are no indications whatsoever in any logs.

What am I missing?

---

### Post by dino99 on 2016-02-16
you said 'vivid', is it running upstart or systemd ?
maybe start xenial with upstart (grub menu)

---

### Post by donoregano on 2016-02-16
Okay, so I installed "upstart-sysv" and rebooted, and now my fork bomb works!

Some further investigation led me to the /etc/systemd/system.conf and the parameter DefaultTasksMax. If I uncomment this parameter and turned it up to 10000 my fork bomb starts working under systemd as well!

The only question is why this limit is affecting my user. I was under the impression that that parameter is only meant to affect systemd units?!

---

### Post by dino99 on 2016-02-17
i suppose you might either ask that question on askubuntu to get devs explanation, or report against systemd, which should handle such case (maybe the systemd manpage can help)

---

