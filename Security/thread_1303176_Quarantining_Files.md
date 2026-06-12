---
title: "Quarantining Files"
date: 2009-10-27
forum: Security
---

### Post by TrentMB on 2009-10-27
Ok this may sound convoluted and I am not sure if people have tried this before so bear with me.

I am in the process of building a server with some spare parts I obtained and was wondering about how to quarantine files.

I right now have three 18.2GB scsi drives and a Card.

I want to make 1 by itself as the system drive and application drive
The other 2 I want to software raid 1 as the web server content (svn server etc).

Down the road I would like to buy a 1TB drive so the server can also be used for local backups similar to freenas, however I want this drive/partition to be near impossible if not impossible to access from the outside world, is this possible and how would I do this?

Is it possible to limit viewers based on ip address so they have to be in my local network in a certain range to view it and also login.
If I installed freenas on vmware server and ran a virtual harddrive in there would that work (does free NAS inherently block the outside world or is there a way to block it?)

Effectively I want the most fool proof way to quarantine a hard drive partition so it can only be locally accessed (Anything I want remote access on will be on the scsi drives (or another partition on the 1TB) I would like it quarantined to the point that even if I or a hacker SSHed from the neighbors house I could not access the files unless I tunneled through a vpn through another computer or similar.

Please throw out ideas.

Thanks,

Trent

Edit - So far I am thinking 4096 bit SSH key as one deterrent as I only have to use one client computer and it will only be connecting to one host, to keep the SSH safe from external threats.  Though it will be a pain.

---

### Post by TrentMB on 2009-10-28
I am starting to think making files only accessible from local IPs may be difficult if not impossible.

So for security right now I am thinking of complex user name and password and running Fail2Ban/DenyHosts or both on about 5-10 screwups

Any other security measures?

---

### Post by HermanAB on 2009-10-28
Just change the user and group of the directory to root.  Then users cannot access it.

---

### Post by TrentMB on 2009-10-28
The problem mostly arises as I want it accessible like a NAS device to the local network (similar to free nas or something)

Im not quite sure how NAS would work but does this work

Two accounts one without ssh abilities one with them

Folder that I only want as NAS is not accessible by the ssher but is accessible by the non ssher and only root can change the user permissions on it.  Then again I suppose I would need to ssh to connect to the server to get at the files :/

Then in windows / osx is there a way to make it so it is as simple as clicking a button to access the storage instead of making other users go through a painful login system.

Edit: If i blocked off the folder from the ssh user and made it (the nas folder) only accessible over SMB could that work?  Is there a way to limit ips an account can be sshed to from? ( I suppose limiting the account using this, AllowUsers myuser@192.168.1.* in the sshd file could work to limit it to inside my subnet and only all that user group to access the folder (is there a way to restrict the sshable account from changing folder permissions?))

Edit 2 - So it appears I could chown the folder so only the user that is in the 192.168.1.* line could access it and it appears only root can change it...

So, with a very strong root password, root account disabled (this forces me to use sudo correct) and chowning the folder and making the account which can access it only sshable from 192.168.1.* keeping me safe.  And by having root acct disabled (provided this allows sudo) they couldn't brute force into the server as easily due to Fail2Ban/DenyHosts

---

### Post by Lars Noodén on 2009-10-29
It sounds like Samba is the way you want to go for that.  
You can use IP Tables to limit connections to a certain ip range.

An easier way, if it works, would be to use tcpd (aka tcpwrappers) to block everything to samba except whitelisted subnets.  See [hosts.allow / hosts.deny](http://manpages.ubuntu.com/manpages/karmic/en/man5/hosts.allow.5.html) and [hosts_options](http://manpages.ubuntu.com/manpages/karmic/en/man5/hosts_options.5.html) for details.

---

### Post by scorp123 on 2009-10-30
> **Lars Noodén said:**
>  An easier way, if it works, would be to use tcpd (aka tcpwrappers) to block everything to samba except whitelisted subnets.  See [hosts.allow / hosts.deny](http://manpages.ubuntu.com/manpages/karmic/en/man5/hosts.allow.5.html) and [hosts_options](http://manpages.ubuntu.com/manpages/karmic/en/man5/hosts_options.5.html) for details. +1

It's easy to do and it works pretty well.

---

