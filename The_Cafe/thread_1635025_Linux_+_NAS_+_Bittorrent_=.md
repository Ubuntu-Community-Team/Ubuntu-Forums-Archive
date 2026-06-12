---
title: "Linux + NAS + Bittorrent = ???"
date: 2010-12-01
forum: The Cafe
---

### Post by cartisdm on 2010-12-01
Any of you guys use a NAS drive with a mix of Linux, Apple, and Windows OSs on the same network?  I'd really like to transfer all my media to a central location and keep it on the Iomega 34337 NAS drive but I switch regularly between all operating systems.

I know that particular model of Iomega doesn't have native Bittorrent support, is this something that be added on?  I'd also like to be able to access the drive remotely via FTP or something but lets not get ahead of outselves just yet...

(PS I will need to keep the drive in a format that my xbox 360 can read because that's what's playing most of the media)

---

### Post by handy on 2010-12-01
I use a Netgear ReadyNAS Duo, which can do all & more than you are talking about. It runs a cut down version of Debian via a Sun CPU, can take a GB of additional RAM, uses next to no electricity when it is idling (90% of the day at least) is quiet, cool & has a great browser based client GUI interface.

Transmission is an add-on someone made for it, which craps all over the Bittorent one that comes pre-installed.

Wonderful hardware/system combo' so much easier (& cheaper to run) than FreeNAS, for my needs anyway.

The ReadyNAS forum is excellent, providing answers to any questions very quickly.

---

### Post by cartisdm on 2010-12-01
> **handy said:**
> I use a Netgear ReadyNAS Duo, which can do all & more than you are talking about. It runs a cut down version of Debian via a Sun CPU, can take a GB of additional RAM, uses next to no electricity when it is idling (90% of the day at least) is quiet, cool & has a great browser based client GUI interface.

Transmission is an add-on someone made for it, which craps all over the Bittorent one that comes pre-installed.

Wonderful hardware/system combo' so much easier (& cheaper to run) than FreeNAS, for my needs anyway.

The ReadyNAS forum is excellent, providing answers to any questions very quickly.

Hmmm...that sounds pretty interesting.  I'm just dipping my toes into the NAS world.  Do you install ReadyNAS on any NAS Hard Drive?  How much was your Netgear hard drive?

The reason I was drawn to the Iomega 1Tb was the $90 price tag which is very appealing.  I need about 1Tb of space and thin pockets because the wifey won't like my dropping a ton of money on something she won't understand... :D

---

### Post by endotherm on 2010-12-01
you could use a torrent engine with a web frontend, like Transmissions web interface, or Torrentflux. then configure teh service to save to a samba share, mapped to a location on the nas. that way everyone in the house can queue up a torrent from their webbrowser, and when teh torrent is done, the file is on your NAS waiting to be used.

---

### Post by cartisdm on 2010-12-01
> **endotherm said:**
> you could use a torrent engine with a web frontend, like Transmissions web interface, or Torrentflux. then configure teh service to save to a samba share, mapped to a location on the nas. that way everyone in the house can queue up a torrent from their webbrowser, and when teh torrent is done, the file is on your NAS waiting to be used.

I did consider doing that, but the idea of running Transmission on my laptop, then having the data save to a mapped drive using 802.11g; I was thinking it might slow down the process.  Is that true?

I just figured having the bittorent software run right from the drive I could save trouble (I don't know if that's the case though)

---

### Post by endotherm on 2010-12-01
> **cartisdm said:**
> I did consider doing that, but the idea of running Transmission on my laptop, then having the data save to a mapped drive using 802.11g; I was thinking it might slow down the process.  Is that true?

I just figured having the bittorent software run right from the drive I could save trouble (I don't know if that's the case though)
your right, if you are using wireless to connect to the NAS, then you don;t want to be moving the data around too much, thought it would still work fine, since even wireless G (54 Mbps) is still much faster than most peoples Internet connection.  I have gigabit line between my server and NAS, so I usually don;t have to worry about badndwidth too much.


so your next worry is finding a nas with BT support, and a client that will work with FF on linux?

---

### Post by cartisdm on 2010-12-01
> **endotherm said:**
> your right, if you are using wireless to connect to the NAS, then you don;t want to be moving the data around too much, thought it would still work fine, since even wireless G (54 Mbps) is still much faster than most peoples Internet connection.  I have gigabit line between my server and NAS, so I usually don;t have to worry about badndwidth too much.


so your next worry is finding a nas with BT support, and a client that will work with FF on linux?

Ok, thanks for confirming that.

Yup, I need to find a NAS drive with about 1tb of storage that has BT support.  I'm not sure if I can buy any ol' NAS drive and add on my own software or if it's a hardware thing...

When you say FF, you meaning FireFox? Why does that matter? (I'd like to be able to access the NAS storage and BT Client from any computer with any OS)

---

### Post by endotherm on 2010-12-01
> **cartisdm said:**
> Ok, thanks for confirming that.

Yup, I need to find a NAS drive with about 1tb of storage that has BT support.  I'm not sure if I can buy any ol' NAS drive and add on my own software or if it's a hardware thing...

When you say FF, you meaning FireFox? Why does that matter? (I'd like to be able to access the NAS storage and BT Client from any computer with any OS)
your Os agnosticism is exactly why I suggest FF. it can be installed everywhere. I could use my internal webservices via just a straight browser without any additional plugins or whatnot, but there are several firefox plugins that really really simplify the process.

---

### Post by cartisdm on 2010-12-01
> **endotherm said:**
> your Os agnosticism is exactly why I suggest FF. it can be installed everywhere. I could use my internal webservices via just a straight browser without any additional plugins or whatnot, but there are several firefox plugins that really really simplify the process.

Cool, using FF makes sense.  Do I need to find a special NAS drive or can I install software on it that will allow BT and the other things I'm looking for?

Basically, can I do all this with the Iomega 34337 (it's the cheapest NAS drive I've found) or do I need to keep looking?

---

### Post by endotherm on 2010-12-01
a nas is basically just an OS, but it;s a proprietary one (or so you must assume). as such, it's a much more closed ecosystem than your average PC. i woudl assume that if your product does not come with these services, that you probably can't install them manually  (at least without a fight).

my NAS ([Synology DS209i]("http://www.synology.com/enu/products/DS209/index.php")) runs linux, so I have tweaked it extensively, but I've never tried to install anything other than what synology has released for it.

---

### Post by Paqman on 2010-12-01
I use a QNAP NAS. I've got one of the two-bay RAID models, but you could get one of the smaller ones if you're on a budget. They run Linux on an ARM chip. They all have a torrent client (based on rTorrent, IIRC) and will do Windows and Apple file sharing. Some of them up the range do NFS, too. I'm very happy with mine, it's packed with features and very efficient. They come with full ssh and telnet access too, so they're not locked down.

---

### Post by NCLI on 2010-12-01
> **cartisdm said:**
> Any of you guys use a NAS drive with a mix of Linux, Apple, and Windows OSs on the same network?  I'd really like to transfer all my media to a central location and keep it on the Iomega 34337 NAS drive but I switch regularly between all operating systems.

I know that particular model of Iomega doesn't have native Bittorrent support, is this something that be added on?  I'd also like to be able to access the drive remotely via FTP or something but lets not get ahead of outselves just yet...

(PS I will need to keep the drive in a format that my xbox 360 can read because that's what's playing most of the media)
I've been running something just like this for the past year, and setup a similar server for a friend, with great success. Just get a mini-ITX motherboard with a built-in Atom CPU, a big case, one small HDD(Possibly from an old computer, it's just for the OS), and three big HDDs(For the RAID5 containing your media files). Install Ubuntu Server 10.04, setup the HDDs in RAID5 using mdadm, and finally install the package "deluged".

"deluged" is the backend of torrent application Deluge. Just install Deluge on your other computers(It is compatible with Windows, OSX, and Linux), and connect it to the server. It can connect via te internet, and via your local LAN.

Then, to access the server, setup both SSH(For Linux and OSX boxes) and Samba(For Windows boxes).

I'd be glad to help you with the details of setting it up, since I have a lot of experience with how to best do it at this point :P

---

### Post by cartisdm on 2010-12-01
> **NCLI said:**
> I've been running something just like this for the past year, and setup a similar server for a friend, with great success. Just get a mini-ITX motherboard with a built-in Atom CPU, a big case, one small HDD(Possibly from an old computer, it's just for the OS), and three big HDDs(For the RAID5 containing your media files). Install Ubuntu Server 10.04, setup the HDDs in RAID5 using mdadm, and finally install the package "deluged".

"deluged" is the backend of torrent application Deluge. Just install Deluge on your other computers(It is compatible with Windows, OSX, and Linux), and connect it to the server. It can connect via te internet, and via your local LAN.

Then, to access the server, setup both SSH(For Linux and OSX boxes) and Samba(For Windows boxes).

I'd be glad to help you with the details of setting it up, since I have a lot of experience with how to best do it at this point :P

Hey thanks for the suggestion!  Unfortunately, I am trying to avoid going down the "server" road due to lack of space.  Currently I have a one bedroom apartment in the city so space is very limited.  That's how I came across these NAS drives. Their all inclusive package is a real turn on for the price! It just seems hard to come by one that is less than $120 and Bit Torrent capable...


EDIT:  Looks like I found one a contender! The [Buffalo Technology LinkStation]("http://www.amazon.com/Buffalo-Technology-LinkStation-Attached-LS-CH1-0TL/dp/B001FFP4PK") has included BitTorrent software, a web browsing interface, and the ability to access anywhere as a FTP...and all for $109 (B&H Video)!

---

### Post by handy on 2010-12-02
**@cartisdm:** You'll have to do a search & see what the price of the Netgear ReadyNAS Duo, currently is in your part of the world.

I bought mine without drives as I already had a 1.5TB WD Green. Apart from that it is cheaper to supply your own drives anyway. Have a search, you will find all of the details available on the net for these little hardware wonders.

If you do get one, contact me as there is a trick or two that I can help you out with as far as getting the most out of the things.

---

