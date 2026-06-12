---
title: "Setting up home network with Ubuntu server"
date: 2010-11-13
forum: Server Platforms
---

### Post by Pas_sa on 2010-11-13
Hi guys,

I'm doing a massive re-setup of my home network (gigabit LAN/802.11n). Part of it will involve setting up an Ubuntu server that will backup our files and then also sync them with UbuntuOne (also act as a print server).

Though as you might see from the planned network map ([http://i.imgur.com/3glsM.png](http://i.imgur.com/3glsM.png)) every major OS platform will be running in some shape or form under the one roof. I need printing and file-sharing for all those machines.

Essentially, what's the best way to setup shares on Ubuntu so they can be easily accessed on both Mac OS X and Windows? Preferably without traditional Samba, Netbios and all that.. that is what we've used in the past and it has been an absolute bitch.

---

### Post by CharlesA on 2010-11-13
Samba would work for the Windows clients. NFS for MAC and Linx boxes.

Not sure if the XBox can see Samba shares, or if you'll need a UPNP media server for it (I've used PS3MediaServer for that).

There really isn't an easy way around not using Samba for Windows boxes.

My experience with Samba has been fine (now, at least), but it took a ton of trial and error to get it to work right.

---

### Post by Pas_sa on 2010-11-13
Hmm I was sort of hoping there was a protocol that was supported on all three platforms that I could use with ease. If I could mount NFS shares in Windows, would that be the way to go completely?

EDIT: Forgot to also ask - I wanted to use the file/print server also as a web development test server. Am I insane for contemplating to run a HTTP server off the same box as all files are hosting or can this be managed sensibly?

---

### Post by CharlesA on 2010-11-13
I've heard of NFS clients for Windows, but I don't know how well any of them work.

I think Macs can access smb shares, but I'm not 100% sure since I don't have a Mac. I know Linux boxes can connect to them as well. Maybe that would be the way to go?

Is there a reason for not using samba outside of the configuration nightmare?

I use a VM running on my NAS for web development stuff, so I don't have to worry about messing stuff up on my main box, but it should work fine either way.

I've got an internal web page running on the NAS as it is and didn't want to mess with virtualhosts and junk on it, which is the main reason I am running my web stuff on a VM.

---

### Post by Pas_sa on 2010-11-13
I was concerned about running a webserver on the same box as a security thing - having all our personal files backed up to it as well and all.

SMB is fine, but I've got it out for NetBIOS, which is essentially the source of all the problems I have currently sharing files. Usually I give up and navigate directly by IP.

Also, what file system would you recommend for a backup system/media storage server such as this one?

---

### Post by CharlesA on 2010-11-13
I use ext4, but ext3 would work fine for a file system (since it's got journalling).

If you are just using the web server locally, and it's fulled up-to-date there should be minimal risk.

As for netbios - you can set up a simple DNS server to get around the name resolution thing. I use DNSMasq on my router for that, works wonders.

---

