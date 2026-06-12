---
title: "Is my system under attack ?"
date: 2009-02-03
forum: Security
---

### Post by ivikas on 2009-02-03
Dear all,

Recently i have installed rkhunter(root kit hunter) and running a system check with it has given some warning.Some files are suspicious
and i don't know what to do with itand suspect some security breach.Please help me out of this.Those lines are given below

[17:03:17] /bin/which                                        [ Warning ]
[17:03:17] [COLOR="Red"]Warning: The command '/bin/which' has been replaced by a script: /bin/which: POSIX shell script text executable ----Is this denotes some security breach.[/COLOR]

[COLOR="Red"][17:03:19] /usr/bin/groups                                   [ Warning ]
[17:03:19] Warning: The command '/usr/bin/groups' has been replaced by a script: /usr/bin/groups: POSIX shell script text executable
[/COLOR]
[COLOR="Red"][17:03:19] /usr/bin/ldd                                      [ Warning ]
[17:03:20] Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne-Again shell script text executable
[/COLOR]
[[COLOR="Red"]17:03:23] /usr/bin/lwp-request                              [ Warning ]
[17:03:23] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: perl script text executable[/COLOR]

[COLOR="Red"][17:03:25] /usr/sbin/adduser                                 [ Warning ]
[17:03:25] Warning: The command '/usr/sbin/adduser' has been replaced by a script: /usr/sbin/adduser: perl script text executable
[/COLOR]
[COLOR="Red"]17:03:56]   Checking for group file changes                 [ Warning ]
[17:03:56] Warning: Groups have been added to the group file:
[17:03:56]          admin:x:115:

[17:03:56] Warning: Groups have been removed from the group file:
[17:03:56]          admin:x:115:ecsion---i have changed this to allow only root access.
[/COLOR]

[COLOR="Red"][17:03:57] Info: SCAN_MODE_DEV set to 'THOROUGH'
[17:03:57]   Checking /dev for suspicious file types         [ Warning ]
[17:03:57] Warning: Suspicious file types found in /dev:
[17:03:57]          /dev/shm/pulse-shm-395976454: data

[17:03:57]   Checking for hidden files and directories       [ Warning ]
[17:03:57] Warning: Hidden directory found: /etc/.java
[17:03:57] Warning: Hidden directory found: /dev/.static
[17:03:57] Warning: Hidden directory found: /dev/.udev
[17:03:57] Warning: Hidden directory found: /dev/.initramfs
[/COLOR]
One of the most thing iam concerned with is the files i have found in the above four location

In /etc/.java

   These are the files

        [COLOR="Red"].systemPrefs/-------------->Folder in /etc/.java

        inside this folder there are two  files 
	
	.system.lock

	.systemRootModFile-------------->Is this a common file( i have  installed java plugin for firefox,so is this file 
					 relate to java plugin or is it [/COLOR]a  remote hack on my computer.
In /dev/.udev

	It contains the following folder
	db,failed,names,rules.d and one file named "uevent_seqnum"


In /dev/.static

       Contains a folder dev which contains lots of device files like fd,pts,shm and so on




In /dev/.initramfs

        varrun------------->folder

	And it contains  a file by name "sendsigs.omit" and it is empty
	
	usplash_fifo---------->This is file, which i cannot open

	usplash_outfifo------->This is file, which i cannot open



	
Apart from this there is also a group added to my system named "polkituser'.So what is this group for.Is there any type of security threat on my system.
How can i know if someone has gained root acces to my system.is there any tools to check security threats.Is rkhunter(root kit hunter) reliable.Any advise 
or weblink will be highly appreciated.My system is ubuntu 8.04.2 LTS Hardy Heron and is regularly updated and i have also installed avg anti virus for 
linux.

Thanks in advance

---

### Post by cariboo on 2009-02-03
Did you run:

```
sudo rkhunter --update
```

before running your scan?

Most of what you are concerned about seem to be ok. but run the above command and run rkhunter again.

Jim

---

### Post by listerdl on 2009-02-03
Can I ask, why would you want to run a "root kit hunter" - are you assuming that your operating system was corrupted or that you have deleted files in error? (Sorry im new, just intersted to know why someone would do that with GNU/linux)

---

### Post by ivikas on 2009-02-04
hello Jim,

                 Yes i have run this command before scanning and it says "No update".
After running update i checked the system.It listed that my system does not contains any root kit but gave some warnings and so was curious to know?

hello listerdl,
               Actually iam new to computer security and i have read some articles.it says every os is vulnerable to virus,trojan and remote attack and linux is no exception.But compared to other os linux is more secure.Still there are threats,someone may install a rootkit into your system and gain full access to it without you being known.so i am curious to know more and protect my system.

---

### Post by brian_p on 2009-02-04
These forums contain much information on the behaviour of rkhunter, the messages it gives and how to interpret or eliminate them.

> **ivikas said:**
> 

Still there are threats,someone may install a rootkit into your system and gain full access to it without you being known.so i am curious to know more and protect my system.

If someone can install a rootkit on your system you have not done well in protecting it in the first place.

---

