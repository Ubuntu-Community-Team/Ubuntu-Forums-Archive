---
title: "Can't get directory to write"
date: 2008-12-09
forum: Server Platforms
---

### Post by happyhacker on 2008-12-09
I have created a directory and subdirectory (office/common) and can get them to show and access on windows. Whatever permissions I give them I cannot edit files. When I open a file and attempt to save it I get windows reporting "can't create the file (Make sure the path and file name are correct)". I can edit files directly on the server. the dir. common is not in the homes dir.

I have testparm samba.conf and passes. The shares are defined as:

[COLOR="Blue"][global]
	netbios name = acdorserver1
	server string = acdor server1
	writeable = yes
	workgroup = ACDOR
	os level = 20
	hide dot files = yes
	encrypt passwords = yes
	security = user
[homes]
comment = user's private files
#valid users = @office
browseable = no
writeable = yes
wide links = no
hide dot files = yes
[common]
	path = /office/common
	comment = all our common shared files
	valid users = @office
	create mode = 777
	directory mode = 777
#	valid users = @office
[forms]
	comment = read only forms and pamplets.
	writable = yes
	valid users = @office
	public = yes
	path = /office/forms
	write list = ceo,admin,info
	available = yes[/COLOR]

I have set (in webmin) the Unix file mode to 777 and the force unix file mode is 000 but I am not sure if this is correct.

Can anyone help?

---

### Post by happyhacker on 2008-12-09
I see now that the unix permissions for these dirs need to be set right. So I have not understood this link. Is there a tutorial which explains the relationships between unix and Samba?

---

### Post by cdenley on 2008-12-09
> **cantthinkofanickname said:**
> I see now that the unix permissions for these dirs need to be set right. So I have not understood this link. Is there a tutorial which explains the relationships between unix and Samba?

The relationship between unix and samba? The permissions work the same way they do on windows. Users are restricted by share permissions (samba) and filesystem permissions (unix). If the user is not by permitted to do something by either permissions, then it will fail.

---

### Post by happyhacker on 2008-12-12
Ialsoassume now that the UNIX permissions are greater priority than Samba so these need to be set for the maximim required value. I am still a bit confussed about UNIX groups and I assume this is the same. Am I right?

---

### Post by cdenley on 2008-12-12
> **cantthinkofanickname said:**
> Ialsoassume now that the UNIX permissions are greater priority than Samba so these need to be set for the maximim required value. I am still a bit confussed about UNIX groups and I assume this is the same. Am I right?

Well, there isn't really a greater one, but Unix permissions are on a lower level. Samba won't even try to access the requested file/directory unless the user has samba permissions to do so. Then, samba will attempt to access the file/directory as the unix user which matches the samba user account. If that unix user doesn't have permission to read it, it will obviously fail.

What do you mean "maximum required value"? For unix permissions, you have read, write, and execute. If you want to read a file, you need read access. If you want to write to a file, you need write access. If you want to delete a file, you need write permission to its parent directory. You can either have your user own the file with the needed permissions, your user's group be the group owner with the needed permissions, or give everyone the needed permissions.

---

