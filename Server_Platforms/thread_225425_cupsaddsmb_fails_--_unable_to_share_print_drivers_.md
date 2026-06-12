---
title: "cupsaddsmb fails -- unable to share print drivers from samba"
date: 2006-07-29
forum: Server Platforms
---

### Post by sgla1 on 2006-07-29
I am running dapper with all updates on a generic wintel pc.  Cupsaddsmb fails with the following error:

```
Unable to copy Windows 2000 printer driver files (1)!
Running command: smbclient //localhost/print$ -N -A /var/spool/cups/tmp/44cb9359ab2bb -c 'mkdir W32X86;put /var/spool/cups/tmp/44cb9354030f8 W32X86/HPofficejet.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'
Domain=[FPIG] OS=[Unix] Server=[Samba 3.0.22]
NT_STATUS_NETWORK_ACCESS_DENIED making remote directory \W32X86
NT_STATUS_OBJECT_PATH_NOT_FOUND opening remote file \W32X86/HPofficejet.ppd
NT_STATUS_OBJECT_PATH_NOT_FOUND opening remote file \W32X86/ps5ui.dll
NT_STATUS_OBJECT_PATH_NOT_FOUND opening remote file \W32X86/pscript.hlp
NT_STATUS_OBJECT_PATH_NOT_FOUND opening remote file \W32X86/pscript.ntf
NT_STATUS_OBJECT_PATH_NOT_FOUND opening remote file \W32X86/pscript5.dll

```

my smb.conf is a follows:
```
 [global]
        workgroup = fpig
        netbios name = sara-desk
        server string = lan printer server
        hosts allow = 192.168.1.
        security = share
        load printers = yes
        printing = cups
        printcap name = cups

[share1]
        path = /sharedstuff
        comment = files for everyone
        read only = no
        browseable = yes
        guest ok = yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        browseable = yes
        printable = yes
        writable = no
        guest ok = yes

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        browseable = yes
        guest ok = no
        read only = yes
        write list = root 
```

the /var/lib/samba/printers directory structure is as follows:
ls -lR /var/lib/samba/printers
/var/lib/samba/printers:
total 8
drwxrwxrwx 2 root root 4096 2006-07-11 05:48 W32X86
drwxrwxrwx 2 root root 4096 2006-07-11 05:48 WIN40

/var/lib/samba/printers/W32X86:
total 0

/var/lib/samba/printers/WIN40:
total 0

the cups drivers were downloaded from the cups website and installed with the included makefile to /usr/share/cups/drivers.  That directory is as follows (windows ps drivers added also):
ls -lR /usr/share/cups/drivers/
/usr/share/cups/drivers/:
total 1432
-rw-r--r-- 1 root root    803 2006-07-26 15:25 cups6.inf
-rw-r--r-- 1 root root     72 2006-07-26 15:25 cups6.ini
-rw-r--r-- 1 root root  12568 2006-07-26 15:25 cupsps6.dll
-rw-r--r-- 1 root root  13672 2006-07-26 15:25 cupsui6.dll
-rw-r--r-- 1 root root 129024 2006-07-26 15:45 ps5ui.dll
-rw-r--r-- 1 root root 455168 2006-07-26 15:45 pscript5.dll
-rw-r--r-- 1 root root  26038 2006-07-26 15:45 pscript.hlp
-rw-r--r-- 1 root root 792644 2006-07-26 15:45 pscript.ntf

I don't understand where cupsaddsmb is trying to create the \W32X86 directory or why there is a permission problem.

This error seems similar to this thread:
[http://www.ubuntuforums.org/showthread.php?t=102408&highlight=cupsaddsmb]("http://www.ubuntuforums.org/showthread.php?t=102408&highlight=cupsaddsmb")
and possibly to this thread:
[http://www.ubuntuforums.org/showthread.php?t=82828&highlight=cupsaddsmb]("http://www.ubuntuforums.org/showthread.php?t=82828&highlight=cupsaddsmb")

---

### Post by zimm0who0net on 2006-10-31
This is pretty old, but I figured I'd put something here in case people search
1. Don't use the root account as your printadmin.  Instead create a new printer administrator account and use smbpasswd -a <username> to stick it into the SMB users.
2. Try this smb.conf:
```

[global]
	workgroup = INT
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad Password
	null passwords = Yes
	enable privileges = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	printcap name = cups
	dns proxy = No
	ldap ssl = no
	eventlog list = /var/lock/samba
	lock directory = /var
	panic action = /usr/share/samba/panic-action %d
	guest ok = Yes
	printing = cups
	print command = 
	lpq command = %p
	lprm command = 

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	write list = root, printadmin

```
3. Make sure the associated directories listed above actually exist and are writable by user printadmin.  (You can chmod -R 666 on them, or else put the printadmin user into the lpadmin group and chmod -R g+w  and chgrp -R lpadmin on them)
4. use this command to do the cupsaddsmb
```
cupsaddsmb -U printadmin%<your_pass> -a -h localhost -v
```

---

### Post by guitard00d on 2006-11-23
Did anybody ever try this and make it work? So far, I'm still getting the "**Unable to copy Windows 2000 printer driver files (2)!**" error every time I run the above cupsaddsmb example command. The **/var/lib/samba/printers/** directory (and all sub-directories) are writeable by the printer admin, I've even tested that by creating a text file there with nano under that account just to be sure.

](*,)

---

### Post by paradexes on 2008-02-27
This did not work for me. I am still getting the copy errors. Has there been a definitive solution for this anywhere?

---

### Post by astrotech226 on 2008-02-27
If you are trying to install print drivers, have you tried it from a Windows computer yet to see what it does?  Here's how I do it:

1) Click Start -> Run
2) \\<linux server hostname here>
3) Double Click "Printers and Faxes" (THIS STEP IS IMPORTANT!!)
4) Right click the printer you want to install the driver and click "Properties".
5) It should ask a question about installing the driver, tell it "No".
6) You will see the print driver properties.  Click the "Advanced" tab.
7) If you have used this print driver on this computer before, just click the "Driver" drop down and select it.  If not, go through the usual process of installing the driver.
8- Click "Apply".  This will now install the drivers to the print$ share.

This might tell you volumes about what is going on in the backend.  Also, set your log level to 3 in smb.conf and check your /var/log/samba/* stuff.

---

### Post by astrotech226 on 2008-02-27
One more thing I noticed.  Your write list may not be flexible enough.  I've had root get mapped to administrator using ldap as a backend if the nsswitch.conf file is configured a certain way.  If that's the case, root wouldn't be able to write to the readonly share.

```
   write list = @domadmins root administrator
```

---

### Post by paradexes on 2008-02-28
Thanks I will give that a try. My issue has mainly been the errors when copying over the files. But I did try the portion of installing the printer from Windows. I am trying to push the driver down from the server. Obviously since cupsaddsmb is failing to copy over, I am dealing with this issue. 

But I will make the changes to the smb.conf and see what my results are and report back. Thanks.

---

### Post by paradexes on 2008-02-28
Well with the help of your excellent advice and a coworkers previous experience with this in another company. We have discovered the main problem. But your advice certainly helped in that direction. It was mainly a permissions problem. I am sorting out the details. But your advice certainly exposed the problem and how to best deal with it. 

Thanks :D

---

