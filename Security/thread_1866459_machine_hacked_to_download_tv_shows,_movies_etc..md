---
title: "machine hacked to download tv shows, movies etc."
date: 2011-10-21
forum: Security
---

### Post by maxxum on 2011-10-21
A little bit of history about the machine.
It is at my workplace (often accessed by multiple people). It is in a network of machines running Win7, XP and Ubuntu. It has a boot drive and a data drive (which is ntfs formatted). I found the ntfs drive was full while the contents were not totalling up to its size. A little bit of investigation on hidden files/folders showed that there was a RECYCLER/.tmp folder in which there were a lot of movies, tv shows etc. in compressed formats. A few months ago, this machine was running windows and the same hard drive was used with it. Initially I thought it must be a malware in windows and these are remnants. Another user had reported such activity on their windows PC which used to be in the same room.
I deleted them and waited a few days. Some new files have appeared even when the machine is running Ubuntu 11.04. There is some malware running on this machine under ubuntu and I need to find out what it is.
Other machines in the room have not shown any such issues so far. So for now this machine is off-internet while I try to find out the culprit.
Any help would be greatly appreciated.
Due to the nature of the job, the machine needs to keep a vnc server running and is often accessed by me from outside networks. A SSH server also needs to be running. I realise these may be sources of security lapses but I want to figure out the best possible compromise.

---

### Post by CharlesA on 2011-10-21
vnc is pathetically insecure. If you have to use it, tunnel it over ssh.

Wipe the drive and try a different method of connecting remotely.

---

### Post by OpSecShellshock on 2011-10-21
Compromise over VNC seems the most likely here. It may not be possible at this point to determine the full extent of changes that were made. Best solution, as offered above, is to completely wipe and re-install. Probably best to require key-based, rather than password-based, authentication, especially considering it has multiple users accessing it remotely.

---

### Post by CharlesA on 2011-10-21
> **OpSecShellshock said:**
> Compromise over VNC seems the most likely here. It may not be possible at this point to determine the full extent of changes that were made. Best solution, as offered above, is to completely wipe and re-install. Probably best to require key-based, rather than password-based, authentication, especially considering it has multiple users accessing it remotely.
Huge +1 to key-based logins. Weak passwords can be cracked and having ssh exposed to the internet with a weak password is an easy way to get your box cracked.

---

### Post by Dangertux on 2011-10-21
Well to be honest, VNC is #1 on the list of ways to get owned in less than an hour. Though vnc4server does offer some level of bruteforce protection.

SSH is reasonably secure even without keys IF your password has enough entropy (32+ characters). Keys are still preferable.

To be honest it sounds like your machine was being used as a warez dump. Wipe and start again.

---

### Post by bruno9779 on 2011-10-21
There is nothing wrong with your machine.

I have the same behavior with my external HD.
When I move something to the trash, being that the trash folder is on a different disk, it goes to the .RECYCLED folder instead.

You just need to empty the trash before logging out.

---

### Post by maxxum on 2011-10-21
I would reinstall with the newer 11.10 but before that I would want to find out what program is running in the background that is down/uploading all these movies etc. and how to detect it on other machines in case they got to them.
bruno9779, no. The machine is not used to download this stuff so since the new stuff is coming in means that the machine is compromised.

---

### Post by vajorie on 2011-10-21
> **maxxum said:**
> find out what program is running in the background that is down/uploading all these movies

Unless it's a rootkit (and I'd assume it is), the following two commands might be of help: 

```

sudo lsof -i 

```

```

netstat -antu

```

---

### Post by Dangertux on 2011-10-21
> **vajorie said:**
> Unless it's a rootkit (and I'd assume it is), the following two commands might be of help: 

```

sudo lsof -i 

``````

netstat -antu

```

Why do you think it's a root kit as opposed to just a simple ftp or xdcc server?

---

### Post by bodhi.zazen on 2011-10-21
As others have indicated, use ssh whenever possible.

Take care with ssh, at a minimum use strong passwords. Personally I prefer to use keys and disable password authentication.

ssh -X will forward graphical applications.

If you *must* use VNC, tunnel it over ssh or better use FreeNX, which is both faster and more secure.

---

