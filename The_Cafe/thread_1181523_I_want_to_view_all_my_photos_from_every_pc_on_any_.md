---
title: "I want to view all my photos from every pc on any computer..."
date: 2009-06-08
forum: The Cafe
---

### Post by davidmigl on 2009-06-08
I want something that will decentralize my photo collection and make it available anywhere on my home network. Additionally, a great degree of user friendliness and automation would be nice, as well as interoperability with windows machines.

As soon as photos are imported from a camera onto a computer, they would be copied onto a central server/storage device that would organize them into a hierarchy and make them available over the network. I'm thinking the "my pictures" folder on the windows pcs would be mapped to the server drive.

Basically what I want is something like the [Intel Whole Home Storage](http://www.intelconsumerelectronics.com/Consumer-Electronics-3.0/Whole-Home-Storage.aspx) concept. That's but a pipe dream for now. The next closest thing is something like an HP mediasmart server with it's media collector function but that involves windows (yuck) and hp (even more yuck).

I realize I might not get a lot of user-friendliness or automation from a linux application. But is there something I could at least try? Does something along the lines of this decentralized photo manager concept exist?

---

### Post by Sealbhach on 2009-06-08
You could try Moovida Media Center (formerly called Elisa). It's got a Devices and Shares section, maybe it would do what you need.

[http://www.moovida.com/features/](http://www.moovida.com/features/)

I think you also need to install Samba to connect to the Windows machines.

.

---

### Post by fatality_uk on 2009-06-08
> **Sealbhach said:**
> You could try Moovida Media Center (formerly called Elisa). It's got a Devices and Shares section, maybe it would do what you need.

[http://www.moovida.com/features/](http://www.moovida.com/features/)

I think you also need to install Samba to connect to the Windows machines.

.

Couldn't agree more. Moovida works a treat. As long as you can see a drive or attached device, then it will scan that for you.

---

### Post by billgoldberg on 2009-06-08
> **davidmigl said:**
> I want something that will decentralize my photo collection and make it available anywhere on my home network. Additionally, a great degree of user friendliness and automation would be nice, as well as interoperability with windows machines.

As soon as photos are imported from a camera onto a computer, they would be copied onto a central server/storage device that would organize them into a hierarchy and make them available over the network. I'm thinking the "my pictures" folder on the windows pcs would be mapped to the server drive.

Basically what I want is something like the [Intel Whole Home Storage](http://www.intelconsumerelectronics.com/Consumer-Electronics-3.0/Whole-Home-Storage.aspx) concept. That's but a pipe dream for now. The next closest thing is something like an HP mediasmart server with it's media collector function but that involves windows (yuck) and hp (even more yuck).

I realize I might not get a lot of user-friendliness or automation from a linux application. But is there something I could at least try? Does something along the lines of this decentralized photo manager concept exist?

Well it's pretty simple.

Figure out what pc you want to act as the main server, where all the data will be stored.

If you only use Linux, SSH will do this.

You can use the "Connect to Server" app under Places to connect to the servers from any pc. Use the Bookmark feature in the app, to display the server permanently in Nautilus on all computers.

Make sure the Photo folder on the server has read/write permissions for anyone on the network so all the users can put their pictures in it.

Automatically moving the pictures will be a bit harder.

You can run a bash script with cron to move all the pictures in /home/Pictures or something every hour onto the shared folder.

If you have windows pc's as well, you can use Samba instead of SSH.

---

### Post by TuckLive on 2009-06-08
I run [_Gallery_]("http://gallery.menalto.com/") on my home server.  Installation is easy and the web interface is pretty nice.

---

### Post by davidmigl on 2009-06-09
Those are some very helpful recommendations. Thanks for your help!

---

### Post by LucianoP on 2009-11-17
try [Dropbox]("https://www.dropbox.com/referrals/NTIwODEyNzY5")
this app is PERFECT!
besides synchronising folder between your different machines it also works with different SO's, supporting Linux, Windows, MAC OS, and even work with iPhone. It also keeps backup on a server that you can access via browser even if Dropbox is not installed
since you are looking for a picture tool, I can tell you it is just create a folder and put some pics there, then right click the folder and choose "Copy Public Gallery Link" and paste is on an email or IM. Wonderful!
its only limitation is that you can only get about 2.5GB for free.. you have to pay if you want to use more space

PS. sorry if this post looks like an add, but I just got too amazed with this app
= )
cheers

---

