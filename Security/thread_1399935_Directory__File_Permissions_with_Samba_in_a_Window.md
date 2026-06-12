---
title: "Directory / File Permissions with Samba in a Windows Domain"
date: 2010-02-06
forum: Security
---

### Post by dudemanbubba on 2010-02-06
I looked through the forum and see a lot on similar topics, but none of them specifically deal with trying to change permissions on a ubuntu server from a windows workstation.

I am adding an ubuntu server into our existing windows domain.  Our existing system is very old, but functional.  For now I am trying to pull the file serving and storage out of the mix and put it on this new server.

Our files are organized by projects in project directories.  The main file share is a directory with subdirectories for each year.

For instance:

08 Jobs
09 Jobs
10 Jobs, etc.

Inside of each of these is the list of projects for each year such as:

09001 - Test Job 1
09002 - Test Job 2, etc.

The location for the share is "/mnt/raid/Project Data".  I copied all of the data from the old server to this location. I then chmod -R 777 the entire thing and then set the "Project Data" and the subsequent "XX Jobs" directories to 775.  My Samba settings are at 777 for both files and directories.  I believe this sets the first two directories up as read/execute only and allows the network users to freely create what they need inside the project folders.

Before I added permissions, everyone would create their random folders for the day and these main directories would be cluttered with personal and unmanaged garbage.  I added permissions to these to main folders to only allow the "Administrators" and a group I created called "Project Creators" to be able to rwx.  All other "Authenticated Users" were read only.  The actual individual project directories were open for all to have rwx.  It has kept everything organized.

I had created a batch file for our secretary to simply type the project information in and it would create the directories and set the proper permissions for new projects using windows xcacls.

I have added ",acls" to the fstab and I can change the permissions on the ubuntu server directly.  I am hoping to have the same setup on the secretary's machine to set the folder permissions from a windows workstation on the ubuntu server using a batch file and xcacls or what ever utility is necessary.  I am the only one who knows anything about how to use the new server (and that knowledge is pretty fresh and limited) and I am usually not in the office to do this stuff myself.

Also, I see informatoin on the setfacl but I haven't found how to use ADS users and groups.  If anyone can point me in the right direction that would be helpful.

Any help is greatly appreciated!

---

### Post by lemming465 on 2010-02-07
There are a bunch of different ways to tie Linux into Microsoft AD, including hideously expensive enterprise scale commercial offerings such a Vintela.  In general you are going to have to fiddle with the Kerberos, Nsswitch, and Samba configurations.  In your situation I'd suggesting using the samba projects' *winbind* daemon.  The [ubuntu wiki winbind howto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") might help.

---

### Post by dudemanbubba on 2010-02-08
> In your situation I'd suggesting using the samba projects' *winbind* daemon.  The [ubuntu wiki winbind howto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") might help. 	

That's the exactly what I used.  Access from the local windows ADS works like a charm.  I am just looking for utilities to allow modification of the permissions from a Windows XP workstation.

Thanks.

---

