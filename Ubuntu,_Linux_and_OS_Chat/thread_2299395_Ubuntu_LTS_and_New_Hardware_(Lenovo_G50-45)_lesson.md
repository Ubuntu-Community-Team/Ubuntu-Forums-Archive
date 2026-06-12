---
title: "Ubuntu LTS and New Hardware (Lenovo G50-45) lesson learnt."
date: 2015-10-18
forum: Ubuntu, Linux and OS Chat
---

### Post by kagashe on 2015-10-18
It will be almost one year since I bought new Laptop Lenovo G50-45 with Windows 8.1 pre-installed.
I had a choice to install Ubuntu 14.04 and 14.10 but I had chosen 14.04 being LTS and since I had used Ubuntu for 10 years I knew about LTS/Hardware Enablement Stack.
After installing I went for fglrx Proprietary Driver which solved the issue of adjusting the Back-light Brightness.
The Wifi had issues which got resolved by editing the configuration:
```
echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Update on 12th April 2015 broke the proprietary fglrx driver and I had to remove it. I went for Hardware Enablement Stack which brought working open source radeon driver (for my Laptop) on Linux Kernel 3.16.

[B]If I had chosen Ubuntu 14.10 instead of 14.04 this problem would not have come.
[/B]
The Blue-tooth did not work at all and after installing driver from ppa it worked once in ten boots, on Ubuntu 15.04 the situation was a little better but not satisfactory. I came to know that the actual Driver will work on Linux Kernel 4.2.

I waited for Linux Kernel 4.2 to arrive on Ubuntu 15.10 and immediately downloaded the Daily image when I learnt that the Kernel was upgraded to 4.2. Although Ubiquity had issues I installed using following workaround:
```
sudo -H bash -c 'ubiquity gtk_ui'
```

Blue-tooth started working but sometimes the Laptop did not accept files from Android Phone although the Music played on Android Phone could be heard on Laptop Speakers through Blue-tooth.

After couple of updates the File Transfer on Blue-tooth became flawless.

Lesson Learnt: It takes time for Ubuntu to catch up with new hardware but you should not stick to LTS version and try the newest and development if required.

Kamalakar

---

### Post by sudodus on 2015-10-18
Interesting. Thanks for sharing your experience :-)

---

### Post by mastablasta on 2015-10-20
well that makes sense. the kernel in LTS was probably form like dec 2013 or something like that. for new hardware, new kernel is a must. and so is HWE stack. or better yet just use the releasaes in between. sometimes even those are too old and in those cases other distros are necessary. or windows :P

---

