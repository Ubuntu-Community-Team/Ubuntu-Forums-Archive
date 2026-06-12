---
title: "android on virtualbox"
date: 2014-05-27
forum: Virtualisation
---

### Post by guyv on 2014-05-27
i tried to run android on virtualbox on ubuntu 14.04 and i got error about '/etc/init.d/vboxdrv setup'. 
i tried to install it manually via terminal and i got this:

```
 [COLOR=#0000ff]Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules/etc/init.d/vboxdrv: 302: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...done.
Trying to register the VirtualBox kernel modules using DKMS/etc/init.d/vboxdrv: 327: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/do_dkms: not found
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)[/COLOR]


```

into [COLOR=#0000ff]vbox-install.log[/COLOR] : ```
[COLOR=#0000ff]/etc/init.d/vboxdrv: 334: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/build_in_tmp: not found[/COLOR]
```

i searched this error and found nothing helpful.

i searched for this error[COLOR=#0000ff] /usr/share/virtualbox/src/vboxhost/do_dkms: not found[/COLOR]
i found that i need to run this command :
```
[COLOR=#0000ff]sudo dpkg-reconfigure virtualbox-dkms[/COLOR]
```

and i got :
```

[COLOR=#0000ff]------------------------------
Deleting module version: 4.3.10
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-4.3.10 DKMS files...
Building only for 3.13.0-27-generic
Building initial module for 3.13.0-27-generic
Error! Bad return status for module build on kernel: 3.13.0-27-generic (x86_64)
Consult /var/lib/dkms/virtualbox/4.3.10/build/make.log for more information.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                       
 * **No suitable module for running kernel found**
                                                                       **  [fail]**
invoke-rc.d: initscript virtualbox, action "restart" failed.[/COLOR]

```

so i tried to update the linux-headers and the dkms in synaptic package manager (i am runing linux-headers-3.13.0-24). and it wasn't helpful.

please help me.

thank you.

---

### Post by gordintoronto on 2014-05-27
Where did you get the Android from? Android for Intel processors is a rare beast.

---

### Post by guyv on 2014-05-28
[http://www.youtube.com/watch?v=TwwH6xBn4mg](http://www.youtube.com/watch?v=TwwH6xBn4mg) 

but i didn't choose the android file yet.. i got the error before i can choose something..

---

### Post by TheFu on 2014-05-29
There is an android emulator to be release shortly. It is supposed to be much faster. OSX and Win7 versions were released in May, I think (could be wrong).   AndyRoid.net - I haven't tried this.  

My attempts at android dev and running apps was a terrible failure.  Setup a Linux VM with lots of CPU and RAM and storage only to discover it was dog-slow.  Guess 6G RAM and 3 Core i7 Cores isn't enough for java development?  OTOH, with Perl 5.20 release a version for Android will be available - perhaps it will finally be fast?

---

### Post by guyv on 2014-05-29
thank you. i will try this.

---

### Post by gordintoronto on 2014-05-29
So your problem has nothing to do with Android, you are having trouble installing and running VirtualBox? Or perhaps more accurately, "reinstalling."

> **guyv said:**
> [http://www.youtube.com/watch?v=TwwH6xBn4mg](http://www.youtube.com/watch?v=TwwH6xBn4mg) 

but i didn't choose the android file yet.. i got the error before i can choose something..

---

