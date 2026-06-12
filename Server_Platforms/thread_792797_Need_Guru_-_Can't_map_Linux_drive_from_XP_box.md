---
title: "Need Guru - Can't map Linux drive from XP box"
date: 2008-05-13
forum: Server Platforms
---

### Post by brianguy on 2008-05-13
Hopefully someone can help as this is really getting frustrating. I&#8217;ve always been a WinBlows guy and was recently convinced to forego buying Windows Home Server and install Ubuntu 8.04 Server on an old system instead. The price was right and a good opportunity to pick up some Linux, so I agreed and loaded it as my new file server. Problem so far has been that none of the disparate Guides/Docs I&#8217;ve run across fixes my problem. (I have one XP system (thru LinkSys router) and just want to use the Linux box to store mp3s/images/photos for local and remote access and php web development). 

The Ubuntu 8.04 Server load went well enough but I cannot map the drive in XP. The XP box runs Zone Alarm and all the necessary IPs have been &#8220;trusted.&#8221; I can ping the Linux box in Windows and vice versa so they do see each other. From XP, I can SSH into the Linux box (using Tunnelier) and copy files over with no problem, etc., so they are talking to one another. My XP box & Linux box both share the same Username/Password.

The problem comes when I try to actually map the drive in XP so I can just drag/drop files into the Linux share. I select &#8220;Map Network Drive&#8221; in XP, assign drive letter, etc and then get prompted for my username/pswd. I put it in but it doesn&#8217;t connect and won&#8217;t create the mapped drive. Can anyone tell me what to do next? Have been working on it for about two weeks now and am obviously missing something. Including my &#8220;smb.conf&#8221; file below.

Thanks!



[global]

   workgroup = MYNET
   server string = %h server (Samba, Ubuntu)
;   wins support = no
;   wins server = w.x.y.z
dns proxy = no
;   name resolve order = lmhosts host wins bcast

#### Networking ####

;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true

#### Debugging/Accounting ####

log file = /var/log/samba/log.%m
max log size = 1000
;   syslog only = no
syslog = 0
panic action = /usr/share/samba/panic-action %d


####### Authentication #######

;   security = user
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
;   guest account = nobody
invalid users = root
unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
map to guest = bad user

########## Domains ###########

;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

;   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
;   usershare max shares = 100
   usershare allow guests = yes

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @ntadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[mp3s]
   path = /home/MP3
   writable = yes

---

### Post by bluefrog on 2008-05-13
you need either:

issue smbpasswd -a your-user in a terminal on your computer to add a user to samba
or
change 
;security = user (commented but it is the default anyway)
by
security = share
and restart samba (sudo invoke-rc.d samba restart)

James Dupin

---

### Post by SomethingCronic on 2008-05-13
Here's some of my smb.conf I use for an open share at work.
```


[sftp]
path = /home
force user = sftpaccess
#force group = users
read only = no
guest ok = yes


```

You might want to force your users to authenticate as a user you create on the server.

---

### Post by brianguy on 2008-05-13
Thanks for the suggestions. Still doing the same thing tho. 

Is there something else I'm missing to enable Ubuntu to play nice in a Windows environment? I've spent so much time on this and no closer to having a functional file server than I was two weeks ago...

Thanks in advance!

---

### Post by HermanAB on 2008-05-13
Debug the problem using smbclient:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by johnwillis on 2008-05-13
If you have set your share level to "share" in smb.conf then you should not have any problems. Make sure the permissions on the folder you are sharing are read write and execute to be sure.

Remember when you change the share level you need to restart the samba services. If you are unsure then just reboot the box.

Once you have "share" access you should not be prompted for a password.

Also in your "MP3" share definition at the bottom - add "guest ok = yes" and "browseable = yes"

-J

---

### Post by brianguy on 2008-05-13
Tried the "debug how-to" to no avail...

It is set to "share" now. The permissions are as follows:

Owner ID 0
Group ID 0

Owner/Group/Other are all set for Read/Write/Execute

Numerical 777.....

I added "guest ok = yes" and "browseable = yes", restarted Samba services, logged off/on XP...same thing tho. 

Beginning to wonder if I have the available time to devote to Linux. Is it this time-consuming once you finally get it working? 

Thanks for the help! Any other suggestions?

---

### Post by Cadmus on 2008-05-14
I found Samba a bit thorny the first time I used it, but I recently re-installed on my HTPC and it took me about 20 minutes the second time to get everything working. After a while the logic of it seeps in.

---

### Post by brianguy on 2008-05-14
Any other problem areas to look at? :confused: I hate to think my next option is MS when I must be so close to getting this thing going...Surely there must be a detailed guide or some Linux gurus that have used 8.04 for a simple file server with XP. Maybe I need to reload the Linux box? Maybe load an older version of Ubuntu server?

Thanks in advance!

---

### Post by HermanAB on 2008-05-14
Well, you could admit defeat and read the Official Howto on the Samba web site at [http://samba.org](http://samba.org), but what would be the fun in that?

Cheers,

Herman

---

### Post by brianguy on 2008-05-14
Especially when my *real* idea of fun is a flippant response to a noob request for help...That always rocks! :guitar:

Now that I've had my fun I'll read that again and see if I can find something I've missed in there...

Thanks

---

### Post by songshu on 2008-05-14
this is one of my old configs when still having to do with XP clients

i think this should work, basically connect to ipaddres/share from XP




```
[global]
	netbios name = SERVER
	security = SHARE

[share]
	comment = share
	path = /home/share
	force group = groupname
	read only = No
	create mask = 0777
	directory mask = 0777
	guest ok = Yes
```

---

### Post by HermanAB on 2008-05-14
The problem is that Samba is immensely complicated, as you'll see when you read the manual.  Reading the manual is ultimately unavoidable and you should buy the book too.  My old copy is about 2 inches thick.

Soooo, advising you to RTFM is not a flippant comment - it is essential and good advice in this case.

---

### Post by johnwillis on 2008-05-14
If your looking for howto's brian then i'd try using [www.howtoforge.com](www.howtoforge.com)

It's got guides for all sorts of things!

Dont give up just yet. It is worth it for the stability, security and the feeling of accomplishment! :)

-J

---

### Post by brianguy on 2008-05-14
I will keep digging and will try the latest suggestions also. If anyone else has run into the same problem with 8.04 let me know - Thanks so much for the help guys! I've been researching for a couple of weeks but very little out on 8.04 as of yet.

To the "non-flippant" element that would muddy the discourse and *genuine* help on this forum (or any other) by cursing at my legitimate request, I *could* take offense but I've seen your type too many times in the past to get ruffled. Bravado is cheap over a high-speed connection...go polish your action figures...

Thanks to all others for the newbie help! :)

---

### Post by cdtech on 2008-05-15
> To the "non-flippant" element that would muddy the discourse and genuine help on this forum (or any other) by cursing at my legitimate request, I could take offense but I've seen your type too many times in the past to get ruffled. Bravado is cheap over a high-speed connection...go polish your action figures...

Thanks to all others for the newbie help! :)

LOL! well said....

---

