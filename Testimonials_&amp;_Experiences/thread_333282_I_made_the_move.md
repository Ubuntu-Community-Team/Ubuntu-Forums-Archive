---
title: "I made the move"
date: 2007-01-07
forum: Testimonials &amp; Experiences
---

### Post by Gregor_s on 2007-01-07
Hi, after years of windows i finely decided to try out linux, downloaded and installed it on my HP nx7010 laptop without any problems (dual boot). Looks great, now my next task is getting my wireless to connect  :)

---

### Post by matthew on 2007-01-07
Welcome! I moved your post to a more appropriate location. I hope you don't mind.

---

### Post by Gregor_s on 2007-01-08
Wireless works - with a little help of NetworkManager Applet. that came with Automatix 2 package. Now I have to work on my bittorent. It's slow as hell, and just when my connection got upgraded by my Internet provider - bad timing :).  Must be my router - firewall. Then I still have to put my sound blaster card in my laptop and see if it works. Enjoying the experience so far.

Sorry about the post, I'm not yet familiar with the whole layout of these forums.

---

### Post by kebes on 2007-01-08
Welcome to Ubuntu! I hope you enjoy it.

> **Gregor_s said:**
> Now I have to work on my bittorent. It's slow as hell

If bittorent is slow, it's often because you have a firewall (on your router for instance) that is not enabling incoming connection requests. While bittorrent will work without any open listening ports, it's much faster when those ports are opened up, because people can initiate packet swaps directly to you. Otherwise it's always your bittorrent client starting to connect to new peers, which means you're always "ignoring" some portion of the swarm.

---

### Post by Soccrmastr on 2007-01-08
you can find many bit torrent cuztomization guides online specific for your client (I reccomend azureus) and ways to port forward for your specific router specifically for azureus. I reccomend this guide: [http://portforward.com/cportsnotes/azureus/azureus22.htm](http://portforward.com/cportsnotes/azureus/azureus22.htm) and that website also has specifics for forwarding azureus ports.  it all works great for me! good luck with everything too!

---

### Post by darweth on 2007-01-08
Good luck!

---

### Post by Gregor_s on 2007-01-10
I'm having some troubles. I installed Azureus with no problem. When I started to download, the connection slowed down, so I opened the port in my router. The speed improved from 40B/s to 200B/s :) - not so good. I experimented and completely stopped firewall on my router but the speed didn't improve. 

Today I tried again, this time I get an error from Azureus – UpnP: Mapping 'Incoming Peer Data Port(***UDP/33591)' has been reserved by 192.168.1.11 – please select a different port.

Those are the settings I used yesterday to configure my router. The trick is that my IP today is 192.168.1.2, but where it gets really interesting is – I don't have any settings in my router. Where is Azureus getting this? There are no ports reserved on my router I put them back to default.

But this is not all. I have changed the port and now I get much better speed 60-100 kB/s,  still not as much as I hoped (should be above 200 kB/s). Firewall is on and no forwarding.

I don't really understand whats happening, some help would be much appreciated.

Please bear in mind I'm a newbie.

---

### Post by Gregor_s on 2007-01-12
Looks like I found the source of my problems:

[http://forum.portforward.com/YaBB.cgi?board=Knowledge;action=display;num=1139203841](http://forum.portforward.com/YaBB.cgi?board=Knowledge;action=display;num=1139203841)

This Monday my internet provider switched »modems« while I was at work (girlfriend let them in). I knew thay brought in new »modem«, but I didn't really check what it was. And yes it's a router, that conects to my Linksys router! I'll check this out today.

---

### Post by jvc26 on 2007-01-12
Welcome to the forums, good to see you here,
Il

---

