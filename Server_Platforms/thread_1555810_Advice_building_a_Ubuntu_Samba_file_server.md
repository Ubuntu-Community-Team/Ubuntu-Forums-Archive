---
title: "Advice building a Ubuntu Samba file server"
date: 2010-08-18
forum: Server Platforms
---

### Post by chris2922 on 2010-08-18
Hi everyone, i've been using Ubuntu Desktop for a few years but am finally posting to the forum for advice on building a server.

I currently have a QNAP 'TS-209' 2 bay NAS.  I have it set to RAID1 - Mirror.  Its a handy little box, performing tasks like scheduled Bit Torrent downloading, and can stream to my Ubuntu / XBMC boxes around the house no problem - a couple of different 720p streams at the same time runs fine with no dropped frames.

Thing is, im out of space.  I dont want to start backing up to DVD because the point of my media library is that its online all the time.  I have already reached the QNAP's disc size limit with 2 x 2tb drives, so i need a new server.

I was going to get a QNAP 4 bay system, but to try and future-proof myself a stage further I am considering building a Ubuntu box and running the Server O/S on it.  I would then connect the server to one of these:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816132016](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132016)

Its a "Rosewill RSV-S8 SATA 8-Bay RAID 0/1/10/5/JBOD Storage Enclosure / Port Multiplier/ PCIe card included".

Apparently the eSATA card included is a bit slow ([COLOR=Red]?[/COLOR]), but the enclosure is fine.

I hope the result of this would be i get a much more expandable server than a 4 bay QNAP - but im worried it might prove to be hard to set up, and im not sure if a Ubuntu server can replicate some of the features of the NAS - namely:

[COLOR=Red]1[/COLOR]) Remote log in to server for admin tasks so it doesnt need a screen/keyboard/mouse.  The QNAP has quite an extensive web-based admin client.
[COLOR=Red]2[/COLOR]) Remote login to control a Bit Torrent client.

I had considered Windows Home Server because it seems to provide the remote login side of things - but id rather go with Linux if possible.

I've rambled on enough - can anyone offer any advice/info?

---

### Post by arrrghhh on 2010-08-18
You can certainly do those two things with Ubuntu server.

I have an Ubuntu server that is completely headless (just power & network plugged into it) and I can manage it remotely in varying ways.

Webmin is probably going to be the tool I recommend for administration of the server as a whole.  Ebox is another alternative, but I personally prefer Webmin.

For a remote login to control a bit torrent client, there are several options.  Transmission has a webUI out of the box.  I wasn't a big fan of it, I felt kinda limited by the client - it was stupid easy to setup, so it really depends on what you use/need it for.  It's also been a couple of years since I looked at Transmission, so it may be better now.

In lieu of Transmission, I use/recommend rtorrent.  It runs with very little footprint, and is extremely customizable.  I use a front-end that is very functional & (IMHO) pretty :P  It's called 'rutorrent' and hands down is the best web front end for rtorrent (again, IMHO...)

So like I said, Ubuntu server can easily meet your needs, and then some.

---

### Post by MakOwner on 2010-08-19
> **chris2922 said:**
> Hi everyone, i've been using Ubuntu Desktop for a few years but am finally posting to the forum for advice on building a server.

I currently have a QNAP 'TS-209' 2 bay NAS.  I have it set to RAID1 - Mirror.  Its a handy little box, performing tasks like scheduled Bit Torrent downloading, and can stream to my Ubuntu / XBMC boxes around the house no problem - a couple of different 720p streams at the same time runs fine with no dropped frames.

Thing is, im out of space.  I dont want to start backing up to DVD because the point of my media library is that its online all the time.  I have already reached the QNAP's disc size limit with 2 x 2tb drives, so i need a new server.

I was going to get a QNAP 4 bay system, but to try and future-proof myself a stage further I am considering building a Ubuntu box and running the Server O/S on it.  I would then connect the server to one of these:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816132016](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132016)

Its a "Rosewill RSV-S8 SATA 8-Bay RAID 0/1/10/5/JBOD Storage Enclosure / Port Multiplier/ PCIe card included".

Apparently the eSATA card included is a bit slow ([COLOR=Red]?[/COLOR]), but the enclosure is fine.

I hope the result of this would be i get a much more expandable server than a 4 bay QNAP - but im worried it might prove to be hard to set up, and im not sure if a Ubuntu server can replicate some of the features of the NAS - namely:

[COLOR=Red]1[/COLOR]) Remote log in to server for admin tasks so it doesnt need a screen/keyboard/mouse.  The QNAP has quite an extensive web-based admin client.
[COLOR=Red]2[/COLOR]) Remote login to control a Bit Torrent client.

I had considered Windows Home Server because it seems to provide the remote login side of things - but id rather go with Linux if possible.

I've rambled on enough - can anyone offer any advice/info?

I did exactly what you have described, but I used these (I picked them up at the local Fry's for about $250 each):
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816111050&cm_re=Sans_Digital-_-16-111-050-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16816111050&cm_re=Sans_Digital-_-16-111-050-_-Product)

I don't know if the controller provided is different, but I saw stuff on the net about issues with speed too.  I set one box up with 9.10 desktop so I could run k9copy to rip directly to the local storage.  

I can do anywhere from 40 - 60 MB/s local transfers on across the controller on DVD size files, and that keeps me pretty happy -- I run 8 1.5TB 5900RPM drives using software raid for raid5.

I share everything via NFS - we are all Mac or Linux so no need for Samba for my media files.

I have an Openfiler server that handles NFS and Samba where I need to swap back and forth between work laptop and my home machines.

If I can answer any questions about my configuration, let me know.

---

### Post by Plecebo on 2010-08-19
> **MakOwner said:**
> I did exactly what you have described, but I used these (I picked them up at the local Fry's for about $250 each):
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816111050&cm_re=Sans_Digital-_-16-111-050-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16816111050&cm_re=Sans_Digital-_-16-111-050-_-Product)

I don't know if the controller provided is different, but I saw stuff on the net about issues with speed too.  I set one box up with 9.10 desktop so I could run k9copy to rip directly to the local storage.  

I can do anywhere from 40 - 60 MB/s local transfers on across the controller on DVD size files, and that keeps me pretty happy -- I run 8 1.5TB 5900RPM drives using software raid for raid5.

I share everything via NFS - we are all Mac or Linux so no need for Samba for my media files.

I have an Openfiler server that handles NFS and Samba where I need to swap back and forth between work laptop and my home machines.

If I can answer any questions about my configuration, let me know.

This is pretty much exactly my setup as well. I have 8 1TB drives in a raid6. I use this to rip DVD's to and stream them to my XBMC. I mostly store full .iso copies of movies/TV shows, lots of .flac and .mp3 files, lots of photos, and some personal files. I use webmin to manage the machine. 

That is until the other day when it was hot in my house and I was copying files accross the network to the server and the array crashed on me. 

Now i'm worried i've lost the data :( Still working to repair, (see my post). 

The setup works VERY well, I did get another esata controller card. If you decide to do that be careful because not all of the controllers will allow you to run in this configuration. 

I would also be conscious that this thing can get warm, so you may want to choose the location in your home carefully.

If I had to do it all over again I might try out freenas which has a web interface and additionally zfs support. Though when I started out I was really focused on the dual disk redundancy of raid6 (a lot of good that did me). Good luck!

---

### Post by MakOwner on 2010-08-19
> **Plecebo said:**
> This is pretty much exactly my setup as well. I have 8 1TB drives in a raid6. I use this to rip DVD's to and stream them to my XBMC. I mostly store full .iso copies of movies/TV shows, lots of .flac and .mp3 files, lots of photos, and some personal files. I use webmin to manage the machine. 

That is until the other day when it was hot in my house and I was copying files accross the network to the server and the array crashed on me. 

Now i'm worried i've lost the data :( Still working to repair, (see my post). 

The setup works VERY well, I did get another esata controller card. If you decide to do that be careful because not all of the controllers will allow you to run in this configuration. 

I would also be conscious that this thing can get warm, so you may want to choose the location in your home carefully.

If I had to do it all over again I might try out freenas which has a web interface and additionally zfs support. Though when I started out I was really focused on the dual disk redundancy of raid6 (a lot of good that did me). Good luck!


I had been running openfiler in tower cases with as many 500GB SATA drives as I could stuff in for file servers - all of them ran the drives hotter than I liked.  This SansDigital box has kept them MUCH cooler.
sda here is the sata drive in the head with the OS and configuration - it's a shuttle something-or-other.  The other 8 devices are the 8 drives in the external enclosure.  These are all Seagate 1.5TB 5900RPM drives.
I have another one connected to my desktop that still has 8 500GB Seagate 7200RPM drives that run the same, so long as I don't block airflow to the cabinet.  Considering I saw these same drives run between 102 and 106 regularly in Antec tower cases with all the extra fans I could stuff in them.... 

SATA Drives
/dev/sda TC 40 TF 104
/dev/sdb TC 34 TF 93
/dev/sdc TC 33 TF 91
/dev/sdd TC 33 TF 91
/dev/sde TC 34 TF 93
/dev/sdf TC 34 TF 93
/dev/sdg TC 35 TF 95
/dev/sdh TC 33 TF 91
/dev/sdi TC 35 TF 95

The second SD case I bought doesn't have a manual switch on the power supply.  That's a bit annoying, but I rarely ever turn that one off.

---

### Post by chris2922 on 2010-11-20
I'm still moving towards a new file server to replace my 2 Qnap NAS boxes - which are rapidly running out of space, and cant be expanded any further.

The Rosewill RSV-S8 still seems like a good base to build the disc array from.  I could put 4 2tb discs in from the Qnap's as a starter.  My old Dell desktop (4700!) is a bit of a power waster though.

The 2 Qnap's will happily spin their 4 combined discs and download torrent files all day and use less power than the Dell.  If im going to go the 'headless server' route (which id like to), i was thinking of something like the Dell Inspiron Zino HD for £329/$523:

[http://www1.euro.dell.com/uk/en/home/Desktops/inspiron-zino-hd/pd.aspx?refid=inspiron-zino-hd&s=dhs&cs=ukdhs1&ref=dthp](http://www1.euro.dell.com/uk/en/home/Desktops/inspiron-zino-hd/pd.aspx?refid=inspiron-zino-hd&s=dhs&cs=ukdhs1&ref=dthp)

My thinking behind this, is that the Zino has 2 eSata ports on the back - something that the rest of these low power nettops dont seem to provide.

The Zino, running Ubuntu Server and connected to the Rosewill RSV-S8 through the 2 eSata ports is a configuration im considering.

I'd really appreciate any comments though - especially if any of you can see flaws in my plan, or if the Zino is not a good machine to use.  Im happy to build a machine instead of going for an 'off the shelf' product, but im not sure how powerful i need it to be.

Other than a torrent downloader, the server will stream 1080p movie rips (around 8gb each) to a couple of XBMC media server built from Intel Atom hardware.

The Qnaps do this no problem with 500mhz processors and 256mb ram - but they dedicated boxes doing nothing else.  Please see their specs here: [http://www.qnap.com/pro_detail_feature.asp?p_id=93](http://www.qnap.com/pro_detail_feature.asp?p_id=93)

If i create a more expandable server ill need to make sure i dont sacrifice useable power.

---

