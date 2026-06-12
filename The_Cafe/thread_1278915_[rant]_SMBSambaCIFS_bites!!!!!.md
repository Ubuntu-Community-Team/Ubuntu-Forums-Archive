---
title: "[rant] SMB/Samba/CIFS bites!!!!!"
date: 2009-09-30
forum: The Cafe
---

### Post by cdekter on 2009-09-30
After years of being in existence, and many iterations, it seems that these network files systems just can't be made to work simply and easily. I have tried for years to get it working on my home network, through multiple versions of Ubuntu, XP, Vista and now Windows 7. I've followed MS wizards, researched online, and yet I can't even get my two Windows 7 PCs to see each other reliably. Even entering their IP address as the hostname sometimes doesn't work. 

Can't blame it on hardware either - this has been in different houses, with different routers, and different PCs. 

What is the solution? Between Linux PCs I tend to just use SSH/SCP but what of Windows? There MUST be something simple that requires minimal config and can run without authentication.

</rant>

---

### Post by LookTJ on 2009-09-30
I suggest that you check out freenas :). I hear it is does the job quite well in sharing hard drives across the network.

If not, you can always use filezilla on Windows to use sftp.

---

### Post by blueturtl on 2009-09-30
SAMBA is trying to emulate the Windows networking model which is just unnecessarily complex.

Now that all our machines run Linux, I made the transition to NFS and boy is it simpler!

The reason I've mentioned this is that I think there is a utility for Windows that allows you to mount NFS shares. Maybe as an alternative to SAMBA you could look into that?

---

### Post by Paqman on 2009-09-30
What exactly are you trying to do? I have all my data on the network, shared over cifs, and don't have any problems.

---

### Post by cdekter on 2009-09-30
> **Paqman said:**
> What exactly are you trying to do? I have all my data on the network, shared over cifs, and don't have any problems.

Basically:
[LIST=1]
[*]Connect all PCs to same LAN (nothing fancy like subnets or anything)
[*]Activate file sharing on all PCs (using Samba etc)
[*]Share selected directories on each machine
[*]Browse network, able to see and access all machines from all other machines, no passwords required
[/LIST]

Sometimes it works, sometimes it doesn't. I've even played around with Windows 7's home group feature - it worked once, then never again. :confused:

Edit: this is actually making me sound rather stoopid... but I'm actually a software engineer and Linux admin (just not a Samba expert, and not interested in becoming one :P)

---

### Post by kevdog on 2009-09-30
Why cant you use ssh with Windows?  Install cygwin for windows -- install the sshd via cygrunsrv -- and there is your sshd!  The configuration file is exactly the same as for linux!  Basically everything is the same!

---

### Post by rickyjones on 2009-09-30
> **cdekter said:**
> Basically:
[LIST=1]
[*]Connect all PCs to same LAN (nothing fancy like subnets or anything)
[*]Activate file sharing on all PCs (using Samba etc)
[*]Share selected directories on each machine
[*]Browse network, able to see and access all machines from all other machines, no passwords required
[/LIST]

Sometimes it works, sometimes it doesn't. I've even played around with Windows 7's home group feature - it worked once, then never again. :confused:

Edit: this is actually making me sound rather stoopid... but I'm actually a software engineer and Linux admin (just not a Samba expert, and not interested in becoming one :P)

And you are sure that you do not have any software firewalls enabled between your local computers? I ask because in my 5 years of working with networks this is what always hoses up the filesharing.

Beyond that the only issue with sharing between two Windows machines that I have ran into is a username/password issue. Easiest way to ensure this is not the issue is to put the same username/password on all the Windows machines.

Hope this helps - I do this all day for a living. Also make sure that the Server service is running on the Windows machines. :)

Thanks,
Richard

---

### Post by Xbehave on 2009-09-30
> **cdekter said:**
> Connect all PCs to same LAN (nothing fancy like subnets or anything)
Sounds like a router problem, go into the router settings and check that dhcp is all set up right, if it is still not working simply assing static IPs to any box having trouble
> Activate file sharing on all PCs (using Samba etc)
Setting this up on samba wasn't to hard (kde had a nice config tool, editing smb.conf isn't too hard either), my friends never figured out how to do it on vista/7 from windows though, i think [this]("http://www.home-network-help.com/simple-file-sharing.html") may help

---

### Post by openfly on 2009-09-30
Every moden OS on earth has NFS support.  EXCEPT WINDOWS.  Anyone want to explain that?

---

### Post by hanzomon4 on 2009-09-30
> **openfly said:**
> Every moden OS on earth has NFS support.  EXCEPT WINDOWS.  Anyone want to explain that?

I hear that nfs is insecure compared to samba

---

### Post by cdekter on 2009-09-30
> **rickyjones said:**
> And you are sure that you do not have any software firewalls enabled between your local computers? I ask because in my 5 years of working with networks this is what always hoses up the filesharing.

Well I believe the default firewall settings are enabled on all the machines (i.e. Windows built in firewall, UFW on the Ubuntu machines). I had assumed that activating Samba/SMB would reconfigure the firewall for me (I'm pretty sure Windows does that, and reasonably sure Ubuntu does it too). Having said that, I haven't tried with the firewalls turned off.

---

### Post by rickyjones on 2009-10-01
> **cdekter said:**
> Well I believe the default firewall settings are enabled on all the machines (i.e. Windows built in firewall, UFW on the Ubuntu machines). I had assumed that activating Samba/SMB would reconfigure the firewall for me (I'm pretty sure Windows does that, and reasonably sure Ubuntu does it too). Having said that, I haven't tried with the firewalls turned off.

While Windows and Ubuntu should reconfigure the firewall to allow the filesharing traffic I would highly recommend disabling all firewalls for at least the testing portion. If you are on a home network behind a NAT router you should stay pretty secure by default.

Let me know the results :)

Thanks,
Richard

---

### Post by kimda on 2009-10-01
I work with Samba at home and also professionally. Have you read the troubleshooting part of the samba howto guide? 

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/troubleshooting.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/troubleshooting.html)

Also you can set the log level higher in Samba to find possible errors.

---

