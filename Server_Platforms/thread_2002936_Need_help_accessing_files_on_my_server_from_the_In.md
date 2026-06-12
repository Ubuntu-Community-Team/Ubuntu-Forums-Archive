---
title: "Need help accessing files on my server from the Internet"
date: 2012-06-13
forum: Server Platforms
---

### Post by tj107us on 2012-06-13
Hey guys I building a file server that will hold my pictures, music, videos, and other important data that i can access anywhere by using the internet. I'm using Ubuntu Server 12.04 64-bit. What my question is, what packages would i need to install in order to acomplish this? And how do i set it up?
 
 
thanks,
tj

---

### Post by Dragonbite on 2012-06-13
**One key is the server needs to be connected to the Internet.  **

If it is plugged into your home system, is it behind a firewall that needs to have the ports open, or are you hoping to use a VPN (virtual private network) to connect to your network from virtually anywhere?

Or are you looking to have it hosted by a web hosting company like Rackspace or Amazon or other?  

**Then, how do you find it?**

There is DynDNS which gives you a single location to go to, and your server is told to periodically "phone in" to give the service it's current IP address.  This is handy for home-based servers.

Otherwise, with a hosted solution either the hosting company will give you an address (often of gibberish) or you can pay for a domain and navigate to it by [http://whateveryouchose.com](http://whateveryouchose.com)).  Of course that also means everybody else can too ;)

**FTP**
I'm not sure the exact applications for doing this, but you'll want to make it as secure as possible.  It also depends on how you want to access these files? Browser? Program?

Or are they just for backup purposes?

**Local file server**
The easy route is to use a cloud storage solution; Ubuntu One, Dropbox, Amazon Cloud Drive, Google Drive, etc.  Some even include options to play or view the media over the cloud.

Now, if you are looking for having it just locally, that's slightly easier: install Samba for file sharing.

If you want it even easier, look at Zentyal, which includes a web interface for managing an Ubuntu server underneath.

---

### Post by LHammonds on 2012-06-13
Dragonbite mentioned the important bits about accessing a device in your home from anywhere on the Internet.

But beyond that, you might want to look into [OwnCloud]("http://owncloud.org/") for the sharing application.

**EDIT:** I'd recommend changing your thread title from "Server" to "Need help accessing files on my server from the Internet"

LHammonds

---

### Post by CharlesA on 2012-06-13
Title changed.

sftp ftw.

---

