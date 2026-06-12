---
title: "&quot;Map Network Folders&quot; for easy mounting of CIFS drives"
date: 2008-10-06
forum: Ubuntu Brainstorm
---

### Post by maybeway36 on 2008-10-06
I posted this idea a while back on the forums ([http://ubuntuforums.org/showthread.php?t=702705]("http://ubuntuforums.org/showthread.php?t=702705")) and it is also on Launchpad (see ideas [4837]("http://brainstorm.ubuntu.com/idea/4837/") and [13568]("http://brainstorm.ubuntu.com/idea/13568/").)
I would very much like to see a "Map Network Folders" applet similar to the one in Windows, either via the fstab or FUSE.
I made a Python script to generate an fstab line for a network share (command-line only, I haven't got the hang of using Glade+Python yet):
```
#!/usr/bin/env python

#cifs.py - script for making a cifs fstab line
#Made by maybeway36

import os

server = raw_input("Server name/IP: ")
share = raw_input("Share name: ")
mountpoint = raw_input("Mount point: ")
username = raw_input("Username on the server: ")
user = raw_input("Local username/UID (optional): ")
group = raw_input("Local group/GID (optional): ")
options = raw_input("Extra options (optional): ")

#Check if you entered a server username
if username == '':
	newusername = ''
else:
	newusername = ',username=' + username

#Define what numbers are
numbers = "0123456789"
#Did you enter a username?
if user == '':
	newuid=''
else:
	userfirstletter = user[0]
	#Is it a username or UID?
	for letter in userfirstletter:
		if letter in numbers:
			newuid = ',uid='+user
		else:
			#If it is a username, find the matching UID
			uiddata = os.popen("grep ^"+user+": /etc/passwd|awk -F':' '{print $3}'")
			newuid = ',uid='+uiddata.read()
			newuid = newuid[:-1]
#Did you enter a group?
if group == '':
	newgid=''
else:
	groupfirstletter = group[0]
	#Is it a group or GID?
	for letter in groupfirstletter:
		if letter in numbers:
			newgid = ',gid='+group
		else:
			#If it is a group, find the matching GID
			giddata = os.popen("grep ^"+group+": /etc/group|awk -F':' '{print $3}'")
			newgid = ',gid='+giddata.read()
			newgid = newgid[:-1]

#Replace spaces in the share with the escape character \040
newshare = share.replace(" ", "\\040")

#Print the line, finally!
print '//' + server + '/' + newshare + ' ' + mountpoint + ' defaults' + newusername + newuid + newgid + ' 0 0'

```

---

### Post by cdenley on 2008-10-07
When you connect to a samba server, it is mounted. I always access my shares after they are mounted by browsing in "~/.gvfs". The "smb://" virtual paths seem to work horribly.

Creating fstab entries would be very annoying in a multi-user environment. Also, the reason I stopped using fstab entries is you just can't seem to get the permissions to follow the rules defined in the server's smb.conf file.

---

### Post by maybeway36 on 2008-10-08
The thing that annoys me about .gvfs is it's a hidden directory, and so by default you can't browse to it in, say, Amarok. Plus, it is GNOME only.

---

### Post by mbeierl on 2008-10-09
I don't get this .gvfs folder, or the smb:// methods - are the usable from a shell (such as if I ssh in, can I access a cifs share mounted in this way?)

Also, what if I need to cd into the share, or use any command line programs - do any of these shares actually show up anywhere as real mounted filesystems, or are the virtual in Nautilus only?

Right now, I'm voting for maybeway36's script!

---

### Post by cdenley on 2008-10-09
They are real directories. The directory .gvfs is in the home directory of the user who makes the connections. It is hidden since it starts with a ".". Typically, you can either do a ctrl+h to show hidden directories, or you can create a link which isn't hidden.
```

sudo ln -s ~/.gvfs ~/network

```
I use the gvfs mounts in the terminal and in the web browser. It looks like the support for gvfs is being improved in intrepid as well.

It is gnome-only, but I don't think an fstab solution would work. Network connections established by/for a user should be user-specific, and should not require root access.

---

### Post by mbeierl on 2008-10-09
First, thanks!

Secondly, how do I "mount" something inside my .gvfs?  I have a 'bookmark' for a Windows share that I can go to in nautilus, which shows up as a "smb://DOMAIN;user@/share", but my .gvfs is empty.

---

### Post by cdenley on 2008-10-09
> **mbeierl said:**
> First, thanks!

Secondly, how do I "mount" something inside my .gvfs?  I have a 'bookmark' for a Windows share that I can go to in nautilus, which shows up as a "smb://DOMAIN;user@/share", but my .gvfs is empty.

Whenever I can see "smb://DOMAIN;user@host/share" in nautilus, there is a directory in ~.gvfs called "share on host". Maybe you need to click "Reload"?

---

### Post by maybeway36 on 2008-10-09
I think it would be nice if you could use the gvfs framework to mount something outside of the .gvfs directory and do it automatically on login. Most users don't even know that .gvfs is there.

---

### Post by cdenley on 2008-10-09
> **maybeway36 said:**
> I think it would be nice if you could use the gvfs framework to mount something outside of the .gvfs directory and do it automatically on login. Most users don't even know that .gvfs is there.

I agree that there should be an unhidden link by default for easy terminal access, and there should be an option for auto-mount. Maybe there is a way to script auto-mounting.

---

### Post by mbeierl on 2008-10-09
Doh!  My .gvfs directory had the wrong userid on it.  (I had changed userid numbers in the past).

So, once I fixed the permissions and rebooted (? don't know if just a login/out would have done it) suddenly .gvfs works!

Is it possible to mount things in there from a script?  That'd be amazing.

---

### Post by cdenley on 2008-10-09
> **mbeierl said:**
> Doh!  My .gvfs directory had the wrong userid on it.  (I had changed userid numbers in the past).

So, once I fixed the permissions and rebooted (? don't know if just a login/out would have done it) suddenly .gvfs works!

Is it possible to mount things in there from a script?  That'd be amazing.

```

sudo apt-get install gvfs-bin
gvfs-mount smb://cdenley@ubuntu/shares

```
If you have a bookmark for the path, and you selected for it to remember the password, it is done without any user input (at least in intrepid).

I made a script
~/.automount.sh
```

#!/bin/sh
grep smb:// ~/.gtk-bookmarks|cut -d ' ' -f 1|xargs gvfs-mount

```
made it executable
```

chmod +x ~/.automount.sh

```
added it to the startup
System>Preferences>Sessions

Now when I log in, after a few seconds, all my samba shares are mounted.

---

### Post by cdenley on 2008-10-13
[[IMG]http://brainstorm.ubuntu.com/idea/14253/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/14253/)

---

### Post by lithorus on 2008-10-16
I just wanted to add a little modification to the script. The problem with the smb:// bookmarks is that they do not appear in the side for applications which doesn't work with smb://. So I added my bookmarks as file:///home/lith/.gvfs/ and reworked the script a little.

```
#!/bin/sh
grep -e '/\.gvfs/' .gtk-bookmarks|sed -e 's/file:\/\/\/home\/lithorus\/\.gvfs\//smb:\/\/\t/g'|sed 's/\(smb:\/\/\)\(\t\)\([a-z\-]*\)%20on%20\([a-z\-]*\)/\1\4\/\3/g'|xargs gvfs-mount
```

---

### Post by cdenley on 2008-10-16
> **lithorus said:**
> I just wanted to add a little modification to the script. The problem with the smb:// bookmarks is that they do not appear in the side for applications which doesn't work with smb://. So I added my bookmarks as file:///home/lith/.gvfs/ and reworked the script a little.

```
#!/bin/sh
grep -e '/\.gvfs/' .gtk-bookmarks|sed -e 's/file:\/\/\/home\/lithorus\/\.gvfs\//smb:\/\/\t/g'|sed 's/\(smb:\/\/\)\(\t\)\([a-z\-]*\)%20on%20\([a-z\-]*\)/\1\4\/\3/g'|xargs gvfs-mount
```

It didn't seem to work for me, even after fixing the path to home. I'm not familiar with regular expressions, so I used the same idea with different commands.
```

#!/bin/sh
grep file://$HOME/.gvfs .gtk-bookmarks|cut -d ' ' -f 1|cut -c $(( ${#HOME} + 15 ))-|awk -F'%20on%20' '{print "smb://"$2 "/" $1}'|xargs gvfs-mount

```

Intrepid used to actually translate the smb:// bookmarks to ~./gvfs paths for firefox, but not anymore after some updates. Now the bookmarks just don't show up if they are smb://.

---

### Post by lithorus on 2008-10-17
> **cdenley said:**
> It didn't seem to work for me, even after fixing the path to home. I'm not familiar with regular expressions, so I used the same idea with different commands.
```

#!/bin/sh
grep file://$HOME/.gvfs .gtk-bookmarks|cut -d ' ' -f 1|cut -c $(( ${#HOME} + 15 ))-|awk -F'%20on%20' '{print "smb://"$2 "/" $1}'|xargs gvfs-mount

```

Intrepid used to actually translate the smb:// bookmarks to ~./gvfs paths for firefox, but not anymore after some updates. Now the bookmarks just don't show up if they are smb://.
Yours is much cleaner :)
Had some issues with getting 'cut' to work like I wanted it to but failed, so I went with some ugly regular expressions :)

---

