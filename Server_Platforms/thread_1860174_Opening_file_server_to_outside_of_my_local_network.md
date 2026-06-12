---
title: "Opening file server to outside of my local network"
date: 2011-10-14
forum: Server Platforms
---

### Post by myusernameisnotvalid on 2011-10-14
Hello I have installed ubuntu 11.04 on my server. It's runing with a tiny problem which in this case is irrelevant. I have setup media server to work over LAN and I can stream whatever I want to tv, pc and other DLNA devices I have at home. Now I would like to open server to the internet. What I mean by that is, I want to be able to stream videos/audio/pictures outside of my home. I would love to be able to watch movies, tv-series I have recorded to my server with a laptop no matter where I am as long as I have internet connection. 

So can somebody explain me how to do what I want to do? I'm not so familiar with these kind of things so noobish quide would probably be good. I'm open to your ideas. I perfer fairly simple and safe solution. 

thank you for reading, I'll be waiting for suggestion

---

### Post by trundlenut on 2011-10-14
First you are going to need a good upload speed on your internet connection at home and 2, read up on security a lot before trying this then read more on security.

---

### Post by myusernameisnotvalid on 2011-10-15
> **trundlenut said:**
> First you are going to need a good upload speed on your internet connection at home and 2, read up on security a lot before trying this then read more on security.

I know that I need good up speed. That's matter of course. I just don't have much experience with ubuntu and though if somebody could post me a quide how to do it. Sure I can read and study myself, but since there are these kind of forums where I can ask from pros', I though I could save some time and trouble if somebody could quide me.

---

### Post by trundlenut on 2011-10-16
you need to find out about port forwarding on your router at home to be able to access the server externally.

---

### Post by rubylaser on 2011-10-16
Just setup OpenVPN or SSH port forwarding.  That way, you don't have a punch a bunch of holes in your firewall.  It will be more secure and easier to maintain.  You'll probably want to consider a streaming setup that will re-encode your content on the fly for you to minimize the bandwidth used.

---

### Post by myusernameisnotvalid on 2011-10-18
I did some research on the internet and though to set up openSSH, could somebody write me a simple set up quide for the program...? (or link to other thread which has a quide)

---

