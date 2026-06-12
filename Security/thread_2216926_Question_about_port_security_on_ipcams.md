---
title: "Question about port security on ipcams"
date: 2014-04-14
forum: Security
---

### Post by jedispork on 2014-04-14
Please move my post to a more appropriate forum if necessary. 

My ipcam supports ssl but it only works through a web browser.  So if I want direct access to a smartphone app I have to give up ssl. I was reading a discussion and someone was saying if you use a ridiculously high port number like 30,000 + that most routers will drop the ip long before they find your port. How accurate is this? I was surprised to find how little people care about security on their cam even in their home. Some cams will come with upnp enabled by default and happily forward all your ports. 

I thought about buying a router with a vpn server but then it would eat my phone battery. I also use a switch to shut the cam off when I'm home. 

thanks for the help

---

### Post by bashiergui on 2014-04-14
> So if I want direct access to a smartphone app I have to give up ssl. Why can't the phone app go over ssl? > I was reading a discussion and someone was saying if you use a ridiculously high port number like 30,000 + that most routers will drop the ip long before they find your port. How accurate is this? Stop reading that discussion. It makes no sense. Routers will find any IP and port you tell it to. Are you talking about remote bad guys scanning the Internet looking for your camera? Changing the port might make it a smidge harder to find, but it's not going make you invisible or invincible.

If you want a camera accessible from the internet then consider limiting the IPs that can connect to it. Get one that allows you to require login with a super long password.

---

### Post by CharlesA on 2014-04-15
I'd probably go so far as to only allow access to the cams via a VPN, so they aren't exposed to the internet.

---

### Post by jedispork on 2014-04-15
here is a quote from a user over at cctv forum

> If you're running behind a half-way decent firewall (either PC-based, or  appliance), you can simply pick a high random port number (30,000 or  so) to forward to you DVR's web port (usually 80).  That way, if some  knucklehead is scanning your IP address, your firewall should drop his  connection after a couple of port hits (and he's likely to be scanning  the lower 1024 ports for common services anyway) 

Unless your antagonist has an infinite number of IP addresses to  use, he'll probably move on to easier targets rather than continue to  knock on your ports and get blacklisted by your firewall. 

Its a great forum for setting up a cctv system however not many seem that worried about security. I have a hikvision cam with ssl and have no idea why their mobile software is not compatible. Sometimes I use ipcam viewer which works with my cam for the most part and has the ssl feature but that doesn't work either (and yes I remembered to set the ports correctly). I've emailed the author but never received a response. Right now I'm using xprotect go on windows for which you can run a self signed cert for ssl. However I want to get away from windows and the expensive commercial software. Zoneminder is a rough setup fwir , less efficient, and doesn't have mobile apps. Dropcam has ssl with no port forwarding. However they have a apple like attitude, charge a yearly fee, and the info is stored on their servers. 

I may go with the vpn router. I could do a local ftp server that syncs snapshots to dropbox for a quick check in.

---

### Post by CharlesA on 2014-04-15
Seems they assume the router/firewall will block an IP after x attempts. Some software can do that such as Fail2Ban or CSF, but I haven't seen that type of firewall configuration on many soho routers unless the firmware allows you to configure it as such.

You don't even have to get a VPN router, just set up a machine with OpenVPN and let it thru the firewall on your current router. A benefit of that is it'll let you access your home network when you are not at home.

---

### Post by jedispork on 2014-04-17
I did come across a explanation about the ssl feature on some of these cams. Here is a quote from network camera critic

> "Hikvision as well as other cameras can use SSL to connect to the camera  via a web browser, but the video stream is RTSP which can&#8217;t be natively  encrypted via SSL. Hence any software that connects to the camera for video can&#8217;t use SSL. One can setup a secure VPN (virtual private network)  tunnel between two points using SSL and any transmissions on that VPN  would be secure. You can even setup VPN software on a smartphone  although I never tried it. Each time you use the camera you would have to log in to the VPN before accessing the cameras. This would truly be the most secure setup possible and be totally independent of camera or app security."

I was hoping for a simpler way besides a vpn. Why would they not design these video protocols with security in mind? I may just stay with dropcam which was designed with ssl from the ground up. I think the ease of use and security is worth the yearly fee until the rest of the ipcam manufacturers start taking security seriously. 

 I appreciate the help and suggestions.

---

