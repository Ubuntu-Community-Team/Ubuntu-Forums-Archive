---
title: "getting error with oracle virtual box"
date: 2013-03-21
forum: Virtualisation
---

### Post by DMGrier on 2013-03-21
So I am new to using a virtual box and I was hoping someone could help me get this working, I set up to run a OS and when I try to run it this is what I am getting.
[ATTACH=CONFIG]240410[/ATTACH][ATTACH=CONFIG]240411[/ATTACH]

How do I fix this?

---

### Post by 2F4U on 2013-03-21
Is the first screenshot from the OS running in the VM? If yes, it seems as if this is crashing the VM. What OS are you running in the VM?

---

### Post by DMGrier on 2013-03-21
I am trying to run opensuse 12.3 32 bit this is what I get when I click on the OS in the VM and click on run.

---

### Post by mayagrafix on 2013-03-22
Try making a new virtual box (first erase the old one for SuSe 12.3 and all of its files) but instead of using a DVD point the installer to the ISO image directly.

---

### Post by DMGrier on 2013-03-22
I did that but I am getting that error when I first setup the virtual for any operating system, it won't even let me get to the machine to tell it to run the ISO.

---

### Post by DMGrier on 2013-03-22
I do apologize, I didn't realize I posted a openshot error thing, here is the other screen shot I meant to post and this will probably give way more information.

---

### Post by DMGrier on 2013-03-23
bump

---

### Post by ibjsb4 on 2013-03-23
Did you do what it said?

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by DMGrier on 2013-03-23
> devon@UbuntuPC:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for devon: 
sudo: /etc/init.d/vboxdrv: command not found
devon@UbuntuPC:~$ 


This is what it gave me

---

### Post by ibjsb4 on 2013-03-23
A couple of possibilities.

[http://ubuntuforums.org/showthread.php?t=1739768](http://ubuntuforums.org/showthread.php?t=1739768)

[http://ubuntuforums.org/showthread.php?t=948373](http://ubuntuforums.org/showthread.php?t=948373)

---

### Post by mayagrafix on 2013-03-23
When I first installed VM, had problems with dkms. this thread has the answer:

[http://ubuntuforums.org/showthread.php?t=2082194](http://ubuntuforums.org/showthread.php?t=2082194)

in particular these two command lines:

sudo apt-get install dkms build-essential linux-headers-generic
sudo /etc/init.d/vboxdrv setup

after running these VM started up and runs good.

---

### Post by SeijiSensei on 2013-03-23
I strongly recommend following the procedure at [https://www.virtualbox.org/](https://www.virtualbox.org/) to add the Oracle repository to /etc/apt/sources.list and let Ubuntu manage VirtualBox installations.  Follow the Download link, then the one for Linux downloads.  Half way down the page you'll see the instructions for "Debian-based distributions."

---

### Post by DMGrier on 2013-03-23
Thanks for all the help, I uninstalled the one from the software center and then installed the one from the Oracle website and it is running flawless now. Saw that is what one guy did in the threads you provided. Thanks a lot. How do I mark this as solved, not seeing the option for it.

---

### Post by BlinkinCat on 2013-03-23
Hi,

Here is the present method for marking threads as solved -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :P

---

