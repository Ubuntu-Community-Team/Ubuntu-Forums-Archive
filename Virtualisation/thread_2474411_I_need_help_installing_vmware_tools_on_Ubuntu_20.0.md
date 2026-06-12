---
title: "I need help installing vmware tools on Ubuntu 20.04"
date: 2022-04-28
forum: Virtualisation
---

### Post by Complete on 2022-04-28
This might be more of a VMware question than an Ubuntu question. But I suppose it might be helpful to make this post here in case I can find some added insight into my issue.

I need to know where to find the ISO file for Ubuntu to install VMware Tools.

I installed VMWARE Workstation 16 Pro to move files. First, I wanted to know how to move files from the hosting computer to the Virtual Machine My computer is a Windows 10 Enterprise and the OS of my vitrual machine is Ubuntu 22.04 64-bit.

I found that I need to install VMware tools before I can share a folder.

[https://i.stack.imgur.com/yFqIq.png](https://i.stack.imgur.com/yFqIq.png)

So I went to packages.vmware.com/tools and downloaded the ISO for Windows, thinking that the ISO type was supposed to be for the hosting computer OS, and not for the Virtual Machine. What I got, did not run on Ubuntu and I was told that it was supposed to be run only if the Virtual Machine was Windows.

[https://i.stack.imgur.com/JvlOF.png](https://i.stack.imgur.com/JvlOF.png)

There must be another ISO that is just for linux (Ubuntu)

I have been trying to find the ISO image specifically for Ubunto or Linux. and, so far, I have not found it. Maybe there is a special method to installing the VMware tools for Ubuntu that does not require an ISO image.

Here is what I have done. I went to packages.vmware.com/tools and, without describing the tree structures of all the folders and subfolders, I will sum up. Looking under the latest releases we see one folder for windows and another folder for ubuntu. This lead me to believe I was on the right path. From this point, drilling down the subfolders to find the ISO disk image for a windows virtual machine was easy. For Ubuntu, the experience was different.

There are four folders for Ubuntu. I think thay are for divverent versions (or updates) of Ubuntu they are:

lucid natty oniric precise I am using verision 22.04. I do not think any of these are for that version. So which one should I use?

But whichever one I pick, I do not find any ISO files. Instead I only find a multitude of .DEB files.

Please help

---

### Post by QIII on 2022-04-28
Moved to Virtualisation as a better location.

---

### Post by DuckHook on 2022-04-28
Please don't post with large images as this is problematic for members on small screens or those who have restricted data plans. Images can be added as attachments using the paperclip icon in the Go Advanced toolbar.

---

### Post by Complete on 2022-04-30
> **DuckHook said:**
> Please don't post with large images as this is problematic for members on small screens or those who have restricted data plans. Images can be added as attachments using the paperclip icon in the Go Advanced toolbar.

OK, but they were links.  

I have news.  The images I have linked to are smaller. So I do not think they will be problimatic.

I have some good news and some news that might not be so good.  First, the good news, I got to this point:

[https://i.stack.imgur.com/5ISP8.png](https://i.stack.imgur.com/5ISP8.png)

So this means that I have VMware Tools 10.3.23 build-16594550 for Linux installed successfully.

The bad news is that I got to this point:

[https://i.stack.imgur.com/X89uZ.png](https://i.stack.imgur.com/X89uZ.png)

This means, of course, that the pl program I was running to install VMware Tools tried to launch another script that would have configured the tools but, strangely, it failed.  I do not why.   It says I do not have permissions.  So, I figured I would try running this pl file seperately instead of being invoked.

[https://i.stack.imgur.com/XjPg2.png](https://i.stack.imgur.com/XjPg2.png)

---

