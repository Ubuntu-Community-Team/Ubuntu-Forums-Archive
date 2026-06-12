---
title: "install package wireless-tools from usb using command line in an offline computer"
date: 2011-03-16
forum: Server Platforms
---

### Post by red1916 on 2011-03-16
Hi,

I installed ubuntu 10.10 server from an usb stick. I do not have access to a wired connection and do not have a CD drive, so now I need to configure the wireless connection.

for that I need to have wireless-tools which if i am not wrong are not installed by default

so the question is: **how can I install the wireless-tools package from an usb using only command line?**


note: I got internet access from another ubuntu-desktop PC so i can download any package needed, etc.

thx in advance

---

### Post by NIN101 on 2011-03-16
Hi,  download:    [http://packages.ubuntu.com/maverick/libiw30](http://packages.ubuntu.com/maverick/libiw30)   [http://packages.ubuntu.com/maverick/wireless-tools](http://packages.ubuntu.com/maverick/wireless-tools).    Copy these packages to your USB stick.  Now go to your server and mount the stick, open a terminal in it's directory and run as root: ```
dpkg -i [libiw packagename] [wireless-tools packagename]
```  So for example it can look like this: ```
dpkg -i libiw30_30~pre9-3ubuntu4_i386.deb wireless-tools_30~pre9-3ubuntu4_i386.deb
```

---

### Post by mikewhatever on 2011-03-16
The command to install a downloaded package would be as follows:
```
sudo dpkg -i package-name
```

suppose you download the 32bit version of wireless-tools:
```
sudo dpkg -i wireless-tools_30~pre9-3ubuntu4_i386.deb
```

Obviously, you'd have to mount the usb stick before doing that, as well as cd to it:
```
sudo mount /dev/sdb1 /mnt
cd /mnt
```

---

### Post by red1916 on 2011-03-20
thanks a million guys :)  it worked perfectly!

I owe you one.

---

