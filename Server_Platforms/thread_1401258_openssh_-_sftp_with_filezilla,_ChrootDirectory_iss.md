---
title: "openssh - sftp with filezilla, ChrootDirectory issue"
date: 2010-02-07
forum: Server Platforms
---

### Post by Zidaps on 2010-02-07
Hi,

I have openssh installed and it works great right out of the box. However, I don't want people accessing everything on my machine.

My machine is behind NAT and ufw firewall. I have configured both so that port 22 is open. I've added the new users I want to have limited access and assigned them to group "sambashare" (just because its convenient.)

When the bottom bit of my config file "/etc/ssh/sshd_config" is set as shown below, everything works great:

> #Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp

UsePAM yes

Match Group sambashare

#    ChrootDirectory /media/Media/Public
    ForceCommand internal-sftp
    AllowTcpForwarding noWhenever I make the change to enable "ChrootDirectory" so that it limits the users access, I simply remove the # and it looks like this:


> #Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp

UsePAM yes

Match Group sambashare

    ChrootDirectory /media/Media/Public
    ForceCommand internal-sftp
    AllowTcpForwarding noHowever, thats when I start running into problems. When I try logging in with Filezilla; I am not able to connect and this is the response I get from Filezilla:

> Status:    Connecting to ##.###.###.###...
Response:    fzSftp started
Command:    open "user@##.###.###.###" 22
Command:    Trust new Hostkey: Once
Command:    Pass: ********
[COLOR=Red]Error:    Could not connect to server[/COLOR]Anyone know how to get this up and running?

---

### Post by joberly on 2010-02-07
What are the directory permissions on the Chroot'ed folder?

---

### Post by Zidaps on 2010-02-07
Hi,
Is this what you are asking for? Its information for the disk.

> drwxrwxr-x  6 zidaps sambashare  4096 2010-02-04 00:09 MediaInfo on the folder I want to share is:

> drwxrwxrwx 10 zidaps sambashare  4096 2010-02-04 23:55 PublicThanks

---

### Post by joberly on 2010-02-07
The directory in which to chroot() must be owned by root.

Change ownership and see what happens.

---

### Post by Zidaps on 2010-02-07
Hi,

The problem persists... I've changed the owner of the folder to "root"

> drwxrwxrwx 10 root sambashare  4096 2010-02-04 23:55 Public

Any other possible solutions or suggessions?
Thanks

---

### Post by Zidaps on 2010-02-08
Ok, so this issue is solved with the help of "gsgleason" on the ubuntu irc room.

It seems as though all directories need to be root and permissions need to be non-writable...

so do the following in terminal:
for ownership
> sudo chown -R root.root /mediafor permissions
> sudo chmod -R 755 /media*Not only does the directory need to be root, all parent directories need to be root.

so for "/media/Media/Public"... ownership needs to be root for all - media, Media and Public.

You can do that by doing the following in terminal as shown above:

> sudo chown -R root.root /media

---

### Post by lfitz on 2010-07-06
finally i found this thread!  my sftp sessions would start in the home directory not restrict viewing to the current chroot'd directory.  with this post, i was able to setup a chroot.  thanks for the info!

---

### Post by P3t3r on 2012-02-27
Is this still up to date for Ubuntu 10.04? I have the same problem and it is not solved by chown/chmod.

What I have done: 

in /etc/ssh/sshd_config: 
```
Match user bramenellen2
# The following two directives force ben_files to become chrooted
# and only have sftp available. No other chroot setup is required.
ChrootDirectory /var/www/trouw2
ForceCommand internal-sftp
# For additional paranoia, disallow all types of port forwardings.
AllowTcpForwarding no
GatewayPorts no
X11Forwarding no
```

on the command line (as root):
```
sudo useradd -d /var/www/trouw -m bramenellen
sudo passwd bramenellen
  (here 2x the password)

sudo useradd -d /var/www/trouw2 -m bramenellen2
sudo passwd bramenellen
  (here 2x the password)

sudo chown -R root.root /var
sudo chmod -R 755 /var
```

However, user bramenellen2 can no longer log in via sftp. For user bramenellen, everything works perfectly, but of course this is not chrooted.

---

