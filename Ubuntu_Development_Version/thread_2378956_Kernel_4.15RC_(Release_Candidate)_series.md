---
title: "Kernel 4.15RC (Release Candidate) series"
date: 2017-11-29
forum: Ubuntu Development Version
---

### Post by Doug S on 2017-11-29
[Kernel 4.15-rc1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15-rc1/") has been available for a few days. I have been running it for about a day without issues.

---

### Post by Doug S on 2017-12-11
[Kernel 4.15-rc3 ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15-rc3/")is available. I missed -rc2, but do notice 131 kernel configuration changes between -rc1 and -rc3.

---

### Post by fyfe54 on 2017-12-11
I have just moved to rc3 from rc2 and must say that (for me) it has been trouble free.

---

### Post by P-I H on 2017-12-16
Couldn't wait. Installed RC3
I was curious about the temperature readings that's supported in the 4.15 kernel.

Ryzen 7 1700 clocked at 3.75 GHz
```
Ambient temp about 21 Celsius


Idle about 0% CPU
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +33.8°C  (high = +70.0°C)


CIV VI about 20% CPU
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +46.8°C  (high = +70.0°C)


Handbrake about 85% CPU
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +71.0°C  (high = +70.0°C)



```

---

### Post by tenshinoneko2 on 2017-12-22
Do you know if 4.15RCs r going to be available? or will it be available once its released officially?

---

### Post by P-I H on 2017-12-22
There is an instruction on this page
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by Yellow Pasque on 2017-12-23
> **tenshinoneko2 said:**
> Do you know if 4.15RCs r going to be available? or will it be available once its released officially?

[https://insights.ubuntu.com/2017/12/06/kernel-team-summary-december-6-2017/](https://insights.ubuntu.com/2017/12/06/kernel-team-summary-december-6-2017/)

> we are tentatively planning to converge on 4.15 for the Bionic Beaver 18.04 LTS release.
On the road to 18.04 we have a 4.14 based kernel in the Bionic -proposed repository. 

---

### Post by Yellow Pasque on 2017-12-23
Oh, and rc4 is available: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15-rc4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15-rc4/)

---

### Post by tenshinoneko2 on 2017-12-23
Thank you :D

---

### Post by Doug S on 2017-12-24
kernel 4.15-rc5 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15-rc5/"). I missed -rc4.

---

### Post by xeizoo on 2017-12-30
4.15-rc5 do not work with my Nvidia GTX1070 on 18.04 Daily, it starts looping halfway through boot. But 4.14-13 works just fine.

edit. I seem to recall now that it is normal, historically Nvidia usually doesn't start working until RC8 or so, don't know why but it is repeating itself each cycle  :)

---

### Post by xeizoo on 2018-01-03
4.15-rc6 doesn't work with Nvidia too, same failure to compile kernel module for Nvidia. 4.14 works great, compiles the Nvidia module with no probs. 

It would be interesting to test 4.15 to see how much performance is lost with the new security patch for Intel, one would probably not want to flip it off since that would mean all internet is kinda insecure. Like it is right now with all kernels without the patch, there are no known exploit as of yet but they are likely to pop up soon. So, we need 4.15 rather quickly.

---

### Post by Doug S on 2018-01-03
> **xeizoo said:**
> It would be interesting to test 4.15 to see how much performance is lost with the new security patch for Intel, one would probably not want to flip it off since that would mean all internet is kinda insecure. Like it is right now with all kernels without the patch, there are no known exploit as of yet but they are likely to pop up soon. So, we need 4.15 rather quickly.Yes, actual performance drop information would be useful. I compiled a 4.15-rc6 kernel with the new kernel configuration parameter, PAGE_TABLE_ISOLATION, set and it didn't seem to make any difference (based only on one clean kernel compile time), around 25 minutes either way. See also [here]("https://www.phoronix.com/scan.php?page=article&item=linux-415-x86pti&num=1"), which also didn't show a difference in kernel compile time, but did in other tests.

EDIT: see also [here]("https://www.phoronix.com/scan.php?page=article&item=linux-more-x86pti&num=1")

---

### Post by xeizoo on 2018-01-05
So 18.04 did get a new patched 4.14 kernel today, runs fine, don't know about performance yet. Image shows cpu_insecure flag meaning the patch is in effect:

[IMG]https://3.bp.blogspot.com/-Xv8s5aZ1zQY/Wk-9THwZcGI/AAAAAAAA0QU/PWya6kv4S3MzS5K1KZYOe0o80oFA8_pegCLcBGAs/s1600/meltdown.jpg[/IMG]

So I benchmarked in Geekbench 4, multi 2.21% slower after patch and single is 0.2% slower, not a big deal imho. One can live with it.

---

### Post by Doug S on 2018-01-22
There is a very rare [-rc9]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15-rc9/") this cycle. see [here]("https://marc.info/?l=linux-kernel&m=151657239531019&w=2").

---

### Post by #&amp;thj^% on 2018-01-22
Thanks Doug:
I am happy they did fix this one:
```
Cong Wang (2):
      tipc: fix a memory leak in tipc_nl_node_get_link()
      tun: fix a memory leak for tfile->tx_array
```
How is it running for you? I see a few stutters here and there, very small and few and far between..

---

### Post by Doug S on 2018-01-22
> **1fallen said:**
> How is it running for you?It has been O.K. for me. I have only been running -rc9 for a few hours now. I missed -rc7 and -rc8 and did some [performance comparisons]("https://ubuntuforums.org/showthread.php?t=2381801&p=13726977#post13726977") with -rc6 (which I should really re-do with -rc9, as things have been so dynamic).

---

### Post by VMC on 2018-02-06
I'm getting "do_IRQ: 0.55 No irq handler for vector" on boot up using 4.15 with [s]nvidia[/s]. There's several issues regarding this:
[do_irq_error]("https://www.google.com/search?ei=B3h6Wu2GL8bGjwOB9KuwBA&q=%22do_IRQ%3A+0.55+No+irq+handler+for+vector%22&oq=%22do_IRQ%3A+0.55+No+irq+handler+for+vector%22&gs_l=psy-ab.12...0.0.0.13793.0.0.0.0.0.0.0.0..0.0....0...1c..64.psy-ab..0.0.0....0.RPA4UTPlL74")

Linus and others are talking about timing issues on the last link.

---

