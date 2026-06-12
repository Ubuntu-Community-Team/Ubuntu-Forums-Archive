---
title: "Now's your home network setup?  Need suggestions for a new house."
date: 2010-05-25
forum: The Cafe
---

### Post by samalex on 2010-05-25
Hi,

We recently had a house built and I had all the coax and cat 5 (broadband and phone) run into a single box in the house.  Unfortunately Time Warner still isn't available, though they should be out in a couple of weeks, so I'm starting to plan the network so it's ready when I get Internet connectivity.

Just curious, how do others have their home networks setup?  Is it simple with a cablemodem to a wireless router?  Or do you have an elaborate setup?  

Here's my basic layout:
```

--[Wiring Closet]--------------------
[Time Warner Cable Modem]
            |
[Linksys Wireless Router]
-------------------------------------
     /            \
{Wired Network}    {Encrypted (WPA) Wireless Network}
      |                 |
 [Bedrooms]         [Laptops]
 [Living Room]      [Nintendo Wii]
 [Office]
 [External Server - Linux (DMZ)]
    -HTTP, SSH, VPN
 [Internal Server - Linux]
    -Backups, Test HTTP, MP3 storage, Firefly Media Server
 [Skype server - Windows XP]
    - Connect to Skype via [USB Phone Adapter for Skype]("http://www.amazon.com/gp/product/B000JCU88S") and 
      tie into second twisted pair of phone lines.

```
The main reason for a wired network is because backing-up over wireless is WAY slow when you have lots of data.  Plus even though I like the portability of wireless I like the idea of having an internal network that I can connect to for desktops, cable box, etc.

How do others do it?  Also any pictures of your home setup or wiring closet?  Also any future projects?  Also any suggestions on how to tweak or better organize what I've typed up here?

Thanks for sharing your set-up and maybe giving some ideas since I'm still at ground zero of setting-up my network in the new place.

Sam

---

### Post by Swagman on 2010-05-25
Like [** THIS**]( http://www.upload3r.com/serve/250510/1274802331.jpg)

That's a netgear 4 port router into a 16 port feeding 5 machines in all rooms

---

### Post by Grenage on 2010-05-25
If money is no object:

Wall-mount rack cabinet, rack-mounted switch and a patch panel.  Pattress network boxes in each room.

If like most of us, you're not flush:

Terminate and plug your cables into the wifi router, plug the router into the modem and call it a day.  It's normally very simple; most plain routers will have a WAN uplink port to use for the modem.  This is usually auto-MDIX, but if not you use a crossover cable.

---

### Post by CharlesA on 2010-05-25
My current set up is Cable Modem - Router - Switch - Wired LAN.

My dream setup is Cable Modem - Router - Switch - Patch Panel - Wired LAN.

As of right now, I am doing the the same setup minus the patch panel. 1 connection from router to 8 port gigabit switch, where if I had a patch panel, it would be patch panel to switch to router.

---

### Post by skierkyles on 2010-05-25
Heres mine....
[IMG]http://i49.tinypic.com/2s94tu0.png[/IMG]
Edit: I guess Access Point would probably be better terminology for the Wireless Routers because they are not serving IP addresses.

---

### Post by Joe of loath on 2010-05-25
> **skierkyles said:**
> Heres mine....
[IMG]http://i49.tinypic.com/2s94tu0.png[/IMG]
Edit: I guess Access Point would probably be better terminology for the Wireless Routers because they are not serving IP addresses.

Just out of interest, why 2 AP's? Range issues?

---

### Post by doas777 on 2010-05-25
one minor recomendation is to place the public facing server on the outside of the wifi router, in a true DMZ, rather than using your routers port direction. it takes an additional router however.

---

### Post by juancarlospaco on 2010-05-25
OMG!
**sudo apt-get install dia**
ASAP

---

### Post by Dragonbite on 2010-05-25
Mine's pretty basic

```

               {{ internet }}
                     |
                     |
                [ DSL Modem ]
                     |
                     |
                [ IPCop ] (Firewall,Router & Content Filter )
                     |
                     |
          [ Wireless Router ] (Linksys, 4 ports & wireless, firewall)
                 /   |   \
                /    |    (wireless) - - - << laptop(s) >>
               /     |
              / << home desktop >>
             /             \
        [8-port Switch]     \
              |         [shared printer]
              |
     << file/web server >>
  ** systems being developed **

```
The Systems being developed includes[LIST=1]
[*]replacement web server running on Ubuntu 10.04 LTS
[*]backup server for all systems to backup onto, with plans of having this one system backup to CrashPlan online backup (for $50/year)
[*]possible media server to hook up to the TV
[/LIST]

This way, *ALL* Internet traffic runs through the content filter. So if any of the kids friends try coming to the house and connect via wireless (netbook, iPod, etc.), or run a LiveCD/USB to try and bypass local system's filtering/etc. it still will be filtered.  Only by physically remapping the wires will counter it.

So I need to get a cage to put it in so they can't do that ;)

---

### Post by juancarlospaco on 2010-05-25
OMG!
Dont use Hub, Get Switch 
ASAP

---

### Post by Dragonbite on 2010-05-25
> **juancarlospaco said:**
> OMG!
Dont use Hub, Get Switch 
ASAP

Actually, it is a switch. I corrected the diagram, thanks!

---

### Post by skierkyles on 2010-05-25
> **Joe of loath said:**
> Just out of interest, why 2 AP's? Range issues?

Well I needed a switch for the desktop near AP #2 because I occasionally have my laptop wired to it, and the only thing I had was wireless, so I figured I might as well have another AP.

---

### Post by samalex on 2010-05-25
Hey Guys --

Thanks for the replies.  I already have a 14"x14" Leviton wiring box with a punchdown for phone, broadband, and a splitter for coax, and power is ran to the box.  There's not enough room in the box for my cablemodem and a larger router, so I'm thinking of going with the [Leviton router]("http://www.leviton.com/OA_HTML/ibeCCtpSctDspRte.jsp?section=23734") or [switch]("http://www.leviton.com/OA_HTML/ibeCCtpSctDspRte.jsp?section=23735&minisite=10028") that just plugs into the box.  If I used the switch I'd run everything to the Linksys router to take care of the firewall.  

As for putting the external server as a true DMZ, I really don't want to have two routers, so using the DMZ feature of the router is the simplest way. 

Also the point of all this is to have it functional and clean.  Back when I was single I had the room full of monitors and network equipment, and the more the better.  But now that I have a family and kiddos I want to keep it as compact as can be.  The closet is small, though there's plenty of room for a few smaller, low powered servers (no ventilation when door closed).  SO nothing too grandiose.

I'll take some pictures when I get it setup, but it may be a week or two since I'm waiting for Time Warner to come out and tie me into their network before i finish-up a few things.

Sam

---

### Post by CharlesA on 2010-05-25
Gigabit router would work, If you've got a patch panel, you'd need a switch as well.

---

### Post by Old_Grey_Wolf on 2010-05-25
You hardwired the house. Did you run the cat5 through conduit? I hope so. 

When I was young, I helped my father build his weekend home. It was before there was an Internet. We planned on a sound system; therefore, we used conduit to construct a network of connection boxes in every room in the house. When he was ready for the sound system, we pulled the wires through the conduit, set up the central sound system, and remote speakers. Later, Internet came along. All we had to do was pull the cat5 wire through the same conduit. No cutting holes in the walls, fishing wires down the hollow spaces in the walls, and no crawling in the attic. 

My father died years ago, and I have sold the house. However, I keep thinking that in a decade or so, when fiber in the home may replace cat5, it would be easy to run the fiber though those same conduits.

My father was an Architectural Engineer, and knew from years of experience that the use of a building changes over time. So he designed his weekend home to be flexible. I learned a lot from him.

---

### Post by skierkyles on 2010-05-25
> **Old_Gray_Wolf said:**
> Did you run the cat5 through conduit?

That is a fantastic idea. :)

---

### Post by samalex on 2010-05-26
> **Old_Gray_Wolf said:**
> You hardwired the house. Did you run the cat5 through conduit? I hope so. 

The builder ran the existing lines (all Cat 5 for phone/ethernet and Coax for TV) through holes in the studs that were sealed, but there's a second conduit running from the box to the attic that I can use to drop more cables as needed.  I asked that all cables be ran through two conduits instead, but for whatever reason the electrician did it this way.  Only sucks if one of the current cables needs to be replaced for some reason... but thus far it's working fine.  

My only regret is that I didn't ask that the cabling box be moved closer to the garage or maybe even in the garage.  For now it's in the back of the house, so to get to it I have to crawl over TONS of A/C duct work and hopefully not fall through the roof :-/  

Sam

---

### Post by pwnst*r on 2010-05-26
> **Joe of loath said:**
> Just out of interest, why 2 AP's? Range issues?

He may be doing what I do.  I have a second WRT54GL that is running DDWRT in client mode.  It sits behind my 55" LCD so it's hidden and my Xbox360 and PS3 are both wired to it.  There is no ethernet port in the living room, but there is in all three bedrooms.  I'll be taking care of that this fall.

---

### Post by samalex on 2010-05-26
> **pwnst*r said:**
> He may be doing what I do.  I have a second WRT54GL that is running DDWRT in client mode.  It sits behind my 55" LCD so it's hidden and my Xbox360 and PS3 are both wired to it.  There is no ethernet port in the living room, but there is in all three bedrooms.  I'll be taking care of that this fall.

In our old house I ran cat5 to behind the TV and had a hub for DishNetwork, XBox, and a few other devices, so when we had the new house built I asked for the same thing there.  For now it's wired for phone, but given it's cat5 I can switch it to broadband easily enough.  

I called Time Warner earlier this morning to get an update, since that's the hold-up, and it's still in the 'construction phase'.  They've had a TW box in our yard for a few weeks now, but the neighborhood isn't connected to their network yet.  It's a new division, and it sucks because the folks three houses down have Time Warner but we don't.  Maybe soon.

Sam

---

### Post by LowSky on 2010-05-26
Here's my setup. 

```

               {{ internet }}
                     |
                     |
                [ Cable Modem ]
                     |
                     |
          [ Wireless Router ] (D-Link, 4 ports & wireless, firewall)
            /    /   ||   \
           /    /    ||   (wireless, Encrypted WPA2) - - - << laptop(s), Phone(s) >>
          /    /     ||
     <<PS3>>  / <<2 desktops>>
             /             
     <<HTPC/File Server>>
            |        
     [shared printer]



```

---

### Post by pwnst*r on 2010-05-26
> **samalex said:**
> In our old house I ran cat5 to behind the TV and had a hub for DishNetwork, XBox, and a few other devices, so when we had the new house built I asked for the same thing there.  For now it's wired for phone, but given it's cat5 I can switch it to broadband easily enough.  



Which is my plan in the fall.

---

