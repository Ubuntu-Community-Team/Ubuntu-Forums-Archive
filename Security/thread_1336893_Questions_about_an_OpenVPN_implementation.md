---
title: "Questions about an OpenVPN implementation"
date: 2009-11-25
forum: Security
---

### Post by ajlee on 2009-11-25
I've been lurking on the forums for a while now, and have been running ubuntu as my main OS for a couple of years.  I'm still a bit of a newbie when it comes to network security.  I'm getting ready to implement an OpenVPN server and I wanted to get some feedback 

I currently have two ubuntu servers, one I am using as a file server that shared by two laptops (one ubuntu, one windows XP), the other I'd like to use for OpenVPN and some additional storage for my ubuntu laptop when I'm away from home.  

Both sit behind a Linksys WRT54G.

Please tell me if what I am thinking makes sense.  

I'm thinking about using dyndns, forwarding a port on my router to the VPN server, and using keys instead of password logins on this box.  I want to for sure keep people off the current file server so I was thinking about using iptables to drop any packets sent to the file server that originate from the VPN server.  

Does this seem like a good idea?  Is the iptables configuration overkill?  Is VPN enough to secure both servers?  I guess it would be nice to have access to both servers if possible, but I was thinking of keeping the one offline for added safety.  

I'm also a bit confused because it is my understanding that the VPN server uses keys, so are ssh keys also necessary?  Are they one in the same?

Sorry if these questions are elementary – like I said, I'm still a bit of a newbie and I'm hoping to draw on the experience of others.  Anything you can share to point me in the right direction would be very much appreciated.  

Thanks!

---

### Post by kevdog on 2009-11-25
You could flash your router with ddwrt (specificall a vpn version) that has OpenVPN built into the router.  That way you could be on the same subnet as the rest of your computers.

OpenVPN does not use ssh keys, you generate these a different way.
And yes OpenVPN is secure.

Here is something that got me going: [http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html](http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html)

Read the user comments at the bottom of the link -- they help!

---

### Post by ajlee on 2009-11-25
Thanks a lot!  I'll check that out.

---

