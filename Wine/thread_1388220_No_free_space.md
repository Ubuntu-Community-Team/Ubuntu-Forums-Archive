---
title: "No free space?"
date: 2010-01-22
forum: Wine
---

### Post by Keith Fox on 2010-01-22
Trying to install VMware Workstation in Wine which is a virtual machine. I get this error saying not enough space (see attached photo).  Strange because my hard drive has like 500 GB free. I'm looking in the Wine Configuration and maybe I'm just not seeing it right, but take a look and see what's going on in my wine configuration for me please.

I don't know :confused: what to do about it. ](*,)

[LIST=1]
[*]How would I find my Wine version? Trying to figure out if I need to upgrade the version.
[*]Does this .NET Framework (2.0) work with Wine?
[LIST]
[*]:arrow: [http://appdb.winehq.org/appview.php?iVersionId=3754](http://appdb.winehq.org/appview.php?iVersionId=3754)
[/LIST]
 
[/LIST]
This website is fantastic, thanks to you all in this community thread! =;

---

### Post by beastrace91 on 2010-01-22
Just a quick question - why are you trying to run the Windows version of VMWare workstation through Wine? It has a native Linux installer...

~Jeff

---

### Post by Keith Fox on 2010-01-23
Thanks for clarifying the Synaptic package is available for VMware Workstation. I didn't know and picked up the windows version instead. 

What should I search for in Synaptic to get this software?  

I'm trying to use a virtual machine to test software on different platforms.

I also need to know how to install the .NET framework in Wine to try and get this software to work in wine. Here is the information about the software and system requirements for it:

[INDENT][I]Software name: FixYa Expert Utility Software
[/I][/INDENT][INDENT][I]Description: Our Instant Messenger will allow you to provide live assistance to users with a 						tech problem while earning cash. (FixYa.com)

Current Version: 					 					 						1.5.1 					 				 				 					 						
Date Added: 					 					 						June 15th, 2008 
					 				 				 					 						File Size: 					 					 						170KB 					 				 				 					 						D
Requirements: 					 					 						Windows (2000, XP, 2003, Vista), Microsoft .NET Framework 
					 				 				 					 						License: 					 					 						Free[/I]

[/INDENT]Normally in Wine I couldn't get it to install, but I am guessing if I get .NET framework installed in Wine theoretically it will work for me.

So anybody have some help for my questions in my thread [post 1]("http://ubuntuforums.org/showpost.php?p=8709235&postcount=1")
[SIZE=2][/SIZE]

---

### Post by beastrace91 on 2010-01-23
The VMWare Station package is not for download in synaptic - the package manager only contains FOSS/Freeware Linux software. You download the Linux packages from VMWare's website (should be in a .bin format).

As for installing .NET, check out [Winetricks](wiki.winehq.org/winetricks) - but remember just because .NET installs does not mean your application requiring .NET is going to run under Wine.

Also may I inquire as to what exactly you are going to be using the VM for? If it is for personal (or even just basic home server) use - you might want to look into [VirtualBox](http://www.virtualbox.org/) as VM is more for server level VM stations.

~Jeff

---

### Post by Keith Fox on 2010-01-23
ok got virtualbox installed, don't know how to run though  :confused:
```
chieffox@FBI:~$ sudo apt-get install virtualbox-3.1
[sudo] password for chieffox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-3.1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 45.6MB of archives.
After this operation, 91.4MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  virtualbox-3.1
Install these packages without verification [y/N]? y
Get:1 http://download.virtualbox.org karmic/non-free virtualbox-3.1 3.1.2-56127_Ubuntu_karmic [45.6MB]
Fetched 45.6MB in 29min 33s (25.7kB/s)                                         
Preconfiguring packages ...
Selecting previously deselected package virtualbox-3.1.
(Reading database ... 251822 files and directories currently installed.)
Unpacking virtualbox-3.1 (from .../virtualbox-3.1_3.1.2-56127%5fUbuntu%5fkarmic_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Setting up virtualbox-3.1 (3.1.2-56127_Ubuntu_karmic) ...
Adding group `vboxusers' (GID 125) ...
Done.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
Success!
 * Starting VirtualBox kernel module                                             *  done.

```

I feel like such a noob again.

---

### Post by beastrace91 on 2010-01-24
Applications->System Tools->VirtualBox

or run 

**VirtualBox** (note the capital letters) in terminal.

Regards,
~Jeff

---

### Post by Keith Fox on 2010-01-24
oh, there it is right there like you said. Many thanks and praises!

---

