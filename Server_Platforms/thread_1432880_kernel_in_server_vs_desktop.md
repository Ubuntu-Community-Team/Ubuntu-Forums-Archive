---
title: "kernel in server vs desktop"
date: 2010-03-18
forum: Server Platforms
---

### Post by jim001 on 2010-03-18
Hi
 
Is the kernel and core system same in server and desktop 9.10?
How do I update/upgrade server similar to what update manager does in desktop?
 
Thanks

---

### Post by cdenley on 2010-03-18
The core system is the same. There is a different kernel used by default.

to install the desktop kernel:
```

sudo apt-get install linux-generic

```

to install the server kernel:
```

sudo apt-get install linux-server

```

to install updates:
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by jrssystemsnet on 2010-03-18
> **jim001 said:**
> Is the kernel and core system same in server and desktop 9.10?One of the bigger differences between the server kernel and the desktop kernel is that, on i386 systems, the server kernel enables PAE (to access 4GB or more of system RAM) whereas the desktop kernel does not.

There are some other differences, but if you're not in a pretty serious production environment, that's likely to be the only one you'd really notice.

---

### Post by cdenley on 2010-03-18
> **jrssystemsnet said:**
> One of the bigger differences between the server kernel and the desktop kernel is that, on i386 systems, the server kernel enables PAE (to access 4GB or more of system RAM) whereas the desktop kernel does not.

There are some other differences, but if you're not in a pretty serious production environment, that's likely to be the only one you'd really notice.

If I'm not mistaken, there doesn't seem to be any restricted modules available for the server kernel anymore. There used to be, but the way the dependencies were, installing new server kernels wouldn't install the restricted modules for that kernel.

---

### Post by jim001 on 2010-03-18
Hi
 
Is it possible to use server kernel on desktop and vice versa?
 
Thanks

---

### Post by jrssystemsnet on 2010-03-18
> **cdenley said:**
> If I'm not mistaken, there doesn't seem to be any restricted modules available for the server kernel anymore. There used to be, but the way the dependencies were, installing new server kernels wouldn't install the restricted modules for that kernel.

Well, I dunno about Karmic, but that wasn't true for Intrepid - before Adobe released their 64-bit beta of Flash, I was running a 32-bit server kernel on my nvidia-powered dual-monitor workstation so that I could access all 8GB of my RAM without having to cope with ndiswrapper and crashing browsers.

Since Adobe finally released the 64-bit Flash beta, I haven't played with a Server kernel on a desktop, so Intrepid is the last of my direct experience with Sever anywhere other than a headless box. :)

---

### Post by jrssystemsnet on 2010-03-18
> **jim001 said:**
> Hi
 
Is it possible to use server kernel on desktop and vice versa?
 
Thanks

cdenley answered that question already.  complete with instructions as to how to do it.

---

### Post by cdenley on 2010-03-18
> **jrssystemsnet said:**
> Well, I dunno about Karmic, but that wasn't true for Intrepid

Which is why I said there used to be.
[http://packages.ubuntu.com/search?keywords=linux-restricted-modules-server&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=linux-restricted-modules-server&searchon=names&exact=1&suite=all&section=all)

---

### Post by FuturePilot on 2010-03-18
The linux-restricted-modules packages are deprecated. All third party modules are using DKMS now.

---

### Post by cdenley on 2010-03-18
> **FuturePilot said:**
> The linux-restricted-modules packages are deprecated. All third party modules are using DKMS now.

I see. I would assume the modules would be in both kernels then?

---

### Post by FuturePilot on 2010-03-18
> **cdenley said:**
> I see. I would assume the modules would be in both kernels then?

Yes.

---

### Post by jim001 on 2010-03-18
When you install linux-generic or linux-server - will it configure boot menu, so you can choose kernel to boot the system from?
 
When you install server kernel on desktop and if you boot with server kernel, will desktop screen still be launched or you will get console login?
 
How is desktop screen insterface tied up with kernel and system startup?
 
Thanks

---

### Post by cdenley on 2010-03-18
> **jim001 said:**
> When you install linux-generic or linux-server - will it configure boot menu, so you can choose kernel to boot the system from?

Yes.
> **jim001 said:**
> 
When you install server kernel on desktop and if you boot with server kernel, will desktop screen still be launched or you will get console login?

If gdm is installed and wasn't disabled, then it will start at boot.
> **jim001 said:**
> 
How is desktop screen insterface tied up with kernel and system startup?

The desktop environment will work regardless of kernel. Startup would behave the same. As already said, there won't really be a noticeable difference between the two kernels. The graphical login is called "gdm". If you don't want a graphical login, you can remove gdm, or [disable it from starting on boot]("http://ubuntuforums.org/showpost.php?p=8196273&postcount=8").

---

### Post by cdenley on 2010-03-18
[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

---

### Post by jim001 on 2010-03-22
Hi

My boot menu has multiple kernel entries to choose from due to kernel upgrades.
How can I remove unwanted kernel version completely?

Is disabling gdm(or not starting at boot) directly tied up with not launching Xwindow interface similar to desktop interface?

Thanks

---

### Post by cdenley on 2010-03-22
> **jim001 said:**
> Hi

My boot menu has multiple kernel entries to choose from due to kernel upgrades.
How can I remove unwanted kernel version completely?

Easiest way would be to remove the unwanted kernels. This command will list the kernels you currently have installed.
```

dpkg -l linux-image-*|grep "^ii "

```
> **jim001 said:**
> 
Is disabling gdm(or not starting at boot) directly tied up with not launching Xwindow interface similar to desktop interface?


GDM is the graphical login manager. Without it, you get the terminal console login prompt, which would give you a terminal when you login. The only way to start any kind of graphic interface would be from the terminal.

---

