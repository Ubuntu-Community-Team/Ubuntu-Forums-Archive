---
title: "Torrent FAQs"
date: 2011-06-30
forum: The Cafe
---

### Post by linuxyogi on 2011-06-30
Hi, 

I prefer downloading files using torrent whenever possible because 

a) I get better speeds
b) Pause/Resume feature
c) I have never got a corrupt download using torrent

I have no open ports on my Router. I haven't opened any ports on the OS 

(Ubuntu) side too. Despite having all ports closed I can download/upload 

without any issues. Therefore what I want to know is why do people open 

ports for torrents ? What's the reason ?

---

### Post by haqking on 2011-06-30
> **linuxyogi said:**
> Hi, 

[SIZE=1]I prefer downloading files using torrent whenever possible because 

a) I get better speeds
b) Pause/Resume feature
c) I have never got a corrupt download using torrent[/SIZE]

[SIZE=2]I have no open ports on my Router. I haven't opened any ports on the OS 

(Ubuntu) side too. Despite having all ports closed I can download/upload 

without any issues. Therefore what I want to know is why do people open 

ports for torrents ? What's the reason ?[/SIZE]


Well it works without port forwarding, but Port forwarding is like a electronic policeman directing traffic and your torrent traffic is the queen coming through on her own without having to stop for other traffic.

It basically speeds up the data by opening a direct path to your machine and torrent client and every millisecond shaved increases your speed.

traffic will normally arrive and look at the ports until it finds an open one (imagine turning up to a house and going around checking all windows and doors until you find one open) with a dedicated port it is like your friend telling you the front door is open so come straight in.

---

### Post by babybean on 2011-06-30
Sometimes it does not "just work" for people. If it doesn't it could be a strict firewall or something like that in the router.

Not sure about this one but sometimes upnp is running in the background sorting all the ports out for you.

---

### Post by haqking on 2011-06-30
> **babybean said:**
> Sometimes it does not "just work" for people. If it doesn't it could be a strict firewall or something like that in the router.

Not sure about this one but sometimes upnp is running in the background sorting all the ports out for you.


thats very true,

But his question was why do people open ports and the reasoning behind it.

and yes you are right, Upnp is a feature which will open ports automatically however some routers have trouble with this and so it is sometimes better to disable Upnp support in your client.

for the most part dedicated port forwarding is preferable, but to be honest the main reason i see slow downloads for most people these days just comes down to lack of seeds (the person downloading doesnt understand seeding) or faulty or misconfigured telecoms equipment such as extension cabling and the like

---

### Post by linuxyogi on 2011-06-30
> **haqking said:**
> 
traffic will normally arrive and look at the ports until it finds an **open one** 

But as I have mentioned I haven't opened any ports. Then how is it data transfer happening at my end ? 


> **babybean said:**
> 
Not sure about this one but sometimes upnp is running in the background sorting all the ports out for you.

You mean upnp is opening ports without my consent ? :confused: 

I don't want that to happen.


Edit : Checked for open ports at grc.com while downloading a file. No ports are open.

---

### Post by haqking on 2011-06-30
> **linuxyogi said:**
> But as I have mentioned I haven't opened any ports. Then how is it data transfer happening at my end ? 




You mean upnp is opening ports without my consent ? :confused: 

I don't want that to happen.


Upnp is on the router and yes will choose a port.

If you dont want anyway in then dont use a torrent client and setup appropriate rules on your firewall.

and closed ports beleive it or not will not prevent an ingress for download or an egress for upload.

---

### Post by linuxyogi on 2011-06-30
> **haqking said:**
> Upnp is on the router and yes will choose a port.

If you dont want anyway in then dont use a torrent client and setup appropriate rules on your firewall.

and closed ports beleive it or not will not prevent an ingress for download or an egress for upload.

I want the upload/download process to go on as usual. Just want all ports to be closed just 

like they are now. No issues. 

My line speed is 512kbps. The max download speed that I get choosing any download method is 45-60 KiB/s. So I dont think that is going to improve even if I decide to open a port for my torrent client. 

Thanks to both.

---

### Post by haqking on 2011-06-30
> **linuxyogi said:**
> I want the upload/download process to go on as usual. Just want all ports to be closed just 

like they are now. No issues. 

My line speed is 512kbps. The max download speed that I get choosing any download method is 45-60 KiB/s. So I dont think that is going to improve even if I decide to open a port for my torrent client. 

Thanks to both.


well port forwarding would be used in this instance for programs that do not work well with NAT and torrent clients being one of them.

If your ports are closed and you get the torrents then dont worry about it ;-)

aside of course form the possible malicious content of torrent downloads ;-)

---

