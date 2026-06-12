---
title: "Checking the torrent Web UI from outside home"
date: 2010-10-09
forum: Security
---

### Post by whitefish10 on 2010-10-09
Hi guys, I am thinking of using Dynamic DNS from DynDns.com to connect to my Ubuntu 10.04 laptop to check from outside home the torrents files that I am downloading. Basically my goal is that if I go to any browser, type the link + password and I am their.  

But what I am worried about is security. Currently my deferences are (wireless router firewall, Ubuntu firewall and the password for the torrent Web UI) which are all what I have. 

What I am looking for is a way to make things more secure, some one recommend me using OpenSSH and/or OpenVPN. But I have no idea if it fits for my case nor will make things easy for me to access the machine from outside (usually OpenVPN need to install a client software, as people will not accept for random places).

Please tell me what do recommend and how to do it if possible.

Thanks.

---

### Post by johngreth on 2010-10-09
Your router probably already blocks incoming connections. If a computer or server on the Internet tries to connect to your router without being prompted to do so by a computer on your network, the router will just deny it.

To allow the Internet to connect to your computer, you need to tell your router to forward incoming connections to your computer. You can either forward all ports (DMZ routing) or you can forward just the port that bit torrent uses. The later is much more secure.

If you have a Linksys router I can describe the steps to do this.

By only allowing the Internet to connect to one port, you are limiting attacks to ones that exploit security weaknesses in bit torrent (which are slim to none) instead of your whole computer.

using openVPN/openSSH would make it more difficult for a hacker to figure out your password, so that's probably a good idea. The protection here is that anyone that can see your communication with the server won't be able to read your password. This is unlikely, but possible.

I don't know very much about either utilities, but I imagine it will take some special configuration to actually protect your connection. When connecting, if you don't see https and get a non-valid key error, it's not set up right.

This is because the server would use a key that was not distributed by verisign or another agency, so your browser will warn you that the since the key hasn't been registered it may not be valid. This is normal.

If you can't get this working, it isn't that big of a deal. The real important thing is that you only allow the ports you are using.

hope this helps

---

### Post by jbrown96 on 2010-10-09
There's no way to make the Ktorrent interface secure. You have to encapsulate it in a secure connection: VPN or SSH.

There's no other way. That interface is not designed to be secure, and you should not enable internet access to it.

---

### Post by johngreth on 2010-10-10
All the vpn/ssh does is hide the information sent over the connection. If there is a security hole in the interface itself, ssh won't protect that.

---

### Post by Agent ME on 2010-10-10
It would stop people who are not authorized from accessing it from trying to poke holes in it though.

---

### Post by johngreth on 2010-10-10
How does that work. Anyone can still create a connection to the server. Then they can send the same commands to hack it. Why does it matter if the hacking/probing is encrypted?

---

### Post by jbrown96 on 2010-10-12
> **johngreth said:**
> How does that work. Anyone can still create a connection to the server. Then they can send the same commands to hack it. Why does it matter if the hacking/probing is encrypted?

No. If you use a VPN or SSH, then there is no way to connect via the internet. The VPN or SSH connection must be established first. There is no access without it.

---

### Post by johngreth on 2010-10-12
What is there to stop a hacker from making that connection?

---

