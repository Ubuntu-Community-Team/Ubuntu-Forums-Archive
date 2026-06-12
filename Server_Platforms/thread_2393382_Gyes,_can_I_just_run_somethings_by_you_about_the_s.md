---
title: "Gyes, can I just run somethings by you about the set up of my Ubuntu 18.4 Server .."
date: 2018-06-02
forum: Server Platforms
---

### Post by daniel228 on 2018-06-02
For the past three days, maybe heading in too five with the installation problems I have had; I have installed and set up Ubuntu 18.4 Bionic Beaver x64 on my Rack.

Now this has not been with out its problems and a steep learning curve.

Having very little to no experience with Ubuntu Server let alone 18.4's netplan, samba, natutilus  and SSH I have run in too many a problems and learned quite a lot.

I wanted too originally have a Ubuntu Server I could use as a File Host \ Media Share. Something I could port in too using a remote connection. I have installed SSH; set up the keys and in order to get Nautilus working on my Client I had too I believe set up Samba.

Using Nautilus I have connected threw this application on my Client PC too smb://user@servier_id . I am able too see the windows directory under networking.

At first I ran in too many a problems from partitioning errors, too seting up static I.P Addresses (figuring it out tbh) and then setting up a HTTP Proxy. [HTTP://user:pass:host:port](HTTP://user:pass:host:port), ..

I managed too get threw the installation I believe and everything went well with the upgrade and update of the OS. The installating of samba and ssh, was simple but the overall configuration on a learning steep curve has been challenging.


So, I have several questions if you gyes can answer them please. Everything I have done over the last 5 days and learned comes down too sharing files on my Server, so;

If I'm too share Files, and Folders on Ubuntu Server; actually copying them over from the Client too the server as I have done all this using the CLI; would this be possible if I create a downloads directory under cd / ; cd/home/user/downloads/ after mkdir downloads .

This is a headless Server so I'm doing everything threw the CLI and using the copy command to manually place my downloads or media on the server from my client, This is the only option I can think of.

Having a HTTP Proxy to an extent will change my I.P Address but leave traffic unencrypted.

Also gyes, is installing samba, and SSH, along with nautilus the rite thing too do. I installed nautilus on my client LM System.

What do you gyes think about the overall process and what I have done.

---

### Post by TheFu on 2018-06-02
Whatever works for you is how you should do it.
I would do things differently.

I wouldn't use samba/CIFS for unix-to-unix file sharing. I would use NFS.  NFS is the native file sharing for Unix systems. File permissions, ownership, and ACLs are honored with NFS, unlike with CIFS.  This is a big deal for me.

I never found a use for a squid proxy.  Seems like a good idea, but when I looked at the cache hits, it just didn't make sense.  I haven't setup squid in about 20 yrs.

ssh is a way of life. It is the basis for all sorts of other protocols, like scp, sftp, rsync, rdiff-backup, and at least 50 others.

When moving files between systems that don't have NFS connections, I tend to use rsync.  I have a clear idea for what is primary storage and what is backup storage.  I want 1 copy across all my primary storage  systems, though I might make read-only NFS mounts for other sharing methods.
For example, I run a nextcloud server that has access to thousands of family photos and our music media.  These are read-only.  And because I don't believe php web-apps are secure, to access the nextcloud system at all requires either an ssh-based SOCKS proxy or a full VPN connection.  Both work equally well.
The same applies for access to the home Plex media server - VPN or SOCKS proxy from the outside world only.

But just because I'd do things differently, that doesn't mean what you've done is _wrong_.  It is your server and only you know what you need or don't need.

There are lots of ways to host files and/or media. Just depends on which protocols you want to support and how much you care about security, or not.

There's always more to learn.  That never changes.

---

### Post by daniel228 on 2018-06-04
Thanks for the feedback. Over the last week or two I have been experimenting a lot with my Home Lab and learning quite a lot about Ubuntu. Now I'm on 18.4 were as I only used 16.4 a very small amount. I'm interested in learning as much as I can about 18.4 so I'm gonna make a separate post about PXE Boot and WoL for an Ubuntu Server Installation.

Thanks for the feed back ..

:) ..

---

### Post by TheFu on 2018-06-04
If you are new to Unix systems, then learning the basics first will make lots of things clearer. Understanding the Unix philosophy is very helpful too, since it is very different from how OSX or Windows do things.

---

### Post by daniel228 on 2018-06-04
I've been using Linux Mint for some time, I've got the commands down I need too use on a regular basis and the installation of Ubuntu has helped a lot with learning how too set up SSH and do remote updates and upgrades.

When I first made posts about not connecting online with regards to Ubuntu Sever, that was because I had problems on my network with the hardware having things on a different sub-nets was the problem I think was sitting behind the ufw.

Thanks.

---

