---
title: "Sharing folders from second HD"
date: 2017-01-03
forum: Ubuntu/Debian BASED
---

### Post by jesus-freak on 2017-01-03
I am running KDE Neon which is just ubuntu running a KDE desktop similar to Kubuntu. The one big difference is that KDE Neon  doesn't come with a lot of software pre-installed so a lot of the programs that come with Ubuntu or Kubuntu might not be on Neon. Here is my question. I have a solid sate drive that I use to run my OS. Then I have a second larger HDD to store music and movies. This second HDD is not a USB external drive, it is installed internally. I want to share some folders from my second HDD to other Ubuntu computers sharing my internet connection. Can someone tell me the easiest simplest way to accomplish this?

---

### Post by Keith_Helms on 2017-01-03
Network File System (NFS)

[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)

A more complicated option would be Samba, which would let you share it with Windows computers if you wanted.

---

### Post by jesus-freak on 2017-01-03
This is the simplest way? I have to say I didn't really understand this part at all  
> You can configure the directories to be exported by adding them to the /etc/exports file. For example:

/ubuntu  *(ro,sync,no_root_squash)
/home    *(rw,sync,no_root_squash)
You can replace * with one of the hostname formats. Make the hostname declaration as specific as possible so unwanted systems cannot access the NFS mount.

To start the NFS server, you can run the following command at a terminal prompt:

sudo systemctl start nfs-kernel-server.service

---

### Post by Keith_Helms on 2017-01-03
It does require a bit of tinkering with config files, doesn't it.  Here's a more verbose explanation:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

An alternative would be to use Samba:

[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

---

### Post by jesus-freak on 2017-01-03
I have not had good luck with samba in the past but I tried it again. I installed samba and all required packages. I installed samba kdenetwork-filesharing. Now I open Dolphin, right click on a folder, click share, select to share the folder. But then when I go to networks, samba shares, it says "Unable to find any workgroup in your network". What am I missing here. A few years ago it seemed like it was so simple in any Ubuntu based system. You could set up a simple share just by right clicking a folder and selecting share. Now I can't get these things to share to save my life.

---

### Post by jesus-freak on 2017-01-03
I just don't understand what I am doing wrong here. I've been trying this thing for hours now.  Everything seems to be installed and working but I select to share a folder and it doesn't show up as being shared.

---

### Post by oldfred on 2017-01-03
Moved to Debian Based sub-forum.

---

### Post by Morbius1 on 2017-01-03
I know I'm going to regret getting involved with this since I hate KDE and wouldn&#8217;t know neon if I tripped over it but .....
> But then when I go to networks, samba shares, it says "Unable to find any workgroup in your network". 
You are using Windows name resolution on a desktop environment that really doesn't handle it very well in an all Linux network. Use a Linux mechanism instead:

** Make sure avahi is running on both systems:
```
sudo service avahi-daemon status
```
** THen run this command on the KDE box to find the exact host name of your box:
```
hostname
```
** Then on the Ubuntu box open a terminal and run:
```
nautilus smb://hostname.local
```
[COLOR=#0000cd][I]Where "hostname" is the host name you have on the KDE box - and don't forget the ".local" at the end.

[/I][/COLOR][COLOR=#000000]If you have any further issues post the output of these commands so the folks here know how you are set up:
```
testparm -s
```
```
net usershare info --long
```
[/COLOR]

---

### Post by yancek on 2017-01-03
Are you trying to set up NFS or Samba.  The example you posted from the link above is just an example and I have posted one below from my computer.

> /mnt/data 192.168.0.0/24(no_root_squash,sync,secure,no_subtree_check,rw) 

The first part "/mnt/data" is the directory mount point of the partition you want to share.  The second part, the '192...) is the IP address  of your computer network and yours may be different.  You can get it with the command:  sudo route -n.  Everything in parenthesis are just different options and you can select what you want.  If I remember correctly, you cannot have spaces in the parenthetical space.  Once you have created the directory for the mount point and edited the /etc/exports file, you need to export with this command:  sudo exportfs -ra (the ra part are options I use, there are different options depending upon what you want)  This would be done on the main/server computer.

You need to install the software mentioned in the first part of the link on the server, the computer you want to share and the nfs-client software on the computers you want to access the share from.  On the client systems, you will need an entry similar to the one below and after making the changes, you need to re-boot or mount the partition.  The example below will access /mnt/data on the server computer from another computer which has a mount point (directory) created on the client of /mnt/HP.   

> 192.168.0.2:/mnt/data /mnt/HP nfs rsize=8192,wsize=8192,nosuid,soft 0 0

---

### Post by jesus-freak on 2017-01-03
okay, Morbius1, I did as you suggested and it worked....sort of. I had selected to share my downloads folder from the SSD that has my OS on it. And I selected a folder from my my second internal HDD that has all my music and movies on it. The downloads folder from the SSD shared fine but the folder from the HDD gave me this message."Unable to access location, permission denied"```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: The 'netbios name' is too long (max. 15 chars).

Server role: ROLE_STANDALONE

# Global parameters
[global]
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb


[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```

```
 net usershare info --long
[Downloads]
path=/home/justdrea/Downloads
comment=
usershare_acl=Everyone:R,Unix User\justdrea:F,
guest_ok=y

[Movies]
path=/media/justdrea/51AA03BC771A6C6E/Movies
comment=
usershare_acl=Everyone:R,Unix User\justdrea:F,
guest_ok=y

```

---

### Post by Morbius1 on 2017-01-04
Both of your shares allow guest access so what I would recommend is this:

Edit /etc/samba/smb.conf and right under the "workgroup = workgroup" line add the following:
```
force user = justdrea
```
Then restart smbd:
```
sudo service smbd restart
```

[I]Reason: 

The /media/$USER directory ( in your case /media/justdrea ) is created by the system and assigned special permissions that prevent anyone other than $USER ( justdrea ) from gaining access to what is beyond it. The samba client user is not justdrea so samba will allow the user access but Linux permissions will prevent it. "force user = justdrea" will make the guest user appear to be "justdrea" ( at least for your samba shares ) so that they may be granted permission.

[/I][COLOR=#0000cd]**BTW**[/COLOR], testparm gave you one reason why your original setup couldn't find your machine:
> WARNING: The 'netbios name' is too long (max. 15 chars).
The old deprecated Windows name resolution mechanism which accounts for the majority of Samba support questions in Linux forums requires that your host name be 15 characters or less in length or that you set the netbios name to that size in smb.conf.

When you use the "hostname.local" method that restriction no longer applies because you are now using Linux standards where the host name can be 32 characters long - or maybe 64 - don't remember right now.

Anyhoo ... I would stick with the hostname.local method. It's faster and more reliable.

---

### Post by jesus-freak on 2017-01-04
Morbius1, you're a genius!! Oh my gosh I've been playing with this for so long and now it's working properly!! Thanks so much for the help.

---

