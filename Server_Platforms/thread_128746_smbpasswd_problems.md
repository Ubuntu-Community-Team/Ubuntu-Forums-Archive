---
title: "smbpasswd problems"
date: 2006-02-12
forum: Server Platforms
---

### Post by merlindahapypig on 2006-02-12
Hi all,

Apologies if this is a bit of a newbie question,  it could be something obvious,  but I can't think of what might be the problem, and doing a search didn't really help.

Using a bare-bones install of Ubunti 5.10 running samba as a PDC,  my users are having problems trying to change their passwords using smbpasswd (or through swat).  smbpasswd works fine as root but using it for a normal user gives me

```
root@bubbles:~# su testy
testy@bubbles:/root$ smbpasswd
Old SMB password:
New SMB password:
Retype new SMB password:
machine 127.0.0.1 rejected the (anonymous) password change: 
Error was : Account restriction.
Failed to change password for testy
testy@bubbles:/root$

```

any ideas?   I was thinking along the lines of perhaps there is a "user can't change password" flag,  but can't find any way of setting that in the samba manual. 

Anyway, any help is appreciated

Cheers,

Tim

---

### Post by Gcool on 2006-02-12
Try "sudo smbpasswd testy"

---

### Post by merlindahapypig on 2006-02-12
That should work fine,  but that's not what I want.

I want individual users to be able to change their own passwords (by logging in through either ssh or SWAT using their own username and password),  I don't want to have to logon using root every time a user wants to change their password.   Changing password through windows networking won't work either, presumably due to the same problem.

---

### Post by Novastorm on 2006-02-12
Have you tried adding the username to the command? I believe the command you tried was actually attempting to change the password for ANONYMOUS. ```
smbpasswd testy
```

---

### Post by merlindahapypig on 2006-02-12
no that doesn't work either.  It produces the same error from SWAT,  if I log in to swat as testy,  then click passwords icon and try to change it there.

I'm pretty sure i've got the correct usage for smbpasswd. 
```

testy@bubbles:~$ smbpasswd testy
When run by root:
    smbpasswd [options] [username]
otherwise:
    smbpasswd [options]
...
...

```

---

### Post by merlindahapypig on 2006-02-12
for what it's worth...

```

[global]
	workgroup = MORSE
	server string = 
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	username map = /etc/samba/smbusers
	max log size = 50
	logon script = netlogon.bat
	logon path = \\%L\Profiles\%U
	logon drive = U:
	logon home = \\%L\%U
	domain logons = Yes
	os level = 64
	preferred master = Yes
	domain master = Yes
	dns proxy = No
	wins support = Yes
	hosts allow = 192.168.
	map system = Yes
	map hidden = Yes

```

---

### Post by Iowan on 2006-02-13
I can't remember the details, but there's also a smbpasswd_chat... type command.  I saw an example *somewhere*, but don't remember where.  I have a similar setup, but haven't progressed to the unified password change stage yet.  I'll be interested to see your results!
If your users were all "sudoers", they could "sudo smbpasswd"... but that'd essentially mean they were all "root".

---

### Post by merlindahapypig on 2006-02-15
I've had a search for smbpasswd_chat and can't find anything about it on the net,  it's not installed as part of normal samba install.

I'm wondering if perhaps there is a problem with my smb.conf,  it's a bit cobbled together when I was trying to get domain logon's happening. maybe pam password change = yes has something to do with it.  I'll try changing this tonight sometime (can't do it now while users are logged on)

also,  when I set up the test system,  I think i was using tdbsam,  I'm beginning to think maybe I should change it to use tdbsam or some other user database.

---

### Post by Iowan on 2006-02-16
Anything in [HERE]("http://www.ee.mnsu.edu/~paco/using_samba/ch06_04.html") helpful?  I gotta print this off and check it later.

---

### Post by merlindahapypig on 2006-02-16
hm,, well tried it with a couple of other users and everything works now.

It was just the test user i had created for whom this problem was occuring.   wierd!

Anyway, it's going pretty smoothly now,  users can change their passwords from windows xp using  ctrl-alt-delete -> Change password

---

