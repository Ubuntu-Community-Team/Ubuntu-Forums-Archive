---
title: "Help Noob with Permissions"
date: 2009-08-11
forum: Security
---

### Post by jet-lee on 2009-08-11
Hi .. 

Let me start by saying I am a Windows man, giving Ubuntu server a bash as my second Linux install (First was Ubuntu Desktop) ... I have managed to wade through mostly at a snails pace.. but have successfully installed the Server, Mounted NTFS Partitions, Configured PPTP access and Got a Samba Server working (partially).

The problem I am having became apparent when I tried to access the Samba shares .. I was getting "Access Denied" messages all the time .. Eventually I tried to log on to the server as the users I was trying to access with and noticed I couldnt even get access to the shares that I had mounted as root .. and this is most likely what is stopping the windows machines form accessing the Samba shares. I can log onto the Samba shares using my "superuser" log on .. so its definately working.

I tried using chmod to grant "rwx" privs to others .. but the "ls -l" doesnt update to show the permission changes ... so I think I am going about this the wrong way. To give a little info on the structure and what Im trying to achieve .. :

I have a user "jet" that is the superuser and a user "jay" that I have added .. when I sign on as "jet" I can access an NTFS drive mounted at install .. but when I log on as "jay" this mount gives me an "access denied" error.. I have tried a few variants of chmod, to allow "jay" full access to the share .. but I am getting nowhere as I have very little clue of exactly what I should be searching on .. 

I dont expect spoon feeding, butif someone could point me to a relevant link .. that would be great ..

PS .. am LOVING Linux so far .. had a full server install up and running in about 10 minutes .. the last windows server install I did took me 2 hours to configure fully .. really .. people say Linux is hard .. its actually easier than windows .. it just takes a little practice.. ;)

---

### Post by hetx on 2009-08-11
And an open mind =)

[http://www.jonathanmoeller.com/screed/?p=889](http://www.jonathanmoeller.com/screed/?p=889)

Helped me. Also in case there's no one with access to the network that you want to keep out, just set Samba up with guest user access.

---

### Post by LarsW_Tierp on 2009-08-11
You might want to give this a peek: [Howtogeek]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")

---

### Post by jet-lee on 2009-08-11
Maybe I should clarify a tad ;) .. I think my Samba setup is fine .. the problem I think relates to the Ubuntu permissions (I think - please correct me if I'm wrong) .. When I log onto the server (via putty) as "jet" .. I access the folder "/Storage" no problem .. but when I log onto the server (via putty) as "jay" .. I access the folder "/Storage" and get "Access Denied"

The purpose of the "/Storage" folder is to be shared via Samba .. which works when windows users log on as "jet" but they get "Access Denied" when logging on as "jay" ..

I have read the link you posted (thank you) .. and I have followed about 99% of those steps (still a little confused by the /user/USERNAME/test reference ??)

thanks for your help ..

---

### Post by hetx on 2009-08-11
chmod 777 -r /path/to/share

Will make it read/writeable by everyone, I know you tried a similar chmod but I'm not as good at permissions as I pretend! I don't remember the numbers for read only, a google search should give you the numbers you want.

The mkdir /home/USER/test just means "create the directory that you want to share using Samba".

---

### Post by jet-lee on 2009-08-11
running the command "sudo chmod -r 777 /Storage" results in an error ?

"cannot access 777 no such file or directory"

removing the -r allows the command to run .. but using 'ls -l' the permissions havent changed at all ??

the info stays like this ??

"drwxrwx---   1 root plugdev 12288 2009-08-06 12:01 Storage"

---

### Post by hetx on 2009-08-11
Try adding the -r at the end instead or using a big R. Some consoles seem touchier about that, although the original command works on this installation.

---

### Post by jet-lee on 2009-08-11
Have tried it with the capital R .. ran no problem .. but the problem persists for user "jay" in putty

jay@nvsserver:/$ cd /Storage
-bash: cd: /Storage: Permission denied
jay@nvsserver:/$

and the ls-l command shows no change to the permissions

---

### Post by cariboo on 2009-08-11
What are the permissions of /Storage? Where is it mounted?

---

### Post by jet-lee on 2009-08-11
> **cariboo907 said:**
> What are the permissions of /Storage? Where is it mounted?

Not sure if I understand your question ? :confused: umm .. when I installed Ubuntu it showed me all the partitions on the drive .. I selected the partition at install ??? (sorry .. Im really not that clued up with mounts and stuff .. in my world hard drives are c: d: e: etc .. ) now if I need to access it .. i go "cd /Storage" .. its not in my home forlder or anything (I think) its just there ?

Sorry if Im not being clear .. ask me to run a command that can help fill in the blanks .. and Ill gladly do it ...

---

### Post by bodhi.zazen on 2009-08-12
Well you will need to provide us with more information. 

The first problem is with basic permissions. You can not change the permissions of FAT or NTFS partitions without re-mounting them.

The second problem is you need to learn to identify your partitions. Linux does not use c:\ or d:\ We can not advise you if you do not know what partition you are having a problem with and what file system it is.

See :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

run ```
sudo fdisk -l
```

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

The next problem I believe is you are asking about file sharing / samba ? Permissions for samba are different.

[Setting Up Samba - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by jet-lee on 2009-08-12
I will read through those links provided .. 

To Clarify .. the reference to Samba was purely to give an idea of what Im trying to accomplish .. I beleive the Samba config is fine and is working .. and once I have given the user correct permissions in Linux, I am confident I will be able to apply the neccessary permissions to the Samba shares.

The problem I am having is more a lack of understanding than anything else, and unfortunately when you have very little experience, finding the information is harder than applying the required fix. 

Unfortunately people trying out Linux for the first time, can only grasp so much of what is required, and its all a little daunting at first, but the difference are the users that stick, and continue to wade through in the dark until they see the light at the end of the tunnel.

I apologize for not having enough information, but at this stage I am not exactly sure how to obtain more information as required by people trying to assist me .. I will read the links, and hopefully find what Im looking for.

Thanks for the kind assistance

---

### Post by jet-lee on 2009-08-12
this is my partition information obtained by the fdisk command

/dev/sda1   *           1        2188    17575078+  83  Linux
/dev/sda2            2551       16709   113732167+   f  W95 Ext'd (LBA)
/dev/sda3           16710       19456    22065277+   c  W95 FAT32 (LBA)
/dev/sda4            2189        2550     2907765   82  Linux swap / Solaris
/dev/sda5            2551        5737    25599546    7  HPFS/NTFS
/dev/sda6            5738        8924    25599546    7  HPFS/NTFS
/dev/sda7            8925       16709    62532981    7  HPFS/NTFS

The end result is that sda5,sda6,sda7 will hopefully be available to the new user "jay"

I hope that makes sense .. I will continue reading the links and post back if I solve my own problem...

Thanks again

---

### Post by jet-lee on 2009-08-12
Ok .. had a read .. will re-read after Ive let it simmer for a bit ...

I perhaps need to rephrase my original question for clarity.

I have a partition /dev/sda5 that I can access as root, but not as other users.

How can I mount the partition, so that it is available to users that I add to the system, and not only to the "super user"

I have tried :
mkdir /mnt/Storage                    (OK)
mount  /dev/sda5 /mnt/Storage   (OK)
chmod -R 777 /mnt/Storage         (Seems OK but permissions show as drwxrwx--- )

su jay
cd /mnt/Storage               (Permission Denied)

I hope this clarifies ???

Thanks for the assistance

---

### Post by bodhi.zazen on 2009-08-12
what file system is it ? FAT ? NTFS ? ext3 ? 

as the fstab link I gave you (I know it is a lot of new information all at once), setting permissions depends on the file system.

---

### Post by jet-lee on 2009-08-12
> **bodhi.zazen said:**
> what file system is it ? FAT ? NTFS ? ext3 ? 

as the fstab link I gave you (I know it is a lot of new information all at once), setting permissions depends on the file system.

The fstab result posted, shows the sda5 file system as ntfs ... ? not sure if you just missed that or if you are looking for something else ?

I was under the impression that editing the fstab was only to make the changes persistent .. I thought running commands would apply the changes for the current "session" ... is this not the case ?

Thanks for the reply

---

### Post by bodhi.zazen on 2009-08-12
The problem is neither fat or ntfs support permissions. Ownership and permissions are set at the time of mounting the partition and can not be changed with chmod or chown.

Since you will need to re-mount the partition with the option you want. 

You can use a gui tool, ntfs-config

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Or you can unmount it and mount it with the permissions you want

```
sudo umount /dev/sda5
sudo mount -t ntfs-3g /dev/sda5 /mnt/Storage -o uid=1000,gid=100,umask=000
```

the link I gave you on fstab has example enteries for ntfs and fat partitions if you wish. I suggest dmask and fmask.

---

### Post by jet-lee on 2009-08-13
Thank you , I will try those and post back .

---

