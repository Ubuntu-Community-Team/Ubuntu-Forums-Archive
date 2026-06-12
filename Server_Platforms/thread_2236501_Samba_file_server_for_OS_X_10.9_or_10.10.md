---
title: "Samba file server for OS X 10.9 or 10.10"
date: 2014-07-27
forum: Server Platforms
---

### Post by neufena2 on 2014-07-27
I run a small home server and have never had a problem setting up a Samba server for my Mac clients.  Since upgrading to 14.04 (with Samba4) I have been unable to connect from either OS X 10.9 (Mavericks) or the new 10.10 (Yosemite) beta.

I've search all over the net for a guide to setting up a simple file server with Samba4 or a way to downgrade to Samba3.  Has anyone out there managed to set up a a samba server accessible from the OS X versions I mentioned?

For now I have switched to Netatalk/AFP but would prefer to get Samba sorted out.

---

### Post by Morbius1 on 2014-07-27
Please post the output of the following command from the Ubuntu machine:
```
testparm -s
```

Question: Are all your client machines running either Linux or OSX? If they are this becomes far far simpler than if you have to deal with Windows.

---

### Post by neufena2 on 2014-07-27
All my clients are OS X, no Windows to worry about here.  I've gone back the the default config then added one share, trying to keep things simple.

If I use Connect To Server in Finder with the direct smb:// url to the IP of the server then wait about 2 mins the login box appears.  I enter my login details as I would log into the linux box and then press connect.  After about 5-8 mins it will error out.

Here's the testparm -s output:

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shares]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[shares]
	comment = Shares
	path = /mnt/WD/Shares
	read only = No

---

### Post by Morbius1 on 2014-07-27
> If I use Connect To Server in Finder with the direct smb:// url to the  IP of the server then wait about 2 mins the login box appears.  I enter  my login details as I would log into the linux box and then press  connect.  After about 5-8 mins it will error out.
So you''re using ip addresses not names. Even so that's a long wait.

Did you add the linux user to the samba password database:
```
sudo smbpasswd -a user-name
```
And do the Linux permissions allow access to that shared folder by that user:
```
ls -al /mnt/WD
```
[COLOR=#0000cd]**EDIT**[/COLOR]: There was an odd bug some time ago about smb://ip-address. I never experienced it myself but the solution was to use cifs://ip-address instead. It may have been fixed by now so this may no longer be relevant.

---

### Post by neufena2 on 2014-07-28
I can use DNS if that helps but I thought I'd try as simple as possible.

I added the user and password but no change.

The /mnt/WD/Shares folder is world 777 so no permission issues.

I tried cifs:// but that did not work either. Also I believe that forces OS X to use SMB1 which is very slow.

I'm going to try and get some logs recorded to see if that give any ideas

---

### Post by Morbius1 on 2014-07-28
Using ip addresses is the most direct and eficient way. I thought this was more a host discovery question in the beginning but now it seems to be something else.

You might want to disable the firewall on Ubuntu if you've done anything with it just to see if it's in the way here.

When you say it "errors out" what is the error message you get?

[COLOR=#0000cd]**EDIT**: you can ping the ip address of the Ubuntu server , right?[/COLOR]

---

### Post by neufena2 on 2014-07-28
The more I look into it the more it seems to be an OS X issue.  The only other client I have available is Android, I tried that and it works perfectly.

I'll try and find a good Mac forum to try from that side.

---

### Post by neufena2 on 2014-07-30
I've taken my mac into my office to try with a Samba 3.6.3 server.  It connects quickly with no problems so I'm back looking at Samba 4 being the issue.

I've taken a copy of the work smb.conf and will see if matching the config on the home server makes any difference.  If not I'll be looking for a way to downgrade to Samba 3.

---

### Post by Morbius1 on 2014-07-30
All I can tell you is that in my network everything works just as it did with Samba3. In fact I set up an avahi ( the Linux Bonjour ) service file for samba so that the Linux host automatically shows up under Shares in Finder so that the OSX users don't have to use "Connect to Server". It all runs without incident.

Maybe I'm just fixated on this issue but maybe it's not Samba but what you are sharing. 

Is /mnt/WD just a folder or is it the mount point for another partition?
If it's a mount point how are you mounting it? - If it's through /etc/fstab can you post the line you are using to mount it?
And in order for access to happen the entire path has to be at least accessible to the remote user so what are the permissions of:
```
ls -dl /mnt
```
```
ls -dl /mnt/WD
```

---

### Post by neufena2 on 2014-07-30
Thanks for the help.  I really wish I could work it out. I've tried everything I can think of so far.

It is a mounted external drive.  The fstab line is:
UUID=b1f2a862-2cbc-434d-bbce-fb62999f175b   /mnt/WD    ext4    relatime 0 2

ls -dl /mnt returns:
drwxr-xr-x 3 root root 4096 Apr  6 19:27 /mnt

and ls -dl /mnt/WD returns:
drwxrwxrwx 13 root root 4096 Jul 28 19:26 /mnt/WD

which all looks fine to me.  When I get home from work I'll try a temp share on the main drive instead of the mounted drive.

---

### Post by Morbius1 on 2014-07-30
That all looks right. 

Does "WD" stand for "Western Digital" by any chance? I occasionally see posts here about problems sharing WD drives but not having one I never much paid attention.

Choosing another non-external folder to share would answer if it's a WD issue.

---

### Post by neufena2 on 2014-07-30
It does indeed (and was all working fine before upgrading) but I'll try that as the next thing.

---

### Post by volkswagner on 2014-07-30
If it's any help, I do have SAMBA4 running with OSX mavericks clients connecting.

I'm using Debian Wheezy and SAMBA4 version 4.1.0pre1-GIT-01f188a

I am able to connect using both ip address and DNS name. I'm using it as a DC so this may be a 
difference for you.  Perhaps you can try provisioning as a domain controller.

Are you able to connect using smbclient on the server itself?

Ill try a 14.04 in a VM if I have time.

---

### Post by volkswagner on 2014-08-02
> **neufena2 said:**
> I run a small home server and have never had a problem setting up a Samba server for my Mac clients.  Since upgrading to 14.04 (with Samba4) I have been unable to connect from either OS X 10.9 (Mavericks) or the new 10.10 (Yosemite) beta.

I've search all over the net for a guide to setting up a simple file server with Samba4 or a way to downgrade to Samba3.  Has anyone out there managed to set up a a samba server accessible from the OS X versions I mentioned?

For now I have switched to Netatalk/AFP but would prefer to get Samba sorted out.

Does the server show in finder's "Shared" section"
Are you using "Connect as" in finder?

FYI: I have a test VM.  It was 12.04 with out samba installed.  I upgraded to 14.04.1 then installed SAMBA using apt-get.
The server showed immediately in finder (OSX 10.9). I was able to navigate directly using finder.

I then added a simple share (using your model, but it's not on a separate disk). Then added user using "smbpasswd -a".

I can write to share without issue.  I do use "connect as" in Finder since my mac user is different than SAMBA user.

I suggest try eliminating the Western Digital mount as an issue.  Create a simple share by making a new directory inside /mnt
and/or try connecting to the server without specifying a share name.  When I browse directly to the server, I can see the "Shares" folder.
I can't connect directly/as guest (The operation can’t be completed because the original item for “shares” can’t be found.) This error occurs because
my usernames don't match and guest access is not granted in samba.

If I add the following to share definition, I can connect as guest.
```
guest ok = yes
```

If I try using a non-existent samba user, password gets rejected immediately... "shaky window response from Finder".



I'm happy to run additional tests.

Here is some info on my setup:
```
printadmin@printsrv:~$ ls -al /mnt/WD/Shares/
drwxrwxrwx 3 root       root       4096 Aug  2 09:14 .
drwxrwxrwx 3 root       root       4096 Aug  2 09:13 ..
drwxr-xr-x 2 printadmin printadmin 4096 Aug  2 09:15 Test

printadmin@printsrv:~$ ls -al /mnt/WD/Shares/Test/
drwxr-xr-x 2 printadmin printadmin    4096 Aug  2 09:15 .
drwxrwxrwx 3 root       root          4096 Aug  2 09:14 ..
-rwxr--r-- 1 printadmin printadmin    4096 Aug  2 09:15 ._Windows_Server_2012_VDI_Deployment_Guide.pdf
-rwxr--r-- 1 printadmin printadmin 1511487 Jul 14 13:22 Windows_Server_2012_VDI_Deployment_Guide.pdf
```

```
printadmin@printsrv:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[shares]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[shares]
	comment = Shares
	path = /mnt/WD/Shares
	read only = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
```

```
printadmin@printsrv:~$ sudo pdbedit -L
printadmin:1000:printer admin
```

---

### Post by volkswagner on 2014-08-04
My previous post was to confirm 14.04.1 and SAMBA should work. Perhaps something went wrong with upgrade' if it's not related to the WD drive.

---

### Post by lptr on 2014-08-24
You know that Apple did implement their own SMB client due to licence changes in Samba starting with OS X Lion? As far as I do remember one of the steps I had to do was to disable in smb.conf in [global] unix extensions = no

---

