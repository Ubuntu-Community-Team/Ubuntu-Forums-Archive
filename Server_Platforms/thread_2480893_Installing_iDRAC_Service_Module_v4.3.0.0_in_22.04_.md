---
title: "Installing iDRAC Service Module v4.3.0.0 in 22.04 LTS"
date: 2022-11-13
forum: Server Platforms
---

### Post by wb6vpm on 2022-11-13
I have a Dell PowerEdge T330 that I am running Ubuntu 22.04.1 LTS on. Has anyone been able to successfully modify the setup.sh script to allow them to install the Dell iDRAC Service Module on it in Jammy? I found someone who had modified an older version of the script to install 20.04 from an 18.04 compatible script (3.5.x) before Dell finally released a proper 20.04 version ([https://github.com/randomnord/idracUbuntu20.04](https://github.com/randomnord/idracUbuntu20.04)), but I know that there are a lot of changes in how things are installed between 20 and 22, and a lot of things were depreciated from v20, so I really don't want to just arbitrarily change scripts and pray that I don't break things, when I try, since I'm by no means a Linux Guru, and depending on what goes wrong, probably wouldn't have the knowledge to back the damage out.

Here is the link to the version that I'm trying to install: [https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=2pk7t&oscode=us008&productcode=poweredge-t330](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=2pk7t&oscode=us008&productcode=poweredge-t330)

Thanks to anyone who reads this, and also to anyone who can help me sort this out!

---

### Post by MAFoElffen on 2022-11-13
In the linked script, lines 398 though line 403:
Change:
```

#check for Ubuntu18.
if [ "$OS" == "Ubuntu" ] && [ "$VER" == "[COLOR=#FF0000]20[/COLOR]" ] ; then
                GBL_OS_TYPE=${GBL_OS_TYPE_UBUNTU18}
                GBL_OS_TYPE_STRING="UBUNTU18"
                PATH_TO_RPMS_SUFFIX=UBUNTU18

```
To:
```

#check for Ubuntu18.
if [ "$OS" == "Ubuntu" ] && [ "$VER" == "[COLOR=#FF0000]22[/COLOR]" ] ; then
                GBL_OS_TYPE=${GBL_OS_TYPE_UBUNTU18}
                GBL_OS_TYPE_STRING="UBUNTU18"
                PATH_TO_RPMS_SUFFIX=UBUNTU18

```
Then it should work...

---

### Post by wb6vpm on 2022-11-14
That worked perfectly with one caveat. I had to install [FONT=var(--ff-mono)]libssl1.1 in order for it to work (the script crashed the first time around, as it is not installed in 22.04):
[/FONT]
For anyone else on here looking for how to get this done, the line you need to change is on line 294:
```
293        #check for Ubuntu20.
294        if [ "$OS" == "Ubuntu" ] && [ "$VER" == "[SIZE=3][COLOR=#ff0000]_***22***_[/COLOR][/SIZE]" ]; then
295                GBL_OS_TYPE=${GBL_OS_TYPE_UBUNTU20}
296                GBL_OS_TYPE_STRING="UBUNTU20"
297                PATH_TO_RPMS_SUFFIX=UBUNTU20
298                PREFIX_FOR_SATA="ubuntu20"
299        fi
```
Commands to download and install libssl1.1:
```
wget http://debian.mirror.ac.za/debian/pool/main/o/openssl/libssl1.1_1.1.1o-1_amd64.deb
sudo dpkg -i libssl1.1_1.1.1o-1_amd64.deb
```
Source:
[https://askubuntu.com/questions/1403778/upgrading-to-ubuntu-22-04-causes-libcrypto-errors-apt-dpkg-broken](https://askubuntu.com/questions/1403778/upgrading-to-ubuntu-22-04-causes-libcrypto-errors-apt-dpkg-broken)

---

