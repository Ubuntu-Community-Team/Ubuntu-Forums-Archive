---
title: "Wanting to create a home server."
date: 2010-09-13
forum: Server Platforms
---

### Post by vanstinator on 2010-09-13
I am in the process of doing the necessary research on what software I would need to start a basic home server/media center.  My goals for the system are as follows.

1.  Provide a basic NAS function for all the devices on my network.
2.  Stream media to boxee across the network.
3.  Automatically backup my windows computer to the linux server.
4.  Provide ssh access so that I might access content/backup when I am away from home.

I have the first to figured out, I basically just need to use samba and setup the sharing, the 2nd two I cannot find the tutorials I need.  Any links/help would be appreciated.  I am planning on using Ubuntu 10.04 for this system, I don't have a ton of experience with the command line, and until I do, I am not interested in the server version of ubuntu.  Any help you guys can provide would be awesome.  Thanks!

---

### Post by arrrghhh on 2010-09-13
For the automatic backups... it really depends on what you want to backup.  It'll probably be easier to setup something on the Windows machine to send the backup files to the server - that way (assuming the server is always available) the client can push the backup files whenever it's conveient for the client to do so.

That is a good solution if you just want to backup specific files/folders... now if you want a complete, bit-for-bit copy of your hard drive that gets a little trickier - and IMHO unnecessary for most people.  Amahi has a really good solution for this, but for something more agnostic I'd look at Clonezilla.  The nice thing about Amahi is it takes care of all the worries related to backing up bit-for-bit - right down to PxE booting the clients.

SSH access is quite easy - assuming you have SSH configured locally, you just need to forward the port on your router and make sure that SSH is set to listen on your firewall.  I use UFW because it's easy - I would not recommend running Ubuntu without the firewall enabled, which is how it comes by default (of course there's no services listening by default either).

For security's sake, you may want to setup SSH to listen on a port other than 22.  Locally I have SSH listening on 22, but I forward that port to a different port for WAN traffic (makes it slightly more difficult if someone was trying to brute-force their way into the machine).

---

### Post by codmate on 2010-09-13
Samba will handle all your NAS needs.

These are the media streaming solutions I use with 10.04:
[http://www.twonky.com/products/twonkyserver/](http://www.twonky.com/products/twonkyserver/)
[http://www.mysqueezebox.com/download](http://www.mysqueezebox.com/download)

Another popular one is Swiss Center:
[http://www.swisscenter.co.uk/](http://www.swisscenter.co.uk/)

I'm currently using the box for torrents too, using deluged and deluge-web.

SSH is easy to set up.

Rsync will do backup duties. There are several versions for Windows.

---

### Post by vanstinator on 2010-09-13
Ok guys thanks, it will be a few weeks yet until I have a box to set this up on, so I can't give any progress updates, but this info helps a lot so thanks.

---

