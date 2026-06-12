---
title: "How to setup simple file server in a native Ubuntu Environment"
date: 2010-12-07
forum: Server Platforms
---

### Post by rdp870 on 2010-12-07
I have two computers on my home lan I am trying to share files between...My desktop which is running Ubuntu Server 10.10 (x64) with a GUI, and my laptop which is running Ubuntu Desktop 10.04. I have tried a million different tutorials regarding SAMBA setup, but they never work.

In addition, most of those tutorials are geared towards hybrid Linux/Windows environment. I do not have any microsoft product in my home.

I have created the share on my server, but I'm not sure how to connect to it from the laptop (once again at this point in the tutorials it explains how to access it from a Windows PC). I tried using the menu doing this:

Places-->Connect To Server-->Service Type-->Windows Share (for the server I tried my server hostname and IP) to no avail.

Does anyone know of a recent step by step tutorial for setting up a complete Ubuntu environment? Is there a simpler method I can use since I do not particularly need to use SMB protocol?

All I want to do is share my music folder from my server so I can access it (from the same LAN) on my laptop...Arrrghhh frustrating.

---

### Post by HermanAB on 2010-12-08
Howdy,

Samba is for masochists only...

NFS requires only 1 line of configuration on each machine:
[http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

---

### Post by Fiddler_Wins on 2010-12-08
Super easy (I am spelling impared so check...)
Make sure to replace italics with your real info - $USERNAME is jdoe or whatever...

This will share your default Music directory read only to anyone (/home/username/Music)
1. sudo apt-get install nfs-kernel-server (installs NFS server)
2. sudo vi /etc/exports (edit file that tells NFS what to share ("export")
/home/*$USERNAME*/Music *(ro,no_subtree_check)

On a client machine you'll need to install the NFS client:
sudo apt-get nfs-common (install client)
sudo mkdir /media/Music  (create location to mount the server's music directory to)
sudo chmod  744 /media/Music (make it rw for root, read only for everyone else)
sudo mount *<server>*:/home/*$USERNAME*/Music /media/Music mount server directory to client

at this point you should see your music on /media/Music on the client. Make sure that you've got read access to it with what ever ID you're using (ls -l should show drwxr--r-- for 744 above).

NFS is far more efficient than samba and easier to configure - using the command line is a little uncomfortable when you start but it does only and exactly what you tell it which is very nice :)

---

### Post by SeijiSensei on 2010-12-08
> **Fiddler_Wins said:**
> sudo chmod  744 /media/Music

I'd use 755 so users can list the Music directory.  744 will let them read a file in the directory, but only if they know the name already.

---

### Post by ingeva on 2010-12-10
Can I butt in here with an additional question?

I've set up NFS and it works perfectly, and as said before, a "million"
times faster than Samba.

But I can't figure out how I can share the root folder, neither with
Samba nor with NFS.  I can manage without it for Samba, but I do
need it for NFS.

I've made a symbolic link, /Base, to the root folder in addition to the
definition in /nfs4exp/ ,  and used that instead of "/" in fstab.  My NFS
definitions in fstab are:

```
# NFS4
/Base    /nfs4exp/Base    none    rw,bind    0    0
/Store    /nfs4exp/Store    none    rw,bind    0    0
/Backup    /nfs4exp/Backup    none    rw,bind    0    0

Papa:/Base    /mnt/Base    nfs4    rw,rsize=8192,wsize=8192,intr    0    0
Papa:/Store    /mnt/Store    nfs4    rw,rsize=8192,wsize=8192,intr    0    0
Papa:/Backup    /mnt/Backup    nfs4    rw,rsize=8192,wsize=8192,intr    0    0

```This is a peer-to-peer system, where both computers are
server and client. Papa, of course, is the remote computer.
The /Base directory is the link to the root folder.

Help, anyone?

---

### Post by rdp870 on 2010-12-12
@fiddler Wins

I tried everything the way you said, but when i try to mount, I get this error:

mount: can't find pitcher:/home/pitcher/Music in /etc/fstab or etc/mtab

Any ideas?

---

### Post by gordintoronto on 2010-12-12
> **rdp870 said:**
> I have two computers on my home lan I am trying to share files between...

You're making it much more complicated than it is.

To share a folder: right-click on it, select "sharing options," give it a name and click on "allow others..." and "guest access."

To access a shared folder: click on Network, then double-click on "Windows network," the workgroup, the computer, the share. (Even if there's no Windows!)

I have never, ever edited a configuration file, and every computer has a shared folder, and every computer can access all the shared folders.

Some routers can block file sharing, as can firewalls.

---

### Post by rdp870 on 2010-12-17
I have tried that numerous times. I guess it could be my firewall (using UFW) or my router (Linksys WRTG54 using dd-wrt custom firmware). Do you know what ports need opening?

---

### Post by tr333 on 2010-12-17
> **rdp870 said:**
> I have tried that numerous times. I guess it could be my firewall (using UFW) or my router (Linksys WRTG54 using dd-wrt custom firmware). Do you know what ports need opening?

I think it's port 111 and 2049.  Both are TCP and UDP.

---

