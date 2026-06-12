---
title: "VirtualBox full screen problem"
date: 2014-11-30
forum: Virtualisation
---

### Post by mostafa3 on 2014-11-30
Hi,
I download latest version Ubuntu (14.10) today and then install ubuntu in VirtualBox but after installing, fullscreen dosen't work.
Also i install the Guest Additions but fullscreen dosen't work!

When I ran the xrandx command, the output was:
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected primary 640x480+0+0 0mm x 0mm
   640x480        73.0* 

```

When I ran the uname -r command, the output was:
```

mostafa@***:~$ uname -r
3.16.0-25-generic

```


Thanks

---

### Post by sudodus on 2014-11-30
Welcome to the Ubuntu Forums :-)

Maybe it will work if you try according to the following post

[http://ubuntuforums.org/showthread.php?t=2251116&p=13158092#post13158092](http://ubuntuforums.org/showthread.php?t=2251116&p=13158092#post13158092)

```
GRUB_TERMINAL=console
```

...

---

### Post by ibjsb4 on 2014-11-30
Also ..

Did you install dkms?
```
sudo apt-get install virtualbox-guest-dkms
```

---

### Post by mostafa3 on 2014-11-30
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Maybe it will work if you try according to the following post

[http://ubuntuforums.org/showthread.php?t=2251116&p=13158092#post13158092](http://ubuntuforums.org/showthread.php?t=2251116&p=13158092#post13158092)

```
GRUB_TERMINAL=console
```

...

> **ibjsb4 said:**
> Also ..
Did you install dkms?
```
sudo apt-get install virtualbox-guest-dkms
```

I can&#8217;t thank you enough,
My Problem Solved. :p

---

### Post by sudodus on 2014-11-30
Congratulations :KS

Please tell us what made it work for you (which one of the methods or both of them together)! It is valuable for other members of the Ubuntu Forums that you share the solution.

Finally, click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

### Post by mostafa3 on 2014-11-30
> **sudodus said:**
> Congratulations :KS
Please tell us what made it work for you (which one of the methods or both of them together)! It is valuable for other members of the Ubuntu Forums that you share the solution.
Finally, click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

I ran the command in terminal and after rebooting OS, my problem [COLOR=#000000]Solved[/COLOR].
```
sudo apt-get install virtualbox-guest-dkms
```

---

