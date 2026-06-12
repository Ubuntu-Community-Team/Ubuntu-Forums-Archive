---
title: "&quot;thermald&quot; is no longer required in Ubuntu Studio 14.04."
date: 2015-12-24
forum: Ubuntu Studio
---

### Post by sethanath2 on 2015-12-24
Hi,

I wonder if someone can teach me why "thermald" is no longer required in Ubuntu Studio 14.04.

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  thermald
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I googled, and I found that "thermald" prevents machines from overheating and was introduced in the 14.04 Ubuntu Trusty LTS release.

Here are the list on my grub menu

- Linux 3.19.0-42-generic
- Linux 3.19.0-42-generic (recovery mode)
- Linux 3.19.0-31-lowlatency
- Linux 3.19.0-31-lowlatency (recovery mode)
- Linux 3.13.0-74-lowlatency
- Linux 3.13.0-74-lowlatency (recovery mode)
- Linux 3.13.0-74-generic
- Linux 3.13.0-74-generic (recovery mode)

I also wonder why I do not have Linux 3.19.0-42-lowlatency installed.

$ apt-cache policy linux-lowlatency
linux-lowlatency:
  Installed: 3.13.0.74.80
  Candidate: 3.13.0.74.80
  Version table:
 *** 3.13.0.74.80 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.13.0.24.28 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages

Thank you so much.

---

### Post by matt_symes on 2015-12-24
Hi

> **sethanath2 said:**
> 
Here are the list on my grub menu

- Linux 3.19.0-42-generic
- Linux 3.19.0-42-generic (recovery mode)
- Linux 3.19.0-31-lowlatency
- Linux 3.19.0-31-lowlatency (recovery mode)
- Linux 3.13.0-74-lowlatency
- Linux 3.13.0-74-lowlatency (recovery mode)
- Linux 3.13.0-74-generic
- Linux 3.13.0-74-generic (recovery mode)

I also wonder why I do not have Linux 3.19.0-42-lowlatency installed.

$ apt-cache policy linux-lowlatency
linux-lowlatency:
  Installed: 3.13.0.74.80
  Candidate: 3.13.0.74.80
  Version table:
 *** 3.13.0.74.80 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.13.0.24.28 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages

Thank you so much.

Do you have both linux-lowlatency-lts-vivid and linux-generic-lts-vivid kernel metapackages installed at the same time ? Maybe that's causing a problem ?

What does this return ?

```
apt-cache policy linux-lowlatency-lts-vivid linux-generic-lts-vivid
```

> 
I wonder if someone can teach me why "thermald" is no longer required in Ubuntu Studio 14.04.

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  thermald
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I googled, and I found that "thermald" prevents machines from overheating and was introduced in the 14.04 Ubuntu Trusty LTS release.


Not sure why.

thermald suggests it's a dependency of the kernel meta packages but if you look at any of the kernel packages such as linux-image-lowlatency, it is a recommends and not a hard dependency.

```

matthew-xu-16-04:/var/log:0 % acrd thermald              
thermald
Reverse Depends:
  linux-image-generic
  linux-signed-image-lowlatency
  linux-signed-image-generic
  linux-image-lowlatency
matthew-xu-16-04:/var/log:0 % acde linux-image-lowlatency
linux-image-lowlatency
  Depends: linux-image-4.3.0-2-lowlatency
  Depends: linux-firmware
  Recommends: thermald
matthew-xu-16-04:/var/log:0 % 
```

It would need some research to see why apt wants to remove it.

Kind regards

---

### Post by sethanath2 on 2015-12-24
Here are the result.

$ apt-cache policy linux-lowlatency-lts-vivid linux-generic-lts-vivid
linux-lowlatency-lts-vivid:
  Installed: (none)
  Candidate: 3.19.0.42.27
  Version table:
     3.19.0.42.27 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
linux-generic-lts-vivid:
  Installed: (none)
  Candidate: 3.19.0.42.27
  Version table:
     3.19.0.42.27 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages

Thanks.

---

### Post by sethanath2 on 2015-12-25
Before this problem happened, here are some of the things I did.

$ sudo apt-get install linux-generic-lts-vivid
Please note that I did the command above by accident. 
It should have been 
$ sudo apt-get install linux-generic-lts-trusty

$ sudo apt-get remove linux-generic-lts-vivid
$ sudo apt-get remove linux-image-generic-lts-vivid linux-headers-generic-lts-vivid

$ sudo apt-get install linux-lowlatency

I am not sure about the sequence above, however.

Thank you.

---

### Post by matt_symes on 2015-12-25
Hi

> **sethanath2 said:**
> Before this problem happened, here are some of the things I did.

$ sudo apt-get install linux-generic-lts-vivid
Please note that I did the command above by accident. 
It should have been 
$ sudo apt-get install linux-generic-lts-trusty

$ sudo apt-get remove linux-generic-lts-vivid
$ sudo apt-get remove linux-image-generic-lts-vivid linux-headers-generic-lts-vivid

$ sudo apt-get install linux-lowlatency

I am not sure about the sequence above, however.

Thank you.

If you want the 3.19 series of kernels for the low latency kernels to be installed automatically, you need to install linux-lowlatency-lts-vivid.

It's the Vivid hardware enablement stack for trusty.

I have the Vivid stack in my Trusty install.
```

matthew-laptop:/home/matthew:1 % apt-cache policy linux-generic-lts-vivid
linux-generic-lts-vivid:
  Installed: 3.19.0.39.25
  Candidate: 3.19.0.42.27
  Version table:
     3.19.0.42.27 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
 *** 3.19.0.39.25 0
        100 /var/lib/dpkg/status
matthew-laptop:/home/matthew:1 % 
```

The 3.19 series of kernels will automatically get installed then.

Kind regards

---

### Post by sethanath2 on 2015-12-25
> **matt_symes said:**
> Hi



If you want the 3.19 series of kernels for the low latency kernels to be installed automatically, you need to install linux-lowlatency-lts-vivid.

It's the Vivid hardware enablement stack for trusty.

I have the Vivid stack in my Trusty install.
```

matthew-laptop:/home/matthew:1 % apt-cache policy linux-generic-lts-vivid
linux-generic-lts-vivid:
  Installed: 3.19.0.39.25
  Candidate: 3.19.0.42.27
  Version table:
     3.19.0.42.27 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
 *** 3.19.0.39.25 0
        100 /var/lib/dpkg/status
matthew-laptop:/home/matthew:1 % 
```

The 3.19 series of kernels will automatically get installed then.

Kind regards

I see. The problem with thermald is now gone as well.

---

### Post by sethanath2 on 2015-12-25
> **matt_symes said:**
> Hi

Do you have both linux-lowlatency-lts-vivid and linux-generic-lts-vivid kernel metapackages installed at the same time ? Maybe that's causing a problem ?

What does this return ?

```
apt-cache policy linux-lowlatency-lts-vivid linux-generic-lts-vivid
```



Do I still need these two linux-lowlatency-lts-vivid and linux-generic-lts-vivid kernel to be installed?

Thanks.

---

### Post by matt_symes on 2015-12-25
Hi

> **sethanath2 said:**
> Do I still need these two linux-lowlatency-lts-vivid and linux-generic-lts-vivid kernel to be installed?

Thanks.

Choose one or the other. From your previous posts it sounds like you want the low latency kernel so remove linux-generic-lts-vivid.

If you want to continue receiving kernel updates for the 3.19 kernel series for the low latency kernel then you want to keep linux-lowlatency-lts-vivid.

The newest low latency kernel from the repos is what linux-lowlatency-lts-vivid is dependent upon and, if you keep it installed, you will automatically get the newest 3.19 low latency kernels when  they become available.

I suspect you want to keep it :).

If this answers your questions then please mark this thread as SOLVED using the thread tools in the menus at the top of the post #1.

It'll help others looking for a solution to similar problems.

Kind regards

---

### Post by sethanath2 on 2015-12-25
> **matt_symes said:**
> Hi



Choose one or the other. From your previous posts it sounds like you want the low latency kernel so remove linux-generic-lts-vivid.

If you want to continue receiving kernel updates for the 3.19 kernel series for the low latency kernel then you want to keep linux-lowlatency-lts-vivid.

The newest low latency kernel from the repos is what linux-lowlatency-lts-vivid is dependent upon and, if you keep it installed, you will automatically get the newest 3.19 low latency kernels when  they become available.

I suspect you want to keep it :).

If this answers your questions then please mark this thread as SOLVED using the thread tools in the menus at the top of the post #1.

It'll help others looking for a solution to similar problems.

Kind regards

I actually want to see both of them. During boot, I have my grub menu displayed, and I can choose whether I should boot with lowlatency kernel or generic one. 

Can I keep both and just choose from the grub menu, then?

Thanks.

---

### Post by matt_symes on 2015-12-25
Hi

> **sethanath2 said:**
> I actually want to see both of them. During boot, I have my grub menu displayed, and I can choose whether I should boot with lowlatency kernel or generic one. 

Can I keep both and just choose from the grub menu, then?

Thanks.

Yep. You can keep both. You may have to remember to remove the older ones more often depending on your setup.

So make sure you have  linux-lowlatency-lts-vivid and linux-generic-lts-vivid.

This will ensure you get both the newest low latency and generic kernels for the Vivid stack in Trusty.

Kind regards

---

