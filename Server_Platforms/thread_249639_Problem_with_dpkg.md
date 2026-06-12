---
title: "Problem with dpkg"
date: 2006-09-02
forum: Server Platforms
---

### Post by frankabel on 2006-09-02
Hi all!

While instaling the samba package my computer turn off. When I run  sudo dpkg -C I get the following output:

"The following packages are only half configured, probably due to problems configuring them the first time.  The configuration should be retried using dpkg --configure <package> or the configure menu option in dselect:
samba                a LanManager-like file and printer server for Unix"

Ofcourse I try dpkg --configure samba but nothing, I get another error.

The question is: What can I do for install a fresh copy of samba package?

Salute
Frank Abel

---

### Post by chrisfay on 2006-09-02
```
sudo apt-get --purge remove samba
sudo apt-get install samba
```

---

### Post by frankabel on 2006-09-02
Thanks for you quick respond

See the result:
"
frankabel@yah:/var/www$ sudo apt-get --purge remove samba
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 21 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 18499 files and directories currently installed.)
Removing samba ...
 * Stopping Samba daemons...                                                                                          [ ok ]
Purging configuration files for samba ...
Removing configuration file /etc/default/samba...
Removing configuration file /etc/default/samba...
frankabel@yah:/var/www$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 7250kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 18450 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
Setting up samba (3.0.22-1ubuntu3.1) ...
Generating /etc/default/samba...
 * Starting Samba daemons...                                                                                          [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
"

Well I will confess something: I remove the /etc/samba directory. Have this any importance?

Salute
Frank Abel

---

### Post by chrisfay on 2006-09-02
> * Stopping Samba daemons... [ ok ]

It looked like your smbd daemon was already running before you removed and reinstalled the package. Try to see if both the smbd and nmbd daemons are actually running on your system now that you've reinstalled:

the smbd daemon:
```
ps -efa | grep -v grep | grep smbd
```
and the nmbd daemon:
```
ps -efa | grep -v grep | grep nmbd
```

If you get output, then they are running. If not, try running:
```
sudo /etc/init.d/samba start
```

If that doesn't start the daemon, or you get errors, you may trying checking the samba logs in /var/log/samba (if it has any)

All else fails, and you can't start it, I would try manualling removing the samba daemon from init.d and the files in /etc/samba before reinstalling.
```
sudo rm /etc/init.d/samba
sudo rm -R /etc/samba
```
Then try purging and reinstalling again.

```
sudo apt-get --purge remove samba
sudo apt-get install samba
```

It looks like you're daemons keep getting left behind with removing the software. Not sure but deleting them before you reinstall may help.

---

### Post by frankabel on 2006-09-03
Hi mate!

Thanks for your reply again.

The smbd daemon and nmbd daemon aren't running and when I try run "sudo /etc/init.d/samba start" I get the follwing output:

"
[2006/09/01 09:31:53, 0] nmbd/nmbd.c:main(727)
  Netbios nameserver version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2006/09/01 09:31:53, 0] param/params.c:OpenConfFile(538)
  params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
        No such file or directory
"

Then I try "sudo rm /etc/init.d/samba; sudo rm -R /etc/samba" and
"sudo apt-get --purge remove samba" and "sudo apt-get install samba" and I get the same error.

I try to install other package and all is fine.

I really don't understand what is the problem

Salute
Frank Abel

---

