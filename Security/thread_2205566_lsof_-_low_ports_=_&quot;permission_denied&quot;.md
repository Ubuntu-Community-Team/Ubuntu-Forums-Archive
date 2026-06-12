---
title: "lsof - low ports = &quot;permission denied&quot;"
date: 2014-02-14
forum: Security
---

### Post by bc.haynes on 2014-02-14
This mainly out of curiosity. When listing open ports with **lsof**, a lot of the lower numberes ports have "Permission Denied". What does this mean? I shall list the first 50 lines of the printout:
```
ben@MissionControl:~$ lsof | head -50
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /root/.gvfs
      Output information may be incomplete.
COMMAND    PID       USER   FD      TYPE             DEVICE SIZE/OFF    NODE NAME
init         1       root  cwd   unknown                                     /proc/1/cwd (readlink: Permission denied)
init         1       root  rtd   unknown                                     /proc/1/root (readlink: Permission denied)
init         1       root  txt   unknown                                     /proc/1/exe (readlink: Permission denied)
init         1       root NOFD                                               /proc/1/fd (opendir: Permission denied)
kthreadd     2       root  cwd   unknown                                     /proc/2/cwd (readlink: Permission denied)
kthreadd     2       root  rtd   unknown                                     /proc/2/root (readlink: Permission denied)
kthreadd     2       root  txt   unknown                                     /proc/2/exe (readlink: Permission denied)
kthreadd     2       root NOFD                                               /proc/2/fd (opendir: Permission denied)
ksoftirqd    3       root  cwd   unknown                                     /proc/3/cwd (readlink: Permission denied)
ksoftirqd    3       root  rtd   unknown                                     /proc/3/root (readlink: Permission denied)
ksoftirqd    3       root  txt   unknown                                     /proc/3/exe (readlink: Permission denied)
ksoftirqd    3       root NOFD                                               /proc/3/fd (opendir: Permission denied)
kworker/0    5       root  cwd   unknown                                     /proc/5/cwd (readlink: Permission denied)
kworker/0    5       root  rtd   unknown                                     /proc/5/root (readlink: Permission denied)
kworker/0    5       root  txt   unknown                                     /proc/5/exe (readlink: Permission denied)
kworker/0    5       root NOFD                                               /proc/5/fd (opendir: Permission denied)
kworker/u    7       root  cwd   unknown                                     /proc/7/cwd (readlink: Permission denied)
kworker/u    7       root  rtd   unknown                                     /proc/7/root (readlink: Permission denied)
kworker/u    7       root  txt   unknown                                     /proc/7/exe (readlink: Permission denied)
kworker/u    7       root NOFD                                               /proc/7/fd (opendir: Permission denied)
migration    8       root  cwd   unknown                                     /proc/8/cwd (readlink: Permission denied)
migration    8       root  rtd   unknown                                     /proc/8/root (readlink: Permission denied)
migration    8       root  txt   unknown                                     /proc/8/exe (readlink: Permission denied)
migration    8       root NOFD                                               /proc/8/fd (opendir: Permission denied)
rcu_bh       9       root  cwd   unknown                                     /proc/9/cwd (readlink: Permission denied)
rcu_bh       9       root  rtd   unknown                                     /proc/9/root (readlink: Permission denied)
rcu_bh       9       root  txt   unknown                                     /proc/9/exe (readlink: Permission denied)
rcu_bh       9       root NOFD                                               /proc/9/fd (opendir: Permission denied)
rcu_sched   10       root  cwd   unknown                                     /proc/10/cwd (readlink: Permission denied)
rcu_sched   10       root  rtd   unknown                                     /proc/10/root (readlink: Permission denied)
rcu_sched   10       root  txt   unknown                                     /proc/10/exe (readlink: Permission denied)
rcu_sched   10       root NOFD                                               /proc/10/fd (opendir: Permission denied)
watchdog/   11       root  cwd   unknown                                     /proc/11/cwd (readlink: Permission denied)
watchdog/   11       root  rtd   unknown                                     /proc/11/root (readlink: Permission denied)
watchdog/   11       root  txt   unknown                                     /proc/11/exe (readlink: Permission denied)
watchdog/   11       root NOFD                                               /proc/11/fd (opendir: Permission denied)
watchdog/   12       root  cwd   unknown                                     /proc/12/cwd (readlink: Permission denied)
watchdog/   12       root  rtd   unknown                                     /proc/12/root (readlink: Permission denied)
watchdog/   12       root  txt   unknown                                     /proc/12/exe (readlink: Permission denied)
watchdog/   12       root NOFD                                               /proc/12/fd (opendir: Permission denied)
ksoftirqd   13       root  cwd   unknown                                     /proc/13/cwd (readlink: Permission denied)
ksoftirqd   13       root  rtd   unknown                                     /proc/13/root (readlink: Permission denied)
ksoftirqd   13       root  txt   unknown                                     /proc/13/exe (readlink: Permission denied)
ksoftirqd   13       root NOFD                                               /proc/13/fd (opendir: Permission denied)
kworker/1   16       root  cwd   unknown                                     /proc/16/cwd (readlink: Permission denied)
kworker/1   16       root  rtd   unknown                                     /proc/16/root (readlink: Permission denied)
kworker/1   16       root  txt   unknown                                     /proc/16/exe (readlink: Permission denied)
kworker/1   16       root NOFD                                               /proc/16/fd (opendir: Permission denied)
cpuset      17       root  cwd   unknown                                     /proc/17/cwd (readlink: Permission denied)
```
What is the **FD** and the **TYPE** = unknown?

---

### Post by ian-weisser on 2014-02-14
The short answer to "Permission denied" is that you (at user-level) are not allowed to query the system for details on those low-number ports. If you elevate to system-level (using sudo), you can see them just fine. Restricting the information from users -who don't have permission to change it anyway- is a form of protection.

FD and TYPE are explained on the lsof manpage.
```
 FD         is the File Descriptor number of the file or:

                       cwd  current working directory;
                       Lnn  library references (AIX);
                       err  FD information error (see NAME column);
                       jld  jail directory (FreeBSD);
                       ltx  shared library text (code and data);
                       Mxx  hex memory-mapped type number xx.
                       m86  DOS Merge mapped file;
                       mem  memory-mapped file;
                       mmap memory-mapped device;
                       pd   parent directory;
                       rtd  root directory;
                       tr   kernel trace file (OpenBSD);
                       txt  program text (code and data);
                       v86  VP/ix mapped file;

                  FD is followed by one of these characters, describing the mode under which the file is open:

                       r for read access;
                       w for write access;
                       u for read and write access;
                       space if mode unknown and no lock
                            character follows;
                       `-' if mode unknown and lock
                            character follows.

                  The mode character is followed by one of these lock characters, describing the type of lock applied to the file:

                       N for a Solaris NFS lock of unknown type;
                       r for read lock on part of the file;
                       R for a read lock on the entire file;
                       w for a write lock on part of the file;
                       W for a write lock on the entire file;
                       u for a read and write lock of any length;
                       U for a lock of unknown type;
                       x for an SCO OpenServer Xenix lock on part      of the file;
                       X for an SCO OpenServer Xenix lock on the      entire file;
                       space if there is no lock.

                  See the LOCKS section for more information on the lock information character.

                  The FD column contents constitutes a single field for parsing in post-processing scripts.
```

```
       TYPE       is the type of the node associated with the file - e.g., GDIR, GREG, VDIR, VREG, etc.

                  or ``IPv4'' for an IPv4 socket;

                  or ``IPv6'' for an open IPv6 network file - even if its address is IPv4, mapped in an IPv6 address;

                  or ``ax25'' for a Linux AX.25 socket;

                  or ``inet'' for an Internet domain socket;

                  or ``lla'' for a HP-UX link level access file;

                  or ``rte'' for an AF_ROUTE socket;

                  or ``sock'' for a socket of unknown domain;

                  or ``unix'' for a UNIX domain socket;

                  or ``x.25'' for an HP-UX x.25 socket;

                  or ``BLK'' for a block special file;

                  or ``CHR'' for a character special file;

                  or ``DEL'' for a Linux map file that has been deleted;

                  or ``DIR'' for a directory;

                  or ``DOOR'' for a VDOOR file;

                  or ``FIFO'' for a FIFO special file;

                  or ``KQUEUE'' for a BSD style kernel event queue file;

                  or ``LINK'' for a symbolic link file;

                  or ``MPB'' for a multiplexed block file;

                  or ``MPC'' for a multiplexed character file;

                  or ``NOFD'' for a Linux /proc/<PID>/fd directory that can't be opened -- the directory path appears in the NAME column, followed by an error message;

                  or ``PAS'' for a /proc/as file;

                  or ``PAXV'' for a /proc/auxv file;

                  or ``PCRE'' for a /proc/cred file;

                  or ``PCTL'' for a /proc control file;

                  or ``PCUR'' for the current /proc process;

                  or ``PCWD'' for a /proc current working directory;

                  or ``PDIR'' for a /proc directory;

                  or ``PETY'' for a /proc executable type (etype);

                  or ``PFD'' for a /proc file descriptor;

                  or ``PFDR'' for a /proc file descriptor directory;

                  or ``PFIL'' for an executable /proc file;

                  or ``PFPR'' for a /proc FP register set;

                  or ``PGD'' for a /proc/pagedata file;

                  or ``PGID'' for a /proc group notifier file;

                  or ``PIPE'' for pipes;

                  or ``PLC'' for a /proc/lwpctl file;

                  or ``PLDR'' for a /proc/lpw directory;

                  or ``PLDT'' for a /proc/ldt file;

                  or ``PLPI'' for a /proc/lpsinfo file;

                  or ``PLST'' for a /proc/lstatus file;

                  or ``PLU'' for a /proc/lusage file;

                  or ``PLWG'' for a /proc/gwindows file;

                  or ``PLWI'' for a /proc/lwpsinfo file;

                  or ``PLWS'' for a /proc/lwpstatus file;

                  or ``PLWU'' for a /proc/lwpusage file;

                  or ``PLWX'' for a /proc/xregs file'

                  or ``PMAP'' for a /proc map file (map);

                  or ``PMEM'' for a /proc memory image file;

                  or ``PNTF'' for a /proc process notifier file;

                  or ``POBJ'' for a /proc/object file;

                  or ``PODR'' for a /proc/object directory;

                  or ``POLP'' for an old format /proc light weight process file;

                  or ``POPF'' for an old format /proc PID file;

                  or ``POPG'' for an old format /proc page data file;

                  or ``PORT'' for a SYSV named pipe;

                  or ``PREG'' for a /proc register file;

                  or ``PRMP'' for a /proc/rmap file;

                  or ``PRTD'' for a /proc root directory;

                  or ``PSGA'' for a /proc/sigact file;

                  or ``PSIN'' for a /proc/psinfo file;

                  or ``PSTA'' for a /proc status file;

                  or ``PSXSEM'' for a POSIX semaphore file;

                  or ``PSXSHM'' for a POSIX shared memory file;

                  or ``PUSG'' for a /proc/usage file;

                  or ``PW'' for a /proc/watch file;

                  or ``PXMP'' for a /proc/xmap file;

                  or ``REG'' for a regular file;

                  or ``SMT'' for a shared memory transport file;

                  or ``STSO'' for a stream socket;

                  or ``UNNM'' for an unnamed type file;

                  or ``XNAM'' for an OpenServer Xenix special file of unknown type;

                  or ``XSEM'' for an OpenServer Xenix semaphore file;

                  or ``XSD'' for an OpenServer Xenix shared data file;

                  or the four type number octets if the corresponding name isn't known.

```

---

### Post by bc.haynes on 2014-02-14
+1 for the detailed info. Thank you.

---

### Post by cariboo on 2014-02-14
Moved to Security discussions, as this isn't a question about the forum.

---

