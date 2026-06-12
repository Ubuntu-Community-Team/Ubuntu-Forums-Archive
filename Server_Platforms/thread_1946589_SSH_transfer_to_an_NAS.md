---
title: "SSH transfer to an NAS"
date: 2012-03-25
forum: Server Platforms
---

### Post by ibates on 2012-03-25
I am attempting to backup using SimpleBackup (SBackup) to a Netgear ReadyNAS on my networkj.  I am using 10.04 upgraded.

The Ubuntu guide suggests that, in order to not expose passwords, it is a good idea to use ssh.  The advice states:

If you do not want to expose your password in the clear you can use SSH keys. For more information see its respective page, a short example follows below. Comments have been added (#) above each step:

# switch to root
sudo su -
# create a key set without a passphrase
ssh-keygen
# copy the public key to the backup server
ssh-copy-id backup-user@backup-server/path/to/backups/machine-id/
# test that the connection will work without a password
ssh backup-user@backup-server
# make sure that the backup user can in fact write to the backup directory
touch /path/to/backups/machine-id/test.txt
rm /path/to/backups/machine-id/test.txt

I have generated the requisite key, but cannot copy the public key to the backup server.

The destination is a networked Netgear ReadyNAS which I can normally access by smb://nas-xx-xx-xx/path_to/backups/, but obviously not using ssh.

So in the above script, I cannot successfully define "backup-server".  I have tried every way I can think to define "backup-server" but to no avail.

Suggestions would be appreciated.

---

### Post by agillator on 2012-03-25
Does your NAS have a web interface? If so, does it connect with https or can it be set to connect with https instead of http? If so, then it should also have a file manager available. If you log into it as admin or whatever it requires you should be able to securely upload the key file(s) you need. Of course this all assumes that your NAS has ssh available.

---

### Post by collisionystm on 2012-03-25
> **ibates said:**
> I am attempting to backup using SimpleBackup (SBackup) to a Netgear ReadyNAS on my networkj.  I am using 10.04 upgraded.

The Ubuntu guide suggests that, in order to not expose passwords, it is a good idea to use ssh.  The advice states:

If you do not want to expose your password in the clear you can use SSH keys. For more information see its respective page, a short example follows below. Comments have been added (#) above each step:

# switch to root
sudo su -
# create a key set without a passphrase
ssh-keygen
# copy the public key to the backup server
ssh-copy-id backup-user@backup-server/path/to/backups/machine-id/
# test that the connection will work without a password
ssh backup-user@backup-server
# make sure that the backup user can in fact write to the backup directory
touch /path/to/backups/machine-id/test.txt
rm /path/to/backups/machine-id/test.txt

I have generated the requisite key, but cannot copy the public key to the backup server.

The destination is a networked Netgear ReadyNAS which I can normally access by smb://nas-xx-xx-xx/path_to/backups/, but obviously not using ssh.

So in the above script, I cannot successfully define "backup-server".  I have tried every way I can think to define "backup-server" but to no avail.

Suggestions would be appreciated.


You need to mount the netgear NAS share in Ubuntu.

First create a credentials file.

/root/.netgearcred

username= USER
password= PASSWORD

make a folder to mount the share

install smbfs

sudo apt-get install smbfs

edit your /etc/fstab

add the line

//NETGEAR/SHARE /FOLDER.YOU.made. smbfs credentials=/root/.netgearcred, 0777 0


sudo mount -a

run df -kh to see if your share mounted

now you can just rsync, ssh, whatever to the local folder you create which is actually the netgear.

---

### Post by agillator on 2012-03-25
collisionystm: Is the password used while mounting the share encrypted? If so, fine. If not, that sort of defeats the purporse, doesn't it? I wasn't (am not) sure which is why i used the method I did. If it is, yours is probably better.

---

### Post by collisionystm on 2012-03-25
> **agillator said:**
> collisionystm: Is the password used while mounting the share encrypted? If so, fine. If not, that sort of defeats the purporse, doesn't it? I wasn't (am not) sure which is why i used the method I did. If it is, yours is probably better.


No, not to the level you want. It is samba traffic on the network but unless you have an endpoint that will support SSH, it might be your only option.

Why not just grab an old desktop, throw ubuntu server on it and connect a large usb or internal hard drive to it. Back it up that way.

---

### Post by agillator on 2012-03-25
That works. But then wasn't our original intention to drain the swamp?  To be perfectly honest, I suspect we are discussing the number of angels on the head of a pin. If you are on a LAN, which the NAS most likely is, and if it is a trusted LAN, as most small or home LANs are, whether or not a password that never leaves that LAN is encrypted or not probably is not a matter of national security. As a navigator, I remember being careful not to measure something with a micrometer so it could be marked with a grease pencil and cut with an ax. In short, you are probably right with the easiest, most understandable and secure enough way.

---

### Post by ibates on 2012-03-25
I seem to have left out quite a bit of detail.

The Netgear ReadyNAS is a network device which can be accessed from each and every other device on the network, without a password.

Either from "Places->Network, or "Windows Explorer" (on the Windows VM).

No password is necessary to gain access.

The problem seems to be that I have set the NAS as a Share rather than for Users.  Thus there is no username or password as required by SBackup configuration for both ssh or ftp.

But the Ubuntu guide for SBackup makes the statement shown in the first posting here.

The problem is that I simply do not know the syntax to use when setting up ssh access as described in the Ubuntu guide, i.e. 

ssh-copy-id backup-user@backup-server/path/to/backups/machine-id/

I assume: backup-user can be any username
          backupserver is the NAS (and the only address I know for it
          is its ID nas-xx-xx-xx   
          machine-id is the device being backed up.

Does this throw some more light on the setup?

---

### Post by kevdog on 2012-03-25
Does your NAS have an ssh daemon running by default?  

It seems kind of silly to me at least that you would restrict your linux users to a very good security model of running ssh with a key, but then on the other hand allow all windows users to have access without any share parameters.  Kind of defeats the point of security at all.

---

### Post by ibates on 2012-03-25
To colisionystm.

By creating credentials and inserting then in fstab, will that change the normal LAN access for other devices in any way?

I would hate to set up the SBackup configuration and then find that none of the other LAN devices can access the NAS.

---

### Post by ibates on 2012-03-25
kevdog:

That I cannot say.

Burt I do believe that the Netgear ReadyNAS does in fact use Ubuntu as its OS although I do not know what version.  I suspect it would be fairly up to date.

Sorry I can't be more helpful.

---

### Post by kevdog on 2012-03-25
For my network configuration I added this to my fstab file:

#Network LapTopShare
//10.0.1.115/Downloads  /media/Downloads  cifs  guest,uid=1000,iocharset
=utf8,codepage=unicode,unicode  0  0

Where //10.0.1.115/Downloads = The network share (remote computer)
/media/Downloads - The local folder where I'm going to mount the remote share

cifs - I'm using cifs rather than smbfs here

uid=1000 is my uid number that can be found by examining the /etc/passwd file and looking up the particular user 

I'm not sure if you can use cifs but I find it to be much more reliable than smbfs.

Additionally if you add this to the local computer, it will not screw up other users of the NAS, however (big if) there might be issues locally if any type of security measure is in place on the remote share computer -- meaning you need to supply more security credentials to mount the remote share.

---

### Post by ibates on 2012-03-25
kevdog:

Just one further comment, and once again, I haven't explained myself very well.  Security is simply not an issue.

This is a private very secure network and anyone on the network has user rights for all devices with the administrator having admin rights over everything.

The issue is how to configure SBackup to backup on schedules to the very large capacity NAS (4 Tb at this stage).  It seems that the SBackup software only allows access to remote devices by ssh or ftp.  The NAS has no such restrictions.  It will allow virtually anything.

And the core problem is that I do not understand how to seetup ssh (or ftp for that matter).

For what it is worth, provided I do manual backups (a bit of a pain), I can simply insert smb, etc., for access and it works, first time every time.  But apparently for automatic backup using SBackup, I need to setup one of the two defined protocols, ssh or ftp.

Once again I emphasise that the problem is with me and the SBackup software.  The NAS seems to accept anything the software sends to it.

---

### Post by collisionystm on 2012-03-25
> **ibates said:**
> To colisionystm.

By creating credentials and inserting then in fstab, will that change the normal LAN access for other devices in any way?

I would hate to set up the SBackup configuration and then find that none of the other LAN devices can access the NAS.


No it will not affect anything else. Its no different that accessing a share normally except samba gives you the ability to mount it locally as if it was a folder. Seamless computing. :guitar:

---

### Post by collisionystm on 2012-03-25
if your sbackup supports ssh, just set your crontab to run an rsync script to the sbackup.

However you choose to do it, if you have enough space, use rsnapshot. Its a nifty program.

---

### Post by kevdog on 2012-03-25
Ok -- so your backup program only supports ssh or ftp -- which is kinda weird since ssh is usually an interactive shell -- I think you probably mean sftp which is like ftp but runs similar to ssh -- but I'm digressing.

I'm fully in the dark on how your backup program works -- gui or command line -- however I'm going to make some assumptions and you can tell me if they are right or wrong.

Say you can mount the remote file system locally either manually or via fstab (which basically creates the mount point at boot), can't you then just ssh to localhost?  This would require that you have setup a ssh daemon on the local client (yes the same machine you are running your backup program on).  If you ssh to localhost, its then possible to treat it as if it were a remote host, and then you can change directories, put, get files like normal sftp or ftp.  I'm guessing this would work for you although I must admit its kind of a round-a-bout setup.  

Are you certain there is no ssh or ftp daemon running on the backup NAS?

---

### Post by ibates on 2012-04-11
It has taken a while for me to study the relevant documentation, and in so doing, I have found that ssh is in fact, not supported by the ReadyNAS.  FTP is.

With respect to the backup program, Simple Backup is a program I obtained through the Synaptic Program manager.  It seems to be a very common program.  It is desirable because it is entirely GUI based and completely eliminates any need for programs to be run in terminal.

I can mount the ReadyNAS manually, just as if it was any other hardware device, and can access all shares via "Places->Network".

As best I can underestand it, I believe if I could mount the device at bootup, I could then access it as though it were any other "local" device.  But I have been unable to do so, despite various tries at editing fstab to do so.

Further, for what it is worth, the ReadyNAS documentaion states:

To access a share using network-attached Linux or Unix device:

1.  Ensure that file-sharing protocols are enabled for any shares that you want to remotely access.  [They are].

2.  Ensure that your Linux or Unix device supports the SMB file-sharing protocol.  [It does.  Remember, I can manually backup to the ReadyNAS using Simple Backup by entering a simple smb:// command].

3.  Using a terminal program, enter the following command:

  mouont [-t cifs -o username=<user_name>,password=<password>]
  //<ReadyNAS-IP_Address>/<share_name> <mount_point>

  Note the following:

  * <user_name> and <passwword> match the user name and password on the RedayNAS system.  However, to connect as a guest, you do not need to provide a user name.  If your operating system requests a password when you access as a guest, press the Enter key.  [The backup program will always be a guest].
  * <ReadyNAS_IP_address> is the IP address of your ReadyNAS system.  [This is a problem because the address is DHCP assigned and is as often as not, different from the last time a boot was carried out].
  * <share_name> is the name of the share you want to access. [Obvious]
  * <Mount_point> is the name of an empty folder on your Linux or Unix device.  [Also obvious].

But no matter how I attempt to tell fstab to mount this device at boot, it just will not mount.

But having said all of that, none of this has ever been necessary to access shares on the ReadyNAS.  All one has to do is click on Network in Places and there is an icon for the NAS-xx-xx-xx.  Simply clicking on that icon opens (mounts) the device and reveals all shares which can then be accessed at will.

What am I doing wrong.

---

### Post by collisionystm on 2012-04-11
> **ibates said:**
> It has taken a while for me to study the relevant documentation, and in so doing, I have found that ssh is in fact, not supported by the ReadyNAS.  FTP is.

With respect to the backup program, Simple Backup is a program I obtained through the Synaptic Program manager.  It seems to be a very common program.  It is desirable because it is entirely GUI based and completely eliminates any need for programs to be run in terminal.

I can mount the ReadyNAS manually, just as if it was any other hardware device, and can access all shares via "Places->Network".

As best I can underestand it, I believe if I could mount the device at bootup, I could then access it as though it were any other "local" device.  But I have been unable to do so, despite various tries at editing fstab to do so.

Further, for what it is worth, the ReadyNAS documentaion states:

To access a share using network-attached Linux or Unix device:

1.  Ensure that file-sharing protocols are enabled for any shares that you want to remotely access.  [They are].

2.  Ensure that your Linux or Unix device supports the SMB file-sharing protocol.  [It does.  Remember, I can manually backup to the ReadyNAS using Simple Backup by entering a simple smb:// command].

3.  Using a terminal program, enter the following command:

  mouont [-t cifs -o username=<user_name>,password=<password>]
  //<ReadyNAS-IP_Address>/<share_name> <mount_point>

  Note the following:

  * <user_name> and <passwword> match the user name and password on the RedayNAS system.  However, to connect as a guest, you do not need to provide a user name.  If your operating system requests a password when you access as a guest, press the Enter key.  [The backup program will always be a guest].
  * <ReadyNAS_IP_address> is the IP address of your ReadyNAS system.  [This is a problem because the address is DHCP assigned and is as often as not, different from the last time a boot was carried out].
  * <share_name> is the name of the share you want to access. [Obvious]
  * <Mount_point> is the name of an empty folder on your Linux or Unix device.  [Also obvious].

But no matter how I attempt to tell fstab to mount this device at boot, it just will not mount.

But having said all of that, none of this has ever been necessary to access shares on the ReadyNAS.  All one has to do is click on Network in Places and there is an icon for the NAS-xx-xx-xx.  Simply clicking on that icon opens (mounts) the device and reveals all shares which can then be accessed at will.

What am I doing wrong.


Please try my method that I mentioned earlier.

> mouont [-t cifs -o username=<user_name>,password=<password>]
  //<ReadyNAS-IP_Address>/<share_name> <mount_point>

CIFS is an older command. 



First create a credentials file.

/root/.netgearcred

username= USER
password= PASSWORD

make a folder to mount the share

install smbfs

sudo apt-get install smbfs

edit your /etc/fstab

add the line

//NETGEAR/SHARE /FOLDER.YOU.made. smbfs credentials=/root/.netgearcred, 0777 0


sudo mount -a

run df -kh to see if your share mounted

now you can just rsync, ssh, whatever to the local folder you create which is actually the netgear.
__________________

---

### Post by ibates on 2012-04-15
Hi Collisiontstm.

Thanks once again for your patience.  But I have tried the method you mentioned earlier and no joy.  I think the problem is that when I setup the NAS, I elected to go for operation on a Share basis, not a User basis.  As a result, there is no "user" or "password".  And that seems to stymie the entire exercise.

The idea of going with Shares is that anyone on my network can access the NAS without logging in.  It is just like any other device on the network.  By using the "User" option, each person on the network must log in each time he/she want to access the NAS, which, by the way, is being used as a common storage for a number of network attached devices.

Now; assuming I can simply ignore the credentials requirement, the next difficulty arises when I attempt to tell fstab what the device is.  I have tried an IP address, but the IP address is assigned by DHCP and as such may be a different address next time I boot it up.  I have tried the usual //nas-xx-xx-xx/etc.  But nothing is recognised.

Any further thoughts?

---

### Post by ibates on 2013-05-02
Collisionystm; I have been trying for the last year, various permutations of the advice you gave me in this post.  But still (and I have almost no hair left from tearing it out), no joy.

I have made the credential file as you have instructed, and I thought I had made the folder to mount the share.  But no matter what folder I make, nor where I put it, (on the desktop HDD, not the NAS), and then run 
sudo mount -a
I get the following message
Couldn't chdir to /media/DesktopBackups.: No such file or directory
ian@ian-desktop:~$ 
Currently the folder I am attempting to use is
/media/DesktopBackups
The line I have inserted in fstab is
//nas-xx-xx-xx/backup/Ian_Desktop_Backups /media/DesktopBackups. smbfs credential=/root/.netgearcred, 0770 0
I have installed smbfs as per your instructions.
And here is where I am stuck.

If you still have the patience, could you please spell out for me where I have gone wrong, or what I should be doing.

Many thanks for your help.

---

### Post by matt_symes on 2013-05-02
Thread moved to **server platforms.**

I'll get you some exposure in this sub forum as well. 

There is still a redirect in place from the wireless and netwoking sub forum.

---

### Post by steeldriver on 2013-05-02
What ReadyNAS device is it? I have a ReadyNAS Duo and it supports NFS as well as SAMBA - I haven't read the entire thread, but have you considered mounting via NFS? It's usually less trouble for *nix clients - I mount my home dir off the NAS to my Ubuntu laptop via NFS using autofs and that seems to work fine

FYI there is a 3rd party addon that enables SSH access by root (at least for the Duo) - I wouldn't suggest using it for scheduled backups but it's useful for admin tasks that are not supported via the frontview web interface - for example I used it to align my UIDs/GIDs

---

### Post by ibates on 2013-05-03
Steeldriver:  It sounds like we have the same ReadyNAS in principle.  This one is an NV+ for four HDD, but I believe that electronically they are the same.
No I haven't considered mouonting it via NFS.  Would that mount remain activated at each boot up?  If so, I would appreciate a step by step on how to actually go about doing it.  It is all a bit of a mystery to me.

---

