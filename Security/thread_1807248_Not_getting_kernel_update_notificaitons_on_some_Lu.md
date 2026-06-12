---
title: "Not getting kernel update notificaitons on some Lucid 10.04 boxes"
date: 2011-07-18
forum: Security
---

### Post by mdlueck on 2011-07-18
I have noticed specifically the kernel is being overlooked for software updates on various Lucid 10.04 boxes I have.

I run apticron on all servers. I do not get emails for the kernel updates, though other updates I am notified about.

Both server and desktop, sometimes when I refresh / mark all upgrades available, sometimes it includes the kernel update, other times I must manually mark the kernel update I know needs to be applied.

On my Ubuntu desktops, I specifically turn OFF update-notifier in the Configuration Editor as I like the orange Updates Available top tray icon which appears no mater what virtual desktop I happen to be in. With that turned off, I still should get kernel update messages... and my servers which do not run a GUI are absolutely without excuse.

Suggestions?

---

### Post by mdlueck on 2011-09-30
Here we go again. A Lucid desktop detected an available kernel update, and applied it.

Our server, running 10.04 server edition, still is not auto selecting the new kernel. I manually searched, and the new kernel package does show up.

Why is Aptitude not correctly chaining onto a new kernel version package available?

I am going to try to paste in the output of Aptitude showing that it wants to download one tiny package, meanwhile ignore the kernel update:

```
 Actions  Undo  Package  Resolver  Search  Options  Views  Help                                                                                                                                      
C-T: Menu  ?: Help  q: Quit  u: Update  g: Download/Install/Remove Pkgs                                                                                                                              
aptitude 0.4.11.11                                                                                                                                                                    DL Size: 210kB 
--- Upgradable Packages (1)                                                                                                                                                                          
--\ New Packages (46)                                                                                                                                                                                
  --\ admin - Administrative utilities (install software, manage users, etc) (28)                                                                                                                    
    --\ main - Fully supported Free Software. (8)                                                                                                                                                    
p     linux-image-2.6.32-318-ec2                                                                                                                                                <none>     2.6.32-318
p     linux-image-2.6.32-34-386                                                                                                                                                 <none>     2.6.32-34.
p     linux-image-2.6.32-34-generic                                                                                                                                             <none>     2.6.32-34.
p     linux-image-2.6.32-34-generic-pae                                                                                                                                         <none>     2.6.32-34.
p     linux-image-2.6.32-34-virtual                                                                                                                                             <none>     2.6.32-34.
p     linux-image-2.6.38-11-generic                                                                                                                                             <none>     2.6.38-11.
p     linux-image-2.6.38-11-generic-pae                                                                                                                                         <none>     2.6.38-11.
p     linux-image-2.6.38-11-virtual                                                                                                                                             <none>     2.6.38-11.
    --- universe - Unsupported Free Software. (20)                                                                                                                                                   
  --- devel - Utilities and programs for software development (18)                                                                                                                                   
--- Installed Packages (471)                                                                                                                                                                         
--- Not Installed Packages (30098)                                                                                                                                                                   
--- Obsolete and Locally Created Packages (3)                                                                                                                                                        
--- Virtual Packages (3296)                                                                                                                                                                          
--- Tasks (13685)                                                                                                                                                                                    
                                                                                                                                                                                                     
                                                                                                                                                                                                     
                                                                                                                                                                                                     
                                                                                                                                                                                                     
                                                                                                                                                                                                     
                                                                                                                                                                                                     
                                                                                                                                                                                                     
                                                                                                                                                                                                     
  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
  &#9474;Search for:                                                                                                                                                                                    &#9474;  
  &#9474;linux-image-                                                                                                                                                                                   &#9474;  
Li&#9474;                                           [ Ok ]                                                                                        [ Cancel ]                                            &#9474;  
Th&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; &#9618;
                                                                                                                                                                                                    &#9618;
Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update.              &#9618;
                                                                                                                                                                                                    &#9618;
Supports Generic processors.                                                                                                                                                                        &#9618;
                                                                                                                                                                                                    &#9618;
Geared toward desktop systems.                                                                                                                                                                      &#9618;
                                                                                                                                                                                                    &#9618;
You likely do not want to install this package directly. Instead, install the linux-ec2 meta-package, which will ensure that upgrades work correctly, and that supporting packages are also         &#9618;
installed.                                                                                                                                                                                          &#9618;
```

---

### Post by mdlueck on 2011-10-01
And I just had an Ubuntu 10.04 desktop not auto select the 2.6.32-34 kernel update. So still some desktop systems are affected by this problem, not just server installations.

Suggestions please?

---

### Post by CharlesA on 2011-10-01
My server install of 10.04 applied that kernel update (2.6.32-34) 2 days ago via automagic updates, set to install security updates automagically.

---

### Post by mdlueck on 2011-10-02
So perhaps do you have a meta-package installed that is updated to point at the latest stable release of the kernel? The systems I am having kernel update trouble with do not seem to have a meta-package:

```
$ dpkg -l|grep linux-
ii  linux-firmware                            1.34.7                             Firmware for Linux kernel drivers
ii  linux-image-2.6.32-33-generic-pae         2.6.32-33.70                       Linux kernel image for version 2.6.32 on x86
```

If not a meta-package, then what IS the mechanism that is used to notify systems of new kernel packages?

---

### Post by CharlesA on 2011-10-02
No idea.

These are the ones I have installed now:

```
ii  linux-firmware                  1.34.7                                          Firmware for Linux kernel drivers
ii  linux-headers-2.6.32-33         2.6.32-33.72                                    Header files related to Linux kernel version
ii  linux-headers-2.6.32-33-server  2.6.32-33.72                                    Linux kernel headers for version 2.6.32 on x
ii  linux-headers-2.6.32-34         2.6.32-34.77                                    Header files related to Linux kernel version
ii  linux-headers-2.6.32-34-server  2.6.32-34.77                                    Linux kernel headers for version 2.6.32 on x
ii  linux-headers-server            2.6.32.34.40                                    Linux kernel headers on Server Equipment.
ii  linux-image-2.6.32-32-server    2.6.32-32.62                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-33-server    2.6.32-33.72                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-34-server    2.6.32-34.77                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-server              2.6.32.34.40                                    Linux kernel image on Server Equipment.
ii  linux-libc-dev                  2.6.32-34.77                                    Linux Kernel Headers for development
ii  linux-server                    2.6.32.34.40                                    Complete Linux kernel on Server Equipment.

```

---

### Post by mdlueck on 2011-10-02
> **CharlesA said:**
> No idea.

These are the ones I have installed now:

```
ii  linux-headers-server            2.6.32.34.40                                    Linux kernel headers on Server Equipment.
ii  linux-image-server              2.6.32.34.40                                    Linux kernel image on Server Equipment.

```

Well these two look like meta-packages to me, which would be able to provide the capability of updating to newer kernel releases.

Thanks, I will hunt down the correct meta packages for my various configurations.

---

