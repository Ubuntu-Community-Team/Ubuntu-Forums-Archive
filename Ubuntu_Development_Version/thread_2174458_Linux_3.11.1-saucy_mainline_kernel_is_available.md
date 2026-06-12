---
title: "Linux 3.11.1-saucy mainline kernel is available"
date: 2013-09-14
forum: Ubuntu Development Version
---

### Post by VinDSL on 2013-09-14
Works.

SOURCE: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.1-saucy/)

---

### Post by zika on 2013-09-14
Ditto. I can smell 3.12 in the air... I only hope that laptop is working good (Linus lost his SSD...)...

---

### Post by VinDSL on 2013-09-14
> **zika said:**
> Ditto. I can smell 3.12 in the air... I only hope that laptop is working good (Linus lost his SSD...)...
Aye!  The scent of 3.12 is abounding...

I wonder if Linus is still running Fedora.

BTW, I've been having to reinstall nVidia 304 lately, after every kernel upgrade.


```
sudo apt-get install -f -m --reinstall -u nvidia-304
```


Are you having to do the same (or similar)?

---

### Post by zika on 2013-09-14
If You're asking me, I'm now in nice age when Raden driver is thriving in OS environment...
It seems that I forgot bad times for Radeon that are not so far back in time...
Joke put aside, I do not have NVidia on my desk... I have one in my son's computer but that machine is not in my U+1 reach...
There is U on it but only regular one or even LTS because serious work is done on it, not to say that I do not do seriously on this machine but, I'm invincible enough to manage this adrenaline rush...

---

### Post by VinDSL on 2013-09-14
I have a 50/50 feeling that it's something with my Frankenstein install, or possibly a bug -- not sure which...

Most of the time, in the past, when I installed a new kernel (sometimes several times a week) the nVidia module will automatically build.  So, I install the kernel and reboot.  Simple pimple.  Took less time than typing this post.

Lately, the nVidia module doesn't build (no errors reported), during the kernel installation.  When I reboot, I'm met with a black screen.  So, I need to shell out, manually install the nVidia drivers, then startx.  After that, everything is fine, until I install another kernel.

Doesn't really matter.  It's an extra step -- that's all.

I was just curious if other ppl were experiencing this behavior, too...  ;)

---

### Post by zika on 2013-09-15
Shot in the dark: Do You have DKMS installed?

---

### Post by QDR06VV9 on 2013-09-15
> **VinDSL said:**
> I have a 50/50 feeling that it's something with my Frankenstein install, or possibly a bug -- not sure which...

Most of the time, in the past, when I installed a new kernel (sometimes several times a week) the nVidia module will automatically build.  So, I install the kernel and reboot.  Simple pimple.  Took less time than typing this post.

Lately, the nVidia module doesn't build (no errors reported), during the kernel installation.  When I reboot, I'm met with a black screen.  So, I need to shell out, manually install the nVidia drivers, then startx.  After that, everything is fine, until I install another kernel.

Doesn't really matter.  It's an extra step -- that's all.

I was just curious if other ppl were experiencing this behavior, too...  ;)
I have not had to install nvidia by hand for a while on HP lappy DV2700 GeForce 7150M / nForce 630M/integrated/SSE2
on the 3 towers nvidia-325 just works.

---

### Post by VinDSL on 2013-09-15
> **zika said:**
> Shot in the dark: Do You have DKMS installed?
Yes.

Is it poisoning my well?

---

### Post by VinDSL on 2013-09-15
> **runrickus said:**
> I have not had to install nvidia by hand for a while on HP lappy DV2700 GeForce 7150M / nForce 630M/integrated/SSE2
on the 3 towers nvidia-325 just works.
Nice!

I need to run legacy drivers, e.g. nVidia 304.x

304.x works fine.  The initial module just doesn't build, lately, while I'm installing a new kernel.

---

### Post by VinDSL on 2013-09-15
Hrm...

I'm going to try [[some of these]("http://askubuntu.com/questions/53364/command-to-rebuild-all-dkms-modules-for-all-installed-kernels")] the next time I install a new kernel in saucy.

I'm in Ubu 10.10 right now -- tested a couple of the one-liners, and they worked, as described.

---

### Post by VinDSL on 2013-09-15
@zika -- I think you're onto something...   :D

I'm back in Ubu 13.10/GS 3.9.91 Staging now, and I ran Answer #3 in the [link]("http://askubuntu.com/questions/53364/command-to-rebuild-all-dkms-modules-for-all-installed-kernels") above:


```
vindsl@Zuul:~$ su
Password: 
root@Zuul:/home/vindsl# dkms status | sed s/,//g | awk '{print "-m",$1,"-v",$2}' | while read line; do ls /var/lib/initramfs-tools | xargs -n 1 dkms install $line -k; done
Error! Could not locate dkms.conf file.
File:  does not exist.
Module nvidia-304/304.108 already installed on kernel 3.11.0-031100-generic/i686
Module nvidia-304/304.108 already installed on kernel 3.11.1-031101-generic/i686
Module nvidia-304/304.108 already installed on kernel 3.11.0-031100-generic/i686
Module nvidia-304/304.108 already installed on kernel 3.11.1-031101-generic/i686
root@Zuul:/home/vindsl# 

```

When I ran it in Ubu 10.10, it found all the modules, and reported they were already installed.

In saucy, it cannot locate my dkms.conf file.

I wonder where it wandered to...

---

### Post by VinDSL on 2013-09-15
Okay... got it!  ;)

```
root@Zuul:/home/vindsl# dkms status | sed s/,//g | awk '{print "-m",$1,"-v",$2}' | while read line; do ls /var/lib/initramfs-tools | xargs -n 1 dkms install $line -k; done
Module nvidia-304/304.108 already installed on kernel 3.11.0-031100-generic/i686
Module nvidia-304/304.108 already installed on kernel 3.11.1-031101-generic/i686
Module nvidia-304/304.108 already installed on kernel 3.11.0-031100-generic/i686
Module nvidia-304/304.108 already installed on kernel 3.11.1-031101-generic/i686
root@Zuul:/home/vindsl# 

```

Had to clear the cruft out of my  /var/lib/dkms  folder.

There were still some remnants from an old nVidia 304 install (Jan 2013) in there.

We'll see how it goes on the next kernel install.

Thanks!

---

### Post by VinDSL on 2013-09-15
Hrm...

Output still looked janky, so I purged Linux 3.11 final.

Got a few error messages on completion, so I manually updated GRUB:

```
vindsl@Zuul:~$ sudo update-grub
[sudo] password for vindsl:         
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.1-031101-generic
Found initrd image: /boot/initrd.img-3.11.1-031101-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
vindsl@Zuul:~$ su
Password: 
root@Zuul:/home/vindsl# dkms status | sed s/,//g | awk '{print "-m",$1,"-v",$2}' | while read line; do ls /var/lib/initramfs-tools | xargs -n 1 dkms install $line -k; done
Module nvidia-304/304.108 already installed on kernel 3.11.1-031101-generic/i686
root@Zuul:/home/vindsl# 

```

Looks clean as a whistle now.

Let's see if it survives a cold boot...  ;)

---

### Post by VinDSL on 2013-09-15
Beautiful!!!

Well, that wiped the slate clean...

I'm going to add that procedure to my trash cleanup routine, in Gnote, before I forget about it. :)

---

### Post by QDR06VV9 on 2013-09-16
> **VinDSL said:**
> Beautiful!!!

Well, that wiped the slate clean...

I'm going to add that procedure to my trash cleanup routine, in Gnote, before I forget about it. :)

Just out of Curiosity are you running Driver 304 from
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) saucy main
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) saucy main
They just work better for me.

---

### Post by VinDSL on 2013-09-16
Yes.  Here's what I'm running, right now:

```
vindsl@Zuul:~$ apt-cache policy nvidia-304
nvidia-304:
  **[COLOR="#0000CD"]Installed: 304.108-0ubuntu1~xedgers~saucy1[/COLOR]**
  Candidate: 304.108-0ubuntu1~xedgers~saucy1
  Version table:
 *** 304.108-0ubuntu1~xedgers~saucy1 0
        **[COLOR="#0000CD"]500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ saucy/main i386 Packages[/COLOR]**
        100 /var/lib/dpkg/status
     304.88-0ubuntu8 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/restricted i386 Packages
vindsl@Zuul:~$ 
```

---

### Post by paul_in_london on 2013-09-16
> **VinDSL said:**
> Yes.  Here's what I'm running, right now:

```
vindsl@Zuul:~$ apt-cache policy nvidia-304
nvidia-304:
  **[COLOR="#0000CD"]Installed: 304.108-0ubuntu1~xedgers~saucy1[/COLOR]**
  Candidate: 304.108-0ubuntu1~xedgers~saucy1
  Version table:
 *** 304.108-0ubuntu1~xedgers~saucy1 0
        **[COLOR="#0000CD"]500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ saucy/main i386 Packages[/COLOR]**
        100 /var/lib/dpkg/status
     304.88-0ubuntu8 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/restricted i386 Packages
vindsl@Zuul:~$ 
```

Yep same here.

```
paul@lubuntu-64:~$ apt-cache policy nvidia-304
nvidia-304:
  Installed: 304.108-0ubuntu1~xedgers~saucy1
  Candidate: 304.108-0ubuntu1~xedgers~saucy1
  Version table:
 *** 304.108-0ubuntu1~xedgers~saucy1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status
     304.88-0ubuntu8 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/restricted amd64 Packages
paul@lubuntu-64:~$
```

 So did you get the same build failure with 3.12-rc1?

---

### Post by VinDSL on 2013-09-16
> **paul_in_london said:**
>  So did you get the same build failure with 3.12-rc1?
Haven't had a chance to try it yet.

Just got home, and I'm updating my FB account, checking my mail(s), reading the forums, feeding my face, blah, blah, blah.

I'll give 3.12 whirl in a few minutes...  ;)

---

