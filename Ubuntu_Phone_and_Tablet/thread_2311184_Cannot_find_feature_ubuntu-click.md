---
title: "Cannot find feature ubuntu-click"
date: 2016-01-25
forum: Ubuntu Phone and Tablet
---

### Post by gil-ildar on 2016-01-25
Hello! I have been created a new test project (from 'QML App with simple UI' template) for Ubuntu Touch. I can build it for host without any problems, but when I try build it for target (i386 emulator) then I get a error:
> 
Cannot find feature ubuntu-click

The problem code in project .pro file:
```

[COLOR=#FF9BA5]#load[/COLOR][COLOR=#FF9BA5]Ubuntu[/COLOR][COLOR=#FF9BA5]specific[/COLOR][COLOR=#FF9BA5]features
[/COLOR][COLOR=#73FF5D]load[/COLOR](ubuntu-click)

```

What I have to do to build it?

PS.
OS: KUbuntu 15.10
IDE: Ubuntu SDK (Qt Creator 3.5.0 based on Qt 5.4.2)

---

### Post by grahammechanical on 2016-01-25
I have no idea what you are taking about but could the problem be coming from emulating i386 CPUs and not AMD64 CPUs?

My 64 bit Ubuntu (16.04) desktop has click-ubuntu-policy installed by default and there are several click libraries that Synaptic Package Manager shows are in the repositories. But I wonder if that is true of a 32 bit version of Ubuntu.

Regards.

---

### Post by gil-ildar on 2016-01-25
Thank you for reply!
I have Ubuntu 15.10 x64. And in Ubuntu SDK IDE I can not create x86_64 emulator, only i386 and armhf
And I have click-ubuntu-policy and other click-packages on my host.

---

### Post by gil-ildar on 2016-01-27
I solved this problem by reinstalling ubuntu-sdk
```

$ sudo apt-get purge ubuntu-sdk*
$ sudo apt-get install ubuntu-sdk*

```

---

