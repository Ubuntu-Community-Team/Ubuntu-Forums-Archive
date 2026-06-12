---
title: "NOOB OPENVPN Setup"
date: 2014-10-02
forum: Server Platforms
---

### Post by Michael_Knight on 2014-10-02
My situation is quite simple, I'm attempting to setup a VPN so that I can access the samba shares on my home server from anywhere in the world. I have setup the samba shares as well as openvpn on the server using the following guide: 

[http://ubuntuguide.org/wiki/OpenVPN_server](http://ubuntuguide.org/wiki/OpenVPN_server)

Where i'm getting lost is with actually connecting to the server from the outside world. My server is located at my apartment and is behind a router. Additionally, I've contacted my ISP and they do not allow static IP for residential connections. As such, I have setup an account with noip and installed the noip dynamic update client on my ubuntu server using a host which points to my current public IP. Nonetheless, I'm still at a loss as to what to do to access my server from the outside, and cannot seem to find any literature anywhere.

I'm hoping somebody can run through a list of steps that will get my server accessible from the outside world. Any help would be greatly appreciated.

Thanks!

---

### Post by TheFu on 2014-10-02
OpenVPN is full of options, which makes it extremely flexible. All those options make it non-trivial to setup for noobs.
[http://www.slsmk.com/getting-started-with-openvpn/installing-openvpn-on-ubuntu-server-12-04-or-14-04-using-tap/](http://www.slsmk.com/getting-started-with-openvpn/installing-openvpn-on-ubuntu-server-12-04-or-14-04-using-tap/) seems to have the steps for a simple setup.

Perhaps you would consider using **sftp** instead?
* simple **apt-get install openssh-server** for install and working configuration
* based on ssh, which is secure (when common sense is used)
* supports ssh-keys which is more secure AND more convenient
* uses the same port that ssh uses so firewall rules are easy
* clients available for **every** platform
* if you run openssh, then sftp is already there, ready to use.

If you need more than ssh/sftp access, then the extra effort of openvpn is smart. OTOH, ssh servers are very well understood, easy to secure, work well for their purpose, and are very easy to install and configure.  There is a great remote desktop, if that is a requirement too, that uses ssh for connections, x2go.

ssh servers are 100x easier than openvpn, in my estimate.  After you get ssh working, be certain to [secure it.]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures")

---

