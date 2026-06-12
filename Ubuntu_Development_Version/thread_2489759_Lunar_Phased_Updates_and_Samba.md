---
title: "Lunar Phased Updates and Samba"
date: 2023-08-09
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2023-08-09
This is just a report on my findings with Phased Updates and Samba.
This was was my upgrade today:
```
Kept Back, Will Not Be Upgraded                                                
================================================================================
  Package:                  Old Version:      New Version:               Size:  
  initramfs-tools           0.142ubuntu2      0.142ubuntu2.2             69 KB  
  initramfs-tools-bin       0.142ubuntu2      0.142ubuntu2.2             56 KB  
  initramfs-tools-core      0.142ubuntu2      0.142ubuntu2.2            202 KB  
  libldb2                   2:2.6.2+samba4.1  2:2.6.2+samba4.           640 KB  
                            7.7+dfsg-1ubuntu  17.7+dfsg-1ubun                   
                            1.1               tu2                               
  libsmbclient              2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1           248 KB  
                            buntu1.1          ubuntu2                           
  libwbclient0              2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1           133 KB  
                            buntu1.1          ubuntu2                           
  python3-ldb               2:2.6.2+samba4.1  2:2.6.2+samba4.           201 KB  
                            7.7+dfsg-1ubuntu  17.7+dfsg-1ubun                   
                            1.1               tu2                               
  python3-samba             2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1          22.2 MB  
                            buntu1.1          ubuntu2                           
  samba                     2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1           4.1 MB  
                            buntu1.1          ubuntu2                           
  samba-ad-provision        2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1          14.1 MB  
                            buntu1.1          ubuntu2                           
  samba-common              2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1           225 KB  
                            buntu1.1          ubuntu2                           
  samba-common-bin          2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1           4.7 MB  
                            buntu1.1          ubuntu2                           
  samba-dsdb-modules        2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1           1.6 MB  
                            buntu1.1          ubuntu2                           
  samba-libs                2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1          25.0 MB  
                            buntu1.1          ubuntu2                           
  samba-vfs-modules         2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1           1.9 MB  
                            buntu1.1          ubuntu2                           
  smbclient                 2:4.17.7+dfsg-1u  2:4.17.7+dfsg-1           2.1 MB  
                            buntu1.1          ubuntu2                           
                                                                                
================================================================================
 Summary                                                                        
================================================================================
 Upgrade    1 Packages                                                          
 Kept Back 16 Packages                                      
```
I need on occasion to depend on Samba so I bit the bullet and manually installed the held packages. (Today was a good day for that no Samba usage) 
```

sudo apt install  libsmbclient  libwbclient0  python3-ldb python3-samba    samba  samba-ad-provision  samba-common samba-common-bin samba-dsdb-modules samba-libs  samba-vfs-modules   smbclient  
```
After my Reboot all is good here on my machine, but your  mileage may vary. **[COLOR="#FF0000"](This is testing only not to be ran for production machines)[/COLOR]**

---

### Post by corradoventu on 2023-08-10
List of packages in phased update: [https://ubuntu-archive-team.ubuntu.com/phased-updates.html](https://ubuntu-archive-team.ubuntu.com/phased-updates.html)
If you want force the installation of phased updates: ```
apt -o APT::Get::Always-Include-Phased-Updates=true upgrade
```
will force install JUST FOR NEXT UPDATE
see full explain in: [https://askubuntu.com/questions/1431741/how-to-disable-skip-phased-updates-on-22-04](https://askubuntu.com/questions/1431741/how-to-disable-skip-phased-updates-on-22-04)

---

### Post by #&amp;thj^% on 2023-08-10
> **corradoventu said:**
> List of packages in phased update: [https://ubuntu-archive-team.ubuntu.com/phased-updates.html](https://ubuntu-archive-team.ubuntu.com/phased-updates.html)
If you want force the installation of phased updates: ```
apt -o APT::Get::Always-Include-Phased-Updates=true upgrade
```
will force install JUST FOR NEXT UPDATE
see full explain in: [https://askubuntu.com/questions/1431741/how-to-disable-skip-phased-updates-on-22-04](https://askubuntu.com/questions/1431741/how-to-disable-skip-phased-updates-on-22-04)
+1
This is a good reply, useful for other members. (I already knew though)
When i took the Phased upgrade's it was at (40% phased) now at:
```
apt policy initramfs-tools-bin
initramfs-tools-bin:
  Installed: 0.142ubuntu2.2
  Candidate: 0.142ubuntu2.2
  Version table:
 *** 0.142ubuntu2.2 500 (phased 60%)
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.142ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> apt policy samba
samba:
  Installed: 2:4.17.7+dfsg-1ubuntu2
  Candidate: 2:4.17.7+dfsg-1ubuntu2
  Version table:
 *** 2:4.17.7+dfsg-1ubuntu2 500 (phased 60%)
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:4.17.7+dfsg-1ubuntu1.1 500
        500 http://security.ubuntu.com/ubuntu lunar-security/main amd64 Packages
     2:4.17.7+dfsg-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages

```

---

### Post by #&amp;thj^% on 2023-08-11
Final Reply for this thread,  Everything as it should be, all in, all good.
```
apt policy samba
samba:
  Installed: 2:4.17.7+dfsg-1ubuntu2
  Candidate: 2:4.17.7+dfsg-1ubuntu2
  Version table:
 *** 2:4.17.7+dfsg-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:4.17.7+dfsg-1ubuntu1.1 500
        500 http://security.ubuntu.com/ubuntu lunar-security/main amd64 Packages
     2:4.17.7+dfsg-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages

###And

apt policy initramfs-tools
initramfs-tools:
  Installed: 0.142ubuntu2.2
  Candidate: 0.142ubuntu2.2
  Version table:
 *** 0.142ubuntu2.2 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.142ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages

```
I find all this a very interesting upgrade process. (thought provoking)

---

