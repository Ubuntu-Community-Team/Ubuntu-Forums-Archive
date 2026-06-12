---
title: "Hosting a Domain"
date: 2007-08-30
forum: Server Platforms
---

### Post by TorchlightJay on 2007-08-30
Okay this may be a weird question but level with me here. 

You know how you can setup a domain like Blah.com or Blah.local that you can setup for a business local network. Is it at all possible to take that domain and make it WAN accessible. In other words, can I hve a notebook outside of the server's local area network and log onto the domain remotely?

I want to try and set that up but am not sure if it's doable, you know, that way I can fully connect to the office without being at the office.

Thanks

---

### Post by wirelessmonkey on 2007-08-31
If your domain is registered by an outside party, ex; I can go to [www.blah.com](www.blah.com) and see your content, then Yes.  If your domain is only internal, ex; intranet, or blah.local, then no.  You may, however, be able to log into the domain via IP. ex; ssh, ftp, rdp, vnc, etc.

---

### Post by rickyjones on 2007-08-31
> **TorchlightJay said:**
> Okay this may be a weird question but level with me here. 

You know how you can setup a domain like Blah.com or Blah.local that you can setup for a business local network. Is it at all possible to take that domain and make it WAN accessible. In other words, can I hve a notebook outside of the server's local area network and log onto the domain remotely?

I want to try and set that up but am not sure if it's doable, you know, that way I can fully connect to the office without being at the office.

Thanks

You could always setup a VPN server on the inside of your network. If your PC is joined to the domain on the inside then when you leave the network you can, at the login screen, opt to dial up to the domain and login. This would require you to have the VPN dialer already setup and working. Theoretically (as I've never done this) the VPN would dial, you'd be on the intranet, and then the login process would log you into the domain.

Hope this helps!

-Richard

---

### Post by HermanAB on 2007-08-31
OK, there is some confusion here.

The domain names are resolved by the Berkeley Internet Name Domain System BIND.  These are a distributed database of English names versus numeric addresses and is the primary mechanism for someone to find your server.  The DNS is a phone directory.

Anyone can go and register a domain with GoDaddy or Internic, but you need a server for the Domain Name System to point to.   An entry in the phone directory is no good if you don't have a phone.

 You can run a server at home or at a business (if you arrange a special server account with your ISP), or you can rent a server, or just a share on a server at a computer farm like CiHost or Yahoo.

When get a server account or rent a server, the service provider will assign you 2 or more IP addresses.  You use these addresses when you register your domain.  However, you still need to configure the server and hook it up to the net.

You could use the Ubuntu server edition, though I would suggest rather using Xubuntu or Mandriva if you want to run a server in your home or business where you would likely want to attach a screen and keyboard to it.

The server edition of Ubuntu is meant to be used 'headless'.  This is good when you have a stack of servers in a data centre with no terminals attached to them and you control them through SSH from another machine (which may be very far away).

'Hope that helps a bit!

Herman

---

### Post by TorchlightJay on 2007-08-31
Good idea Herman. You mention getting DNS from your ISP. Well I got five static IPs from my ISP and they gave me DNS servers. I bought some domains on GoDaddy and one is assigned to the my ip address which I am hosting a server. So do I need to go to GoDaddy and switch from their DNS servers to the ones my ISP gave me or should I keep the GoDaddy ones or should I attempt to build an in house domain servers. 

Once I have the DNS setup and what not, do I setup like OpenLDAP or Kerberos as a directory and then log into my domain remotely as we've mentioned throughout this whole convo, just setup to connect to this domain like i would any local domain? Does this sound right or am I missing stuff?`

---

