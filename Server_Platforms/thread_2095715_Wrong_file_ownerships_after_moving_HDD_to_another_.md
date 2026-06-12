---
title: "Wrong file ownerships after moving HDD to another computer"
date: 2012-12-17
forum: Server Platforms
---

### Post by Kljuka on 2012-12-17
I've installed Ubuntu server on Computer1 a while ago and added an additional Hdd to it.

Now I want to create a backup server of Computer1. I've installed new Ubuntu server on Computer2 with the same packages, and users. The last step is to move the Hdd from Computer1 to Computer2.

And here is the problem:
the users on Computer2 were not created in the same sequence as on Computer1 so when I mount the Hdd to Computer2 the files have wrong ownerships (www-data becomes mysql, etc.).

Is there a script to change ownersip of all files of particular user to another user? Or is there a better way of moving files to another computer?

---

### Post by koenn on 2012-12-18
changing ownership is pretty easy, sometimes 1 command is enough (man chown). 
It's also tricky. There's quite a few threads on these forums about "I changed althe ownership/file permissions and now my computer won't boot"

You're going to have to look very carefully at your data disk and carefully decide the ownership of each relevant directory.

With a  naieve approach like "switch everything from www-data to mysql, and from mysql to www-data" you risk getting stuck half-way trough.


The only way you could have avoided this, I think, is by making sure your UIDs on both computers match up. Depending on the UIDs involved, that may be more tricky than changing ownership afterwards.

---

### Post by SeijiSensei on 2012-12-21
If the numerical UIDs and GIDs on the old drive reference different users on the two machines, you'll be in for some tedious work.  However if the overlap is manageable, or there's no overlap at all, the easiest solution by far is to merge the user entries in the two machines' /etc/passwd and /etc/group files.  You'll also need to merge /etc/shadow which contains the password hashes.  Make sure you preserve all the correct permissions on these files: 644 for passwd and group and 600 for shadow, with root as owner and group of course.

---

### Post by CharlesA on 2012-12-21
> **SeijiSensei said:**
> If the numerical UIDs and GIDs on the old drive reference different users on the two machines, you'll be in for some tedious work.  However if the overlap is manageable, or there's no overlap at all, the easiest solution by far is to merge the user entries in the two machines' /etc/passwd and /etc/group files.  You'll also need to merge /etc/shadow which contains the password hashes.  Make sure you preserve all the correct permissions on these files: 644 for passwd and group and 600 for shadow, with root as owner and group of course.

+1. I ran into this when I decided to change the UID and GID a while ago when I reinstalled my server. It was a bit of a pain to get the permissions and ownership set up again, but it wasn't too bad.

---

### Post by Kljuka on 2012-12-21
Thanks for your help.
If I understood correctly, this is what I should do:

[LIST=1]
[*]Run Ubuntu Live CD (so I have access to all files) on the newly installed system (Computer2)
[*]Change UIDs and GIDs of all files on the new system to be matched with the ones of the old system. For example if UID:GID changed from 1300:1301 to 1400:1401 I would run:
```
cd /
chown -cR --from=1300:1301 1400:1401 *
```
[*]Copy /etc/passwd, /etc/group and /etc/shadow from old system to the new system (and make sure the permissions stay the same)
[*]Attach the old Hdd to the new system. Everything should work :)
[/LIST]
Here are my remaining three questions:

[LIST=1]
[*]Will the above work?
[*]Is it OK to just move /etc/shadow file because it contains encrypted passwords? Will the copied user passwords work on the new system?
[*]What about /etc/gshadow? It's not empty. What's the purpose of this file and should I also transfer it?
[/LIST]

---

### Post by SeijiSensei on 2012-12-22
I just edit /etc/passwd, group, and shadow in a text editor.  If user 1003 on one machine is now user 1002, I just change the ID's in passwd and group accordingly.  For reorganizing a bunch of accounts that's a lot faster and cleaner than running a bunch of chown/chmod commands.  /etc/shadow is organized by username so you just have to make sure the combined shadow file has the complete set of users with unique entries for each one.

---

### Post by koenn on 2012-12-22
> **SeijiSensei said:**
> I just edit /etc/passwd, group, and shadow in a text editor.  If user 1003 on one machine is now user 1002, I just change the ID's in passwd and group accordingly.

Hm. I thought about something like that as well, but I didn't see how that would work in this case.

OP speaks of daemon accounts such as www-data and mysql.
Also, he's moving a disk, so on the new system, one disk will have ownership with UIDs as on computer1, another disk will have computer2 UIDs. 
Whatever he sets as a UID in /etc/passwd, it's going te be wrong for the files on one of the disks, no ? 

say,
dsk 1, /var/something/* , owned by uid 1004 ; 1004 = mysql
disk2,  /srv/something/*,  owned by uid 1004 ; 

disk 2 is the foreign disk, where 1004 refered to www-data, so by migrating the disk, ownership of /srv/something/ switched from www-data to mysql. 
Giving  UID 1004 to www-data will fix that, but will cause mysql to lose ownership of /var/somthing, which is possibly bad. 


So what changes in /etc/passwd would fix this ?  

Or maybe I'm misreading the OP's problem ...

---

### Post by koenn on 2012-12-22
> **Kljuka said:**
> 
[*]Will the above work?


I don't see why your approach includes both chown **and** juggling passwd and shadow files.


The one thing you need to look out for is this:
say you chown  from 1300 to 1400
say you also need to change files from 1400 to something else
how do you distinguish between 'real 1400' and '1400 that were 1300 previously' ? 


That's the reason it's hard to give a recipe for your problem; I think it requires a close look at exactly what files and owners need to be changed, and carefully thinking true the consequences of your consecutive changes.

---

### Post by SeijiSensei on 2012-12-22
> **koenn said:**
> Hm. I thought about something like that as well, but I didn't see how that would work in this case.

OP speaks of daemon accounts such as www-data and mysql.
Also, he's moving a disk, so on the new system, one disk will have ownership with UIDs as on computer1, another disk will have computer2 UIDs. 
Whatever he sets as a UID in /etc/passwd, it's going te be wrong for the files on one of the disks, no ? 


Not if the source and target are from the same distribution.  The system users remain the same across Ubuntu machines.  Mixing Ubuntu/Debian with RedHat-flavored distros like CentOS and Fedora will encounter problems in the accounts assigned to daemon processes.  The RH accounts also begin at UID=500 rather than UID=1000.  If you have fewer than 500 accounts on the RH machine, none of which are duplicated on the new Ubuntu/Debian machine, you can just merge them together.  There's nothing intrinsic in the decision to start numbering at 500 or 1000.

---

### Post by koenn on 2012-12-22
> **SeijiSensei said:**
> Not if the source and target are from the same distribution.  The system users remain the same across Ubuntu machines. 
Yeah, I was wondering whether that is supposed to be the case. 

But then moving a disk across machines would not affect ownership of daemon-owned data files at all, as tha UIDs would already match. 

Yet, in the OP, I read
>  files have wrong ownerships (www-data becomes mysql, etc.).

---

### Post by Kljuka on 2012-12-22
>                      Originally Posted by **SeijiSensei**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12417488#post12417488")                 
                 *Not if the source and target are from the same distribution.  The system users remain the same across Ubuntu machines.*
No, unfortunately they are not the same. Even though I installed Ubuntu 10.04 server on both machines following (almost) the same procedure, the UIDs of system users are different. I probably didn't install all the packages in the same order. For example:
mysql (UID): 106 -> 104
clamav (UID): 110 -> 106 (so mysql data on Comp1 is owned by clamav on Comp2)
etc.

> I don't see why your approach includes both chown **and** juggling passwd and shadow files.I want to match UIDs and GIDs on both machines. To do that I first need to copy them (passwd, group, shadow) from Comp1 to Comp2. Afterwards I need to change ownerships of the files on Comp2 to match the changes in passwd, group and shadow files.
That way I will also be able to move the HDD in the future without any needed adjustments because the UIDs and GIDs will be the same on both machines (unless I add new users).

> The one thing you need to look out for is this:
say you chown  from 1300 to 1400
say you also need to change files from 1400 to something else
how do you distinguish between 'real 1400' and '1400 that were 1300 previously' ? Very good point. Hmm... I could use a temporary random UID and use it as an intermediary:
1300 -> 1500(temporary UID)
1400 -> 1300
1500 -> 1300
I just tried it and the temporary UID doesn't even have to belong to any user in passwd file.

---

### Post by volkswagner on 2012-12-23
I think from reading this thread one can gather this is not a pretty situation. 

I'm wondering how many users are actually impacted.  You say this is a second drive added after install.  What type of data is stored?

How many users are owning files on this drive?  A recursive ls may show you how many users own files.

Output to a text file for easy reading/query.

```
ls -lR /mnt/secondhd > ownership.txt
```

I think chmod owner:group of the second drive should be all that is needed if this system were to replace the original.  

If this second drive needs to move from machine to machine, I would suggest a reinstall of your backup server.  Create an image of the primary disk of system 1 using something like dd or clonezilla.  In my opinion this will be a better starting ground and likely less work.

---

### Post by fdrake on 2012-12-23
> **Kljuka said:**
> I've installed Ubuntu server on Computer1 a while ago and added an additional Hdd to it.

Now I want to create a backup server of Computer1. I've installed new Ubuntu server on Computer2 with the same packages, and users. The last step is to move the Hdd from Computer1 to Computer2.

And here is the problem:
the users on Computer2 were not created in the same sequence as on Computer1 so when I mount the Hdd to Computer2 the files have wrong ownerships (www-data becomes mysql, etc.).

Is there a script to change ownersip of all files of particular user to another user? Or is there a better way of moving files to another computer?
maybe i missunderstood the issue but instead of installing ubuntu on pc 2,why did't you copy the / partition from pc1 to pc 2?? mybe with dd with a live cd, so that all the conf files and user/group id are all the same?
and then you can mount the back up files easily.

---

### Post by SeijiSensei on 2012-12-23
> **Kljuka said:**
> No, unfortunately they are not the same. Even though I installed Ubuntu 10.04 server on both machines following (almost) the same procedure, the UIDs of system users are different.

That's terrible packaging if true, and another reason for me to continuing running only CentOS on servers.  The "apache" user is always UID 48 on RedHat-flavored distributions no matter when it is installed.  

Can anyone else confirm this?  If so, there should be a bug filed against the server version to correct this problem.

---

### Post by Kljuka on 2012-12-23
> maybe i missunderstood the issue but instead of installing ubuntu on pc 2,why did't you copy the / partition from pc1 to pc 2??Unfortunately the Comp1 is a server that must always stay online. Comp2 will be it's backup in case of Comp1 failure. That's why I need to move all those files (and hdd). 
As I understand I can't use dd or Clonezilla to clone mounted system.

> The "apache" user is always UID 48 on RedHat-flavored distributions no matter when it is installed.  I checked on 5 of my Ubuntu computers. The Apache (www-data) has a consistent UID of 33. But other processes that are UID 102+ don't.: postfix, sshd, mysql, ntp. It seems to me they get it based on the time they get installed. I don't know whether this is a bug or not.

Thank you all for your help. You've shown me a way to configure my backup server. It's not the easiest solution but it should work (and hopefully this posts will also be useful to others).

---

### Post by Kljuka on 2012-12-23
> I'm wondering how many users are actually impacted.  You say this is a  second drive added after install.  What type of data is stored?This second drive contains Apache www-data and is mounted to /var/www. Apache is configured to use mpm-itk which forces separate UID:GID for each user. So there are quite some users/groups.

Slightly off the topic quiestion:
I was wondering if I can manually create a new user on Ubuntu by only adding an appropriate line to passwd, group and shadow files without using useradd command?

Do you think there is a better way to create a clone of a live server than fresh-installing it, changing UIDs and ownerships to be the same as on the original server and afterwards copying the data to it?

---

### Post by fdrake on 2012-12-23
> **Kljuka said:**
>  Do you think there is a better way to create a clone of a live server than fresh-installing it, changing UIDs and ownerships to be the same as on the original server and afterwards copying the data to it?

if you cannot copy the partition / i'd chande the UID and GID (of the user that i need)of the files contained in the backup of pc-1.
```

find /media/mybackup -mount -user UID-of-pc-1 -exec chown UID-of-pc-2  {} \;
find /media/mybackup -mount -group GID-of-pc-1 -exec chgrp newgroup GID-of-pc-2 {} \;

```

change the uid and the GID of the files in the back up to the uid & gid of the system in pc-2. You should run the command with a live section (it is adviced not to be logged as the old/new user while doing it.)

reference [http://blogging.dragon.org.uk/index.php/mini-howtos/howto-change-the-uid-and-gid-on-files](http://blogging.dragon.org.uk/index.php/mini-howtos/howto-change-the-uid-and-gid-on-files)

---

### Post by volkswagner on 2012-12-23
> **Kljuka said:**
>  ...

Do you think there is a better way to create a clone of a live server than fresh-installing it, changing UIDs and ownerships to be the same as on the original server and afterwards copying the data to it?

You can use dd as previously mentioned.  I have applied dd image to a live system and rebooted into the new system.  It is very powerful. Here is a good start on [learning some dd magic]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/").

After applying dd to a new drive you may have some minor tweaks such as fixing ../persistent-net-rules (fix or remove mac address from old system), ../fstab (fix/change uuids and mount points), and possibly Grub 2 may need to be reinstalled to find correct disk uuid.

---

