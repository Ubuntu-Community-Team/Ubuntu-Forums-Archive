---
title: "Configuring Samba permissions to emulate Netware"
date: 2010-04-22
forum: Server Platforms
---

### Post by Fooshnik on 2010-04-22
I'm replacing an ancient Netware server with a new Ubuntu 8.04 box running samba and LDAP. I want to see if there's a way to get Samba to emulate the way permissions propagate through Netware. Namely, if I see a directory structure like this:

[User Cant See]
--- [User Cant See]
------- User Can Edit.txt
------- User CANT Edit.txt

With Netware I can give permission to User to edit "User Can Edit.txt" and the permissions will propagate in reverse to allow User to see the two [User Cant See] directories and edit the text file. "User CANT Edit.txt" will still be invisible to User. This is very convenient as I can simply give user access to one file, they can navigate to it through the directory structure, and all files not explicitly given access to will still be invisible.  

With Samba the only way I've been seeing to get this would be to explicitly give User access to both [User Cant See] directories, give him access to the "User Can Edit.txt" and remove any access to "User CANT Edit.txt" and every other file in the latter two nested directories. 

I think I'm just missing something. Any way to get this to work like Netware?

---

### Post by Vegan on 2010-04-22
Netware, I abandoned that so long ago now its a faint memory.

The best way to achieve that is to cross connect SAMBA with the Linux users. Then you can map the /home/username to the user directory the same as Netware does.

You can also have a /public folder as well just like Netware uses.

Its all the way back to the DOS era when I used Netware until I became fed up with it and swicthed to FreeBSD and was able to achieve a far more secure platform.

---

### Post by Fooshnik on 2010-04-22
I have home/username working and /public working. What I'm curious about is what is the method to provide access to one database file under /acctg/access/, without providing access to all the other files in /acctg and /access/. The only way I'm coming up with is to add read access to /acctg and /access/ and read/write to the database file. Unfortunately this also provides read access to the files under /acctg and /access/ which I don't want. What's the best way to do this?

---

### Post by redmk2 on 2010-04-22
> **Fooshnik said:**
> I have home/username working and /public working. What I'm curious about is what is the method to provide access to one database file under /acctg/access/, without providing access to all the other files in /acctg and /access/. The only way I'm coming up with is to add read access to /acctg and /access/ and read/write to the database file. Unfortunately this also provides read access to the files under /acctg and /access/ which I don't want. What's the best way to do this?

I assume you are using the /etc/samba/smb.conf file to configure your shares.  When you create the share you are actually setting the root directory for the share.

I keep all of my samba shares in /smb.  I have a share for backups at /smb/backups and a share for pictures at /smb/pictures.  The users of /smb/pictures (the share is Pictures) do not see /smb/backups (the share is Backups).

There are a ton of configuration parameters for smb.conf.  The smb.conf page from the documentation is a big help.  See [**_here_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

If you have the time read the By-Example doc at Samba.  It is [**_here_**]("http://www.samba.org/samba/docs/man/Samba-Guide/").

There have been a few changes recently.  See [**_here_**]("http://www.samba.org/samba/news/symlink_attack.html").  This may not be in the current documentation.  I don't use symlinks in shares.  It's a bad practice.  I'm mentioning it for completeness.

---

### Post by Fooshnik on 2011-01-28
I had a lot of issues with permission inheritance, both wanted and unwanted but i've been testing this for a while and come up with this. So far it's been working ok and no one seems to have access to files they shouldn't and new file permissions are being inherited correctly. 

Scenario: 

Samba share called "Secr" located on the server at /home/Secr. Share is mapped to the S:\ drive on the workstation. Owner and group Secr have rwx, Everyone has zero permissions. User Bob is not a member of the Secr group but needs rw access to the directory S:\Prj\32x\XLS (would show using windows UNC at \\server\Secr\Prj\32x\XLS). This is what I've done here:

1. Edit the smb.conf so the share looks like this:

> [Secr]
	writeable = yes
	path = /home/Secr
	force directory mode = 770
	force create mode = 770
	valid users = Bob,@Secr
	create mode = 770
	directory mode = 770

2. On the file server add Bob rx to the /home/Secr folder (see below).

3. Using Windows Explorer browse to //server/Secr. To the Prj and 32x folders, right-click, Properties, Security, Advanced, Edit, Add, add user Bob, check "Traverse" and "List folder". Apply permissions to "This Folder Only".

4. Repeat for the XLS folder, except add all permissions but "Full Control", "Change Permissions", "Take Ownership". (Even with these unchecked, Windows is still granting "Full Control" to XLS folder, must be a limitation of POSIX ACL) Apply permissions to "This Folder, Subfolders and Files". 

Bob should then be able to browse to S:\Prj\32x\XLS and write the files under it. New files under XLS should have Bob's rw permissions. Other relevant items from the smb.conf (some of these may be redundant or obsolete, things were added during troubleshooting that may not need to be there):

> # Enable a user to be admin for administration/backup
        admin users = USERNAME

# Intended to allow permissions change to non-creator of files
acl group control = yes

# Prevent unwanted permissions from being inherited
inherit acls = no
inherit owner = no
map acl inherit = no
inherit permissions = no

# Hide files people can't read or write
hide unreadable = yes
hide unwriteable = yes

One issue you'll run into is if you need to add another group to the root share with rwx you can't use Windows to modify the ACL for this, ie the \\server\Secr folder. If you want to add the Ltr group to have full control of the Secr share then first add to the samba share as follows

> [Secr]
	writeable = yes
	path = /home/Secr
	force directory mode = 770
	force create mode = 770
	valid users = Bob,@Secr,@Ltr
	create mode = 770
	directory mode = 770

Then use setfacl to add the Ltr group to the Secr folder. From the /home folder:

> setfacl -m g:Ltr:rwx Secr
setfacl -d -m g:Ltr:rwx Secr

The first adds the group Ltr to the Secr folder. The second adds the Ltr group to the Default Group list which allows the permissions to propagate to new folders created under Secr. Use -R to add the permissions to existing files/folders. "Getfacl Secr" should look something like this:

> # file: Secr
# owner: root
# group: Secr
user::rwx
user:Bob:r-x
group::rwx
group:Ltr:rwx
mask::rwx
other::---
default:user::rwx
default:group::rwx
default:group:Ltr:rwx
default:mask::rwx
default:other::---


To apply new permissions to existing files using Windows right-click the folder, go to "Properties", "Security", "Advanced", "Edit", and there's a check box that says "Replace all existing inheritable permissions...". Change your permissions, check that box and click Apply. This can take a while with a large amount of files. Command line is quicker:

> setfacl -R -m u:USERNAME:rwx DIRECTORYNAME
setfacl -R -d -m u:USERNAME:rwx DIRECTORYNAME


...I'm not sure if any of that makes any sense. The granularity of permissions is there but it's a lot more complicated to get where I need it than with Netware. But it can be done.

---

