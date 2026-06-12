---
title: "Samba Help"
date: 2010-02-22
forum: Server Platforms
---

### Post by snake_eyes_775 on 2010-02-22
Hi Guys, I have a samba server running 9.04 jaunty joined to a Windows A[COLOR=Black]D [FONT=Verdana][FONT=Verdana]domain[/FONT][/FONT]. I need to set it up so that only members of the Windows groups have permissions to [/COLOR]the shared samba directories
 
my domain is it.domain.com and my domain controller is called win2ks
my ubuntu machine is linux1.it.domain.com
 
Users can authenticate as IT\username but I can't access my samba shares from a windows box, and I am completely lost in what should be in my smb.conf
 
I have set to different security modes and it will work, but in that case, anyone can access them. 
 
 ```

 
 [global]
workgroup = IT
realm = DOMAIN.COM
security = ADS

[admshare]
        comment = Linux Server Share for Admin Group
        path = /var/custom/shared/admin
        browsable = yes
        create mask = 0755
        writable = yes
        guest ok = yes
```If anyone has any experience with setting up samba permissions on a domain, please help me out [IMG]http://www.linuxforums.org/forum/images/smilies/icon_razz.gif[/IMG]
 
Thanks in advance!

---

### Post by joberly on 2010-02-22
What is the group name of the users you want access? You should be able to utilize the valid users parameter with groups.

Under your admshare try putting:

valid users = @groupname

---

### Post by snake_eyes_775 on 2010-02-22
I tried with the group, and I tried accessing the server at  \\serverip\admshare 

A dialog box pops up and says I don't have permissions to view that network resource.

---

### Post by joberly on 2010-02-22
I would have a look here if you haven't already. [Samba_&_Active_Directory]("http://wiki.samba.org/index.php/Samba_&_Active_Directory").

Hopefully will shed some light on the situation, and give us some feedback as well!

---

### Post by snake_eyes_775 on 2010-02-22
I used likewise-open to join to the domain, everything works fine for seeing AD users and groups, just the permissions seem to be off, I think it must have to do with the smb.conf

---

### Post by snake_eyes_775 on 2010-02-22
If I set my smb.conf to 'security = share'  I can go to \\serverip\ and it will list out all of the shares I have and it works just fine. but if I set it to 'security = ADS' it says the network path was not found, has anyone ever set this up before?

---

