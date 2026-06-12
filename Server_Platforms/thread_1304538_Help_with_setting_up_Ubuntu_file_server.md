---
title: "Help with setting up Ubuntu file server?"
date: 2009-10-29
forum: Server Platforms
---

### Post by faulknerm on 2009-10-29
Afternoon all,

I'm trying to set up a linux box as a file server, to share files amongst Windows and Linux clients. 

The main purpose is to use the server as a repository for my media files, which will be accessed by my media centre PC - but I also want to be able to access the files from other clients on the network too (and, eventually remotely).

I admit that my *nix skills are VERY rusty, so please bare with me. It's been a while... :rolleyes:

I've installed Ubunti server 9.10 and during the installation chose the option for a SAMBA server (I also set up for LAMP, but that's for another time one this is sorted). I have my HDD partitioned as 20GB ext4 system partition, 3.1GB swap and 212GB xfs media partition.

I (perhaps incorrectly) chose the default option to mount the xfs partition as /home and gave it a label of media.

Now I'm trying to set up the SAMBA shares, but not sure whether I'm barking up entirely the wrong tree. I currently have the following in my /etc/samba/smb.conf

```
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user’s home directory as \\server\username
[homes]
comment = Home Directories
browseable = yes
 # By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only “username” can connect to \\server\username
valid users = %S
 # By default, the home directories are exported read-only. Change next
# parameter to ‘yes’ if you want to be able to write to them.
writable = yes

```

Does this look anything like correct? Or am I missing something?

Any help on this would be greatly appreciated, as I'd like to get the share working today if possible so that I can start the long process of copying my media to it before getting the media centre set up. :)

Many thanks in advance!!

Marc :D

---

### Post by elvinatom on 2009-10-29
Is this your complete smb.conf?  If so, it's missing a lot of stuff.

---

### Post by faulknerm on 2009-10-29
> **elvinatom said:**
> Is this your complete smb.conf?  If so, it's missing a lot of stuff.

Hi,

No, sorry, this is just the section for share definitions. Would you need to see the rest of it? (if you do I'll need to sort out an SSH to the server first, as there's too much to copy out!!)

Cheers,

---

### Post by faulknerm on 2009-10-29
Just to update - I think I may now have solved my problem. :)

I added the following beneath the [home] section in the above extract

[media]
path = /home
browseable = yes

ANd I can now access the share from one of my clients. It's still prompting for a user logon (using my servers logon works fine here) but that's something else I can tackle seperately. 


As another side note, the mapped drive has a folder called "Faulknerm"(which is my username on there). Is this a result of it being mounted as /home? 

If so, would I be best mounting the media partition as /media instead - so that it doesn't end up containing anything else?

Cheers!! :D

---

### Post by faulknerm on 2009-10-29
Right, I goofed up whilst fiddling around in the smb.conf file and was left with a totally non functioning SAMBA server, so figured the best bet would be to just start from scratch, that way I an iron out a few other niggles such as the correct mounting of the partitions etc.

I'll lay out my plans for the installation - would appreciate it if you could "yay or nay" them, and make any suggestions which could improve the install, or help prevent disaster if I've got it totally wrong!

Os to be installed - Ubuntu Server 9.10

HDD config - 

Drive - 250GB SATA 
Partition 1 - 20GB ext3/4 primary
Partition 2 - 3-4GB SWAP
Partition 3 - 211GB xfs logical, mounted as /media

Installed options - SAMBA, LAMP, SSH

How does all of this sound so far?

I want the end result to be a 211GB partition which can be mapped as a network drive on my client machines, with no user logon required and full read/write perms. 

Thanks again. :)

Marc

---

### Post by negativ on 2009-10-29
You want this:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
At least skim all of it, but section 7 seems to be what you're looking for.

Also:
[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id2559459](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id2559459)

---

