---
title: "vsfptd - only allow registered users access"
date: 2009-11-12
forum: Server Platforms
---

### Post by roundhay on 2009-11-12
I would like to set up a file server for few friends and family to access and down load files (not delete or change) and have an upload folder where they can send files.

I was hoping to use ssh /sftp but this does not suit my needs.

I have installed vsftpd but I do not want to allow any anonymous access and woudl rather have a set up where only users I set up can access the files.

Can vsfpt be set up in this way? i have read a few guides which lead me to believe that it can but they are not so easy to follow.

Ideally I would also like to use a secure connection (ssl certs?) and force users to log in when they enter the ftp site

---

### Post by kevin11951 on 2009-11-12
> **roundhay said:**
> I would like to set up a file server for few friends and family to access and down load files (not delete or change) and have an upload folder where they can send files.

I was hoping to use ssh /sftp but this does not suit my needs.

I have installed vsftpd but I do not want to allow any anonymous access and woudl rather have a set up where only users I set up can access the files.

Can vsfpt be set up in this way? i have read a few guides which lead me to believe that it can but they are not so easy to follow.

Ideally I would also like to use a secure connection (ssl certs?) and force users to log in when they enter the ftp site

Have you been to Ubuntu's own server guide?  [https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.10/serverguide/C/ftp-server.html)  You can use those instructions, no matter what version you are using (as long as its 8.04 or later).  Make sure you do the "User Authenticated FTP Configuration," and "Securing FTP" sections.

Ps. Its very easy to do once you get into actually doing it :D

---

### Post by roundhay on 2009-11-12
I have looked at this and some of the other guides but I'm struggling to understand exactly what is being referred to when 'users' are discussed.

I'll try to explain....

When I am reading the guides and they mention users I'm not sure if I need to set up a 'user' up as a user on the server or if it can just be set up as a 'user' of vsftpd 

When I set up my sever I set up one user e.g. Frank. Frank has a home directory and is the user that logs into the system.

If I want to create a user, Simon who has access to the ftp site do I have to set Simon up as a user on the server or can they just be added as a user in the vsftpd config files?

---

### Post by kevin11951 on 2009-11-12
> **roundhay said:**
> I have looked at this and some of the other guides but I'm struggling to understand exactly what is being referred to when 'users' are discussed.

I'll try to explain....

When I am reading the guides and they mention users I'm not sure if I need to set up a 'user' up as a user on the server or if it can just be set up as a 'user' of vsftpd 

When I set up my sever I set up one user e.g. Frank. Frank has a home directory and is the user that logs into the system.

If I want to create a user, Simon who has access to the ftp site do I have to set Simon up as a user on the server or can they just be added as a user in the vsftpd config files?

There are multiple ways you can do it, but the easiest way is to just create the users on the server like:
```
adduser <username>
```
then do what is said before, and it will make it so that when they login they are taken to their home dirs, and can only see their home dirs instead of the server root.

---

### Post by roundhay on 2009-11-13
I followed some of the steps in the following guides:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup#How_To_Get_VSFTPD_Started]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup#How_To_Get_VSFTPD_Started")

[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/]("http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/")

I created a group ftp-users, set up the a new user, USER2 and a ftp folder, /home/USER1/ftp-files and set some permissions

> USER1@server:~$ sudo groupadd ftp-users
USER1@server:~$ sudo mkdir /home/USER1/ftp-files
USER1@server:~$ sudo chmod 750 /home/USER1/ftp-files
USER1@server:~$ sudo chown root:ftp-users /home/USER1/ftp-files
USER1@server:~$ sudo useradd -g ftp-users -d /home/ftp-files USER2
USER1@server:~$ sudo passwd USER2

Then I changed the vsftpd.conf file and added

chroot_local_user=YES

local_root=/home/USER1/ftp-files

when I logged in through the web browser I had to input a login & password and was inside the folder ftp-files (I checked this by creating a folder 'docs' /home/USER1/ftp-files/docs which I could see)

Now I cannot get any files into the folder, I get a permission error?

I would like to be able to drag and drop files this folder from other PC's on my LAN but can't.

I also need to figure out and understand more of the vsftp.conf options.

---

### Post by Lars Noodén on 2009-11-16
Then, if you are not dead-set on sticking to the FTP protocol, nor want to tunnel FTP over SSL (aka FTPS), then I would propose using the sftp subsystem built into the ssh server running on your machine.  

Except for the name, the end users won't notice much difference between the old ftp client and the sftp client.  If the use Fetch or Filezilla, then it will even be the same client.  The difference being that one is both hard to set up and insecure, which the other is easy to set up and quite secure.  

sshfs uses fuse and the sftp subsystem to make the remote machine accessible to the user via a folder.  Anything that can be done to a local folder can be done to the sshfs folder.  

sftp is very easy to chroot.  So these users can be limited in access to only their home directories, with almost no effort on your part.  

```

# add chroot users to the group 'sftponly' for this to work
 
Match Group sftponly
   ChrootDirectory %h
   ForceCommand internal-sftp
   AllowTcpForwarding no

```

---

### Post by roundhay on 2009-11-16
I have found an interesting link discussing sftp and scponly which seems to match what I'm looking for

[http://ubuntuforums.org/showthread.php?t=451510]("http://ubuntuforums.org/showthread.php?t=451510")

I use sshfs already and find it really useful.

I'm still struggling to configure vsftpd so I might have a look into this.

---

### Post by Lars Noodén on 2009-11-17
> **roundhay said:**
> I have found an interesting link discussing sftp and scponly which seems to match what I'm looking for

[http://ubuntuforums.org/showthread.php?t=451510]("http://ubuntuforums.org/showthread.php?t=451510")

I use sshfs already and find it really useful.

I'm still struggling to configure vsftpd so I might have a look into this.

sshfs actually uses the sftp-subsystem already built into ssh server.  The thread above is interesting but more complex than it needs to be.  If you want to provide access via sshfs and sftp, then you don't need that thread.  You only need the following at the end of /etc/[sshd_config](http://linux.die.net/man/5/sshd_config)

```

Match Group sftpusers
   ChrootDirectory %h
   ForceCommand internal-sftp

```

The add any users you wish to lock into sftp to the group **sftpusers** or whichever one you put on that line in sshd_config.  They'll be able to use sshfs and sftp, but not login or use scp or anything else dangerous.

---

### Post by roundhay on 2009-11-17
This sounds like the simple solution I'm looking for, can you confirm the directory that the sftp users will be locked into?

When I set up the sever I created a user, USER1 which has a home directory. This is the users account I log into and use for SSH and SSHFS access. If I create other user for SFTP which directory will they be locked into, their own home directories? If this is where they will end up how can I use this set up to share a common folder in:

> /home/USER1/Commom-folder 

with all of the users so that they can download content?

Edit - I have just tried following this guide without success. I can't seem to figure out file transfer

[http://ubuntuforums.org/showthread.php?t=1057657]("http://ubuntuforums.org/showthread.php?t=1057657")

---

### Post by Lars Noodén on 2009-11-18
Try sketching on paper first then.  

The users will be locked into the directory specified by the ChrootDirectory directive.  They can't go up even a single level from that.  They can't go sideways, via symlinks, either.  

You can use special symbols with [ChrootDirectory](http://linux.die.net/man/5/sshd_config)

[list]
[*] **%u** = user's login name
[*] **%h** = user's home directory
[/list]

So you need to plan your directory structure and maybe give the various users a special home directory.  

usermod -d /home/sftp/$USER $USER

---

