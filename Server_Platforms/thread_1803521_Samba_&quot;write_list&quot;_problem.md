---
title: "Samba &quot;write list&quot; problem"
date: 2011-07-13
forum: Server Platforms
---

### Post by proma on 2011-07-13
Hello.

What I want to get is samba server which has a folder with "r-x" permissions for everyone and "rwx" for a certain users. 

```

proma@Server:~$ uname -a
Linux Server 2.6.38-10-generic #46-Ubuntu SMP i686 i686 i386 
proma@Server:~$ smbd -V
Version 3.5.8

```

Here is my smb.conf
```

# Global parameters

security = user
workgroup = workgroup
netbios name = Samba
encrypt passwords = yes

[homes]
read only = no
browseable = no

[music]
path = /mnt/music
create mode = 0700
directory mode = 0700
browseable = yes
public = yes
writeable = yes
#following line should do the trick
write list = joe

```

So I created on my ubuntu-server new guy named joe. And of course gave him his brand new samba account.
```
 
sudo useradd -d /home/joe -s /dev/null joe
sudo smbpasswd -a joe

```

Now I'm going to my ubuntu-desktop and mounting the folder.
```
 
sudo mount //192.168.1.15/music ~/mnt_music -o username=joe,password=qwerty,dir_mode=0777,file_mode=0777

```

What I get is joe is a regular user like everyone else. He does not have rights to write in the folder. 


At first I thought that's because on desktop-ubuntu I'm not currently logged in as joe, so I logged in as joe. Apparently it doesn't matter because it didn't work. Also mounting with dir_mode and file_mode seems pointless, but I cannot make it work.

Am I missing something obvious?

---

### Post by proma on 2011-07-23
Seriously? No one? :(

---

### Post by Morbius1 on 2011-07-23
What are the permissions on /mnt/music?

If it's sitting there with 755 and ownership = root then it doesn't matter how you configure the share definition everyone except root will have read only access.

Either set /mnt/music at 777.

Or make the owner joe.

Or make the permissions 775, create a new group ( newgroup) , add joe to that group, and make the ownership root:newgroup.

Or some combination of the above.

BTW, that mount command can't be right since you left out the filesystem. Maybe it's a typo. Something like this seems right to me:

sudo mount.cifs //192.168.1.15/music ...........

---

