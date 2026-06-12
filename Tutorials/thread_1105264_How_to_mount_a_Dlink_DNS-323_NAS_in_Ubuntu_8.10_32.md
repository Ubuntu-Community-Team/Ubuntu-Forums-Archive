---
title: "How to mount a Dlink DNS-323 NAS in Ubuntu 8.10 32 bit and 64 bit"
date: 2009-03-24
forum: Tutorials
---

### Post by runes on 2009-03-24
NOTE: 
For the sake of this tutuorial we are assuming that you log in to Ubuntu 8.10 (32bit or 64 bit) with the username doej...where you see the username doej you would substitue with your username.

Rule # 1 BACKUP BACKUP BACKUP
Rule # 2 Refer to Rule # 1

What you need to know:
The ip address of your NAS  in my case and for this tutorial it is 192.168.0.40  yours may be different
The names of your folders for sharing  fir this tutorial there are two folders on my share I want to  mount within my home folder of /home/doej:
Documents 
Music 

What you need to install:
smbfs and if missing smbclient
How to install?

Click System>Administration>Synaptic Package Manager
under the Quick search type in  smbfs  and if not green check it
under the Quick search type in smbclient and if not green check it
clic apply then click apply again


Now onto the mounting of your NAS folders:

NOTE: Remember that the foldernames are CaSe sensitive so check that you use the proper case!


First step:
create file in /root called .smbcredentials
add:
username=username to log into nas
password=password to log into nas

Commands to do this:
 Click applications>accessories>Terminal
 sudo touch /root/.smbcredentials
 sudo nano .smbcredentials
 username=username to log into nas
password=password to log into nas
 press ctrl-o to save the file
 press ctrl-x to exit
 [SIZE=2]now type in  sudo chmod 600 /root/.smbcredentials[/SIZE]
 ** **

 ** Samba Configuration:**

 First thing we do is backup the original configuration file 
We start with creating a folder in your home directory called Backups  to place the original files

Click Applications>Accessories>Terminal

type in:

sudo mkdir /home/doej/Backups

Next step is to create two mount points in your home folder so that you can browse Music and Downloads within your home folder to mount your shares so  you can browse them in Places and on your desktop.  In this example we will create two folders in /home/doej called MusicNAS and DownloadsNAS so that we know the files we see are from the NAS  once again these foldernames are CaSe sensitive :

sudo mkdir /home/doej/MusicNAS
sudo mkdir /home/doej/DocumentsNAS

then type in:
sudo cp /etc/samba/smb.conf /home/doej/Backups/smb.conf

You have now made a backup of your smb file in /home/doej/Backups

sudo nano /etc/ samba smb.conf
Under the heading  #======================= Global Settings =======================
  add line :

# This allows older lanman autorization for the Dlink NAS-323

client lanman auth=yes

then press ctrl-o to save the file
press ctrl-x to exit

To fix an unmounting issue with cifs(samba) when rebooting type:
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
sudo ln -s  /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh 

Next step it to automount your shares so that they are there everytime you log in!  This required editing your fstab file...our first step is to back it up before making any changes.
** FSTAB Configuration:**

 sudo cp /etc/fstab /home/doej/Backups/fstab
You have now made a backup of your fstab file in /home/doej/Backups

Now to tell fstab to mount your shares

sudo nano /etc/fstab                                                                                        
 # /etc/fstab: static file system information. 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # /dev/sda1 
 UUID=ee64b879-124a-48a0-95ef-650fc9a1ceb7 /               ext3    relatime,errors=remount-ro 0       1 
 # /dev/sda5 
 UUID=123792b0-ea3f-4d59-8f38-a036af9435ce none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 //192.168.0.40/Downloads /home/doej/DownloadsNAS cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 
 //192.168.0.40/Music /home/doej/MusicNAS cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 
 

 **The last two lines are the ones we add manually starting with the ipaddress of your nas then the folder you want to mount then the home folder you want to mount it to.**

**Once completed you then hit CRTL-O  then CRTL-X to save and exit**
**Last step:**
**mount -a**
**This will mount your shares.**

---

### Post by dmizer on 2009-03-25
Just FYI, there is no need to edit smb.conf.  You can specify lanman auth in the cifs mount like so:
```
//192.168.0.40/Music /home/doej/MusicNAS cifs credentials=/root/.smbcredentials,[COLOR="Red"]sec=lanman[/COLOR],iocharset=utf8,file_mode=0777,dir_ mode=0777 0 0
```

---

### Post by runes on 2009-03-25
> **dmizer said:**
> Just FYI, there is no need to edit smb.conf.  You can specify lanman auth in the cifs mount like so:
```
//192.168.0.40/Music /home/doej/MusicNAS cifs credentials=/root/.smbcredentials,[COLOR=Red]sec=lanman[/COLOR],iocharset=utf8,file_mode=0777,dir_ mode=0777 0 0
```


One problem with that..in the case of the Dlink NAS 323...it still uses lanman auth..so a person who does not add that to the smb.conf will not be able to log in by browsing through Places>Network and connect to their NAS...it will only allow them to mount the predefined shares they create in fstab and only access those shares.

If they are not concerned with browsing all their folders on the NAS and just want to mount a few of them then I agree, your solution will work best.  The moment I commented out the reference to lanman in smb.conf I lost access to browsing the NAS Through Nautilus...unless there is another way?

---

### Post by chennaivennai on 2010-03-13
Folks,

         A newbie question here. I tried connecting my Ubuntu 9.10-thinkpad Z61t laptop, and followed the steps specified here. The error tells me this:

          [mntent]: line 14 in /etc/fstab is bad

        Line 14 is the only line that I've added and this error :).

        I also do not have user-name/ password set up on the DNS-323, What would my entries on the .smbcredentials look like.

        Appreciate your responses.

Thanks
CV!

---

### Post by dmizer on 2010-03-14
> **chennaivennai said:**
> Folks,

         A newbie question here. I tried connecting my Ubuntu 9.10-thinkpad Z61t laptop, and followed the steps specified here. The error tells me this:

          [mntent]: line 14 in /etc/fstab is bad

        Line 14 is the only line that I've added and this error :).

        I also do not have user-name/ password set up on the DNS-323, What would my entries on the .smbcredentials look like.

        Appreciate your responses.

Thanks
CV!

Please post the contents of your /etc/fstab. Please be sure to enclose the output in ```
 bbc markup like so
[noparse][code]/etc/fstab output
```[/noparse]

---

### Post by immoweichert on 2010-04-12
Hi, I had the same problems like chennaivennai.
I don't have a password for my NAS and I also wanted to mount the complete drive into the folder DNS-323 which shows up as the directory Volume_1. The address of my NAS is 192.168.0.199. Like chennai I got the"line .. in /etc/fstab is bad" message (relating to the last line) after entering sudo mount -a

I found a solution in the D-link forum [http://forums.dlink.com/index.php?topic=7848.0](http://forums.dlink.com/index.php?topic=7848.0)

So in my situation to mount just once I had to enter

```
sudo mount -t cifs //192.168.0.199/Volume_1 /home/immo/DNS-323 -o guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777
```

in Terminal.

To permanently mount it I added this line as the last line in fstab instead:

```
//192.168.0.199/Volume_1 /home/immo/DNS-323 cifs guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Oh yes, and I didn't enter anything into .smbcredentials as I don't have a password set up for my NAS.

It works perfectly (though I still have no idea what it all means ... been using linux and ubuntu only for a week :)) !!!!!

---

### Post by immoweichert on 2010-04-17
Its meant to be file_mode and not f ile_mode !

---

### Post by runes on 2010-04-17
> **chennaivennai said:**
> Folks,

         A newbie question here. I tried connecting my Ubuntu 9.10-thinkpad Z61t laptop, and followed the steps specified here. The error tells me this:

          [mntent]: line 14 in /etc/fstab is bad

        Line 14 is the only line that I've added and this error :).

        I also do not have user-name/ password set up on the DNS-323, What would my entries on the .smbcredentials look like.

        Appreciate your responses.

Thanks
CV!

Can you please post the line you added to your fstab?

---

### Post by chennaivennai on 2010-05-02
```
//192.168.1.5/Volume_1 /home/uthra/NAS   cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_ mode=0777       0  0
```[COLOR=#000000][FONT=Times New Roman][FONT=verdana]**immoweichert**[/FONT][/FONT][/COLOR] - The fix works! I am on the same boat, been running Ubuntu for the last 15 days on a Thinkpad z61t! 

Thanks all for the inputs.

:guitar: Chennai!

---

### Post by petit-pere on 2010-08-22
Hi,
I hope anybody can help me with my error, because I can't find my way out of this maze ;)

I actually have Ubuntu 9.10

sudo mount -a gives this error
> mount : type erroné de syst .de fichiers, option erronée, super bloc
        erroné sur //192.168.1.2/volume_1/Multimedia, codepage ou aide manquante ou autre erreur
       (pour plusieurs syst. de fichiers (nfs, cifs) vous aurez
       besoin d'un programme /sbin/mount.<type> intermédiaire)
       Dans quelques cas certaines informations sont utiles dans syslog - essayez
       dmesg | tail  ou quelque chose du genreIt seems the file system is wrong. I looked into the DNS-323 but couldn't find any information (it's Raid1 BTW)

The fstab file looks like this

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1ae62acc-1d7f-4855-97dd-eab80ba9e942 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f1274621-63e8-4010-83e9-d6467ee9bf47 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//192.168.1.2/volume_1/Systems /home/herve/NAS-Multimedia cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0Does anybody have an idea about what I'm doing wrong?

That's a lot for your precious help

---

### Post by dmizer on 2010-08-22
> **petit-pere said:**
> Does anybody have an idea about what I'm doing wrong?

That's a lot for your precious help

You will need to install smbfs. You can search for the package "smbfs" in synaptic or install it with the following command:
```
sudo apt-get install smbfs
```

---

### Post by petit-pere on 2010-08-22
thanks a lot dmizer ... it solves the problem ...  sorry for disturbing ...

---

### Post by immoweichert on 2010-09-18
Must not forget smbfs ....just stumbled about this again whilst setting up a new system ... now I know what I'd forgotten :)

---

### Post by oyeindia on 2012-10-23
I have 12.10, and I just followed all instructions so far.

mount -a gave me the following error:
```
mount: wrong fs type, bad option, bad superblock on //192.168.27.7/Media/Music,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I realised I did not have smbfs, and when I tried to install it, I got this:
```
ram@frodo:/$ sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  cifs-utils

E: Package 'smbfs' has no installation candidate

```

So I installed cifs-utils instead.

This time, mount -a gives me this error:
```
mount error(2): No such file or directory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Any suggestions?

---

