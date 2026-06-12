---
title: "[SOLVED] VirtualBox error!"
date: 2008-06-05
forum: Virtualisation
---

### Post by Rytron on 2008-06-05
Hi,
VirtualBox was always running perfectly yet when I tried to run it today, I got this error message:

[B]VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
[/B]

Could someone please explain what I need to do in order to get VirtualBox back working  properly. Thanks.

---

### Post by Redptc on 2008-06-05
Some answers at this thread[HTML]http://ubuntuforums.org/showthread.php?t=811808&highlight=virtualbox[/HTML]

---

### Post by cszikszoy on 2008-06-05
The error message kinda tells you what to do...

open console and type:
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Redptc on 2008-06-05
Another good thread[HTML]http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox[/HTML]

---

### Post by Joeb454 on 2008-06-05
> **cszikszoy said:**
> The error message kinda tells you what to do...

open console and type:
```
sudo /etc/init.d/vboxdrv setup
```

Exactly what I did :) It's annoying when you get 2 kernel releases in about 2 weeks - i.e. when we went to -17 the other week, and -18 a few days back

---

### Post by cszikszoy on 2008-06-05
Definitely annoying, but at least the fix wasn't too painful.  Would be helpful if vbox just did this automatically I suppose, but I guess we can't have our cake and eat it too!

> **Joeb454 said:**
> Exactly what I did :) It's annoying when you get 2 kernel releases in about 2 weeks - i.e. when we went to -17 the other week, and -18 a few days back

---

### Post by G-Dawg on 2008-06-06
.......
* Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
.........
[reveals:]
/etc/init.d/vboxdrv: 311: /usr/lib/virtualbox/src/build_in_tmp: not found

erg vbox stopped working for me on the last kernel update as well but cant remember exactly how I fixed it.. I think the above step just worked last time..

---

### Post by Rytron on 2008-06-07
> **cszikszoy said:**
> The error message kinda tells you what to do...

open console and type:
```
sudo /etc/init.d/vboxdrv setup
```

Thanks, this did the trick.

---

### Post by G-Dawg on 2008-06-07
Any ideas why this didn't work for me?

---

### Post by Rytron on 2008-06-07
> **G-Dawg said:**
> Any ideas why this didn't work for me?

Sorry G-Dawg, but I don't know how to resolve your situation.

---

### Post by G-Dawg on 2008-06-07
if you have OSE version like me:

[http://www.nabble.com/Kernel-Update-broke-VirtualBox-td17644214.html]("http://www.nabble.com/Kernel-Update-broke-VirtualBox-td17644214.html")

---

### Post by G-Dawg on 2008-06-07
Actually this only works for the .17 kernel and not .18.... this is really annoying!

---

### Post by mali on 2008-06-07
> **cszikszoy said:**
> The error message kinda tells you what to do...

open console and type:
```
sudo /etc/init.d/vboxdrv setup
```


I get this message after the entering the line above.

[I]* Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
[/I]

---

### Post by cszikszoy on 2008-06-08
You will get that message if you don't type 'setup' at the end.  Make sure you type the whole line, including 'setup'.

> **mali said:**
> I get this message after the entering the line above.

[I]* Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
[/I]

---

### Post by cszikszoy on 2008-06-08
Sorry G-Dawg.  I am using the non OSE version, and what I posted earlier worked fine for me.


> **G-Dawg said:**
> Actually this only works for the .17 kernel and not .18.... this is really annoying!

---

### Post by teratomata on 2008-06-09
> **mali said:**
> I get this message after the entering the line above.

[I]* Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
[/I]

I got the same message.

Instead I just updated my machine, there's a couple of new virtualbox updates since I last checked last week, it works fine now.

---

