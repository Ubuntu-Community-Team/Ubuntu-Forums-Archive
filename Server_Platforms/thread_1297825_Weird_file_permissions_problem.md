---
title: "Weird file permissions problem"
date: 2009-10-22
forum: Server Platforms
---

### Post by BarryDocks on 2009-10-22
Hi there,

Having a small problem with file permissions.  

Background is a Ubuntu 8.04 server edition as a file/print/zoneminder server with 6 xp clients.  Hosting a MS Access database.  

Problem is when the access database is exported to a text file (unfortunately this needs to be done fairly frequently)the text file is not readable by other XP clients only the machine it was created by:confused:

I have the force create mask = 0777 and on inspection the file permissions are correct (ie rw by everyone) please see screen dump below of the permissions: 
[IMG]http://i731.photobucket.com/albums/ww313/jonesal2/Screenshot-UpdatetxtProperties.png[/IMG]
If I manually change the owner to another machine I can only open the file on that machine:confused:

Do I need to create a user group for this share?
Here is my smb.conf:
```
[global]
	netbios name = FileServer
	workgroup = WORKGROUP
	server string = %v
	password level = 8
	log file = /var/log/samba/log.%m
	max log size = 50
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	dns proxy = No
	security = user 
	encrypt passwords = true
	printcap name = cups
	load printers = yes
	printing = cups
	cups options = raw
	local master = yes
	preferred master = yes
	os level = 65
	name resolve order = bcast host lmhosts wins
;	hosts allow = 10.1.0.0/255.255.255.0

	kernel oplocks = no
	oplocks = false
	level2 oplocks = false
	smb ports = 139

[printers]
  	comment = All Printers
   	path = /var/spool/samba
  	browseable = no
# to allow user 'guest account' to print.
   	guest ok = yes
   	writable = no
   	printable = yes
   	create mode = 0700

[print$]
  	path = /var/lib/samba/printers
  	browseable = yes
  	read only = yes
  	write list = root

# A useful application of samba is to make a PDF-generation service
# To streamline this, install windows postscript drivers (preferably 
# colour)on the samba server, so that clients can automatically install
# them.

;[pdf-generator]
;   path = /var/tmp
;   guest ok = No
;   printable = Yes
;   comment = PDF Generator (only valid users)
   #print command = /usr/share/samba/scripts/print-pdf file path win_path recipient IP &
;   print command = /usr/share/samba/scripts/print-pdf %s ~%u \\\\\\\\%L\\\\%u %m %I &

# Case Preservation can be handy - system default is _no_
# NOTE: These can be set on a per share basis
;  preserve case = no
;  short preserve case = no
# Default case is normally upper case for all DOS files
;  default case = lower
# Be very careful with case sensitivity - it can break things!
;  case sensitive = no

# a service which has a different directory for each machine that 
# connects this allows you to tailor configurations to incoming 
# machines. You could also use the %u option to tailor it by user name.
# The %m gets replaced with the machine name that is connecting.
;[pchome]
;  comment = PC Directories
;  path = /usr/pc/%m
;  public = no
;  writable = yes

;[homes]
;	comment = Home Directories
;	read only = No
;	browseable = No

[Adrian]
	comment = Adrians Files
	path = /media/disk/adrian
	valid users = adrian, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Music]
	comment = MP3s etc
	path = /media/disk/music
	read only = No
	guest only = Yes
	guest ok = Yes
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[CCTV]
	comment = CCTV images from ZM	
	path = /media/disk/cctv
	read only = No
	guest only = Yes
	guest ok = Yes
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Staff]
	comment = Staff Files
	path = /media/disk/staff
	valid users = adrian, reception, dispensing, imaging, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Focus Data]
	comment = Data files for Focus and Clinical Records
	path = /media/disk/focus_data
	valid users = adrian, reception, dispensing, imaging, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Practice Documents]
	comment = Practice documents and files
	path = /media/disk/practice_documents
	valid users = adrian, reception, dispensing, imaging, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[HoyaLog]
	comment = HoyaLog files
	path = /media/disk/hoyalog
	valid users = adrian, dispensing, office
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Clinical Images]
	comment = Clinical image files
	path = /media/disk/clinical_images
	valid users = adrian, imaging, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[SAGE]
	comment = SAGE accounts files
	path = /media/disk/sage
	valid users = adrian, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Drivers_etc]
	comment = Windows drivers & device settings
	path = /media/disk/drivers_etc
	valid users = adrian, reception, dispensing, imaging, office, consulting
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

```

Any suggestions would be great!

---

### Post by knnniggett on 2009-10-22
Your file permissions look ok, but just to be sure go to a command prompt and do and "ls -lh".  Note any differences between the two files in question... particularly the file owner.

PS: I'm tempted to go off topic and recommend you configure your environment as a domain rather than a workgroup.  You may want to consider that.

---

### Post by BarryDocks on 2009-10-22
> **knnniggett said:**
> Your file permissions look ok, but just to be sure go to a command prompt and do and "ls -lh".  Note any differences between the two files in question... particularly the file owner..
the file owner is always the user (machine) that created the file, I have tried manually changing it without success.  I was considering setting up group access to the shares but I'm not sure it would help in this instance?

> **knnniggett said:**
> PS: I'm tempted to go off topic and recommend you configure your environment as a domain rather than a workgroup.  You may want to consider that.
to show my complete ignorance of networking, why? -this is really the only problem I have otherwise this setup works well for my small office.

---

### Post by knnniggett on 2009-10-22
What I'm getting at/wonder about is if you are dealing with a workgroup user account/password sync type problem.  In a workgroup, you have to manually verify that all the participating machines have the exact same local user accounts and passwords set on them.  In a domain, this happens automatically.

So for example, if you create a samba account called "joe" on your server, you need to make sure that account "Joe" exists on all the machines that Joe will use and make sure the password is the same.  If Joe ever changes his password then you need to manually update the pasword on all the other machines... sooner or later, every person in this IT management role asks themselves if there is a better way... the answer is yes... a domain. :)

Because I'm used to dealing with this kind of problem from a command line, rather than the gui, please do an "ls -lh" from the folder in question so I can see the differences between the two files in question.  Call it force of habit I guess.  I've gotten used to performing certain tasks a particular way.

---

### Post by knnniggett on 2009-10-22
I just had another thought which goes along the lines of the user group comment you said earlier.  I don't use samba nearly as much anymore, but I went back and looked at my smb.conf file to jog my memory a bit...

What I did for a two user system was to create a unix group called "samba" and then placed two unix accounts into that group.  On the folder I wanted to share, I made sure that folder had the samba group assigned to it, and I verified the folder had had rwx group permissions.

Once the unix accounts were created, I used the smbpasswd command to add samba accounts that match the unix accounts.

In my smb.conf file, I made each share look like this:

[archives]
        comment = Software, Drivers, etc.
        path = /mnt/LargeDataDisk/archives
        valid users = abauer, klouis
        write list = abauer, klouis
        force group = samba
        writeable = yes
        browseable = yes

Any new file that gets created under the archives share, will be owned by the samba group.  By virtue of the parent folder's group permissions of rwx, the file should have group permissions of rwx as well.  So as long as you have everyone in the same group this should work.

Lastly, I created two matching, local user accounts on the Windows machine I wanted to use.

Hopefully you can use the above info to get your setup working.

---

### Post by swerdna on 2009-10-22
The problem likely lies in the disparity between:
[LIST]
[*]the owner and group for the file update.txt (which is consulting+consulting)
[*]the owner and group for a user accessing the file (which is probably like office+office, whatever.
[/LIST]

You have a file update.txt which is readable by owner and more importantly by group=consulting.

So make all members who access the folder where update.txt resides -- make them members of the group "consulting".

Alternatively you can play with the force user and force group parameters, that should work too.

I'm flying in fog here because I don't know which directory update.txt sits in, or who owns that directory or which group it belongs to or which [stanza] in smb.conf pertains. If the adjustment of group membership doesn't work, please supply that info too.

---

### Post by BarryDocks on 2009-10-23
Thanks chaps, 

I think it is probably a group problem, I will try specifying access via groups of users rather than individuals.

Very grateful for your help/time

---

