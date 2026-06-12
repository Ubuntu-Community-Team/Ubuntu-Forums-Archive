---
title: "Which Nvidia driver should I install?"
date: 2013-03-11
forum: Ubuntu Development Version
---

### Post by victor9098 on 2013-03-11
Hi All,

In 12.10 I was using the 310 experimental repo, but from what I can remember there was just the one listed in the 'additional drivers'. in 13.04 I have three 310 repo's to choose from an an additional 313 too. In 12.10 I was using 310 to ensure the best performance with steam, but was wondering which is the best for me to aim for now?

I have attached an image for my list of options.

Thanks

---

### Post by carl4926 on 2013-03-11
```
sudo apt-get install nvidia-current
```

Is what I do

I have seen some threads with issues related to your proposal

---

### Post by victor9098 on 2013-03-11
> **carl4926 said:**
> ```
sudo apt-get install nvidia-current
```

Is what I do

I have seen some threads with issues related to your proposal

Yeah, I have come across one related to the 313. Will play safe for now and stick with the nvidia-current.

---

### Post by mc4man on 2013-03-11
There is an overabundance of nvidia packages atm - 9 total for 3XX in synaptic.
Some are currently the same like '310 & 310-updates',  '304, 304-updates & nvidia-current',  the experimental packages are slightly older versions of 304 & 310
I'd probably use the latest - 313 (only 1 version) or the latest 304 or 310 (ie. not the experimental

Ultimately use what works best for your hardware, read changelogs if need be.

---

### Post by victor9098 on 2013-03-11
> **mc4man said:**
> There is an overabundance of nvidia packages atm - 9 total for 3XX in synaptic.
Some are currently the same like '310 & 310-updates',  '304, 304-updates & nvidia-current',  the experimental packages are slightly older versions of 304 & 310
I'd probably use the latest - 313 (only 1 version) or the latest 304 or 310 (ie. not the experimental

Ultimately use what works best for your hardware, read changelogs if need be.

I moved from the nvidia-current to 313, the performance in steam was not very good, well not as good as the 310 repo in 12.10.

I noticed that enabling the Nvidia repo still messes up the the splash screen. I normally use the answer to this Ask Ubuntu question [Enabling Nvidia driver messes up splash screen]("http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen") to change the settings, but it does not seem to work now. I noted that after inputting the final stage I got the following output;

[INDENT]~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.8.0-11-generic
modprobe: ../tools/modprobe.c:550: print_action: Assertion `kmod_module_get_initstate(m) == KMOD_MODULE_BUILTIN' failed.
Aborted (core dumped)[/INDENT]

---

### Post by chenriques on 2013-03-11
> **carl4926 said:**
> ```
sudo apt-get install nvidia-current
```

Is what I do

I have seen some threads with issues related to your proposal

What will "nvidia-current" install? The latest stable version of nvidia drivers? At this moment, nvidia 310?

---

### Post by victor9098 on 2013-03-11
> **chenriques said:**
> What will "nvidia-current" install? The latest stable version of nvidia drivers? At this moment, nvidia 310?

It installs the 304 repo. Not even sure if that gets updated after release either, usually there is a 304-updates (or to that effect) if you want post-release updates. 310 was the bleeding edge if you wanted full steam support in 12.10. The new 313 is new to me.

I have gone back to the default xorg, some applications (like skype) would not run with the new driver. Will wait to try again after some updates come down the line

---

### Post by VinDSL on 2013-03-11
> **victor9098 said:**
> It installs the 304 repo.[...]
I'm running bleeding edge software on ancient iron.  Unfortunately, I'm stuck with nVidia 304.x legacy drivers.

As mc4man stated, there are lots of different flavors available.

On this rig, this is what works best (currently)...

```
vindsl@Zuul:~$ apt-cache policy nvidia-304
nvidia-304:
  **[COLOR="#0000FF"]Installed: 304.84-0ubuntu2[/COLOR]**
  Candidate: 304.84-0ubuntu2
  Version table:
 *** 304.84-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/restricted i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 
```

If it works on this machine, it should work on anything.

Just saying...

---

