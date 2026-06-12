---
title: "Windows XP accessing Samba Share"
date: 2008-12-05
forum: Server Platforms
---

### Post by akafb on 2008-12-05
Hi everyone if this has been asked before then I deeply apologise.

I have a Windows 2003 Active Directory and now have some Linux machines which have until recently only been used in Development. We are looking to put one in to production and would like to use the Windows 2003 Active Directory User accounts to be the ones used to login to the Linux Servers. 

I have gone through the web and found out how to do that. I can login to the Linux Server using DOMAIN+username and I am on the server and it even creates the home drive fantastic.

So I am now logged in to the Windows XP machines and want to access this home drive which is on my Linux server. I can do start run \\linuxserver and I can then see my home drive share. If I double click on the home drive share I get a box asking for my username and password. 

I have looked at the smb.conf and it looks to be correct but I am not convinced. Running getfacl on the /home/DOMAIN/username gives me the correct rights for this user. If I run wbinfo -u I can see the user and wbinfo -g returns all the groups also.

smb.conf contains

[homes]
valid users = %S
read only = no
writable = yes
browsable = no

I have also tried to create a share called common for people to share data. I have created active directory groups called linux-users and linux-users-ro. When I do the getfacl on the /share/common I can see DOMAIN+linux-users rwx and DOMAIN+linux-users-ro rx the smb.conf is 

[common]
path = /share/common
guest ok = no
read only = no
writeable = yes
create mask = 0760
directory mask = 0760
acl group control = yes
store dos attributes - yes
browsable = yes

When I run \\linuxserver on the Windows XP pc i can see this share common. When I double click it I get \\linuxserver\common is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found.

I am running Ubuntu 8.04 server. 

Has anyone else seen this and if so how did you get around it?

Thanks

---

### Post by alan34 on 2008-12-05
This might be no help to you but are your usernames and passwords the same on your Linux server , smbpasswd and XP box exactly the same? If not I have never been able to connect to a samba share.

Have you added your users to the group common? Edit /etc/group and add the users at the end of the "common" line like

common:x:somenumber:user1,user2,user3

Here is my smb set up for my "common" share at work

[common]
	path = /home/samba/common
	force group = common
	read only = No
	create mask = 0770
	force create mode = 0770
	directory mask = 0770
	force directory mode = 0770

And here is my crib sheet to set up new users on the Linux server

TO ADD USER


adduser --shell /bin/false 'name'

passwd 'name' 'new password'

edit /etc/group    -  if new group

smbpasswd -a 'name'

edit /etc/samba/smb.conf    - add new 'group'


/etc/init.d/samba restart

Hope this is some help and sorry about the smilie :)

---

### Post by HermanAB on 2008-12-05
You are using Active Directory for login authentication, but you added a Samba server on Linux later.  So you need to configure the Samba authentication in /etc/pam.d to also authenticate against Active Directory.

---

### Post by akafb on 2008-12-08
Hi. Yes I am trying to use Active Directory to authenticate to the share. There are no linux accounts on the server except for the root and another admin.

I have added the information to the pam.d already though so I am at a loss. I can login to the linux server using an active directory account and that works fine weird.

Thanks for any other suggestions I will post the pam.d config files when I get to the site later on today.

Many thanks

---

