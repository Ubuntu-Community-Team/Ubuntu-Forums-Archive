---
title: "Issues with sftp permissions"
date: 2012-07-08
forum: Server Platforms
---

### Post by kubiej21 on 2012-07-08
I am trying to setup a simple file server for multiple users. I installed a 1Tb drive in my server, and mounted the drive under /media/data. 

What I was trying to setup, was to only allow myself to ssh into the server and to allow other users to sftp into the server under the /media/data directory.

I got the first portion working correctly by creating a ssh_users group, adding my user to it, and adding "AllowGroups ssh_users" to sshd_config.

I then added 
    Match Group sftp_users
        ChrootDirectory /media/data
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand /usr/lib/openssh/sftp-server
   Match

at the end of the sshd_config file. 

When I try to sftp into the server as one of the sftp_users, it returns with a permission denied. 

root owns the directories /media and /media/data, and the permissions are set to 755.

This should be really easy to setup, but I must be missing something incredibly obvious.

---

### Post by kevindontenville on 2012-08-20
Did you get this issue solved? I have worked through this sort of thing twice following guides and forum posts and each time came unstuck with some of the subtle bits that just kill the thing until they are right.

Permissions seem to be part of the problem but I have also found using the subsystem section in ssh_config as:

```
Subsystem sftp /usr/lib/openssh/sftp-server
```

but the match group section using:

```
ForceCommand internal-sftp
```

Also I saw an extra 'match' at the bottom of your snippet that perhaps shouldn't be there.

Permissions as you state should be that the root of the users directory structure is owned by root:root and should not be writeable by any other group.

The directories under the root, ie /media/data are to be owned and accessible by the users.

NB a directory can be owned by a user such as root but the contents need not be. 

```
chown root:root /media
```

will change to root ownership only the directory.

```
chown -R user:user /media/data
```

will change the directory and contents including sub dirs to user and user group ownership.

```
chmod 755 /media
``` 

will set rights on the root directory to read and execute world and group but r/w/x for root user.

```
chmod -R 775 /media/data
```

will set rights for all content including sub dirs as r/w/x for user and group

Personally, for simple means of identifying things I like to create another mount point that is not as system controlled and as potentially changeable as /media and get the UUID of the drive and force it to mount somewhere else eg /bigdisk/shareddrive but that is just me and probably of no significance!

Good luck with it all!

K

---

