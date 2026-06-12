---
title: "How to make Ubuntu faster"
date: 2009-02-06
forum: The Cafe
---

### Post by t12t43 on 2009-02-06
What do you do to make your ubuntu faster?
Let's discussion.

---

### Post by steeleyuk on 2009-02-06
Install Preload.
Disable unneeded services.
Remove Tracker (doesn't make too much difference on Intrepid because I think it doesn't scan by default).

I'm sure I've said this in a similar thread not so long ago...

---

### Post by Johnsie on 2009-02-06
I'm not sure about now but swapiness used to be an issue. Lowering swapiness used to help me speed ubuntu up on slower machines.

---

### Post by imlinux on 2009-02-06
use xfce or lxde environment

---

### Post by MindFlayer on 2009-02-06
Compiled a 64-bit custom kernel for my Intel Core 2 Duo and optimized some stuff such as kernel Hz, scheduling and preemption modes etc.. Everything's blazing fast now. :p

---

### Post by adamlau on 2009-02-06
1. Choose the best hardware I can afford at the moment.
2. Always start with a minimal install off the minimal CD.
3. Install  a featherweight window manager such as JWM :) .
4. Compile as many kernel and userland apps as possible.
5. Focus on lightweight apps with as few dependencies as possible.
6. Rely heavily on bash aliases, functions and scripts.

mkfs.xfs -f -l size=**64m**,lazy-count=**1** [COLOR="Indigo"][format to and tune xfs][/COLOR]

tmpfs /tmp **tmpfs noatime** 0 0 [[COLOR="Indigo"]/tmp on tmpfs and noatime for all mounts][/COLOR]

xfs_db -r /dev/sda(x)
	frag
xfs_fsr -v /dev/sda(x) [COLOR="#4b0082"][defrag fragmented xfs partitions][/COLOR]

/etc/default/console-setup [COLOR="#4b0082"][disable ttys][/COLOR]

/etc/sysctl.conf > vm.swappiness=0 [COLOR="#4b0082"][limit swapping][/COLOR]

sysv-rc-conf [COLOR="#4b0082"][disable unnecessary services and daemons][/COLOR]

.gtkrc-2.0 > gtk-menu-popup-delay = 0 [COLOR="#4b0082"][for GNOME][/COLOR]

/etc/dhcp3/dhclient.conf > prepend domain-name-servers 208.67.222.222,208.67.220.220; [COLOR="#4b0082"][use opendns][/COLOR]

/etc/modprobe.d/aliases > alias net-pf-10 off [COLOR="#4b0082"][disable ipv6][/COLOR]

That should about cover most of what a typical speed demon does to go faster ;) .

---

### Post by MikeTheC on 2009-02-06
Run it on faster hardware?

Get the source code and hand-optimize it then re-compile it?

Profit?

---

### Post by chucky chuckaluck on 2009-02-06
the most noticeable speed difference i ever got using ubuntu was using a wm instead of a DE. also, using lighter apps (terminal apps instead of gui apps, etc).

---

### Post by mikjp on 2009-02-06
Install Debian instead of Ubuntu :-)

Mikko

---

### Post by angelosapo on 2009-02-07
1 Go for a minimal install

2 Xfce/Jwm as a WM

3 Install prelink through synaptic or 
```
sudo apt-get install prelink
```


```
sudo nano /etc/default/prelink
```
(or your favourite   terminal based editor)

 change > PRELINKING=yes

 ```
sudo /etc/cron.daily/prelink
``` (WAIT until it completes!!!)

 ```
sudo /etc/cron.daily/prelink 
```Has to be executed after each system update

---

### Post by PhoHammer on 2009-09-22
I wrote an article [COLOR=Blue]_[here]("http://bit.ly/4tthBI")_[/COLOR] that might help with this. It's the same one as in my sig.

---

### Post by tcoffeep on 2009-09-22
I install Gentoo.

---

### Post by sdlynx on 2009-09-22
> **Johnsie said:**
> I'm not sure about now but swapiness used to be an issue. Lowering swapiness used to help me speed ubuntu up on slower machines.

Unless you have low RAM.

---

### Post by dragos240 on 2009-09-22
> **t12t43 said:**
> Let's discussion.

Agreed. We need to discussion this!

---

