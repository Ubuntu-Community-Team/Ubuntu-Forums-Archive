---
title: "Samba not sending NetBIOS name out?"
date: 2011-05-17
forum: Server Platforms
---

### Post by usszulu on 2011-05-17
Hello all!

I have been a lurker here while I have been learning about Linux and Ubuntu and have found all the information here excellent! That brings me here today. It appears that I have found a question that I cannot answer with just research and need to directly ask people. 

I have been attempting to set up a very basic Samba server in a VirtualBox (Trying to learn Samba and how it works), and have a rather odd problem.

The Samba machine does not show up on the networking screen on my Windows machines.

I have been able to set up Samba and have the services running, but for some reason, the servers NetBIOS name gets lost somewhere. On the Windows machine, when running the "net view" command, I get this output.

```

C:\Users\Example>net view
Server Name                                               Remark
--------------------------------------------------------------------------------------------------
\\                                                               Test Samba Server.
\\EXAMPLE                                                  Windows Seven Box.
\\EXAMPLE2                                                Windows Vista Box.
The command completed successfully.

```I can access my shares by using the command
```
net view \\192.168.1.6
```Here is a dump of my configuration file for Samba

```


[Global]
   netbios name = SMBTEST
   workgroup = TESTNET
   encrypt passwords = yes
   server string = Test Samba Server.
   security = share
   load printers = no
   show add printer wizard = no
   printing = none
   printcap name = /dev/null
   disable spoolss = yes
 
[Data]
   comment = Test Share
   path = /home/testsb
   volume = Sample-Data-Drive
   writable = yes
   guest ok = yes
   share modes = yes
   browseable = yes

```
Does anyone have any ideas what could be going on here? I have exhausted all ideas.

Thank you in advance for your responses!

---

### Post by papibe on 2011-05-18
There used to be a [bug]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/572410") (have you updated recently?), where the process that provides NetBIOS services was not started. The process is called nmbd. Check if it is running in your system like this:
```
$ ps aux | grep nmbd
```
If it's not there, try update your system to get the latest version of the samba packages:
```
$ sudo apt-get update
$ sudo apt-get upgrade
```
Restart samba:
```
$ sudo service smbd restart
```
And then check again if the name is being broadcast to the other machines in your network.

If that doesn't work, what solved the problem for me was this (is in the launchpad page):
```
$ sudo dpkg-reconfigure samba-common-bin
```
I hope it helps.

---

### Post by Morbius1 on 2011-05-18
. Sorry redundant post

---

