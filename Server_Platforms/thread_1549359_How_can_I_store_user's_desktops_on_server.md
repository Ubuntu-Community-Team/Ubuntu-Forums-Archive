---
title: "How can I store user's desktops on server?"
date: 2010-08-09
forum: Server Platforms
---

### Post by Triton Yurin on 2010-08-09
Hi everyone,

I'm looking for a way to store network users desktops on a local server.

Here is the problem:

I have a local network with approx. 80 user computers (running Xubuntu 6.06) and one server (running Ubuntu Server 10.04).

How can I configure this server and clients computer the next way:

One 250 GB hard disk is installed on server, and it is divided by 1 GB per user (250 users in approx.). Users logins and passwords are too stored on server.

Any of the 250 users gets to any client computer (running xubuntu) and does the network authorisation, so his personal desktop with user's own files, docs, favorites etc. is being loaded from the server.

In general, this is made for users to have possibility to access their files and docs stored on server from any computer.

Heard smth about it can be made through Samba or NFS, but I have no ideas how to get it working:(

How can I configure computers and server such a way?

Thanks in advance.

---

### Post by arrrghhh on 2010-08-09
Well, to do what you want to do is a little more complex than just samba/nfs share (unless I'm misunderstanding you...)

The users can always get their files no matter what machine they login to - but getting preferences, settings, and an entire desktop?  It sounds like what you want is a thin client setup.  Which may in turn create more work for you, and your server hardware may not be beefy enough.

Here's some thin client links:

[Thin Client HowTo](https://help.ubuntu.com/community/ThinClientHowto)
[UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by lisati on 2010-08-09
It sounds like [LTSP]("https://help.ubuntu.com/community/UbuntuLTSP") might be something similar to what you are trying to achieve.

---

### Post by koenn on 2010-08-09
thin client / LTSP - that's server based computing, i.e. all users work on the server. 
It's one way of centrally managing users and user configs.

The other way is having all user home directories (which include data and user prefs / settings) on an NFS server, and mount them to the users's computer. 
This is different from server-based because the user works on a PC - the server is just a file server that serves up the home directories.
In this scenario, you'd still need a separate solution for centralized account management and log-ons

---

### Post by Triton Yurin on 2010-08-09
Well, what about placing to /etc/fstab on each client machine a statement that points to the /home directory on server?

---

### Post by YesWeCan on 2010-08-09
@Triton
For example, mount the server /home/user as an NFS directory? Then have the server /etc/exports include all home paths. Interesting.
I guess you would want the client mount to be done on a per user basis so that each client doesn't have 80 directories mounted all the time.
Sounds like the sort of thing linux can do in its stride but I don't know how to do it.

Edit: Oh. I suppose it is possible to run a shell script when a user first logs in. The script would mount the NFS directory. Not sure how to unmount when the user logs out.

---

### Post by amauk on 2010-08-09
Pointing client /home to NFS shared /home on server is a quick and dirty way of storing all user data on the server
however, it sounds like you want more than that
You mentioned central authentication
This means using LTSP

LTSP is not just about thin clients
You can do what's called a fat client, as well
This means that client machines use their own CPU & RAM, GPU (and, possibly their own storage if required)

- A compressed OS image is stored on the server

- Upon client boot, client requests the server to send it an OS image to boot from (network boot)

- Server can be setup to serve one (or more) images to client machines (if using multiple images, image sent is distinguished by the network MAC address of client)

- Usernames & passwords are stored on the server

- Client logs in (all authentication happens server-side)

- Client /home folder is an NFS share on the server

This page details how to setup LTSP Fat Clients
[https://help.ubuntu.com/community/UbuntuLTSP/FatClients](https://help.ubuntu.com/community/UbuntuLTSP/FatClients)

Advantages to LTSP
- Single OS image to administer
If you wish to install AppX on your clients, all you have to do is chroot into the server stored image, install AppX, and re-build the compressed image
Upon client reboot, all clients will have AppX available
There's no need to install stuff on each individual client machine
This goes for installing apps, or other admin tasks
This also means that no client is forgotten or deviates from your intended setup
All clients will boot off of one image - you administer just that one image

- Separation between client "types"
You may wish to have a "normal" client image, and a specialised client image (specialised maybe used for managers, or whatever, but they have different stuff installed, or different shares available, etc.)
You can setup the server to serve different client images based on the client MAC address

---

### Post by koenn on 2010-08-10
I wouldn't call NFS mounts of /home[/username] quick and dirty. 
It's a mechanism, which means you have to configure/customize/tweak it to suit the situation. 

The LTSP Fat Client approach looks like something that might work for central user management without resorting to pure server-based computing. 

Kerberos and/or LDAP probably offer alternative solutions for centralized account management and authentication


Note that with any config based on the client's MAC address, you let things depend on which computer the user is sitting at, not the user as such. 

If you look at the (sample) scripts in  /etc/gdm/PostLogin and /etc/gdm/PostSession (and possibly /etc/gdm/Init and PreSession), you'll see that gdm provides a mechanism to do user-specific configuration (and undo it after the user logs out). I assume other desktop managers have something similar, if you're not using gdm.

---

