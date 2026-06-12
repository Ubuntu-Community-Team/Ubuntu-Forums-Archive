---
title: "missing header when running VMWare player"
date: 2011-05-01
forum: Virtualisation
---

### Post by kvant_doan on 2011-05-01
Hello all,

I am a newbie in Ubuntu. I have downloaded VMWare player to run for my exercises but when I run VMWare player I get the windows likes this

[[IMG]http://img834.imageshack.us/img834/4975/firsterror.png[/IMG]]("http://img834.imageshack.us/i/firsterror.png/")


[IMG]http://img834.imageshack.us/i/firsterror.png/[/IMG]

Later, I choose the path /usr/src/linux-headers-2.6.38-8-generic for the path. But the error window also appears 

[IMG]http://img20.imageshack.us/i/seconderror.png/[/IMG][[IMG]http://img20.imageshack.us/img20/5227/seconderror.png[/IMG]]("http://img20.imageshack.us/i/seconderror.png/")



I also google some link in internet but hopeless and use some commands like sudo apt-get install linux-source but ubuntu announces that I am using the newest version of linux header

Previously, I tried to compile linux source so is it the problem? My computer just upgraded to Natty 11.04, are there any incompatible between 11.04 and VMWare?

Hope you can help. Thank you so much

---

### Post by fjgaude on 2011-05-02
Player 1.3.4 works fine with 11.04. Maybe you need to download essentials:

```
sudo apt-get install build-essentials
```

Let's see if that does it for you.

---

### Post by kvant_doan on 2011-05-02
Hi fjgaude,

Thank you for your help. I also try your command but it's still the same. Would you please give me more information?

This is the result after running your command:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  java-common libjaxp1.3-java python-gnutls tzdata-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

---

### Post by kvant_doan on 2011-05-03
Dear all, 

Thank all, I have fixed my own problem. It happens because all of link in linux-headers-2.6.38-8-generic link to linux-headers-2.6.38-8 but this folder in my computer has some problems so all the link are broken.

Remove the linux-headers-2.6.38-8 and reinstall it.

---

