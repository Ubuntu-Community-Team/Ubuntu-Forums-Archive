---
title: "AMD Ryzen unexpected irq trap at vector 07"
date: 2017-03-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Ben_Mather on 2017-03-07
Hello,

I have just upgraded my computer to AMD Ryzen with a Gigabyte Aorus AX370 Gaming 5 motherboard and when I boot into the Ubuntu LiveUSB I can't get past the Ubuntu splash screen, instead "unexpected irq trap at vector 07" continuously prints on-screen. This issue has also been reported over at [https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/amd-linux/935547-amd-ryzen-on-linux](https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/amd-linux/935547-amd-ryzen-on-linux) but is still unresolved.

Ryzen is fully compatible with the Linux 4.10 kernel so I've been attempting to install Ubuntu 17.04, but the same issue occurs for 16.10 and 16.04. I tried a Fedora 25 LiveUSB and it installed flawlessly, which tells me it is not a hardware fault. (Even though Fedora installs fine it is not my desired end-game - I would rather stick with Ubuntu!)

Other things I've noticed:
[LIST]
[*]Ubuntu will boot if acpi=off is set in the GRUB bootloader, but acpi=ht will not. 
[*]Error code 56 - Invalid CPU type or speed - will display on the motherboard whenever Ubuntu is booting. 
[*]I cannot find the source of the IRQ trap from ```
cat /proc/interupts
``` 
[/LIST]

Any help would be greatly appreciated!

---

### Post by javiervg on 2017-03-07
Hi Ben,

I built a system this week and I haven't been able to install Ubuntu due to the same error. Coincidentally, I also have the same mother board, [COLOR=#000000]Gigabyte Aorus AX370 Gaming 5 .[/COLOR] I have tried quite a few things and nothing has worked.

Someone claims that turning [COLOR=#333333][FONT=Ubuntu]acpi=off worked for them but I have not been able to do it since I have a new built. Not sure if that might help you. Also people are reporting updating to the latest Linux kernel, 4.11rc1, released this weekend, as a solution for their problems.

Good luck and and I would appreciate if you post here if you find a solution,

Javier[/FONT][/COLOR]

---

### Post by mastablasta on 2017-03-08
thanks for posting here, but at the same time it would be really good if you posted to launchpad, so that developers can have a look at it and fix it.

---

### Post by fiedzia on 2017-03-09
Reported here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1671360](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1671360)

---

### Post by QIII on 2017-03-09
That bug will be closed as incomplete soon.  There are no log files, etc, included.

---

### Post by rsandru on 2017-03-09
Same setup here and also affected: Gigabyte X370 Gaming 5 + 1700X.

---

### Post by QIII on 2017-03-09
I do not have a Ryzen system to test, but I did test installing the 4.11 rc1 kernel, which should support the Ryzen line.  

If anyone is interested or intrepid enough, you might give that a try.

WARNING WARNING WARNING:

The following may render you machine inoperable.  This information is provided at your risk for testing. You assume all responsibility for doing this.

For 64 bit systems.

```
cd /tmp
```


```
wget kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc1/linux-headers-4.11.0-041100rc1_4.11.0-041100rc1.201703051731_all.deb
```


```
wget kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc1/linux-headers-4.11.0-041100rc1-generic_4.11.0-041100rc1.201703051731_amd64.deb
```


```
wget kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc1/linux-image-4.11.0-041100rc1-generic_4.11.0-041100rc1.201703051731_amd64.deb
```

```
sudo dpkg -i linux-headers-4.11*.deb linux-image-4.11*.deb
```

```
sudo update-grub
```

Reboot.

To remove the kernel

```
sudo apt remove linux-headers-4.11* linux-image-4.11*
```

```
sudo update-grub
```

Reboot.

In reality, the grub update is not strictly necessary, but I'd recommend it anyway.

---

### Post by rsandru on 2017-03-09
I'm setting up a new system so there is no previous OS to upgrade. Is there a way to update the installation image on the USB drive to use a newer kernel?

---

