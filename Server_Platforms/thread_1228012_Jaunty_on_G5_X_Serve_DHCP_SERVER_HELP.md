---
title: "Jaunty on G5 X Serve: DHCP SERVER HELP"
date: 2009-07-31
forum: Server Platforms
---

### Post by tom_tylutki on 2009-07-31
Hi everyone. Newbie to linux. I've looked at it time and again and made the decision to change a server at my wife's vet clinic to a linux blade instead of Mac OSX Server 10.4.x

This server is (well should be) a simple stand-alone server for a lan with no external connections. It is a G5 PPC blade. So I need to have it do the following:

DHCP server
Samba server
CUPS server
and I'm setting up mail as IM for internal use only.

I got JJ installed fine last night (I had tried yellow dog a few weeks ago and it gave me problems). Spent time trying to get DHCP server up and running as I was doing other stuff around the clinic (in addition to my regular work, I'm the IT, maintenance, contractor, etc for my wife......small business is great!) and I called it quits at 1 am. Since this blade is not connected to the outside world, I was using my MacBook to grab files off the web and transfer to the server. All was working great. I first tried latest build of DHCP (4.xx) but that wouldn't even build right on the blade so I grabbed 3.1.2p1. Seemed to build ok using make. Then did sudo make install. Appeared to work BUT there is no DHCP files of any type in /etc/init.d so when I tried to start it, it isn't doing anything. When I looked in the build path, I see a folder named Linux 2-2 and within that is a server folder and within that is a file named DHCP which is executable. 

So my thinking is my build/install failed somewhere and I started looking at the JJ repository this morning. I see a download for DHCP3-server. But the download formats are for i386 or AMD64. 

SO: what do I do? I need help on this. 

TIA

a highly frustrated Tom

---

### Post by tom_tylutki on 2009-07-31
I just found in the repositories a ppc build for DHCP3-server for Dapper. Can I just use this in JJ?

---

### Post by shredkingj on 2009-07-31
It's worth a shot.  Hopefully libraries and stuff that the DHCP server relies on haven't changed too much between now and then.  Have you considered just using Dapper?  You will continue getting updates until 2011, I believe, with Dapper.

---

### Post by tom_tylutki on 2009-08-02
well it won't install. 

doing some searching to see if I can get around this without having to downgrade

---

