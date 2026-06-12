---
title: "amanda: tape operations give &quot;invalid argument&quot;"
date: 2008-09-02
forum: Server Platforms
---

### Post by fedoraboy on 2008-09-02
This is driving me nuts...

Ok, I have done a recent migration from Fedora to Ubuntu 8.04.  I moved my existing amanda backups to the Ubuntu server.  So far so good.

But all tape operations via amanda seem to fail (and all operations from the OS work okay.)

a little example here.  Here I try to re-label a tape.  The write operations all seem to work, but the read operations fail:

(as user 'backup'):
$ amlabel -f sporadic s029
rewinding, reading label, not an amanda tape (Invalid argument)
rewinding, writing label s029, checking label
amlabel: not an amanda tape (Invalid argument)

Now I run it with strace, just to see what's going on (snippet below):
open("/dev/nst0l", O_RDONLY|O_LARGEFILE)         = 4
ioctl(4, MGSL_IOCSTXIDLE or MTIOCGET or SNDCTL_MIDI_MPUCMD, 0xbfc08c70) = 0
mmap2(NULL, 266240, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7bd9000
ioctl(4, MGSL_IOCGPARAMS or MTIOCTOP or SNDCTL_MIDI_MPUMODE, 0xbfc07a44)                   = 0
read(4, 0xb7bd9008, 262144)             = -1 EINVAL (Invalid argument)
munmap(0xb7bd9000, 266240)                                = 0
close(4)                = 0

Okay, so read syscall gives invalid argument.  So I look at the tape label with dd:

$ dd if=/dev/nst0l bs=32k
AMANDA: TAPESTART DATE X TAPE s029
014
1+0 records in
1+0 records out
32768 bytes (33 kB) copied, 13.7026 s, 2.4 kB/s

...so the label is written okay.

I have also used tar/cpio to write to the tape and read back off the tape (as user 'backup') with no issues.

Is anyone else having issues here with amanda?  I originally thought this was something with the drive... now I am wondering if there is something wrong with the amanda package.

---

### Post by fedoraboy on 2008-09-02
some kind soul on a different forum gave me the answer, so this is just a followup to pass this on to anyone else needing it.

add to tapetype in amanda.conf:
    readblocksize 32

---

