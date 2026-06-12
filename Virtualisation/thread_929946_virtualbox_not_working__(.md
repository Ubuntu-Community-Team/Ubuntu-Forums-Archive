---
title: "virtualbox not working  :("
date: 2008-09-25
forum: Virtualisation
---

### Post by jazzman14 on 2008-09-25
Hi,

I've installed virtualbox ose on  my ubuntu 8.04 computer. I've gone through adding the users to the vbox group through the gui and through the terminal, I've logged out, restarted many times still to get this error:


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

any ideas?

---

### Post by gpredrag on 2008-09-25
> ...adding the users to the **vbox** group through the gui ...

> for /dev/vboxdrv by adding them to the **vboxusers** groups

is this typo?

what does
```
lsmod |grep vboxdrv
``` tells you? Is module actualy loaded?

---

### Post by jazzman14 on 2008-09-25
vboxdrv                68376  0

---

### Post by gpredrag on 2008-09-25
Here
```
ls -laF /dev/vb*
```
gives
```
crw-rw---- 1 root vboxusers 10, 60 2008-09-25 21:59 dev/vboxdrv
```

so correct group name should be vboxusers not vbox, that's why I asked about typo.

---

### Post by jazzman14 on 2008-09-25
yes, it was a typo

i get this from ls -laF /dev/vb*:

crw-rw---- 1 root vboxusers 10, 62 2008-09-25 11:31 /dev/vboxdrv

---

### Post by jazzman14 on 2008-09-25
any ideas?

---

### Post by linux6994 on 2008-09-26
A couple of things that you need to do to make your virtual life easier:

1.Uninstall the OSE version that comes via the repositories, it sucks.

2.Go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and select Hardy 386 (I assume you are on Hardy)

3. Install via the Package manager, you can install directly from the download.

4. If you already have a .virtualbox file in your home directory then its ok. I have several machines and copy it out to Document folder or network drive for safe keeping. The virtual machines are just a file set so treat it a such. You will have to go to home folder and view hidden files to copy it out. Remember to copy it for saving to a VBOX folder or something and view hidden files there as well to see it.

5. You might have to add the machine or register it from within vbox. 

6. After a kernel update you might see "spawning session" if so then just redownload the package and reinstall. I have a copy saved in my Document folder to use after kernel changes. It needs to compile after kernel updates and reinstalling does the trick.

My daughter Vista crashed last night so I loaded Ubuntu and she has Xp running in Virtualbox, so everything is stuck in my head.

Good Luck!

---

### Post by davidryder on 2008-09-26
```
sudo usermod -aG vboxusers <your_username>
```

This will add your UID to the group vboxusers - a neccessity to use VB. Log out, log back in. Try again.

Good luck!

---

### Post by linux6994 on 2008-09-26
I had added myself to the vboxusers group and I still had gotten that same error that why I went to the non ose version.

---

