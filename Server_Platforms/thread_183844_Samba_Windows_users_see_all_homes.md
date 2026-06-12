---
title: "Samba: Windows users see all homes"
date: 2006-05-28
forum: Server Platforms
---

### Post by Pitt Stains on 2006-05-28
Hello,

I'm running Samba on Ubuntu.  I've set up my smb.conf file as follows:

[INDENT]
[global]
	workgroup = WORK
	netbios name = BOX
	printcap name = cups
	disable spoolss = Yes
	show add printer wizard = No
	printing = cups
	guest ok = No
	deadtime = 1

[homes]
	comment = Home Directory
	valid users = %S
	path = /home/%u/remote
	read only = No
	browseable = No
	guest ok = No
[/INDENT]

There's more (a public share and a printer share), but I think this is all that's relevant.

The issue is that user bobjones can see the home shares of users joesmith and donpablo.  He can't enter them, but I don't like that they're visible.  It should be noted that all users are using the same Windows XP Professional box.  Unfortunately, I don't have a third box to see if this issue would occur if the users were on different boxes.

Any help or references are appreciated.
-Pitt

---

### Post by Pitt Stains on 2006-05-29
Anybody out there experience this too?  I tried adding:

[INDENT]browseable = No[/INDENT]

to my [GLOBAL] section, but that didn't change anything...

Suggestions please?

---

### Post by FredSambo on 2006-05-29
try changing read only to yes under homes.  get rid of browsable in global though.

[homes]
comment = Home Directory
valid users = %S
path = /home/%u/remote
read only = yes
browseable = no
guest ok = no

then restart the samba daemons.

---

### Post by FredSambo on 2006-05-29
you can also try adding 

public = no

as well

---

### Post by FredSambo on 2006-05-29
let me know how it turns out!  ;)

---

### Post by oly on 2006-05-30
you can also try putting in [$home] the $ means hide the folder so its not in the browsable list.

---

### Post by Pitt Stains on 2006-05-31
Sorry for the delay in my response.  I'm currently working two jobs, 3 days a week each, so it doesn't leave a lot of free time.

Turns out it was my own fault the homes directories were visible to users who shouldn't be seeing them.

While logged into to Windows on the client machine, I had the smb.conf configured one way (can't remember what I was doing) and the result was that shares X, Y, and Z were visible -- correctly so.  I then changed the smb.conf file so that only share X should be visible, and even after rebooting both machines (and restarting Samba) share Y and Z remained.  They couldn't be entered though.

What I found was that, if I created a new Windows user account and connected to the fileserver, only the shares I wanted them to see were visible.

So, in summary, it seems that once a particular Windows user account has seen a share, it stays visible regardless of what's in the smb.conf.  A really stupid mistake...

And yes, putting
[INDENT]browseable = No[/INDENT]
under the [GLOBAL] section achieved the expected effect: New Windows user accounts couldn't see any shares at all -- obviously not my desired environment.

Thanks, everyone.  Sorry for polluting the forum with something so inane.

---

### Post by Iowan on 2006-06-01
[QUOTE=Pitt Stains]Sorry for polluting the forum with something so inane.[/QUOTE]I've seen worse... glad you found a solution.  It still seems curious that > once a particular Windows user account has seen a share, it stays visible regardless of what's in the smb.conf.   There *should* be a way to disempower users. I wonder... if the share was disabled (semi-coloned out), would it still show up for the old users?  Wonder if the Neighborhood has TOO good a memory...

---

