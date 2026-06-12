---
title: "Public Private Keys"
date: 2009-03-05
forum: Security
---

### Post by vanderkerkoff on 2009-03-05
Sorry to be such a dumb *** but I wanted to clarify something.

I've setup an OpenSSH Ubuntu 8.04 server

ssh -v
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007

to not allow password logins, running on a non standard port, created a public/private key pairing with ssh-keygen,, moved the public key onto my MacBook

ssh -v
OpenSSH_5.1p1, OpenSSL 0.9.7l 28 Sep 2006

and now connect to the server from around the world successfully through the terminal window.

Is all the data that I pass from my laptop to the server, such as commands in the terminal window, or file transfers with scp in the terminal, encrypted on my end, and then decrypted at the server?  And then is all the data similarly encrypted in the other direction?  Or is the only thing that the key pair is used for is initial access to the server itself?

A colleague has suggested setting up VPN and using PPTP to connect, but I was wondering if my setup was an acceptable level of security cpmpared to the VPN.

---

### Post by brian_p on 2009-03-05
> **vanderkerkoff said:**
> 

Is all the data that I pass from my laptop to the server, such as commands in the terminal window, or file transfers with scp in the terminal, encrypted on my end, and then decrypted at the server?  And then is all the data similarly encrypted in the other direction?

Your understanding is correct.

---

### Post by vanderkerkoff on 2009-03-05
Thanks Brian

So would you say my system is more or less secure than the VPN option?

What a colleague is suggesting is that I use VPN to get into our network, via a VPN Server, and then use ssh through that VPN tunnel once I am in the network.

I don't know how VPN works but how would I authenticate with the VPN server?  Wouldn't I have to send a username password down that line?  Wouldn't that be less secure?

Another problem I saw with that is that will only work for accessing the data from outside the network, I'd then have to use the same public private key access for inside the network.  So I'd have to setup 2 systems, and as far as I see the VPN one is not more secure than the original public private key system already in place.

Any help is greatly appreciated with this.

---

### Post by Brandon.Viking on 2009-03-05
If I read what you have written correctly, you would have to setup a key pair twice if you want to use key pairs for your vpn. All you end up doing is encrypting your data twice. Completely up to you and whether your organisation has a security policy to comply with or not.

Brandon.

---

### Post by brian_p on 2009-03-05
> **vanderkerkoff said:**
> 

So would you say my system is more or less secure than the VPN option?

With strong passwords or keys ssh is immediately secure over a public network (e.g. the internet). A VPN is a private network which is run over a public network and is not necessarily as cryptographically secure but can be made so.

For the uses you outline a VPN seems overkill. You could read

[http://computer.howstuffworks.com/vpn.htm](http://computer.howstuffworks.com/vpn.htm)

---

### Post by vanderkerkoff on 2009-03-05
Thanks both

I'm happy with the system in place and feel it to be secure enough for my purposes.

If I get into an argument/discussion with the VPN bods about it then I'll ask them for alot more information about how they have setup the VPN and probably come back to you guys for advice/ammunition. :-)

Thanks again

---

