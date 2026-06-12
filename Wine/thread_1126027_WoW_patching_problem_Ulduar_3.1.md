---
title: "WoW patching problem Ulduar 3.1"
date: 2009-04-15
forum: Wine
---

### Post by Mat 339 on 2009-04-15
Hi I'm downloading installing the new patch 3.1  through wine but it is incredibly slow I'm at 55% now started it about 7 Hours ago.It says that my computer appears to be behind a firewall but I can't seem to figure out what or where it is to disable for the time being.

I read that it is iptables but I can't find the program to disable it,or is there a program in Wine that acts like a firewall?I'm very new to Ubuntu and linux so I apologise for being such a noob =)

---

### Post by Mmmbopdowedop on 2009-04-15
If you're using a router, then this may help (from Blizzard's site);

> If you are using a firewall or router, be sure that port orts 6112, 3724, and 6881 through 6999 are open and forwarded to your computer and only your computer. You may need to refer to your firewall/router's documentation for instructions on opening ports and setting up port forwarding. Also, make sure that no other programs that use bandwidth are running while attempting to use the Blizzard Downloader.

But on a sidenote, I find the downloader sucks for me, you could try one of the mirrors here; [http://www.wowwiki.com/Patch_mirrors](http://www.wowwiki.com/Patch_mirrors)

There's a few direct links, though, as it is patch day, chances are they're all getting hammered around this time anyhow.

I've never had any problems with Wine and a firewall, but i'm pretty much a noob too, just thought i'd throw these links out there.

---

### Post by TimothyLuke on 2009-04-15
I had the same prob this morning when I went to work.  (I just left it and hope it will be finished by the time I get home.)

What I noticed was that in the Blizzard Downloader Log, it didnt recognise my Billion Modem/Router/Firewall as a UPNP device.  

Windows sees this device and lists it as a UPNP Firewall that it can interact with.  The Blizzard Downloader under Windows then opens the appropriate ports and plays nicely.  [SIZE="1"]I know its not the solution but hopefully someone else will be able to make use of this info in creating a solution.[/SIZE]

---

### Post by rJ~ on 2009-04-15
Have you tried disabling peer-to-peer transfer (view -> preferences)? I find the Blizzard Downloader completely chokes out my connection through excessive upload if it's not restricted.

I don't think you will get top speed from the HTTP mirrors that the downloader uses, but it's faster than 7 hours at least.

---

### Post by hikaricore on 2009-04-15
Your best bet is to just download from the patch mirrors section on WoWWiki anyway, it's quicker and easier.

---

### Post by johnl on 2009-04-16
I also found that if I started the downloader, it generated a "BackgroundDownloader.torrent" file in the ${Wow}/Cache/ directory.  I opened this with the transmission bittorrent client, saved it to my WoW directory, and it worked fine.

---

### Post by Z0014ND3l2 on 2009-04-16
I had the same problem last night and what I ended up doing was following this [http://ubuntuforums.org/showthread.php?t=973060](http://ubuntuforums.org/showthread.php?t=973060) and by the time I finished adding the ports to the exception list the download was complete.

---

