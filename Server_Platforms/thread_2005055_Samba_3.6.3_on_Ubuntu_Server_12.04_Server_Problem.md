---
title: "Samba 3.6.3 on Ubuntu Server 12.04 Server Problem"
date: 2012-06-16
forum: Server Platforms
---

### Post by glsjr on 2012-06-16
I upgraded a machine that had been configured as a PDC running Ubuntu Server 11.04 (and whatever version of Samba was default in July 2011) to the new 12.04 Server LTS, which has Samba 3.6.3 (I did a fresh install).  I restored the existing samba configuration file (smb.conf), and re-created the user accounts (both adduser and smbpasswd).  The PDC serves roaming profiles to user on Windows 7 Professional and Windows XP Professional computers.

I then removed each computer from the domain (changed to workgroup "WORKGROUP") and then re-added three computers to the domain.  Each initially worked, connecting to the domain, and downloading the user's roaming profile.  I was able to logon and logoff successfully a few times, then started getting the following error: "There are currently no logon servers available to service the logon request.".  

When that error appeared the first time, I was able to reboot the client (Win7) machine, and then logon to the domain successfully once, and then the error message would reappear at the next attempt to logon (a few minutes later).  This worked two or three times, and has since failed - I get the same error message no matter what now.

I am still able to ping and SSH into the PDC, so connectivity is still there, just not when I try to use it as a PDC!

Does anyone know if there is anything in either Ubuntu Server 12.04 LTS or Samba 3.6.3 that has changed that would cause this strange behavior?

Thanks in advance for any help that you can provide!  I have to have this server back up and running by Monday morning, even if it means rolling back and re-installing 11.04.
Greg

---

### Post by alfredo.marchini on 2012-06-21
Hi,
I made some particular configurations on this samba,
I migrated a w2k3 (w2k style) domain to samba (I know the vampire is only for NT), I made a partial copy (to retrieve sid) and then finished to configure as normal PDC.
Everything worked fine until I shut down the W2k3 pdc. After no more login "No domain found".
I copied the samba configuration from a working 10.04 lts server of another customer.
I found an error on charset param (have to disable it) and tried to remove and readd the xp client to the new domain.
Nothing. No logon. "Domain not available".
Tomorrow I will try to create a new domain (now that all files and permissions are copied I can destroy everything and reset the wins and everything under /var, but I my experience tell me that the problem is another... 
So I will tell you tomorrow...

---

