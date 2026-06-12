---
title: "star1 ubuntu 10.04.1 TLS &amp; system76 driver"
date: 2010-12-07
forum: System76 Support
---

### Post by jimmie-watters on 2010-12-07
I have a Star1 system76 netbook. it was running Ubuntu 9.04 and i started getting messages that this version was no longer supported. I upgraded to 9.10 then to 10.04.1 TLS but can't seam to get the system76 drive to install which is required to get my wireless working. Can anyone point me in the right direction to get the system76 drive to run successfully?

Thanks for you help

Jim

---

### Post by isantop on 2010-12-07
Double upgrades, particularly from 9.04 and from 9.10, typically cause issues. I think you may want try a fresh installation. 

If you can't do that, I may be able to help you fix it, but keep in mind a fresh install may be faster. I'll need to know what errors prevented you from installing the driver.

---

### Post by jimmie-watters on 2010-12-07
Thank you for the quick reply. Both upgrades went well and the netbook seams to functioning without any issues. I know that one of the drivers loaded by running the System76 driver is for the wireless nic. There was some challenges with the Star1 and wireless connectivity. When I try to install or restore the System76 drive through the GUI under System. I don't get an error it just runs indefinitely without installing or restoring the driver. I though it might not have the System76 repository but i thought that is what the restore accomplishes. If there is a manual way to do this and you can point to a link with instructions that would be excellent. 

Thanks again for your help.

Jim

---

### Post by isantop on 2010-12-08
Please open a Terminal and run it from there:
```
system76-driver
```
Then, try the restore again and send me anything that comes up in the terminal. I'll have a look and see what's going on.

---

### Post by jimmie-watters on 2010-12-08
i had found this link 

[http://knowledge76.com/index.php/LucidUpgrade#Upgrade_your_System76_driver](http://knowledge76.com/index.php/LucidUpgrade#Upgrade_your_System76_driver)

and followed the instruction to no avail. The following command seamed to run successfully:

```
sudo dpkg -i system76-driver-2.5.9.deb

```But neither the restore or install from the GUI worked.

I just tried to run it from the command line as per you instructions and here is the output:

```
sudo system76-driver

Traceback (most recent call last):
  File "/usr/bin/system76-driver", line 50, in <module>
    main()
  File "/usr/bin/system76-driver", line 44, in main
    os.environ['GDMSESSION'] == 'default'
  File "/usr/lib/python2.6/UserDict.py", line 22, in __getitem__
    raise KeyError(key)
KeyError: 'GDMSESSION
```'


Thanks again

Jim

---

### Post by strk on 2010-12-09
I've a darter ultra running Ubuntu 10.04 too
and confirm the problem.

Just upgraded system76-driver (old one told me only versions of Ubuntu from 6.06 and 8.04 were supported).

Now have version 2.5.9 of the driver, but running it gives:

Traceback (most recent call last):
  File "/usr/bin/system76-driver", line 50, in <module>
    main()
  File "/usr/bin/system76-driver", line 44, in main
    os.environ['GDMSESSION'] == 'default'
  File "/usr/lib/python2.6/UserDict.py", line 22, in __getitem__
    raise KeyError(key)
KeyError: 'GDMSESSION'

---

### Post by strk on 2010-12-09
FYI: started from the menu works

---

### Post by jimmie-watters on 2010-12-17
Thanks for your replies. I am still not having any luck getting the System76 driver to load either from the command line or the GUI. I am not sure what I can try next any suggestions would be great.

Thanks again for the help.

Jim

---

### Post by smulloni on 2010-12-21
I have the same problem -- just upgraded a star1 to lucid (from jaunty) and the system76 driver hangs.  Starting it from the command line actually works fine without sudo, incidentally.  But the script outputs very little debug information before it hangs; just "options snd-hda-intel model=acer-aspire".

---

### Post by isantop on 2010-12-22
I think you have a different issue. Did you upgrade directly to Lucid? From Jaunty to Karmic, then Karmic to Lucid? Or did you do a fresh install?

---

### Post by smulloni on 2010-12-22
> **isantop said:**
> I think you have a different issue. Did you upgrade directly to Lucid? From Jaunty to Karmic, then Karmic to Lucid? Or did you do a fresh install?

I upgraded from Jaunty to Karmic and then Karmic to Lucid, which I had done on another starling a few months ago.

---

### Post by isantop on 2010-12-22
I think that somewhere along the line, you may have hit an upgrade corruption, as it was very common on both of those upgrade cycles. What exactly are you seeing as output in the terminal, if you run:
```
system76-driver
```

---

### Post by smulloni on 2010-12-22
> **isantop said:**
> I think that somewhere along the line, you may have hit an upgrade corruption, as it was very common on both of those upgrade cycles. What exactly are you seeing as output in the terminal, if you run:
```
system76-driver
```

It outputs only "options snd-hda-intel model=acer-aspire"; nothing else.

---

### Post by jimmie-watters on 2010-12-23
Here is the output if i run system76-driver from the command line and then select restore

```
system76-driver
/opt/system76/system76-driver/src/System76Driver.py:255: GtkWarning: gtk_widget_is_ancestor: assertion `ancestor != NULL' failed
  gtk.main()
--2010-12-23 09:26:37--  http://www.planet76.com/sources.list.d/system76.list
Resolving www.planet76.com... 64.13.254.166
Connecting to www.planet76.com|64.13.254.166|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 145 [text/plain]
Saving to: `/etc/apt/sources.list.d/system76.list'

     0K                                                       100% 3.74M=0s

2010-12-23 09:26:38 (3.74 MB/s) - `/etc/apt/sources.list.d/system76.list' saved [145/145]

OK
Get:1 http://security.ubuntu.com lucid-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US  
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://planet76.com ./ Release.gpg                               
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:2 http://security.ubuntu.com lucid-security Release [38.5kB]      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                         
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                       
Get:3 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]                               
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                              
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                              
Get:4 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]                                 
Ign http://planet76.com/repositories/ ./ Translation-en_US                          
Hit http://planet76.com ./ Release                                                           
Get:5 http://security.ubuntu.com lucid-security/main Packages [114kB]                        
Hit http://us.archive.ubuntu.com lucid/main Packages                                               
Hit http://us.archive.ubuntu.com lucid/restricted Packages                                         
Hit http://us.archive.ubuntu.com lucid/main Sources                                                
Hit http://us.archive.ubuntu.com lucid/restricted Sources                                          
Hit http://us.archive.ubuntu.com lucid/universe Packages                                           
Hit http://us.archive.ubuntu.com lucid/universe Sources                                             
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                                          
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                                           
Get:6 http://us.archive.ubuntu.com lucid-updates/main Packages [375kB]       
Ign http://planet76.com ./ Packages                                                 
Ign http://planet76.com ./ Packages                                                                
Get:7 http://security.ubuntu.com lucid-security/restricted Packages [14B]                          
Get:8 http://security.ubuntu.com lucid-security/main Sources [38.2kB]                                                       
Hit http://planet76.com ./ Packages                                                                                         
Get:9 http://security.ubuntu.com lucid-security/restricted Sources [14B]            
Get:10 http://security.ubuntu.com lucid-security/universe Packages [53.4kB]
Get:11 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,240B]      
Get:12 http://us.archive.ubuntu.com lucid-updates/main Sources [141kB]              
Get:13 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]            
Get:14 http://us.archive.ubuntu.com lucid-updates/universe Packages [158kB]             
Get:15 http://security.ubuntu.com lucid-security/universe Sources [15.3kB]              
Get:16 http://security.ubuntu.com lucid-security/multiverse Packages [2,003B]           
Get:17 http://security.ubuntu.com lucid-security/multiverse Sources [660B]                 
Get:18 http://us.archive.ubuntu.com lucid-updates/universe Sources [61.4kB]                
Get:19 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [7,366B]
Get:20 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [3,677B]
Fetched 1,058kB in 3s (347kB/s)                           
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
system76-driver is already the newest version.
The following packages were automatically installed and are no longer required:
  java-common odbcinst unixodbc sdparm odbcinst1debian1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
options snd-hda-intel model=acer-aspire
cp: cannot stat `/etc/default/grub': No such file or directory
Exception in thread Thread-2:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/opt/system76/system76-driver/src/restore.py", line 120, in run
    driverscontrol.installDrivers()
  File "/opt/system76/system76-driver/src/driverscontrol.py", line 1211, in installDrivers
    acpi.star1()
  File "/opt/system76/system76-driver/src/acpi.py", line 137, in star1
    for line in grub_menu:
  File "/usr/lib/python2.6/fileinput.py", line 253, in next
    line = self.readline()
  File "/usr/lib/python2.6/fileinput.py", line 322, in readline
    os.rename(self._filename, self._backupfilename)
OSError: [Errno 2] No such file or director
```
It appears to be hanging because it can't find a grub folder and then the restore just hangs.


Thanks again for your help

Jim

---

### Post by smulloni on 2010-12-24
For me, the solution was to create an empty /etc/default/grub file:

  sudo touch /etc/default/grub

Then installing drivers worked normally.

---

### Post by jimmie-watters on 2010-12-27
Thanks Smulloni,

i did what you suggested and i was able to install the 76 driver and  my Starling 1 has wireless working again.

Thanks again!

---

