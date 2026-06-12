---
title: "HOWTO:Add WebP (weppy) support to GIMP."
date: 2011-07-21
forum: Tutorials
---

### Post by ron999 on 2011-07-21
I used this method with Ubuntu Lucid Lynx 10.04 and GIMP 2.6.8.

First install some packages.
Paste this ***single*** command:-
```
sudo apt-get install \
build-essential \
checkinstall \
gimp
```

Then compile and install the WebP library **libwebp**.
Paste this ***single*** command:-
```
cd ~/ && \
wget http://webp.googlecode.com/files/libwebp-0.1.2.tar.gz && \
tar -xvf libwebp-0.1.2.tar.gz && \
cd libwebp-0.1.2 && \
./autogen.sh && \
./configure && \
make && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname libwebp \
--pkgversion 0.1.2 --backup=no --default && sudo ldconfig
```

When it's finished...
check that libwebp is installed OK with this command:-
```
cwebp -version
```

> ron@ubuntu:~$ cwebp -version
[COLOR="Red"]0.1.2[/COLOR]

Now to fix GIMP.
The WebP plugin is from here:- [http://registry.gimp.org/node/25366]("http://registry.gimp.org/node/25366")
Paste this ***single*** command:-
```
cd /tmp && \ 
export LIBS=-lwebp && \
wget http://registry.gimp.org/files/file-webp.tar_0.gz && \
tar -xvf file-webp.tar_0.gz && \
gimptool-2.0 --install file-webp.c
```

That's it.:P

When you start GIMP it should be able to open webp files.
And also Save As... WebP image (*.webp)

P.S.
How to revert changes.:(

To uninstall libwebp use Synaptic Package Manager.:)

To un-patch GIMP? :confused: 
Delete the **hidden** folder /home/user/.gimp-2.6 then re-start GIMP.

---

### Post by George Edison on 2011-08-06
That's great! (And I'm not just saying that because I wrote the plugin ;))

But there is a much easier way to install the plugin. I have setup a PPA on Launchpad that contains the packages [FONT="Courier New"]libwebp[/FONT] and [FONT="Courier New"]gimp-webp[/FONT]. You can find the PPA here: [https://code.launchpad.net/~george-edison55/+archive/webp](https://code.launchpad.net/~george-edison55/+archive/webp)

After adding the PPA, it's just a matter of:

```
sudo apt-get update ; sudo apt-get install gimp-webp
```

---

### Post by jan.petras on 2011-12-09
> **George Edison said:**
> That's great! (And I'm not just saying that because I wrote the plugin ;))

But there is a much easier way to install the plugin. I have setup a PPA on Launchpad that contains the packages [FONT="Courier New"]libwebp[/FONT] and [FONT="Courier New"]gimp-webp[/FONT]. You can find the PPA here: [https://code.launchpad.net/~george-edison55/+archive/webp](https://code.launchpad.net/~george-edison55/+archive/webp)

After adding the PPA, it's just a matter of:

```
sudo apt-get update ; sudo apt-get install gimp-webp
```

This is really amazing. I appreciate this. Thank you.

---

### Post by Spaceeman on 2013-04-02
Using GNU/Linux Mint 14 based on GNU/Linux Ubuntu quantal 12.10.

Adding PPA repository, update and install... :

```
# apt-add-repository ppa:george-edison55/webp 
# apt-get update
# apt-get install gimp-webp
```

A problem stay ... The plugin file of gimp-webp is in /lib/gimp/2.0/plug-ins folder "instead"(?) of /usr/lib/gimp/2.0/plug-ins

The ("bad"/"trivial") solution is to copy the file in "good" folder :

```
# cp /lib/gimp/2.0/plug-ins/file-webp /usr/lib/gimp/2.0/plug-ins/ 
```

Is this problem known ?

---

