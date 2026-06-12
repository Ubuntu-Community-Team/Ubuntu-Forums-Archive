---
title: "Ubuntu Server 10.4 64 bit RAM usage"
date: 2010-09-25
forum: Server Platforms
---

### Post by jmz2 on 2010-09-25
Hello,

It is normal that I have a used RAM of 150mb just after installacion of a minimun server install? Is an Ubuntu server 10.4 64bit with nothing running but SSH

It surprise me because I had installed in the same hardware the Lubuntu 10.4 32bit which has full desktop an it used only 70Mb after installation.

Why so much RAM consumption?

Thanks.

---

### Post by jmz2 on 2010-09-26
How much RAM is your Ubuntu Server 10.4 in idle and nothing running?

---

### Post by CharlesA on 2010-09-26
How are you measuing the RAM used?

Try this:

```
free -m
```

---

### Post by jmz2 on 2010-09-26
I use 'htop' normally to measure RAM use.

This is what I get using 'free' after just reboot:


```
jrg@hp-ml150:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5854        222       5632          0         27         44
-/+ buffers/cache:        150       5703
Swap:            0          0          0
```

Normally, how much RAM does Ubuntu Server 10.4 64bit uses when installed with the minimum?

Thnaks.

---

### Post by CharlesA on 2010-09-26
That looks fine.

You've got 6 gigs or RAM, why do you care if the main OS uses 150MB or 75MB of it?

Here's what mine looks like, but keep in mind this is just a virtual machine (I did a full install of Ubuntu Server 10.04.1)

```
charles@luna:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           999         84        915          0         12         24
-/+ buffers/cache:         47        952
Swap:         1101          0       1101
```

This is what my main server looks like:

```
charles@thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       5306        675          0          4       1485
-/+ buffers/cache:       3816       2165
Swap:        12401          0      12401
```

Then again, that machine is running 5 VMs atm.

---

### Post by jmz2 on 2010-09-26
> **CharlesA said:**
> That looks fine.

You've got 6 gigs or RAM, why do you care if the main OS uses 150MB or 75MB of it?

I don't really care but surprise me that the figure is so high and thought that maybe is something to do with my hardware.

[QUOTE=CharlesA;9892877
Here's what mine looks like, but keep in mind this is just a virtual machine (I did a full install of Ubuntu Server 10.04.1)

```
charles@luna:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           999         84        915          0         12         24
-/+ buffers/cache:         47        952
Swap:         1101          0       1101
```[/QUOTE]

Is that a Version of 32 or 64bits?

This is one virtual machine with Ubuntu Server 10.4.1 32bits, this is why the 150Mb surprise me:

```
ge@ubuntu-nas:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           189         79        110          0         15         39
-/+ buffers/cache:         23        165
Swap:          149          0        149

```

---

### Post by CharlesA on 2010-09-26
They are both 64-bit.

Here's with all the VMs powered off:

```
charles@thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       3681       2300          0          3       3316
-/+ buffers/cache:        [COLOR="Red"]361[/COLOR]       5619
Swap:        12401          0      12401
```

It is running: SSH, Samba, Apache, Exim4, and a few other services.

---

### Post by R.Bucky on 2010-09-26
My Server edition install uses around 1500MG RAM after a few hours. Upon initial startup, RAM usage sits around 300MB. However, once Apache gets going and people view a couple of my sites, RAM usage climbs. I have noticed that the 64-bit version really uses whatever RAM is available to make services and content more readily available, where the 32-bit version did not. Difference in architecture makes a difference...

---

### Post by windependence on 2010-09-26
Linux != Windows.
 
Linux uses available RAM if it can. In some cases all available RAM will appear to used and in fact it IS used, but just not the way it is used in Windoze. This is a good thing. Linux will cache programs in RAM until they are ready to be used thus increasing performance and why not? If you've got the resources why not use them?
 
-Tim

---

### Post by CharlesA on 2010-09-26
> **R.Bucky said:**
> My Server edition install uses around 1500MG RAM after a few hours. Upon initial startup, RAM usage sits around 300MB. However, once Apache gets going and people view a couple of my sites, RAM usage climbs. I have noticed that the 64-bit version really uses whatever RAM is available to make services and content more readily available, where the 32-bit version did not. Difference in architecture makes a difference...

Yep, that's the way Linux manages memory.

> **windependence said:**
> Linux != Windows.
 
Linux uses available RAM if it can. In some cases all available RAM will appear to used and in fact it IS used, but just not the way it is used in Windoze. This is a good thing. Linux will cache programs in RAM until they are ready to be used thus increasing performance and why not? If you've got the resources why not use them?
 
-Tim

+1.

Check [here]("http://www.linuxatemyram.com/") as well. ;)

---

