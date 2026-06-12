---
title: "hybrid network"
date: 2011-04-24
forum: Server Platforms
---

### Post by menglim on 2011-04-24
We have a small network in the office that uses linux as its main server doing SAMBA PDC with client workstations primarily using MS Windows

Now we're planning to migrate some(not all) workstations into linux. 

What's currently happening with the windows workstation is they login to the domain, and gain access to mapped drives located in the server.

For linux workstations, is there a way for them to login to the and basically have access to some sort of mapped drives that are assigned to them similar to windows users with the same server?

---

### Post by Paddy Landau on 2011-04-24
Generally, Ubuntu should automatically see any other Linux machines on the network.

Additionally, provided you have Samba installed, it should see any other Windows machines on the network. Note that Samba emulates a Windows network drive, which is why Windows can see the Linux server.

You do not map a "drive" as such in Linux. You always map to a directory. Generally, Ubuntu will do this automatically. Just go to Places > Network, and you should find your network drives there.

---

### Post by menglim on 2011-04-24
but is it possible to let linux users login and automatically authenticate against the list of users in the server?

---

### Post by Ryan Dwyer on 2011-04-24
Yes. I played around with this setup using virtual machines a while ago and found it somewhat complicated.

If memory serves me correctly, I think I got it working by using an LDAP backend for the Samba server and adding a PAM module on the client machine to auth via the remote LDAP with fallback to the local /etc/passwd.

The whole process is a bit dodgy to be honest. I wouldn't recommend it. An easier solution would be to have the Linux clients log in locally and use an init script to mount Samba drives. You could investigate storing the init script on the server so you can manage it from a central location.

---

### Post by Vegan on 2011-04-24
I use SAMBA extensively in my shop and it works for me. It has lots of ability to be easy to setup or secure enough for corporate use.

I suggest install SAMBA generally as its that helpful.

---

### Post by Ryan Dwyer on 2011-04-24
This looks like it might work:
[http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html](http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html)

---

### Post by menglim on 2011-04-24
I think likewise open could be it. but need to test it out first :)

assuming that linux workstations would need to authenticate with linux running samba.

am reading here  
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/pam.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/pam.html)

that you can use pam to authenticate against Samba? if its correct, is there a way to run a netlogon script that mounts directories onto the computer where each user logs in from?

the /etc/fstab route is not so feasible if multiple users share a pc

---

