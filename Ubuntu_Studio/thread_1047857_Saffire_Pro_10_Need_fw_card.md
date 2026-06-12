---
title: "Saffire Pro 10 Need fw card"
date: 2009-01-22
forum: Ubuntu Studio
---

### Post by otz070 on 2009-01-22
After 3 years I finally got a multi channel interface (For Christmas:D)
Unfortunally I have come to find that my new computer a compaq v6000 sucks terribly hardware wise (Enter Ricoh curse) So After finding and researching that express cards for it are around 60$ I give up. 
Fortunally I have another computer an old hp (520n) from when Hp made good stuff (came with 512 ram back in 2002!!!) Yes I know It's terribly old, but I hate to give it up because It seems to serve quite well.

[COLOR="SeaGreen"]So I now need to find a pci firewire card for it that works without breaking the bank. Under 20$-25$[/COLOR]

I heard TI chips work better than via so I think I will go with that.
But since there are nearly 200million choices out there can anyone name a good brand or more specificly a particular card?

(Yes I am already aware of all the various cavaets of firewire cards. I read the pages on ffado and the trouble shooting guide on focusrite. So you need not waste time explaining these things. All I simply need Is a card that works and works good.:D)

In the meantime Fortunatly I have my Art Dual Pre To get me by. But for those More complex multi channel routing operations........

Thank You for any suggestions Ideas ect.:D

---

### Post by otz070 on 2009-01-22
Update:

Just thinking out of curiosity (as the old hp desktop has a fw card already)
I went to check the chipset---> Its a TI (Belkin Card) 
I have hooked the Saffire 10  up to that card with no luck either (Using Win Xp home) So now I am just hoping Its just simply a windows being stubborn issue. I hope I don't Have to RMA It. I'm Downloading a 32bit ubuntu Iso To install on there So hopefully gscanbus will dectect It. Otherwise Looks Like I might have gotten A defective unit Maybe.:(

---

### Post by otz070 on 2009-01-27
Ok My old computer up and running Intrepid 32bit...(Using to make this post;))

Gscanbus gives me this:```

:~$ gscanbus
couldn't get handle: No such file or directory
This probably means that you don't have raw1394 support in the kernel or that
you haven't loaded the raw1394 module.
```

Also searched google found and tried this/and got this
```
:~$ sudo chmod a+rw /dev/raw1394 
[sudo] password for owner: 
chmod: cannot access `/dev/raw1394': No such file or directory
```

Finally Just in case My firewire Is:
```
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB12LV26 IEEE-1394 Controller (Link)
                vendor: Texas Instruments
                physical id: d
                bus info: pci@0000:01:0d.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3 module=ohci1394

```

Any thoughts?
Thanks;).....

---

### Post by kayosiii on 2009-01-29
try adding raw1394 to your /etc/modules file this will force loading of the module at startup. also try the card in other pci slots if you haven't already and make sure it doesn't need additional power (I know some of the belkin combo cards do)

---

