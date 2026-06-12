---
title: "Upgraded 9.10 to 10.04, now cant connect"
date: 2010-06-06
forum: Server Platforms
---

### Post by penguin_patrick on 2010-06-06
I have a prod box, that I put 9.10 on a while ago, clean install.

I've now did a do-release-upgrade to 10.04.

The operation went through, but now I can't connect to the box.  Our IT group turned off ping, so I can't see if that works.  I can't connect to apache, even though the server says it's running (ps -a | grep apache). I looked at the interfaces file, and all looks OK there, and ifconfig shows the ip address the same as before.  

I'd really rather not do a clean install on it, as there's a lot of data that I don't feel like re-sending from the backups.  It really seems like there's something askew in a config file, but I'm not sure where to look, or what file it may be.

Any help would be greatly appreciated.

---

### Post by garfonzo on 2010-06-07
I often have this problem on my home server where I do an update of some sort. The update goes well, but then the box is offline.

For whatever reason, I have found the following works. This assumes you have physical access to the box and can work right on it (ie, it has a monitor and keyboard). I have two ethernet cards, with only one actually in use (ie: eth0, and eth1). 

Here's what I do:

```

ifconfig eht0 down
ifconfig eth1 down
ifconfig eth1 up

```

That works for me, hopefully it helps you!

Cheers

---

### Post by penguin_patrick on 2010-06-07
Thanks for the input, I had seen that idea on another thread, and had tried the up part, but always saw that eth1 was UP in ifconfig.  I do have another eth (eth0) but it's not plugged in, just hanging out.  

But it still didn't connect. 

But, now after putzing around for hours, cleaning a crappy malware fake antivirus on my laptop (that I'm using to find info), and various reboots without really changing anything, the server is working again. 

I was in my office, trying to think of an easy way to grab the cert and key off the server to put on my dev box, and I happened to check the main web page, and it's working.  huh, go figure.

To celebrate, i'm going to pull the 2 ssl files off the prod server and store on the backup box, so it'll already be running, in case I need to do this again.

Thanks again for your input, it may have actually helped me out, but I did it the hard way, i think.

---

