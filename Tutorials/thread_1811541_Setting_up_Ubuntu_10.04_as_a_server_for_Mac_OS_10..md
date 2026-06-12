---
title: "Setting up Ubuntu 10.04 as a server for Mac OS 10.7 (Lion) Time Machine"
date: 2011-07-25
forum: Tutorials
---

### Post by wch on 2011-07-25
I recently upgraded my Mac to OS 10.7, at which point my Time Machine backups stopped working because Apple made some changes to the AFP client in 10.7. I did some research and figured out how to make it work. The information out there is a patchwork, so I decided to put this all in one place. If there are any errors or omissions, please let me know and I'll try to fix it!

Quick instructions first, then some detailed notes below.

- You'll need a newer version of netatalk. To install version the latest (2.2beta4,  as of this writing):
```

    sudo add-apt-repository ppa:stefanor/ppa
    sudo apt-get update
    sudo apt-get install netatalk

```

- Edit /etc/netatalk/afpd.conf to allow guest login. This configuration line is the same as the default, with only uams_guest.so added.
```
- -tcp -noddp -uamlist uams_guest.so,uams_dhx.so,uams_dhx2.so -nosavepassword
```

- Edit /etc/netatalk/AppleVolumes.default so it contains the following lines. Change "/mnt/TimeMachine" to a directory of your choice. Also, "username" should be replaced with username that you want to access the Time Machine volume.
```

~/                "Home Directory"   options:usedots,upriv    ea:ad
/mnt/TimeMachine  "TimeMachine"      options:usedots,upriv,tm ea:ad allow:username

```

- Create the TimeMachine directory, then set ownership and permissions so the user can back up. 
```

mkdir /mnt/TimeMachine
sudo chown username:username /mnt/TimeMachine
chmod 600 /mnt/TimeMachine

```

- Add an entry to broadcast the shares with Avahi (Bonjour), so that the shares just show up for OS X clients. Create a file named /etc/avahi/services/afpd.service, with the following contents:
```

<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">%h</name>
<service>
<type>_afpovertcp._tcp</type>
<port>548</port>
</service>
<service>
<type>_device-info._tcp</type>
<port>0</port>
<txt-record>model=Xserve</txt-record>
</service>
</service-group>

```

- Restart the services.
```

sudo /etc/init.d/netatalk restart
sudo /etc/init.d/avahi-daemon restart

```

At this point, the shares should be visible from the Finder on the client computers. You should be able use the TimeMachine volume as a backup disk at this point. I don't remember the details here since I didn't need to redo this part, but it should be straightforward. If you need more information on how to do it, you should search for the terms "Time Machine sparsebundle".



Other notes:

Unlike with previous versions of netatalk, you no longer need run this command on your Mac:
```

defaults write com.apple.systempreferences TMShowUnsupportedNetworkVolumes 1

```
If you had set it to 1 in the past, I think you can set it back to 0 now.

In the AppleVolumes.default file, I added the "ea:ad" option. This tells it to use .AppleDouble directories instead of native extended attributes (xattrs). Version 2.1 added support for native xattrs if the host filesystem supports them (this is possible with ext3 and ext4), and even defaults to this. It may sound like a cleaner solution than using .AppleDouble directories for xattrs, but those directores apparently will still exist, for resource forks. Also, it seems to me that a lot of Linux tools don't really handle xattrs very well, so it's probably more reliable to stick with .AppleDouble directories. See [this thread]("http://sourceforge.net/mailarchive/message.php?msg_id=27845129") for more information.

The "cbd" database backend doesn't seem to be supported anymore, so the shares now use "dbd".

If you want more than one user to be able to access the Time Machine volume, the easiest way is to just use one account (on the server) for backups. If this isn't secure enough for your setup, you'll probably have to set it up with separate user accounts, but that's beyond what I have experience with.

---

### Post by hammas on 2011-07-30
Great to see an update for Lion! 

Everything works just fine. My shared folders pops up in finder as Xserve, Time Machine finds the volume I've dedicated. It accepts using it as my Time Machine volume but the back up fails with message "The network backup disk does not support the required AFP features". 

I have followed your guide back and fourth and triple checked that afpd.conf, AppleVolumes.default and afpd.service are exactly the same as described in guide (differing on drive paths and userid of course).

The only thing I can't check, because I don't know how, is which Netatalk version I'm running. I have tried to upgrade it according to your instructions with following result

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
netatalk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have also removed and installed it. Did the same with avahi-daemon. Conf files unchanged for both.

I'm quite new to Ubuntu so it's very likely that I've made some rookie mistake. Also I don't know what information to provide to get help but I'll give it a shot.

I run ubuntu 11.04 and I see your guide is for 10.04. Gut feeling is that it doesn't differ too much.
Time Machine backup on:
2 TB USB drive ext 4 (Two partitions:  1.5TB (Media) 0.5 TB (Time Machine))
mounted at /mnt/TimeMachine
Netatalk = ?

*content of AppleVolumes.default*
```
# The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: options:upriv,usedots
# By default all users have access to their home directories.
~/ "Home Directory" options:usedots,upriv    ea:ad allow:anders
#Regular AFP Share
#/home/anders/video "Video" cnidscheme:dbd options:usedots,upriv
#/home/anders/FileServer/Media "Media" cnidscheme:dbd options:usedots,upriv
/home/anders/FileServer/Media "Media" options:usedots,upriv    ea:ad allow:anders
#TimeMachine Share
/srv/TimeMachine "Time Machine" options:usedots,upriv,tm ea:ad allow:anders
# End of File
```

*content of afpd.conf*
```
# default:
- -tcp -noddp -uamlist uams_guest.so,uams_dhx.so,uams_dhx2.so -nosavepassword
#- -transall -uamlist uams_randnum.so,uams_dhx.so,uams_dhx2.so -nosavepassword -advertise_ssh
```


On Mac-side I run Macbook air 2,1 Os X 10.7 Lion.

I'm very grateful for all help I can get. Been working with this for a few days now an I only run in to dead ends.

---

### Post by daqron on 2011-08-05
Thanks for the info. When I configured as directed, I received the following error:

```
Time Machine can't access the backup disk "TimeMachine". 

The operation couldn't be completed. (OSStatus error 2.)
```

However, when I chmod the directory to 755 instead of 600, it works great. Not a secure solution, obviously, but it did the job. I'll have to experiment to see how far I can restrict permissions without breaking it.

Thanks for your hard work.

Cheers,
Jeremy

---

### Post by ajmctaggart on 2011-08-19
A couple of notes to newbs and those who rush alike - please note that these are mistakes anybody could make, and it took me quite some time to figure everything out.

I am using a 2TB drive SOLELY for TM on this Ubuntu box - so I have a drive that's just dedicated to Ubuntu, and one that is only for Time Machine Backups.  I backup 2 Macs to this drive, one is Snow Leopard, the other is Lion.

1.  DO NOT try to format a brand new drive as hfs+ (hfsplus) in GParted - once Time Machine on your Mac attempts to write to it, Ubuntu detects journaling and will mount the drive as read-only to protect it - this means all will work well ONCE (if at all) and then will not work again.  From what I've read - keep it ext2/3/4.   NTFS and FAT are not good options - FAT has filesize restrictions and NTFS may mount as read-only as well.

2.  When using a 2nd disk - you cannot just use the standard /media directory, you must use something like /mnt or /share (whatever you choose).  I also went as far to add the line to my /etc/fstab (see [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab"))  EVERYTHING STARTED WORKING AFTER ADDING THE ENTRY TO /etc/fstab, BEFORE THAT I COULDN'T GET THE ACCESS TO THE SHARE ON OS X SIDE.

3.  It's up to you on Avahi - I don't use the drive for anything else other than TM Backups, so I don't need it broadcasting and showing up in Finder.

4.  Safest bet (at least on first backup) is to change your Power (Energy) Settings on both Ubuntu and OS X to never sleep or power down disks when on Power Adapter.  If you forget to do this you may need to go to the root of the drive (/mnt/TimeMachine for example) and actually wipe out the .AppleDB file (you will need to use ls -al to actually see the file in Terminal) - otherwise you will get restricted CNID metadata.  What happened for me was when the Ubuntu "Time Capsule" went to sleep, the Backup got kicked offline and it didn't know where to start-up again.  Deleting this database file fixed it.

5.  As Jeremy posted above - I couldn't get the share to be accessible by TM or OS X without changing the permissions to 755 (chmod 755 /mnt/TimeMachine -600 did not work for me).  I don't know much about permissions - but I work in a small office and really don't care - if someone could shed light on this I'm sure we'd all appreciate it - could be something as simple as adding ourselves to a certain group on Ubuntu side.  Again, just not sure...

Other than that - it is fairly straightforward. :)

---

### Post by nhimf on 2011-10-11
The last reply is about 2 months old but I'd like to reply.

The TimeMachine directory should be chmod 700 (not 755 if you like your privacy). If you want to access a directory you must have the executable bit set for the user accessing it.

I have tried this and it works fine.

---

### Post by maltje on 2011-11-05
Is there an easy way to acces my shared files on a pc with ubuntu using my macbook?
On my MB I "see" the shared ubuntu maps but I can't open them,get following error
"can't find orriginal map"
Strange!!!

---

### Post by coolaj86 on 2011-12-24
Must I allow guest login?

Can I require a username and password instead? If so, how do I do that?

I'm on a network where I have real public ip addresses. I don't want to share with the whole world.

---

### Post by blacksunseven on 2012-01-20
[deleted]

---

### Post by SirKingChase on 2012-07-25
Just wanted to say that this rocks!  And it still works with Mountain Lion, upgraded this morning. :)

$300 LINUX Server > $300 Mac Time Capsole

---

### Post by Gwyneth Llewelyn on 2012-08-16
This sounds interesting. After upgrading to Mac OS X Lion, it stopped being able to connect to my Iomega NAS, which failed in the mean time, so I thought I could give the Ubuntu server a try with netatalk.

Unfortunately in my case, the connection always failed (although the server shows up correctly on Finder!) with the dreaded "There was a problem connecting to the server "rivendell.local" Check the server name...[...]". So I thought the problem was somehow related to DNS, so I put the server name on /etc/hosts (on the Mac and on Ubuntu), but still no luck: afpd always crashed with signal 11 after authenticating.

Ubuntu is freshly updated as of today :)

Luckily, this is a known bug and was reported here: [https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732](https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732)

All that I did was to change **/etc/netatalk/afpd.conf** and use the following line instead:

```
- -tcp -noddp -uamlist uams_dhx.so,uams_dhx2_passwd.so
```

This works for me. It doesn't allow guest logins but that's fine for me.

The link to LaunchPad also suggests different workarounds, specially when both Samba and netatalk need to work nicely with each other.

---

