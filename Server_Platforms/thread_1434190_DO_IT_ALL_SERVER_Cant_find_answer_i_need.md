---
title: "DO IT ALL SERVER Cant find answer i need?"
date: 2010-03-19
forum: Server Platforms
---

### Post by duramaxx2003 on 2010-03-19
Hey guys, I have been looking into building a home server that:

Router/Firewall
File Server (Windows/Linux Machines)
XBOX 360 and Wii File Sharing
DVR (just record shows)
Blog Host (possibly)
Torrent Downloads
Backup (windows/linux machines)

PC Specs
2.4 Ghz AMD Athlon64
2 GB Ram
Two 160 Gb IDES
motherboard eth and pci eth(if wont work ill buy one)

I know there have been posts on ubuntu router an so forth but i have searched for two days and can not find anything specific to what I need answered.

Here it goes. I want all this in one package. Need to know if it is possible? Next Security setup? Smoothwall? Ipcop? Whats best setup for firewall/router in ubuntu?  Im gonna use ushare for the xbox sharing. Found a few wii programs but haven't decided(input welcome). Mainly just input on programs to do the task and if they will all work together seamlessly. Thanks guys hope to hear back from ya.

---

### Post by Donny Bahama on 2010-03-19
Personally, I'd say that's a bad idea. (It's certainly way beyond the typical scope of the term "server".) In my experience, trying to get one box to do too many things is setting yourself up for failure. At a minimum, I'd offload DVR duties to another box. Maybe also consider offloading router/firewall duties to a small appliance like a Linksys router running DD-WRT or Tomato.

---

### Post by jrssystemsnet on 2010-03-20
By far the hardest tasks on your list are the DVR and the firewall/router.

Unless you just really REALLY want to do it to flex your "nerd nuts", you're almost ALWAYS better off letting a cheap SOHO router handle your firewall/router needs.  It's cheap, you probably already have one anyway, it has no moving parts, generates less heat, and has a far lower mtbf than your PC as hardware... much less your PC as "a thing you like to tinker with".

As for the DVR part... doable, but very complex, needs specialized hardware (capture card), and your cable company is going to do their d***dest to make it difficult for you - you won't be able to get pay-per-view on your DVR, and you likely won't be able to get HD channels either.  SERIOUSLY consider saying "the heck with it" and either just renting the cable company's DVR... or bypassing the cable company entirely, and just watching video off Hulu and Netflix.  (DISPLAYING video is easy... RECORDING video is what's hard.)

The rest of the stuff is simple by comparison: Samba for filesharing, you already said you plan to use ushare for your uPNP server for the x360, LAMP for the bloghosting (psst: WordPress for the actual blog app), rsync for the network backup.

---

### Post by ushills on 2010-03-20
> **jrssystemsnet said:**
> By far the hardest tasks on your list are the DVR and the firewall/router.

Unless you just really REALLY want to do it to flex your "nerd nuts", you're almost ALWAYS better off letting a cheap SOHO router handle your firewall/router needs.  It's cheap, you probably already have one anyway, it has no moving parts, generates less heat, and has a far lower mtbf than your PC as hardware... much less your PC as "a thing you like to tinker with".

As for the DVR part... doable, but very complex, needs specialized hardware (capture card), and your cable company is going to do their d***dest to make it difficult for you - you won't be able to get pay-per-view on your DVR, and you likely won't be able to get HD channels either.  SERIOUSLY consider saying "the heck with it" and either just renting the cable company's DVR... or bypassing the cable company entirely, and just watching video off Hulu and Netflix.  (DISPLAYING video is easy... RECORDING video is what's hard.)

The rest of the stuff is simple by comparison: Samba for filesharing, you already said you plan to use ushare for your uPNP server for the x360, LAMP for the bloghosting (psst: WordPress for the actual blog app), rsync for the network backup.

I would suggest myth server as a backend for myth but agreed that this should be a seperate box, drive access and speed is critical and needs a high spec machine for recording and passing to a myth frontend.

---

### Post by HermanAB on 2010-03-20
Hmm, you could do it all on one machine, but the problem is that once you installed something complex like DVR, then installing something else may break it.  

So the best way to experiment is on multiple machines and for the dollar challenged, the trick is to use Virtualbox or Vmware to keep things separated.

---

### Post by Vegan on 2010-03-20
Like many, I have a Linsys box, so it gets the firewall job.

I use a standard LAMP stack, plus many programming languages.

SAMBA is my sharing tool to make using Windows feasible to edit the various web sites. The root disk is large so I use a share for general storage.

Additional tasks like PVR are dealt with on the Windows box. I have a Windows 7 x64 Ultimate license so I am not hard up.

Linux is fine as we web appliance, but more hardware is needed for the OPs desire. No machine is god.

---

### Post by abyrne on 2010-03-20
When you say "Wii File Sharing", do you mean a softmodded (aka homebrew) Wii? I'm not saying that thats bad. In fact i softmodded my wii too :P . Most developers of Wii homebrew use samba for any filesharing. And if your using Win7 (I think you need a certain edition), its backup can also be done through samba, which windows just sees as another windows box. And there is a huge amount of backup applications for linux. And filesharing is done through, you guessed it, Samba. So really 3 of your tasks can combined into one. Just use 3 different shares.

I agree with the others on the DVR and router. Unnecessary. Router can be pulled off with a $40 linksys, DVR can be pulled off with a TiVo or your cable provider's DVR box, if availible.

Other than that: Tons of BitTorrent clients have web interfaces. I perfer Transmission. A blog can be pulled off with Wordpress (i think, dont quote me here. I'm not into blogs ;) )   

All done! Your super-server is complete! Good luck

---

### Post by duramaxx2003 on 2010-03-20
Hey guys thanks for the info. Im ditching the dvr idea. Gonna look into external drive to give cable company dvr more space.(yea more research) 
I am running a WGT 624 v3 with latest firmware. Wondering how secure is it and if it isnt can i run a firewall behind it to help it out?

---

### Post by ApEkV2 on 2010-03-20
> **jrssystemsnet said:**
> you're almost ALWAYS better off letting a cheap SOHO router handle your firewall/router needs.

Do not get a cheap router, it doesn't pay off.
I bought a cheap linksys and it craps out when I run Tor with over 100 established connections.
You get what you pay for...in most cases.

---

### Post by emyr42 on 2010-03-20
> **duramaxx2003 said:**
> Hey guys thanks for the info. Im ditching the dvr idea. Gonna look into external drive to give cable company dvr more space.(yea more research) 
I am running a WGT 624 v3 with latest firmware. Wondering how secure is it and if it isnt can i run a firewall behind it to help it out?

Is that a Netgear? I've had good times with the DG834 series, flashed with open source firmware. There might be a similar project for your router...?

---

### Post by duramaxx2003 on 2010-03-20
I have looked into tomato, dd-wrt, and openwrt. Nobody build for netgear wgt624. ANybody have any ideas for some software modding for my netgear. Do ya think its is better left alone.

---

