---
title: "[SOLVED] Low Powered Network Storage. Throw in some Ideas"
date: 2008-02-19
forum: The Cafe
---

### Post by Scarath on 2008-02-19
Hi

I have been thinking about getting some network attached storage to put all my DVD's and music on so they can be accessed from the various bits of hardware that are kicking around the house.

But I want his storage to be very low on energy consumption. I think I have 3 main options.

1. Buy some pre-build Network Storage. 
2. Use one of my old PCs to make a media server.
3. Use something like [this]("http://www.aleutia.com/") attach to a huge external drive.

Each of these has problems and benefits (infact I am unsure as to whether 3 would really work well although it would be very low on power usage).

Number 1 is expensive and I cant find any power consumption data on the network storage devices so they may use as much as a PC. Anyone know how much power these things use?

Number 2 is cheap and easy (lots of tutorials all over the net) but again, the lower consumption will be large, unless I can find a minimal power supply for tiny computers that could run an old media server??

Has anyone got any genius ideas as to how this sort of thing can be achieved with minimal power use?

cheers

Matt

---

### Post by benfindlay on 2008-02-19
Personally I use an bottom of the end P4 flat-pak type 'tower'. I've got a couple of external hard drives plugged in and samba sharing stuff. The Western Digital Mybooks (and other makes) power down when not in use, after a few minutes. This may be ideal for you, if power consumption is an issue. When in standby mode, they use very little power, and there is only a short delay (~5 secs) in powering them back up when accessed over the network.

Hope this helps!

---

### Post by dasunst3r on 2008-02-19
My dream low-powered network storage device:
[list]
[*]VIA C7 or AMD Geode board
[*]RAID1 hard disk configuration
[*]Debian Linux
[*]OS installed on flash memory card
[/list]
At that rate, I can purpose the server for whatever I want it to do.

---

### Post by Scarath on 2008-02-19
Thanks for the replies, glad to know most External drives go to standby. Although I have read some [odd things about mybooks]("http://www.theregister.co.uk/2007/12/07/western_digital_drm_crippled_harddrive/"), have you experienced any problems?


> **dasunst3r said:**
> My dream low-powered network storage device:
[list]
[*]VIA C7 or AMD Geode board
[*]RAID1 hard disk configuration
[*]Debian Linux
[*]OS installed on flash memory card
[/list]
At that rate, I can purpose the server for whatever I want it to do.


Some sort of thin client with external drives may be the answer. Those Geodes look impressive.

---

### Post by jimrz on 2008-02-19
I received one of [[COLOR="Sienna"]**_these_**[/COLOR]]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1118334819312&pagename=Linksys%2FCommon%2FVisitorWrapper") for Christmas and it is great. It is low power, dead simple to setup (basically just plug everything in and samba sees it straightaway) and works beautifully. I have 2x 500Gb  WD MyBook's (also low power consumption)attached and will likely retire my old home file server as a result. Also, if you are so inclined, the device is very hackable.

---

### Post by Scarath on 2008-02-20
> **jimrz said:**
> I received one of [[COLOR="Sienna"]**_these_**[/COLOR]]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1118334819312&pagename=Linksys%2FCommon%2FVisitorWrapper") for Christmas and it is great. It is low power, dead simple to setup (basically just plug everything in and samba sees it straightaway) and works beautifully. I have 2x 500Gb  WD MyBook's (also low power consumption)attached and will likely retire my old home file server as a result. Also, if you are so inclined, the device is very hackable.

Nice, that device seems to be just what I was looking for and it works with linux so w00t. 

Thanks for all the posts.

---

