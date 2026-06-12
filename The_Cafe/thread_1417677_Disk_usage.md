---
title: "Disk usage"
date: 2010-02-27
forum: The Cafe
---

### Post by theozzlives on 2010-02-27
Look at the difference between the server (non-gui) and desktop (gui)
```
Server:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  1.2G  7.8G  14% /
udev                  468M  184K  468M   1% /dev
none                  468M     0  468M   0% /dev/shm
none                  468M  464K  468M   1% /var/run
none                  468M     0  468M   0% /var/lock
none                  468M     0  468M   0% /lib/init/rw
/dev/sda3              64G  557M   60G   1% /home

Desktop:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.9G  3.7G  5.7G  40% /
udev                  2.0G  308K  2.0G   1% /dev
none                  2.0G  400K  2.0G   1% /dev/shm
none                  2.0G  512K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda3             271G   14G  244G   6% /home

```
It's enough to go CLI only, if only there was a browser and mail client.

---

### Post by dragos240 on 2010-02-27
> **theozzlives said:**
> Look at the difference between the server (non-gui) and desktop (gui)
```
Server:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  1.2G  7.8G  14% /
udev                  468M  184K  468M   1% /dev
none                  468M     0  468M   0% /dev/shm
none                  468M  464K  468M   1% /var/run
none                  468M     0  468M   0% /var/lock
none                  468M     0  468M   0% /lib/init/rw
/dev/sda3              64G  557M   60G   1% /home

Desktop:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.9G  3.7G  5.7G  40% /
udev                  2.0G  308K  2.0G   1% /dev
none                  2.0G  400K  2.0G   1% /dev/shm
none                  2.0G  512K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda3             271G   14G  244G   6% /home

```It's enough to go CLI only, if only there was a browser and mail client.

Links (with FB), and mutt.

---

### Post by SomeGuyDude on 2010-02-27
Or maybe you need a drive that's more than ten friggin' gigs. Seriously, you can buy an 80GB drive for like $40.

---

### Post by FuturePilot on 2010-02-27
> **SomeGuyDude said:**
> Or maybe you need a drive that's more than ten friggin' gigs. Seriously, you can buy an 80GB drive for like $40.

That's just the / partition. There's another partition on the same disk for /home that is much bigger.

---

### Post by earthpigg on 2010-02-27
as long as any given partition is less than 85% full (or 90%, or 75%, depending on who you ask), the data on that partition isn't slowing your system down.

the GUI itself may be slower than typing (if you have a good collection of aliases), but copying large files from point a to point b won't be any faster from the command line than from a GUI.

instead of skipping directly to terminal-only, maybe try a minimal gui... openbox and pcmanfm. add lxpanel if you still want menus that are automatically generated and updated whenever you install/uninstall software.

---

### Post by SomeGuyDude on 2010-02-27
> **FuturePilot said:**
> That's just the / partition. There's another partition on the same disk for /home that is much bigger.

All right, that makes more sense.

Regardless... so? Saying that the GUI takes up more space than the server is like saying buttered popcorn has more calories than plain. No duh. But if you want the various other benefits the GUI gets ya, you have to take the space.

---

### Post by theozzlives on 2010-02-27
> **SomeGuyDude said:**
> All right, that makes more sense.

Regardless... so? Saying that the GUI takes up more space than the server is like saying buttered popcorn has more calories than plain. No duh. But if you want the various other benefits the GUI gets ya, you have to take the space.

See I was bred DOS, so the "butter on the popcorn" means nothing. I just need to browse the web and check my mail (some web based). I can live without the "pretty pictures".

---

### Post by The Real Dave on 2010-02-27
> **SomeGuyDude said:**
> Or maybe you need a drive that's more than ten friggin' gigs. 

My / partition on my main (Gnome) desktop is only 8Gb, with 3.6 free.

My server has Ubuntu installed on an 8Gb *drive*, 2Gb of which goes to swap. Here's the result.

```
/dev/sda2             5.8G  1.4G  4.2G  25% /

```

Compare that with a full install of Ubuntu with quite a few packages ;)
```
/dev/sdb5             8.7G  4.6G  3.7G  56% /

```

---

### Post by theozzlives on 2010-02-27
I think I'm gonna force myself into the command line. The Linux+ exam is all about that anyhow.

---

### Post by dragos240 on 2010-02-27
> **theozzlives said:**
> I think I'm gonna force myself into the command line. The Linux+ exam is all about that anyhow.

Again, you can use mutt for email, and links -g for internet, links -g uses the framefuffer on your computer to display pictures and graphics without the need for Xorg.

---

### Post by theozzlives on 2010-02-27
> **dragos240 said:**
> Again, you can use mutt for email, and links -g for internet, links -g uses the framefuffer on your computer to display pictures and graphics without the need for Xorg.

Is this in the repositories?

---

### Post by dragos240 on 2010-02-27
> **theozzlives said:**
> Is this in the repositories?

Absolutely! However links needs to be compiled with graphics support, it goes under the name xlinks in the ubuntu repo. Mutt should be there as well.

---

### Post by theozzlives on 2010-02-27
> **dragos240 said:**
> Absolutely! However links needs to be compiled with graphics support, it goes under the name xlinks in the ubuntu repo. Mutt should be there as well.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xlinks
o
```

---

### Post by dragos240 on 2010-02-27
> **theozzlives said:**
> ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xlinks
o
```

Wait, it's links2, my bad, I haven't used ubuntu in a while.

---

### Post by MooPi on 2010-02-27
This file shows my full desktop install on a flash drive experiment.

---

### Post by theozzlives on 2010-02-27
```
ozzie@www-server:~$ links2 -g

   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.2.7 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2008  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2009-06-02 06:26) 
(*) Direct/Memcpy: Using Generic 64bit memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
svgalib: Cannot get I/O permissions.
ozzie@www-server:~$ 

```
I'm running a headless server, does that matter?

---

### Post by dragos240 on 2010-02-27
> **theozzlives said:**
> ```
ozzie@www-server:~$ links2 -g

   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.2.7 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2008  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2009-06-02 06:26) 
(*) Direct/Memcpy: Using Generic 64bit memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
svgalib: Cannot get I/O permissions.
ozzie@www-server:~$ 

```I'm running a headless server, does that matter?

Well..... yes if you want graphics, but if you just need toxt for browsing, don't use the -g option.

---

