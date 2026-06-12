---
title: "Help Setting a Home Server"
date: 2009-03-01
forum: Server Platforms
---

### Post by daf2 on 2009-03-01
Hello all,

For a long time now I've had a windows box as my home server, so far it's been doing the job ok but I wanted to make it better, I considered Windows Home Server as the way to go, but... Linux seems to be so much more flexible for my "special" needs that it just seems a better choice. Unfortunately I&#8217;ve always been a windows user, so, not knowing much of Linux I thought I'd ask for help and advice here having been told Ubuntu was one the most popular and noob friendly distro around (boy was that a long intro :P).

Currently my windows server provides:
* SMB File Server (with per user permissions)
* Apache Web Server + PHP + SVN
* bittorrent client with utorrent webui
* ftp server with filezilla

I&#8217;d expect a linux server to do the same and hopefully solve the following &#8220;problems&#8221;:

**Storage**
Currently I&#8217;m using HDDs with single partitions and a "master folder" that's made up of junction points (similar to hardlinks) to folders on the several partitions so I can share it as one big folder with Volume Shadow Copies enabled so I can recover a file that's deleted by mistake.

It requires some tedious management when one hdd becomes full but it also allows me to keep the hdd "lose" and easily readable by any external computer. I've been looking into this for some time now and seems a virtual unionfs like fs based on fuse might be the solution. I'd keep the partitions in ntfs and just create a folder to direct the fuse fs to it. Is this crazy? is there a better way? Also, it seems samba has shadow copies but only under xfs, is there any other way to make a sort of .Trash folder? I&#8217;d be happy with just a safety net for accidental deletes (I keep all the important stuff backed up anyways).


**Multiuser webui type torrent client**
Unlimited internet access isn't fully widespread in my country yet so I allow friends with striker web limits to use my torrent client. Is there a simple webui based bittorrent client for linux with some user separation? all I really want is that users can't delete each others torrents by accident and possibly not see them for privacy.

**Users logins**
Right now when I want to add a new user to my server I have to create a login for each service and go about setting it all by hand. Is it possible in linux to make a 1 login for everything type thing? I'm not afraid to write a little code but I'd like to know if it's really hard or easy.

**Updating**
Also on windows I have to update each application by hand, I'm led to believe that in ubuntu all I really need is apt-get update command and i would be done. Is it that simple?


I'm sorry for the Great Wall of Text, Linux is still alien to me and I don&#8217;t know any Linux master to pester with questions :p

Any help appreciated,
daf

---

### Post by cferriby on 2009-03-01
I have a very similar setup only I have one hard drive for my server. but I use webmin for administration of pretty much everything system related. there are tutorials on setting it up, just Google it. 

torrentflux-b4rt for torrent use. it has all the features that you asked about

i only use a single user sign on but i think that these services are based on system users. not sure but its not too hard to set up users separately.

also if your interested, i use ushare for streaming videos music and pictures to my xbox, very easy to set up also

and firefly for an itunes music shared play list server. 
also very easy to set up.

---

### Post by balloooza on 2009-03-01
Ebox is awsome,
I am sorry that I didn't realy read your whole  post :), but I get the idea.

ebox is ubuntu with a package on top called ebox
in addition this ebox-platform as they call it (ebox-platform.com)
makes a cd to install it all automagicly, so, if you get the latest .iso you can install a fully operational and easy server.

look at some of the screenshots I took a while ago for somthing I was How-toin a while ago (how to set up VPN, witch I did get working, in about 5 minuits)

So basicly it will manage all the users, you can setup windows shares, and give individual accounts access to certain shares, aand even act as a windows domain (i said domain, NOT workgroup)

I use the jabber server at my house for in home chatting.

One question, do you use the windows server as a gateway, with a dhcp server and dns, or is it connected to the same network as all the other computers

eg1

LINKSYS ROUTER (or somthing simeler)
       |
  +----+-------+----------+           wireless )))
server      desktop1   desktop2       laptop

or
eg2
Windows server (or somthing simeler)
       |
  +----+-------+----------+           wireless )))
Wireless AP  desktop1   desktop2       laptop

I hope the text drawing stay intact.

---

### Post by daf2 on 2009-03-04
Thanks for suggesting ebox, I'll look into it, still would the fuse file system be a good idea?

---

