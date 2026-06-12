---
title: "Oracle Virtualbox 3.2?"
date: 2010-10-26
forum: Virtualisation
---

### Post by chrispche on 2010-10-26
I upgraded to the latest version of Oracle Virtualbox as was suggested when I ran it. I have been using Windows XP for some time with full support for my mobile phone. However since the upgrade it won't run. Any help please?

Here's a screenshot of the problem.

[[img]http://i25.servimg.com/u/f25/11/95/68/21/vb10.jpg[/img]](http://www.servimg.com/image_preview.php?i=39&u=11956821)

Thank you.

---

### Post by carl.davis on 2010-10-26
Hello,

How did you originally install VirtualBox? Can you please post the output from:

```
dpkg --list |grep virtualbox
```

---

### Post by gradinaruvasile on 2010-10-26
Well in a window it states what should you do (you have to recompile the kernel module used by virtualbox):

Open a console and type:

sudo /etc/init.d/vboxdrv setup

then try again.

---

### Post by carl.davis on 2010-10-27
> **gradinaruvasile said:**
> 

Open a console and type:

sudo /etc/init.d/vboxdrv setup

then try again.

Hi gradinaruvasile,

I think the screenshot shows that there was a terminal window open with that command typed and an error returned. Unless you saw something I missed?

---

### Post by nerdy_kid on 2010-10-27
try reinstalling virtualbox.

---

### Post by chrispche on 2010-10-27
> **carl.davis said:**
> Hello,

How did you originally install VirtualBox? Can you please post the output from:

```
dpkg --list |grep virtualbox
```

```
chrispche@chrispche-laptop:~$ dpkg --list |grep virtualbox
ii  virtualbox-3.2                                               3.2.10-66523~Ubuntu~maverick               Oracle VM VirtualBox
chrispche@chrispche-laptop:~$ 
```

It was already pre-installed with a disk from Ubuntu Magazine.

---

### Post by chrispche on 2010-10-27
> **nerdy_kid said:**
> try reinstalling virtualbox.

I tried reinstalling. Same thing happens.

---

### Post by carl.davis on 2010-10-28
> **chrispche said:**
> I tried reinstalling. Same thing happens.

You could try to remove the config files and reinstall with:

```
sudo apt-get purge virtualbox-3.2
sudo apt-get update
sudo apt-get install virtualbox-3.2
```

---

### Post by chrispche on 2010-10-28
Does the OSE version allow for USB devices to work in the virtual machine?

---

### Post by chrispche on 2010-10-28
> **carl.davis said:**
> You could try to remove the config files and reinstall with:

```
sudo apt-get purge virtualbox-3.2
sudo apt-get update
sudo apt-get install virtualbox-3.2
```

How I can't thank you enough for this. It's working perfectly now. Thanks a lot pal.

---

### Post by carl.davis on 2010-10-29
> **chrispche said:**
> Does the OSE version allow for USB devices to work in the virtual machine?

No, the OSE version does not have USB support. 

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by carl.davis on 2010-10-29
> **chrispche said:**
> How I can't thank you enough for this. It's working perfectly now. Thanks a lot pal.

You're welcome. I am glad we got it working.

---

### Post by chrispche on 2010-10-29
> **carl.davis said:**
> No, the OSE version does not have USB support. 

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

I thought not. Hence using the Oracle version, as to using the version in the repos.

---

