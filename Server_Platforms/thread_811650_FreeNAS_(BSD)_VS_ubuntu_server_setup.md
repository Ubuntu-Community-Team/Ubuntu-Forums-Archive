---
title: "FreeNAS (BSD) VS ubuntu server setup"
date: 2008-05-29
forum: Server Platforms
---

### Post by L14UX_1NS1D3 on 2008-05-29
Dear Linux users,

Recently I got interested in setting up a NAS (network attached storage). I downloaded a small iso is called FreeNAS. FreeNAS is a distro based off of BSD and is a welcome alternative to commercial NAS setups. FreeNAS has a cool option to install to a external memory stick or other such media. With only a 20GB HD running as storage I went with the thumbdrive option. It took about ten minutes to install, the rest was configure the network service from the webgui. I have tried time and time again to get a server setup with other distros, but with FreeNAS I was finally able to get many services up and running without breaking a sweat. I only have a few qualms with this server setup. It would be much better if I had a second ethernet port on the server so I could get updates and download stuff etc while it was connected to other PCs. Secondly the transfer rate is painfully slow 10kb. this would be ok for up loading/download documents but let's say I wanted to upload a rip from my dvd collection so I could stream it to any computer in the house. I feel all empowered from my little foray into creating a server that I might try my hand at setting up a ubuntu server. Oh another thing I didn't so much care for was BSD default filesystem (UFS). I don't really trust an FS that I'm not familiar with. 

It would be great to get some feedback on this matter, especially if anyone knows of a way to increase upload/download rate. Thanks

---

### Post by tigerplug on 2008-05-29
I dont' know much about this but thankyou for the information on FreeNAS - Sounds interesting. Definately something that I am interested in and I will be looking at setting it up on my home network :)

---

### Post by NateMan on 2008-05-29
Are you sure your transfer rates are not 10MBs per a second? that's about normal for 100Mb ethernet. Maybe I'm not familiar with freeNAS, but should you be able to access the internet and get updates, while users are accessing data? I know this is possible on my server running ubuntu. Also are you using a very old network card or something of that kind? I really can't picture even an ancient card as being that slow since even 10Mb ethernet should still provide around a MB of transver.

---

### Post by L14UX_1NS1D3 on 2008-05-29
Let me just clarify. I only have one ethernet port on the server running freeNAS. With that free port running out of the NAS PC I hooked it up to my compy thats running a setup with two ethernet ports and a PCI wireless LAN. I know that the slow transfer rate is not due to outdated hardware. The server on which freenas is running is a P4 running at a speedy 2.2Hz. The The LAN on the client comp says specifically that it's a 100Mbps enabled card. I read on some websites that hardware on the PC that I'm using is also good for 10/100. I really have no idea what might cause this odd defect. In the meantime I'll just have to play around with my setup. I also have other computers that I could hook up to the server to test it. Another thing that I might do is try install ubuntu server 8.04 on the PC dedicated as the server and see if anything changes. I'm guessing I just made a stupid mistake somewhere. Ohh well...   :confused:

---

### Post by NateMan on 2008-05-29
I doubt it was a mistake on your part, I don't see how that could have been caused by what you did. Perhaps a bug in freeNAS or a defective cable is causing the issue.

So your not going through a switch or a router, just a direct setup? I wonder if that has something to do with your slow speeds.

---

### Post by NateMan on 2008-05-29
By the way, UFS is the Unix File System, and it has been around longer than any other file system I can think of. Its quite mature and safe.

---

### Post by netztier on 2008-05-30
> **L14UX_1NS1D3 said:**
> Let me just clarify. I only have one ethernet port on the server running freeNAS. With that free port running out of the NAS PC I hooked it up to my compy thats running a setup with two ethernet ports and a PCI wireless LAN. 

Sounds a weird setup to me, might be asymmetric traffic flows going on here, hence the poor performance. 

In general, you should run a current-day ethernet as a star or tree (resp. cascaded star) topology with a LAN switch (might be integrated in your broadband router) or Hub in the center of the star. 

To avoid a lot of hassle and untroubleshootability, all computers connected should only have one active (logical) NIC at any time (use bonding to form a single logical NIC out of two physical NICs).

Except for devices that do routing tasks of course, these need an "internal" interface to your LAN and an "external" one towards your upstream network (which might be your ISP), very probably your broadband router already does this job.

Can you give a scheme of how your network is wired up and what connects to where, including information about IP addresses, subnet masks and gateway settings for each device/NIC?

regards

Marc

---

### Post by L14UX_1NS1D3 on 2008-05-31
I tried using using a different cable and I also got a 4 port network switch (NETGEAR DS104). I plugged in the cable and the hub showed that the cables were both running at 100M not 10. Everything still work just the same. when I went copy files over via samba sharing, I STILL had the same problem! I'm still in the dark here. :confused:

---

### Post by L14UX_1NS1D3 on 2008-06-15
FIXED!! :) I after some tinkering I finaly got it to work! I have to ethernet port on my main comp. the onboard ethernet port is called eth0 and I installed a pci ethernet card on my pc. that pci ethernet port was named eth1. I set both of the port to a static IP but when I was trying to get it to work I had ther server connected to to pci ethernet port. I was stumped as to what the problem might be. so I switched the connection from the pci to the onboard. When I tried again to copy files via FTP and smb it worked! I was able to get a 10mb and up transfer rate. Now I have a dedicated ftp, nfs, smb, and Upnp server. My plan is to install a wireless router with WEP and set it up for remote access so I can get to my files from almost any computer! I am also going to be getting a N800 internet tablet so I can mess around with the upnp setup. I highly recommend for anyone setting up quick and easy server at home to try FreeNAS!! :popcorn: ):P \\:D/ =D> :biggrin:

---

### Post by windependence on 2008-06-16
Just remember upnp is very insecure. I wouldn't be running it unless my server was isolated from the rest of the network.

[http://www.grc.com/UnPnP/UnPnP.htm](http://www.grc.com/UnPnP/UnPnP.htm)

-Tim

---

### Post by hyper_ch on 2008-06-16
> **windependence said:**
> Just remember upnp is very insecure.

Why is it very insecure?

---

### Post by windependence on 2008-06-16
> **hyper_ch said:**
> Why is it very insecure?

Do a google search for UPnP vulnerabilities. You'll see that there is a history of serious security vulnerabilities going all the way back to 2001. Each time Micro$oft has released a patch and each time shortly after yet another vulnerablilty has been found and the cycle repeats itself.

Judging from your sig, I'm thinking you may also want to read up on this one. It is generally recommended if you are going to use this service that you don't leave it on after you are finished.

-Tim

---

### Post by hyper_ch on 2008-06-16
> **windependence said:**
> Do a google search for UPnP vulnerabilities. You'll see that there is a history of serious security vulnerabilities going all the way back to 2001. Each time Micro$oft has released a patch and each time shortly after yet another vulnerablilty has been found and the cycle repeats itself.

And how would that affect linux?

---

### Post by windependence on 2008-06-16
It doesn't. I am just making the OP aware of this since he mentioned he has a Upnp server on the network. :)

-Tim

---

### Post by hyper_ch on 2008-06-16
you mean you're making the op aware that upnp is a bad thing for windows as there are tons of insecure services installed by default and also when he gets software from dubious sources that this mighle also install open stuff?

---

