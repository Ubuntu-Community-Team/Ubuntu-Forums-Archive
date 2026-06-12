---
title: "wireless broken (no light) after upgrade"
date: 2010-09-28
forum: System76 Support
---

### Post by missLiz on 2010-09-28
Hello.

We upgraded from 9.04 to 9.1 to 10.04.

We have a starling netbook.

We were not lucky, and the wireless did not work out of the box.

We installed the driver with dpkg because the gui seemed not to work.

Then we ran the driver from the command line, and the exception causing the gui to hang became visible.

The message is below.

It looked like it started with a missing grub config file, but i am not sure. I ran apt-get install grub, but it just says grub is installed.

here is the error.

liz@system76-netbook:~$ system76-driver
--2010-09-27 21:18:18-- [http://www.planet76.com/sources.list.d/system76.list](http://www.planet76.com/sources.list.d/system76.list)
Resolving [www.planet76.com]("http://www.planet76.com/")... 64.13.254.166
Connecting to [www.planet76.com|64.13.254.166|:80](www.planet76.com|64.13.254.166|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 145 [text/plain]
Saving to: `/etc/apt/sources.list.d/system76.list'

0K 100% 3.02M=0s

2010-09-27 21:18:19 (3.02 MB/s) - `/etc/apt/sources.list.d/system76.list' saved [145/145]

OK
Hit [http://planet76.com]("http://planet76.com/") ./ Release.gpg
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid Release.gpg 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates Release.gpg 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://planet76.com/repositories/](http://planet76.com/repositories/) ./ Translation-en_US
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid Release 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates Release
Hit [http://planet76.com]("http://planet76.com/") ./ Release 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security Release 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/main Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/restricted Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/main Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/restricted Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/universe Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/universe Sources
Ign [http://planet76.com]("http://planet76.com/") ./ Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/multiverse Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/multiverse Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/main Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/main Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/restricted Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/universe Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/universe Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/multiverse Packages
Ign [http://planet76.com]("http://planet76.com/") ./ Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/main Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/restricted Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/main Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/restricted Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/universe Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/universe Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/multiverse Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-security/multiverse Sources
Hit [http://planet76.com]("http://planet76.com/") ./ Packages 
Reading package lists... Done
Reading package lists... Done
Building dependency tree 
Reading state information... Done
system76-driver is already the newest version.
The following packages were automatically installed and are no longer required:
sdparm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
options snd-hda-intel model=acer-aspire
cp: cannot stat `/etc/default/grub': No such file or directory
Exception in thread Thread-2:
Traceback (most recent call last):
File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
self.run()
File "/opt/system76/system76-driver/src/restore.py", line 120, in run
driverscontrol.installDrivers()
File "/opt/system76/system76-driver/src/driverscontrol.py", line 1074, in installDrivers
acpi.star1()
File "/opt/system76/system76-driver/src/acpi.py", line 137, in star1
for line in grub_menu:
File "/usr/lib/python2.6/fileinput.py", line 253, in next
line = self.readline()
File "/usr/lib/python2.6/fileinput.py", line 322, in readline
os.rename(self._filename, self._backupfilename)
OSError: [Errno 2] No such file or directory



thanks for the help. I miss my netbook.

---

### Post by isantop on 2010-09-28
Hi.

The first thing to try to get the wireless working is to try turning it on, as it may have been turned off during the upgrade. There should be a toggle switch on the front, right edge of the computer. Slide it once to the right, then let it go and reboot.

---

### Post by missLiz on 2010-09-28
Yup, I had already done that with no success, and after trying it again just now, same result.

I also tried the fn-F2 key, and no success.

I looked in the hardware drivers as well, and it tells me "there are no proprietary drivers in use on the system."

That makes me think the failed system76 driver install might be the issue.

peace
Liz

---

### Post by thomasaaron on 2010-09-28
Please try running this command from a terminal (with a wired internet connection)....

sudo apt-get install grub-pc

If it offers you any options, choose the default.

Then reboot your computer and try to run the System76 driver again.

---

### Post by missLiz on 2010-09-28
WooHoo.  That fixed it.  

installed grub, as suggested
ran system76 driver and ran install
noted arrival of wireless driver
ran restore
did the button thing with the wifi
rebooted, and all is well.

many thanks

---

