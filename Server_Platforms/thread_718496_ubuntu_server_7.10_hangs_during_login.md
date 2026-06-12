---
title: "ubuntu server 7.10 hangs during login"
date: 2008-03-08
forum: Server Platforms
---

### Post by nicolasdiogo on 2008-03-08
hi folks,

i have a ubuntu gutsy installation with ebox which was working fine until i had a power cut and it no longer starts.

it loads the kernel and everything well but when i enter user name and password at which point it stops.

just hangs there forever.

i noticed that the only thing that is not completely correctly is the following entry;

Checking quotas...
quotacheck: Cannot create ne quotafile //aquota.user.new: File exists
quotacheck: Cannot initialize IO on new  quotafile: File exists
quotacheck: Cannot create ne quotafile //aquota.group.new: File exists
quotacheck: Cannot initialize IO on new  quotafile: File exists

but i do not think it is the problem.

but i start the system in recovery (single user) mode it starts correctly and i can check quotas successfully.

i would like to find out the reason for this installation to hang.
thus i would welcome suggestions on how to fix it.

thanks,

Nicolas

---

### Post by faulkes on 2008-03-08
Recovery mode is an entirely different ballgame in terms of what is available and running.  So I wouldn't say it's an accurate reading of the problem.

My frist suggestion would be to remove or disable quota checking and boot, if you 
get past the login prompt to a session, then you know there is an issue with quota's.

At which point, you're at a login prompt and can fix it or look for additional information.

Faulkes

---

### Post by nicolasdiogo on 2008-03-09
thanks,

i have uninstalled quota and i can successfully login.
but i need quota as other packages depend upon it.
could you tell me how to intall it but turn it off?

Kind regards,

Nicolas

---

