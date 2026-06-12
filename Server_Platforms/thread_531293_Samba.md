---
title: "Samba"
date: 2007-08-21
forum: Server Platforms
---

### Post by alsehendo34 on 2007-08-21
Is there forum for Samba somewhere.

I can smbmount a share as root and write to it as root, from a remote system, but I can't write to it login to other accounts.  As you can see from the config file share for_all is set up as wide open share and in fact works this way from xp fine.

On the remote ubuntu system I do from root--and it works:
smbmount //192.168.0.100/for_all  /mnt/smb_for_all -o username=root,password=xxxxxx,rw 

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

# smb.conf is the main Samba configuration file. You find a full commented
# version at /usr/share/doc/packages/samba/examples/smb.conf.SUSE if the
# samba-doc package is installed.
# Date: 2007-06-29
[global]
	workgroup = WORKGROUP
	printing = cups
	printcap name = cups
	printcap cache time = 750
	cups options = raw
	map to guest = Bad User
	include = /etc/samba/dhcp.conf
	logon path = \\%L\profiles\.msprofile
	logon home = \\%L\%U\.9xprofile
	logon drive = P:
	usershare allow guests = Yes
	encrypt password = yes
	smb passwd file = /etc/samba/smbpasswd
	add machine script = /usr/sbin/useradd  -c Machine -d /var/lib/nobody -s /bin/false %m$
	domain logons = No
	domain master = No
	passdb backend = smbpasswd
	security = user
[homes]
	comment = Home Directories
	valid users = %S, %D%w%S
	browseable = No
	read only = No
	inherit acls = Yes
[profiles]
	comment = Network Profiles Service
	path = %H
	read only = No
	store dos attributes = Yes
	create mask = 0600
	directory mask = 0700
[users]
	comment = All users
	path = /home
	read only = No
	inherit acls = Yes
	veto files = /aquota.user/groups/shares/
[groups]
	comment = All groups
	path = /home/groups
	read only = No
	inherit acls = Yes
[printers]
	comment = All Printers
	path = /var/tmp
	printable = Yes
	create mask = 0600
	browseable = No
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/drivers
	write list = @ntadmin root
	force group = ntadmin
	create mask = 0664
	directory mask = 0775
[for_all]
	path = /home/all_users/
	read only = No
	case sensitive = No
	guest ok = Yes

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

I even tried setting all files on server share directory:

chown xxxxx
which xxxxx is the username on the remote system & there is xxxxx  linux user on the server also.  Also did smbpasswd -a xxxxx and made password same as remote.

Also tried making all files in share directory chmod 777

The thing I don't understand is after mount the file permissions on  /mnt/smb_for_all, (the remote directory change from rwx-rwx-rwx to rwx-r-x.  Is this my proplem?

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

---

### Post by mizzouxc on 2007-08-21
From what I read awhile back, smbmount was meant to be an administrative task. Thus the samba team has disabled user-mounted samba shares. That being said, when you mount a samba filesystem in the manner  you've described, only root will have r/w access because root owns the mount point. Changing ownership of the mount point won't really help either. 

I did find a link that should be of some use.

[http://ubuntuguide.org/wiki/Dapper#How_to_permanently_mount_a_samba_share](http://ubuntuguide.org/wiki/Dapper#How_to_permanently_mount_a_samba_share)

The arguments:  dmask=777,fmask=777  seem to be what you need. 

Example:

mount -t smbfs -o fmask=777,dmask=777,username=user,password=password //server/share /path/to/mount-point

or

smbmount //server/share /path/to/mount-point -o fmask=777,dmask=777,username=user,password=password

Depending on your version of samba, the arguments might be slightly different, but that is the jist of how to get it going.

**edit**

One thing I forgot to suggest. If you're going from Linux to Linux or Linux to *nix, the traditional method of file transfer is using NFS. Why emulate a Microsoft protocol to transfer files between two non-microsoft computers!?! :)

---

### Post by alsehendo34 on 2007-08-21
Thanks but I got it figured out.

Add the option uid=xxxxx were xxxxx is you local user name and all the shared files come up owner xxxxxx instead of root and all is rw by owner permissions to xxxxx

smbmount //192.168.0.100/for_all /mnt/smb_for_all -o username=<root>,password=<xxxxxx>,**uid=<my_local_username**,rw
Changing permissions with you command no dought would work also!!

"One thing I forgot to suggest. If you're going from Linux to Linux or Linux to *nix, the traditional method of file transfer is using NFS. Why emulate a Microsoft protocol to transfer files between two non-microsoft computers!?!"(mizzouxc)

Good point but I have to run it anyway as well as Etalk, because I have to run MS once in a while and my little one has the old Blue&White 9.2 mac on her desk.  Dam if I get any Linux ISOs to boot on that one.  Like you said I could have just run both nfs & samba.

My neighbor also comes in on wifi and stores his multimedia as well as jumpping through the proxie to the internet on the same server, and he will never switch to Linux.

Thanks again

---

### Post by mizzouxc on 2007-08-21
Look at yellow dog linux for your mac. I know it's blasphemy on Ubuntu forums, but if you run linux on PPC, you run yellow dog IMO.

---

