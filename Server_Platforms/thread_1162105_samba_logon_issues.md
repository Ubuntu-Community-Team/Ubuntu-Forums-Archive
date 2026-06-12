---
title: "samba logon issues"
date: 2009-05-17
forum: Server Platforms
---

### Post by lenswipe on 2009-05-17
Hey there guys


I just managed to setup a samba domain controller (after all this time) and i got it to work (kinda) asin i can logon to it with all clients etc etc etc...


*however* 


When i logon i get a message telling me that my roaming profile could not be found (happens for all my users) and another message saying something like the domain controller could not be found and im being logged on with a temp profile.

As this happens *before* i get logged on i am unable to show you any screenshots for this (sorry) also windows is putting like 5 commas after the user names on the start menu

eg

"John Smith,,,,,,,"

like that, anyone have any ideas about this?

My smb.conf can be found here:

[http://pastebin.com/f12e6096e](http://pastebin.com/f12e6096e)


does anyone have any idea whats going on here?

Btw: the guide i followed for creating this domain controller was found on the ubuntu site.

Regards

-lenswipe

---

### Post by lenswipe on 2009-05-17
ok heres something really weird, its working for my account now, but not for my dads account.

For my account i can logon and log off perfectly and save setting etc, for my dads account however it still gives the cannot find your profile message, any ideas?

-Lenswipe

---

### Post by lenswipe on 2009-05-17
still having some issues with this guys, when i run my logon script windows says to me in the cmd window:

> preparing to delete old drive mappings
There are open files and/or incomplete directory searches pending on the connect
ion to Z:.

Is it OK to continue disconnecting and force them closed? (Y/N) [N]:


anyone know how to get rid of this?

also my user name has about 5 commas after it for no descernable reason....

I would appreciate any help with this


-Lenswipe

---

### Post by lenswipe on 2009-05-18
bump

---

### Post by Gone fishing on 2009-05-18
I note that your add machine script looks quite different to mine and am wondering about whether the machine accounts are being made and if the permissions correct also your profiles are stored 


path = /var/lib/samba/profiles and mine 

path = /home/samba-ntprof although I don't see why that should be a problem. If its any help my samba conf looks like:


```

# Global parameters
[global]
	logon drive = H:
	domain master = Yes
        # winbind use default domain = Yes
	map to guest = Bad User
	username map = /etc/samba/smbusers
	encrypt passwords = yes
	logon home = \\%L\%u\.win_profile\%m
	wins support = Yes
	printcap cache time = 750
	cups options = raw
	#ldap machine suffix = ou=Computers
	logon script = logon.bat
	#ldap suffix = dc=example,dc=com
	workgroup = SCHOOL
	logon path = \\%L\profiles\%u\%m
	os level = 65
	printcap name = cups
	security = user
	domain logons = Yes
	preferred master = Yes
	add machine script = /usr/sbin/useradd  -c Machine -d /var/lib/nobody -s /bin/false %m$

[netlogon]
	path = /usr/local/samba/lib/netlogon
	browseable = No

[profiles]
	path = /home/samba-ntprof
	read only = No
	create mask = 0600
	directory mask = 0700
	browseable = No

[homes]
	writeable = yes
	veto files = /*.scr/*.scf/*.msi/*.bat/*.com/*.ade/*.adp/*.asp/*.asx/*.chm/*.cmd/*.cpl/*.vbs/*.hta/*.mp3/*.inf/*.ins/*.isp/*.js/*.jse/*.exe/*.dll/
	
[pdf]
	comment = PDF creator
	path = /var/tmp
	create mask = 0600
	printable = Yes
	print command = /usr/bin/smbprngenpdf -J '%J' -c %c -s %s -u '%u' -z %z

[printers]
	comment = All Printers
	path = /var/tmp
	create mask = 0600
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/drivers
	write list = @ntadmin, root
	force group = ntadmin
	create mask = 0664
	directory mask = 0775

```

Don't now if thats perfect but it is working. Although I hoping to use LDAP soon.

---

