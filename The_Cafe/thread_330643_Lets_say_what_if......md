---
title: "Lets say what if....."
date: 2007-01-03
forum: The Cafe
---

### Post by jleemc44 on 2007-01-03
OK, I work for a digital signage company. I'm using ubuntu a lot for file serving, data gathering, ect....

The digital sign units runs windows (go figure). Part of the system requires me to update files in a data directory on the windows biased player. Most of the time I just run an FTP server on the player and have Linux shoot out the updates I need with via FTP.

However (you knew that was coming), some of the plays will not establish an FTP connection with my Linux or windows machines. This is because I can't get to the network controllers of some of the locations due to security reasons.

Is there any software that would allow me to sync a remote folder or accesses a hard drive remotely without the need of FTP? Something that’s no bothered by a firewall?

Thanks.

---

### Post by PriceChild on 2007-01-03
Well samba?

Just open ports?

---

### Post by meng on 2007-01-03
SSH, allows secure FTP etc.

---

### Post by RandomJoe on 2007-01-03
I would also suggest ssh/scp (or rsync over ssh ideally) - you're far more likely to get an administrator to open ssh than ftp.  But that also implies you'll get them to open _any_ port for you.  I work with HVAC controls, which are more and more being put on the network and many IT departments are unwilling to allow remote access.

The best luck I've had, if they have VPN access for their users, is just to get a VPN account.  This also lets them lock us down to only access our panels.  It's a little annoying - gets hard to juggle multiple VPN clients (some of them refuse to coexist together) and may even be Windows-specific unless you can figure out how to make Linux work with their particular software choice.  (At work, it's 100% Windows :( so this isn't an issue for me.)

Another option we have had luck with is giving them the IP we will be coming from.  Rather than opening the port up to the world, they can only accept connections from our IP, which apparently makes them a little happier...

---

