---
title: "Need some advie on a VPN solution"
date: 2007-12-16
forum: Server Platforms
---

### Post by mespork on 2007-12-16
Hello all,

I am in search of some advice for remote access to our network at work. The person before me achieved remote access through RDP right to a server. I need to get rid of this because it very insecure. I would like to setup a VPN solution but all the VPs are used to just using remote desktop to get in from any computer that they sit down at. 

I finally have some of the VPs realizing that we need a more secure way of accessing the network. The problem is that there will not be the budget for a hardware VPN until July. This has me looking at openvpn. My question is does anyone have experience setting up a openvpn server on an Ubuntu server?

Thanks

David

---

### Post by HermanAB on 2007-12-17
Why do you say RDP is 'very insecure'?

Microsoft terminal services (bought from Citrix) uses RC4 encryption with a 128 bit key.  That is still strong enough for ordinary mortals.

Ensure that all users use proper long passwords and all should be well.

Cheers,

Herman

---

### Post by rickyjones on 2007-12-17
I personally use the VPN server that comes with Windows Server 2003 for my customers.

From what I've read about OpenVPN it should easily be doable, although last time I looked at it it seemed pretty complicated.

Good luck!

-Richard

---

### Post by koenn on 2007-12-17
I use OpenVPN but in a commercial application / applience, so i never had do deal with it directly, although I had a look at the documentation and it looked rather straightforward.  We use it as an alternative to leased lines, connect networks together over the internet. That also makes it transparant to the users : everything is solved at the network level, and users/applications don't even need to know about vpn. 
So, yes, openvpn looks like a good sollution to me.

---

### Post by The Cog on 2007-12-17
I vote OpenVPN too. It works very well, and seems much more reliable than MS VPNs. You may have to write your own script if you want to use username/password authentication as well as the client certificate.

Its normal authentication method is to use a unique certificate given to every client. Creating the certificates is a little complicated the first time you do it, but the OpenVPN documentation is very thorough, and you just follow the instructions parott fashion.

---

### Post by mmichalik on 2007-12-17
We use OpenVPN on our 6.06.1 server and it's as solid as a rock.  We set it up 2 years ago and it just keeps going and going.  

We manage it with Webmin and we've used the Windows VPN client in the past and now we use KVpnc on our remote laptops since we went strictly Ubuntu.  (with no problems.)

It's solid, and from what I remember somewhat easy to set up.

---

### Post by mespork on 2007-12-30
Do you dump the computers into a DMZ when they login? The only thing that I worry about is that I don't trust some of the computers that will be logging in so I need to protect our network. I am contemplating locking them down in a DMZ zone to isolate them from the rest our infrastructure. 

I have also considered using a freenx which to get them in.

Thanks for your input.

---

### Post by ^rooker on 2007-12-30
If you're looking for a simple solution to connect to RDP, etc. you could take a look at SSH tunneling. You can configure on the sshd-server side which ports the clients are allowed to connect to. 
(Search the web for "ssh tunneling")

You can use public/private keys to make it more comfortable for the clients to connect (no password). In my setup, I'm having a single user for all clients, and each one identifies by its own key - so I can simply lock out old/bad clients by removing their public key from my server. 

Details on demand.

---

