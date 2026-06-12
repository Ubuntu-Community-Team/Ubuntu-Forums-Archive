---
title: "Mapping a Remote Network Drive"
date: 2012-04-30
forum: Server Platforms
---

### Post by Frankincense93 on 2012-04-30
Hi guys, I would like to remotely map a network drive of my Ubuntu server on my Windows 7 laptop.

I have working SSH as I use putty to connect to the server. I also have local samba working. I have been looking online for a while and I cant seem to find a solution perfect for me.

I need a secure way of connecting to my files on the server (without using FTP as I would like to access the files directly). The other things I have seen online either involve me installing 3rd-party software on my Windows PC, using an insecure connection, using FTP or creating an NFS which does not help as I am trying to access the files on a Windows PC.



Is there anything that suits my needs?

Many thanks,
Jack

---

### Post by Habitual on 2012-04-30
Jack:

You are contradicting yourself here.
"map a network drive of my Ubuntu server on my Windows 7 laptop." and " I am trying to access the files on a Windows PC**"**
Is that "Access the files **from** a Windows PC"?

Can you please clarify the requirement in a little more detail?

SAMBA works just fine for me for mapping a Linux Share for Windows machines. It requires little or  no additional software (well, maybe an MS patch for netbios) on the Windows host.

Please let us know...

---

### Post by Frankincense93 on 2012-04-30
Sorry for any confusion,

I am trying to access the files ON an Ubuntu server, FROM a Windows PC

i.e Ubuntu Server - Windows Client.


I can do this locally using Samba, but I would like to access it remotely over the internet.

---

### Post by collisionystm on 2012-04-30
You could use FTP or SSH to access the files over the net

---

### Post by Frankincense93 on 2012-04-30
Unfortunately I would like to access the files as if it was a local folder (i.e a network drive), FTP would be awkward for this as I don't want to copy each file locally each time. Can SSH enable me to do this?

---

### Post by bubylou on 2012-04-30
If you already have openssh working on the server then you can access your files via SFTP by using a ftp client for windows. (Filezilla) That would be the simplest method of accessing your files. Just port forward your ssh port for the server. Also make sure you have enough security since your server will be accessible over the internet. (key authentication)

---

### Post by ruffEdgz on 2012-04-30
Have you tried to make your Windows machine share out a folder on your Windows machine then mounting it to the Linux server?

I don't know were your server is to your client but if I was doing this from my own computers are you house, I would do the following:

1) enable my windows machine to share a drive/folder through my domain: [http://technet.microsoft.com/en-us/library/cc770880.aspx](http://technet.microsoft.com/en-us/library/cc770880.aspx)

2) try and mount the Windows share onto my machine via the 'mount' command (or anything else that might work): [http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html)

I can't confirm this right now but once I get home, I can try it out on my windows laptop to my linux server and see if I can get a more process guide on how to do this.

---

### Post by Frankincense93 on 2012-04-30
That sounds like a good idea! I will have to try it, but is there no way of doing it the way I suggested? It just sounds like functionality thats missing! ;)

---

### Post by SeijiSensei on 2012-04-30
SMB, the protocol that Windows networking uses, was designed to run on local networks. In general, it's not considered secure enough to expose to the Internet.

One approach you might consider is using [OpenVPN]("http://openvpn.net/") to build an encrypted tunnel between your Windows client and your Linux server.  Take a look at the [documentation]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") for setting up a simple static key tunnel.  Documentation for using OpenVPN with Samba is [here](http://openvpn.net/index.php/open-source/documentation/howto.html#samba).  You can install OpenVPN on Ubuntu from the repositories with "sudo apt-get install openvpn".  The Windows client is [here](http://swupdate.openvpn.org/community/releases/openvpn-2.2.2-install.exe).

---

### Post by Habitual on 2012-04-30
Right mouse click "My Computer" > Map Network Drive... 

\\IP\SambaShareName/ 

and provide Samba userid and password and give it a network drive letter.

NOTE: You WILL have to know the SambaShareName b/c browsing to it is kind of "iffy".

You also may need to download and install/reboot after applying [this MS patch]("http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=15123"):

---

### Post by Frankincense93 on 2012-05-02
How do NAS boxes work in terms of sharing over the internet? 

As not only would I like to view my files in a remote PC, but I would like to stream videos & images. i.e I would like to be able to watch the videos stored on my server, on a remote pc.

---

### Post by collisionystm on 2012-05-02
> **Frankincense93 said:**
> How do NAS boxes work in terms of sharing over the internet? 

As not only would I like to view my files in a remote PC, but I would like to stream videos & images. i.e I would like to be able to watch the videos stored on my server, on a remote pc.


Your best bet is to use a VPN. As soon as someone discovers your server open on the net with videos and music accessible all hell will break loose.

---

### Post by Frankincense93 on 2012-05-02
Ok so if I setup a vpn (could I have a good link to a tut?) How do I go about streaming the data? Or is it just held as files and the client has to do something with it?

---

### Post by SeijiSensei on 2012-05-02
> **Frankincense93 said:**
> Ok so if I setup a vpn (could I have a good link to a tut?) How do I go about streaming the data? Or is it just held as files and the client has to do something with it?

Re-read my post above.  It has links to the relevant documents for OpenVPN.

As for the second question, yes, the clients will need software (Windows Media Player, [smplayer]("http://smplayer.sourceforge.net/"), etc.) to play the files.

---

### Post by collisionystm on 2012-05-02
> **Frankincense93 said:**
> Ok so if I setup a vpn (could I have a good link to a tut?) How do I go about streaming the data? Or is it just held as files and the client has to do something with it?


Well with a vpn, you could just simply map the drive and access the files as if you were at your computer.

Once you setup openvpn, you can just hand out the openvpn program and config file to whomever.

A vpn is also nice because if you are transferring some kind of sensitive information between machines, it will be encrypted and no one can 'sniff' the traffic.

---

### Post by Frankincense93 on 2012-05-03
[COLOR=Red]Well as the Openvpn forum seems to be very quite, could I ask for some help here?[/COLOR]

[COLOR=Black]Scratch that, I have it working now :)[/COLOR]

---

### Post by Frankincense93 on 2012-05-03
New question regarding SAMBA now:

How can I disable access to paths above the one setup in smb.conf?

As when I connect to my server using ftp, I get directed to a path. But I have the ability to go anywhere I like on the server, including the root / path.

How can I stop this?

---

### Post by SeijiSensei on 2012-05-03
Strip all the share definitions out except the one that points to your shared directory.

Usually it's not possible to move at will on the Samba server unless you have "/" defined as a share.

---

### Post by Frankincense93 on 2012-05-03
Ok I think I got my question wrong :L

When I said SAMBA, I think I meant ssh, as thats the ftp part of my server :)

(I cant access anywhere im not allowed to with SAMBA, so thats fine :) )

---

### Post by SeijiSensei on 2012-05-03
SSH gives you a shell with the same privileges you'd have if you were logged in at the console.  If you want to restrict an SSH or SFTP session, you'd need to run the sshd server daemon in a [chrooted environment]("http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229").

---

### Post by Frankincense93 on 2012-05-04
Well I think I have everything working that I need to atm, cheers for your help guys :)

---

