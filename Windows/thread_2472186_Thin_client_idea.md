---
title: "Thin client idea"
date: 2022-02-20
forum: Windows
---

### Post by fiveeyed on 2022-02-20
Hi everyone, so my work recently got a  new server and a bunch of thin clients to put through out the factory to make file access simpler across the site. While playing around on the system, I realized it was basically doing what I eventually want my home system to do, minus a couple of features here and there. Eventually my goal is to set up one server for my whole house and have a bunch of thin clients in other rooms running off the much more powerful system. The primary use will be general computer access around the house, word documents, web surfing, video streaming. However I also would like the option to have my 3090 installed on the server (possibly a second one if needed) and use it to game on one or at most 3 of the thin clients at any time. The idea would basically be like Linus's 7 gamers 1 cpu , actually looking at it I guess it would be exactly like what they did there. The only difference I can see is that I would like to have the ability to run my thin clients with either and instance of ubuntu for general/everyday usage and also be able to access a windows session on the server for gaming. Is there an easy way to do this? (if there is an obvious answer I am mission, I appoligize in advance this is not an area of computing I have spent much time in, thin clients and virtual machines that is. )  

p.s. this isnt a current real issue, this is more of a thought experiment / future goal type thing. Just curious to know how one would handle such a use case.

---

### Post by TheFu on 2022-02-20
No, it is not easy.
Your thin clients will need to support a proprietary GPU network layer.
If you remove the gaming and wifi as requirements, it is trivial and Unix/Linux has been doing this for 30+ yrs using standard X11 capabilities.  That's for LAN.
If you want remote WAN access for productivity software, then check out x2go or any NX-based client-server setup.  VNC/RDP are jokes in comparison. They are 2-3x slower.

LTT setup 3 different VMs and used a $10,000 server with 3 powerful GPUs.  Are you planning to do that? I think he also used $3000 in fiber connected video connections.

1080p video streaming is best to as client-side processing where the client handles all the video decoding. This has been available for a decade using DLNA, if you don't want to use proprietary protocols.  CIFS access to storage for streaming media has been problematic in many situations.  Use NFS, the native Unix network file system. There's something about the way that NFS works which makes media access faster. I don't know why and neither do the KODI guys, but it just works that way.  I've had the DLNA and NFS setup with a raspberry pi v2 for playback at home for a long time. Over 5 yrs. My media server was a $50 Pentium CPU from 2015 until last fall. That same CPU was running a number of VMs (wallabag, ZNC, nextcloud, calibre) concurrently with plex, jellyfin and mpd. It only had 8G of RAM. The only reason for my upgrade to a newer computer was for some other VMs I wanted to spread more evenly, not because there were any performance issues with the stuff on the box already.

I saw an update that let's raspberry pi v4 systems have access to nvidias proprietary network GPU stuff. [https://www.makeuseof.com/tag/stream-pc-game-tv-raspberry-pi/](https://www.makeuseof.com/tag/stream-pc-game-tv-raspberry-pi/) That will allow gaming from 1 client. 
> Setting up Parsec on your gaming PC and Raspberry Pi, meanwhile, overcomes hardware and Steam limits. You can literally play and stream any PC game!

This entire area is rapidly changing.

For Linux, we needed another GPU to be used on the server. These GPUs need to be setup for exclusive access.  Someone relatively new to Linux reported a few days ago that he got GPU passthru working on a Proxmox VM host. I think he was really lucky with the hardware he happened to get, so it had the required capabilities necessary.  I've never had a system with more than 1 GPU, but I do passthru to a VM a PCIe NIC for security reasons.  That NIC is exclusive to one VM. No other VMs or the host can access it.

All of that may have changed. IDK.

In a work environment, I'd dump Windows and setup light clients using browser-only document access.  A clone version of ChromeOS tied into a central server running Nextcloud + OnlyOffice would be a first step.  The client really wouldn't matter, so Linux, OSX, Windows, Android, iOS can all be supported.  Clearly, a raspberry pi with old keyboard, mouse, and monitor would probably be the cheapest to get and run long term.

You can also check out LTS - Linux Terminal Server. [https://ltsp.org/](https://ltsp.org/) This basically runs xdmcp with clients connected into the server, all on the same OS instance concurrently. 5-20 clients should be easy on almost any x86-64 hardware today. It is highly network sensitive. They recommend wired GigE for all clients and the server with at last 800Mbps solid. That usually means wifi will be problematic.  

It is only Windows that creates the need for more expensive hardware. If you can dump Windows, a 5 yr old Core i5 (or similar performance) with 16GB of RAM will easily support 20 end-users concurrently doing office-type stuff. The LTSP says 4G RAM is recommended. I'd probably use 8G as the min adding 1-2G more for each client.  When different users run the same program inside the same OS, the amount of RAM used doesn't increase at all for the program or libraries, just for the data used by each user which remains separate.

Some other options besides Parsec [https://alternativeto.net/software/parsec/](https://alternativeto.net/software/parsec/)  I don't know anything about these. I don't game.  I  run programs on other computers here all the time, daily, right now.  Actually, this browser window is running on a VM in a machine in a different room. I'm typing on a laptop.  Normal X11 forwarding that has been included in ssh since the mid-1990s. Without ssh, it has been normal, probably since the mid-1980s.  [https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) explains the methods from 2010. The X11 stuff is still correct.

---

### Post by Tadaen_Sylvermane on 2022-04-05
To add to the LTS suggestion. They can also be run as fat clients. They can boot and run from the network but use the local hardware (i.e. video card, ram, cpu). I've run my desktop from it just fine with the full access to my RX570. The only difference is it's not nearly as quick as the local SSD drive. Works quite well though. This may solve your remote gaming idea while maintaining a single filesystem image to deal with. This also means the LTS server doesn't need to be the most powerful thing in the world. Since you are using local hardware it becomes little more than a file sharing system for all purposes. Currently I'm running 3-4 machines in my house at any given time. I think my only limitation with fat clients is network bandwidth.

---

