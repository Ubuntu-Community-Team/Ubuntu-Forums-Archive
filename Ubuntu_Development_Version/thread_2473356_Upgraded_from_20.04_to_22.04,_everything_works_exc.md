---
title: "Upgraded from 20.04 to 22.04, everything works except sound snd_hda_intel module"
date: 2022-04-01
forum: Ubuntu Development Version
---

### Post by xxasdqwe on 2022-04-01
I got shunned for posting this on AskUbuntu, but heres the post and Ill copy the info: [https://askubuntu.com/questions/1400470/kernel-module-not-getting-installed-after-full-upgrade-to-22-04](https://askubuntu.com/questions/1400470/kernel-module-not-getting-installed-after-full-upgrade-to-22-04)


I just full upgraded to 22.04 from 20.04 and things seem to be in order except the generic VM audio snd_hda_intel. 

I keep getting the error:

    modprobe snd-hda-intel
    # modprobe: FATAL: Module snd-hda-intel not found in directory /lib/modules/5.
[*]-generic

I thought maybe the new kernel (5.15..23) was missing the module, so I've tried 4 other kernels, plus generic and my lowlatency - 5.4, 5.13, 5.14, 5.17. The first didnt boot, but the others had the same error. It must be a configuration problem. The only possible clue I have is when trying to reinstall my old working kernel (5.4.0-105-lowlatency), it said [residual config]. I tried some suggestions to change the conf file, but the module is actually not where its looking for it, and not at all in the ../sound dir "/lib/modules/5.17.0-051700rc7-generic/kernel/sound/".. there is no "pci" dir at all. So its not being installed, even though I assume it would have been in at least on of the versions I tried.

Also `dpkg -S snd-hda-intel` says it finds the module in all the kernels. It must be searching either the package listing or the deb file contents, because its not on disk.

    linux-modules-5.17.0-051700rc7-generic: /lib/modules/5.17.0-051700rc7-generic/kernel/sound/pci/hda/snd-hda-intel.ko
    linux-modules-5.4.5-050405-lowlatency: /lib/modules/5.4.5-050405-lowlatency/kernel/sound/pci/hda/snd-hda-intel.ko
    ...

There may be other kernel modules not installed, but so far everything except ufw seems to work.

---

### Post by Doug S on 2022-04-01
On my test Ubuntu desktop 22.04 the module loads fine and is located in the normal place:

```
doug@desk-jj:~$ locate snd-hda-intel
/usr/lib/modules/5.15.0-18-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/usr/lib/modules/5.15.0-23-generic/kernel/sound/pci/hda/snd-hda-intel.ko
```

---

