---
title: "NFS fstab"
date: 2008-02-07
forum: Server Platforms
---

### Post by expatCM on 2008-02-07
I can mount an nfs share from the client as a root user.  This does not work if I try to mount from the fstab.

I guess this is something to do with needing to  add "no root squash" but do I add it to the exports file on the server or the fstab on the client?

---

### Post by astrotech226 on 2008-02-07
Can you post the command you are running from the command line as well as your fstab entry?  Also, what OS is the nfs server running?

The no_root_squash should go in the exports file on the server.  Something like this:

/path/to/nfs/share           *.yourdomain.com(rw,acl,no_root_squash)

This will allow any host on your domain to mount the nfs share as root and keep any access control lists intact.

Then run "exportfs -a" to re-export the file without bouncing the nfs service.

---

### Post by expatCM on 2008-02-07
Thanks for your response. Ubuntu server 7.10.   I will post the information you requested in a few hours.

I have just learned about uid's and compared the user id on both the server and the client and they are different which no doubt is why it does not work.

I read that nis is the way to solve this but I also read that this is now considered to be out dated.

Do you think I should install nis or is there another package I would be best to focus on?

---

### Post by astrotech226 on 2008-02-07
I use LDAP for all of my user and group mappings.  It's convenient because it also works with Samba, so if you ever have need for a Windows domain controller, all of your data is in one spot.

LDAP is a little intimidating at first, but has some nice features.  It has the ability to replicate it's data to multiple backup servers.  Most LDAP clients already support failing over to backup servers if the primary is down.  You can even do simple load balancing and writes to the LDAP database work transparently with its own referral system.

As far as the NFS, UIDs are important, but it should still mount.  Are you trying to mount as a specific user from fstab?  And are you restricting to a particular user on the server side?

Another key piece to this I've discovered is that the client needs to have a reverse DNS entry.  So if your hostname is "hostname", the nfs server needs to be able to resolve the IP address back to "hostname".  If that doesn't happen, you will get  permission denied.  I don't think this is your problem as you stated that it works from the command line as root.

---

### Post by expatCM on 2008-02-10
I have just taken a look though LDAP and yes, I can see what you mean when you say that it is a bit intimidating .....  Not sure that this is what I need though since I have zero contact with Windows and so I would only need a small part of what was there  ....

I am trying to first get things working with NIS.  I seem to be getting a message of 

YPBINDPROC_DOMAIN: Domain not bound

but I cannot find out what this message actually means.  Does it mean that the server is not running or cannot be accessed or that the client is not correctly set up?

On a different level, I am reasonably sure that NFS is set up correctly since if I open a file browser using Sudo then the shares appear as intended.  If I open a file browser as a normal user I get 

List Failed - Access Denied.

Which would seem to suggest a permissions error but I cannot quite see how..

---

### Post by astrotech226 on 2008-02-10
It does sound like a permission problem.  Like you said earlier, it's most likely a UID mismatch problem,  Is it possible to set the UID the same on both machines?  If you can't do that, you'll probably have to do something a little different with the permissions on the nfs server. 

Ubuntu doesn't support access control lists over nfs by default, but it's not too big a deal to recompile the kernel to include it.  What that would allow you to do is keep the permissions the same on the nfs server and simply add another "user" (or multiple users) to the permissions on the nfs server.  This might be a bad solution because if you make the UID of the client have permission to the files, whoever gets the same UID on the server will also have permission.  This would be an unexpected and unwanted result.  All depends on your situation. 

As far as the NIS stuff, it's been forever since I've monkeyed with it.  I remember there are some commands like ypbind and ypset.  You have to take one machine and set up the nis domain and get the service running.  Every nis client need to set the same nis domain.

---

