---
title: "Ubuntu 13.10 - Kernel 3.12rc4 - CPU scaling not working right"
date: 2013-10-10
forum: Ubuntu Development Version
---

### Post by rimez on 2013-10-10
Hi all,

I need to use the 3.12 kernel because of my hardware so I compiled it according to the[ instructions here]("http://ubuntuforums.org/showthread.php?t=2177674&p=12803771#post12803771"). The kernel is working great except for the fact that scaling doesn't appear to be working right OR cpu indicator is broken. 

Here's the scaling indicator under the 3.12 kernel: 
[IMG]http://i.imm.io/1i1yh.png[/IMG]

And here it is on the same machine with the 3.11 kernel that ships with Ubuntu 13.10: 
[IMG]http://i.imm.io/1i1yI.png[/IMG]


Can anyone help me to understand why it's different?  Is there something specific in the kernel config that needs to be selected? The scaling options were already selected: 
[IMG]http://i.imm.io/1i1zr.png[/IMG]

Any advice or help would be most appreciated. 

Cheers,
Rimez

---

### Post by JMB74 on 2013-10-10
The latest kernels run with the intel pstate driver active by default rather than the old acpi-cpufreq. So on your self compiled kernel you are seeing that, as you do not manually set frequency with that and only have a performance or powersave setting.

Now ubuntu decided on reports that the new driver was a bit buggy for some people, so patched their kernel builds to enable the old acpi-cpufreq scaling driver by default. Which is what you see when you are running the 3.11 kernel. hence I think why you are seeing different options with the two kernels? The indicator applet only offers valid option for the running scaling driver.

If you want to run the old acpi-cpufreq driver on your self compiled 3.12 then add **intel_pstate=disable** to your boot command line or append to the default in /etc/default/grub and then update-grub.

Or the other way around append **intel_pstate=enable** to the ubuntu 3.11 kernel to enable the new driver for that.

---

### Post by JMB74 on 2013-10-10
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1188647](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1188647) for reference.

---

### Post by rimez on 2013-10-10
> **JMB74 said:**
> The latest kernels run with the intel pstate driver active by default rather than the old acpi-cpufreq. So on your self compiled kernel you are seeing that, as you do not manually set frequency with that and only have a performance or powersave setting.

Now ubuntu decided on reports that the new driver was a bit buggy for some people, so patched their kernel builds to enable the old acpi-cpufreq scaling driver by default. Which is what you see when you are running the 3.11 kernel. hence I think why you are seeing different options with the two kernels? The indicator applet only offers valid option for the running scaling driver.

If you want to run the old acpi-cpufreq driver on your self compiled 3.12 then add **intel_pstate=disable** to your boot command line or append to the default in /etc/default/grub and then update-grub.

Or the other way around append **intel_pstate=enable** to the ubuntu 3.11 kernel to enable the new driver for that.

Thanks a million. That did the trick. It was driving me nuts.

---

### Post by JMB74 on 2013-10-10
No probs. The pstate driver should be better than the old cpufreq driver either now or in the not too distant future. For me at the moment though it results in this laptop running around 10 degrees hotter, so I'm defaulting back to the old driver until it sports itself out in stable kernels.

---

### Post by Linuxisfast on 2013-10-10
Pstate works beautifully when combined with Intel Thermal Daemon. Under load it keeps multi core laptops cool and benchmark better than typical cases where programs crash, abruptly slow down and laptops shut off due to high heat. Also battery consumption on laptops is far lower when combined with TLP.

---

### Post by wittyman37 on 2013-10-26
> **JMB74 said:**
> The latest kernels run with the intel pstate driver active by default rather than the old acpi-cpufreq. So on your self compiled kernel you are seeing that, as you do not manually set frequency with that and only have a performance or powersave setting.

Now ubuntu decided on reports that the new driver was a bit buggy for some people, so patched their kernel builds to enable the old acpi-cpufreq scaling driver by default. Which is what you see when you are running the 3.11 kernel. hence I think why you are seeing different options with the two kernels? The indicator applet only offers valid option for the running scaling driver.

If you want to run the old acpi-cpufreq driver on your self compiled 3.12 then add **intel_pstate=disable** to your boot command line or append to the default in /etc/default/grub and then update-grub.

Or the other way around append **intel_pstate=enable** to the ubuntu 3.11 kernel to enable the new driver for that.

This seems to work well for my Phenom II x4 960T and Ubuntu 13.10!  She runs cooler and faster over-clocked!  I am using the open source Gallium with me HD6670 card and L4D2 and Dota 2 run really smooth at medium settings; however, I get periodic freezing with looping sound that lasts between 5-50 seconds!  Any ideas?

---

### Post by Doug S on 2013-10-26
> **wittyman37 said:**
> This seems to work well for my Phenom II x4 960T and Ubuntu 13.10!  She runs cooler and faster over-clocked!  I am using the open source Gallium with me HD6670 card and L4D2 and Dota 2 run really smooth at medium settings; however, I get periodic freezing with looping sound that lasts between 5-50 seconds!  Any ideas?are you saying that you have this 5-50 seconds freeze problem when using the intel_pstate driver, but no freeze problem when you use the apci-cpufreq driver? And you can repeat the freeze / no freeze condition over multiple re-boots with only the single change as to which driver is used? Which method are you using, the stock 13.10 setup or with the 3.12RC6 (as that is now the latest upstream) kernel?

Edit: Doesn't "Phenom II x4 960T" mean an AMD CPU, in which case the intel_pstate driver does not apply?

---

### Post by wittyman37 on 2013-10-26
> **Doug S said:**
> are you saying that you have this 5-50 seconds freeze problem when using the intel_pstate driver, but no freeze problem when you use the apci-cpufreq driver? And you can repeat the freeze / no freeze condition over multiple re-boots with only the single change as to which driver is used? Which method are you using, the stock 13.10 setup or with the 3.12RC6 (as that is now the latest upstream) kernel?

Edit: Doesn't "Phenom II x4 960T" mean an AMD CPU, in which case the intel_pstate driver does not apply?

The intel_pstate does seem to make a difference with my AMD CPU.  My problem with freezing is not associated with intel_pstate.  It occurs with the open source Gallium driver in 3D games, but does not occur with the proprietary Catalyst driver.  I like Gallium because my desktop is smoother and the 3D games are smoother at medium settings except for the infernal freezing with looping 1 sec audio (not cool when playing VS or Dota 2!)

---

### Post by Doug S on 2013-10-26
> **wittyman37 said:**
> The intel_pstate does seem to make a difference with my AMD CPU....I can not understand how, the driver should realize that it doesn't support your CPU and fall through to the acpi-cpufreq driver. While trying to use the intel_pstate driver, what do you get for this?:```
doug@s15:~/temp$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
```

---

### Post by wittyman37 on 2013-10-26
> **Doug S said:**
> I can not understand how, the driver should realize that it doesn't support your CPU and fall through to the acpi-cpufreq driver. While trying to use the intel_pstate driver, what do you get for this?:```
doug@s15:~/temp$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
```

You are right!  Doh!
```
$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq

```

---

### Post by wittyman37 on 2013-10-26
I am going to undo that intel_pstate addition to grub, and try installing kernel 3.12rc6 as per [this site]("http://linuxg.net/how-to-install-kernel-3-12-rc-6-on-ubuntu-linux-mint-debian-crunchbang-pear-os-and-elementary-os/") so wish me luck!

---

### Post by cariboo on 2013-10-26
@wittyman37  3.12-rc6 is available [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc6-saucy/"). There's no need to follow any tutorials, just download the packages, and use:

```
sudo dpkg -i *deb
```

to install.

---

