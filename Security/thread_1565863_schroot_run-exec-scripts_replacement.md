---
title: "schroot run-exec-scripts replacement?"
date: 2010-09-01
forum: Security
---

### Post by bismark on 2010-09-01
Running x64 bit lucid but I have a few programs that will not function under it (though admittedly they are in the repos such as vncsnapshot). So I've configured a schroot install for a x86 base install of lucid.

Now the problem is that everytime I want to run my schroot environment I need to manually copy a few files over from my main environment such as /etc/resolv.conf. Before the "run-exec-scripts" option was available and it would copy the files listed in /etc/schroot/copyfiles-default but according to the man page run-exec-scripts is deprecated and being phased out.

```

run-exec-scripts=true|false Set whether chroot execution scripts will be run.

The default is the same as the default for the run-setup-scripts key.
This option was called run-session-scripts in versions prior to 0.2.5.
This option is deprecated and no longer used by schroot, but is still
permitted to be used; it will be obsoleted and removed in a future release.
```

So my question is, how do you copy /etc/resolv.conf now?


Solved:
After a little digging in release notes (huh go figure they contain useful information, who would have thunk it) I found a solution. If you change the type of schroot from plain to directory as shown below, schroot will run the scripts in /etc/schroot/setup.d/ directory. These scripts setup your schroot environment

```

[lucid-x86]
description=Ubuntu Lucid x86
type=directory
directory=/home/chroot/lucid-x86
priority=3
users=bismark
groups=users
root-groups=root
personality=linux32
aliases=default

```
S

---

### Post by nullzone on 2011-01-28
edit - comment deleted.

---

