---
title: "Where to put Windows VM for access by multiple users?"
date: 2012-05-13
forum: Virtualisation
---

### Post by Rebelli0us on 2012-05-13
I have Win7 in my home/user1.. but other users have no rights to that directory. Is there a way to have all users access the VM and log into Windows to their respective accounts? i.e. in some **common** directory. I understand that only one instance of win7 will be possible in this case.

---

### Post by jayshomebrew on 2012-05-13
I think you're asking a windows question not a VM one. Start your win7 from your VM host computer, and allow remote access:

[http://www.howtogeek.com/howto/windows-vista/turn-on-remote-desktop-in-windows-vista/]("http://www.howtogeek.com/howto/windows-vista/turn-on-remote-desktop-in-windows-vista/")

[IMG]http://www.howtogeek.com/geekers/up/sshot-2009-10-19-01-23-27.png[/IMG]

Then using your favorite remote access app (ie, remmina, remote desktop viewer, ) access your VM. You can search within the software center for **RDP**

[IMG]http://cdn1.sudobits.com/wp-content/uploads/2011/11/remmina-remote-desktop.jpg[/IMG] 

or from another windows computer:
[IMG]http://i661.photobucket.com/albums/uu331/NosferatuX/RDC/RemoteDesktopConnection.png[/IMG]

---

### Post by Rebelli0us on 2012-05-13
Thank you. I think you answered a different question. :)

I simply want my guests/friends/visitors to be able to start the Win7 VM, login to the guest account, and check their email. The problem is that my guests have no rights to my home directory.  (../“VirtualBox VMs”)

---

### Post by Dubslow on 2012-05-13
I have relatively limited experience with this sort of admin stuff on Linux, but I have a few ideas.

A:
1) Put the VM folder in /home, i.e. "/home/VirtualBox<whatever name>"
2) For each user to whom you want to grant access, do something like:
```
$ USR = "<insert username here>"
$ LOC = "/home/VirtualBox/<prog name>"
$ NAME = "<virtual-box-executable-name-of-choice>"
$ sudo chown root:root $LOC # Or whatever your admin username is
$ sudo chmod 755 $LOC
$ cd /home/$USR
$ sudo ln -s $LOC ./$NAME
$ sudo chown -h $USR:$USR $NAME
```
The actual executable is only writable by root/admin, but other users have execute permissions. They see an executable in their home folder that will launch VirtualBox.

Edit: On further thought, you could even keep the actual executable where it is now, owned by you and not root, just be sure the permissions are 755 (rwx r-x r-x You Group Other[meaning guests]) and then use a similar "ln -s" command to put a link in their home folders.

B: Well I forget now, but almost any solution will have one common location for the actual executable and then produce links (sym or otherwise) to the executable that are in each user's home folder.

---

### Post by Rebelli0us on 2012-05-15
Thank you. I moved the VM to an NTFS partition. Now any user can boot it up.

---

### Post by dcstar on 2012-05-16
> **Rebelli0us said:**
> 
I simply want my guests/friends/visitors to be able to start the Win7 VM, login to the guest account, and check their email. The problem is that my guests have no rights to my home directory.  (../“VirtualBox VMs”)

Or simply run the Windows VM permanently and have the other users connect to it via Remmina and then log in.

---

### Post by Rebelli0us on 2012-05-16
> **dcstar said:**
> Or simply run the Windows VM permanently and have the other users connect to it via Remmina and then log in.

Thank you. Remote Desktop Viewer & Remmina is kind of slow, I want users to have full use of the machines on my network but logged into separate guest account. It's working so far with VM on NTFS partition. But I've run into another problem though, [wakeonlan is not working on Ubuntu hosts!]("http://ubuntuforums.org/showthread.php?t=1980486")

---

