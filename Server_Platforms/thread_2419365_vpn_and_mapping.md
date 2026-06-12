---
title: "vpn and mapping"
date: 2019-05-20
forum: Server Platforms
---

### Post by matt18 on 2019-05-20
Ok, so i have a win10 box at home. I have a traveling laptop that i use for school. i would like to setup a vpn server at home that allows me to map my win10 box drive to my laptop so i can access the files whereever i am. 

would the setup be like so:

win10box connects to vpn server.
laptop connects to vpn server
on laptop, map a drive by typing in the "private" ip of the win10 machine

I have done this succesfully with hamachi but i would like to try out a vpn ubuntu server to accomplish samething.

thanks

---

### Post by wildmanne39 on 2019-05-20
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by darkod on 2019-05-21
You don't need "step 1".

If your win10 and vpn server are on the same home LAN, connecting a laptop to the vpn server will make it available the laptop to use any LAN private IP as if it was in the same LAN. The speed over internet is a different thing, since you want to access files.

For the above to work simple and easy, make sure the server.conf of the vpn server includes the line to push a route to the client. That makes the client know to send traffic destined to that LAN over the vpn tunnel.

The only issue you could have is if sometimes the client is connected to same LAN network subnet as your home network. For example, if you have the standard 192.168.1.0/24 at home, and you are at a friends who also has 192.168.1.0/24 and use his wifi, your laptop will not know the difference between your friend's IPs and your IPs behind the vpn.

---

### Post by TheFu on 2019-05-21
Darko points out an important subnet problem.  In general, if you are going to run a VPN server on your home network, then you don't want any of these subnets for your home because they are commonly see at other locations:
192.168.0.x/24
192.168.1.x/24
172.16.x.x/24  <--- don't confuse that the actual allowed subnets is a /16
10.1.x.x/whatever  <---- this is a /8 for non-routing, but commonly split as /24

Pick almost any odd number below 255 for the 3rd byte and you should be fine, almost always. The goal is for your home network subnet to be unique from which any networks you might remote connect. This assumes you understand subnetting and pick from the valid non-internet-routable subnets.
I use 172.22.22.x and 172.22.21.x for my LANs.  The ISP uses 10.1.10.x/24 for the subnet they force me to have, which I treat like the raw internet.  My ISP router bridges the public IPs to my router.  Most cafes, restaurants, hotels will be 192.168.x.x and most corporations will use a 10.x.x.x.  All of these are private networks.

Also, beware that the openvpn guys recommend against using samba or cifs sharing over openvpn due to the way the protocol likes to broadcast.  I think there is a specific sort of openvpn setup they recommend if that is required. If you don't use samba/cifs, then any other file sharing technique works fine. Being windows-to-windows, you are sorta stuck.  If you had some Linux in there, you could just setup ssh, get sftp and scp for free, then connect from your travel computer using any sftp client, like WinSCP and your ssh-keys.  setting up ssh is fairly bonehead. Openvpn can be challenging if the very simple, default, setup isn't sufficient.  I have both, but use ssh access with keys 95% of the time.

---

### Post by matt18 on 2019-05-22
Yes, i have ran into the subnet issue before. thanks for the reminder:) To avoid this, i ussually use an obscure ip scheme. such as 25.x.x.x to avoid this. My school uses 10.x.x.x, so does my parents but my friends house uses 192, and another uses 173. So i have concluded to use 25.x.x.x haha. wait.... i dont think i can use 25.x.x.x, ill have to read the rfc for private ip again. anyway, ill find the right one, or ill just have to use an odd subnet OF those above networks.

I used to have ssh setup a few weeks ago, BUT the person who owns the router moved. Now a new campus router is installed and i have NO ACCESS AT ALL. hence the reason i went with hamachi. Plus i like the integrated setup with mapping. it opens the drive right up in file explore without a client. Granted i could use SFTPnetdrive, but then again, i have to have ssh working. however, ssh works over hamachi.

Main reason i want an open vpn server... to learn and i have heard it is faster and better than hamachi.

Unless you know of a way to port forward without access to the router, im all ears. im serious, i would love to have my ssh server back up. The router is a basic xfinity router. I can get to the router page and it says security is set to low, but i do not know user and pass. I do know that all incoming by default is blocked except ports 80, 25 and a few others. could i piggy back ssh on one of those?

thanks

---

### Post by TheFu on 2019-05-22
You should talk to the official owner of the new router about your needs. Definitely check the RFCs for private subnets.

---

### Post by matt18 on 2019-05-26
lol, yeah. 25 belongs to the british department of defense haha. it is a private space but it belongs to someone else

I did talk to owner and no go.... sooo

---

### Post by darkod on 2019-05-27
I would stick to the RFC defined private subnets, that is why they were created. Don't use public subnets.

Just because someone uses 10.x.x.x (your parents + other sites) that doesn't mean you should discard all of it. That subnet is huge.

Select some value to minimize the possibility of identical subnet, and go for it. For example, choose something like 10.141.252.0/24 and you would have really bad luck to find it elsewhere.

The private subnets with 172. are also rarely used so they are a good choice. Just make sure you select from within the private range because there are public ranges beginning with 172. (unlike 10.).

---

### Post by The Cog on 2019-05-27
Darkod is right. I would also suggest using a chunk of 10.x.x.x. Picking random numbers for the second and third bytes is unlikely to clash with any private network you are likely to connect into, and 10.x.x.x is guaranteed never to be public so you won't be masking real internet sites. I run 2 VPNs, and they are 10.9.8.x and 10.9.9.x. Not as random as they could be, but I think I'm safe enough using those, and I can remember them.

---

### Post by TheFu on 2019-05-27
> **matt18 said:**
> lol, yeah. 25 belongs to the british department of defense haha. it is a private space but it belongs to someone else

I did talk to owner and no go.... sooo

If the owner won't forward ports, then you are done, at least at running a server there.
Spend $5/month and get a VPS. Go crazy running whatever servers you like.  You could run a gateway on the VPS.

As for using public IPs inside a LAN.  I've worked places where we did that.  It simply meant that our internal computers wouldn't be able to find a route to the real IPs on the internet.  As long as your router isn't trusted to maintain BGP or RIP2 route exchanges, it won't be THAT bad.
OTOH, it is 1,000x easier to just use one of the thousands and thousands of private LAN subnets setup to be used privately.  If you don't fully understand networking, stick with the private LAN subnets listed in the RFCs, like others have said.

---

### Post by matt18 on 2019-05-27
> **TheFu said:**
> If the owner won't forward ports, then you are done, at least at running a server there.
Spend $5/month and get a VPS. Go crazy running whatever servers you like.  You could run a gateway on the VPS.

As for using public IPs inside a LAN.  I've worked places where we did that.  It simply meant that our internal computers wouldn't be able to find a route to the real IPs on the internet.  As long as your router isn't trusted to maintain BGP or RIP2 route exchanges, it won't be THAT bad.
OTOH, it is 1,000x easier to just use one of the thousands and thousands of private LAN subnets setup to be used privately.  If you don't fully understand networking, stick with the private LAN subnets listed in the RFCs, like others have said.

25.x.x.x/8 is not a public ip, its a private ip space that the british government uses:) We can still use it, but if i plan on talking with the BMOD, then i would have to change because then its the same issue with running a VPN in the 192.168.0.0

When it comes to networking, i WAS cccnp about 10 years ago. I still know how to configure cisco switches and routers for enterprise protocols, i just do not like to... at all haha. I may not remember all the private IP's but i can subnet and suppernet like crazy. im pretty good at it. 

I have ssh working.. Im just running it through my hamachi client. I am just looking for a better solution than hamchi, or a way to piggy back ssh on another protocol such as port 80.

let me re-read my posts to see if i miss communicated something. I really appreciate your advice about the VPS as well. If they have a way to allow me to keep my data stored locally and not on their servers, then i might:)

---

