---
title: "Server Setup"
date: 2012-04-23
forum: Server Platforms
---

### Post by Frozen001 on 2012-04-23
Hi all,

I have been messing around with getting a small network setup with 5 computers.  My ultimate goal is to have each one running ubuntu, totally eliminating windows.

I wold like to have 1 server that will be used for the following:

1)  Print server
2)  Domain controler
3)  DNS server
4)  File server
5)  User authentification
6)  Software roll out.

My goal is that any user can log on to any machine and have the same software, same desktop, etc.  

I have to time line on when I complete this so if it takes me a while to understand things I am ok with this.

---

### Post by lykwydchykyn on 2012-04-23
It might be easier to set up something with LTSP using the "fat client" approach, as discussed here:

[https://help.ubuntu.com/community/UbuntuLTSP/FatClients](https://help.ubuntu.com/community/UbuntuLTSP/FatClients)

This eliminates the need for a domain controller, centralized authentication, file serving, and software deployment services.

If you really want to do things the way you're describing, though, probably your first stop needs to be understanding Samba.

Start here: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by Frozen001 on 2012-04-24
> **lykwydchykyn said:**
> It might be easier to set up something with LTSP using the "fat client" approach, as discussed here:

[https://help.ubuntu.com/community/UbuntuLTSP/FatClients](https://help.ubuntu.com/community/UbuntuLTSP/FatClients)

This eliminates the need for a domain controller, centralized authentication, file serving, and software deployment services.

If you really want to do things the way you're describing, though, probably your first stop needs to be understanding Samba.

Start here: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Thank you for the informnation.  The fat client approach seems nice, but from what I read, I would still need a seperate DHCP server, which I would prefer to avoid.

On Samba, isn't that only needed if a windows client is to be attached to the network?

---

### Post by lisati on 2012-04-24
> **Frozen001 said:**
> 
On Samba, isn't that only needed if a windows client is to be attached to the network?

I have samba on my server. It doesn't seem to mind if I'm using Windows or Ubuntu to access it.

---

### Post by lykwydchykyn on 2012-04-24
> **Frozen001 said:**
> Thank you for the informnation.  The fat client approach seems nice, but from what I read, I would still need a seperate DHCP server, which I would prefer to avoid.

Where do you get that from?  You can have the same server doing DHCP; in fact, that's how it configures from default.  You can really have anything doing DHCP, as long as it allows you to set the necessary options.

> 
On Samba, isn't that only needed if a windows client is to be attached to the network?

It re-implements the Microsoft networking protocols; so it's built for Windows clients, but not limited to Windows clients.  It turns out it's a nice bundle of services for any kind of clients.

Another option would be NFS for file sharing and OpenLDAP for authentication.

---

### Post by Jonathan L on 2012-04-24
Hi Frozen

> fat client approach seems nice, but from what I read, I would still need a seperate DHCP server, which I would prefer to avoid.

On Samba, isn't that only needed if a windows client is to be attached to the network?

DHCP can be supplied by anything on your network; usually done with either your all-in-one server (which I'd recommend) or sometimes your router (only recommended if you have a specially good one.)  DHCP server is such a low load process (for a network your size) it won't have any noticeable impact on performace.  You definitely want to run it on something which is always on.

Samba is in brief a re-implementation of Microsoft's filesharing protocol SMB (hence the name), also known as CIFS ([http://en.wikipedia.org/wiki/Server_Message_Block](http://en.wikipedia.org/wiki/Server_Message_Block)).  it's a decent-enough filesharing protocol, most often used when you have Windows clients accessing a non-Windows file server, but also used for other circumstances: including non-Windows clients such as Ubuntu and Macintosh.  If you've got mixed clients, it's common to just use Samba as the file server software, so you don't have to run anything special for the Macintoshes or Unix-like machines.

Hope that helps.

Kind regards,
Jonathan.

---

