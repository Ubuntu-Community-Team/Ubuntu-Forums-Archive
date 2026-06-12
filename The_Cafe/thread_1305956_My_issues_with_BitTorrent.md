---
title: "My issues with BitTorrent"
date: 2009-10-30
forum: The Cafe
---

### Post by PacSci on 2009-10-30
As soon as I got home yesterday (around five EST), I fired up Transmission and began torrenting the Ubuntu and Xubuntu Desktop ISOs. It looked pretty good, I was getting 800kbps and it said the downloads would be complete in approximately an hour. I come back in 30 minutes, and the rate's gone down to 250kbps. I'm thinking, "What?" Later, my rate has gone down to the range of 60kbps to 120kbps. At that time, I had to leave for somewhere, so I left the torrents running. I come home, and they are only about 70% done and still at ridiculously low speeds. No one else was using the Internet for anything big this whole time. I paused both torrents and left, and began the process of system-upgrading my laptop. All 800kbps were back for pretty much the duration of the upgrade. I turn the torrents back on, and the connection slows again shortly - not just for that computer, but for every computer in the house.

My point is that my ISP (Time Warner Cable of "we're going to try out charging per gigabyte" fame - I live in one of the areas they were going to try it in) is most likely checking for BitTorrent tracker traffic, and when found it squeezes the life out of the connection. I've already downloaded the CDs and seeded a complete copy of each, but I don't think I want to use BitTorrent anymore to avoid my connection adopting the properties of a snail. Does anyone have similar experience? And can anyone recommend the second fastest way to download the Ubuntu ISOs?

---

### Post by t0p on 2009-10-30
There are a couple of approaches you could adopt.  You can do a direct download from one of the many Ubuntu servers and mirrors dotted around the globe.  Or you can change ISP to one that doesn't throttle bittorrent connections.

---

### Post by kripkenstein on 2009-10-30
Many Bittorrent clients support protocol encryption, which 'hides' the protocol, so ISPs can't easily throttle it. No idea about Transmission, but for example Deluge does.

Encryption isn't guaranteed to help, but it does in some cases.

---

### Post by Paqman on 2009-10-30
> **kripkenstein said:**
> No idea about Transmission

Yep, encryption is supported.

---

### Post by lovinglinux on 2009-10-30
I suspect your network was clogged due to excessive uploading traffic, since your speed came back to normal after shutting down the BitTorret client.

Try to set your UPload limit on your BitTorrent client to 80% of your actual UPload bandwidth limit. For more info and troubleshooting suggestions see [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by xpod on 2009-10-30
@ OP
> Does anyone have similar experience? And can anyone recommend the second fastest way to download the Ubuntu ISOs?


You could try installing a multi-threaded HTTP download manager, such as the Down-Them-All Firefox extension.
I`m quite lucky as my ISP hosts it`s own [mirrors](http://mirrors.virginmedia.com/)  that i can download ISO`s from but if you hunt around you can usually find somewhere that gives you decent download speeds. 

You could also just set up your torrents to run through the night, while you sleep.That way your not bogging down the rest of your connection.

---

### Post by madhi19 on 2009-10-30
First tip is to limit your upload for the download part than you turn up your upload speed after you downloaded the file. And don't forget to seed! You get good speed initially because I never get more than 400kbps so your upload is probably messing thing up. 

The other trick is that when a torrent goes dead just pause it for 15 minutes. That force the client to rescan the seed list and maybe find new active seeder.

---

