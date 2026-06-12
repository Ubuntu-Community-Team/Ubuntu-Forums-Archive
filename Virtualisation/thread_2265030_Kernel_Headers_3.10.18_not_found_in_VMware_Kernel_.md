---
title: "Kernel Headers 3.10.18 not found in VMware Kernel Module Updater - Ubuntu 14.10"
date: 2015-02-12
forum: Virtualisation
---

### Post by AGeekofMuch2Learn on 2015-02-12
[COLOR=#333333][FONT=UbuntuRegular]I had Ubuntu 14.10 and VMware Player 7.0.0 installed on my Acer Chromebook 11. Wwhen I open VMware, I get the exact same error message as mentioned this thread - "[What is the path to the kernel headers so I can install vmware?]("http://askubuntu.com/questions/40979/what-is-the-path-to-the-kernel-headers-so-i-can-install-vmware?newreg=79b443032c2e4d498b84086ab72906b0")", except it is "Kernel Headers 3.10.18", not "2.6.38-8-generic". I tried every suggestion in that thread, but to no avail. Can someone please help me?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Your suggestion is much appreciated! Thank you so much![/FONT][/COLOR]

---

### Post by ajgreeny on 2015-02-12
I suggest you install synaptic first, then use that to search for and install the correct **linux-headers** version packages (probably two of them) for your current kernel.

---

### Post by AGeekofMuch2Learn on 2015-02-12
[SIZE=4][FONT=arial]I run "apt-get install linux-headers-generic" before and installed 3.16.0-24, 3.16.0-30 and 3.16.0-30-generic. I also installed the synaptic and only saw linux-headers of different versions of 3.16.0. I also run [/FONT][/SIZE][COLOR=#333333][FONT=Arial][SIZE=4][FONT=arial]"apt-get install build-essential linux-headers-$(uname -r)", which came back telling me "could n't get lock /var/lib/dpkg/lock - open (11: resource temporarily unavailable)". It seems my ubuntu doesn't have 3.10.18 at all, or for some reason, I missed finding this header.[/FONT][/SIZE]
[/FONT][/COLOR]

---

### Post by ajgreeny on 2015-02-12
Please use the default font!

What kernel are you really using?
Show the output of **uname -a**

If synaptic was still open when you ran the apt-get install commnd, that is why you saw the lock error; close synaptic and try again, but make sure you get the correct header packages, ie, tyhe same version as the **uname -a** kernel output.

---

### Post by sammiev on 2015-02-12
this should work or what I use

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

this is what you have posted

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

---

