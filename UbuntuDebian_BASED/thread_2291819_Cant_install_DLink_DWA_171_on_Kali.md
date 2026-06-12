---
title: "Cant install DLink DWA 171 on Kali"
date: 2015-08-23
forum: Ubuntu/Debian BASED
---

### Post by ahmed_mohamed2 on 2015-08-23
I keep getting this error when I try to install dlink dwa 171 drivers

```

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/[kernel]/build M=/root/Desktop/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517  modules
make: *** /lib/modules/[kernel]/build: No such file or directory.  Stop.
make: *** [modules] Error 2
```

---

### Post by Hadaka on 2015-08-23
Hi, see post #4 and #6
[http://ubuntuforums.org/showthread.php?t=2240631&](http://ubuntuforums.org/showthread.php?t=2240631&)
good luck.

---

### Post by ahmed_mohamed2 on 2015-08-23
I already tried that, I get this error.
[http://i.imgur.com/fEs6YZt.png](http://i.imgur.com/fEs6YZt.png)

---

### Post by Hadaka on 2015-08-23
hi..
```
sudo apt-get install linux-headers-generic build-essential git
```
is a valid clean command and runs fine on my machine.
I noticed you are in the root mode...why...you shuould not be in the root#
i suggest you type exit and try the commands again..including....sudo apt-get update.
just run chill555's file from a regular terminal.
post back if you have problems
thanks.
```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd ~/rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au
```

---

### Post by ahmed_mohamed2 on 2015-08-23
I still get make is not a valid directory, also what directory should I be in, if not the root directory.

---

### Post by Hadaka on 2015-08-23
you should be in just your regular home directory.
 
here it is on my machine... HOME DIRECTORY
```
hadaka@the-beach:~$ sudo apt-get install linux-headers-generic build-essential git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version.
linux-headers-generic is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hadaka@the-beach:~$ 

```
and also as ##ROOT
```
hadaka@the-beach:~$ sudo su
[sudo] password for hadaka: 
root@the-beach:/home/hadaka# sudo apt-get install linux-headers-generic build-essential git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version.
linux-headers-generic is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@the-beach:/home/hadaka# exit
exit

```
So it looks like you have other issues.

---

### Post by chili555 on 2015-08-24
First of all, you absolutely shouldn't be running as root in root's directory. One of the great safeguards in Linux is that ordinary users can't make fundamental changes to the entire system. Therefore, neither can drive-by virii, malware, malicious emails, etc. You have made the decision to remove the seatbelts *AND* the airbags *AND*, for that matter, the brakes from your system. Please stop now:```
exit 
cd ~
```When you need to make needed changes, you can gain administrative privileges temporarily with sudo.

Second of all, it appears that you are running Kali Linux. It is a specialized derivation of Ubuntu, I believe. These specializations make it different enough from Ubuntu that ordinarily easy commands like this don't work:```
sudo apt-get install linux-headers-generic
```You might try:```
sudo apt-get install linux-headers-`uname -r`
```Beyond that, my friend Hadaka and I have no other suggestions. We know nothing about Kali.

---

### Post by howefield on 2015-08-24
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by coffeecat on 2015-08-24
@ahmed_mohamed2, I've edited your thread title. Kali is based on Debian and has nothing to do with Ubuntu. Although you are welcome to post your question in this section of the forum, you may find more people with experience of Kali on their own forum:

[http://forums.kali.org/](http://forums.kali.org/)

---

