---
title: "AFP permission issues"
date: 2012-10-13
forum: Server Platforms
---

### Post by mbischoff on 2012-10-13
I'm new here and kind of new to Ubuntu and since it's my first post, hello everybody! :)

Since Apple keeps changing Mac OS X Server and by definition requires a Mac to run, I wondered if it might be possible to set up a basic file server for Mac clients with Ubuntu. While the installation and basic configuration of Netatalk and Avahi was pretty straight forward, I ran into weird issues with AFP permissions. So here's what I did and what I hope someone more experienced than me can help me with. I use Ubuntu Server 12.04 in VMWare and connecting with Mac OS X 10.8.2.

Installed Netatalk:
```
apt-get install netatalk
```

Installed Avahi:
```
apt-get install avahi-daemon
```

Uncommented this line in /etc/netatalk/afpd.conf to enable encrypted password transmission:
```
- -tcp -noddp -uamlist uams_dhx2.so -nosavepassword
```

Edited /etc/netatalk/AppleVolumes.default so it reads:
```
# The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: options:upriv,usedots

# By default all users have access to their home directories.
~/			"Home Directory"
/srv/files/Agentur	"Agentur"		allow:@mitarbeiter dperm:0775 fperm:0664
/srv/files/Test		"Test"			allow:@mitarbeiter dperm:0755 fperm:0664
```

Added some users and groups:
```
adduser marcel --ingroup staff
adduser lutz --ingroup staff
addgroup mitarbeiter
addgroup marcel mitarbeiter
addgroup lutz mitarbeiter
```

So far, so good. The first test connecting with user "marcel", using the share "Agentur" worked fine. I copied a file there. When connecting with user "lutz", I could read but not write or delete the file and not copy any more files there. User "marcel" still worked as expected. I found the issue when looking at the permissions of the files that were created after the first login. Here's a list if the permissions:

```
drwxr-xr-x 2 root   staff   4096 Oct 13 18:09 .AppleDB/
drwxr-xr-x 2 root   staff   4096 Oct 13 16:21 .AppleDesktop/
drwxr-xr-x 2 root   staff   4096 Oct 13 17:51 .AppleDouble/
-rw-rw-r-- 1 marcel   staff  15364 Oct 13 17:14 .DS_Store*
-rw-rw-r-- 1 marcel staff 153080 Oct 12 13:54 IMG_2006.JPG
drwxr-xr-x 3 root   staff   4096 Oct 13 16:21 Network Trash Folder/
drwxr-xr-x 3 root   staff   4096 Oct 13 16:21 Temporary Items/
```

Apparently the .Apple* files get created after the first connect &#8211; with the name of the user who logged in first over AFP. But no matter how I changed the permissions in that folder, nothing short of

```
chown root:staff * .Apple*
chmod 777 * .Apple*
```

did work. Is that correct behavior? I'm confused, since Mac OS X Server handles this quite differently. All files are assigned to root:root and when setting up a new share there is of course no waiting for the first login and then adjusting the permissions by hand. What I don't understand is why I need to have world rwx permissions, when all users connecting are in the default group "staff". When I remove x from world, the share stops working altogether, r and w do what the should do.

Which brings me to ACLs. I read about problematic ACLs [here]("http://signalboxes.net/mac2linux/replace-mac-os-x-file-servers-with-linux/#Permissions_and_ACLs") and [here]("http://www.mattb.net.nz/blog/2007/07/09/posixnfsv4-acl-inheritance-problems/"), so I kind of understand the reasoning. I still feel it's confusing since the usual expected behavior on practically and file server would be to inherit the permissions from the parent folder when creating a new file or folder.

To summarize:

[LIST]
[*]Can anyone clear up the permission issue?
[*]Is there a good and clear guide to using ACLs in combination with AFP for Ubuntu?
[*]Does a clear guide for AFP exist that covers all those pitfalls?
[/LIST]

Thanks in advance for taking the time to read this and possibly help me. Please excuse if I may have forgotten to include vital information. This is my first serious try with Linux.

---

### Post by mbischoff on 2012-10-21
Unfortunately no one replied to my post to give me pointers. I thought I'd share the preliminary solution I found after quite some digging. Maybe it helps others having the same trouble.

I have come across yet another weirdness: the explicit permissions set by dparm and fparm were not carried out. No matter what I did, it did not work. Until I came across the option umask. All that was needed was to change /etc/netatalk/AppleVolumes.default to this:

```
# The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: options:upriv,usedots

# By default all users have access to their home directories.
~/			"Home Directory"
/srv/files/Agentur	"Agentur"		allow:@mitarbeiter dperm:0770 fperm:0660 umask:0007
/srv/files/Test		"Test"			allow:@mitarbeiter dperm:0750 fperm:0660 umask:0007

```

Aside from running

```
chmod 777 * .*
chown root:staff * .*
```

after creating a new share and logging in for the first time, everything works like charm now.

You're very welcome to add to this or correct me where I'm wrong.

---

### Post by bernstein on 2013-08-31
with ```
dperm:0770 fperm:0660 umask:0007
``` i got the group sticky bit set (might be a bug in netatalk 2.2.2-1ubuntu1) : ```
drwxrw[COLOR="#FF0000"]s[/COLOR]---   3 bernstein bernstein       4096 Aug 31 19:00 test
``` so i had to change it to ```
dperm:0770 fperm:0660 umask:[COLOR="#FF0000"]7[/COLOR]007
```

fyi afaik: dperm and fperm always force the given rights (like ug+rwx or ug+rw), however they don't prevent anything. umask is for denying rights (like o-rwx, ug-s & a-t).

---

