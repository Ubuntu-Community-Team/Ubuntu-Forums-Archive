---
title: "Due to Hurricane Sandy, some US Ubuntu Mirrors may not be accessable"
date: 2012-10-29
forum: The Cafe
---

### Post by sandyd on 2012-10-29
Due to Hurricane Sandy, some of the data links, datacenters, fiber cables, and/or core/routers in New Jersey (especially New York) are currently down due to flooding. Many datacenters are currently unable to operate due to their basement (and the power generators that reside inside them) flooding. As a result, people with routes to us.archive.ubuntu.com that run through any of the affected locations may find themselves unable to connect. Your ISP should have rerouted around NYC, but some havent.

This does not only affect people close to any of the flood areas/cities, as your data passes through those very datacenters and connections that are now damaged/flooded

The bandwidth providers, and the datacenters are aware of this, but there is no ETA on a fix, as water getting into electronic equiptment causes lots of damage, and you can't fix anything when there is 5 feet of water in the basement.

If you experience problems connecting, switch to the 'Main Server' or other mirrors by opening the Ubuntu Software Center, going to Edit -> Software Sources -> Ubuntu Software.

You can change the mirror there to 'Main Server', or something else while the hurricane continues

Here is an example traceroute that shows an affected link: [http://paste.debian.net/204830](http://paste.debian.net/204830)

Major Datacenters Offline: [Internap&Peer1@75 Broad]("http://pastebin.com/9Fr2eW6U"), [Datagram]("http://www.datagram.com/"), [Steadfast]("https://support.steadfast.net/News/NewsItem/View/397/full-nyc16-power-outage"), and many more.

Widespread outages on Verizon, AT&T and Windstream, so online datacenters may have issues connecting as well.

**Update**
Some of the datacenters have begun to pump water out of their basements, which means that some links will now be back online with generator power.

---

### Post by jerrrys on 2012-10-30
NYC is down :(

---

### Post by sandyd on 2012-10-30
> **jerrrys said:**
> NYC is down :(

That is because the fiber cables for Verizon and all other carriers are down due to flooding.

Many Datacenters have core routers and stuff inside for the carriers. If the datacenter floods like Datagram did, the fiber equiptment become dammaged. Some datacenters are not prepared for this level of flooding and/or water entering their basement or fiber connects. There are also datacenters that do not have the resources to run on generator power, or have damaged generators, and are unable to supply power to the links.

The links will also go down if water gets into the cable

Currently a lot the fiber cables in New York and Connecticut are offline, and many ISPs have already rerouted to alternate cities.

---

### Post by kansasnoob on 2012-10-30
Thanks for the heads up :)

I was doing some specific app testing for a proposed SRU and I stumbled into trouble. You've explained it so it's just time to chill out.

I certainly hope everyone back east stays safe and sound.

---

### Post by Paddy Landau on 2012-11-01
My sympathies to everyone caught up in that mess. Thanks for letting us know.

---

