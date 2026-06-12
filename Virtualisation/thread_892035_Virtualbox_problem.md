---
title: "Virtualbox problem"
date: 2008-08-16
forum: Virtualisation
---

### Post by Mr.Kuchinawa on 2008-08-16
Hello. I hope this falls under the right category, I reckon that it does since I'm pretty much a noob..Anyway:

I want to use virtualbox, as I have used it on previous systems. However, I encounter a strange problem when I try to boot the virtual machine I have prepared for XP. It says: 


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

Frankly, I have no clue what to do. I googled a couple of forum posts around the internet, but they were inadequate in different ways. Any help would be greatly appreciated.

---

### Post by dje on 2008-08-16
please post the output of the following from the terminal (applications >> accessories >> terminal):
```
uname -a
```

dje

---

### Post by Mr.Kuchinawa on 2008-08-16
Linux simen-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

---

### Post by dje on 2008-08-16
ok in the terminal run:
```
sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic
```
then try starting the virtual machine again

dje

---

### Post by Mr.Kuchinawa on 2008-08-16
No juice

---

### Post by dje on 2008-08-16
> **Mr.Kuchinawa said:**
> No juice

what happens? what is the error output?

dje

---

### Post by overdrank on 2008-08-16
moved :)

---

### Post by Mr.Kuchinawa on 2008-08-16
> **dje said:**
> what happens? what is the error output?

dje

The same as I mentioned before. Nothing seems different.

---

### Post by dje on 2008-08-16
ok remove virtualbox:
```
sudo apt-get autoremove --purge virtualbox-ose virtualbox-ose-modules-2.6.24-19-generic
```
then follow [this guide]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html"), it has always worked for me. i recommend following the guide to install the PUEL version as it has USB support

dje

---

### Post by Mr.Kuchinawa on 2008-08-16
Thanks for the effort, but following the guide did not change anything..

---

### Post by dje on 2008-08-16
> **Mr.Kuchinawa said:**
> Thanks for the effort, but the following the guide did not change anything..

did you follow the PUEL guide? i cannot see why it shouldn't work, did you logout and then in again before trying it. if that doesnt work try rebooting

dje

---

### Post by Lod on 2008-08-17
I have the same problem with the OSE-version. I also have the kernel 2.6.24-19-generic.
I'm using the installation howto in the ubuntu-wiki: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
The virtualbox-ose-modules-generic metapackage somehow depends on the 2.6.24-20-generic. If I don't use the metapackage but install the 2.6.24-19 modules myself installation goes fine but I can't start virtualbox because he's missing the correct modules.
The PUEL-version works for me.
```
louis@erato:~$ sudo apt-get install virtualbox-ose virtualbox-ose-source virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages

```
```
louis@erato:~$ uname -r
2.6.24-19-generic

```

---

### Post by Lod on 2008-08-17
> **Lod said:**
>  but I can't start virtualbox because he's missing the correct modules.Well, this might be caused by me not logging in again after adding myself to the group virtualbox users.:o . I booted up my testcomputer this morning to copy the correct error Virtualbox gave me and now it's working.... I'll deny everything though.

So, my problem was solved by installing the 'virtualbox-ose-modules-2.6.24-19-generic' package instead of the recommended metapackage.

---

### Post by Mr.Kuchinawa on 2008-08-17
Works now, thanks. I reinstalled the puel version.

---

### Post by agibby5 on 2008-09-07
I always use this:

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Very quick and easy.

```
sudo apt-get install virtualbox-ose virtualbox-ose-source virtualbox-ose-modules-generic
```

Then: 
```
sudo adduser $USER vboxusers
```

Logout.  Log back in (to reset permissions).

Run VirtualBox without any issues.

---

