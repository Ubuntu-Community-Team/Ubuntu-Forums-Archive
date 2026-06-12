---
title: "wireless connection *novice question*"
date: 2011-05-29
forum: Server Platforms
---

### Post by snuggerdog on 2011-05-29
Hello, 

so i have most recent ubuntu server installed (10.04 i believe) and currently i have a usb netgear WG111 v3 plugged into my computer server. However it does not supply internet. I was told to edit the /etc/network/interfaces file and put in ```

[LIST=1]
[*]/etc/network/interfaces
[*]auto lo wlan0
[*]iface lo inet loopback
[*]iface eth0 inet dhcp
[*]iface wlan0 inet manual
[*]wpa-roam /etc/wpa_supplicant.conf
[*]wpa-roam-default-iface wlan0-default
[*]iface wlan0-default inet dhcp
[*]---------------------------------
[*]wpa_supplicant.conf
[*]network={
[*] ssid="UNPRINTABLE"
[*] psk="UNPRINTABLE"
[*]}
[/LIST]

```but i have no idea how to edit it properly let alone, And this assumes your wireless NIC is already supported and visible as wlan0. Could someone help me or perhaps walk me through the process to correctly set it up so i don't have to bridge my connection from my laptop please?

---

### Post by nicolasdiogo on 2011-05-29
did you see this post

[http://ubuntuforums.org/archive/index.php/t-1259003.html](http://ubuntuforums.org/archive/index.php/t-1259003.html)

---

### Post by snuggerdog on 2011-05-29
I am looking at it and is says use wpa_passphrase to g4et your hex key. How exactly do i do that? also when i opened up my /etc/wpa_supplicant.conf in editor, there is nothing in there

edit: i used [http://jorisvr.nl/wpapsk.html](http://jorisvr.nl/wpapsk.html) to generate a hex key since i had no idea how to use the wpa_passphrase method and i manually put it in. After restarting the network i still get an error saying /sbin/wpa_supplicant daemon failed to start but i am able to ping from my router, just not able to connect to internet, did i do something wrong?

---

### Post by snuggerdog on 2011-05-29
Scratch everything, Lets start from beginning since i'm receiving no aid from continuing from where i've already started, How do i set up a netgear WG111 v3 usb wireless adapter on ubuntu server 11.04.?

---

### Post by Dry Lips on 2011-05-29
Are you sure that the modules for your wireless antenna are included in
the kernel of Ubuntu server? I've got a D-link wireless Usb antenna that 
I wanted to use with an old version of Ubuntu server; of course the module
was not included, so I had to download the driver and try to compile it 
manually.  Unfortunately, it didn't succeed for some funny reason. :( 
You can read about my attempt here:
 

  [http://ubuntuforums.org/showthread.php?t=1733816](http://ubuntuforums.org/showthread.php?t=1733816)

---

### Post by snuggerdog on 2011-05-29
> I've got a D-link wireless Usb antenna that 
I wanted to use with an old version of Ubuntu server; of course the module
was not included, so I had to download the driver and try to compile it 
manually.   Well i took a look at your forum post, you're trying to configure a USB antenna so you would be able to use your server as a wireless hub for your other electronic devices whereas i am only trying to install a wireless USB adapter so i can use wireless internet on my server.

I suppose you could be suggesting to try and download the driver for my adapter and attempt to follow the same process as you but it sounds tedious and i attempted before following this site: [http://ubuntuforums.org/showthread.php?t=732827](http://ubuntuforums.org/showthread.php?t=732827) but i could not finish due to it being biased towards those only using Ubuntu desktop. I was also getting errors in the midst of it.

Appreciate the thought though :D

---

### Post by Dry Lips on 2011-05-29
> **snuggerdog said:**
> Well i took a look at your forum post, you're trying to configure a USB antenna so you would be able to use your server as a wireless hub for your other electronic devices whereas i am only trying to install a wireless USB adapter so i can use wireless internet on my server.

Well, I think I was attempting to do exactly the same as you are, getting internet access through my USB dongle. (Sharing that connection over the wired network was a secondary goal.)
 

 I think (please correct me if I'm wrong) that the modules for wireless adapters, generally are left out of the linux-server kernel. Therefore I believe the only way to get support for a wireless adapter is to compile the driver manually. Or alternatively you could perhaps try to install ndiswrapper and use the drivers for windows.
 

 Where were you stuck? If you provide a little more information, perhaps someone will be able to help you out. Did you manage to compile the drivers correctly? I'm not claiming that all this compiling stuff is easy... Expect to use a little time if you attempt to do this. You need to have the correct kernel headers installed to be able to compile drivers. And you also need to find the correct drivers for download.  
 

 Finally I think this thread is in the wrong section. Wireless stuff is best dealt with in the “Networking & Wireless” section... Perhaps a mod will move this thread for you?

---

### Post by snuggerdog on 2011-05-29
well via the link i mentioned in my previous post, i followed step one and that worked fine, but in step two it says that you must type ```
[COLOR=Blue]sudo apt-get -y install build-essential debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg libstdc++6-4.3-doc diff-doc lib64stdc++6-4.3-dbg lib64mudflap0[/COLOR]
```

but when i do that, none of what i am attempting to install is found. Maybe they're outdated? I havn't a clue

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package lib64stdc++6-4.3-dbg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libstdc++6-4.3-dbg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libstdc++6-4.3-doc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package g++-4.3-multilib
E: Couldn't find any package by regex 'g++-4.3-multilib'
E: Unable to locate package gcc-4.3-doc
E: Couldn't find any package by regex 'gcc-4.3-doc'
E: Package 'libstdc++6-4.3-dbg' has no installation candidate
E: Package 'libstdc++6-4.3-doc' has no installation candidate
E: Package 'lib64stdc++6-4.3-dbg' has no installation candidate

```

if i knew how to compile the drivers, i would attempt but i wasn't sure if there was an easier way

So i suppose i did not successfully compile the driver correctly. > Or alternatively you could perhaps try to install ndiswrapper and use the drivers for windows.
 
 
I don't think that ndiswrapper would work for USB devices because when i googled it one person said it was not possible.

---

### Post by Dry Lips on 2011-05-30
First of all, the reason why I'm interested in your case is that you have a similar problem to mine. I wonder if you eventually would run into the same problem as myself since you too run the server version of Ubuntu. So even if you follow my suggestions I don't guarantee that this will work.

Anyway, start by installing the packages you need in order to compile your driver. 

**1. **This gives you a root shell:
```
sudo -i 
```**2. **I'm not sure all these packages are needed, I've seen different suggestions
at different web-pages.
```
apt-get install build-essential checkinstall fakeroot dpkg-dev
```**3. **This gives you the kernel-headers you need:```
apt-get install linux-headers-`uname -r`
```[B]

4.[/B] I think this would be the correct driver for your device, but I suggest  you do a little research on your own to confirm my assertion. You need  to identify the chipset of your wireless antenna, then download the  appropriate driver:
```
wget [http://download.wireless-driver.com/driver/Realtek/RTL8187L/rtl8187L_linux_26.1039.0104.2010.release.tar.gz](http://download.wireless-driver.com/driver/Realtek/RTL8187L/rtl8187L_linux_26.1039.0104.2010.release.tar.gz)
```[B]
5.[/B]Unpack the tarball you downloaded ```
tar -xzvf rtl8187L_linux_26.1039.0104.2010.release.tar.gz
```**6.** Go to the directory where you unpacked the tarball.```
cd rtl8187L_linux_26.1039.0104.2010.release
```**7.** Compile!
```
make clean
make
make install

```**8. **Exit from the root shell.```
exit
```[B]
9.[/B] If you managed to compile the driver correctly,  I would then try to follow the instructions in the readme that comes with the the driver you downloaded, in order to load the correct module.

Good luck!

---

### Post by snuggerdog on 2011-05-30
Well from doing a little research, i've been able to find out that the driver i need i get from [http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2) . Easy fix i just substitute it in from the one you provided before which may work also. Unfortunately i've run into a new problem, i can't connect to us.archive.ubuntu.com on my server any more there fore i can not download the necessary driver. I'm connected via internet currently bridging my connection from my wireless internet from my laptop to my server until i get the wireless adapter up and running. I have no idea what has happened... It seems when a sensible solution may be in your grasps, something has to come and complicate things...:( i'm still able to ping to my router with ease but i can't even run apt-get update anymore.

---

### Post by Dry Lips on 2011-05-31
> **snuggerdog said:**
> Well from doing a little research, i've been able to find out that the driver i need i get from [http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2) . Easy fix i just substitute it in from the one you provided before which may work also. Unfortunately i've run into a new problem, i can't connect to us.archive.ubuntu.com on my server any more there fore i can not download the necessary driver. I'm connected via internet currently bridging my connection from my wireless internet from my laptop to my server until i get the wireless adapter up and running. I have no idea what has happened... It seems when a sensible solution may be in your grasps, something has to come and complicate things...:( i'm still able to ping to my router with ease but i can't even run apt-get update anymore.

How do you share your internet connection?
   I do it like this:
  
Wireless Router -->(via wireless) Desktop computer --->Wired router (lan)--->Server.
 
 I share my internet connection by: 

System>preferences>Network connections>Wired eth0>IPv4 Settings>Method: Shared to other computers.
 
I've never had any trouble with this set-up...

---

### Post by snuggerdog on 2011-05-31
bump
 
Currently at school right now, will respond when i return home but i do not have a wired router only a wireless that provides internet to my laptop that is in my room. From there i plug in via ethernet from my server to my laptop and i bridge my connections. I hadn't had a problem with it until a couple nights ago when it mysteriously stopped working. I will explain in thural detail when i return home though.

---

