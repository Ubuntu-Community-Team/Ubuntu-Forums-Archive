---
title: "Daily live  installed and running great on Acer 1410"
date: 2012-06-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-06-11
Wireless rock solid. Everything works so far.

Apart from the usual synaptic, myunity and SC that wont install stuff.

gksu synaptic works fine.

> MUnity
Ubuntu 12.10
Sorry, Ubuntu release not supported.
From term > WARNING: gMainWindow::setToolBox not yet implemented

---

### Post by wilee-nilee on 2012-06-11
Same basic experience here on a older toshiba a20 been running the development since about two weeks past the last release.

Franq N Steen

---

### Post by ventrical on 2012-06-11
Just did an install of A1 (64bit) on Acer <extensa4420> and it finally recognizes the ATI RadeonXpress1250 adapter card. That means I finally have Unity 3D where Precise would not install the ATI driver using 64bit.iso.

  Also .. cannot download synaptic from terminal:

0 upgraded, 7 newly installed, 0 to remove and 173 not upgraded.
Need to get 2,686 kB/3,584 kB of archives.
After this operation, 13.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main sgml-data all 2.0.6 [271 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main sgml-data all 2.0.6 [271 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/universe synaptic amd64 0.75.11 [2,416 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/universe synaptic amd64 0.75.11 [2,416 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/universe synaptic amd64 0.75.11 [2,416 kB]
Fetched 1,294 kB in 6s (201 kB/s)                                              
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sgml-data/sgml-data_2.0.6_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sgml-data/sgml-data_2.0.6_all.deb)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/synaptic/synaptic_0.75.11_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/synaptic/synaptic_0.75.11_amd64.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ventrical@ubuntu:~$

---

### Post by ventrical on 2012-06-11
Fix:

sudo apt-get update --fix-missing

sudo apt-get install synaptic

---

### Post by ventrical on 2012-06-11
Definitely cannot download ccsm with synaptic.
edit: Whoops .. sorry. off topic.:)

---

### Post by wilee-nilee on 2012-06-11
> **ventrical said:**
> Definitely cannot download ccsm with synaptic.
edit: Whoops .. sorry. off topic.:)

Installed fine here, it is not ccsm in synaptic, it is compizconfig settings manager

Maybe it is in the universe or multiverse repo not sure check your sources.list

Using acronyms makes things more confusing by the way, then we have to ask did you search with the correct words.

---

### Post by balloons on 2012-06-11
> **philinux said:**
> Wireless rock solid. Everything works so far.

Apart from the usual synaptic, myunity and SC that wont install stuff.

gksu synaptic works fine.


From term > WARNING: gMainWindow::setToolBox not yet implemented

I'm going to sound like a broken record. Please forgive me! Philinux, can you add your success result here?

[http://iso.qa.ubuntu.com/qatracker/milestones/219/builds](http://iso.qa.ubuntu.com/qatracker/milestones/219/builds)

Glad to hear things are running smooth! BTW, it's odd myunity doesn't have a force switch to let you mess with things anyway. It's not like you couldn't fix it if something failed.

---

### Post by ventrical on 2012-06-11
> **wilee-nilee said:**
> Installed fine here, it is not ccsm in synaptic, it is compizconfig settings manager

Maybe it is in the universe or multiverse repo not sure check your sources.list

Using acronyms makes things more confusing by the way, then we have to ask did you search with the correct words.

Yes I did.

ccsm is not an acronym of my own making. It is the standard used for testing.

---

### Post by philinux on 2012-06-12
> **guitara said:**
> I'm going to sound like a broken record. Please forgive me! Philinux, can you add your success result here?

[http://iso.qa.ubuntu.com/qatracker/milestones/219/builds](http://iso.qa.ubuntu.com/qatracker/milestones/219/builds)



Done.

Also myunity bug report updated. [https://bugs.launchpad.net/myunity/+bug/1009590](https://bugs.launchpad.net/myunity/+bug/1009590)

---

### Post by kevpan815 on 2012-06-19
Yeah, X86 Daily-Live runs nice on my 2005 Dell Dimension 8400 Desktop Computer as well. Now that I know how to use ZSync, Updating is easy!

---

### Post by jerrylamos on 2012-06-19
> **philinux said:**
> Wireless rock solid. Everything works so far.Not so fine here!  Once wireless is up (!) runs fine on Acer Aspire 1 with Intel Corporation Centrino Wireless-N 1000.  

Every time I power on, network-manager disconnects from WPA network.  Why?  Enable wireless is checked, and network-manager has the password etc.

Then the network-manager applet does not display the "connect to hidden wireless" choice until I select the applet again, and again.

Then the choices on "connect to hidden wireless" choices are greyed out, mouse doesn't activate anything, nor arrow keys, nor tab, etc.

Try and try again, finally the selections will work, it already has all the information network name, password, etc. Since it already had all the info, why didn't it connect??  

Still just sits there.  Finally after a long time connects.

I don't know what "Enable wireless" means, it is checked when I boot, but it does not enable wireless.

That's with 3.4.0-5.  I have a notebook T40 mostly upgraded to quantal except kernel is 3.2.0-24.  network-manager menus appear on first selection (!) all the choices work (!) remembering the right selections (!) then connects right way (!).

Tried writing a bug #1015096.

Jerry

---

### Post by jerrylamos on 2012-06-19
> **philinux said:**
> Wireless rock solid. Everything works so far.

Much thrash getting wireless going here on Acer Aspire 5253 wide screen notebook Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

Select edit connections ... wireless security and the selection box says:
None
and refuses to allow selecting WPA.  Mouse doesn't work.  Down arrow doesn't work.  Thrash thrash.  (Could be it is waiting for my linux password but doesn't ever ask for it).

Try and try.  Finally it is at least polling. 

Some time later it asks for WPA password, then after some time finally connects.  Phew.

Ugh.  I'd re-boot to see if network-manager remembers anything, but have lost a lot of time already. Why doesn't "Enable Wireless" enable wireless?  Why won't edit "connect to hidden wireless network" enable editing?

Time for daily update and see what goes.  This external monitor working fine after tricky bug #1007588 fixed.

Jerry

---

### Post by philinux on 2012-06-19
Ah the 1410 has this.

```
-network
                description: Wireless interface
                product: Centrino Wireless-N 1000
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0

```

One of many reasons I got this netbook.

---

### Post by jerrylamos on 2012-06-19
Phillinux, are you using WPA password security with your wireless?  My neighbor(s) are a couple hundred feet from here and I can see their network names, so I turned on WPA security on my network.  

My son-in-law has several neighbors so his wireless network only permits certain hardware addresses. 

Jerry

---

### Post by cariboo on 2012-06-19
> **jerrylamos said:**
> Phillinux, are you using WPA password security with your wireless?  My neighbor(s) are a couple hundred feet from here and I can see their network names, so I turned on WPA security on my network.  

My son-in-law has several neighbors so his wireless network only permits certain hardware addresses. 

Jerry

Restricting hardware addresses, is just like leaving the system wide open, I'd suggest you tell him to setup a minimum of WPA, if not WPA2. Utilities for changing mac addresses are freely available for Mac, Windows and Linux.

As far as seeing your neighbours access points, you'll see them even if you have encryption enabled. Network manager should show you whether the access point is open, or locked.

---

### Post by philinux on 2012-06-20
> **jerrylamos said:**
> Phillinux, are you using WPA password security with your wireless?  
Jerry

Yes.

---

### Post by jerrylamos on 2012-06-20
Today's 20 June update same wireless problem.  Intel Corporation Centrino Wireless-N 1000.

1.  Does not connect to wireless WPA on boot.

2. Select "Hidden Wireless Network" choices unresponsive, all greyed out.
 
3. Exactly as if it is waiting for "sudo"

4.  Do something else on terminal that requires "sudo", example "sudo aptitude update".

5. Then the "Hidden Wireless Network" wakes up, after a couple tries, connects.

How do I start the network-manager "Hidden Wireless Network" with the "sudo" command instead of a mouse selection?

Thanks, Jerry

---

### Post by philinux on 2012-06-20
> **jerrylamos said:**
> Today's 20 June update same wireless problem.  Intel Corporation Centrino Wireless-N 1000.

1.  Does not connect to wireless WPA on boot.

2. Select "Hidden Wireless Network" choices unresponsive, all greyed out.
 
3. Exactly as if it is waiting for "sudo"

4.  Do something else on terminal that requires "sudo", example "sudo aptitude update".

5. Then the "Hidden Wireless Network" wakes up, after a couple tries, connects.

How do I start the network-manager "Hidden Wireless Network" with the "sudo" command instead of a mouse selection?

Thanks, Jerry

In this situation I would delete all connections reboot and let it search for wireless connections then set up the one that's yours.

---

### Post by kevpan815 on 2012-06-20
> **jerrylamos said:**
> Not so fine here!  Once wireless is up (!) runs fine on Acer Aspire 1 with Intel Corporation Centrino Wireless-N 1000.  

Every time I power on, network-manager disconnects from WPA network.  Why?  Enable wireless is checked, and network-manager has the password etc.

Then the network-manager applet does not display the "connect to hidden wireless" choice until I select the applet again, and again.

Then the choices on "connect to hidden wireless" choices are greyed out, mouse doesn't activate anything, nor arrow keys, nor tab, etc.

Try and try again, finally the selections will work, it already has all the information network name, password, etc. Since it already had all the info, why didn't it connect??  

Still just sits there.  Finally after a long time connects.

I don't know what "Enable wireless" means, it is checked when I boot, but it does not enable wireless.

That's with 3.4.0-5.  I have a notebook T40 mostly upgraded to quantal except kernel is 3.2.0-24.  network-manager menus appear on first selection (!) all the choices work (!) remembering the right selections (!) then connects right way (!).

Tried writing a bug #1015096.

Jerry

Wireless is working fine here when using my Apple IPhone 4S as a Personal Hotspot. By the way, did you see my comments about how I Reproduced the ATI Graphics Problems during install on my other Dell Desktop (ATI Radeon 3200 HD Video Card with HDMI)?

---

### Post by jerrylamos on 2012-07-06
> **philinux said:**
> Ah the 1410 has this.

```
-network
                description: Wireless interface
                product: Centrino Wireless-N 1000
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0

```

One of many reasons I got this netbook.
Philinux, I'm having fits connecting wireless WPA security with my

Centrino Wireless-N 1000

Ubuntu bug #1019083, upstream bug #44291.

Broadcom on my widescreen notebook not perfect but much much faster response to network settings.

What sort of internet connection do you use with the Centrino?

Thanks, Jerry

---

