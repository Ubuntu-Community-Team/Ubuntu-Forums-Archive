---
title: "Package Manaager Failure"
date: 2007-07-26
forum: Ubuntu Christian Edition
---

### Post by jonathonblake on 2007-07-26
Symantic, Updae manger, Add/Remove, and apt-get all give me an error message indicating they can't remove "twiki".

What file do I edit so that twiki does not show up to be removed?
[I've forgotten what the issue is, but twiki never was installed on my system.  All attempts to do so failed with an error message along the lines of "Baddevice, invalid or uninitialized input device".

I also got an error message along the lines of "unable to authenticate either the host or the packages."

######
I'm asking all this so I can get my DVD burner to work.  Once I've archived my data, I'll repartition the hard drive, so the next time I upgrade, I will have a fall back partition to work from.

xan

jonathon

---

### Post by tak1150 on 2007-07-26
What's the exact error message?

---

### Post by jonathonblake on 2007-07-29
The remove/update/install process begins with the following statement:

[i]Error bad Device: Invalid or Uninitialized input device 167
Major opcode: 144
Minor opcode: 3
Resource Id:  0x0
Failed to open device
Error bad Device: Invalid or Uninitialized input device 167
Major opcode: 144
Minor opcode: 3
Resource Id:  0x0
Failed to open device
Session Mangement error: Authentication rejected, reason: None of the authentication protocols are supported and host based authentication failed.[/i]

Then comes a whole lot of stuff of it trying to do something.
The remove/update/install process ends with the following statement:
*Not all changes and updates succeeded.  For further details of the failure, please expand the 'terminal' panel below.*

I have no idea what terminal panel it is referring to.  

Clicking on the "Close" button gives the following screen/error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Running "sudo dpkg --configure -a" gives the following result:

Setting up twiki (4.0.5-9.1ubuntu1) ...
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Can't open /etc/twiki/LocalSite.cfg: No such file or directory.
Can't open /etc/twiki/apache.conf: No such file or directory.
Can't open /etc/twiki/apache.conf: No such file or directory.
rm: cannot remove `/etc/twiki/*~': No such file or directory
dpkg: error processing twiki (--configure):

 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 twiki

xan

jonathon

---

### Post by tak1150 on 2007-07-29
have you tried running:

```
sudo apt-get --purge remove twiki
```

?

---

### Post by jonathonblake on 2007-07-30
jonathon@e-sword:~$ sudo apt-get --purge remove twiki
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-utils apache-common libapr1 libpq5 libaprutil1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  twiki
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 8507kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 412516 files and directories currently installed.)
Removing twiki ...
 * /usr/sbin/apachectl is not executable, exiting...                                                                 [fail]
invoke-rc.d: initscript apache, action "reload" failed.
dpkg: error processing twiki (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 twiki
E: Sub-process /usr/bin/dpkg returned an error code (1)

xan

jonathon

---

### Post by tak1150 on 2007-07-30
I'm really not sure how to cleanly remove twiki at this point... :(

But, if all you want to do is to burn a data DVD, you should be able to do that w/out installing anything.
The process is very much integrated with Nautilus. If you know all this already, forgive me, but;

1. insert a blank dvd
2. hit ignore on the popup windown
3. open the DVD icon on the desktop
4. drag & drop things you want to be recorded on the DVD
5. click on "write to disk"

---

### Post by tak1150 on 2007-07-31
I did a little research and it seems like you have the same problem as this [post]("http://ubuntuforums.org/showthread.php?t=240548&highlight=twiki")

Not that the above thread helps ... :(

I'm almost out of ideas, and if you've done this already, sorry, but have you run:

```
sudo apt-get autoremove twiki
```
?

And how did you install twiki?
If you compiled it yourself, you need to do
```

sudo make uninstall
```

from the directory that has you Makefile file (where you compiled your twiki).

---

### Post by jonathonblake on 2007-08-01
> 
1. insert a blank dvd
 2. hit ignore on the popup windown
 3. open the DVD icon on the desktop
 4. drag & drop things you want to be recorded on the DVD
 5. click on "write to disk"


If only it were that easy.

* X-CD-Roast requires that I run as superuser, so that doesn't work. :(
* Brassero will burn ISO image :KS
but not create one :(
* K3B requires that I use a double density DVD, not the single density ones that I have, even to create an ISO image.   :confused:

[QUOTE=tak1150]
Not that the above thread helps ... :(
[/quote]

> but have you run:
```
sudo apt-get autoremove twiki
```

With the same error messages as before.  :(

> And how did you install twiki?
If you compiled it yourself, you need to do

I didn't. Had i done so i wouldn't have the issue I have.  

xan

jonathon  S
* K3B requires that I use a double density DVD, not the single density ones that I have, even to create an ISO image.   

[QUOTE=tak1150]
Not that the above thread helps ... :(
[/quote]

> but have you run:
```
sudo apt-get autoremove twiki
```

With the same error messages as before.  :(

> And how did you install twiki?
If you compiled it yourself, you need to do

I didn't. Had i done so i wouldn't have the issue I have.  

xan

jonathon

---

### Post by tak1150 on 2007-08-01
Are you trying to burn a simple data DVD or ISO image of your harddrive on a DVD?

Unless you want to restore system files for the OS, etc, you could simply archive your data with tar and put it on a DVD.

What OS are you using?

Sorry; these are questions I should've asked first

---

