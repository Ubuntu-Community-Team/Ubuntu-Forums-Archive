---
title: "Help with Ubuntu and driver!!"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bsanehi on 2012-03-30
Hi I installed Ubuntu 12.04 beta 2 **using WUBI** on my HP Pavilion dv6-6b50sa

My labtop started to overheat but then I went to [Additional Drivers] and downloaded [Ati/Amd proprietary FGLRX graphics driver] and that stopped the overheating, but it change the GUI i mean lots of features are gone... Like before you could use the windows 7 snap feature but now it is gone after installing the driver and also the [Workspaces] changed too before I could see Youtube videos on [Workspaces] and I could see live animations but now its just like frozen.

When I uninstall the driver the overheating comes back and all the Ubuntu 12.04 features come back like the snap thing and the live animation on your [workspaces] and lots more things.

Here are two screenshots showing what I mean:
[COLOR=Red][B]
Before:[/B][/COLOR]

[IMG]http://img585.imageshack.us/img585/6100/screenshotfrom201203302.png[/IMG]

[B][COLOR=Red]
After installing Driver:[/COLOR][/B]

[IMG]http://img17.imageshack.us/img17/6100/screenshotfrom201203302.png[/IMG]




Can anyone help please.



[COLOR=Red]Edit: and I'm a huge noob with Ubuntu its my first time using it.[/COLOR]

---

### Post by Paddy Landau on 2012-03-31
Are you aware that 12.04 is still in Beta phase? This thread should really be in the [Ubuntu+1 (Precise Pangolin)]("http://ubuntuforums.org/forumdisplay.php?f=412") forum.

It seems that installing your driver disables the advanced features of Compiz, possibly returning you to 2D.

In each mode, open a terminal and enter the command:
```
 echo ${DESKTOP_SESSION}
```It should show "ubunutu" if you have 3D, and "ubuntu-2d" if you only have 2D.

Another command to try in each mode is:
```
/usr/lib/nux/unity_support_test --print
```This will show whether or not your current set-up is compatible with 3D.

You should reboot each time you enable or disable the driver.

---

### Post by howefield on 2012-03-31
Thread moved to "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by dino99 on 2012-03-31
be sure you have made a standard installation, here is a follow up (mine) :

[http://ubuntuforums.org/showpost.php?p=11654218&postcount=3](http://ubuntuforums.org/showpost.php?p=11654218&postcount=3)

The system will detect your hardware configuration and install the required drivers, no worry, here its not the winblow nightmare :)

---

### Post by bsanehi on 2012-03-31
> **Paddy Landau said:**
> Are you aware that 12.04 is still in Beta phase? This thread should really be in the [Ubuntu+1 (Precise Pangolin)]("http://ubuntuforums.org/forumdisplay.php?f=412") forum.

It seems that installing your driver disables the advanced features of Compiz, possibly returning you to 2D.

In each mode, open a terminal and enter the command:
```
 echo ${DESKTOP_SESSION}
```It should show "ubunutu" if you have 3D, and "ubuntu-2d" if you only have 2D.

Another command to try in each mode is:
```
/usr/lib/nux/unity_support_test --print
```This will show whether or not your current set-up is compatible with 3D.

You should reboot each time you enable or disable the driver.


I know its in beta phase but the problem was in 12.04 beta 1 too.

Yes  you are right it changes it from 3D to 2D when I install the driver...

And when I put in ```
/usr/lib/nux/unity_support_test --print
``` with driver on it gives me a bunch of errors...


**[COLOR=Red]Driver on:[/COLOR]**

[COLOR=Black]```
behzad@ubuntu:~$ echo ${DESKTOP_SESSION}
ubuntu-2d
```[/COLOR]
```
behzad@ubuntu:~$ /usr/lib/nux/unity_support_test --print
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22

```[B][COLOR=Red]


Driver off:[/COLOR] [/B]

[COLOR=Black]```
behzad@ubuntu:~$ echo ${DESKTOP_SESSION}
ubuntu
```[/COLOR]
```
]
behzad@ubuntu:~$ /usr/lib/nux/unity_support_test --print
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  3.0 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```[B][COLOR=Lime][COLOR=SeaGreen]Anyway of fixing this issue?
[/COLOR]

[/COLOR][/B]

---

### Post by Paddy Landau on 2012-04-01
> **bsanehi said:**
> Any way of fixing this issue?
Sorry, I don't know. May I suggest you try scouring the forums for solutions to the overheating (since the default driver works), and if you don't find it, start a new thread for overheating. With luck, you can solve the overheating and keep 3D.

In case someone else reading this thread may be able to help, please post the output of the following command in both modes:
```
sudo lshw -C display
```

---

### Post by bsanehi on 2012-04-01
> **Paddy Landau said:**
> Sorry, I don't know. May I suggest you try scouring the forums for solutions to the overheating (since the default driver works), and if you don't find it, start a new thread for overheating. With luck, you can solve the overheating and keep 3D.

In case someone else reading this thread may be able to help, please post the output of the following command in both modes:
```
sudo lshw -C display
```

okay :)


[COLOR=Red]**Driver on:**[/COLOR]

```

behzad@ubuntu:~$ sudo lshw -C display
[sudo] password for behzad: 
  *-display               
       description: VGA compatible controller
       product: Seymour [Radeon HD 6400M Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:a0000000-afffffff memory:c6500000-c651ffff ioport:5000(size=256) memory:c6520000-c653ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:6000(size=64)
```[COLOR=Red][B]


Driver off:
[/B][COLOR=Black]```
behzad@ubuntu:~$ sudo lshw -C display
[sudo] password for behzad: 
  *-display               
       description: VGA compatible controller
       product: Seymour [Radeon HD 6400M Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:52 memory:a0000000-afffffff memory:c6500000-c651ffff ioport:5000(size=256) memory:c6520000-c653ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:6000(size=64)
```
[B][COLOR=Red]By the way Ubuntu games don't run when the driver is installed.
[/COLOR][COLOR=Red]

[COLOR=Blue]Also is there a way to report this bug so the Ubuntu developers can fix this bug? I would hate to see this bug on the final release of 12.04 .....[/COLOR][/COLOR][/B][B][COLOR=Red]
[/COLOR][/B] [/COLOR][/COLOR]

---

### Post by Paddy Landau on 2012-04-02
> **bsanehi said:**
> okay
Apart from the first *configuration:driver* and *resources:irq*, the outputs are identical.

> **bsanehi said:**
> Ubuntu games don't run when the driver is installed.
That seems to show that the default driver is the better one, apart from the heating issues.

> **bsanehi said:**
> is there a way to report this bug so the Ubuntu developers can fix this bug?
First, start a new thread about the overheating to see whether or not that can be fixed. Once you have a solution, you'll know whether it was caused by a bug or something else. If it is a bug, [you can report it]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Testing_images_and_Reporting_bugs"). Be sure to keep your system up-to-date while testing.

---

### Post by ratcheer on 2012-04-02
@bsanehi, did you install fglrx with jockey or did you download directly from AMD? I had the same problem (unity-2d, only) after installing directly from AMD. 

If you installed from jockey, you then need to run "sudo apt-get update" and "sudo apt-get upgrade" to get the latest version of the driver, which has been working well for me.

Tim

---

### Post by bsanehi on 2012-04-02
> **Paddy Landau said:**
> Apart from the first *configuration:driver* and *resources:irq*, the outputs are identical.


That seems to show that the default driver is the better one, apart from the heating issues.


First, start a new thread about the overheating to see whether or not that can be fixed. Once you have a solution, you'll know whether it was caused by a bug or something else. If it is a bug, [you can report it]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Testing_images_and_Reporting_bugs"). Be sure to keep your system up-to-date while testing.

Alright I will , thanks for all the help man appreciate it.


> **ratcheer said:**
> @bsanehi, did you install fglrx with jockey or did you download directly from AMD? I had the same problem (unity-2d, only) after installing directly from AMD. 

If you installed from jockey, you then need to run "sudo apt-get update" and "sudo apt-get upgrade" to get the latest version of the driver, which has been working well for me.


Tim


I installed it using the **[COLOR=DeepSkyBlue]Additional Drivers[/COLOR]** software.

**[COLOR=Red]Edit:[/COLOR]** I done "sudo apt-get update" and "sudo apt-get upgrade" and restarted, but still same thing.[B]


Ohhh crap I forgot to mention I installed Ubuntu using WUBI and I still have my windows 7.
[/B]

---

### Post by Paddy Landau on 2012-04-02
> **bsanehi said:**
> Alright I will , thanks for all the help man appreciate it.
Yes, sorry I can't be of more help. Post the thread URL here so that we can follow it.

---

### Post by bsanehi on 2012-04-02
> **Paddy Landau said:**
> Yes, sorry I can't be of more help. Post the thread URL here so that we can follow it.

Under which topic should I start the thread on?

---

### Post by Paddy Landau on 2012-04-02
> **bsanehi said:**
> Under which topic should I start the thread on?
You've only 5 posts. Try the [Absolute Beginner Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=326").

---

### Post by bsanehi on 2012-04-02
> **Paddy Landau said:**
> You've only 5 posts. Try the [Absolute Beginner Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=326").

OK I started the thread.

[http://ubuntuforums.org/showthread.php?p=11812556#post11812556](http://ubuntuforums.org/showthread.php?p=11812556#post11812556)

---

### Post by Paddy Landau on 2012-04-02
Great. I hope you get a good result.

---

