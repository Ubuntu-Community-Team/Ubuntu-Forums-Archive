---
title: "How to install ideviceinstaller"
date: 2010-05-03
forum: Tutorials
---

### Post by chaosz911 on 2010-05-03
Hello,

I noticed it should be possible to sync apps with Ubuntu / iPod / iPhone too so went in and looked to install it.
Below is a guide to install ideviceinstaller, hope it works. Any info to make this guide better is more then welcome!
I am by no means an expert, but it worked for me :)

---
**Howto - Iphone App sync**


**Preparation**

```
$ sudo apt-get install libtool automake autoconf git-core swig build-essential python-dev libusbmuxd-dev libglib2.0-dev libgnutls-dev libplist-dev libplist++-dev libplist++1 libzip-dev libclutter-1.0-dev libclutter-gtk-0.10-dev intltool
```

**Get and compile the latest 'libimobiledevice'**

```
$ cd ~/Downloads
$ wget http://www.libimobiledevice.org/downloads/libimobiledevice-1.0.1.tar.bz2
$ tar xvjf libimobiledevice-1.0.1.tar.bz2
$ cd ~/Downloads/libimobiledevice-1.0.1
$ ./configure
$ make
$ sudo make install
```

**Get and compile ideviceinstaller**

```
$ git clone git://git.sukimashita.com/ideviceinstaller.git
$ cd ideviceinstaller/
$ ./autogen.sh
$ ./configure
$ make
$ sudo make install
```

**Get and compile sbmanager**

```
$ git clone git://git.sukimashita.com/sbmanager.git
$ cd sbmanager
$ ./autogen.sh
$ ./configure
$ make
$ sudo make install
```

**How does it work**

* List all apps on your iPhone/iPod:
```
$ ideviceinstaller -l
```
* Archive an app:
```
$ ideviceinstaller -a <app>
```
* Restore an app:
```
$ ideviceinstaller -r <app>
```
* Create a backup:
```
$ idevicebackup backup ~/backup
```
* Restore a backup:
```
$ idevicebackup restore ~/backup
```
* Get info:
```
$ ideviceinfo
```
* Manage your springboard:
```
$ sbmanager
```

**Troubleshooting**

*** Error:** ideviceinstaller: error while loading shared libraries: libimobiledevice.so.1: cannot open shared object file: No such file or directory
**- Fix:**
```
$ sudo ln -s /usr/local/lib/libimobiledevice.so.1.0.1 /usr/lib/libimobiledevice.so.1
```
*** Error:** idevicebackup: /build/buildd/libplist-1.1/src/plist.c:576: plist_get_uint_val: Assertion `length == sizeof(uint64_t)' failed.
**- Fix:** No fix (yet). The error appears on both my iPod Touch and iPhone 3GS on both 32 bit and 64 bit Ubuntu

---

### Post by peshko-lnx on 2010-05-16
Just a quick info. I was able to install everything as per your guide. Thanks a lot!

The binary for apps is ideviceinstaller -l - to list the apps and not ideviceinstall.

One issue I have is that sbmanager runs under root - sudo sbmanager.

Under the local user it throws an exception. I am still trying to figure what is the problem. I am sure it is permission problem, but for sure it is not on the sbmanager.

---

### Post by miguelastico on 2010-05-16
is it normal that I cannot find ifuse-dev???
also, I had to install intltool due to an error like 
```
syntax error near unexpected token `0.35.0'
```

---

### Post by chaosz911 on 2010-05-20
> **peshko-lnx said:**
> Just a quick info. I was able to install everything as per your guide. Thanks a lot!

The binary for apps is ideviceinstaller -l - to list the apps and not ideviceinstall.

One issue I have is that sbmanager runs under root - sudo sbmanager.

Under the local user it throws an exception. I am still trying to figure what is the problem. I am sure it is permission problem, but for sure it is not on the sbmanager.

Changed the binary :)
Glad you liked it, it was my first tutorial.
No idea about sbmanager, except like you mentioned: permissions

---

### Post by chaosz911 on 2010-05-20
> **miguelastico said:**
> is it normal that I cannot find ifuse-dev???
also, I had to install intltool due to an error like 
```
syntax error near unexpected token `0.35.0'
```

I'm pretty sure you do not need ifuse-dev, and I cannot recall finding it either. Either way, ifuse-dev is removed and intltool is added :)
Thanks for the info!

---

### Post by G@B0 on 2010-05-22
> **chaosz911 said:**
> 
**Troubleshooting**

*** Error:** ideviceinstaller: error while loading shared libraries: libimobiledevice.so.1: cannot open shared object file: No such file or directory
**- Fix:**
```
$ sudo ln -s /usr/local/lib/libimobiledevice.so.1.0.0 /usr/lib/libimobiledevice.so.1
```


In my case this doesn't work even changing the code to 1.0.1. I don't know if it's because of a new version (1.0.1) but I can't get SBManager to work, neither ideviceinfo.

Any solution?

---

### Post by chaosz911 on 2010-05-23
> **G@B0 said:**
> In my case this doesn't work even changing the code to 1.0.1. I don't know if it's because of a new version (1.0.1) but I can't get SBManager to work, neither ideviceinfo.

Any solution?

Sorry to hear it didn't work for you. Could you post the error you get?

---

### Post by G@B0 on 2010-05-23
> **chaosz911 said:**
> Sorry to hear it didn't work for you. Could you post the error you get?

Forget it, I ran an apt-get upgrade and now it's working.

Thx

---

### Post by jephrei on 2010-05-24
YOU...my friend...are the bee's knees. thanks chaosz911! i even needed the first fix that you so graciously included.

---

### Post by JohnnyBee on 2010-05-25
Hey guys I've been trying to get these apps working on my laptop, but I come up with an error concerning libclutter-1.0-dev libclutter-gtk-0.10-dev installation packages.
The following packages have unmet dependencies:
  libclutter-1.0-dev: Depends: libgtk2.0-dev but it is not going to be installed
  libclutter-gtk-0.10-dev: Depends: libgtk2.0-dev but it is not going to be installed

Any ideas?

---

### Post by era506 on 2010-05-25
Hi! I really want to try this! Thanks for the guide! Just a question: isn't libimobiledevice already installed with Lucid? Should I uninstall it before trying this guide?

---

### Post by chaosz911 on 2010-05-25
> **era506 said:**
> Hi! I really want to try this! Thanks for the guide! Just a question: isn't libimobiledevice already installed with Lucid? Should I uninstall it before trying this guide?

Hi,

You are correct, it is installed, but not the latest version which is required for this to work. There is no uninstall needed at the same time it cannot hurt either :)

---

### Post by chaosz911 on 2010-05-25
> **JohnnyBee said:**
> Hey guys I've been trying to get these apps working on my laptop, but I come up with an error concerning libclutter-1.0-dev libclutter-gtk-0.10-dev installation packages.
The following packages have unmet dependencies:
  libclutter-1.0-dev: Depends: libgtk2.0-dev but it is not going to be installed
  libclutter-gtk-0.10-dev: Depends: libgtk2.0-dev but it is not going to be installed

Any ideas?

Hi,

Like said, I am no expert and still learning. Nevertheless this might help:

$ sudo apt-get install -f (this fixes dependencies)

You can also try:

$ sudo apt-get update
$ sudo apt-get dist-upgrade

Hope this helps! Let me know :)

---

### Post by JohnnyBee on 2010-05-26
Thanks for your reply. Already try this, but it does not seem to work.

---

### Post by katnenis on 2010-05-27
> **chaosz911 said:**
> Hi,

You are correct, it is installed, but not the latest version which is required for this to work. There is no uninstall needed at the same time it cannot hurt either :)
I tried installing libimobiledevice 1.01 with ur instructions and it seemed to install, but in synaptic it still shows up as 0.97, what am I doing wrong? I am running lucid by the way

---

### Post by G@B0 on 2010-05-27
> **katnenis said:**
> I tried installing libimobiledevice 1.01 with ur instructions and it seemed to install, but in synaptic it still shows up as 0.97, what am I doing wrong? I am running lucid by the way

It will not show up on Synaptic, so no problemo.
I made a tutorial with the updated version of libimobiledevice, in case any one of you want to read it, go [HERE.]("http://120linux.com/sbmanager-ubuntu/")
It's in spanish but it's easy to understand.

---

### Post by katnenis on 2010-05-27
> **G@B0 said:**
> It will not show up on Synaptic, so no problemo.
I made a tutorial with the updated version of libimobiledevice, in case any one of you want to read it, go [HERE.]("http://120linux.com/sbmanager-ubuntu/")
It's in spanish but it's easy to understand.
Thank you, but how can I check the version number of libimobiledevice to make sure I'm running 1.01

---

### Post by chaosz911 on 2010-05-29
Howdy,

The tutorial has been updated (thank you G@b0).
I ran into some problems myself though which I still cannot solve.
ideviceinstaller -l works perfectly it shows all apps on the iPhone (3gs). It is not possible to create a backup however. Below is the output, any ideas?

> idevicebackup backup ~/iPhone/
Backup directory is "~/iPhone/"
Started "com.apple.mobilebackup" service on port 49222.
Reading Info.plist from backup.
Starting backup...
Reading existing Manifest.
Could not read Manifest.plist, switching to full backup mode.
Creating Info.plist for new backup.
Requesting backup from device...
Full backup mode.
Please wait. Device is preparing backup data...
idevicebackup: /build/buildd/libplist-1.1/src/plist.c:576: plist_get_uint_val: Assertion `length == sizeof(uint64_t)' failed.
Aborted

---

### Post by defcloud on 2010-06-27
I followed the steps on this site. i have an ipod touch 2g 8gig, with ios4 istalled. I'm using linux mint 9

when I try to back up the ipod i get this error:
Backup directory is "/home/dc/ipodbackup"
Started "com.apple.mobilebackup" service on port 49171.
Reading Info.plist from backup.
Starting backup...
Reading existing Manifest.
Could not read Manifest.plist, switching to full backup mode.
Creating Info.plist for new backup.
Requesting backup from device...
ERROR: Could not start backup process: device refused to start the backup proces

Is there somthing else I need to install or is this a result of upgrading to ipod's ios4.

I get this error when I try and archive an app:

Archive - Error occured: APIEpicFail

I'm kind of new with linux so I have no idea what I should do. Any help would be great.

I can rearange my ipod apps on sbmanager with no problem.

I don't know if this will help but ideviceinfo gives me this:

ActivationPublicKey: LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JR0pBb0dCQUlpQ1RWOFovNkRCZFNISkxxUGE1NUE1MXpidnZraTZXNlllSDU3TWNtZmdtT2pBMENaQytWY3oKanFoblBueUNDdWNBdDRlS0hYZjlyakhST0IyODRJak9lNldkT0UxV3BCeU4xUm5mQzA2b3FsWVNrSnh1TmEreQpVbVJOQUF1K3FoejFLZFF1b3VVcldlSTRWbWVTRS9CSnh0VUJOdGdGelREZHJVdmY1N25UQWdNQkFBRT0KLS0tLS1FTkQgUlNBIFBVQkxJQyBLRVktLS0tLQo=
ActivationState: Activated
ActivationStateAcknowledged: true
BluetoothAddress: d8:30:62:0f:87:be
BuildVersion: 8A293
CPUArchitecture: armv6
CallsInProgress: false
DeviceCertificate: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUM0VENDQWtxZ0F3SUJBZ0lLQUpPS2dpL3lWejRaRURBTkJna3Foa2lHOXcwQkFRVUZBREJhTVFzd0NRWUQKVlFRR0V3SlZVekVUTUJFR0ExVUVDaE1LUVhCd2JHVWdTVzVqTGpFVk1CTUdBMVVFQ3hNTVFYQndiR1VnYVZCbwpiMjVsTVI4d0hRWURWUVFERXhaQmNIQnNaU0JwVUdodmJtVWdSR1YyYVdObElFTkJNQjRYRFRFd01EWXlOREU0Ck1EWTBObG9YRFRFek1EWXlOREU0TURZME5sb3dnWU14TFRBckJnTlZCQU1USkVSRk5FVXpRa1kzTFRVME1UQXQKTkRrMlJTMDROVEV6TFRoRU9UTTJSamcxTXpReU16RUxNQWtHQTFVRUJoTUNWVk14Q3pBSkJnTlZCQWdUQWtOQgpNUkl3RUFZRFZRUUhFd2xEZFhCbGNuUnBibTh4RXpBUkJnTlZCQW9UQ2tGd2NHeGxJRWx1WXk0eER6QU5CZ05WCkJBc1RCbWxRYUc5dVpUQ0JuekFOQmdrcWhraUc5dzBCQVFFRkFBT0JqUUF3Z1lrQ2dZRUFpSUpOWHhuL29NRjEKSWNrdW85cm5rRG5YTnUrK1NMcGJwaDRmbnN4eVorQ1k2TURRSmtMNVZ6T09xR2MrZklJSzV3QzNoNG9kZC8ydQpNZEU0SGJ6Z2lNNTdwWjA0VFZha0hJM1ZHZDhMVHFpcVZoS1FuRzQxcjdKU1pFMEFDNzZxSFBVcDFDNmk1U3RaCjRqaFdaNUlUOEVuRzFRRTIyQVhOTU4ydFM5L251ZE1DQXdFQUFhT0JnekNCZ0RBZkJnTlZIU01FR0RBV2dCU3kKL2lFalJJYVZhbm5WZ1NhT2N4RFlwMHlPZERBZEJnTlZIUTRFRmdRVW9kMFU4TmIyUENQZEVxai91VDBZM1pvVgpzR0F3REFZRFZSMFRBUUgvQkFJd0FEQU9CZ05WSFE4QkFmOEVCQU1DQmFBd0lBWURWUjBsQVFIL0JCWXdGQVlJCkt3WUJCUVVIQXdFR0NDc0dBUVVGQndNQ01BMEdDU3FHU0liM0RRRUJCUVVBQTRHQkFHT0FFbm4vUW9hNWFWSzUKWmUwejhvendLbEZlQWR3MWtDcHo2elZOMlduUW01d1R5c1cxbXVSbzl2OGFZa29oYWJkeENpcGlUY2dFWnkzUQp6NkZKbUt0cEY4dWJDa1hWZ1R6Qit4NzgxMkl0OHp1d1pmbUMwcGdzbDkrb1dpMy9BT0FrUVBaVmZoQk1yMFQ4ClpSSVBRL3lXc1RodVNMdnpqZUdid3Ric1h3a0IKLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLQo=
DeviceClass: iPod
DeviceColor: iPodShinyMetal
DeviceName: Daniel’s iPod
DevicePublicKey: LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JR0pBb0dCQUtJODdKUDliNWU4RTdTblVod2loSDJhQ2N4clJ4QkwrcUhGL2g0TlczblVZdTlZZWNzdDRwcWoKcDF5QW5ablpYQTRINlI0QkljWGJmUDFXTnozazFvcGEvb1NrMVB2TDZMWmVJRTBlWExNcFlNVTlzdmlUMmVzdAozdmo0SEFDZWRLUHk3RWp0Z0JLalQxaUJENGl1UGdJZ2syRkthWnBiZmZkYjJhNyt5cmtsQWdNQkFBRT0KLS0tLS1FTkQgUlNBIFBVQkxJQyBLRVktLS0tLQo=
DieID: 1338124057264
FirmwareVersion: iBoot-889.24
HardwareModel: N72AP
HostAttached: true
MLBSerialNumber: 9C020324Y8UFA
MobileSubscriberCountryCode: 
MobileSubscriberNetworkCode: 
ModelNumber: MC086
PartitionType: GUID_partition_scheme
PasswordProtected: false
ProductType: iPod2,1
ProductVersion: 4.0
ProductionSOC: true
ProtocolVersion: 2
RegionInfo: LL/A
SBLockdownEverRegisteredKey: false
SDIOManufacturerTuple: 
 IOSDIOManufacturerID: 19792
 IOSDIOProductID: 19784
SIMGID1: AAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAQAAAAAAAAA=
SIMGID2: AAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAQAAAAAAAAA=
SIMStatus: kCTSIMSupportSIMStatusReady
SerialNumber: 1C02086075J
SoftwareBehavior: EQAAAAAAAAAAAAAAAAAAAA==
SoftwareBundleVersion: 2
SupportedDeviceFamilies[1]: 
 0: 1
TimeIntervalSince1970: 1277755481
TimeZone: US/Pacific
TimeZoneOffsetFromUTC: -25200.000000
TrustedHostAttached: true
UniqueChipID: 1199739981199
UniqueDeviceID: 05b4888873aa0df176bd8d7746f12b4cb3117d99
Uses24HourClock: false
WiFiAddress: d8:30:62:01:85:26
iTunesHasConnected: true

---

### Post by herchu on 2010-07-03
Hello,
I am trying to compile ideviceinstaller, but I have a problem in the dependency on libimobiledevice.

I am using pmcenery PPA: [https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=lucid](https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=lucid) ,
so I have now installed libimobiledevice1, v 1.0.1:
```

$ apt-cache showpkg libimobiledevice1
Package: libimobiledevice1
Versions: 
1.0.1-1ubuntu1~ppa1 (/var/lib/apt/lists/ppa.launchpad.net_pmcenery_ppa_ubuntu_dists_lucid_main_binary-i386_Packages) (/var/lib/dpkg/status)

```
however when I run autogen.sh on ideviceinstaller:
```

$ ./autogen.sh 
(...)
checking for libimobiledevice... configure: error: Package requirements (libimobiledevice-1.0 >= 0.9.7) were not met:

No package 'libimobiledevice-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```
It does not find my library. I believe it has to do with the naming (libimobiledevice1 vs. libimobiledevice, v1.0), but I am not sure.

I want to keep using libimobiledevice from the PPA, not install it myself as suggested in this tutorial. Is there any workaround to have the ./configure step find my library version?

Any help greatly appreciated!

---

### Post by csoler on 2010-07-08
Hi,

I get this error. I don't know what to do:

> ./src/ideviceinstaller -l
Could not start com.apple.mobile.installation_proxy!


Any idea??

Thanks!

---

### Post by csoler on 2010-07-08
.

---

### Post by oneadvent on 2010-07-08
I'm sorry i am getting:

```
config.status: error: cannot find input file: `Makefile.in'

```

---

### Post by antrunner85 on 2010-07-10
Hey has anyone gotten this error and knows how to solve it? I been doing trying to get this installed for a couple of days already and I always get stuck here

Thanks



```

Making all in data
make[2]: Entering directory `/home/yo/sbmanager/data'
LC_ALL=C /usr/bin/intltool-merge -d -u -c ../po/.intltool-merge-cache ../po sbmanager.desktop.in sbmanager.desktop
Generating and caching the translation database
Merging translations into sbmanager.desktop.
make[2]: Leaving directory `/home/yo/sbmanager/data'
Making all in src
make[2]: Entering directory `/home/yo/sbmanager/src'
  CC     libsbmanager_la-device.lo
cc1: warnings being treated as errors
device.c: In function ‘device_sbs_save_wallpaper’:
device.c:195: error: implicit declaration of function ‘sbservices_get_home_screen_wallpaper_pngdata’
make[2]: *** [libsbmanager_la-device.lo] Error 1
make[2]: Leaving directory `/home/yo/sbmanager/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/yo/sbmanager'
make: *** [all] Error 2

```

---

### Post by uMany on 2010-07-11
Hi,
Antrunner85,

I'm getting the same error message with the device.c file into the src folder.

Did you solve it?
Because I don't yet.

Thanks in advance.

---

### Post by lukasw on 2010-07-11
I got the same error during the make process. So I used [an older version]("http://cgit.sukimashita.com/sbmanager.git/commit/?id=931bdf26da0e5a116a881f429dfdb1e8eafbba3d") of sbmanager.
Now everything works fine :D

Hope this helps

---

### Post by antrunner85 on 2010-07-11
uMany,

I did try to modify device.c according to what is posted on [http://cgit.sukimashita.com/sbmanager.git/](http://cgit.sukimashita.com/sbmanager.git/) but it was pretty worthless.

I did what lukasw mentioned, install an older version, and it installed it. It's not working properly though. I have the iphone 4 and the icons look way too big, and it does not move my apps around on my iphone, just on the computer. Oh also as I expected, it shows no folders or backgrounds.

Please let me know if anyone else knows about this error or how to fix it.

---

### Post by lukasw on 2010-07-11
herchu: You also need to install *libimobiledevice-dev*.

antrunner85: [This]("http://cgit.sukimashita.com/sbmanager.git/commit/?id=d16ba43dcea96e4a27be04c0532d712c659a8089") version should fix the problem with the icon  size.
But the wallpaper still doesn't show, I guess.

EDIT: I submitted a bug report at the libiphone bug tracker page. The bug is fixed now!

---

### Post by yerfinojul on 2010-07-12
> **herchu said:**
> Hello,
I am trying to compile ideviceinstaller, but I have a problem in the dependency on libimobiledevice.

I am using pmcenery PPA: [https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=lucid](https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=lucid) ,
so I have now installed libimobiledevice1, v 1.0.1:
```

$ apt-cache showpkg libimobiledevice1
Package: libimobiledevice1
Versions: 
1.0.1-1ubuntu1~ppa1 (/var/lib/apt/lists/ppa.launchpad.net_pmcenery_ppa_ubuntu_dists_lucid_main_binary-i386_Packages) (/var/lib/dpkg/status)

```
however when I run autogen.sh on ideviceinstaller:
```

$ ./autogen.sh 
(...)
checking for libimobiledevice... configure: error: Package requirements (libimobiledevice-1.0 >= 0.9.7) were not met:

No package 'libimobiledevice-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```
It does not find my library. I believe it has to do with the naming (libimobiledevice1 vs. libimobiledevice, v1.0), but I am not sure.

I want to keep using libimobiledevice from the PPA, not install it myself as suggested in this tutorial. Is there any workaround to have the ./configure step find my library version?

Any help greatly appreciated!

Try using "sudo apt-get install libimobiledevice-dev" first

---

### Post by peshko-lnx on 2010-07-24
I just tried this on iphone 4. I created a couple of folders and the folders don't show up in sbmanager. All single icons that are not part of any folder show up. Anyone else with the same issue?

---

### Post by oneadvent on 2010-08-02
I am still getting errors with the old version:
```
config.status: error: cannot find input file: `src/Makefile.in'

```

I tried a few things, but I cant seem to get a Make file.

Can anyone shed some light?

---

### Post by oneadvent on 2010-08-02
Gave up, found a deb:

[http://sourceforge.net/projects/ihack/files/sbmanager/UbuntuLucid/sbmanager_1.0.1-1_i386.deb/download](http://sourceforge.net/projects/ihack/files/sbmanager/UbuntuLucid/sbmanager_1.0.1-1_i386.deb/download)

---

### Post by cyberey66 on 2010-08-07
> **peshko-lnx said:**
> I just tried this on iphone 4. I created a couple of folders and the folders don't show up in sbmanager. All single icons that are not part of any folder show up. Anyone else with the same issue?

Yes, I have the same issue.  Do not try and use sbmanager if you have folders, it will remove them and scatter the items.

---

### Post by zorgh on 2010-09-12
> **oneadvent said:**
> I'm sorry i am getting:

```
config.status: error: cannot find input file: `Makefile.in'

```

apt-get install libtool

---

### Post by Didile on 2010-09-14
I am trying to compile sbmanager but I get an error when I try to "make".

libtool: Version mismatch error.  This is libtool 2.2.6, but the
libtool: definition of this LT_INIT comes from libtool 2.2.6b.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.6
libtool: and run autoconf again.
make[2]: *** [libsbmanager_la-device.lo] Error 63
make[2]: Leaving directory `/home/tokamak/Downloads/libimobiledevice-1.0.1/sbmanager/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tokamak/Downloads/libimobiledevice-1.0.1/sbmanager'
make: *** [all] Error 2


P.S: I was a bit hasty, I compiled libtool 2.2.6b and everything works!!!!!!!!!!!


Any idea?

---

### Post by Squirrel King on 2010-10-05
Im having troubles getting my iphone to backup using the tool....this is what i did, and got for output:
```

jester@parasite:~/backup-phone$ idevicebackup backup ~/backup-phone
Backup directory is "/home/jester/backup-phone"
Started "com.apple.mobilebackup" service on port 49914.
Reading Info.plist from backup.
Starting backup...
Reading existing Manifest.
Could not read Manifest.plist, switching to full backup mode.
Creating Info.plist for new backup.
Requesting backup from device...
ERROR: Could not start backup process: device refused to start the backup process.
jester@parasite:~/backup-phone$ 

```Ideas on how to get this to work would be greatly appreciated...
thanks

---

### Post by eMxyzptlk on 2010-11-15
> **Squirrel King said:**
> Im having troubles getting my iphone to backup using the tool....this is what i did, and got for output:
```

jester@parasite:~/backup-phone$ idevicebackup backup ~/backup-phone
Backup directory is "/home/jester/backup-phone"
Started "com.apple.mobilebackup" service on port 49914.
Reading Info.plist from backup.
Starting backup...
Reading existing Manifest.
Could not read Manifest.plist, switching to full backup mode.
Creating Info.plist for new backup.
Requesting backup from device...
ERROR: Could not start backup process: device refused to start the backup process.
jester@parasite:~/backup-phone$ 

```Ideas on how to get this to work would be greatly appreciated...
thanks
I'm having the same problem as you, I opened a ticket upstream [http://libiphone.lighthouseapp.com/projects/27916-libiphone/tickets/180-cant-backup-iphone4](http://libiphone.lighthouseapp.com/projects/27916-libiphone/tickets/180-cant-backup-iphone4)

Any help appreciated...

---

### Post by JacquesKik on 2011-01-09
Same problem here...
no backup and no archiving of apps

I get the following when trying to archive an app:
Archive - Error occured: APIInternalError

Thank you!

---

### Post by yule0 on 2011-01-10
When I launch ```
ideviceinstaller -l
``` I get ```
ERROR: instproxy_browse returned -3
```

Does anyone know what this means?

---

### Post by yule0 on 2011-01-10
Just found it out myself: you have to unmount the iOS device from ubuntu before you launch ideviceinstaller... obviously.

---

### Post by druitex on 2011-03-30
Hi, I want compiler **ideviceinstaller **in maverick** but **when I type make , I olny obtain the next answer, Somebody have any idea?

(CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/bash /home/harold/Descargas/libimobiledevice-1.0.1/missing --run autoheader)
rm -f stamp-h1
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: se ingresa al directorio «/home/harold/Descargas/libimobiledevice-1.0.1/ideviceinstaller»
Making all in src
make[2]: se ingresa al directorio «/home/harold/Descargas/libimobiledevice-1.0.1/ideviceinstaller/src»
  CC     ideviceinstaller-ideviceinstaller.o
cc1: warnings being treated as errors
ideviceinstaller.c: In function ‘zip_f_get_contents’:
ideviceinstaller.c:166: error: format ‘%lld’ expects type ‘long long int’, but argument 3 has type ‘long unsigned int’
make[2]: *** [ideviceinstaller-ideviceinstaller.o] Error 1
make[2]: se sale del directorio «/home/harold/Descargas/libimobiledevice-1.0.1/ideviceinstaller/src»
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio «/home/harold/Descargas/libimobiledevice-1.0.1/ideviceinstaller»
make: *** [all] Error 2


What  can I do?

---

### Post by WeeB2 on 2011-04-02
I got it to compile with this simplistic change to line 166.

vi +166 src/ideviceinstaller.c

and then add the extra cast to (long long int) as below.


                fprintf(stderr, "ERROR: zip_fread %lld bytes from '%s'\n", (long long int)(uint64_t)zs.size, filename);

---

### Post by zosky on 2012-04-30
> **WeeB2 said:**
> I got it to compile with this simplistic change to line 166 [...] and then add the extra cast to (long long int) as below.


this didn't do anything for me, still error

[LIST]
[*]libplist-1.8
[*]libimobiledevice-1.1.2
[*]ideviceinstaller-1.0.1 
[/LIST]

is it because libimobiledevice didn't install properly ?

```
$ ./configure && make && sudo make install
$ ./tools/ideviceinfo
# ... it shows iphone4 info #

$ ideviceinfo
ideviceinfo: error while loading shared libraries: libimobiledevice.so.3: cannot open shared object file: No such file or directory
```

the first post says to check links...
```
$ ls -lah /usr/local/lib/libimobiledevice.so*
lrwxrwxrwx 1 root root   25 2012-04-30 01:36 /usr/local/lib/libimobiledevice.so -> libimobiledevice.so.3.0.0
lrwxrwxrwx 1 root root   25 2012-04-30 00:51 /usr/local/lib/libimobiledevice.so.1 -> libimobiledevice.so.1.0.5
-rwxr-xr-x 1 root root 296K 2012-04-30 00:51 /usr/local/lib/libimobiledevice.so.1.0.5
lrwxrwxrwx 1 root root   25 2012-04-30 01:36 /usr/local/lib/libimobiledevice.so.3 -> libimobiledevice.so.3.0.0
-rwxr-xr-x 1 root root 642K 2012-04-30 01:36 /usr/local/lib/libimobiledevice.so.3.0.0

```

help please
fixing library path for [/usr/local/bin/]idevice*
and compiling ideviceinstaller

---

### Post by ravi6456 on 2012-05-21
I am also facing a similar problem. Any inputs or work around for the mentioned problem ??

checking for libgtk... yes
checking for libcluttergtk... no
configure: error: Package requirements (clutter-gtk-1.0 >= 1.0) were not met:

No package 'clutter-gtk-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libcluttergtk_CFLAGS
and libcluttergtk_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

