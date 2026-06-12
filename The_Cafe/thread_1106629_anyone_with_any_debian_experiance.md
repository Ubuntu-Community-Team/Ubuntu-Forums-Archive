---
title: "anyone with any debian experiance?"
date: 2009-03-25
forum: The Cafe
---

### Post by mamamia88 on 2009-03-25
i just installed it to go alongside ubuntu and windows but can't figure out how to get my wireless broadcom driver working any ideas?

---

### Post by wolfen69 on 2009-03-25
you will need to get the broadcom driver from synaptic. just search for broadcom. you may need to enable a repo or 2 before it shows up in synaptic.

you may want to do the following also:
```
apt-get install wireless-tools wpasupplicant network-manager network-manager-gnome
```
i recommend wicd for wireless management.

Wicd is included in Debian Sid, so you can just use apt-get install to get it.

You can also use the apt repository. Just add the following line to your /etc/apt/sources.list

    deb [http://apt.wicd.net](http://apt.wicd.net) lenny extras 

where lenny is your version of Debian in lowercase (lenny, sid). You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    ```
wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 
```

Now you can apt-get update and apt-get install wicd to install Wicd. If you are using Lenny and you use Madwifi, make sure to use wext in Wicd.

---

### Post by mamamia88 on 2009-03-25
for some reason i can't even find synaptic

---

### Post by stmiller on 2009-03-25
In Debian you have to setup sudo, so that doesn't work like Ubuntu out of the box.

You may have to do:

```

su -

```
to get a root shell. Then:

```

apt-get install synaptic

```

---

### Post by ddnev45 on 2009-03-25
If you have the xfce/lxde version of Debian, synaptic isn't included. You'll have to install packages with apt.

*edit -- too late, with this post.*

---

### Post by mamamia88 on 2009-03-25
i have the gnome version and how can i download the synaptic package if i can't even get internet acess in debian?  im in ubuntu now

---

### Post by wolfen69 on 2009-03-26
you will probably have to temporarily hook up your computer via network cable to a router.

or, you could download [this]("http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2") file and put it in your home folder and
```
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..
```
then download [this]("http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2") file and extract it to the /lib/firmware directory. then restart. good luck either way.

---

### Post by Polygon on 2009-03-26
or connect a ethernet cable to your laptop/computer to a router or a jack temporarily

---

### Post by Yashiro on 2009-03-26
Installing Debian using only a Wireless connection is not fun.

*If you are new to Debian* and you installed using the CD1 without having any net access. 
Do yourself a favour:
Plug in a wire. 
Do a full re-install.
Select the base system and standard desktop using the gui installer.

Finding out which repositories you need to add manually, 
which non-free modules you may need, 
finding basic apps you need,
including build tools
will take you more time than the re-install with ethernet plugged in.

A Debian base install is OK if you know what your are doing. 
Otherwise it's alot of digging through rubbish posts on the internet to sort it out.

---

