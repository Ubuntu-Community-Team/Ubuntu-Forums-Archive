---
title: "Samba Server Configuration"
date: 2014-06-02
forum: Server Platforms
---

### Post by sweekly44 on 2014-06-02
Hi, I'm trying to set up a samba server on Ubuntu 14.04 LTS that approximately 50 people will be accessing using windows, mac and linux machines from the local network as well as other networks.In the near future it will also server as a print server. I have some basic questions as follows; Is samba even the best approach for this? What is the most secure way for it to be reached that is easy to configure on client machines? Is there a way I can allow clients to view videos? Would it be easier to make the server appear to be a mounted network drive, or could I configure it to be entirely in browser access? What is the easiest way to reach the server from other networks (I think I can use HTTP, openVPN, or SSHFS, but I could be wrong about this.) If some of these questions don't make sense it's probably because I don't fully understand the way clients interact with the samba server yet. Just ask and I'll try to be more specific. Thanks in advance for your time.

---

### Post by TheFu on 2014-06-02
Yes, some of your options in the questions are conflicting.
 
Samba is a CIFS server. Nothing more.  That means it is "windows file sharing" - with all the positives and negatives that entails.  Basically, you should NEVER use this over any untrusted network like the internet. It is not encrypted.

For cross-platform access to files on a LAN, CIFS is the industry standard.

Making files accessible over a web interface has different issues and security concerns. This method would have absolutely NOTHING to do with samba.  I would avoid WebDAV ... the protocol and every implementation have known security issues.

If you want to make files available over the internet in a secure way, look no further than SFTP. There are clients for every platform imaginable, it is based on ssh, so it is secure (as secure as anything is these days) and can be infinitely configured to allow/prevent access as needed though userids, group management and if you become desperate, ACLs.

So ... when you ask for easiest way, but most secure (those are competing needs) ... that normally leaves out VPNs since the easy to deploy VPNs are known to have trivial security issues (pptp), openvpn is non-trivial to setup on the server AND every client config is usually a non-trivial thing with the free deployment versions. Unless you are willing to give the administrative team exactly the same access as brand-new-user "Joe".  OpenVPN means you really need to understand networking, firewalls, ip-forwarding and routing too. 

If you plan to stream videos over the internet and don't want to make these all public to the world, then openvpn is really the only choice, regardless of the difficulties. Good luck with that.  OpenVPN solves all the other issues for alternative connectivity methods too - you can setup CIFS over openVPN for a network performance price.

So ... if you can back up and tell us more about the exact uses for this server and how people will get access, we can lead you in specific directions better.  If nobody is on the LAN, that is completely different than if 49 users are on the LAN and 1 person is remote.

---

