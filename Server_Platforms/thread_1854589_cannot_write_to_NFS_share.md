---
title: "cannot write to NFS share"
date: 2011-10-04
forum: Server Platforms
---

### Post by JBtje on 2011-10-04
Dear all,
 
i have tried to long, but failed each time and therefor came here, lets hope any of you can help :D
 
I have 2 servers, one having 1TB hdd space, which I want to share via NFS with the other server.
Lets call the 1 TB server the "server" and the other one the client.
 
The server has the following line in the file /etc/exports
```
/media/Data/Name/   IPADDRESS(rw,no_root_squash,async,acl)
```
 
With /media/Data/Name being a real folder, and IPADDRESS bing a real IP address.
 
The client has the following sh file, which I load wirht the root crontab each time the server reboots (@RELOAD command)
 
mount.sh:
> mount -t nfs -o rw,defaults,no_root_squash IPADDRESS:/media/Data/Name /media/Name
 
the mounting works, great :)
 
but now the problem. I cannot write to the NFS share from ANY account, but root... :|
 
Server:
> root@Server:/media/Data# ls -ln
total 8
drwxrwsr-x 7 0 0 4096 2011-10-04 21:37 Name

 
Client:
> root@Client:/media# ls -ln
total 12
drwxr-xr-x 2 0 0 4096 2011-10-04 20:23 Name

 
What do i need to do, to have other users on the Client, being able to write to the NFS too ?
 
Thank you!
Jeffrey

---

### Post by volkswagner on 2011-10-04
I'm not sure why you are using a script to mount the nfs share.  If it mounts every boot, then I'd recommend adding it to fstab.

[This NFS how-to]("http://ubuntuforums.org/showthread.php?t=249889") is bookmarked and has been my bible for nfs shares for several years now.

---

### Post by Jonathan L on 2011-10-05
> **JBtje said:**
> Dear all,
 
i have tried to long, but failed each time and therefor came here, lets hope any of you can help :D
 
I have 2 servers, one having 1TB hdd space, which I want to share via NFS with the other server.
Lets call the 1 TB server the "server" and the other one the client.
 
The server has the following line in the file /etc/exports
```
/media/Data/Name/   IPADDRESS(rw,no_root_squash,async,acl)
```With /media/Data/Name being a real folder, and IPADDRESS bing a real IP address.
 
The client has the following sh file, which I load wirht the root crontab each time the server reboots (@RELOAD command)
 
mount.sh:

 
the mounting works, great :)
 
but now the problem. I cannot write to the NFS share from ANY account, but root... :|
 
Server:

 
Client:

 
What do i need to do, to have other users on the Client, being able to write to the NFS too ?
 
Thank you!
Jeffrey

Hi Jeffrey

To me it looks like you haven't got the permissions or perhaps the groups quite right. From your examples:
```
root@Server:/media/Data# ls -ln
total 8
drwxrwsr-x 7 0 0 4096 2011-10-04 21:37 Name                      
root@Client:/media# ls -ln
total 12
drwxr-xr-x 2 0 0 4096 2011-10-04 20:23 Name
```I notice that the server says the directory is owned by group 0: are you sure the users who are supposed to write to it are in group 0?  I'd also check that you have your users and groups in sync on both systems.

Also from the fact the times and totals are different, are you quite sure you had the drive mounted?  It looks to me like the client is reporting its own /media/Name -- I'd give that a double-check.  I typically have my mountpoints be 555 or 500 root/wheel and contain a single file MOUNTPOINT so they show up easily if I make a mistake.

Lastly, I'd agree with volkswagener: is there a reason you didn't want to put the mount into /etc/fstab?

Hope that's of some use.

Kind regards,
Jonathan.

---

### Post by a2j on 2011-10-05
did you try *anonid=* option?

---

### Post by JBtje on 2011-10-05
Hey everyone,
 
Thank you for your replies!
 
> **Jonathan L said:**
> 
I notice that the server says the directory is owned by group 0: are you sure the users who are supposed to write to it are in group 0?

True, the users are NOT in group 0 (root), butm placing them in group 0 does not give them premission to write :|
Also, the folders that are in the folder "Name", DO have other groups set, in which I do have the users that need to have write premission. Also the premission of that folder is "d rwx rws r-x"
 
> **Jonathan L said:**
> 
I'd also check that you have your users and groups in sync on both systems.

Well... to be quite honest, the systems are not in sync, and that basically is the exact reason why i use two systems. This way i can have the same username on the 2 systems, but not having them interfearing with eachother.
 
as in:
The server is a NFS server, but also a Samba server.
The Client is only a Samba server, which uses the NFS server disk for storage.
Both systems have Samba, and on the Server its all working perfect. But since i need to give someone else controll over the whole Client, i preferable cannot use just one system.
 
> **Jonathan L said:**
> 
Also from the fact the times and totals are different, are you quite sure you had the drive mounted?

ah... so thats what the 7 and 2 stands for... At the time i started this topic, i already tried so many things, that i forgot to mount it again for the information :)
 
 
> **Jonathan L said:**
> 
Lastly, I'd agree with volkswagener: is there a reason you didn't want to put the mount into /etc/fstab?

Well... my reason is that if the NFS share is offline, ubuntu hangs on trying to mount the NFS share, until is succeed. (at least, thats my experiance with it :S). Not sure if i forgot a flag or so to prefent ubuntu from hanging while booting?
 
 
ok, I tried mounting the nfs via fstab with the following line
> **Client /etc/fstab**
IPADDRESS:/media/Data/Name /media/Name nfs users,rsize=8192,wsize=8192,timeo=14,intr,nosuid,gid=9000

I placed the users that need to write, in group 9000, thought i was unable to mount it like this... :|
 
 
What system checks for the premissions? is it the Server (that gives the nfs) or the Client that mounts the NFS?
Also, how do i propperly use the gid option :| and should i use it on the client, or the server? i assume the client... but with ubuntu i never know :)
 
The *anonid* options leaves me with basically the same question as gid, how to use it :S, I cannot say that i do understand the man page of mount...
 
Thank you!
Jeffrey

---

### Post by Jonathan L on 2011-10-06
> **JBtje said:**
> Hey everyone,
 
Thank you for your replies!
 

True, the users are NOT in group 0 (root), butm placing them in group 0 does not give them premission to write :|
Also, the folders that are in the folder "Name", DO have other groups set, in which I do have the users that need to have write premission. Also the premission of that folder is "d rwx rws r-x"
 

Well... to be quite honest, the systems are not in sync, and that basically is the exact reason why i use two systems. This way i can have the same username on the 2 systems, but not having them interfearing with eachother.
 
as in:
The server is a NFS server, but also a Samba server.
The Client is only a Samba server, which uses the NFS server disk for storage.
Both systems have Samba, and on the Server its all working perfect. But since i need to give someone else controll over the whole Client, i preferable cannot use just one system.
 

ah... so thats what the 7 and 2 stands for... At the time i started this topic, i already tried so many things, that i forgot to mount it again for the information :)
 
 

Well... my reason is that if the NFS share is offline, ubuntu hangs on trying to mount the NFS share, until is succeed. (at least, thats my experiance with it :S). Not sure if i forgot a flag or so to prefent ubuntu from hanging while booting?
 
 
ok, I tried mounting the nfs via fstab with the following line

I placed the users that need to write, in group 9000, thought i was unable to mount it like this... :|
 
 
What system checks for the premissions? is it the Server (that gives the nfs) or the Client that mounts the NFS?
Also, how do i propperly use the gid option :| and should i use it on the client, or the server? i assume the client... but with ubuntu i never know :)
 
The *anonid* options leaves me with basically the same question as gid, how to use it :S, I cannot say that i do understand the man page of mount...
 
Thank you!
Jeffrey

Hi again Jeffrey

I see what you're doing now: I've run systems like that where the "real" file server (with the disks) serves over NFS, a "middle" server is NFS-client-and-SMB-server, and the "real" client (with the person) is SMB client.  (Also with middle netatalk server.)  It's not terrible, but it can be a little complex.  I'm going to use real, middle, user-machine to speak of the three.

1.  Remember that NFS validates by numeric user ID, not the username.  Let's say that the users are in a group called 'people' with gid 9000,  and are called alice (1000), bob (1001), charles (1002) etc.  On the real server, alice bob charles must all be in group people; normally done in /etc/group

2.  On the middle server, alice bob and charles need to have the same user ids as on real server, but their groups don't matter much.  (Programs here could check permissions if they want to, but most don't, they just try things and see if they fail.  Macintosh Finder is an exception (or used to be) as it wants to show a unreadable folder with a different icon, and won't try opening it.)  And actually, the don't need to have the same user names, just the ids: for example, on the middle server they could be ali, robert, charlie so long as they were 1000, 1001, 1002.

3.  On the user Windows/Macintosh machines, there aren't any unix user IDs.  They'll log in on the middle server by name.  Each user mount gets (as I remember) a samba process of its own which is owned by the unix user of the appropriate name.

4.  On the real server, the shared directory needs to be 775 (or 770) root.people and needs to be set-gid.
```
chmod 775 /media/Name
chmod g+s /media/Name
chown root.people /media/Name

```These permissions exist on the real disk, so you do this on the real server.  But they will show up identically on the middle server too.  The purpose of the set-gid is to make new files and directories have the group of their parent folder, which is pretty much essential for the kind of group-shared workspace I believe you to want.
```
drwxrwsr-x 16 root people 4096 2011-10-06 09:32 /media/Name

```The 16 is the number of links to this item, for a directory it will be the number of subdirectories + 2.

5. Your fstab entry seems a ltitle overcomplex, and I'd try with the simplest
```
PADDRESS:/media/Data/Name /media/Name nfs bg,suid 0 0

```bg is the way to tell it to mount in the background if it fails
You need suid (to get setgid bits to work)

6.  Make it work from Ubuntu on the middle machine before trying anything from the user machines.  I'd test it, from the middle machine, by 
```
sudo su -l alice
umask 2
cd /media/Name
mkdir alice
date > alicefile

sudo su -l bob
umask 2
cd /media/Name
mkdir bob
date > bobfile
date >> alicefile
cd alice
date > bobfileforalice

```Everybody should be able to work on all the files and directories
Directories should all end up 775 setgid username.people, files will be 664 username.people

7.  Once that goes, check from the user machines.  You'll need to get the umask right (002 or 007, not, 022, or people won't be able to work on each other's files) in the samba configs on the middle machine.

Hope that's of use.  Let us know how you get on.

Kind regards,
Jonathan.

---

### Post by JBtje on 2011-10-06
Dear Jonathan,

 
Thank you very much for the information!
The setup is indead as you described, and 99% works now :D


 
**Real file server: /etc/passwd**
> ict: x:2000:2100:ict:/home/dimensie:/bin/bash
bes: x:2010:2100:bes:/home/dimensie:/bin/bash
rva: x:2020:2100:rva:/home/dimensie:/bin/bash
com: x:2030:2100:com:/home/dimensie:/bin/bash
eall: x:2100:2100:all:/home/dimensie:/bin/bash


 
**Middle file server: /etc/passwd**
> ict: x:2000:2100:ict:/home/dimensieict:/bin/bash
bes: x:2010:2100:bes:/home/dimensiebes:/bin/bash
rva: x:2020:2100:rva:/home/dimensierva:/bin/bash
com: x:2030:2100:com:/home/dimensiecom:/bin/bash
all: x:2100:2100:all:/home/dimensieall:/bin/bash


 
**Real & middle file server: /etc/group**
> 
ict: x:2000:ict,bes,rva
bes: x:2010:ict,bes,rva
rva: x:2020:ict,bes,rva
com: x:2030:ict,bes,rva,com,all
all: x:2100:ict,bes,rva,com,all


**Note, there is a space between the : and the x, because the forum else thinks its a smily :x**
 
I would like to see, that people that login with the account "all" or "com", are NOT able to change or delete ANY file created by the user ict, bes or rva.

 
Though,
> -rw-r--r-- 1 root ict 0 2011-10-06 18:28 blaat.txt
The file above, I can delete with the account "all" even thought the account all is not the user root, or in the group ict.

 
In order to protect the files from being deleted by some user, i do need this protection. What causes the system to not check the users for being in the right group?
 
I have mounted the disk with fstab as you said, with bg and suid as options. I do not think suid causes the check to be gone?

 
Thank you very much!
Jeffrey

---

### Post by Jonathan L on 2011-10-06
> **JBtje said:**
> Dear Jonathan,

 
Thank you very much for the information!
The setup is indead as you described, and 99% works now :D


Hi Jeffrey

Glad that helped.

Groups: I can't quite tell from your example what you're trying to achieve, but it looks funny because all the users appear to be in each others groups.

Here's the classical setup:

Password:
```
ant: x:1000:1000:Mr Ant:/home/ant:/bin/bash
bee: x:1001:1001:Mr Bee:/home/bee:/bin/bash
cat: x:1002:1002:Mr Cat:/home/cat:/bin/bash
dog:x:1003:1003:Mr Dog:/home/dog:/bin/bash
```group:
```

ant:x:1000:ant
bee:x:1001:bee
cat:x:1002:cat
dog:x:1003:dog
animals: x:9000:ant,bee,cat,dog
insects:x:9001:ant,bee
mammals:x:9002:cat,dog
```On the file server it should look like this:
```
dr-xr-xr-x root wheel /media/Name
drwxrwsr-x root animals /media/Name/animals
drwxrwsr-x root insects /media/Name/insects
drwxrwsr-x root mammals  /media/Name/mammals
drwxrwsr-x root ant  /media/Name/ant
``` ...

Now all animals can write in /media/Name/animals but only insects can write in insects/ and only mammals can write in mammals/

You appear to be trying to get it so that certain groups are excluded; these permissions only permit a (single) group.  (It's possible to use access control lists to do this, but not needed for what you're doing).

Does that help at all?

Kind regards,
Jonathan.

---

### Post by JBtje on 2011-10-06
Dear Jonathan,
 
Thats exactly what i need, thought for some reason it does not seem to work :|
For example, the user "all" is not in the group "ict", nor in the group "root"
and still, this happens:
> 
[COLOR=black]root@server:/media/Name/Dir[/COLOR]# mkdir blaat
 
root@server:/media/Name/Dir# mkdir ls -l
drwxr-sr-x 2 root all 4096 2011-10-06 23:29 blaat
 
root@server:/media/Name/Dir# mkdir chgrp root ./blaat/
 
root@server:/media/Name/Dir# mkdir ls -l
drwxr-sr-x 2 root root 4096 2011-10-06 23:29 blaat
 
root@server:/media/Name/Dir# su -l all
all@server:~$ cd /media/Name/Dir/
all@server:/media/Name/Dir/$ rmdir ./blaat/
all@server:/media/Name/Dir/$

 
so... even though UNIX user "all" is not in the group "root", it still is able to remove the file created by user root. The premission was not "o+w", so it should have no rights!?
 
Also, i mounted the data disk on the middle server with the acl command, but that did not change anything :|
 
Any idea why it does not work as it should?
 
Jeffrey
 
 
**Edit:** sigh... i should understand better what happens.... Even though the directory blaat in the above example, is set to the group "root", the directory "blaat" was created in, has groep "all" set.... so basically, to reach what i wanted, i should have set the directory "Name" to group "ict", so that only the people in that group, can edit the stuff  :D

---

### Post by Jonathan L on 2011-10-07
> **JBtje said:**
> Dear Jonathan,
 
Thats exactly what i need, thought for some reason it does not seem to work 
Any idea why it does not work as it should?
 

Hi Jeffrey

It does work as it should, though it is a little confusing sometimes.  Think of it like this: files exist entirely independently of directories, and are basically numbered, per filesystem, with an 'inode number'.  A directory is basically a file which translates a name 'foo' to an inode number such as 12345 (you can see this with ls -li), and therefore a given file could exist in multiple directories if two different names 'first' and 'second' both translate to the same inode number.  With this in mind, it should be clear that removing a file is simply removing an entry 'foo'=12345 in some directory, and so what you need is write permission on the directory.  Similarly, 'mv foo goo' is an edit on the directory, chaging foo=12345 to goo=12345.

You'll see in my example[FONT=monospace]
[/FONT]```
dr-xr-xr-x root wheel    /media/Name
drwxrwsr-x root animals  /media/Name/animals
drwxrwsr-x root insects  /media/Name/insects
drwxrwsr-x root mammals  /media/Name/mammals
drwxrwsr-x root ant      /media/Name/ant

```That the top directory Name/ has no write permission.  That means that no animals can change the structure of animals/ insects/ and mammals/, they can only write in their appropriate directories.

I hope that clarifies things a bit more.  Let me know when you get to 100%.

Kind regards,
Jonathan.

PS. acls: my advice would be don't use them at all.  They're not needed for your situation, so remove 'acl' from the fstab entry.  When you get the right setup for you groups and directories, it will be nice and simple and do everything that you need.

PPS. To finish up on links.  A filesystem is basically a box of loose files,  numbered from 1 for each filesystem, with the root directory of that  filesystem having inode number 2.  What I've described here is called  the 'hard link' mechanism, and is basic to the way all Unix-type  filesystems work.  Plain files have a link count of 1, and few will have multiple links.  Directories have a  link count of nsubdirectories + 2: it's possible but extremely rare  for it to be higher.  When a file of any kind gets a link count  of 0, it is actually deleted, and its space is available to be reused.   (Though will actually continue to exist while a process has it open, which sometimes happens by accident or design.)

Why do directories have so many links?  A directory 'foo' has an inode number just like everything else, and exists in its parent as 'foo', in itself as '.', and in each subdirectory as '..' -- managing all these links is the job of mkdir and rmdir. To properly understand it. see if you can explain the output of:
```
ls -lid /var /var/. /var/*/..
```Multiple hard links to a file are rare because we now use   symbolic links.  If you want to try them, use 'ln' without -s.  To find some on your system try
```
find / -type f -links +1
```Don't  make hard links to directories unless you want an education in fixing  filesystems :)

---

### Post by JBtje on 2011-10-12
Hey Jonathan,
 
Thank you for all the information! Reading it for a second time made me understand it clearly!
It is funny to see (and understand) that
```
 
/var
/var/.
/var/*/..

```
Indeed do have the same inode number, its logical, but still nice to realize.
 
> ...education in fixing filesystems
well *rolleye* i kinda made a mistake a few months (read 6-9 months or so) with chown :)
it turns out that you do actually need to use the {dot} at the right place in order to make it work as you need to...
 
The hard way i figured out that i needed to check my typinh when i work with chmod/own/grp
```

chmod ./ ...something...
chmod /. ...something...

```
its just not the same :)
 
I messed up the whole server, though... it kept working w/o problem... (until the next restart or so...)
Had to reïnstall everything, cuz well.. how to set all premissions of like half the filesystem? not manually at least
 
 
I have fixed all groups and set the write premission to what it needed to be and guess what, it works perfectly! :P
 
Though... one "little" problem... while opening a MS. Access file i get the response:
> The database has been placed in a state by an unknown user that prevents it from being opened or locked.
I would say this is caused due to the fact that the windows user (for example in my case "Jeffrey") does not meet the samba username (ICT), nor the ubuntu username (ICT)/ ID (some number).
 
Do you by any change have an idea of what i say above, is correct? and if there is a fix beside creating the windows uid on the samba / unix server?
 
Thank you!
Jeffrey

---

