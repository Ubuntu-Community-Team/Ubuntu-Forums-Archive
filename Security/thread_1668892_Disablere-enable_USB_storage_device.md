---
title: "Disable/re-enable USB storage device"
date: 2011-01-16
forum: Security
---

### Post by gfpoow on 2011-01-16
how to do that? (storage only, because  printer, mouse, and keyboard use USB ports too)

i need 2 conditions
1. usb computer A : can not write and read
 2. usb computer B : only read,  can not write

i still beginner in Linux
need helps
thanks

---

### Post by fabricator4 on 2011-01-17
> **gfpoow said:**
> 
1. usb computer A : can not write and read
2. usb computer B : only read,  can not write


Access control in Linux is done by file permissions, dependent on the users login, and groups.

So, the user on computer A must have a different login to the user on computer B.  Users A and B must preferably be a Desktop user only, as if they are an administrator then they can get around the security by using 'sudo' (Super User DO).

Note that this will work for _any_ linux computer, since the security is based on the user, not the physical computer, so it doesn't actually matter which computer a particular user is logged into. The exception is group access, which much be set up on each computer or network that you want the group member to belong to.

First, using your own login you need to format the USB drive with a Linux ext2 partition. Login as user A and Open "computer" in "places" and right click on the USB drive, then format.  Select ext2 partition as the 'type' and give the drive a unique volume name.

Note that this USB won't be accessible on any Windows machine any more because it has been formated with a specific Linux ext2 partition.

Now double click on "file system" to open it, then double click on "media". Now right click on the folder that has the volume name that you gave the USB drive earlier and select 'properties'

click on the 'permisions' tab.  It should say that owner (user a) has "folder access: create and delete files"

Down the bottom in 'others' the folder access should be "list files only" if you want them to be able to see that there are files there.  Change the file access for others to "none" to prevent them from entering subdirectories if you want. Click on the button "apply permissions to enclosed files". Click OK to save and exit.

Any other user should now be unable to read any files and directories on that USB drive and will also be unable to write to them or the directories. They won't even see the file names unless you gave that permission.

The next bit is a bit tricky because you have to set up a group and group permissions for anyone who you want to be able to read the files but not write to them.

You would have seen the second kind of permissions which are group permissions.  This defines the access based on what group a user belongs to, regardless of their login name, and is useful to give a group of users specific access to certain files or directories.

Follow the directions previously for setting permissions, but set the group name to something specific (eg 'usbaccess' - must be all lowercase).  Change the folder access to "access files" and the file access to "read-only"

You'll now need to go into the user management for each Computer and add the group name, and make the relevant users members of that group.

This won't take you as long to do as it took me to write the instructions.  ;-)

Chris.

---

### Post by gfpoow on 2011-01-17
thanks chris
you help me a lot

but i want to ask some question

1. Can this method works for all usb-storage (like flash, external hard drive with usb ports, memory stick) without setting again?

2. is there any script to do that? because for >80 computers
 such as  in windows, I only need to execute the registry file  only

regards

---

### Post by fabricator4 on 2011-01-18
> **gfpoow said:**
> 

1. Can this method works for all usb-storage (like flash, external hard drive with usb ports, memory stick) without setting again?

2. is there any script to do that? because for >80 computers
 such as  in windows, I only need to execute the registry file  only

regards

Hi, yes as far as I know it will work for any device that has a linux partition on it that supports access control.  Even if you copy the folders from one directory to another I think the permissions will be copied also, but you will need to test this.

Regarding the scripts, I'm not sure if you're talking about changing the permissions, or setting up groups. You can certainly change permissions with a script.  Investigate the chmod command.  Scripting, as you know, is quite powerful.

As for adding a group and making certain users members of a group, I'm fairly sure there would be no problem doing this, and I'm sure sysadmins have been doing it for decades.  Unfortunately I'm not a sysadmin and am not the best person to advise you on this.  Perhaps this would be a good topic for another question on one of the other forums here such as 'security discussions' or "Networking & Wirless" perhaps.

Also note that I confused myself in the instructions above, saying the usb device should be formatted and the permissions set under the user A login.  I should of course said that these things need to be done under your own login.

Chris.

---

