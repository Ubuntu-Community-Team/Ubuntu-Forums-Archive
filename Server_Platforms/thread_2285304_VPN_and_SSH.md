---
title: "VPN and SSH"
date: 2015-07-04
forum: Server Platforms
---

### Post by branau on 2015-07-04
So I'm looking to set up a home server, and I had originally intended for it to work as a backup for important files and a cloud, so I could stream music and movies and I planned to do all of this through SSH. However, I travel a lot and I've been reading up on VPN, so I'd like to make this server a VPN server as well. First question, could I run a VPN server and transfer files via SSH without having them conflict each other in any way? Second, if that can be done, what kind of hardware requirements would I be looking at? This server is probably just going to be for me and maybe a couple members of my immediate family, and it certainly won't have anything super important like corporate financial information, so ideally it would be a sort of virtual playground for me to learn some more about networking and security while I tinker with it. Thanks in advance!

---

### Post by TheFu on 2015-07-04
A file server doesn't require much.  A $25 raspberry-pi can suffice for this. For internet performance, I doubt the r-pi would be the problem for throughput, though if your home network is wired GigE, then the R-pi probably cannot access data quickly enough.  Any cheap x86 CPU+MB combo total price of $80 will be able to flood a GigE network.

All you need to install is openssh-server and fail2ban.  Then just use sftp to access the system from inside the LAN and from the internet. Please use ssh-keys, not passwords over the internet.  If the ssh port is left on the default (22/tcp) setting, the default fail2ban settings are fine out of the box without any changes. When ssh works, sftp and scp also work - by default. You get all three.

When you say "virtual playground" to me, I hear that you might want to run 10 virtual servers.  Hardware to do that isn't much more expensive, provided none of those virtual machines runs MS-Windows. A $150 CPU+MB and 8G of RAM can easily support 5-10 Linux VMs - clearly a more powerful CPU will perform better. If you have $400, a Core i5 system would be amazing. Look for VT-x and VT-d support.

If you are comfortable with ssh and only intend to provide file access to family, there really isn't any need for openVPN (or any VPN): [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

Windows users would use WinSCP and Putty to access sftp and ssh servers on any Unix machine.

IMHO, the only reason to run openvpn (and there really isn't any other F/LOSS VPN that is respected), would be to stream media from anywhere in the world.  ssh can handle everything else and running ssh tunnels inside a VPN just isn't smart from a performance perspective. You can have both and use 1 or the other. Once configured, openvpn is slightly easier for end-users to work with, but it is harder to setup and explain that using sftp can happen with or without the vpn running, but browsing samba can only happen with the vpn up/active.  ssh sorta just works and if you listen on both 443 and some strange high-port (61022), you'll probably not have any issues from hotels blocking it. 

[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) - ssh security

Hope this all helps.  ssh is an amazing tool.

---

### Post by branau on 2015-07-04
Hey Fu, thanks for the reply. I was hoping to hear from you haha. I've been reading articles from your blog with security tags on them for the past couple of weeks :D

I definitely want to use SSH for file transfer because of what I've read on your blog. I've even begun figuring it out by setting up my git repositories with BitBucket to be accessed via SSH keys, I was just curious about VPN because this particular server will be set up in the US so that I can still access things like Pandora while I'm abroad. I actually live in Mexico so I spend maybe 1-2 months out of the year in the States. That was the primary reason for the VPN because I don't trust using someone else's US VPN server to get access to US-only websites or having secure browsing while at an airport or coffee shop. If I were to run two virtual machines, both linux, could I have one for SSH file transfer and another running a VPN server for me to remotely access it for streaming music or secure browsing on public, unsecured networks?

[s]And seeing as I'll be physically away from this server for 10+ months a year, could I remotely perform maintenance and test things with it securely?[/s]
EDIT: Looks like I can do that through SSH, nevermind.

---

### Post by TheFu on 2015-07-04
ssh is just like being there ... er ... mostly.  If ssh doesn't work, there is always "console" access provided by the VPS vendor which generally sucks. Learn to love ssh.  A GUI is just to have more ssh windows, IMHO.  I have 13 windows on my system right now. 2 are NOT terminals (ssh) onto other systems.

For streaming audio and video - a vpn really is the easiest way, but be aware you are adding 2 hops, so performance will reflect that and a 10G monthly transfer limit will go fast with video.

You can have ssh and vpn on the same machine. I would.  Basically, I have ssh running on every system, period. How else would I patch weekly using a trivial script (or ansible)?  It isn't like I want to manually ssh into each machine and run the commands manually. As a lazy sys admin, that would just be crazy!

Good on you for NOT trusting any VPNs - a recent security researcher article showed how 80% of VPNs were making dumb mistakes which leaked IP data of the source system. When you run the VPN, YOU have control (and responsibility) for preventing source-IP leaks.  Oh - and don't use pptp if you care anything about security.

For secure browsing from a cafe, I just use ssh to tunnel back to the house and let my ISP/NSA see the traffic they expect from that origin. ;(  I know they'd be disappointed if I skipped a day of surfing, even when traveling overseas. ;)

Yes - ssh is amazing.

---

### Post by branau on 2015-07-04
Well, thanks again for all the help Fu! I've definitely got a lot to look up and play around with to keep me busy for a while, so I'll get to it. 


All of this has made me consider studying network security instead of software development...

---

### Post by TheFu on 2015-07-04
> **branau said:**
> Well, thanks again for all the help Fu! I've definitely got a lot to look up and play around with to keep me busy for a while, so I'll get to it. 


All of this has made me consider studying network security instead of software development...

I'd do 50/50 on each. ;)  I started out developing software for the first 15 yrs of my career, then switched to architecture,  sysadmin and eventually got forced into technical architecture roles.  Networking is my weakest area, but I haven't coding anything significant in about 15 yrs.   If you do stay on software, you'll probably earn more money starting out. Be certain to read the OWASP guides for your language. [https://www.owasp.org/](https://www.owasp.org/)

All this stuff takes time. I don't recall when networking "clicked" for me ... probably after about 8 yrs doing SW development, but it was a different world back then and at work we didn't have IP networks.

---

### Post by branau on 2015-07-04
That's good to know. I didn't plan on completely dropping software as I do enjoy writing programs for myself but I'm thinking of changing my focus, we'll say. If you recommend I go at em both equally, though, then I'll make sure to keep at what I've been doing and just add some security/networking studies in with it. 

Patience isn't one of my best traits but I do try to keep in mind that I won't get it all within a couple of months, or even years. I understand that it takes a long time and I need to get a lot of experience. Regardless, I've been reading so much and changing so many habits when it comes to networking that my girlfriend now thinks I'm paranoid :P

---

### Post by Lars Noodén on 2015-07-05
+1 for all the TheFu wrote above.  

Since you almost wrote that you would not have physical access most of the time, if you  are fiddling with iptables, you might prefer to use [iptables-apply](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-apply.8.html) to work with your rules so you don't get locked out.  If you are using only UFW then you can set an [at](http://manpages.ubuntu.com/manpages/trusty/en/man1/at.1.html) job set for the near future to undo your changes. That can also keep you from getting locked out.  

Fail2ban has the name recognition still but as far as I know it does not support IPv6, so if you need IPv6 or maybe for other reasons, you can look at sshguard.  

And one of the smooth ways of connecting to the remote server via SFTP is to use sshfs.  That uses FUSE to mount the remote system as what appears  to be a local folder.  Then all the normal file management tools can be used transparently.  Though these days, most file managers themselves support SFTP fully.

---

### Post by branau on 2015-07-05
> **Lars Noodén said:**
> if you  are fiddling with iptables, you might prefer to use [iptables-apply](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-apply.8.html) to work with your rules so you don't get locked out.  If you are using only UFW then you can set an [at](http://manpages.ubuntu.com/manpages/trusty/en/man1/at.1.html) job set for the near future to undo your changes. That can also keep you from getting locked out.    That looks helpful, thanks! Right now I'm still learning how to use ufw and I've barely scratched the surface of iptables but I'll keep those in mind.   > **Lars Noodén said:**
> Fail2ban has the name recognition still but as far as I know it does not support IPv6, so if you need IPv6 or maybe for other reasons, you can look at sshguard.    I have to read up a lot on IPv4 vs IPv6 to understand the differences but I'll look into that too. Thanks  > **Lars Noodén said:**
> And one of the smooth ways of connecting to the remote server via SFTP is to use sshfs.  That uses FUSE to mount the remote system as what appears  to be a local folder.  Then all the normal file management tools can be used transparently.  Though these days, most file managers themselves support SFTP fully.  That would be a really convenient feature, pretty much just like DropBox right? I'll look to see if the built-in Files program is compatible with SFTP.  Thanks for all your help!

---

