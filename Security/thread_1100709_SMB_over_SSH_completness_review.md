---
title: "SMB over SSH completness review"
date: 2009-03-19
forum: Security
---

### Post by LakesProse on 2009-03-19
[So I roamed Google and Ubuntu forums for someone who had a truly similar question to mine but found none, so here it goes. It's quite a long post, sorry for that! I am trying to figure out if I've left out any security concerns]
So I've got myself Ubuntu 8.10 installed and I am implemented Samba sharing over SSH. From a Windows client, this is how it happens.

A .bat file loads putty with a profile and RSA key.

That profile is configured to tunnel local connections from port 139 to server's port 139.*

That profile uses a user called (let's say) 'brutus'. 

On the server, brutus has shell set to /bin/false.**
Also server-side, sshd_config uses the PermitOpen option to only allow forwarding to a certain IP address and certain port.

The samba share is pointed towards /media/share which is a partition (rather, it's a HDD) by itself. That partition is mounted in fstab with the noexec option.

That /media/share is also being incrementally backed up using rsync.

*Actually, Windows need a loopback adapter created to bind to locally. Also, for some reason, forwarding the connection to localhost on the server didn't work, I had to use the server's IP address on LAN. So it's more like 10.0.0.1:139 to 192.168.0.106:139.
**since shell=/bin/false, putty must use -N option when called to not actually request a shell and only ask to authorize to permit port forwarding. 

ALL RIGHT! So, that's about it. Ssh server is secure in itself I'd think, changed default port, only allows ssh2 connections, only allows rsa authentication, exhaustive list of allowed users to login, root login disabled, OSSEC's supposed to handle iptables, firewall only forwards ssh's port.

I see 2 possible flaws:
The RSA key is not really secure. Since it's resting on a machine at all times, it's relatively out in the open. But I figure it's not that bad. Worst case scenario, someone gets the key, gets in the system and deletes all my files (backups, yeah!, saved!) or fills up all available space (incremental backups, yeah!). Since the drive is mounted as noexec, no problem.

I know samba connects using smb over netbios or smb over tcp/ip directly and I know associated ports are 139 and 445. I'm just wondering, can someone do any damage on my network even though I restricted forwarding to port 139 ?

Sorry again for the long post, any input (or actually having read all that) is appreciated.

---

### Post by HermanAB on 2009-03-19
It is secure.  Your firewall only needs to allow port 22.

See this:
[http://www.aeronetworks.ca/samba-ssh-tunnel-howto.htm](http://www.aeronetworks.ca/samba-ssh-tunnel-howto.htm)

Cheers,

Herman

---

### Post by LakesProse on 2009-03-19
Hey there Herman, yeah my firewall already only forwards my ssh port (which isn't 22 anymore :P )

I also read your How-to and it's quite good. Helped me understand why file sharing must be disabled and why a trick must be used if file sharing is to stay enabled (loopback adapter, picked up here [http://www.blisstonia.com/eolson/notes/smboverssh.php](http://www.blisstonia.com/eolson/notes/smboverssh.php)).

---

### Post by dfreer on 2009-03-19
This is something I have been considering myself, although my server is currently down so I can't really do much right now. Be interesting to see how you progress, and once I get my server up again I can probably help out (if you haven't already got it working).

---

### Post by bodhi.zazen on 2009-03-19
Why not use ssh only ?

You can mount shares on linux clients with sshfs and from windows clients with winscp.

In terms of ssh security, there are two keys, public and private. One needs both to decrypt. The public key is on the server and the users have the private key.

So to break in we would need to know a valid user name, a copy of the private key, and a password.

OSSSEC will make brute force attempt impractical to say the least (as would denyhosts, fail2ban, or even a simple rule in iptables).

---

### Post by LakesProse on 2009-03-19
Hi dfreer,
well it's progressing quite well as in it's live and running and my winamp is playing music off my server through ssh as I type this! 

I forgot to mention this: using puttytray helps a lot. It's putty + capacity to sit quietly in the system tray ([http://www.xs4all.nl/~whaa/putty/](http://www.xs4all.nl/~whaa/putty/))

I do feel the -N option in putty is not publicized enough (to allow port forwarding when user has a /bin/false shell) just as  the PermitOpen option is sshd_config isn't either.

---

### Post by LakesProse on 2009-03-19
Hi bodhi.zazen,
So yeah to break in, you need my private key. That key is sitting in a folder with scripts that have the username for ssh and username/password for the samba password. So if you can grab the key, you can probably grab everything you need to login (because the setup is constructed to allow simple drive mapping over the web).

well I didn't know you could actually map a drive letter using winscp and mount in linux using sshfs, so that's interesting to discover. 

I do have one problem, I'm under the impression that those two methods require a user with a shell that isn't false. And then that would require some jailing/chrooting. And so, it seems just more secure to use samba's confined space instead. 
This was more like a solution for a friends-only ftp since vsftpd has me crawling up some teflon walls (not vsftpd but the protocol itself, it seems).

---

### Post by bodhi.zazen on 2009-03-19
> **LakesProse said:**
> Hi bodhi.zazen,
So yeah to break in, you need my private key. That key is sitting in a folder with scripts that have the username for ssh and username/password for the samba password. So if you can grab the key, you can probably grab everything you need to login (because the setup is constructed to allow simple drive mapping over the web).

:lolflag:

You should fix that.

> well I didn't know you could actually map a drive letter using winscp and mount in linux using sshfs, so that's interesting to discover. 

Well, not map a drive, but assess stuff over ssh with a gui on windows, yes.

---

### Post by HermanAB on 2009-03-19
It really depends on the user.  I find SSH with Filezilla easy from Windows, but some people really want a VPN with the distant machine mapped to a drive letter.  Tunneling SMB over SSH achieves that quite neatly.

Cheers,

Herman

---

### Post by LakesProse on 2009-03-19
All right so I guess my setup is all right ? No major improvements? No screaming security holes ?

---

### Post by dfreer on 2009-03-20
> **bodhi.zazen said:**
> Why not use ssh only ?

You can mount shares on linux clients with sshfs and from windows clients with winscp.

EDIT: Whoops, missed a whole conversation. Yeah, I need the ability to access files as if they were local (i.e. map a network drive in windows). It isn't just downloading/uploading files to the server, it's transparently streaming my media.

---

### Post by LakesProse on 2009-03-21
well dfreer, for getting stuff working transparently, smb over ssh method gives that (under Windows anyways, that's where I tested it more extensively but I'm pretty sure it rocks under other OSes too). 
It's not as hard you'd think, if you understand a little bit stuff about ports, IP addresses and SSH.

---

