---
title: "Installing the most updated Virtualbox"
date: 2012-02-15
forum: Virtualisation
---

### Post by cat2005 on 2012-02-15
I am running Ubuntu 10.10 with kernel 2.6.35-28-generic-pae.  I want the most recent version of Virtualbox.

This is what my repository shows - all at Virtualbox version 3.2.8:

virtualbox-ose 3.2.8-dfsg-2ubuntu1
virtualbox-ose-qt
virtualbox-ose-dkms
virtualbox-ose-guest-dkms
virtualbox-ose-dbg
virtualbox-ose-fuse
virtualbox-ose-guest-x11
virtualbox-guest-additions
virtualbox-ose-guest-utils

To get the most recent version, which is 4.1.8, I went here:  [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

          and download this:  Ubuntu 10.10 ("Maverick Meerkat") [ i386]("http://download.virtualbox.org/virtualbox/4.1.8/virtualbox-4.1_4.1.8-75467%7EUbuntu%7Emaverick_i386.deb")   version 4.1.8

My repository shows the main 3.2.8 file (ose 3.2.8-dfsg) and many others 3.2.8 files, as shown above.  However, my repository only shows the one main 4.1.8 file.

**_Question:_**  Is that one mail 4.1.8 file all I need?  I don't care about the extension pack which gives USB functionality, etc.  However, I do want the "guest addition" option.

I appreciate your help.

Thank you.

---

### Post by japzone on 2012-02-16
You have to first Uninstall Virtualbox 3.2 before Installing 4.1.8. Once you've done this you can install Virtualbox 4.1 using the PPA or DEB file available on Virtualbox.org

---

### Post by thepisu on 2012-02-16
I advise you using the VirtualBox PPA, in order to have the latest official version; for Ubuntu 10.10 is this:

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free

You also have to register public key:

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

After installing VirtualBox, for having USB and other features download and install (open with double click) the Extension Pack:

[http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack](http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack)

---

### Post by cat2005 on 2012-02-20
> **japzone said:**
> You have to first Uninstall Virtualbox 3.2 before Installing 4.1.8. Once you've done this you can install Virtualbox 4.1 using the PPA or DEB file available on Virtualbox.org

Sorry, I should clarify.  I never had 3.2 installed.  3.2 showed up in repository automatically.  4.1.8 only appeared after placing it in the repository.

---

### Post by cat2005 on 2012-02-20
> **thepisu said:**
> I advise you using the VirtualBox PPA, in order to have the latest official version; for Ubuntu 10.10 is this:

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free

You also have to register public key:

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```After installing VirtualBox, for having USB and other features download and install (open with double click) the Extension Pack:

[http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack](http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack)


thepisu, or anyone else reading,

I went where you suggested:  

          deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free

but I only found a directory with nearly empty contents.

_Question_:  What is wrong with going to the virtualbox website and simply downloading the one I want?  I selected the Ubuntu Maverick (10.10) version:

          [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

I got the version directly from the virtualbox website and installed it with something called "gdebi package installer."  However, I haven't yet used it but I have downloaded and registered the key using the directions you gave.

Thanks.

---

### Post by cat2005 on 2012-02-29
Bump - anyone - Bueller ?

---

### Post by CharlesA on 2012-02-29
You add the "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free" to /etc/apt/sources.list, then update the repo list with:

```
sudo apt-get update
```

Then install Vbox:

```
sudo apt-get install virtualbox-4.1
```

Otherwise you can just download the deb from the same page and install it that way.

---

