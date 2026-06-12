---
title: "Only detects one processor after installing virtual box"
date: 2008-07-30
forum: Virtualisation
---

### Post by kerryhall on 2008-07-30
Hello, I have a Dell PowerEdge R200 server that I installed hardy on. Everything was working perfectly until I tried to install virtual box. I installed "virtualbox-ose-modules-2.6.24-19-386" then rebooted, and now only one processor is detected. I tired uninstalling this module, no help.

Thanks!

---

### Post by mannheim on 2008-07-31
I'll have a guess at what might have happened. The version of the virtualbox modules that you installed ends in -386. This means (I think) that it is for the -386 kernel, not the -generic kernel. When you installed the virtualbox modules, you maybe pulled in the -386 kernel as a dependency; or perhaps the -386 kernel was already installed, and your system is now reconfigured to use it. Anyway the -386 kernel does not support multiple processors (or at least, it used not to). You need the -generic kernel.

To test what flavor of kernel you are using, open a terminal and type:
```
uname -r
```
You want to see something like "2.6.24-19-generic". If you see instead something lke "2.6.24-19-386", then that is the problem.

To fix it, first step would be to uninstall the virtualbox thing, and then reinstall the virtualbox package whose name ends in  -generic (or whatever matches the kernel you want to be running).

---

### Post by bodhi.zazen on 2008-07-31
very odd. What is the output of :

```
cat /proc/cupinfo
```

---

