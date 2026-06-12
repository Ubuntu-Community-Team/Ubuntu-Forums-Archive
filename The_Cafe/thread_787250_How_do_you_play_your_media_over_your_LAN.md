---
title: "How do you play your media over your LAN?"
date: 2008-05-08
forum: The Cafe
---

### Post by Misterbadexample on 2008-05-08
I have a couple of Macs, a couple of PCs and a couple of Linux boxes, and hopefully one day, they'll be LANed together and playing nicely. I have an OSX/Ubuntu/Mythbuntu Mac Mini that hooks up to the DVI of my TV pretty nicely and I've used it to play media off of external hard drives and the web since I got it. But that's not exactly the perfect solution. That and Mythbuntu just sort of doesn't sit well with me.

I'd like to have a centralized media server I can hook up a couple of TB to and share or stream media over the LAN. I'd also like to view the files in as easy a manner as posible--not having to sit in front of the television as if it was a computer and mount shared disks, then navigate through files with a mouse and keyboard.

I guess, saying that, what sort of setup do you guys use for sharing media over your home networks? Anyone do this sort of thing? What operating system do you run on the various machines, including what is hooked up to the TV and the media server?

Not really looking for a "solution," but I would enjoy reading about how other people get it done.

---

### Post by elustran on 2008-05-08
Not sure what to do with macs, but I have a linbox as a media PC and some media on my winbox.  I just have my shared windows folders fstabbed and linked to so they're already there on my desktop.  All my media is just a few clicks away.  If you want to make things easy, just kill compiz so you don't have resources fighting for gl.  Also, get a decent wireless keyboard.

---

### Post by hellmet on 2008-05-08
I'm sure this is not the perfect solution, but I use VLC to stream videos over my LAN.
And to share files, I always use sftp:// (SSH).

---

### Post by Misterbadexample on 2008-05-08
@elustran: Have a pretty descent mouse/keyboard set from Kensington. Doesn't chew up batteries, which is nice. But I'd like to really free myself from having to use the keyboard and navigate entirely with a remote. At least, that's part of my goal. Thought a media center like Mythbuntu would work out for me, but I've had no success with it as of yet. Mostly because it sort of overwhelms me.

@hellmet: I've read about using VLC for streaming. It might be a good solution after all. I'll read up on it and see if I can get it to work.

What I can gather is that there's not really trouble sharing Windows folders drives in Linux. Macs can share windows folders, too. I'd rather set up a Linux box for media storage, but it might not be in my best interest, if it's a serious pain to get OS X and Windows to share.

Does anybody do this--can anyone recommend a specific distro, maybe?

---

### Post by frego on 2008-05-09
I have a Fedora Core 4 set up with many harddrives that are LVM'd so they appear as one big 1.7TB drive.  On that drive are many videos and mp3s.  It is being shared with samba which I've setup to also do appletalk so any Mac that is on my LAN can see the share as can any windows machine.  I use NFS to share files to other linux boxes.  I'm using Myth on a couple of machines, which I mount the nfs share and then change the couple of shortcuts so mythvideo finds the files.  Then the myth boxes can seemlessly navigate through the videos without using a keyboard or mouse, I just use a MCE 2 remote.  I could have done all the file sharing off of the myth box of course, but due to historical reasons, that just so happens to be served up on a redhat box.  I just switched my Mythtv backend from Knoppmyth to Mythbuntu.

---

### Post by madjr on 2008-05-09
> **Misterbadexample said:**
> I have a couple of Macs, a couple of PCs and a couple of Linux boxes

i think you mean "Winboxes"

Personal computer (pc) =! windows

my normal "PC" has only linux on it.

my linux box is a small mini-itx media center in my living room.

i think u seen too many apple commercials :confused:

:lolflag:

---

### Post by Misterbadexample on 2008-05-09
@frego: Your setup sounds pretty sweet and gives me some good starting points. I appreciate it. I've toyed around with Mythbuntu on my Intel Mac, but I've not really come to understand how to set it up properly. I'll have to look into some tutorials/FAQS on the internets somewhere. Any reasons/advantages for using Fedora Core for storing your files over other Distros?

@madjr: There's no need to act like that. I know what PC means. But, yes, what I typed before was a little askew. I'm used to talking to normal humans that don't really even know what an "operating system" is. And apparently that =! you.

---

### Post by uknowho008 on 2008-05-09
i use modded xboxs running xbmc to access all my media from an ubuntu server.

---

### Post by herbster on 2008-05-09
I just have a server running mythbackend, mounted as NFS and I watch all the stuff on my desktop as a frontend using a MCE remote. Piece o' cake.

---

### Post by madjr on 2008-05-09
> **Misterbadexample said:**
> But, yes, what I typed before was a little askew. I'm used to talking to normal humans that don't really even know what an "operating system" is. And apparently that =! you.

yea in ubuntuforums i think everyone knows what an OS is :D

but am just messing, those apple r pretty funny

i think that once linux starts gaining more marketshare they may start calling it "linux box" in the next apple commercials :lolflag:

---

### Post by teet on 2008-05-09
I'm pretty sure you could do everything you wanted with MythTV.  It used to be a bear to set up, but it's pretty easy now that mythbuntu is around.  Of course, I've been messing with it for a couple of years now...

All you need to do is install mythbuntu (or just the control center if you already have ubuntu).  Then install the mythmusic and mythvideo plugins.  Share the folders with your vids/music on your remote machine and then mount those folders on your local machine (you'll prolly have to edit /etc/fstab ... there are lots of tutorials --> ubuntuguide.org).  Then change teh settings of the mythvideo/mythmusic plugins to look in the proper folders for content and BOOM!  you're done.

-teet

---

### Post by intense.ego on 2008-05-09
I just use an xbox 360 for video. I either transfer the files to a USB drive and play off there, or I stream over wifi from one of the windows pcs in my house.

If I want to play music, either I connect speakers to the computer and play directly, or I use my iPod dock/speakers.

Old school and not to technologically fancy, but does the job without any hassle.

---

### Post by Misterbadexample on 2008-05-10
@madjr: S'alright. I doubt apple will ever mention Linux much. It's hard to compete with the price you can get Linux for ($0 and 1 CD-R). That and the Linux developers know/care about what they're doing, so it's not as easy to trash as Windows is in the commercials.

@uknowho008: That is a thought. As soon as my Pro Action Replay gets delivered, I'm going to softmod my Xbox. I was going to try Slayers Evox or UnleashX, but I may give XMBC shot. I don't plan to change out the HDD, so ripping games to the disk may not be the most necessary of features.

@herbster: Have to get me a remote like that. It will probably make my life easier. The apple IR refuses to work in Ubuntu or MythTV for me. As far as I know it is not supported. BTW, nice avatar. Queen is awesome.

@teet: Nice post. That does sound easy. I've not messed around with Mythbuntu since I installed it, and I guess the idea of reading a bunch of tutorials after installing a triple-boot didn't appeal to my laziness. I appreciate the link to that wiki. I may be on my way to setting up the network I want.

@intense.ego: Doesn't sound bad, especially the streaming over Wifi--didn't know the 360 was capable of that. But it's not for me. The DIY nature of setting up this system is part of what appeals to me. When I'm finished setting up my network I'll probably build a log cabin to put it in so I can feel like a real MAN.

Here's what I'm starting to imagine: Ubuntu system running 1TB+ of HDD space, sharing to Windows/Macs with Samba, NFS for Linux machines. Edit fstab to have Mythbuntu mount disk over network, and get a good USB(?) MCE remote that will run in Ubuntu and Mythbuntu. And XBMC for good measure on my trusty Xbox.

Hope I can pull all that off. This will end up being a big project for me.

Anybody else have an impressive setup for their LAN media?

---

### Post by frego on 2008-05-10
Misterbadexample>  The only reason I setup that one server with FC4 was because it handled LVM really easy back then.  I'm sure Ubuntu can do the same thing, I've seen some tutorials on how to do LVM with mythbuntu.  But with drives being so big now and so many motherboards having RAID, LVM might not be needed.  Plus you can run into a world of hurt when a drive fails in an LVM.  I had one fail once and the only reason I recovered anything off the other drives was because one of the developers of LVM was kind enough to walk me step by step through everything on IRC.  Otherwise the one drive crashing would've lost me everything!

As far as your remote, here's the MCE USB remote I'm using and it works with Mythbuntu without having to recompile LIRC (which is what I had to do when I was using Knoppmyth on the same box):
[http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851](http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851)

---

### Post by teet on 2008-05-10
[http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=604651&prodlist=celebros](http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=604651&prodlist=celebros)

I just bought this remote a couple of months ago.  Awesome price.  Come with 2 IR blasters plus the USB receiver has a cord that is like 12' long.  Had it set up in mythbuntu with 3-4 clicks.

-teet

---

### Post by gn2 on 2008-05-10
I have all my music files on a USB drive connected to a Linksys NSLU2 Network Storage Adapter and play the files with Audacious on my laptops by simply drag and dropping the files into the playlist.

---

### Post by pelle.k on 2008-05-10
I have PIII 400 as a file server, and it also hooked up to the TV (only).
Currently i'm running arch linux with autologin from inittab, and run openbox + freevo from my profile. I'm thinking i'll try debian/ubuntu running oxine soon though. But i don't need anything TV related so freevo/oxine will be fine for me.
Most buttons on my USB IR remote are already mapped as X keycodes, so what input events are left i mapped with xmodmap.
I also run this as a samba server + rtorrent (with "watched" directories, so i just drop torrent in there and let rtorrent do it's business). The samba share has full RWX rights (only my desktop computer IP allowed) so i do all file managing directly on the share.

If you have a separate file server, you need to mount the share properly (to the file system) if you want to play music etc from an application that isn't KIO or GnomeVFS(GVFS) aware (kaffeine/totem is, xmms etc isnt)

It took a bit of work, by everything is seamless and automated now, so i'm a happy camper :)

---

### Post by UbuWu on 2008-05-10
A NAS-drive or a pc running mediatomb as the server connecting to a hardware media player connected to the tv such as the netgear eva 8000.

---

### Post by uknowho008 on 2008-05-11
xbmc is definitely the way to go if youre using it for media. it will play virtually anything you through at it. neither evo x or unleash x play media to my knowledge. and use the latest ndure mod. i think thats still the way to go.

---

