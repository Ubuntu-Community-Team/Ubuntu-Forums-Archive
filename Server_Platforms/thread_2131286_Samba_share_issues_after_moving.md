---
title: "Samba share issues after moving???"
date: 2013-04-01
forum: Server Platforms
---

### Post by Delarth on 2013-04-01
I recently moved houses and prior to the move everything on my network was working fine. I could access my network shares from any computer on the network with relative ease. The server has been shutdown and restarted before along with the router so I know its not something that was just patched together and broke upon being shutdown. I installed no updates about a week or so prior to moving and haven't done so since. After getting everything over to my new place I got everything unpacked and hooked back up and then the trouble began.

Whenever I attempt to access any of the shares from my computers they take an eternity to load and I have no clue why. I've tried different cables and ports on the router and even deleting the mapped network drives and remapping them but none of that seems to work. I have tried reflashing the router's firmware and rebooting everything but still end up back at the beginning. I can ping the server just fine and access it via puTTy. I'm pretty sure the issue lies somewhere within samba or maybe something else on the server because the loading issue persists across every computer on my network. I've even tried to access the shares via my Droid and I have the same loading issue.

I've tried to use Wireshark to see if I can figure out anything. I see a ton of Tree Connect, Tree Response, and Tree Requests. It seems to be attempting to access the same share and going through multiple attempts to access it over and over again. These persist every 5 seconds or so and then after about 5 to 10 minutes there is a huge flood of traffic with anywhere from 50 to 200 lines of traffic appearing in under a second. After this the folder within the share will either open or fail to open and I will be left sitting within the parent folder. Occasionally I see some resets and a few duplicate ACK frames


Devices:
The server: Ubuntu Server 12.04 LTS
The computers: Windows 7 Pro
Router: Linksys with Tomato 1.28 firmware



Edit: After shutting the server down for a few days and then turning it back on I was unable to connect remotely. Upon connecting a monitor to the server I was able to see that in fact one of the drives was returning SMART errors. After disconnecting that drive I was able to access all of the other shares just as quickly as I was before. So in the end I guess it turned out to be a hardware problem that just manifested itself at a really bad time.

---

