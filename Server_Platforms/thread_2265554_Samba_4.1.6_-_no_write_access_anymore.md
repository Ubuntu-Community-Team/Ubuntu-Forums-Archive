---
title: "Samba 4.1.6 - no write access anymore"
date: 2015-02-16
forum: Server Platforms
---

### Post by geohei on 2015-02-16
Hi.

I copied my Ubuntu 12.04 Samba (3.6.3) config to my new Ubuntu 14.04.1 machine, which uses Samba 4.1.6.
The server is a standalone server. Samba 3.6.3 security was "security = user".

Initial testing of Samba 4.1.6 revealed that I could not access shares in write mode from a Windows 7 machine (as Administrator), which was possible with Samba 3.6.3.

I kept all settings in smb.conf to their default values.

Here an example of such a share (etc/smb.conf).

```
[global]
workgroup = testgroup
server role = standalone server
[raid6]
        path = /mnt/raid6
        valid users = Administrator
        write list = Administrator
        force user = root
        force group = root
        create mask = 0644
```
What did I miss?

---

### Post by darkod on 2015-02-16
Something similar happened to me after upgrading 12.04 to 14.04. I don't know if it's the correct way but I solved it by using the original smb.conf and just copying into it the parts I need. Don't replace the whole smb.conf file. Try if that works.

---

### Post by geohei on 2015-02-16
That's what I did as well right from the beginning. I took the original Samba 4.1.6 config, modified the "workgroup =" and added the shares. All this manually. Nevertheless it didn't work.

However I noticed that the "security =" option is missing in the Samba 4.1.6 smb.conf file. Adding "security = user" doesn't generate an error (testparm), but it doesn't make Samba 4.1.6 behave like 3.6.3 either. If I try to access the share in the OP (raid6) from my Windows 7 machine, I get the credetials authentification window. So something must be wrong on this level (I believe ?!). The user "Administrator" is generated as follows on Ubuntu:

```
root@gan:~# useradd --no-create-home -s /usr/sbin/nologin Administrator
root@gan:~# passwd Administrator
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@gan:~# smbpasswd -a Administrator
New SMB password:
Retype new SMB password:
Added user Administrator.
```

Is this the correct way to create a Samba user for my Windows 7 access?

Is "security = user"  still a valid option of Samba 4.1.6 configuration?
If yes, is this option in conflict with "server role = standalone server"?

---

### Post by geohei on 2015-02-16
I found the problem, but not the solution. It's ...

```
...
        force user = root
...
```
If I subsititude "root" with "Administrator" (or any other valid name), I have write access, but the user of written directories/files is of course "Administrator" and not "root" (as desired).
"force group = root" works fine!

I didn't use the option "invalid users =".
If I use "valid users = Administrator, root", it still doesn't work!

Samba 3.6.3 behaviour was for sure different!

Could this be a bug?

---

### Post by darkod on 2015-02-16
Not sure. It all depends how your folder permissions are set on linux level too. That's important for sharing.

Why would you force root user at all? root is root and should be left alone. If you want a user to be forced but not Administrator, simply create any username that you wish. Leave root for the system tasks.

For example create user shared (by default that creates shared group too). Set the folders permissions to 775 or similar, and add Administrator to group shared so it should have RW access.

You can do it in any way you like, it simply depends which user/group you are forcing on the shares, and the folders linux permissions.

---

### Post by geohei on 2015-02-16
It's apparently a known issue, though I didn't see the word "BUG" yet.
[http://www.google.lu/?gws_rd=ssl#q=samba4+%22force+user+%3D+root%22]("http://www.google.lu/?gws_rd=ssl#q=samba4+%22force+user+%3D+root%22")

My folder permissions are 755 and file permissions are 644 with root:root on everything.

Yes, I know about the security considerations regarding root, but that's the way it was setup and worked for Samba 3.6.3. I'd like not to touch this at this time. My aim is to get Samba 4.1.6 to behave like 3.6.3 in this respect. Strange it's not reported more often. Also I'd like to know how to circumnavigate it and to know if it's a bug or some kind of feature (as per design).

---

### Post by darkod on 2015-02-16
It could be a bug, it could be that samba or ubuntu developers simply decided not to allow root to be forced on the shares.

Under the assumption that this force user option does not work the same as in 3.6, it's logical that Administrator would not have W access since your permissions are 755 as you say, which means only the owner user (root) has W access. The owner group and the rest of users have only R access.

That's why I suggested 775 (for files 664), and adding Administrator to the group that owns the files. In that case you don't even need to force any user, Administrator will have W access. Of course in such case new files will probably appear with owner Administrator. If you want to control that behavior you need to use force user, but I still would not use root.

Samba 4.1.6 is not required to behave identical to 3.6.3 so maybe this is one of the things they don't do in the same way. Bug or no bug (intentionally)...

---

### Post by volkswagner on 2015-02-16
Could this be a UID/GID issue between the two systems?  Is /mnt/raid6 data from the previous system (possibly copied via rsync)?
Have you tried to chown root:root /mnt/raid6 and possibly on folder deepter, chown root:root /mnt/raid6/foldername?

---

### Post by geohei on 2015-02-16
> **darkod said:**
> It could be a bug, it could be that samba or ubuntu developers simply decided not to allow root to be forced on the shares.
Then (if decided by devels) it would/should be published and found on Internet. I didn't find any indication in that direction.

> **darkod said:**
> Under the assumption that this force user option does not work the same as in 3.6, it's logical that Administrator would not have W access since your permissions are 755 as you say, which means only the owner user (root) has W access. The owner group and the rest of users have only R access.
User "Administrato"r is supposed to be user "root" (or more general, the Samba authentificated user takes the role of the "force user ="), hence 755 is be sufficient to access the shares in W mode as desired (and implemented by Samba 3.6.3). Besides this, "write group =" also works like this, even in Samba 4.1.6.

> **darkod said:**
> That's why I suggested 775 (for files 664), and adding Administrator to the group that owns the files. In that case you don't even need to force any user, Administrator will have W access. Of course in such case new files will probably appear with owner Administrator. If you want to control that behavior you need to use force user, but I still would not use root.
That works, but is not as what I want to have. The intention of my posting was to ask if someone knows why "write user =" (1.) behaves differently in 4.1.6 vs. 3.6.3, (2.) if it is a known bug in 4.1.6, (3.) how to circumnavigate this bug (if it is one), (4.) if I possibly missed something in the doc/config.

> **darkod said:**
> Samba 4.1.6 is not required to behave identical to 3.6.3 so maybe this is one of the things they don't do in the same way. Bug or no bug (intentionally)...
The Google link shows some hits on this problem (so, I'm apparently not alone) and the "force group =" option works properly as per man pages and as 3.6.3 did.

> **volkswagner said:**
> Could this be a UID/GID issue between the two systems? Is /mnt/raid6 data from the previous system (possibly copied via rsync)?
Have you tried to chown root:root /mnt/raid6 and possibly on folder deepter, chown root:root /mnt/raid6/foldername?
No, it's the same system. No rsync or uid/gid issues, since "ls -ln" shows the same uid/gid number (0/0). Also ... the Google hits (see posting further up) show that other users also report the "force user =" doesn't work as per 3.6.x any more.

Thanks.

---

### Post by geohei on 2015-02-16
I found the solution ... !!!

The shares' section option "valid users =" needs to include "root", then all works as per 3.6.3.

Thanks for the replies which kicked me in the right direction!

---

### Post by bab1 on 2015-02-17
> **geohei said:**
> That's what I did as well right from the beginning. I took the original Samba 4.1.6 config, modified the "workgroup =" and added the shares. All this manually. Nevertheless it didn't work.

However I noticed that the "security =" option is missing in the Samba 4.1.6 smb.conf file. Adding "security = user" doesn't generate an error (testparm), but it doesn't make Samba 4.1.6 behave like 3.6.3 either. If I try to access the share in the OP (raid6) from my Windows 7 machine, I get the credetials authentification window. So something must be wrong on this level (I believe ?!). The user "Administrator" is generated as follows on Ubuntu:

```
root@gan:~# useradd --no-create-home -s /usr/sbin/nologin Administrator
root@gan:~# passwd Administrator
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@gan:~# smbpasswd -a Administrator
New SMB password:
Retype new SMB password:
Added user Administrator.
```

Is this the correct way to create a Samba user for my Windows 7 access?

Is "security = user"  still a valid option of Samba 4.1.6 configuration?
If yes, is this option in conflict with "server role = standalone server"?

This does not appear to be a Samba problem specifically.  Most probably this is a file system configuration problem.  Samba can only grant access and read write permissions at the application level.  If you have no access at the file system level (e.g. EXT4) then there is no access available to to the user.

What are the fle system ownership and permissions for /mnt/raid6?```
ls -l /mnt/raid6

and 

/mnt
```

There is no functional difference other than a few very technical options between Samba (smbd) v3 and Samba (smbd) v4.  I use the shares I created 5 years ago on my Samba v4 servers.

---

### Post by bab1 on 2015-02-17
> **geohei said:**
> I found the problem, but not the solution. It's ...

```
...
        force user = root
...
```
If I subsititude "root" with "Administrator" (or any other valid name), I have write access, but the user of written directories/files is of course "Administrator" and not "root" (as desired).
"force group = root" works fine!

I didn't use the option "invalid users =".
If I use "valid users = Administrator, root", it still doesn't work!

Samba 3.6.3 behaviour was for sure different!

Could this be a bug?
I know of no bug in this area.

The parameter ```
 force user = root
```... is not a very good solution for shared files.  What would the reason be for having files and directories owned by root to be shared (a very bad idea IMO).  Unless you are administrating the local systems files or directories you shouldn't really be logged in as root anyway.

---

### Post by bab1 on 2015-02-17
> **geohei said:**
> It's apparently a known issue, though I didn't see the word "BUG" yet.
[http://www.google.lu/?gws_rd=ssl#q=samba4+%22force+user+%3D+root%22]("http://www.google.lu/?gws_rd=ssl#q=samba4+%22force+user+%3D+root%22")

My folder permissions are 755 and file permissions are 644 with root:root on everything.

Yes, I know about the security considerations regarding root, but that's the way it was setup and worked for Samba 3.6.3. I'd like not to touch this at this time. My aim is to get Samba 4.1.6 to behave like 3.6.3 in this respect. Strange it's not reported more often. Also I'd like to know how to circumnavigate it and to know if it's a bug or some kind of feature (as per design).

Are you aware that on Ubuntu the root users umask (used in creating files and directories) is different from the mortal (human) user?  The mortal user's umask is 0002. This provides the user with 0775 permissions on directories and 0664 permissions on files that are created by that user.  The root user has a umask of 0022 and therefore the permissions are 0755 on directories and 0644 on files.

This in effect means you can never share the files when using a common group.  When you share files with a common group it doesn't matter what user (other than the root user) creates the directory or file.

The different default umask is set by Ubuntu.  Both Samba v3 and Samba v4 act the same in this respect.

---

### Post by bab1 on 2015-02-17
> **geohei said:**
> User "Administrato"r is supposed to be user "root" (or more general, the Samba authentificated user takes the role of the "force user ="), hence 755 is be sufficient to access the shares in W mode as desired (and implemented by Samba 3.6.3). Besides this, "write group =" also works like this, even in Samba 4.1.6.
The user Administrator is not the root user.  The user Administrator is no different from any other user on a Linux system.  You can make the root user act on the behalf of a user however.  Remember the umask limitation.  This is the *write list = * (there is no write group) allows Samba users to have write permissions at the Samba application level, but not if the Linux file permissions are read only.> 


That works, but is not as what I want to have. The intention of my posting was to ask if someone knows why "write user =" (1.) behaves differently in 4.1.6 vs. 3.6.3, (2.) if it is a known bug in 4.1.6, (3.) how to circumnavigate this bug (if it is one), (4.) if I possibly missed something in the doc/config.



The Google link shows some hits on this problem (so, I'm apparently not alone) and the "force group =" option works properly as per man pages and as 3.6.3 did.


No, it's the same system. No rsync or uid/gid issues, since "ls -ln" shows the same uid/gid number (0/0). Also ... the Google hits (see posting further up) show that other users also report the "force user =" doesn't work as per 3.6.x any more.

Thanks.
All of these work arounds are just causing you more problems and will continue to cause you problems.  The easiest way is to solve this for the long term is to correctly configure the Linux file system that you want to share and then create the share.  In that way you and any other user will have complete access to all the files.

It is also advisable to make sure that all Linux (and therefore Samba users) have consistent UID/GID's across multiple Linux hosts.  By default the command add user will select the next available uid/gid starting at 1000.  This is the Debian standard.  If you use useradd the default is the next available UID/GID starting at 500 if I'm not mistaken.  Not the Debian standard.  In any event you should always control the UID/GID for a particular user when you are not using centralized user management.

---

### Post by bab1 on 2015-02-17
> **geohei said:**
> I found the solution ... !!!

The shares' section option "valid users =" needs to include "root", then all works as per 3.6.3.

Thanks for the replies which kicked me in the right direction!
Not a solution.  It will work for now, but you should really learn to configure the system correctly without resorting to using the root user to do the work a regular user should be doing.

On the other hand, it is your system and you can run it as you please.

---

