---
title: "Bionic + 4.16 kernel"
date: 2018-04-09
forum: Ubuntu Development Version
---

### Post by makitso on 2018-04-09
I am running daily Bionic but have installed the 4.16 kernel.  I know the up side of this action but wondering what the down side is?

---

### Post by PaulW2U on 2018-04-09
> **makitso said:**
> I am running daily Bionic but have installed the 4.16 kernel.  I know the up side of this action but wondering what the down side is?
I'm assuming you've installed from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds) states:
> Does the kernel team support the mainline kernel builds?

The mainline kernel builds are produced for debugging purposes and therefore come with no support. Use them at your own risk. 

Fine for testing but I think I'm right in saying that none of these kernels have been updated by the [Ubuntu Kernel team]("https://wiki.ubuntu.com/KernelTeam") with any patches that they might think are required before general release to the Ubuntu community. I'm not sure that every mainline build actually makes it into Ubuntu anyway.

---

### Post by cruzer001 on 2018-04-09
The down side for me, virtualbox didn't work.  But that was rc1.  Haven't tried it since.

---

### Post by monkeybrain20122 on 2018-04-09
Same here, so far no downside. Wifi doesn't work for my card in kernel 4.15, so I have compiled a custom kernel from source with a wifi patch (that time the patch has not been merged upstream yet so mailine kernels wouldn't work) I am wondering what might happen when Nvidia driver updates.

---

### Post by makitso on 2018-04-09
Yes, I installed using the files from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16/)

Have 4.16 installed on 4 hardware systems (3 with xubuntu and 1 with Ubuntu)  the most complex runs  LAMP and Virtualbox.  So far everything works very well.

---

### Post by cruzer001 on 2018-04-10
Good to know, thanks.

---

