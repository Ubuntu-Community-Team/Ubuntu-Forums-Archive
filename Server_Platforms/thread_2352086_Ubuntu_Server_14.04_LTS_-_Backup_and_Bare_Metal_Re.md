---
title: "Ubuntu Server 14.04 LTS - Backup and Bare Metal Recovery of remote system"
date: 2017-02-09
forum: Server Platforms
---

### Post by ernstv2 on 2017-02-09
Hi Community!

I own an Ubuntu 14.04 LTS VM at a hosting provider (Host Europe) and have some services running there (Mail, some Websites, Docker, Graphite/Carbon, some self-made stuff, etc.).
In case I screw my server up, I can reset the machine back to it's defaults, just takes a few minutes. Ready for a restore.

If I *would have *documented all the installation and configuration steps I did in the past couple of months, it would be Ok to recover the system in a timely manner. I do daily backups of my application data, .conf files (at least from whom I know being important) and some of the other stuff (/etc, /var/lib, ...) to a tar archive and back them up to my Dropbox via dropbox APIv2. Works like a charm so far.

But do you know a way how I can backup my entire system (to the cloud) and, in case of a disaster, get everything up and running from a blank install of Ubuntu?

I cannot shutdown the machine and back up the VM files, of course, I a just a customer of my provider.

Any suggestions?
Thank you,
EV

---

### Post by SeijiSensei on 2017-02-09
I use [Linode]("http://www.linode.com/") and have the nightly snapshot service enabled.  I can spin up a new VM and restore the backup to it.  Does your provider not offer a service like that?

You can use the --set-selections and --get-selections options to dpkg to create a list of installed packages and use that to restore.  For configuration files and such, keeping an off-site backup of places like /etc is the way to go.

---

### Post by jamesr on 2017-02-10
Hi,

I personally use and would recommend looking at mondorescue (mondorescue.org) for bare metal backups. I personally backup to a local archival file-server so I do not know if it works to the cloud. But Bruno who is one of the lead developer uses a VM to develop and checkout the software. I have used Mondo from before the days of Dapper and it has saved my bacon several times. Since you are using 14.04 you should have no problems downloading, installing and running the software.  This software is is the only reason that I have not upgraded to 16.04, although I am just testing it  on my test file-server. It works but Samba seems to not W10 or vice-versa.

---

