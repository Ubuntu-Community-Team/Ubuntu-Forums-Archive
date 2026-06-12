---
title: "How Come NO Mention of PAE issue"
date: 2013-04-05
forum: Ubuntu Studio
---

### Post by hbnmgr on 2013-04-05
Dear Gentlepeople,

  A year later I decide to check to see if a new relaese of UbuntuStudio is available, as 12.04 would not work on most computers due to the PAE issue. I find it extremely annoying that in the welcome and download page, in fact nowhere do I see mention that you must have a newer computer with CPU capable of PAE (whatever that is). No mention whatsoever, that without PAE capability in your computer, you can forget about Ubuntu or any "flavor" of it.

What say You?  Am I wrong? 

Will Ubuntu or UbuntuStudio v12+ or v.13+ work with a non-PAE capable CPU? If no, then there should be a NOTICE TO ALL regarding this issue on all download pages. The NOTICE should also mention, What PAE means / is and which last stable version you can use with those computers.

We Need To Know!

Thanks,
hbnmgr

---

### Post by howefield on 2013-04-05
> **hbnmgr said:**
>  I find it extremely annoying that in the welcome and download page, in fact nowhere do I see mention that you must have a newer computer with CPU capable of PAE (whatever that is). No mention whatsoever, that without PAE capability in your computer, you can forget about Ubuntu or any "flavor" of it.hbnmgr

Can't find the release notes ?

---

### Post by Elfy on 2013-04-05
[https://bugs.launchpad.net/ubuntu-website-content/+filebug](https://bugs.launchpad.net/ubuntu-website-content/+filebug)

File a bug.

---

### Post by kostkon on 2013-04-05
> **hbnmgr said:**
> Dear Gentlepeople,

  A year later I decide to check to see if a new relaese of UbuntuStudio is available, as 12.04 would not work on most computers due to the PAE issue. I find it extremely annoying that in the welcome and download page, in fact nowhere do I see mention that you must have a newer computer with CPU capable of PAE (whatever that is). No mention whatsoever, that without PAE capability in your computer, you can forget about Ubuntu or any "flavor" of it.

What say You?  Am I wrong?
Yes, you are. Even Pentium 2s have PAE support. PAE was introduced in 1995, so it's not something new.

> **hbnmgr said:**
> Will Ubuntu or UbuntuStudio v12+ or v.13+ work with a non-PAE capable CPU? If no, then there should be a NOTICE TO ALL regarding this issue on all download pages. The NOTICE should also mention, What PAE means / is and which last stable version you can use with those computers.
Only a very small number of Pentium M CPUs lack PAE support, so there is not need to put anything on the download page, in my opinion.

Hope that helps.

---

### Post by hbnmgr on 2013-04-05
Apparently 'kostkon', 'elfy', and 'howefield' are not aware of the depth of this issue. It is not a bug, and yes I found the Release Notes and nothing mentioned about the PAE issue.

Here are some links regarding this issue.


[http://ubuntuforums.org/showthread.php?p=12089249#post12089249](http://ubuntuforums.org/showthread.php?p=12089249#post12089249)

How to Install v12.04 on Non PAE capable system
[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html)

Index - Non PAE
[http://people.canonical.com/~diwic/12.04-nonpae/](http://people.canonical.com/~diwic/12.04-nonpae/)

Kernel REQUIRES PAE - Unable to Boot
I think JerryLamos has the right idea in this thread
[http://ubuntuforums.org/showthread.php?t=1959675](http://ubuntuforums.org/showthread.php?t=1959675)

How to Non PAE issue
[http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)

Realese Notes
Under NEW FEATURES of v12.10

> Kernel 3.5.5
Transitioning of the i386 generic-pae flavor to become the generic flavor offering

What does that mean?
My CPU is AMD about 1.5Ghz.

hbnmgr

---

### Post by jejeman on 2013-04-05
Give
```
cat /proc/cpuinfo | grep name
```

---

### Post by mörgæs on 2013-04-05
> **hbnmgr said:**
> 
My CPU is AMD about 1.5Ghz.



Then you are not affected by the PAE 'problem'.
If you had one of the Pentium M's (400 MHz front side bus) then [Fake-PAE]("http://ubuntuforums.org/showthread.php?t=2113826") might help.

---

### Post by hbnmgr on 2013-04-05
Attempting to Upgrade to Ubuntu Studio v12.04 with DVD and get this message.

"This kernel requires the following features not present on the CPU:
pae
Unable to boot - please use a kernel appropriate for your CPU."

Have Toshiba Satellite S114.

> **jejeman said:**
> Give
```
cat /proc/cpuinfo | grep name
```

model name : Intel(R) Celeron(R) M Processor  1.3 Ghz

---

### Post by oldfred on 2013-04-05
[http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

   How To Install Ubuntu 12.04 On Non-PAE Capable Hardware.
[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more)
To see processor
lscpu
grep --color=always -i PAE /proc/cpuinfo

But the issue is, if system does not have PAE, it really does not have the capability to run full Ubuntu anymore. Ubuntu is a full featured systems and requires a lot of resources. It does run just fine on my 6 year old system as I have enough RAM. But many systems even with PAE, may not have enough RAM to run Ubuntu. Then you can run Xubuntu or more likely Lubuntu.

```
fred@fred-Precise:~$ grep --color=always -i PAE /proc/cpuinfo
flags        : fpu vme de pse tsc msr [COLOR=#ff0000]pae[/COLOR] mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow
flags        : fpu vme de pse tsc msr [COLOR=#ff0000]pae[/COLOR] mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow

```

---

### Post by kostkon on 2013-04-05
> **hbnmgr said:**
> model name : Intel(R) Celeron(R) M Processor  1.3 Ghz
So, your CPU is indeed a Pentium M that lacks PAE support.

---

### Post by hbnmgr on 2013-04-05
I am going to try Kubuntu v12.04
Will install and write back.
Thanks!

---

### Post by mörgæs on 2013-04-06
> **hbnmgr said:**
> I am going to try Kubuntu v12.04


You are of course welcome to try, but as Oldfred has already told you it is not going to work (without tweaking).
Xubuntu 12.04.2 works and is supported two years from now.

---

### Post by hbnmgr on 2013-04-08
Thanks 'oldfred', installed Kubuntu v12.04 LTS - Up and Running fine. 

Case Solved.
Thanks everyone for your patience and support.
hbnmgr

---

