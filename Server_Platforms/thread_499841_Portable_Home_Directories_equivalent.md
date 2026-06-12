---
title: "Portable Home Directories equivalent?"
date: 2007-07-13
forum: Server Platforms
---

### Post by laertes on 2007-07-13
Not sure where to put feature requests, but here goes:

OS X Server has a very useful feature for network home directories called Portable Home Directories, where a "thick client" that boots independently has both a network home directory on the server and a local home directory that are periodically synchronized. The user has the choice of syncing on log-in and/or log-out, or manually while logged in. The syncing occurs in the background.

I'm not as familiar with Windows roaming profiles but perhaps Microsoft has a similar option for users of portable machines that want to carry their network home directory with them when away from the LAN.

This works very well for laptops that come and go, essentially maintaining a full backup on the server that can be logged into from any other machine on the network. This also saves a lot of time and hassle when machines get lost or broken--just log in from any other client on the LAN while the machine is being replaced or repaired, and when the replacement is ready, do another Portable Home Directory sync and you're back in business with little to no downtime.

I believe all the components are in place to do this with Ubuntu, both server and desktop: OpenLDAP, NFS, Unison. It just needs to have a configuration panel on the server that consolidates all the setup, along with a login panel addition on the client that offers the "do you want to create a portable home directory" choice and a control panel offering sync options.

With SMB and AFP support the server implementation could even support Windows and OS X clients.

If there is already a project to implement this, please point me to it.

---

### Post by rickyjones on 2007-07-13
I'm not sure if there is a project but I'm pretty sure it can be done as-is. I'm still trying to get it though.

I have an Ubuntu Desktop authenticating to an Active Directory domain. I'm trying to get the Ubuntu desktop to mount /home/DOMAIN/ to my network share that contains the users profiles folders (for roaming profiles). I haven't had a chance to get into it, just some initial testing.

What you might be able to do as well is have a cron job run on log in to run unison or some other file sync program.

Hope that helps you in some way. :)

-Richard

---

