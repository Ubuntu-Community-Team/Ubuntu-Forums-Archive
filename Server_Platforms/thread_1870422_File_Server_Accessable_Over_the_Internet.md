---
title: "File Server Accessable Over the Internet"
date: 2011-10-27
forum: Server Platforms
---

### Post by spuzzdawg on 2011-10-27
Hi Everyone,

I would like to implement a home file server, however, what I would like to achieve seems to be a little more complex than the standard. Essentially, there are several laptops and desktops in the household that need to keep their files synced. There is also a central media collection that the laptops and desktops need access to. This setup seems easy enough to achieve using a combination of samba and rsync, however, the problem is getting the laptops to work when they are away from the local network. Samba doesn't work over the internet and I'm not aware of anyway to tell rsync to swap between local and non-local addresses.

As I see it there are two types of sharing required:

[LIST]
[*]Media collection should be stored on a central server at home as the media collection is going to be too large to store copies on each individual computer. Each computer should mount the media collection through the network. Ideally the media collection should be available to the laptops over the internet but it is not a deal breaker if they can't. The laptops (and desktops I suppose) must be able to boot even if the media collection can not be accessed. (I've had problems with a missing connection to a samba share causing the computer to totally hang before)
[*]Personal files should be stored locally on each computer and backed up to a central server at home. Some, but not all, files will be required to synchronize between computers and the central server. File synchronization should be able to work across the local network when the laptops are locally connected to the central server but also work across the internet when the laptops are away from home. The computers must be able to continue to work if the server can not be contacted either locally or through the internet.
[/LIST]
I have had a go at setting something like this up with a number of setups, namely iFolder and Samba but it is access through the internet that seems to be the big issue. I suppose what I'm really after for personal files is an application that works in a similar manner to Spideroak (which is what I am currently using to synchronize personal files) that back up to my own server instead of their cloud. 

Does anyone have any ideas on how to achieve something like this?

Thanks,
spuzzdawg

---

### Post by papibe on 2011-10-28
Hi spuzzdawg.

I've accomplished some of the things you want to do. I would be happy to give you some tips, but since you have a lot of requirements I wonder which one has more priority.

These are some ideas:
[LIST]
[*]In order to access your server from the Internet, you need a service like Dynamic DNS (free).
[*]You can automate your rsync using a script that determines if the machine is in the LAN, or outside of it.
[*]I would not mount the Samba share, but use media apps that can handle the url smb://server/share. That way you don't need to mount anything, and boot time don't depend on access to the home server. Example: XMBC.
[*]For most cases rsync will be enough. For sophisticated two-way synchronization you can use Unison.
[*]For alternatives to 'cloud syncing' check [Sparkleshare]("http://sparkleshare.org/") or [ownCloud]("http://owncloud.org/"). Both of them can be host in your own server.
[/LIST]
Tell me if you want more details on those ideas, or if you want suggestions for another of your concerns.

I hope this helps,
Kind Regards.

---

