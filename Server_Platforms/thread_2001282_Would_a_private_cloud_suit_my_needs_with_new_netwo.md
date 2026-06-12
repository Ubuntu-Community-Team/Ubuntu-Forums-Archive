---
title: "Would a private cloud suit my needs with new network setup"
date: 2012-06-10
forum: Server Platforms
---

### Post by rough60 on 2012-06-10
Hi all,

Currently I have one laptop with 3 standard users, this laptop is incrementally backed up to a server nightly.

I have got a new laptop I am adding to the network and would like to configure it differently.

The server has a hard drive partitioned, user a, user b, user c.

As each user can use either laptop I would like it so that if they work on a file on one laptop then open the file on the other laptop, the most up to date version of the file is opened.

I was thinking to setup the default 'save as' place would be the users partition on the server hard drive over ssh, but I have no idea how to do this. Then I thought maybe a private cloud running on the server would be easier.

I don't know if either of these options is possible or the pros and cons for either.

All advice appreciated and links to more info/guides would be great.

Thanks.

---

### Post by spynappels on 2012-06-11
I think the word cloud is the most misused word in IT at the moment, I don't think a true cloud would be of any help to you at all.

What would be helpful is having a network location mounted as user a, user b and user c's home directory, meaning that whichever laptop they log on to, as long as it has network access to the network storage server, their storage will be mounted as home.

Are both laptops running Linux? Will they be used outside of the LAN at all?

---

### Post by volkswagner on 2012-06-11
As spynapples asked it would be helpful to know what operating system the laptops are running.

If you want this function to work strictly over LAN, setting up an NFS share would be a good solution.  You could setup three shares (one for each user) or one share with subfolders for each user.

If you want this to work outside your LAN, you could consider VPN setup, or SFTP.

A filesync solution may also be what you are after.  I have recently tried [Owncloud]("http://owncloud.org/") which seems pretty stable at the moment.  I have not done any in depth testing yet.  It does have other functions such as shared contacts and calendars.

---

### Post by rough60 on 2012-06-12
Thanks guys

> **spynappels said:**
> 
What would be helpful is having a network location mounted as user a, user b and user c's home directory, meaning that whichever laptop they log on to, as long as it has network access to the network storage server, their storage will be mounted as home.


This is exactly the kind of thing I'm after, auto mount the partition on the server as the home directory for each user.

All machines are Ubuntu 12.04 and 99% of the time the connection would be within the LAN.

Any guides to doing this, I couldn't find any.

Thanks again,
Cheers

---

### Post by SeijiSensei on 2012-06-12
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by rough60 on 2012-06-13
> **SeijiSensei said:**
> [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Excellent, TY. I'll give it go.

Cheers

---

### Post by spynappels on 2012-06-13
I actually used that how-to last night to connect my Raspberry Pi running OpenElec to my file server and it worked flawlessly. No more Samba for my media streaming!

---

### Post by rough60 on 2012-06-13
This is a pretty basic Q, but just wondering before I start, for user a/b/c to have access to their own drive on the server, do they need to have a account on the server? Or can I configure NFS to load it into their directory automatically? What I mean is the server accepts a login from the laptop IP address and NFS looks to see who is logged on from this IP address, and loads the appropriate drive on the server into the laptop directory tree.

Also, if a user has to be added to the server, can this account be setup so they can't login to the server manually (through keyboard attached or over the network) and NFS will still load their own drive into the directory tree?

Thanks

---

### Post by rubylaser on 2012-06-13
> **spynappels said:**
> I actually used that how-to last night to connect my Raspberry Pi running OpenElec to my file server and it worked flawlessly. No more Samba for my media streaming!

I know this is off topic, but how well does the Raspberry Pi + Openelec work.  I'm especially interested in the interface speed with a large library.  I have (2) Shuttle XS35GT's with Openelec and they work great, but I'm looking to add a Raspberry PI for the TV in our bedroom.  Thanks.

---

### Post by spynappels on 2012-06-13
> **rubylaser said:**
> I know this is off topic, but how well does the Raspberry Pi + Openelec work.  I'm especially interested in the interface speed with a large library.  I have (2) Shuttle XS35GT's with Openelec and they work great, but I'm looking to add a Raspberry PI for the TV in our bedroom.  Thanks.

I didn't have too much time to play with it other than verifying it worked, but as a general comment, I'm very impressed. Navigating the menus is a little slow, as can be expected with 120MB of RAM available, but playing of the videos, both in SD and HD works very well indeed. I'm seriously impressed and will be doing some more in-depth testing over the next week or so. A Logitech wireless keyboard and mouse combo works very nicely, mine will also live behind my TV.

I'll report back when I've had more time to do some stress testing, but my initial view is very positive indeed.

---

