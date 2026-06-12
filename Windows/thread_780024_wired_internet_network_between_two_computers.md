---
title: "wired internet network between two computers"
date: 2008-05-03
forum: Windows
---

### Post by wwzulu on 2008-05-03
Hello everyone!

I 've been having a hard time setting up my home network with the prime purpose of sharing my internet (and multiplaying Heroes 3) between my desktop and brand new laptop. You might be thinking why not wireless but I tohught I'd try wired first. It should have been easy but it proved not so. I have ADSL modem (my provider might be limiting me in some way but not sure i.e. number of computers that can suse that connection). Anyway, here's what I did:

1. Got a second ethernet adapter (Repotec RP-1624WK), crossover cable
2. Followed these steps:
-right click on the original ehternet card (the one connecting the desktop to internet)>>Properties>>in the Advanced tab I checked "Allow other network users to connect through this 
computer's Internet connection">>OK>>Close
- went to the newly added ethernet card (LAN 3 int the screenshot) Properties>>TCP/IP>>Configure >>IP 192.168.0.1, Subnet Mask: 255.255.255.0, Default Gateway &#1080; DNS Servers left empty>>OK
-Laptop: LAN >>Properties>> IP Address: 192.168.0.2, Subnet Mask: 255.255.255.0, Default Gateway: 192.168.0.1, DNS Server: 192.168.0.1 >> Ok > Close.
- Restart both computers
3. Nothing happened ... Well, the laptop LAN connection says it's connected (and sending some packages but receiving none) but the newly added ethernet says: A network cable is unplugged :(

4. I turned off both firewalls - nothing
5. I did have VMware player (which had 2 software cards in the network bridge) and Hamachi too but even after uninstalling these nothing happened.
6. I removed LAN 3 from the bridge - still same message

Screens:
[[img]http://xs227.xs.to/xs227/08184/clipboard02418.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs227&d=08184&f=clipboard02418.jpg)

[[img]http://xs227.xs.to/xs227/08184/clipboard021933.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs227&d=08184&f=clipboard021933.jpg)

What should I do? I am really frustrated ..Please HELP!

---

### Post by Aearenda on 2008-05-03
Not all network interfaces will work properly with crossover cables. 

Turning on connection sharing should have set your other interface's ip address automatically - you shouldn't need to do it; and the laptop should be given an ip address automatically by the desktop, so you shouldn't need to set anything manually there either.

What is the IP address of the original interface? (from right-click->status or the 'ipconfig' command)

EDIT: just saw your screen shot (it loads really slowly here). It's showing a bridge. I don't think you should be bridging the cards with local-only static IP addresses. Best to remove the bridge, turn off internet connection sharing, set the laptop to use dynamic addressing and DNS, then turn on internet connection sharing again, and see what happens.

---

### Post by LaRoza on 2008-05-03
You might want to get a router for this.

---

### Post by fiddledd on 2008-05-03
Years ago I used an XP box as a Gateway (an old PIII 500mhz actualy) using ICS, all other boxes on the LAN used it to connect to the Internet. But I used a Hub to connect all the boxes together and it worked fine for years. But eventually I got smart and got a Modem/Router so I retired the PIII box. I guess I could have just typed "What the last Poster said" but I was looking for something to do :)

btw, here might help [http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

---

### Post by wwzulu on 2008-05-03
Thanks all for your replies so far :) .... I did try Aearenda's suggestion and at first it didn't work. Then as I saw the problem was definitely about this message "network cable unplugged" I opened my box and rubbed the contact space of my second ethernet with a pencil eraser ; instaled it back in and ... voilla ... dunno what happened but it worked :lolflag: .I tweaked some firewall settings and there you go - I have i-net on my laptop. 

@LaRoza and fiddledd: I know what you suggest is a much smarter option but I just didn't want Windows to win :) and also I am on a low budget so this solution is best for now.

All that's left now is to be able to start my multiplayer Heroes 3 game with my wife :)) ... It still displays an error message although the laptop game does "see" the created game by the desktop host to which it should join ... Report back later ;)

edit: Wow, you guys are fast on responding -->> Thanks a bunch!!!

---

