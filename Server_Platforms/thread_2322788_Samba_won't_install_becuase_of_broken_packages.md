---
title: "Samba won't install becuase of broken packages"
date: 2016-04-30
forum: Server Platforms
---

### Post by padred123 on 2016-04-30
I am running Ubuntu Server 14.04.4 and I didn't install Samba with the original OS setup. I would like to install it now but I keep getting a error about broken packages. It appears that the main hangup is the samba-libs dependency. Its saying "***Depends: libldb1 (< 1:1.1.25~) but 2:1.1.17-2 is to be installed**" *but I already have the latest libldb1 installed. I've tried almost everything I can google but maybe I'm overlooking something. Any pointers would be greatly appreciated. 


[B]Here's whats happening:
[/B]
```
root@MAILSVR:/etc/apt# sudo apt-get  install  sambaReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 samba : Depends: python-samba but it is not going to be installed
         Depends: samba-common-bin (= 2:4.3.8+dfsg-0ubuntu0.14.04.2) but it is not going to be installed
         Depends: samba-libs (= 2:4.3.8+dfsg-0ubuntu0.14.04.2) but it is not going to be installed
         Recommends: samba-dsdb-modules but it is not going to be installed
         Recommends: samba-vfs-modules but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


[B]Here's what aptitude gives me:
[/B]
```
root@MAILSVR:/etc/apt# aptitude install sambaThe following NEW packages will be installed:
  libwbclient0{a} python-crypto{a} python-ldb{ab} python-samba{a} python-talloc{a} python-tdb{ab} samba samba-common{a} samba-common-bin{a} samba-dsdb-modules{a} 
  samba-libs{ab} samba-vfs-modules{a} tdb-tools{a} 
0 packages upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,519 kB of archives. After unpacking 48.3 MB will be used.
The following packages have unmet dependencies:
 python-tdb : Depends: libtdb1 (= 1.3.8-0ubuntu0.14.04.1) but 1.3.8-2 is installed.
 samba-libs : Depends: libldb1 (< 1:1.1.25~) but 2:1.1.17-2 is installed.
 python-ldb : Depends: libldb1 (= 1:1.1.24-0ubuntu0.14.04.1) but 2:1.1.17-2 is installed.
The following actions will resolve these dependencies:


     Keep the following packages at their current version:
1)     python-ldb [Not Installed]                         
2)     python-samba [Not Installed]                       
3)     python-tdb [Not Installed]                         
4)     samba [Not Installed]                              
5)     samba-common-bin [Not Installed]                   
6)     samba-dsdb-modules [Not Installed]                 
7)     samba-libs [Not Installed]                         
8)     samba-vfs-modules [Not Installed]                  


     Leave the following dependencies unresolved:         
9)     samba-common recommends samba-common-bin           




Accept this solution? [Y/n/q/?] 
```


[B]Samba-libs error:
[/B]
```
root@MAILSVR:/etc/apt# apt-get install samba-libsReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 samba-libs : Depends: libldb1 (< 1:1.1.25~) but 2:1.1.17-2 is to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by darkod on 2016-04-30
There are couple of commands to try when there are broken dependencies. First try something like:
```
sudo apt-get -f install
```

And check that you have enough free space on the root or /boot partition (if there is separate /boot). Sometimes when you have small separate /boot it will fill up and apt doesn't work any more.

---

### Post by padred123 on 2016-04-30
> **darkod said:**
> There are couple of commands to try when there are broken dependencies. First try something like:
```
sudo apt-get -f install
```

And check that you have enough free space on the root or /boot partition (if there is separate /boot). Sometimes when you have small separate /boot it will fill up and apt doesn't work any more.

I have plenty of space because I don't have a separate boot partition. I've tried apt-get -f install and I get no results. Thx for the help.

```
root@MAILSVR:/etc/apt# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by darkod on 2016-04-30
Did you try to update the apt cache? Try this:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

I see that you are running the commands as root. If that is the case, you don't need the sudo in front, simply ignore it. We usually put the full command for apt-get including sudo because many users run it as their own user. If you are using root, drop the sudo part.

---

### Post by padred123 on 2016-05-02
> **darkod said:**
> Did you try to update the apt cache? Try this:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

I see that you are running the commands as root. If that is the case, you don't need the sudo in front, simply ignore it. We usually put the full command for apt-get including sudo because many users run it as their own user. If you are using root, drop the sudo part.

Yep I've tried that too and I'm running as root because I don't like having to constantly put in my password. This makes no sense! (To me at least hahaa)

---

### Post by padred123 on 2016-05-05
The issue was with my package sources so I changed my /etc/apt/sources.list back to default with the help of [repogen.simplylinux.ch]("https://repogen.simplylinux.ch/"). 

Then I did a 
[I]**apt-get update** 
[/I][I]**apt-get autoremove libtdb1 --purge** 

[/I]and then
[I][B]apt-get install libtdb1=1.3.8-0ubuntu0.14.04.1

[/B][/I]then 
[I][B]apt-get install samba

[/B][/I]Done. Thx for your assistance!

---

### Post by KaRiToR on 2016-12-14
The same happened to me but none of the previous replies worked for me.... after searching for the solution for many hours I got this one to work properly:

sudo wget [http://launchpadlibrarian.net/109052632/python-support_1.0.15_all.deb](http://launchpadlibrarian.net/109052632/python-support_1.0.15_all.deb)
sudo dpkg -i python-support_1.0.15_all.deb
Run: 
sudo apt-get install samba

I'm using ubuntu server 16.04.1

Cheers

---

