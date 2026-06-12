---
title: "How To: Set up a VMware Server host with no GUI"
date: 2007-12-21
forum: Virtualisation
---

### Post by jayson.rowe on 2007-12-21
Inspired by a reply I made in another thread, here is a "re-paste" so it can be more visible and available to folks looking for a "How To"

Yes, you can install VMware Server on a system without a GUI, you will just have to install the VMware Console (downloadable from VMware for both Linux and Windows) on a remote system to administer it. That is how my personal VMware host server is set up.

The easiest way is to use Ubuntu 7.04 server as VMware Server is in the commercial repo, so to get it set up, simply install Ubuntu Server 7.04 (the default install will not install the X window system).

You will want to run your initial updates (which will be quite small since there is no GUI and a bunch of other apps installed), this is especially important as it will install a new kernel, and the VMware module in the commercial repo is built against the newer kernel, so execute:

```
sudo apt-get update
```

and then

```
sudo apt-get upgrade
```

Then you will need to add the following line to your Sources list, so execute:

```
sudo nano /etc/apt/sources.list
```

The append the following line to the end of the file:

```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

Now execute:

```
sudo apt-get update
```

If you host is an x86_64, and you are running the 64-bit version, you may need to install the ia32-libs package. Do this by executing:

```
sudo apt-get install ia32-libs
```

You will also need to install xinetd, so run:

```
sudo apt-get install xinetd
```

Now you are ready to install VMware Server, so execute:

```
sudo apt-get install vmware-server
```

It's an 80MB file, so while that is downloading, head on over to the VMware site [to get your free serial number.]("http://register.vmware.com/content/registration.html")

Now that you have written down your Serial Number, go check back up on your server - it will ask you some basic questions, and for most people, the defaults are fine. Eventually you will be presented with a EULA you have to read and agree to, and after some more installing stuff, you will be asked to enter your serial. After that, you are all set!

---

