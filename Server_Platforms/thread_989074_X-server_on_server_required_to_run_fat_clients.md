---
title: "X-server on server required to run fat clients?"
date: 2008-11-21
forum: Server Platforms
---

### Post by tegel123456789 on 2008-11-21
Hi,

Iam trying to setup a fat LTSP client. The server is running Ubuntu Server 8.04. **Do I need to install an x-server on my server in order for the fat clients to login???** 
(I have used the Fat Client plugin on [UbuntuLTSPLTSPFatClients]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPFatClients"))

When I boot my fat client, no GDM Login screen is shown. All I see is this:

> *setting up LTSP client
*stopping GNOME Display Manager
*Starting GNOME Display Manager
*Stopping portmap daemon
*starting portmap daemon
*Stopping NFS common utilities
*Starting NFS common utilities
can't set permissions on mtab: Operation not permitted

*starting portmap daemon
*Already running
*Starting NFS common utilities

The issue with permissions on mtab I solved by using mount -n
when mounting /home.

I know that an x-server is required when running thin LTSP clients, but I didn't think it was required when having fat clients...

Has anyone succeded with a fat client setup using Ubuntu Server 8.04??

BR Anders

---

