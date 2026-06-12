---
title: "Validate samba shares using Active Directory (almost there)"
date: 2010-06-01
forum: Server Platforms
---

### Post by wormie_dk on 2010-06-01
Hi there,

I have been working with setting up active directory on a Ubuntu 8.04 LTS machine and I think I am almost there.

I can log in to the machine using AD credentials
I can use wbinfo -g to get a list of groups
I can use wbinfo -u to get a list of users
getent passwd works
Using windows I can log on to the samba host and see my shares.
This share works:
> [rd]
  comment = rd share
  path = /home/shares/XX
  valid users = @DOMAIN+USERS
  writable = yes
  browseable = yes

This share does not work (I can see it but am not allowed to open the folder):
> [homes]
   comment = Home Directories
   browseable = No
   read only = No
   valid users = %S

And assigning individual users to a share does not work either
> [test]
   comment = test
   browseable = Yes
   read only = No
   valid users = DOMAIN+USER1 DOMAIN+USER2

Output of smbclient -U USER -L 127.0.0.1
> Password: 
Domain=[DOMAIN] OS=[Unix] Server=[Samba 3.0.28a]

	Sharename       Type      Comment
	---------       ----      -------
	rd              Disk      rd share
        test            Disk      test
	IPC$            IPC       IPC Service (XX server (Samba, Ubuntu))
	USER          Disk      Home Directories
Domain=[DOMAIN] OS=[Unix] Server=[Samba 3.0.28a]

	Server               Comment
	---------            -------

	Workgroup            Master

Any ideas as to how I can single user authentication and user directories to work?

---

