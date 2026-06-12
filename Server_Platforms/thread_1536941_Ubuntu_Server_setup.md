---
title: "Ubuntu Server setup"
date: 2010-07-22
forum: Server Platforms
---

### Post by Gordon D on 2010-07-22
Hi,

I am a really new to this, so please be gentle with me! :D

I am replacing a home network - Windows Server 2003 and 5 PCs (XP Pro) with UBUNTU 10.4 LTS Server and client versions. I am keeping a couple of the PCs with dual boot until I can migrate everything over (Having some issues with iTunes, Family Tree Maker, Media serving, DVD decrypt and a couple of others, but that is for another post)

It was great fun getting the server up and running using only shell commands. Took me ages just to get a folder shared! Migrating the data over from NTFS to ext3 was also fun given the limited space on the partitions.

I really only want to use the server for communal network type things ... central user account maintenance, shared folders for music, video etc and data backup. I don't need it to be performing server functions on the Internet e.g. web server etc although that may come later.

Could someone give me some advice as to how I set up central user management? All the PCs are currently setup with local user ids, and it is a bit of a pain to go round each PC every time I change something.

The server is not always up, so I need to be able to log into the local PC without it being active. I was using Active Directory on Server 2003, but I don't need anything that complex really ... just 3 or 4 users to manage.

I have been looking at the setup tutorial at [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2) but am not sure how relevant a lot of it is.

I have SSH setup so I can login remotely, NFS is working to share the folders, but that is about all I have done so far.

Loving UBUNTU and it is taking me back to my college days 20 odd years ago when I did some work in Unix and C on a DEC Vax (eek!)

Anyway, this is already way too rambling a post, but any help and advice would be very much appreciated.

Cheers

Gordon

---

### Post by tgalati4 on 2010-07-22
If you have root account on all the machines, then you should only need to log into the desktop machines (using ssh) once every few months to perform:

sudo apt-get update
sudo apt-get upgrade

What specific user management functions do you need to perform?  Printers can be shared (published) and are automatically detected by other desktop machines on the same network.  So any printers on the server will only show up when the server is up.  Direct-connect ethernet printers work well in this setup.

After a few months, each user will have customized their desktop environment to their liking.  You shouldn't have to log into their accounts to make mods.

If you need to place an icon on their desktop to open a server application, then you can send an email with a script to place that icon on the desktop.

Without a specific maintenance task, it's hard to recommend a procedure.

---

### Post by Gordon D on 2010-07-22
> **tgalati4 said:**
> What specific user management functions do you need to perform? [snip}
Without a specific maintenance task, it's hard to recommend a procedure.
I suppose the main thing would be their desktop customisations so that when they move to another PC whatever changes they make would follow them.

If I make a change to the /etc/fstab file for example, how can I distribute this to all the clients automatically?

---

