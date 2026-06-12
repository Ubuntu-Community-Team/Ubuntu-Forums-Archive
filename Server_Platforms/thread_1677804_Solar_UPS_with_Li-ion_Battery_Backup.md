---
title: "Solar UPS with Li-ion Battery Backup"
date: 2011-01-29
forum: Server Platforms
---

### Post by fela on 2011-01-29
This is just an idea of mine: I run a server at home, and currently there isn't a UPS connected. We don't have problems as our power is very reliable, however we were recently thinking of (in the medium future) getting some photovoltaic solar cells for power generation.

My idea is this: get a Li-ion battery pack, connect it to the prospective solar cells, and use it as a constant backup power supply for the server - which I've measured to use about 50W. I'll say 60W to be on the safe side. The reason for a backup power supply is because I don't like having downtime on the server (the system runs quite a few services), and we sometimes need to turn off the supply to modify the ring main.

We already have a Li-ion battery rated at 30 amp hours at 24 volts, used to power a 500 watt motor at the moment. My calculation is this:

30Ah x 24V = 720 watt hours
720 watt hours / 60 watts = 12 hours

That means that according to my calculations, the battery that we already have could run the server for 12 hours. This is ample time for things like turning off the supply to install power sockets for example - and we've never had any power cuts that long (we've actually only ever had one power cut believe it or not).

My other question:

is it possible to keep Li-ion batteries charging **while in use**? If not, for my plan to work, I'd have to configure the system to disconnect the solar cells while the mains is up.

Thanks very much!!!
Fela

---

### Post by Vegan on 2011-01-29
UPS gear is abundant. For longer times without power, most use a diesel engine to replace the grid.

Most use cheap lead batteries.

Lithium tends to degrade rapidly.

---

### Post by fela on 2011-01-29
> **Vegan said:**
> UPS gear is abundant. For longer times without power, most use a diesel engine to replace the grid.

Most use cheap lead batteries.

Lithium tends to degrade rapidly.

My idea was to get a UPS *if* we do the solar panels idea (so diesel engine is out of the question). I don't have a massive need for a UPS at the moment.

Although, I hear what you're saying about the lead instead of Li-ion - maybe if we get the solar panels I'll look at that instead. Cheers :)

---

### Post by tgalati4 on 2011-01-29
The issue becomes the inverter electronics--they are expensive and only last a few years.

---

### Post by nitrogensixteen on 2011-01-29
If you are really into DIY there are DC-DC power supplies available for computers, so the inverter wouldn't be an issue, and should increase efficiency.

---

### Post by fela on 2011-01-30
> **nitrogensixteen said:**
> If you are really into DIY there are DC-DC power supplies available for computers, so the inverter wouldn't be an issue, and should increase efficiency.

That sound's awesome :D And I guess there would be a power brick transformer to go with it for plugging into the mains? Maybe I'll look into that...

> **tgalati4 said:**
> The issue becomes the inverter electronics--they are expensive and only last a few years.

Hmm, although if I found a good DC-DC PSU that wouldn't be a problem :guitar:

I've always found it intriguing that so many devices run on DC and yet the mains is all AC - I know that transformers are inefficient and it would be better to just have one big transformer going from say 240V AC to the same DC voltage, at the consumer unit?
I'm sure there are efficient ways of turning DC high voltage into DC high current using electronics, with minimal loss? Not like a transformer, where I've even heard some of it is lost as **sound**! :lolflag:

---

### Post by Vegan on 2011-01-30
I have seen 5000W inverters for cheap, so they are not a real problem. Batteries will be more costly as will alternate power.

5kW is enough for a standard house.

Cheap 5kW generators are readily available for under $1000, with better models always hoping for a sale.

Once enough batteries are installed, wind, solar and alternate sources can all supply 12V to keep the batteries charged.

Diesel is durable but very expensive. Wind and solar have some potential but they are also costly.

---

### Post by fela on 2011-01-30
> **Vegan said:**
> I have seen 5000W inverters for cheap, so they are not a real problem. Batteries will be more costly as will alternate power.

5kW is enough for a standard house.

Cheap 5kW generators are readily available for under $1000, with better models always hoping for a sale.

Once enough batteries are installed, wind, solar and alternate sources can all supply 12V to keep the batteries charged.

Diesel is durable but very expensive. Wind and solar have some potential but they are also costly.

Hmm, I wasn't looking at getting a UPS for the whole house, lol. Or did you mean, I could get a 5kW inverter and install it at the supply for use with DC appliances such as PCs/the server? That would be kind of beside the point in this case because the original idea was to feed the server off the prospective solar panels. Basically the updated idea is:

Have solar panels feeding the grid as well as an array of lead acid (instead of Li-ion) batteries totalling ~0.75-1kWh of storage.

These batteries would feed the server if the mains went down (oh and to use the server with just the mains with the DC-DC PSU, I'd have a transformer power brick like on a laptop)

---

