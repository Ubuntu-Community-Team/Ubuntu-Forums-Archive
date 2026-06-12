---
title: "Guides for server setup"
date: 2007-05-21
forum: Server Platforms
---

### Post by DrNick on 2007-05-21
Hi all

I would like to set up a home server of sorts using the Ubuntu Server edition. I have previous experience using this, in fact I use it at work to run a variety of services, and have a medium level of Linux knowledge and experience, being a network technician by trade.  What I would like to do is build a box with 2 NIC's, which can do all of the following:  routing (to glue together my LAN with my broadband), DHCP, DNS, NAT, IP firewall, File & Print server, mail server, web server (LAMP), FTP server.  There is also the possibility of using it for: half life dedicated server, streaming audio server and network app testing server (probably inside a VM!)  

As previously mentioned, I already have some experience with (successfully) setting up many of these services.  However as a whole the project is a largish one, and I was wondering if anyone knew any good guides which I could consult for reference if (when) I get stuck on things?  I can generally work things out on my own with no guides given enough time, but a good guide would be appreciated if it saves a lot of head scratching...

In my experience, the Ubuntu server documentation is good to get you going, but doesn't really go into enough detail at all when it comes to setting things up specifically.  I know for some things its fairly obvious, however as with everything, the sad truth is that's never always the case :-) 

The second question I have is if you think the hardware I have to hand will be powerful enough for what I'm asking.  I've previously been very impressed with what Linux is able to run on limited hardware, but I just wondered what your thoughts were.  It won't ever be used by more than 3 machines at once, and usually less than that.  The box in question is a 450Mhz pentium 3, with 384Mb RAM, and several (4) disks for storage, the largest being 250Gb for the file store.  It also has 2 NIC's (obviously). 

Any information would be greatly appreciated.  Thanks for reading, 

Tom Byrne

---

### Post by tgm4883 on 2007-05-21
That could be pushing it for the Halflife 2 dedicated server even by itself.

The rest looks fine though.  The audio should stream fine, but if you plan on streaming video you may/may not run into problems.  I did have streaming video on my 700mhz server and it worked ok, but now have upgraded that to an athlon xp 2000+

:EDIT:

Just noticed you will test network apps in a VM on that server.  Your not planning on running a GUI on the server are you?

---

### Post by DrNick on 2007-05-21
Thanks for your reply tgm. Looks like I was hoping for a little too much with the half life server then  :-)

I certainly won't be doing any video streaming, so I'll give the rest a go.

---

### Post by DrNick on 2007-05-21
Well, I *might* test network apps on it.  But being the server side, they won't have gui's no.

No one else any ideas for guides?

Thanks,

Tom

---

### Post by Brazen on 2007-05-21
If it considered very poor security practice to run services like file share or game servers on your firewall appliance.  I would suggest picking up a linksys wrt54gl and install dd-wrt on it for your firewall/dns/dhcp and the put your server behind that.

---

### Post by DrNick on 2007-05-21
I would disagree there.  I'm planning on doing routing, firewalling etc on a proper Linux box because of the added flexibility it gives.  I am aware of modded firmware for the wrt54gl, and I've seen such devices in action.  As impressive as they may be, they still don't quite cut it in terms of manageability etc.

Regarding security, it is fairly easy to take sensible security precautions when installing multiple services on such a machine.  The most logical first step is only binding services such as samba to the internal network interface.  Once this is done, only machines from the internal 'net even see these services, so the only way an attack could happen would be if someone somehow gained control of a machine on the internal 'net.  Combined with sensible firewall rules and good security updates, the system will be pretty secure.  

I do take on board your point however, and in a business situation it would be pretty silly to put services like that on a device protecting your entire network - not least because of loading issues. However this is just a home server...

---

### Post by vbmds on 2007-05-21
I just setup a server with some of the same roles as your looking to run on yours, and found this to be useful: [http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10]("http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10")

---

### Post by DrNick on 2007-05-22
That looks a very helpful article, thanks for your replay!  :D

---

