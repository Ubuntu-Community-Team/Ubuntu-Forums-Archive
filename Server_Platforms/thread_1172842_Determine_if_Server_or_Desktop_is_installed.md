---
title: "Determine if Server or Desktop is installed"
date: 2009-05-29
forum: Server Platforms
---

### Post by hictio on 2009-05-29
Is there a way to determine which Ubuntu version (not release) is installed on a given system?
I want to determine if this particular box has Ubuntu Server or a stripped down Desktop plain vanilla Desktop edition.

I know about lsb_release & '/etc/issue', but on the system I have at hand, Jaunty, they don't print ding about that.

TIA :D

---

### Post by netJackDaw on 2009-05-29
The command:

uname -a

will give you information about which kernel is running. My desktop says something like:

Linux computername 2.6.xx-yy-generic #...

and my server says someting like:

Linux computername 2.6.xx-yy-server #...

Hope this helps

---

### Post by cdenley on 2009-05-29
They're both the same distro with different default configurations/kernels. If you install desktop packages and the generic kernel on a server "version", then it becomes a desktop "version", possibly with some server packages installed. This isn't like windows. When there isn't a pricing scheme, there is no reason to limit what desktop installs are capable of.

---

### Post by netJackDaw on 2009-05-29
Still it is good to know since server and desktop kernels are optimized in different ways. A desktop installation also comes with "unnecessary" daemons if you run is as a server.

Most important of all is the support periods, which for LTS versions of Ubuntu is five years but only three for desktops. Intermediate versions have support periods of 18 months server and laptop alike.

---

### Post by cdenley on 2009-05-29
> **netJackDaw said:**
> Still it is good to know since server and desktop kernels are optimized in different ways. A desktop installation also comes with "unnecessary" daemons if you run is as a server.

Most important of all is the support periods, which for LTS versions of Ubuntu is five years but only three for desktops. Intermediate versions have support periods of 18 months server and laptop alike.

Kernels can easily be switched. Also, hictio said his ubuntu was "stripped down", so the "unnecessary" daemons probably weren't installed. If it didn't have a GUI and wasn't a server install, then it was probably installed with the alternate installer, or a net installer, in which case the argument can be made that it was neither "desktop" or "server" version. Anyway, my point was that there are no different "versions", they are all the same OS. It helps to know what kernel you are using, though.

I've never seen documentation about this, but I think the support in LTS for server releases after the desktop EOL is for server-related packages, not necessarily a system originally installed with a server installer. If you install gnome on an ubuntu server, gnome will not be supported after desktop EOL. If you install server packages on a minimal ubuntu install, you will be fully supported until server EOL.

meta-package equivalents:
```

desktop = ubuntu-desktop + linux-generic
server = ubuntu-standard + linux-server

```
Of course you can have any combination of the above. There are also realtime kernels and virtual machine optimized kernels. Also, for a leaner install, there is a ubuntu-minimal meta-package.

---

### Post by netJackDaw on 2009-05-29
Just trying to answer questions as clear as possible... Agree that the support in LTS is for server related packages. ...and you shouldn't install GUI on a server, but that's another story..

---

### Post by hictio on 2009-06-04
Thanks for the replies and please excuse the delay getting back, being really busy.
This is what uname prints:

```

~$ uname -a
Linux FQDN.here 2.6.28-6-386 #20-Ubuntu Fri Apr 17 08:32:39 UTC 2009 i586 GNU/Linux

```

This is a Ubuntu Server install I did, from a [Minimal CD image](https://help.ubuntu.com/community/Installation/MinimalCD), and then choosing "Standard Ubuntu Server" (IIRC the exact wording), I seem to recall I did choose a kernel upon installation, so, the thing is, if I depart from the standard, there is no way of knowing if this is a Server or Desktop install? Am I correct?

TIA

---

### Post by cdenley on 2009-06-04
> **hictio said:**
> Thanks for the replies and please excuse the delay getting back, being really busy.
This is what uname prints:

```

~$ uname -a
Linux FQDN.here 2.6.28-6-386 #20-Ubuntu Fri Apr 17 08:32:39 UTC 2009 i586 GNU/Linux

```

This is a Ubuntu Server install I did, from a [Minimal CD image](https://help.ubuntu.com/community/Installation/MinimalCD), and then choosing "Standard Ubuntu Server" (IIRC the exact wording), I seem to recall I did choose a kernel upon installation, so, the thing is, if I depart from the standard, there is no way of knowing if this is a Server or Desktop install? Am I correct?

TIA

As I already explained, terms like "server install" and "desktop install" are meaningless. You appear to be running a kernel which I'm assuming has very little optimizations in order to be compatible with any x86 CPU. This isn't the default for a desktop or server install. You can install either one, though.

"Desktop" kernel
```

sudo apt-get install linux-generic

```

Server kernel
```

sudo apt-get install linux-server

```

If you want to choose from all sorts of default configurations, even server configurations:
```

sudo tasksel

```

---

### Post by netztier on 2009-06-04
> **hictio said:**
> so, the thing is, if I depart from the standard, there is no way of knowing if this is a Server or Desktop install? Am I correct?


I would tend to agree - it's neither "Desktop" nor "Server". 

As others said, there is no real "difference" in what makes Ubuntu Desktop and what makes Ubuntu Server - they're just each a compilation of software packages (from a single, common repository) on a downloadable CD image.

The packages you'll find on the Ubuntu Desktop CD are geared towards general-purpose desktop use, the ones on the Ubuntu Server CD for a general-purpose server. 

The one important software package that stands out is the kernel, with a general-purpose kernel for Ubuntu Desktop and a server-optimized one for Ubuntu-Server. Any other software you add to the system, like openssh-server, mysql, apache or BIND is the same.

If you started off the minimal CD, you now have a "custom compilation" of software packages - which you can keep and continue to customize. The output of **uname -a** tells that the 2.6.28-6**-386** kernel version is installed. I would suggest to replace this by it's **...-server** sibling.

There are so-called "meta packages", which are just pointers to the currently most suggested version:

```
user#@host:~$ **aptitude search linux-image**
p   linux-image-2.6.25-2-386                                                                                       - Linux kernel image for version 2.6.25 on i386                                                                           
p   linux-image-2.6.27-10-generic                                                                                  - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-10-server                                                                                   - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-10-virtual                                                                                  - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
i   linux-image-2.6.27-11-generic                                                                                  - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-11-server                                                                                   - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-11-virtual                                                                                  - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-12-generic                                                                                  - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-12-server                                                                                   - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-12-virtual                                                                                  - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-13-generic                                                                                  - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-13-server                                                                                   - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-13-virtual                                                                                  - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
i   linux-image-2.6.27-14-generic                                                                                  - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-14-server                                                                                   - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-14-virtual                                                                                  - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-3-rt                                                                                        - Linux kernel image for version 2.6.27 on Ingo Molnar's full real time preemption patch (2.6.26.5-rt9)                   
c   linux-image-2.6.27-7-generic                                                                                   - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-7-server                                                                                    - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-7-virtual                                                                                   - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
i   linux-image-2.6.27-9-generic                                                                                   - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-9-server                                                                                    - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   linux-image-2.6.27-9-virtual                                                                                   - Linux kernel image for version 2.6.27 on x86/x86_64                                                                     
p   **linux-image-386**                                                                                                - Linux kernel image on 386.                                                                                              
i   **linux-image-generic**                                                                                            - Generic Linux kernel image                                                                                              
p   **linux-image-rt**                                                                                                 - Rt Linux kernel image                                                                                                   
p   **linux-image-server**                                                                                             - Linux kernel image on Server Equipment.                                                                                 
p   **linux-image-virtual**                                                                                            - Linux kernel image for virtual machines 

```

The same goes for the package that contains some additional kernel modules (to make some hardware work properly), look at the output of 

```
user#@host:~$ **aptitude search restricted-modules**
```

So now you can install the most recent server kernel together with the restricted-modules

```
user#@host:~$ **sudo aptitude install linux-image-server linux-restricted-modules-server**
```

To "convert" your current installation into Ubuntu "Server". Don't forget to reboot, of course.

regards

Marc

---

### Post by cdenley on 2009-06-04
FYI, I don't think restricted modules are installed on a default server configuration. I'm not sure if they're considered untrustworthy, unreliable, or both. The only reason I can think of for installing it would be for a wireless card or a video card.

---

