---
title: "I need help to install VMware Workstation."
date: 2011-07-08
forum: Virtualisation
---

### Post by BulgarianBoy on 2011-07-08
Hello Everyone,
So I have been trying to install VMware so I can play maplestory. The version I am trying to install is 7.1.4 32 bit, I also tried installing the 64 bit and nothing happened. And even before that I tried installing VMware 5.5.9 still could not get it to work and able to create cm module or something. Anyways now I was using a tutorial and I still could not get it to work this is what happened. 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`
moris@moris-laptop:~$ sudo sh ./VMware-Workstation-Full-7.1.4-385536.i386.bundlesh: Can't open ./VMware-Workstation-Full-7.1.4-385536.i386.bundle
moris@moris-laptop:~$ sudo sh ./VMware-Workstation-Full-7.1.4-385536.i386.bundlesh: Can't open ./VMware-Workstation-Full-7.1.4-385536.i386.bundle
moris@moris-laptop:~$ ./VMware-Workstation-Full-7.1.4-385536.i386.bundle
bash: ./VMware-Workstation-Full-7.1.4-385536.i386.bundle: No such file or directory
moris@moris-laptop:~$ sudo ./VMware-Workstation-Full-7.1.4-385536.i386.bundle
sudo: ./VMware-Workstation-Full-7.1.4-385536.i386.bundle: command not found
moris@moris-laptop:~$ /home/user/Downloads/VMware-Workstation-7.1.4-385536.i386.bundle
bash: /home/user/Downloads/VMware-Workstation-7.1.4-385536.i386.bundle: No such file or directory
moris@moris-laptop:~$ /home/moris/Downloads/VMware-Workstation-7.1.4-385536.i386.bundle
bash: /home/moris/Downloads/VMware-Workstation-7.1.4-385536.i386.bundle: Permission denied
moris@moris-laptop:~$ ^C
moris@moris-laptop:~$ /home/moris/Downloads/VMware-Workstation-7.1.4-385536.x86_64.bundle
bash: /home/moris/Downloads/VMware-Workstation-7.1.4-385536.x86_64.bundle: Permission denied
moris@moris-laptop:~$ su
Password: 
root@moris-laptop:/home/moris# /home/moris/Downloads/VMware-Workstation-7.1.4-385536.i386.bundle
bash: /home/moris/Downloads/VMware-Workstation-7.1.4-385536.i386.bundle: Permission denied
root@moris-laptop:/home/moris# /home/moris/Downloads/VMware-Workstation-7.1.4-385536.x86_64.bundle
bash: /home/moris/Downloads/VMware-Workstation-7.1.4-385536.x86_64.bundle: Permission denied
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I have been looking for tutorials on this website, on Google, and on YouTube found many but nothing worked. Please Help. Thank You.

---

### Post by e79 on 2011-07-08
```
cd /path/where/vmware-installer/is
```
 
```
chmod +x VMware-Workstation-Full-7.1.4-385536.i386.bundle
```
 
```
sudo ./VMware-Workstation-Full-7.1.4-385536.i386.bundle
```
 
That should do it, I always installed it using this method.
 
Hope this helps

---

### Post by BulgarianBoy on 2011-07-09
Got it to work. But the problem I have now is that Maplestory had a patch the other night the blocked users from using virtual machines.

---

### Post by e79 on 2011-07-10
> **BulgarianBoy said:**
> Got it to work. But the problem I have now is that Maplestory had a patch the other night the blocked users from using virtual machines.

I'm glad you could install Vmware player, however I don;t think I can help you regarding Maplestory  :(

Cheers

---

