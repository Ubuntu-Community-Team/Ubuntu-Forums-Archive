---
title: "vsftpd lock user to folder"
date: 2023-02-11
forum: Server Platforms
---

### Post by jazzstar on 2023-02-11
Hello All

I'm very new to linux so please excuse my ignorance.
I'm trying to setup FTP server and all is working except one thing.
I want to lock user to specific folder, but so far it does not work, I'm able to navigate everywhere.

```
 
GNU nano 6.2                                                    /etc/vsftpd.conf

chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
require_ssl_reuse=NO
ssl_ciphers=HIGH
vsftpd_log_file=/var/log/vsftpd.log

```

---

### Post by TheFu on 2023-02-12
New people to Linux/Unix (i.e. those coming from MS-Windows) haven't been told this, I suppose.  Plain FTP shouldn't be used since around 2002.  Move to sftp.  If you've installed ssh, then there is an sftp-server included with instructions on how to setup a chroot for each user login.

The only way plain FTP makes sense is if you intend to share everything on the system with the entire world.  If that's your intention, then you don't need chroot.

But if you care about security, then using sfp-server built-into the "openssh-server" package is what you want.  You can force more security by allowing only ssh-key/cert based authentication for logins too.  I always install the metapackage "ssh" and "fail2ban" to get both the ssh client and server programs. Fail2ban will firewall block after more than 3 or 5 failed attempts from the same IP address.  There's little reason not to have both.

[https://askubuntu.com/questions/49271/how-to-set-up-a-sftp-server-with-users-chrooted-in-their-home-directories](https://askubuntu.com/questions/49271/how-to-set-up-a-sftp-server-with-users-chrooted-in-their-home-directories) spells out how to accomplish the chroot you seek with the openssh sftp server.

---

### Post by LHammonds on 2023-02-12
And here is how you can configure [vsftpd for FTP over SSL]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=298").  I documented that for Ubuntu Server 20.04 but should be very similar on 22.04.

**EDIT:** +1 to avoid pure FTP at all costs.  There might be some edge cases where you have old phone equipment or whatnot that can only back up to FTP only but make sure you lockdown the FTP port to only accept connections from known IP addresses.

LHammonds

---

### Post by jazzstar on 2023-02-12
OK, I managed to configure SFTP and it's working, Thanks          TheFu 

Had some issues with permissoins though
My ChrootDirectory is /mnt/raid1/storage/ftp/ and I could login but could not download/upload
I added /mnt/raid1/storage/ftp/public and it is working

```
 GNU nano 6.2                                                  /etc/ssh/sshd_config

KbdInteractiveAuthentication no
UsePAM yes
PrintMotd no
AcceptEnv LANG LC_*
Subsystem sftp  /usr/lib/openssh/sftp-server
PasswordAuthentication yes
ChallengeResponseAuthentication no
Match Group ftp-users
ForceCommand internal-sftp
ChrootDirectory /mnt/raid1/storage/ftp/
PermitTunnel no
AllowAgentForwarding no
AllowTcpForwarding no
X11Forwarding no

```

Another question, when I'm trying download/upload it is asking again for password.
Can I remove this?

---

### Post by TheFu on 2023-02-12
> **jazzstar said:**
> OK, I managed to configure SFTP and it's working, Thanks          TheFu 

Had some issues with permissoins though
My ChrootDirectory is /mnt/raid1/storage/ftp/ and I could login but could not download/upload
I added /mnt/raid1/storage/ftp/public and it is working

```
 GNU nano 6.2                                                  /etc/ssh/sshd_config

KbdInteractiveAuthentication no
UsePAM yes
PrintMotd no
AcceptEnv LANG LC_*
Subsystem sftp  /usr/lib/openssh/sftp-server
PasswordAuthentication yes
ChallengeResponseAuthentication no
Match Group ftp-users
ForceCommand internal-sftp
ChrootDirectory /mnt/raid1/storage/ftp/
PermitTunnel no
AllowAgentForwarding no
AllowTcpForwarding no
X11Forwarding no

```

Another question, when I'm trying download/upload it is asking again for password.
Can I remove this?

Great that you got it working.
If you don't want to be asked for login credentials, then you can setup ssh-keys between the client and the host. Those will be honored.  If you have ssh-agent (or whatever key-management your client machines use) on your client, then you'll only need to "unlock" the ssh-keys once per login.  This makes all ssh-based connections, including sftp, hassle free AND more secure.
From any Unix-based client, run these to commands to create a key, put the 2-halves (pub/private) in your ~/.ssh/ directory on the client, then the 2nd command will push the public ssh-key to the remote system, place it in the correct location and setup the permissions as required.  I've never done this without having full ssh enabled, so I don't know how it works inside a chroot with only sftpd enabled.  Can't hurt to try and if it doesn't work, relax the limitations for a few minutes to get the public-key uploaded, then lock it back down for sftp-only access again.
[Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)
[Https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278](Https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278)

And don't forget fail2ban and firewall settings:
[Https://ubuntuforums.org/showthread.php?t=2446413&p=13969099#post13969099](Https://ubuntuforums.org/showthread.php?t=2446413&p=13969099#post13969099)

If you need help with permissions, much more data will need to be provided.  Do you already understand 80+% of Unix file permissions?

---

### Post by jazzstar on 2023-02-12
fail2ban installed, thanks for that. Didn't know that software

For client, it will be windows and person is not tech savy.

As for permissins, I come up with this

```

@server:/mnt/raid1$ ls -l
total 24
dr-xr-xr-x 3 root root  4096 Feb  6 18:34 storage

@server:/mnt/raid1$ ls storage/ -l
total 4
dr-xr-xr-x 3 root root 4096 Feb 12 11:53 ftp

@server:/mnt/raid1$ ls storage/ftp/ -l
total 228
-rw------- 1 root   root      227226 Feb  8 09:22 1.jpg
drwxrwxr-x 2 lukasz ftp-users   4096 Feb 12 13:03 public

@server:/mnt/raid1$ ls storage/ftp/public/ -l
total 440
-rw-r--r-- 1 lukasz ftp-users 227226 Feb 12 12:04 1.jpg
-rw-r--r-- 1 lukasz ftp-users 209429 Feb 12 13:02 2.jpg
-rw-r--r-- 1 lukasz ftp-users   4713 Feb 12 13:03 bout.JPG


```

---

### Post by TheFu on 2023-02-12
Win10+ has ssh-keygen and it works the same as on Linux.

However, MSFT decided **not** to include ssh-copy-id, so that will need to be handled manually.  Further, I don't know if the built-in ssh from MSFT will work with WinSCP or Filezilla, which are the best sftp clients on that platform.  Probably need to find a how-to for the specific program to be used that explains how to setup ssh-keys and move the public key  to the remote server.  Fortunately for me, I don't deal with MSFT anymore.  OTOH, I bet google will have answers.

Google found these:
[https://winscp.net/eng/docs/guide_public_key](https://winscp.net/eng/docs/guide_public_key)
[https://wiki.filezilla-project.org/Howto](https://wiki.filezilla-project.org/Howto)

So, those permissions allow anyone in the ftp-user's group to delete any files. Is that your intention?  That comes from the directory permissions where the files are located.  In general, for minimal security, it is best to never allow end-users to see the directory where their uploads go, then to do some processing on those uploads to ensure they don't contain malware before making them available to others in a download directory.  Don't mix upload/download directories.

If this is for 1 person, then there's no need to setup an ftp-users unix group.  Actually, if it were me, I'd rename that group to sftp-users to prevent confusion. People mix up sftp, ftps and plain ftp all the time. They are each very, very, different, even if the FTP interface is the same to make it easier for end-users to be force-switched to the encrypted versions.


OT:
On the good side, pretty much any Linux file manager has sftp:// URL support and will honor the ssh keys just liky 50+ other ssh-based tools.  Not that this helps your non-technical MSFT users.  ssh and ssh-based tools are how computers talk to each other in a secure way.  Almost everything that isn't HTTPS-based uses an ssh-based tunnel for everything else.  Things like remote commands, running remote applications, running remote GUI programs and having those displayed locally, in addition to transferring files and doing backups are all based on ssh.  It's hard to explain how central ssh is to user-to-system communications.  Heck, even sshfs is a remote file system using ssh providing secure access to files like they are local.

Ever heard of github?  That's all accessed over ssh by the programmers checking in and out code.

---

### Post by jazzstar on 2023-02-12
Deleting will not be a big problem, this is for family use and possibly trusted friends.
However out of curiosity, which folder should be changed to prevent delete action?
ftp or public?

---

### Post by TheFu on 2023-02-12
> **jazzstar said:**
> Deleting will not be a big problem, this is for family use and possibly trusted friends.
However out of curiosity, which folder should be changed to prevent delete action?
ftp or public?

Well, if you want everyone to be able to upload to the same place, you are stuck.  The permission that allows creating a new file is the same as the permission that allows deletion.  Typically, the upload directory won't allow "read", so others might upload, but they can't get a list of files.  Remember when I said to have upload and download directories separate?  This is 1 reason, but there are 10 others I can think of off the top of my head.  It is a standard Unix pattern.

Other options:

You know, for a family, I'd deploy Nextcloud instead.  Then they'd each have their own upload spaces and could set those up to share with everyone.   I run a nextcloud server.  These days, that isn't very hard, but you'll still want to require either a VPN or ssh-tunnel for access.  While lots of people do have their nextcloud servers directly on the internet, I don't and wouldn't.  Complicated software like that just has too many opportunities for remote cracking and failures.

And if you really want end-users to have control and bullet-proof security, you might consider something like Retroshare.  RetroShare uses GPG keys for authentication and has a chat, upload, and a few other working-together/family communications methods.  OTOH, even I found it too cumbersome for use ... and that's saying something.

Ok, so in reality, I'd still use sftp, just with different upload directories for each user.  If you trust everyone, you could move files hourly (or daily) to a shared download directory that is read-only.  Heck, you could put the files to be downloaded on a webserver, if you like.

For a once a year file upload, something like wormhole (aka magic wormhole).  You can use someone else's intermediate wormhole "Rendezvous Server" or run your own.  I've pulled huge files (35GB) over wormhole from friends.  [https://ubuntu.com/blog/magic-wormhole-send-files-with-ease](https://ubuntu.com/blog/magic-wormhole-send-files-with-ease) has more.  Hummmm.  Actually, making a tiny webserver that provides a wrapper around wormhole so that non-technical people don't need to install anything shouldn't be too hard.  Wormhole is easy when two people are talking or orchestrate:
```
$ wormhole send glances-root.log
Sending 1.3 kB file named 'glances-root.log'
Wormhole code is: 5-conformist-newborn
On the other computer, please run:

wormhole receive 5-conformist-newborn

```
That's a 1-time xfer command. The person sending has to leave wormhole running until the other person who knows the code can grab it.  Only 1 grab is allowed.  That's got me thinking.

---

### Post by jazzstar on 2023-02-12
You are a Star Sir.
Thank you very much for your help and have great day.

---

