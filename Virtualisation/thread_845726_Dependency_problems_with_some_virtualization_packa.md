---
title: "Dependency problems with some virtualization packages"
date: 2008-06-30
forum: Virtualisation
---

### Post by Endymion Zhang on 2008-06-30
I am a newbie in ubuntu forum, can anyone give me a help?

I want to install UME on my system and followed the steps
[https://wiki.ubuntu.com/Testing/Cases/UMEinstall](https://wiki.ubuntu.com/Testing/Cases/UMEinstall)

But when I try to install 
sudo apt-get install virtual-mobile-builder
It tells me virtual-mobile-builder can't be found, but I have add that repository in my /etc/apt/sources.list.
So I go to that website and download the package virtual-mobile-builder manually. Then try to
sudo dpkg -i virtual-mobile-builder_1.0-0ubuntu1~804vmb1_all.deb
It tells me ubuntu-vm-builder (>= 0.4-0ubuntu0.3) should be installed first.
So, I use apt-get to install ubuntu-vm-builder but the version is  0.4-0ubuntu0.3~804um1, which results in the original package virtual-mobile-builder which I want to installed can't be correctly configured.

Now, my question is:
1) if the dependency problem can't be resolved by apt automatically, how can I do these steps manually? How can I find a specific version of one package and not always get the latest version of one package?
2) if some dependency problem can't be resolved eventually, is there any option which can ignore these dependencies, such as --nodeps in rpm, let me go ahead to install and configure the package? 

Thanks!

---

