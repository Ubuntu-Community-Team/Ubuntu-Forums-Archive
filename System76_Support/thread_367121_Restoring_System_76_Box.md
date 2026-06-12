---
title: "Restoring System 76 Box"
date: 2007-02-21
forum: System76 Support
---

### Post by jvslice on 2007-02-21
I have a new Sable Performance Desktop with I am real enjoying, but I tend to try thing over my head, or at least do not know when to ask for help.  i tried to make a new mount point for /home but failed and completely killed the file system.  So off I go to [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System), and followed the instructions.

I downloaded and burned a copy of edgy, installed and partitioned a separate / and /home mount.  The install went perfect.  Next a downloaded system76-driver-1.9.7.deb and installed as instructed.  When I run System 76 Driver install the display for install starts but the progress hangs at about 30-50 % complete, I have waited for at least 10 minutes and does not complete. so I exit out.

My big question I what I'm I doing wrong?

thanks

---

### Post by jvslice on 2007-02-22
This is a follow up to my post, I tried to install nvidia-glx, when I did:

"sudo nvidia-glx-config enable" I received the following error message:

Error: unable to load nvidia kernel driver!  Be sure to have installed the nvidia driver for your running kernel.

The first thing I did, don't no why, but I looked at xorg.conf and found that the device was set to "vesa" instead of "nv" as I've seen on other boxes with nvidia driver.  I changed vesa to nv,  then reloaded nvidia-glx and changed nv to nvidia in xorg.conf, and restarting x with control-alt-backspace.  After that I tried to System 76 drivers again, still hangs, bu this time at about 80%.

Since the computer is an AMD64, dual core, should I have loaded the 64 bit edgy, I loaded the 386 version.

Any ideas what to do next, thanks

---

### Post by crichell on 2007-02-22
We need to install linux-restricted-modules-generic.

```
sudo apt-get install linux-restricted-modules-generic
```

If you have a chance run the system76 driver from terminal - you'll be able to tell what's hanging and we can get it fixed.

```
system76-driver
```

---

### Post by jvslice on 2007-02-23
Thanks for the reply, I'll will try when i get home tonight.

---

### Post by jvslice on 2007-02-23
Followup -

1. First step - sudo apt-get install linux-restricted-modules-generic - response newest module already installed

2. system76-driver - response grep: /opt/system76/model/model: No such file or directory, Also receive popup driver only supports 6.06 and 6.10 on System76 computers.  pressing the OK button dose not close popup, but get another The window "" is not responding.  After a force quit both the popup and System76 driver closes but the terminal window does not go to a prompt until ^C.  

3. Hope to get this fix, on a trip for the company Sunday and not back until Thursday night.

---

### Post by AusIV4 on 2007-02-24
Where might I find the source for system76-driver? I prefer Kubuntu, and on my other computers I've installed Kubuntu from the Kubuntu CD, rather than having a gnome base. When I tried that on my Gazelle, I found that the system76-driver had dependencies that aren't installe with Kubuntu, so I thought if I could find the source I'd see if I can port it to QT.

---

### Post by crichell on 2007-02-25
> Where might I find the source for system76-driver?

[http://planet76.com/repositories](http://planet76.com/repositories)

> 2. system76-driver - response grep: /opt/system76/model/model: No such file or directory

You should get this output as the first line.  Sounds like there is unique information within your motherboard that is causing the driver hang.  Please email the output of

```
sudo dmidecode > ~/Desktop/dmidecode.txt
```

to support (at) system76.com

Thanks.

---

### Post by jvslice on 2007-03-02
Back home from my trip, I have sent the file sudo dmidecode > ~/Desktop/dmidecode.txt to [email]support@system76.com[/email].  Hope to get this fix this weekend, will be back on the road again.

Don't know if this may also help or if this a different problem, under screen resolution can only select 1024x768, but should be able to select 1440x900 with my monitor and nvidia installed, this used to work until I reinstalled edgy.

thanks

---

### Post by jvslice on 2007-03-02
Solved the problem with the resolution problem with the display by manually editing xorg.conf and manually adding "1440x900" to the modes in the Screen Section.

---

### Post by jvslice on 2007-03-10
Well I am back again from another trip, and I thought I would bring everyone up to date.  I initially sent an e-mail to [email]support@system76.com[/email], asking for additional help.  As we worked through the problem using the dmidecode output, it appears that the problem was with the System76 driver deb file and was told that they were fixing the problem.  The new driver was discussed on the System76 forum ([www.system76.com/forums](www.system76.com/forums)) for another problem - not mine.  Well I downloaded the new deb and installed.  Everything now works, like it did before I broke it.  One thing that I found during the installation,was that  my apt-get repository list was replaced and included the System 76 repository.  So I will now be current with any changes from System 76, but I had to re insert additional 3rd party repositories.  

Thanks to all, and Carl for bearing with this traveler.

---

