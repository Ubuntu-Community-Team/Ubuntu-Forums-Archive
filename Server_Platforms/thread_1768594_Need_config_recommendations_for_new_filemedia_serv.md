---
title: "Need config recommendations for new file/media server"
date: 2011-05-27
forum: Server Platforms
---

### Post by Ron Jones on 2011-05-27
I'm building a new file/media server for my household to use, and would like to hear the experiences of others, and suggestions, or links to appropriate howto's.

I'll be using two (2) [250 GB Western Digital RE4]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136797") drives mirrored via mdadm RAID 1 for the Operating System. The storage area will be handled by four (4) [500 GB Western Digital RE4]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136697") drives in a RAID 5 array, managed by an Areca 1210 controller.

What I'd like to configure is a basic Samba file server, on which we have individual user folders, and a shared drive. As well, I'd like to add the ability to manage our movie collection so it can be accessed by the [Boxee Box]("http://www.boxee.tv/") attached to the television.

[Twonky]("http://www.twonky.com/") looks promising (and I don't mind paying the $19.95 for something that works well). However, as this is new to me, there may be other solutions out there that are better, and easier to administer.

Moving forward, I'd like to explore the feasibility of configuring LDAP on this machine to authenticate users on the network (perhaps even integrate the mail server somehow), and the remote users (only two) who VPN into the network using the [pfSense]("http://www.pfsense.org/") firewall appliance. There are no Windows servers, so Active Directory is not a factor.

If anyone has been through this, or something similar, I would certainly appreciate your insight and suggestions. If you are aware of any existing howtos out there, I would be grateful for that as well.

Thanks,

---

### Post by Lars Noodén on 2011-05-27
From what I gather, RAID 10 is faster than RAID 5.  I'm not sure which has the greater storage capacity, but if you are streaming media, then speed is an issue.

---

### Post by Ron Jones on 2011-05-27
Yes, I have heard RAID 10 is faster than RAID 5 for writes in a small array like mine. But the read speed is comparable... and it's not worth the cost of the extra discs.

I have been doing some searching, and found several good sources of information and tutorials on setting up an Ubuntu home server 

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760) is an extensive tutorial on setting up an OpenLDAP + Domain Controller on Ubuntu (a bit too "corporate" for my needs).

[http://www.linuxhomeserverguide.com](http://www.linuxhomeserverguide.com) is a whole website devoted to setting up a media hub, torrent box, file server, web server. We don't typically use torrents, nor do we store mp3's, just movies. And, I have separate servers to handle email, web, and phone.

Ultimately, all I'm looking to set up is a media server that holds our movies (not music); a file server that provides user folders, and a shared drive; and... possibly (if it's not hopelessly complex) an LDAP authentication server.

Perhaps what I'm looking for can be found in a blend of the information found within these links. However, I am still hopeful that someone else has scratched this same itch before, and shared their experiences.

regards,

---

### Post by arrrghhh on 2011-05-27
Well I can try to provide help with the media server side of things - but instead of Boxee Box, I use a PS3 as my media hub.

I found an app called "PS3MediaServer" - it works better than any other UPnP media streamer I could find.  It was originally designed with PS3's in mind, but I've heard that it works great with anything that is DLNA compliant.

I've never used Boxee, is there no way to connect it to network storage...?  Is DLNA your only option?

---

### Post by Ron Jones on 2011-05-27
> **arrrghhh said:**
> Well I can try to provide help with the media server side of things - but instead of Boxee Box, I use a PS3 as my media hub.

I found an app called "PS3MediaServer" - it works better than any other UPnP media streamer I could find.  It was originally designed with PS3's in mind, but I've heard that it works great with anything that is DLNA compliant.

I've never used Boxee, is there no way to connect it to network storage...?  Is DLNA your only option?

What Boxee does is sit between your TV and the media source. It scans and presents the media available on your network (plus hundreds of internet sources) via its menu.

I don't know enough about the DLNA and the UPnP standard to be conversant, but from the brief googling I did on it just a few moments ago (before which I'd never heard of it lol). BUT... Originally, it only connected to your files via Samba (and, perhaps NFS). But recently, UPnP capability was added as well... apparently all one has to do is go to "Add UPnP device as a source" in the boxee menu, and it automagically sees your files.

I have not yet purchased the Boxee box, but of the devices on the market (Boxee, Roku, etc) that is the one towards which I'm leaning.

What does the PS3 do as a media hub. Never having been a gamer (outside the occasional game of Pac Man as a youngster, when I could wrangle a quarter out of Mom & Dad), I know very little about it (other than the fact that my nephew thinks it's the greatest piece of electronic equipment in existence.

---

### Post by arrrghhh on 2011-05-27
> **Ron Jones said:**
> I have not yet purchased the Boxee box, but of the devices on the market (Boxee, Roku, etc) that is the one towards which I'm leaning.

What does the PS3 do as a media hub. Never having been a gamer (outside the occasional game of Pac Man as a youngster, when I could wrangle a quarter out of Mom & Dad), I know very little about it (other than the fact that my nephew thinks it's the greatest piece of electronic equipment in existence.

Yea, I'm aware how Boxee works on a basic level, I thought you could just point it to a network share - I think that would be the easiest solution, use samba or NFS to just share your files to the device.  Much easier than dealing with DLNA streamers, assuming the device can handle many formats...

At any rate, the PS3 is a DLNA-compliant device.  So I use PS3MediaServer to stream movies, music, TV shows, whatever really from my Ubuntu server to my PS3.

The main reason for this was surround sound.  I used to just have a PC hooked up and would watch movies etc thru it... but I kept wrestling with surround sound, and it was always a PITA.  Now with the PS3, there's no messing - if the file has some sort of surround sound track, the PS3 picks it up and it 'just works'.  That was honestly the main reason I use the PS3 as a media hub... I originally got it for the games, but honestly I watch media on it 99% of the time, haha.

---

