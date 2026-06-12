---
title: "How can I disable the startup for ubuntu's desktop during booting the system?"
date: 2010-04-26
forum: Server Platforms
---

### Post by ivancheng on 2010-04-26
Hi,

How can I disable the startup for ubuntu's desktop during booting the system?  I would like to start it manually.  I tried to remove the /etc/init.d/gdm file but no help.

Thanks in advance.

Rgds,
Ivan Cheng

---

### Post by sisco311 on 2010-04-26
In /etc/default/grub replace:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
with
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```
then run:
```
sudo update-grub
```

---

### Post by wojox on 2010-04-26
Try:

```
sudo update-rc.d gdm remove
```

---

### Post by arrrghhh on 2010-04-26
> **wojox said:**
> Try:

```
sudo update-rc.d gdm remove
```

Be wary, this command will prevent gdm from starting - ever (unless of course you add gdm back to the init, this doesn't remove the script from /etc/init.d)

I'm confused, why does your server install have gdm installed anyways?

BTW, sisco311's suggestion would remove the splash screen from bootup, which again you shouldn't have on an actual ubuntu-server install... Unless you did something crazy like install the ubuntu-desktop package on your -server install ;)

---

### Post by dannyboy79 on 2010-04-26
> **wojox said:**
> try:

```
sudo update-rc.d gdm remove
```
+1

---

### Post by wojox on 2010-04-26
> **arrrghhh said:**
> Be wary, this command will prevent gdm from starting - ever (unless of course you add gdm back to the init, this doesn't remove the script from /etc/init.d)

I'm confused, why does your server install have gdm installed anyways?

BTW, sisco311's suggestion would remove the splash screen from bootup, which again you shouldn't have on an actual ubuntu-server install... Unless you did something crazy like install the ubuntu-desktop package on your -server install ;)

You can start the desktop with:

```
startx
```

This will restore it:

```
sudo update-rc.d gdm defaults 13 01
```


True though, I never understood why people just don't download the Desktop Edition.

---

### Post by ivancheng on 2010-04-26
Hi,

GRUB_CMDLINE_LINUX_DEFAULT="text"
After doing above, the desktop didn't start automatically.

>>I'm confused, why does your server install have gdm installed anyways?

I have a problem on the RAID disks issue if one of the RAID disk failed and would like to disable the desktop to see whether it can fix the problem.

Thanks a lot.

Rgds,
Ivan Cheng

---

### Post by arrrghhh on 2010-04-26
> **ivancheng said:**
> Hi,

GRUB_CMDLINE_LINUX_DEFAULT="text"
After doing above, the desktop didn't start automatically.

>>I'm confused, why does your server install have gdm installed anyways?

I have a problem on the RAID disks issue if one of the RAID disk failed and would like to disable the desktop to see whether it can fix the problem.

Thanks a lot.

Rgds,
Ivan Cheng

I guess you didn't read what I - or others - have said...

Plus your explanation for having gdm on a server install makes no sense... why would you have installed it in the first place?

If you want to remove gdm, use the update-rc.d remove command.  That command you posted removes the pretty splash screen from -desktop installs.  I already explained that...

**Read the post below, evidently update-rc.d isn't used for GDM any longer...**

---

### Post by sisco311 on 2010-04-26
> **arrrghhh said:**
> 
If you want to remove gdm, use the update-rc.d remove command.  That command you posted removes the pretty splash screen from -desktop installs.  I already explained that...

Since 9.10, gdm's System-V style init script was replaced by an Upstart job. In Karmic and Lucid you can't use the update-rc.d command to remove gdm. You have to edit/rename /etc/init/gdm.conf or boot with the *text* kernel parameter.

---

### Post by arrrghhh on 2010-04-26
> **sisco311 said:**
> Since 9.10, gdm's System-V style init script was replaced by an Upstart job. In Karmic and Lucid you can't use the update-rc.d command to remove gdm. You have to edit/rename /etc/init/gdm.conf or boot with the *text* kernel parameter.

Odd... so does this only apply to GDM then?  I assume update-rc.d is still used for other init scripts, I'm pretty sure I just used it the other day for rtorrent...

---

### Post by cdenley on 2010-04-26
> **arrrghhh said:**
> Odd... so does this only apply to GDM then?  I assume update-rc.d is still used for other init scripts, I'm pretty sure I just used it the other day for rtorrent...

It applies for anything that has been converted to the upstart format.
```

ls /etc/init

```
The "update-rc.d" command only works if there are links created for the /etc/init.d/appname script in the /etc/rc?.d directories.

---

### Post by dannyboy79 on 2010-04-26
> **arrrghhh said:**
> Odd... so does this only apply to GDM then?  I assume update-rc.d is still used for other init scripts, I'm pretty sure I just used it the other day for rtorrent...

i upgraded from jaunty to karmic, and then to lucid. I originally installed a GUI on a ancient dell (mythbuntu jaunty -9.04) but since realized that I don't need the gui since it's only a server (mythtv, samba, apache2, transmission-deamon torrent) and I am comfortable with CLI. 
Anyway, my point is that I used 
sudo update-rc.d remove xdm

and now xdm doesn't start nor does X or any other useless panels or desktop environment etc etc.
xdm is similar to gdm but for xubuntu which is used within mythbuntu.
My point is that update-rc.d remove does WORK!

---

### Post by arrrghhh on 2010-04-26
> **dannyboy79 said:**
> My point is that update-rc.d remove does WORK!

Apparently it's only applicable to 10.04, Lucid Lynx.  Plus I don't know if that applies to Xubuntu/XDM...

I wish there was a way to know about these changes... it seems I always find out about these changes by someone correcting me in the forums...

---

### Post by antenna on 2010-04-26
Sometimes I long for the simpler times of inittab.

---

### Post by cdenley on 2010-04-26
> **dannyboy79 said:**
> My point is that update-rc.d remove does WORK!

For xdm, not gdm! It removes links created in /etc/rc?.d. However, gdm does not have those links when enabled, so as far as update-rc.d can tell, it is already removed.

---

### Post by arrrghhh on 2010-04-26
> **antenna said:**
> Sometimes I long for the simpler times of inittab.

One of the many reasons I consider going to Arch... It was just way too much of a PITA to configure.

Rolling release cycle... simpler service management... I love the concepts of Arch, just wish it was executed in a more friendly manner!

---

### Post by cdenley on 2010-04-26
> **arrrghhh said:**
> Apparently it's only applicable to 10.04, Lucid Lynx.  Plus I don't know if that applies to Xubuntu/XDM...

I wish there was a way to know about these changes... it seems I always find out about these changes by someone correcting me in the forums...

GDM was converted in 9.10. XDM appears to still use the old sysv-compatible format in 10.04.

If you ever attempted to use or view an init script which was converted, you would have seen:
```

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service service_name start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start service_name
start: Unknown job: service_name

```

I personally think the uptstart jobs are much better. You shouldn't need multiple symlinks for each script in order to make a service work. Upstart is simpler and more configurable.

---

### Post by antenna on 2010-04-26
> **arrrghhh said:**
> One of the many reasons I consider going to Arch... It was just way too much of a PITA to configure.

Rolling release cycle... simpler service management... I love the concepts of Arch, just wish it was executed in a more friendly manner!

Agreed, the concepts are great and it's so easy to poke around with the internals in Arch.  Everything in Ubuntu feels very abstracted in comparison.  Like you say, Arch has its downsides though and I am very much liking Lucid right now.

---

