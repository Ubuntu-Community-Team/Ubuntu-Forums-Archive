---
title: "Home Server Help Request"
date: 2012-10-22
forum: Server Platforms
---

### Post by ercomer on 2012-10-22
I need to set up a home server to house mostly photos, from my wife's photography hobby, with some project documentation, and custom code storage from me. It is a budget system.

My Linux Administrator skill level: Noobie

Server Hardware: Dell gx620, 2.8 ghz Pentium D, 4 gig ram, 320 GB HD, 2- 1.5 TB storage disks.

The server will be headless and accessed via xRDP. I am comfortable using command line administration but the wife and daughters need to do photo organization and will be better off with a GUI. I would also like to set up a web server for remote file access, mostly for photo catalog access by my wife.

Client systems: One Windows 7 laptop, one Windows 7 desktop, one XP desktop, one Ubuntu 12.10 desktop and one Ubuntu 12.10 laptop.

I would like to use the server 12.04.1 LTS or 12.10 depending on the advice I hear here.

Any help would be greatly appreciated since a Linux server is new to me and I was not very impressed with WHS.

I'm sure there is a lot with this setup that I haven't even though of.

Thanks in advance,

Eric

---

### Post by dniMretsaM on 2012-10-22
I would look at [ownCloud](http://owncloud.org/). It does pretty much everything you will need for a file server and provides a great WebUI. I use it on my server and it works really nicely. The Web site has good instructions for installing the latest version (4.5) on Ubuntu. You don't need a GUI on the server because ownCloud does picture management itself. Also, I recommend sticking with 12.04.

---

### Post by Cheesehead on 2012-10-22
Generally, most headless servers really don't need to run X. xRDP is fun,  but it means a *huge* number of extra dependencies, and correspondingly higher resources consumptions and energy use and heat generation...which may matter for the physical location (like a closet).

For example, instead of xRDP, you can use samba to share the server over the network. Or, even more simply, sshfs.

Servers often start out with a single use (photo storage)...but those uses grow (backup, torrent, monitor, music, etc). Flexible hardware, and a flexible plan for the software, make adding new uses simple.

Don't forget Security. A poorly secured always-on server with network connection is a bad guy's gold mine. That means a smart network design, good firewall on your router, keys instead of passwords for ssh connections, and much more.


For example, here's how I configured a shared household server using sshfs:
On the server:
1) Install the server
2) Attach a temporary keyboard and monitor, Login to the server.
3) Configure the filesystem (the shared space on /mnt/Common, RAID, or backup)
4) Configure the network connection (reserved IP on the router, assigned by dhcp)
5) Configure the firewall (optional if behind a good router)
6) Configure the ssh server (or Samba server)
7) Add the users (each client should be a separate user), and configure the access for each
8 ) Test a ssh connection from one client. Disconnect the keyboard and monitor.

On each client:
9) Install the sshfs package (or Samba client)
10) Test connection
11) Script or shortcut to make connection simpler

---

### Post by ercomer on 2012-10-23
> **dniMretsaM said:**
> I would look at [ownCloud]("http://owncloud.org/"). It does pretty much everything you will need for a file server and provides a great WebUI. I use it on my server and it works really nicely. The Web site has good instructions for installing the latest version (4.5) on Ubuntu. You don't need a GUI on the server because ownCloud does picture management itself. Also, I recommend sticking with 12.04.


Thanks for the suggestion. That sounds like an answer to the remote access.

---

### Post by ercomer on 2012-10-23
> **Cheesehead said:**
> Generally, most headless servers really don't need to run X. xRDP is fun,  but it means a *huge* number of extra dependencies, and correspondingly higher resources consumptions and energy use and heat generation...which may matter for the physical location (like a closet).

For example, instead of xRDP, you can use samba to share the server over the network. Or, even more simply, sshfs.

Servers often start out with a single use (photo storage)...but those uses grow (backup, torrent, monitor, music, etc). Flexible hardware, and a flexible plan for the software, make adding new uses simple.

Don't forget Security. A poorly secured always-on server with network connection is a bad guy's gold mine. That means a smart network design, good firewall on your router, keys instead of passwords for ssh connections, and much more.


For example, here's how I configured a shared household server using sshfs:
On the server:
1) Install the server
2) Attach a temporary keyboard and monitor, Login to the server.
3) Configure the filesystem (the shared space on /mnt/Common, RAID, or backup)
4) Configure the network connection (reserved IP on the router, assigned by dhcp)
5) Configure the firewall (optional if behind a good router)
6) Configure the ssh server (or Samba server)
7) Add the users (each client should be a separate user), and configure the access for each
8 ) Test a ssh connection from one client. Disconnect the keyboard and monitor.

On each client:
9) Install the sshfs package (or Samba client)
10) Test connection
11) Script or shortcut to make connection simpler

That makes sense to me. I will use your step by step. I need a mirrored set so raid  1configuration should do it, and I haven't forgotten the backup. You provided a good basis for my flow chart and I will try ssh for my windows clients, if I can get it configured and stable. Thank you very much.

---

### Post by Habitual on 2012-10-24
> **ercomer said:**
> ...My Linux Administrator skill level: Noobie...

Eric:
check out [http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)

---

### Post by rg4w on 2012-10-24
> **Habitual said:**
> Eric:
check out [http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
Thanks for that link - very helpful info there.

---

### Post by ercomer on 2012-10-24
> **Habitual said:**
> Eric:
check out [http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)

Thanks for the information. It looks like I will try several configurations before I make a decision on the final form. I really appreciate all the help I am getting. It is very nice to get this kind of help. When I make a final decision on the setup, I will post it here and welcome critiques.

---

