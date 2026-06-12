---
title: "Re: broken gksu"
date: 2014-05-21
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-05-21
At this point with current kernel gksu is pretty much broken.
An initial bug report is here, currently marked incomplete though that should change (or I'll change or dupe
[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/1312159](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/1312159)

Workarounds - 
In cases where pkexec is usable it can be set up & used instead (text editors, file managers
or ( and in the case of gdebi which is gksu only

Remove ~/.gksu.lock prior to attempting to use gksu (must be removed for each use of gksu
or
*Not recommended* -  disable the grab mode in gksu-properties for Screen grabbing

Even when working there seems to also be cursor run on which is not particulary a good thing so where applicable I'd switch to pkexec until this is fixed

---

### Post by squakie on 2014-05-21
Thanks for the info.  I reloaded my system over the weekend and got Ubuntu reloaded for dual-boot last night and found gksudo wasn't there so I installed it via apt-get.  I'll have to remember not to use it!

Thanks!

---

### Post by zika on 2014-05-22
I might be wrong (as many times before...) but I think that trouble with **gksu** is over...
(I'm using latest versions of 3.15 (rc-6, 994, 999)...)

---

### Post by Elfy on 2014-05-22
when the kernel in the repos is upgraded - then we can say that's over - if it works :)

---

### Post by Cavsfan on 2014-05-22
Broken here as well.
```
cavsfan@cavsfan-MS-7529:~$ gksudo gedit /etc/fstab

** (gksudo:18750): CRITICAL **: fcntl error

** (gksudo:18750): WARNING **: Lock taken by pid: -1. Exiting.
cavsfan@cavsfan-MS-7529:~$ 
```

I signed on to the bug and it's incomplete and of medium importance? :confused:

---

### Post by ventrical on 2014-05-23
> **Elfy said:**
> when the kernel in the repos is upgraded - then we can say that's over - if it works :)

This:

```

ventrical@ventrical-MS-7798:~$ uname -a
Linux ventrical-MS-7798 3.15.0-2-generic #6-Ubuntu SMP Thu May 22 16:14:57 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-MS-7798:~$ 


```

works just fine now with gksu.  Not bad error like 3.15.0-1.

---

### Post by grahammechanical on 2014-05-23
My daily update brought in Linux 3.15.0-2 which fixed the gksudo problem but brought back the dnsmq not getting internet bug. I have had to boot into Linux 3.13.0-24 to get an internet connection on this particular updated install.

Now, for the big question. Do I use gksudo or pkexec to edit /etc/NetworkManager/NetworkManager.conf and comment out dns=dnsmasq? :)

---

### Post by Elfy on 2014-05-23
> **grahammechanical said:**
> ...

Now, for the big question. Do I use gksudo or pkexec to edit /etc/NetworkManager/NetworkManager.conf and comment out dns=dnsmasq? :)

sudo nano :p

---

### Post by Elfy on 2014-05-23
:lol:

so gksudo mousepad works fine here 

so does the interwebs except apt in a terminal apparently without me fiddling with dnsmasq

---

### Post by grahammechanical on 2014-05-23
> [COLOR=#000000]sudo nano[/COLOR]

Choices. choices. Too many choices! #dns=dnsmasq fixes things for me.

---

### Post by Elfy on 2014-05-23
wonder why I'm ok without #'ing dns= line though

---

### Post by zika on 2014-05-23
> **grahammechanical said:**
> Choices. choices. Too many choices! #dns=dnsmasq fixes things for me.Do not discard dnsmasq so easily... It is a very nice peace of caching-SW... Easy to set up and delightful to use...

---

### Post by Elfy on 2014-05-23
> **zika said:**
> Do not discard dnsmasq so easily... It is a very nice peace of caching-SW... Easy to set up and delightful to use...

unless you can't get any internet with it allowed ;)

---

### Post by ventrical on 2014-05-23
> **grahammechanical said:**
> Choices. choices. Too many choices! #dns=dnsmasq fixes things for me.

 I am of the thinking that this may be on again - off again throughout this cycle, so, thats a good fix when it breaks up the road so to speak.

Regards..

---

### Post by ventrical on 2014-05-23
> **Elfy said:**
> unless you can't get any internet with it allowed ;)

:)

---

### Post by Sworddragon on 2014-05-23
> **grahammechanical said:**
> Now, for the big question. Do I use gksudo or pkexec to edit /etc/NetworkManager/NetworkManager.conf and comment out dns=dnsmasq? :)

Interestingly I'm also getting issues with pkexec. It doesn't launch a graphical appliction for me and after entering my password in the terminal it closes without giving an error message.

---

### Post by Cavsfan on 2014-05-23
It works for me with the newer kernel but still gets an error.

[ATTACH=CONFIG]253391[/ATTACH]

Oh well at least it works. :p

---

### Post by mc4man on 2014-05-23
> **Sworddragon said:**
> Interestingly I'm also getting issues with pkexec. It doesn't launch a graphical appliction for me and after entering my password in the terminal it closes without giving an error message.

nano is easy to use, probably your best bet.
In the few cases where gedit is more suitable pkexec should be ok how did you set it up?
(if you followed the post in closed thread it should have been put in a code box & there is a spelling error, <annotate key="org.freedesktop.policykit.exec.allow_gui">tru e</annotate>, that should be true, not tru e

Also better to run a root gedit or nautilus from run command than from terminal..

---

### Post by Cavsfan on 2014-05-23
> **Sworddragon said:**
> Interestingly I'm also getting issues with pkexec. It doesn't launch a graphical appliction for me and after entering my password in the terminal it closes without giving an error message.

Here's a link with the correct workaround. [https://bbs.archlinux.org/viewtopic.php?pid=999012](https://bbs.archlinux.org/viewtopic.php?pid=999012)

---

### Post by Elfy on 2014-05-23
I get *so* fed up with the ubuntu centric point of view :p

So - I get a massive error with gksudo gedit - if I try to run it - it want's it installed :D

No way I'm doing that either - that wants me to install zeitgeist :)

No pkexec for mousepad either ;)

---

### Post by Cavsfan on 2014-05-23
> **Elfy said:**
> I get *so* fed up with the ubuntu centric point of view :p

So - I get a massive error with gksudo gedit - if I try to run it - it want's it installed :D

No way I'm doing that either - that wants me to install zeitgeist :)

No pkexec for mousepad either ;)

:lol: Lol

At least Utopic now gets the exact same error that Trusty gets with gksudo gedit. :)

---

### Post by zika on 2014-05-23
> **Elfy said:**
> unless you can't get any internet with it allowed ;)Open new thread about that or some moderator could warn You... ;P
Joke aside, that is easily solved, been there, done that... ;)
It is, really, worth that small effort...

---

### Post by Elfy on 2014-05-23
> **Elfy said:**
> :lol:

so gksudo mousepad works fine here 

so does the interwebs without me fiddling with dnsmasq

Fed you a bum steer here - sorry - edited it.

---

### Post by Cavsfan on 2014-05-28
I realize this thread is closed but doesn't the problem lie with gedit more than gksu. I get absolutely no warnings or errors substituting leafpad for gedit.

```
cavsfan@cavsfan-MS-7529:~$ gksu leafpad /etc/fstab
cavsfan@cavsfan-MS-7529:~$ 
```

```
cavsfan@cavsfan-MS-7529:~$ gksu gedit /etc/fstab

(gedit:6506): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
cavsfan@cavsfan-MS-7529:~$ 
```

Both times I made a change and saved the file. :-k

---

### Post by mc4man on 2014-05-28
> **Cavsfan said:**
> I realize this thread is closed but doesn't the problem lie with gedit more than gksu. I get absolutely no warnings or errors substituting leafpad for gedit.

```
cavsfan@cavsfan-MS-7529:~$ gksu leafpad /etc/fstab
cavsfan@cavsfan-MS-7529:~$ 
```

```
cavsfan@cavsfan-MS-7529:~$ gksu gedit /etc/fstab

(gedit:6506): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
cavsfan@cavsfan-MS-7529:~$ 
```

Both times I made a change and saved the file. :-k
The issue with gksu was due to kernel & rectified. 
As far as Warnings they're a dime a dozen in linux & most times can be ignored.

---

### Post by Cavsfan on 2014-05-28
> **mc4man said:**
> The issue with gksu was due to kernel & rectified. 
As far as Warnings they're a dime a dozen in linux & most times can be ignored.

Thanks for the explanation. I thought pkexec was replacing gksu. I asked grahammechanical if that was the case but I guess he didn't see it.
That's a relief!

---

### Post by Maytapchaybo on 2014-05-29
Thanks

---

