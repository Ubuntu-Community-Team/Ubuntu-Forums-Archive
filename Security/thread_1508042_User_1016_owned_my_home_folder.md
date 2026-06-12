---
title: "User: 1016 owned my home folder"
date: 2010-06-12
forum: Security
---

### Post by soelk on 2010-06-12
Yesterday I realized that I was unable to write files to "/home/myname".

So i typed: ls -l

Both owner and group was set to "1016". Could that be a sign that my computer has been compromised or did something non-malicious cause this?

I looked through my terminal history to see if I had used any bad/drunken chmod commands, but my chmod commands all look good and sober.

I have recently used Windows XP a couple of times. But I think that WinXP can't access my Ubuntu drive because it is using the ext4 file system. I have used some third party p2p apps on Ubuntu such as Octoshape, Sopcast and Veetle.

Edit: I have not used VNC at all. There has never been a VNC server running on my box.

All the usual malvare tools report negatives. I haven't noticed any suspicious CPU or RAM use.

Ubuntu Lucid, upgraded from a fresh Karmic install.

---

### Post by anomie on 2010-06-12
Out of curiosity, what does **id <your_username>** show? 

Some possible candidates to cause this problem (in order of likelihood, IMO): 
[list]
[*] user management (i.e. deleting a user and then recreating him with a different UID)
[*] restoring /home from a tarball or pax archive (where users/UIDs don't match your current system)
[*] a mistaken chown command where UID/GID was provided instead of username/group name
[/list]

(I'm presuming you know how to fix this and don't need help with that part..)

---

### Post by soelk on 2010-06-12
Thanks for the input.

EDIT: Just to clarify: I did take ownership of the folder right away when I noticed the problem. I don't need help with that. I'm trying to figure out what might have caused the problem in the first place.

```
id username

uid=1000(username) gid=1000(username) groups=1000(username),4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),115(admin),120(sambashare)
```


I haven't made any changes whatsoever to the users lately. I was still the owner of /home/username/ last week when I created a folder there.

Restoring home from a backup? Nice guess, but no.

Not chown either. I didn't know chown existed until yesterday when I needed it to take back ownership of my folder. 

I'm a hardware/EE geek rather than a software geek. I don't really know how to properly administer a Linux system. I try to do as little as possible...

Oh by the way, I have messed with the udev rules to make a persistent link to a USB device (a Bus Pirate). I think that is the only hackish thing that I have done to this system since the fresh Karmic installation.

---

### Post by cariboo on 2010-06-12
You could go through the logs located in /var/log, to see if anything sticks out. Check messages, including the archived copies.

---

### Post by PGScooter on 2010-11-08
this problem happened to me and it was indeed caused by Veetle.

---

### Post by JG6_oddball on 2010-11-10
Ditto on the Veetle causing me the same problem, also i started getting the following message on bootup

"Failed to update ICEauthority"

becuase it could not right to the file because Veetle changed the ownership...I wonder why Veetle did that?

---

### Post by BurningMind on 2011-11-11
Had the same problem in Bohdi Linux just after installing veetle with the sh file.

---

