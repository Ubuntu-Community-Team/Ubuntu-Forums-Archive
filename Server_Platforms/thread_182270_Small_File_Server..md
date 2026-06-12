---
title: "Small File Server."
date: 2006-05-25
forum: Server Platforms
---

### Post by OkydOky on 2006-05-25
Hello,
I am somewhat a newb when it comes to linux, and even a bigger one when it comes to servers.

Anyways, The reason I am doing this is:
1. It'll be a gret learning Experiance.
2. Fun
3. Need Storage space -- I could probably easilly do this in windows, but yea, as stated above, I want to increse my knowledge of linux.

Basically what I want this machine to do is:
1. Store Files - Mosly large Video Filess for Viewing on other Machines.
2. Download and Seed some Torrents.
3. Act as a Small FTP server for my Private Use.
4. Accessing it remotelly. (This is the least Important one)


My question is.. hwo easilly would this be done?
My Other main question is, How good is the RAID 5 support for the Intel ICH7R southbridge in linux? -- This is probably one of my main conserns.. actually.

---

### Post by Socratez on 2006-05-25
[QUOTE=OkydOky]Hello,
I am somewhat a newb when it comes to linux, and even a bigger one when it comes to servers.

Anyways, The reason I am doing this is:
1. It'll be a gret learning Experiance.
2. Fun
3. Need Storage space -- I could probably easilly do this in windows, but yea, as stated above, I want to increse my knowledge of linux.

Basically what I want this machine to do is:
1. Store Files - Mosly large Video Filess for Viewing on other Machines.
2. Download and Seed some Torrents.
3. Act as a Small FTP server for my Private Use.
4. Accessing it remotelly. (This is the least Important one)


My question is.. hwo easilly would this be done?
My Other main question is, How good is the RAID 5 support for the Intel ICH7R southbridge in linux? -- This is probably one of my main conserns.. actually.[/QUOTE]


Shouldn't be too hard to set this up. If you have mainly Windows/MS based clients you can get it donw using Samba. Windows file sharing is not that big of a deal when it comes down to it. Check out the Wiki for Samba information and you should be able to get it up in less then 20 minuts. The ftp and torrents can be managed on here to. I use TorrentFlux on my server. I know it means setting up a webserver but that is as easy as sudo apt-get apache2 and then the mods + libs you want to include. Many tutorials on that can be had on the TorrentFlux site. vsftp or proftpd are the best bet for the ftp access ... proftpd is easy as pie to setup and it even has a GUI front end in Gnome .. serach synaptic and you'll find it. Last but not least is the RAID .. I have only used 4 different RAID host controllers in linux but all worked well. I would check out the HCL and see if your card is supported but I can't see such a popular chipset not being functional ... 

Sorry I don't have specifics but hopefully ths helps ...

---

### Post by OkydOky on 2006-05-26
One other thing...
I'm guessing this is possible... But wondering if anything real complicated needs to be done for this..

I'll have Two Network Cards.
One Connected to a Cable Modem, with all the torrent Uploading/Downloading going on.
A second.. connected to a Router which connects the Other comps.
That Router is Connected to a Second Cable Modem, connected to a 2nd Cable line.
That one is for all the other comps.

Basically I want THAT server to connect to One NIC for Internet amd a 2nd NIC for the Filesharing..

---

