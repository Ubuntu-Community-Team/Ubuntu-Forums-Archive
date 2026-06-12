---
title: "My Dream Server"
date: 2007-02-27
forum: Server Platforms
---

### Post by pseif1 on 2007-02-27
I want to set up a server at my grandparents house across town. I want this server to:

[LIST]
[*]Be a torrentflux server
[*]Be Secure
[*]Have my media accessible via FTP
[*]Backup ALL the computers in my house once a week AUTOMATICALLY (2 Win XP Boxes-Contain the "bulk of information" , 1 Ubuntu box, 2 Win XP laptops, 1 Ubuntu laptop)
[/LIST]

I am planning on using a computer with about 1/2 a tb of space.

I do not have a static ip and neither does the house I am putting this computer in so I will need to set up a noip client etc.

What are the best ways to set this all up?

---

### Post by gaten on 2007-03-01
> I want to set up a server at my grandparents house across town. I want this server to:[LIST]
[*]Be Secure[/LIST]For security you'll want to use SSH as much as possible, or maybe even OpenVPN. I'm going to suggest SSH because its  a breeze to set up and I've never used OpenVPN.

You can forward ALL your services through SSH (the ones that use TCP at least, and in your cause that's all of em). Rather than setting up an FTP server and open more ports on the system, use SCP. This provides FTP like availability but uses the SSH protocols to ensure that your data is secure. SCp is installed by default with OpenSSH and the syntax for the command is 
```
scp -P PORT_NUMBER username@localhost:file username@remotehost:file
```A GUI is available for windows: [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

You will need to ensure that all the data you wish to be accessible is available to the user you SSH in as (not root, this is a bad idea).

> Backup ALL the computers in my house once a week AUTOMATICALLY (2 Win XP Boxes-Contain the "bulk of information" , 1 Ubuntu box, 2 Win XP laptops, 1 Ubuntu laptop)I really don't know about this one, this is a LOT of information to send outside of your internal network. But hey, whatever floats your boat. As far as a solution, I don't know. Perhaps a script that uses SCP or something. 

> I do not have a static ip and neither does the house I am putting this computer in so I will need to set up a noip client etc.Are your behind a router at either location? Most routers nowadays have the ability to update hosts like Zonedit or DynDNS. If not, they all have update clients available for download (yes, linux ones too).

I don't know a thing about the Torrent server, sorry. Hope that helps.

---

### Post by firefly2442 on 2007-03-02
"rsync" is a great program for backups under Linux.  You could mount the shares through Samba and then grab the information off that.  It's really fast because it doesn't backup the whole thing, it checks against the source and only transfers files that are different.

edit: Oh, and you'll want to use a Cron job to automatically run the backup every week.

---

### Post by punx45 on 2007-03-02
you may find that the combination of backing up all the PCs at home and accessing all your media over the internet to/from your grandparents' house will be excruciatingly slow.   not to mention the constant flow of traffic between backups and streaming media/torrents could anger your ISP(s).

---

### Post by genesis[OFT] on 2007-03-03
Yeah mate - It'd be hella slow.

I suggest maybe backing up all your computers to your grandparents house maybe once a month.  I mean otherwise, you're even going to have issues with your internet being capped (if you're on such a plan) - and that wouldn't be fun.

---

