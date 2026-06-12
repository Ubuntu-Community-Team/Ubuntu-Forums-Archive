---
title: "Redundancy and Security"
date: 2015-01-15
forum: Server Platforms
---

### Post by andy117 on 2015-01-15
[COLOR=#333333][FONT=UbuntuRegular]I've recently set up an ubuntu 14.04 Server for one of our computer repair shops. It is used as a Samba, FTP server and will also host a VM eventually. The server is used to store customer data and i have used rsync to clone one drive to another to insure this data will be safe if the primary drive fails.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I am wondering:[/FONT][/COLOR]

[LIST=1]
[*]can i use Rsync/DD or something similar to clone the drive containing the OS, to another one to provide redundancy if the primary OS drive fails? if so what is the best way to do this?

[*]What security measure would be recommended for a system of this sort? i need to leave samba open to guest access for convenience but i'm thinking of using "fail2ban" to harden SSH, set up the UFW firewall to allow only the services we use, and perhaps run snort or a similar IDS/IPS system to protect the server (Although this may be over kill for this environment) 
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]Any other suggestions would be appreciated.[/FONT][/COLOR]

---

### Post by TheFu on 2015-01-16
a) don't use plain ftp.  Use sftp instead. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
b) use tcp-wrappers for all services. Don't allow any unwanted IPs to have access, so use a default-deny configuration. Whitelist only.
c) If the network is hostile, and it sounds like it is, only ssh tools (ssh/scp/sftp) with fail2ban and key-based authentication should be allowed. No samba, no ftp, no web, no email, .... NEVER USE PASSWORDS!!!!!!!!!!!!!!!!
d) versioned, automatic, backups are the primary security tool for all computers.  There isn't any other method that can help resolve more issues than having 60-90 days of backups where any of the prior days can be restored.  Good backups can fix most things.

Chances are that an IDS/IPS isn't useful in a tiny environment that isn't connected to the internet. Running an IDS/IPS on the same system that is running other services is terrible idea.

What is the purpose of this system and how is it networked?

Cloning?  There are 50 different ways to do this. dd is fine, partimage, clonezilla, or 20 others all work.  fsarchive is probably more efficient if you must have an image. Image backups are not very efficient and require the image is created by booting alternate media (can't do this safely if the OS being cloned is running).  rsync will work for everything in a much more efficient way for everything, except setting up grub. rsync is how I clone OS/data/settings for one-time needs. Setting up grub isn't that hard, once you've done it a few times. Takes just a few seconds.  Being able to perform backups while the system is running makes it much more likely to be performed, automated, consistent.

---

