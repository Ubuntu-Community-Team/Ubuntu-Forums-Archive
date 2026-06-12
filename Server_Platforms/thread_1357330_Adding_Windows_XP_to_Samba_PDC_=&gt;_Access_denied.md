---
title: "Adding Windows XP to Samba PDC =&gt; Access denied"
date: 2009-12-17
forum: Server Platforms
---

### Post by Stan* on 2009-12-17
I followed [this tutorial (link)](https://help.ubuntu.com/9.10/serverguide/C/samba-dc.html) to setup a Samba PDC on Ubuntu server 9.10. Everything is setup and I edited the smb.conf to use a WINS-server.
The server has a static IP (10.0.0.1) and the client (Win XP) has also a static IP 10.0.0.10. When I try to add the client to the domain and login with the main account or with root I get an error message  "access denied".

What can be the cause?

---

### Post by Donlup on 2010-02-01
Same problem here could some one help pls?
Its has to be the add machine script or the /srv/samba/netlogon/ homes share thats causing problems.

---

### Post by Stan* on 2010-02-01
I solved it, I forgot to login with the root. I gave root a password by:

sudo passwd root

But then you must logout (exit) and login as root. Then the root account is fully enabled and you can add computers to your domain.

At least in my case, I don't know if you tried it yet. What steps did you take till now?

---

### Post by Donlup on 2010-02-01
Man i could kiss ya ;)
 
4 days of trying, it must how ever be a user level error perhaps samba doesent use sudo for adding the machine or doesent know how to use sudo with a pass or something.
Or maybe its the netlogon share rights it.
Any ways thanks a lot! :)

---

### Post by Stan* on 2010-02-01
I'm glad I could help :)

---

### Post by Donlup on 2010-02-01
Bonus qustion :)
Did you have a problem after adding the computer?
I added a winxp pc to the domain, rebooted it and it complains that theres two computers with one name and now cannot contact the domain.
It might be the fact i am running them on virtual pcs

---

### Post by Stan* on 2010-02-01
Is your server in a virtual machine as well? In my case I had a pc running Ubuntu server and 2 virtual machines on my computer (XP and Vista) that are connected to the domain. VMware (for Mac) handled it very well.
Does it help if you login locally and change the computer's name?

---

### Post by Donlup on 2010-02-01
Ya its a virtual one to, I will have to test on the real machines in school tomorrow, they dident fit in my backpack ;)
Thanks again for your help

---

### Post by Donlup on 2010-02-04
Did you ever test the server with another user then root?
Cause the way i see it from the guide mentioned the profiles should be stores like this
 
logon path = [\\%N\%U\profile]("file://\\%N\%U\profile")
srv/samba/netlogon/"username"/profile
 
and should have a home drive mapped to
logon home = [\\%N\%U]("file://\\%N\%U")
srv/samba/netlogon/"username"/
 
BUT, what happens is that it ignores the %u and dumps every profile in srv/samba/netlogon/profile and maps every user to srv/samba/netlogon/

---

