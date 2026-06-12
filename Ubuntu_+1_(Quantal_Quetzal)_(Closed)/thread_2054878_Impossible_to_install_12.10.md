---
title: "Impossible to install 12.10"
date: 2012-09-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by axelsvag on 2012-09-08
I downloaded the beta 1 of 12.10. Used usb-creator from a 10.10 machine but the installation is just black nothing can be seen. If I use unetbootin I get the launcers but no mouse no background and nothing usable.
I got a CQ60 with nividia 8200M any suggestions??

---

### Post by mips on 2012-09-08
Try using the 'nomodeset' kernel line boot option.

---

### Post by cicoandcico on 2012-09-08
maybe it's bug #[1043518]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518")?

---

### Post by axelsvag on 2012-09-08
I tried the nomode method, I should have remembered. Then the installation or at least live test installation went on . But the system was very very slow and the menu for example "system settings" opened in 4-5 seconds very slow. And the system could not read another USB stick where I had the password for the network so nu luck getting into internet either. So there is something not good with maybe the nvidia and 12.10. I 'd better wait for beta 2

---

### Post by bullfrog13x4 on 2012-09-08
i am having similar problems with 12.10 and nvidia,, i am currently looking at the nvidia driver web site and it appears that they have recently released a driver just for the new kernel,, i am in the process of trying to install it now,,, i will update you with the results,,

 that web site is here,,  [http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html](http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html)

 the install looks to be very complicated,, this will probably take me all night... as i am no expert


 hope this helps,,,

---

### Post by mips on 2012-09-08
> **bullfrog13x4 said:**
> i am having similar problems with 12.10 and nvidia,, i am currently looking at the nvidia driver web site and it appears that they have recently released a driver just for the new kernel,, i am in the process of trying to install it now,,, i will update you with the results,,

 that web site is here,,  [http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html](http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html)

 the install looks to be very complicated,, this will probably take me all night... as i am no expert


 hope this helps,,,

That driver (304.43) is in the repos, why not install it from the repos?

```
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by fjgaude on 2012-09-08
Downloading daily update and dd to flash drive on main box, Intel HD3000 box. Install starts going to manually selected partition, the stops just after the location is selected.

We wait, and I'm gonna try Alpha3 and see if I can install it.

---

### Post by fjgaude on 2012-09-08
Well, I installed Alpha3 and updated,upgraded, and all is well.

Don't know why the daily or Beta1 would not install.

---

### Post by axelsvag on 2012-09-09
I tried to install the lubuntu 12.10 beta 1 and the installation went perfectly but the same problem connecting and usb stick.

---

