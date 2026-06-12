---
title: "fileserver samba deletes files and folders"
date: 2008-11-20
forum: Server Platforms
---

### Post by silviorelli on 2008-11-20
Hello
Last mont I set up a fileserver inside an office, no domain, no DC, just shares of users with different properties/permissions.

I can't understand why some files and subfolders *disappeared* randomly from the shares, on the filesystem: this is not the classic wrong permissions problem, file and folders are deleted physically from the disk!!

Samba log files are clean, no error on the raid..
For now I've been able to recover lost files from a NAS, every night cron makes an rsync --archive (without --delete) from the shares to the NAS.

What's happened?
The distro is a Ubuntu server 8.04

As a solution I updated samba (last update was done 20 days ago) and moved the shares from the users home to a /fileserver folder with all the shares inside.

I don't know it this will work, I only hope it will not lose files/folders in the next days.
What could it be???? A bug in samba?? rsync???

Please help, I really don't know what's the problem.

This is part of my smb.conf


[global]
	server string = Samba
	workgroup = SEDE
	obey pam restrictions = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	ldap ssl = no
	panic action = /usr/share/samba/panic-action %d
	invalid users = guest
	users = massimilianop, simones, ceciliac, paolog, laviniap, alessandrog, giovannis, ospite, antonellam, daviden
	admin users = paolog
#	include = /etc/samba/dhcp.conf
	browsable = Yes
	browse list = Yes
	wins support = Yes
	domain master = Tes
	local master = Yes
	preferred master = Yes
	name resolve order = wins bcast
	create mask = 0777
#	force create mode = 0777
	directory mask = 0777
#	force directory mode = 0777
	force group = summa


[archivio]
	comment = Archivio
	path = /fileserver/archivio
	read list = massimilianop, simones, ceciliac, paolog, laviniap, alessandrog, giovannis, ospite, antonellam, daviden
	write list = paolog
	read only = No

[lavori]
	comment = Lavori in corso
	path = /fileserver/lavori
	read list = massimilianop, simones, ceciliac, paolog, laviniap, alessandrog, giovannis, ospite, antonellam, daviden
	write list = massimilianop, simones, ceciliac, paolog, laviniap, alessandrog, giovannis, ospite, antonellam, daviden
	read only = No

[paolog]
	comment = File personali di Paolo
	path = /fileserver/paolog
#	read list = massimilianop, simones, ceciliac, paolog, laviniap, alessandrog, giovannis, ospite, antonellam, daviden
        read list = paolog
        write list = paolog
        browsable = No
        browse list = No
        valid users = paolog
	invalid users = massimilianop, simones, ceciliac, laviniap, alessandrog, giovannis, ospite, daviden

[alessandrog]
	comment = File personali di Alessandro
	path = /fileserver/alessandrog
	read list = massimilianop, simones, ceciliac, paolog, laviniap, alessandrog, giovannis, ospite, antonellam, daviden
	write list = alessandrog, paolog

[massimilianop]
	comment = File personali di Massimiliano
	path = /fileserver/massimilianop
	read list = massimilianop, simones, ceciliac, paolog, laviniap, alessandrog, giovannis, ospite, antonellam, daviden
	write list = massimilianop, paolog

and the other shares are the same as the last one

---

### Post by smileypaul on 2008-11-20
Nasty user knows how to use ssh?

check

cat /var/log/auth.log | grep Accepted

that will show you all of the last succesful logins..(last will also work)

I doubt its a bug, probably just someone doing something. Check the log files, secure the permissions, remove users out of the sudo (admin) group, Make sure ssh denies root log in, etc etc..

---

### Post by silviorelli on 2008-11-20
Thankyou
Maybe.. I'll verify that. But I'm pretty sure this users aren't able to write a line on a shell.

Is there a way to log all the actions (copy, edit, move ecc ecc) done by users on the shares?

If someone has other ideas about how the files could be disappeared/lost/deleted, it would be very appreciated.

---

