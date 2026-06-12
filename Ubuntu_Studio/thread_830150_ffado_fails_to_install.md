---
title: "ffado fails to install"
date: 2008-06-15
forum: Ubuntu Studio
---

### Post by wurdien on 2008-06-15
I have had problems getting my firepod to work with freebob, so I decided to try ffado instead. However installing ffado fails with following message:
```
scons: *** DirNodeInfo instance has no attribute 'csig'
scons: internal stack trace:
  File "/usr/lib/scons/SCons/Job.py", line 114, in start
    task.prepare()
  File "/usr/lib/scons/SCons/Script/Main.py", line 157, in prepare
    return SCons.Taskmaster.Task.prepare(self)
  File "/usr/lib/scons/SCons/Taskmaster.py", line 162, in prepare
    self.exception_raise()
  File "/usr/lib/scons/SCons/Taskmaster.py", line 659, in next_task
    task.make_ready()
  File "/usr/lib/scons/SCons/Script/Main.py", line 278, in make_ready
    SCons.Taskmaster.Task.make_ready(self)
  File "/usr/lib/scons/SCons/Taskmaster.py", line 299, in make_ready_current
    t.disambiguate().make_ready()
  File "/usr/lib/scons/SCons/Node/Alias.py", line 81, in make_ready
    self.get_csig()
  File "/usr/lib/scons/SCons/Node/Alias.py", line 137, in get_csig
    contents = self.get_contents()
  File "/usr/lib/scons/SCons/Node/Alias.py", line 95, in get_contents
    childsigs = map(lambda n: n.get_csig(), self.children())
  File "/usr/lib/scons/SCons/Node/Alias.py", line 95, in <lambda>
    childsigs = map(lambda n: n.get_csig(), self.children())
  File "/usr/lib/scons/SCons/Node/__init__.py", line 760, in get_csig
    return self.ninfo.csig
scons: building terminated because of errors.
```

This happens if I try to install it to /usr. If I install it to /usr/local test program fails (can't find shared library ffado.so or something similar, I don't remember).

I searched with google and found that some people had had same problems, however, I didn't find how to solve problems. I think that I read somewhere that this is bug in scons, but I can't find that resource anymore...

Please forgive me if there's clear instructions how to solve this problem somewhere in the internet, I just couldn't find them...

---

### Post by wurdien on 2008-06-15
Well, I managed to go around this problem. (set prefix to my home directory and manually copied files to /usr). But, I have understood things right, I have to recompile jack. As programs installed by package manager are already compiled, I have to install it myself from source code.

The problem is, to install new jack, I must remove old. But if I try to remove it, it also wants to remove all packages depending on it.

So how am I able to compile jack from source (or do some other thing to make ffado work)

---

### Post by Stochastic on 2008-06-17
You don't need to uninstall old versions of Jack to compile a new version.  Just make sure to execute the final sudo make install **with SUDO**, then that will grant the scripts permission to copy over older files of the jack install.

Be sure to back your system up before doing this level of modification to your audio chain though.

---

### Post by Maucca on 2008-09-02
watch out when going with the tutorial. My Ubuntu doesn't start up anymore after the last attempt to install FFADO beta 6.

If you are not an experienced sudoka you need to wait for the first 2.0 release.

Re-installing soon and attempting AGAIN! YAY, this is fun! thank god I bought the other harddrive for this (typing from xp)

---

