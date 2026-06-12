---
title: "Ubuntu Server or VPN w/ NAS Server? (copied from beginner talk for better response)"
date: 2007-05-11
forum: Server Platforms
---

### Post by csleech on 2007-05-11
Ubuntu Server or VPN w/ NAS Server? 

--------------------------------------------------------------------------------

Hello all!

I am rather new to linux and can honestly say I haven't done any more than install a couple different distros and play with them for a couple days before I have become frustrated with not knowing what to do. I am very profficent in Windows (I am an Application Engineer for a software reseller) and want to take the next step in trying to learn linux. So PLEASE bear with me.

With that out of the way :) , I would like some opinions or advice from some of you out there that know this software.

At home I currently have three computers and a laptop. My one computer houses 5 hard drives and contains about 800MB of information. I would like to be able to share that accross my house (eventually) to any machine that is connected to my network; now I know I can do this with Windows, but follow along. I have a machine that I am dedicating to host files and currently I have NASLite running on that machine; there are some downfalls to NASLite (I have CDD verion) such as it cannot set user permissions and you cannot block access to a certain drive to a certain user. My ultimate goal is to share this information with friends and family and also allow them to have a drive to place information to share with me. I want to be able to control access to the discs based upon a user login. 

I have several options in doing this. One of them is to purchase a VPN router that controls the access for me. There is one that I have been looking at that is a ZyWall SSL 10 that allows for remote CLIENTLESS VPN connections (clientless is a MUST for me, my family is computer illiterate). However, this solution is $350. Another solution is to purchase a Linksys and do the DD-WRT flash and utilize the VPN capabilities of that modified router. The issue with this is that I do not know if you can control disc access with this firmware (I am in the process of trying to find out).

LAST option that I see is to keep the router that I have, enable VPN passthrough and setup a VPN type server. I do not know anything about what the linux community has to offer as a solution for my VPN desires, but I figured no better place to ask then here. :). So with that said, what is a must for my situation is as follows:

1. Clientless access (HTTP or HTTPS)
2. Controlled Access to certain discs (or files on discs)
3. Security, this is a must, some of the files are sensitive information.
4. MUST work with Windows (currently NASLite uses SMB to do this)
5. Scalability, I need the ability to keep adding hard drives using PCI expansion cards.

Can anyone from the community give me a linux (Ubuntu) prospective on this :confused:   

THANKS IN ADVANCE EVERYONE!!!:)

---

### Post by mohnkern on 2007-05-11
I may be wrong, but I think Samba would let you do Windows File Shares with user name and password authentication.

---

### Post by csleech on 2007-05-11
So from what I quickly read, Samba will allow me to have a computer act as a File server, but will it also help with my VPN desires or do I need other software to handle that?

---

### Post by Frosty Cold Drink on 2007-05-11
You can use Apache + mod_dav and SSL to get secure 2-way access to your server. User's can browse and all, and you can mount the thing as a remote drive / web folder depending on operating system.

You can use Samba, but to do it "right" you would need a VPN setup. PPTP is quick, easy, and broken. Recent versions of modern operating systems  can connect to a PPTP VPN without much work. IPSec+L2TP is a better choice, and almost as widely supported, but is a bit more complicated to set up.

A VPN appliance will give you a network-to-network or client-to-network VPN. Maybe you want this, maybe you don't. Do you want to spend $100-$400 or do you want to do the grunt work setting up IPSec+L2TP? :)

---

### Post by csleech on 2007-05-11
Mr.Frosty... You are exactly right! Which do I want to do... :confused: 

How difficult is the setup that you are referring to (IPSec+L2TP)? If I were to use this type of setup, what would the user login be like? Would it be a simple webpage? The biggest key for me is to make it EASY for people to utilzie; as I mentioned, my family is not the most computer savy. 

As for your point regarding the client-to-network and network-to-network, the only advantage I can see to using a dedicated VPN router is that the VPN tunnels would have better encryption that any standard VPN server setup, is that a safe assumption?

Thanks for the info and help, please keep it coming. :) 

(ps... i like the picture!)

---

### Post by Frosty Cold Drink on 2007-05-11
> **csleech said:**
> Mr.Frosty... You are exactly right! Which do I want to do... :confused: 
I think the first thing to do is deal with termonology, since there is a slight disconnect here.

VPN = Virtual Private Network, which has absolutely nothing to do with remote access. (Yes, yes. I know, I know...) VPNs provide encrypted network segments. That's it.

> How difficult is the setup that you are referring to (IPSec+L2TP)? If I were to use this type of setup, what would the user login be like? Would it be a simple webpage? The biggest key for me is to make it EASY for people to utilzie; as I mentioned, my family is not the most computer savy. 
If you use a VPN, user's connecting *will* have to do some sort of setup and then "dial-in" to your network whenever they wanted to do a little file sharing, and THEN do something to share files.

If you set up the VPN and Samba, and someone connects, they can then go to (dare I say it) My Network Places, browse around, and find your server, among other things.

> As for your point regarding the client-to-network and network-to-network, the only advantage I can see to using a dedicated VPN router is that the VPN tunnels would have better encryption that any standard VPN server setup, is that a safe assumption?
No. There should be no signifigant difference. The less capable VPN routers are actualy worse.

> Thanks for the info and help, please keep it coming. :) 

(ps... i like the picture!)
One of my favorite episodes!

---

### Post by PilotJLR on 2007-05-11
1. export the file shares with Samba (this presents a CIFS share that Windows can use)
2. establish remote access via SSL VPN

To be clientless as you mention, use SSL Explorer.
[http://www.subvs.co.uk/ssl_vpn_on_ubuntu](http://www.subvs.co.uk/ssl_vpn_on_ubuntu)


shazzam!

---

### Post by csleech on 2007-05-12
Well I have determined that it can't hurt to try the recommended method and see how easy it is for my family to utilize. I am currently downloading the latest version of the server edition and I am POSITIVE I will need help in getting every thing setup. 

I appreciate all the help so far. I am looking forward to this "learning" experiance. :)

---

### Post by csleech on 2007-05-12
So I get 7.04 downloaded and burned to a CD and the first of my issues begins... The computer won't boot to that CD (I tried burning it to two different CD's). Luckily I had an old 6.10 version lying around. 

And it begins... lol :)

---

### Post by csleech on 2007-05-12
OK... So I am installing the Server version, for my desired setup do I want a DNS or LAMP. (I am not going to control the names of other computers or handle a mail server) I imagine I want LAMP... Is that correct?

---

