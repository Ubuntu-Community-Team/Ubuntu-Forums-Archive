---
title: "Win XP cannot Update Roaming Profile for Samba PDC"
date: 2008-01-17
forum: Server Platforms
---

### Post by rolies106 on 2008-01-17
Dear all,

I have been tried to build PDC with SAMBA 3.0 and it's work, I can join Windows Xp Pro SP2 to my SAMBA PDC with Roaming Profiles, but when I log out windows says unable to update the profile bla bla bla .... ACCESS DENIED. I have been working this for 3 days and there's still no way out.

I have set permission to my profile share to 0777 but there still cannot update the profile out.

This is my smb.conf
```

[global]
   workgroup = MYDOMAIN
   netbios name = SERVER
   server string = %h server (Samba, Ubuntu)

   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts bind dns
   domain logons = yes
   preferred master = yes
   wins support = yes

   # Set CUPS for printing
   load printers = yes
   printcap name = CUPS
   printing = CUPS

   # Default logon
   logon drive = R:
   logon script = %U.bat
   logon path = \\%L\profile\%U


   # Useradd scripts
   # add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
   add user script = /usr/sbin/useradd -m '%u' -g users -G users
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usernod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000
   template shell = /bin/bash

   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   passwd chat debug = yes
   unix password sync = yes

   # set the loglevel
   log level = 3

[homes]
	comment = Home
	writable = yes
	valid users = %S
	browsable = no
	path = /mnt/data/home/%U

[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
   write list = root, @smbadmin


[netlogon]
	writable = yes
	admin users = Administrator
	path = /mnt/data/samba/netlogon
	guest ok = yes
	comment = Network Logon Service
	public = yes
	share modes = yes
	browsable = yes
        available = yes

[profile]
	map system = yes
	profile acls = yes
	writable = yes
        read only = no
	map hidden = yes
	path = /mnt/data/samba/profiles
	store dos attributes = Yes
	guest ok = no
	comment = User profiles
	valid users = %U
	create mode = 0777
	public = yes
	browsable = yes
	directory mode = 0777
	case sensitive = no
        available = yes

[allusers]
        comment = All Users
        path = /mnt/data/shares/allusers
        valid users = @users
        force group = users 
        create mask = 0660
        directory mask = 0771
        writable = yes
        available = no
        browsable = no
        public = no


```

And I see an error at my log.smbd
```


[2008/01/17 18:24:34, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 192.168.0.10. Error Connection reset by peer


```

Is that okay ??
I have try set permission 0777 for all my share folder but still nothing happen..??
My share folder inside my NTFS partition, I mount my NTFS partition with NTFS-3G is that okay ??

Please somebody help me... :sad: I really need these thing...:cry:

NB : Sory if my english is bad.

---

### Post by rolies106 on 2008-01-17
I Have restart my machine both server ( Ubuntu ) and client ( WinXP ) and I remove all the profile of my user in the server, and when I login to mydomain with WinXP it's look like I solved the problem cause I can Login and Logout normally, but after I try to Login again I have the same problem again with update my roaming profile.

Windows say :

```


Windows cannot update your roaming profile. Possible causes of this error include network problems or insufficient security rights. If this problem persists, contact your network administrator. 


DETAIL - Access is denied. 


```

I almost give up with this thing, is SAMBA have any problem with roaming profile or it's just because I don't know the problem is ???

:(

---

### Post by peitschie on 2008-01-17
Does it save the information after the first logout?  Like are the changes you make then stored for the next login?

---

### Post by rolies106 on 2008-01-18
I'm sory but I think I have solved the problem, I just change my current setting for profile folder at smb.conf :

```


[profile]
	map system = yes
	profile acls = yes
	writable = yes
        read only = no
	map hidden = yes
	path = /mnt/data/samba/profiles
	store dos attributes = Yes
	guest ok = no
	comment = User profiles
	valid users = %U
	create mode = 0777
	public = yes
	browsable = yes
	directory mode = 0777
	case sensitive = no
        available = yes


```

I change to :

```


[profile]
	profile acls = yes
	writable = yes
        read only = no
	path = /mnt/data/samba/profiles
	c:)omment = User profiles
	create mode = 0600
	browsable = no
	directory mode = 0700


```

And now it can saved and update the roaming profile but I'm not yet try to another user, but I think this will change for all user.

Thanks for your help.

:)

---

### Post by peitschie on 2008-01-18
I was going to enquire about the permissions lol.  Congrats on working it out (maybe) :).  Hope you've fixed it :)

---

### Post by rolies106 on 2008-01-21
> **peitschie said:**
> I was going to enquire about the permissions lol.  Congrats on working it out (maybe) :).  Hope you've fixed it :)

Now i'm sure I have solve that thing cause I have test it. so glad to see my system work :)

---

