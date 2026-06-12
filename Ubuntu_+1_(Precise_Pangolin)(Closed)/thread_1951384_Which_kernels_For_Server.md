---
title: "Which kernels? For Server"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Skaperen on 2012-04-02
I was trying to replace the desktop kernel installed with Xubuntu with the server kernel.  I still get a generic kernel.  Are they really just the same now days?  The machine is intended to run as a server on server class hardware (e.g. 10-core, up to 256G) and I want to be sure I've got a kernel that is configured for a server like that.  Installed Xubuntu because we do need an X server on these machines, too (one of our apps won't run unless it can run on X, and X by other means slows it down).

Xubuntu 12.04 Beta2 amd64

---

### Post by xebian on 2012-04-02
> **Skaperen said:**
> I was trying to replace the desktop kernel installed with Xubuntu with the server kernel.  I still get a generic kernel.  Are they really just the same now days?  The machine is intended to run as a server on server class hardware (e.g. 10-core, up to 256G) and I want to be sure I've got a kernel that is configured for a server like that.  Installed Xubuntu because we do need an X server on these machines, too (one of our apps won't run unless it can run on X, and X by other means slows it down).

Xubuntu 12.04 Beta2 amd64

Available kernel.  Looks like the one on red is the one you are looking for?

```

p   linux-image                                         - Generic Linux kernel image.                                  
p   linux-image:i386                                    - Generic Linux kernel image.                                  
v   linux-image-3.0                                     -                                                              
v   linux-image-3.0:i386                                -                                                              
p   linux-image-3.2.0-20-lowlatency                     - Linux kernel image for version 3.2.0 on x86/x86_64           
p   linux-image-3.2.0-20-lowlatency:i386                - Linux kernel image for version 3.2.0 on x86/x86_64           
p   linux-image-3.2.0-20-lowlatency-pae:i386            - Linux kernel image for version 3.2.0 on x86                  
i   linux-image-3.2.0-21-generic                        - Linux kernel image for version 3.2.0 on 64 bit x86 SMP       
p   linux-image-3.2.0-21-generic:i386                   - Linux kernel image for version 3.2.0 on 64 bit x86 SMP       
p   linux-image-3.2.0-21-generic-pae:i386               - Linux kernel image for version 3.2.0 on 64 bit x86 SMP       
p   linux-image-3.2.0-21-lowlatency                     - Linux kernel image for version 3.2.0 on x86/x86_64           
p   linux-image-3.2.0-21-lowlatency:i386                - Linux kernel image for version 3.2.0 on x86/x86_64           
p   linux-image-3.2.0-21-lowlatency-pae:i386            - Linux kernel image for version 3.2.0 on x86                  
p   linux-image-3.2.0-21-virtual                        - Linux kernel image for version 3.2.0 on 64 bit x86 Virtual Gu
p   linux-image-3.2.0-21-virtual:i386                   - Linux kernel image for version 3.2.0 on 64 bit x86 Virtual Gu
v   linux-image-3.4                                     -                                                              
i   linux-image-3.4.0-rc1-ik0                           - Linux kernel binary image for version 3.4.0-rc1-ik0          
p   linux-image-extra-3.2.0-21-virtual                  - Linux kernel image for version 3.2.0 on 64 bit x86 Virtual Gu
p   linux-image-extra-3.2.0-21-virtual:i386             - Linux kernel image for version 3.2.0 on 64 bit x86 Virtual Gu
p   linux-image-extra-virtual                           - Linux kernel extra modules for virtual machines              
p   linux-image-extra-virtual:i386                      - Linux kernel extra modules for virtual machines              
i   linux-image-generic                                 - Generic Linux kernel image                                   
p   linux-image-generic:i386                            - Generic Linux kernel image                                   
p   linux-image-generic-pae:i386                        - Generic Linux kernel image                                   
p   linux-image-lowlatency                              - lowlatency Linux kernel image                                
p   linux-image-lowlatency:i386                         - lowlatency Linux kernel image                                
p   linux-image-lowlatency-pae:i386                     - lowlatency Linux kernel image                                
p   [COLOR="Red"]linux-image-server                                  - Linux kernel image on Server Equipment.                      
p   linux-image-server:i386                             - Linux kernel image on Server Equipment.    [/COLOR]                  
p   linux-image-virtual                                 - Linux kernel image for virtual machines                
```

---

### Post by 2F4U on 2012-04-02
My understanding from the release notes is that they are the same, at least for amd64

[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Ubuntu_Kernel](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Ubuntu_Kernel)

---

### Post by Skaperen on 2012-04-02
Here's what I have right now (hope my grep filter wasn't too narrow to show what you want to see):

```
root@feynman:~# dpkg -l | fgrep 'ii  linux'
ii  linux-firmware                         1.75                                    Firmware for Linux kernel drivers
ii  linux-headers-3.2.0-21                 3.2.0-21.34                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-21-generic         3.2.0-21.34                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-server                   3.2.0.21.23                             Linux kernel headers on Server Equipment.
ii  linux-image-3.2.0-21-generic           3.2.0-21.34                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-server                     3.2.0.21.23                             Linux kernel image on Server Equipment.
ii  linux-libc-dev                         3.2.0-21.34                             Linux Kernel Headers for development
ii  linux-server                           3.2.0.21.23                             Complete Linux kernel on Server Equipment.
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu1                    base package for ALSA and OSS sound systems
root@feynman:~# uname -a
Linux feynman 3.2.0-21-generic #34-Ubuntu SMP Fri Mar 30 04:25:35 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
root@feynman:~# 
```I want to be running the server kernel.  Now if they are the same that's actually good.  Maybe the linux-*-server packages are legacy meta packages being retained so proper references can be used in case a desktop vs. server kernel split is needed in the future?

---

### Post by Skaperen on 2012-04-03
It is definitely the same kernel.  The linux-*-server packages install some documentation and depend on the other packages that get the real kernel.

---

### Post by dcstar on 2012-04-03
[http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm](http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm)

In my experience Ubuntu Server kernels do not support sound and are not optimised for real time user interfaces (i.e mouse /keyboard response) as the Desktop kernels are.

Unless someone can show that the compilation options for both kernels are identical then it is a big jump to say that they are identical.

---

### Post by Skaperen on 2012-04-04
> **dcstar said:**
> [http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm](http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm)

In my experience Ubuntu Server kernels do not support sound and are not optimised for real time user interfaces (i.e mouse /keyboard response) as the Desktop kernels are.

Unless someone can show that the compilation options for both kernels are identical then it is a big jump to say that they are identical.

Given that the server kernel packages are meta packages that depend on the generic kernel, I'm feeling confident, now, in saying that they are identical.  You get the same files.  The server gets a few more doc files.

---

