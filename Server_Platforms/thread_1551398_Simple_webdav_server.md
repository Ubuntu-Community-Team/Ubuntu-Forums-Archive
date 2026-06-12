---
title: "Simple webdav server?"
date: 2010-08-12
forum: Server Platforms
---

### Post by tpspoons on 2010-08-12
Hey guys

My boss just asked me to see if I could setup a way for him and the other employees to access our local network from anywhere securely (oh and it has to be for free or very very cheap). I'm his go-to guy for all techie things and usually thats fine but I've never setup a server before so I've been having a few troubles with this one.

I figured the best solution would be to build an ubuntu server using one of our old PC's with webdav +ssh security set up? What do you think?

Based on that I've been reading various how-to's and guides but not much has worked as planned :(

Well anyway rather than try to debug each problem individually I figured first it would be better to ask the experts what the best route to take would be.

Any advice at all would be very much appreciated :)

---

### Post by NIT006.5 on 2010-08-12
Is this to access the entire local network, or just files stored on the Web server? I haven't used Webdav before myself, but by definition it appears to be for the latter.

If complete access to the local network is required, then I would think you want to go with a VPN. Something like OpenVPN would work quite nicely for this, and there's Windows client software for it too. That will cater for encrypted, authenticated connections to the local network.

---

### Post by tpspoons on 2010-08-12
Yea it would be for the entire local network - not for the files on the server. I didn't realise that wouldn't be possible with webdav cheers I'll look into OpenVPN.

---

### Post by NIT006.5 on 2010-08-12
> **tpspoons said:**
> Yea it would be for the entire local network - not for the files on the server. I didn't realise that wouldn't be possible with webdav cheers I'll look into OpenVPN.

For all I know it "may" be possible with Webdav, but not sure. OpenVPN should suit your needs quite nicely though. Good luck!

---

### Post by mituw16 on 2010-08-12
it is NOT possible with webdav. Webdav is almost exactly like FTP in functionality, except it operates over the HTTP protocol (or HTTPS.. :D ) ... 

based on what the OP is saying he needs. Open VPN is really your only solution.

---

### Post by tpspoons on 2010-08-12
Thanks alot.

I'm setting up OpenVPN at the moment I'll let you know if I come across any problems.

---

