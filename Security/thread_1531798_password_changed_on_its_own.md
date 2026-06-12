---
title: "password changed on its own?"
date: 2010-07-15
forum: Security
---

### Post by noway2 on 2010-07-15
We have an Ubuntu 10.04 box that we use as a shared PC amongst four of us at work.  Physical access to the machine is restricted by key-cards to a handful of people.  The machine is used for R&D and pet projects for the few of us.

I was out of the office yesterday and when I returned, the machine continuously failed to authenticate my user. I am 100% certain that I did NOT forget my password, which I have used for the last few months.

I was able to change my login password using the root recovery method and this enabled the account to login.  However, the home directory was encrypted and this does not decrypt.  This is expected since changing the password in this method does NOT propagate through to the encrypted home folder. My 'OLD' password will not unlock the encryption.

I saved the MOUNT password (hash) and GPG'd it on a separate computer and I can get at the data.  I need to sudo to root and manually mount the folder.

My questions for the group are:
1 - What could have gone wrong, other than someone changing my password on me (as a prank or to be malicious?)

2 - Is there a way to recover the password or should I just use the long mount password and then destroy the original user account (delete the user and shred the directory).

3 - due to the nature of the usage and the limited number of users, against my better judgment I was talked into allowing the other 3 users admin privilege.  I suspect that one of these users (the one that I think might do something like this) was the last one to physically access the machine because his account came up automatically at the login prompt.  Is there a way to prevent these people from being able to alter passwords (and logs) while still allowing them to install software and setup cron tasks?

EDIT: I discovered that the mount APPEARS to work.  If I ls the mount directory, I see the file names but I can't decend into any of the directories or open any of the files.  Attempting to do so gives: "No such file or directory"

---

### Post by anomie on 2010-07-15
[QUOTE=noway2]due to the nature of the usage and the limited number of users, against my better judgment I was talked into allowing the other 3 users admin privilege.  I suspect that one of these users (the one that I think might do something like this) was the last one to physically access the machine because his account came up automatically at the login prompt.  Is there a way to prevent these people from being able to alter passwords (and logs) while still allowing them to install software and setup cron tasks?[/QUOTE]

It depends on what kind of applications they're installing. If they need to write to protected binary / library directories, they'll need root or full sudoer access. My suggestion in that case would be for *you* to act as the sole sysadmin that installs software. 

If they're "installing" new web applications under, e.g., /var/www/foo, then you can easily handle this with some group and permissions changes. In that case, they have no reason to be sudoers. 

Of course, users can run cronjobs under their own accounts, depending on the nature of the cronjobs (and the type of access they'll need). 

I manage several servers where other sysadmins are full sudoers. In addition to regular review of logs (which can be worked around by a malicious person), I run a distributed HIDS to keep an eye on important changes.

---

### Post by noway2 on 2010-07-16
anomie,

Thank you for the suggestions.  I am going to put together my response to this situation and it is probably going to be as follows:

1 - re-establish my account
2 - remove admin priviliges for the other users
3 - relocate the server to an area where physical access will be more difficult.  
4 - Install a HIDS and set it up to email me with changes.

I may not use option 3, because that would negatively impact myself too as it would mean putting the machine under the dominion of a different department and my access would be limited too.

With a HIDS, I would at least know what changed, even if the logs were removed.  

There is also a lesson here in what "physical access == root access" really means.  With physical access you don't even need to know or crack the user password.  You can simply drop to recovery mode and get a root prompt at boot up. Until yesterday, I wasn't fully aware of this (and I am a several year veteran user of Ubuntu).  

My biggest question is if there is any way other than someone physically changing my password that this could have happened?  I don't see how a power failure crash or anything of that sort would cause my account to loose its password.

---

### Post by anomie on 2010-07-16
> **noway2]There is also a lesson here in what "physical access == root access" really means.  With physical access you don't even need to know or crack the user password.  You can simply drop to recovery mode and get a root prompt at boot up. Until yesterday, I wasn't fully aware of this (and I am a several year veteran user of Ubuntu).[/quote]

Physical access indeed equals complete access (they don't even need root said:**
> 
[*] Disable booting from CD, USB drive, network, etc. in the BIOS (so that live media can't be used to access the hard drive). 
[*] Password protect the BIOS (so that boot order can't be overridden). 
[*] Buy an inexpensive case lock and put it in place (so that the BIOS can't be reset by simply removing the battery). 
[*] Password protect GRUB if it isn't already (so that someone can't easily drop to single-user mode).   
[/list]

[QUOTE=noway2]My biggest question is if there is any way other than someone physically changing my password that this could have happened?  I don't see how a power failure crash or anything of that sort would cause my account to loose its password.

A power failure or hard reset could cause filesystem corruption. You'd want to run fdisk to determine whether that's the case, and whether it is fixable. But, at this point, who knows. I'm not sure where Ubuntu logs passwd changes to (auth log?), but there should be a record of it there - assuming it wasn't tampered with.

---

### Post by alphaamanitin on 2010-07-16
This is a very interesting discussion to me, as some one who uses computer security as a hobby.  I know it is off topic, but could some one link me to where I can find info on doing the steps that anomie last suggested?

Thanks,

AlphaA

---

### Post by anomie on 2010-07-16
Article on accessing your PC BIOS: [http://pcsupport.about.com/od/fixtheproblem/ht/accessbios.htm](http://pcsupport.about.com/od/fixtheproblem/ht/accessbios.htm)

Once there, poke around to find the features I mentioned. (Don't change anything you do not understand.) 

PC case lock: [http://www.google.com/search?q=pc+case+lock](http://www.google.com/search?q=pc+case+lock)

Here's a thread from the Ubuntu forums on password protecting grub (not sure I can vouch for it, though; be sure to read the ensuing discussion): [http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)

---

### Post by noway2 on 2010-07-17
I spent quite a bit of time yesterday undoing most of the damage. The damage was a little more pervasive than I first thought.  It turns out that the root password to MySQL was also trashed or deleted (easily fixed).  Another user account was modified so that it will login with no password (convenient for covering your tracks).  The machine is on a private LAN with no inward access of one of the most paranoid companies I have seen so I am certain it was an inside job.  

I was able to recover my files from the encrypted home partition.  Somehow, I managed to use insert the long unwrapped password into the right key chain and mount the partition.  I then copied everything to a different directory and recovered my files.  Not sure what I did right that time, but I wasn't able to recreate the process again.  Thankfully I didn't have any private GPG keys on the machine (I was messing around with putting them on an encrypted partition of a USB stick for this vary reason).  I deleted all the SSH keys to my personal servers and will recreate new ones in case he got a hold of any of those.  

I established myself as a new user with a different password.  I am now the only user with admin privilege.  Recovery mode has been disabled in grub.  It is also running snort and Ossec, which is set to email me any time something changes.  Ossec already alerted me to a couple of things that should be better locked down.  One thing that the suspect user liked to do was hijack services for his own usage regardless of whether someone else was using them, and do so without asking.  As part of the process, permissions for configuration files for Apache were changed to make them all writable.

Anomie, changing the boot order and putting a password on the BIOS, are good ideas that I didn't think of.  Thank you for that and the other tips.

I know since "locking him out" the user logged in at the machine's keyboard again.  Normally, most of us work remotely, but you need to be local to mess with the user accounts unless you know the command line instructions and the files to modify.  He is a definite "know it all", but I don't think his kung-fu is THAT good.  According to our IT guy, this person has a real history of asking for access and privilege to things he should not have and wanting "locally installable" version of programs and the permissions to do, purportedly to install it on everyone else's machines.

Now that logs can't be changed by him, I intend to look at the auth logs and see what his local login "signature" is.  By looking for it, or rather it's absence, in the logs for the time of the attack, it will pretty much confirm that he did this and then tried to cover it up.

---

### Post by HermanAB on 2010-07-18
Well, this is Ubuntu - edit the sudoers file.

---

