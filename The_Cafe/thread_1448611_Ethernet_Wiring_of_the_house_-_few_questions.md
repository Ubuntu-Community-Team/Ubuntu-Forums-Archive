---
title: "Ethernet Wiring of the house - few questions"
date: 2010-04-06
forum: The Cafe
---

### Post by Kdar on 2010-04-06
Plan to do it tomorrow, got everything that I need today.

I picked up wall plates with two places for Ethernet jacks.

Can those jacks be connected by same Ethernet wire? like in series or something? or be split.. etc... (I am not sure if it is possible).

Or I need each wire (2 of them) to trace back to my garage, where I will have switch, router.. etc

---

### Post by handy on 2010-04-06
One cable per plug back to the switch in your garage is required.

---

### Post by sdowney717 on 2010-04-06
cant split Ethernet connections, the splitting is handled by a router.
I would guess you need to think of this like a radial web where it all ties back to a central router access point. You can link multiple routers together. They can either function as routers or a dumb hub.
When they work as a hub, you plug the outgoing LAN line from the main source router into the LAN of the second router and turn off DHCP on the second router.
Or you can plug it into the WAN of the second router and double NAT with DHCP on both. There is a lot of ways to link things up.

I have 2 wireless routers in my house. One is just acting like a hub. And it passes out the wireless connection just fine with WPA security.
Well actually 3 routers, one is a voip router.

---

### Post by jflaker on 2010-04-06
Unless your house is huge where you would be further than 150 feet from your access point, why not get a wireless router and enough wireless cards for your computers?

That way, if you decide to move your computer, all you need to do is *Move the computer*.

I have only 2 wired clients out of 6 computers because they are in the same room as the router.  The others are 2 rooms away and work great wirelessly and no holes in the walls.

Wires are great, but do not lend themselves to change very well....

Just a thought.

---

### Post by v1ad on 2010-04-06
its better to pull 2 wires. that way no setup hassle, and also faster transfer speeds between computers. wire needed? cat5, if money to spare cat6

---

### Post by Kdar on 2010-04-06
well, I will be building a server and HTPC, so I kind of want to have a direct connection.

Thanks for your replied, I will use two wires.

Does anyone know how far should I put my ethernet plugs from electrical plug? Somewhere I was reading it is 12".

---

### Post by v1ad on 2010-04-06
6" minimum if wires are side by side with electrical wires but they can cross when you pull. 12" preferred.

---

### Post by handy on 2010-04-06
If money is tight, Cat5e will allow you to use gigabit speed, providing your cable runs aren't too long.

---

### Post by Kdar on 2010-04-06
I think the longest run will be like 60ft

---

### Post by v1ad on 2010-04-06
your perfectly fine, the longest run that you could run is 300 feet. have fun pulling the wire.

---

### Post by CharlesA on 2010-04-06
Just be sure to use plenum-rated cable.

Are you going to go all out and get a patch panel, or just run them to a switch?

---

### Post by v1ad on 2010-04-06
plenum cable is more for commercial use and it is more expensive, the difference in plenum cable and regular cable is the shielding, plenum is not toxic so when it burns it does not release toxics.... if your house burns down i am sure you won't care.

and by the router i would just put a 2 port wall plate so you won't need two holes for wall plates.

---

### Post by CharlesA on 2010-04-06
> **v1ad said:**
> plenum cable is more for commercial use and it is more expensive, the difference in plenum cable and regular cable is the shielding, plenum is not toxic so when it burns it does not release toxics.... if your house burns down i am sure you won't care

It is part of building codes (fire codes too). I'd rather have cable that doesn't release as many toxins if there was a fire.

---

### Post by Kdar on 2010-04-06
> **v1ad said:**
> your perfectly fine, the longest run that you could run is 300 feet. have fun pulling the wire.

oh ok. Nice :)
Thanks. I am sure going to enjoy this little project.. then build server and HTPC and everything will be like I want :)

---

### Post by v1ad on 2010-04-06
> **CharlesA said:**
> It is part of building codes (fire codes too). I'd rather have cable that doesn't release as many toxins if there was a fire.

hmm that code applies for commercial only, or at least in California but for residential its personal preference, if he wants to fork that price, quite a hefty price difference. (pulled a lot of cat5 in commercial and residential work area's)

---

### Post by Kdar on 2010-04-06
> **CharlesA said:**
> Just be sure to use plenum-rated cable.

Are you going to go all out and get a patch panel, or just run them to a switch?

Yes. I got plenum. It cost a bit a lot... like $70 for 250ft... I hope it will be enough.

I probably will get patch panel, maybe it will be easier to install.
Maybe get this one:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16831101002&cm_re=patch_panel-_-31-101-002-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16831101002&cm_re=patch_panel-_-31-101-002-_-Product)

---

### Post by CharlesA on 2010-04-06
Patch panel looks good. Rated for gigabit speeds.

Have you thought about using a gigabit switch, or just your router being hooked up to it?

---

### Post by v1ad on 2010-04-06
for 2 cat5s ? 
let me give you the spec sheets
4 of [http://www.homedepot.com/Electrical-Voice-Data-Communications/Leviton/h_d1/N-5yc1vZ1xglZbm2cZwc/R-100020255/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053](http://www.homedepot.com/Electrical-Voice-Data-Communications/Leviton/h_d1/N-5yc1vZ1xglZbm2cZwc/R-100020255/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053)

2 of [http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100181794/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053](http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100181794/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053)

1 of by router [http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100117817/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053](http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100117817/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053)

save a bit of money and space.
i just have a habit of making everything at minimum space consumption and compatibility.

---

### Post by CharlesA on 2010-04-06
If you only have 2 drops going, might as well not bother with a patch panel. If you want to wire the whole house, you'd be better off to use a patch panel.

---

### Post by Kdar on 2010-04-06
well, no. 2 for each room.
Two per plug (per single wall-plate)

So 8 in total (for 4 rooms in my house... but I have other rooms which I might wire in future).


> **v1ad said:**
> for 2 cat5s ? 
let me give you the spec sheets
4 of [http://www.homedepot.com/Electrical-Voice-Data-Communications/Leviton/h_d1/N-5yc1vZ1xglZbm2cZwc/R-100020255/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053](http://www.homedepot.com/Electrical-Voice-Data-Communications/Leviton/h_d1/N-5yc1vZ1xglZbm2cZwc/R-100020255/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053)

2 of [http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100181794/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053](http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100181794/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053)

1 of by router [http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100117817/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053](http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100117817/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053)

save a bit of money and space.
i just have a habit of making everything at minimum space consumption and compatibility.

Yes, I got those.

---

### Post by Kdar on 2010-04-06
> **CharlesA said:**
> Patch panel looks good. Rated for gigabit speeds.

Have you thought about using a gigabit switch, or just your router being hooked up to it?

I might use switch.
Can you recommend me something?

---

### Post by v1ad on 2010-04-06
4 port wall plate, 2 port wall plate in rooms. you won't need a switch until you go more than 4. if you will go more than 4 just add a second wall plate by it and add a switch. the big patch panel is not really needed in my opinion. if you want to really hide it. get a leviton media panel and cut it into a wall install modem, router, switch in media panel. thats optional.

---

### Post by handy on 2010-04-06
> **Kdar said:**
> I might use switch.
Can you recommend me something?

HP make a nice 8 port gigabit managed switch, can't remember it's name, but it is what I will be using before too long.

A quick search will find it for you.

[I]**[Edit:]** This is it:

[http://www.superwarehouse.com/HP_ProCurve_1810G-8_8_Port_Switch/J9449AABA/p/1569199](http://www.superwarehouse.com/HP_ProCurve_1810G-8_8_Port_Switch/J9449AABA/p/1569199)[/I]

---

### Post by CharlesA on 2010-04-06
> **Kdar said:**
> I might use switch.
Can you recommend me something?

The one I am using is this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833127082](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127082)

It's unmanaged, but does support VLANs and whatnot. It's hooked up my my router (10/100) with a simple Cat5e patch cable. Internet network is gigabit tho.

---

### Post by Kdar on 2010-04-06
> **v1ad said:**
> 4 port wall plate, 2 port wall plate in rooms. you won't need a switch until you go more than 4. if you will go more than 4 just add a second wall plate by it and add a switch. the big patch panel is not really needed in my opinion. if you want to really hide it. get a leviton media panel and cut it into a wall install modem, router, switch in media panel. thats optional.

I will end up with 8 wires going into garage. and might me more if I will wire other rooms.

mmm.. I need to run all those wires to my garage right?

---

### Post by v1ad on 2010-04-06
its all personal preference. keep it in the same place where your modem will be in. and out of the way so you won't have to see it, or stumble over it. basically you will set it up and forget about it. if i did it for myself i would just run the wires through a open wall plate and put in cat5 connectors on the end. (rj45) but i have the tools.

---

### Post by cascade9 on 2010-04-06
> **jflaker said:**
> Unless your house is huge where you would be further than 150 feet from your access point, why not get a wireless router and enough wireless cards for your computers?

That way, if you decide to move your computer, all you need to do is *Move the computer*.

I have only 2 wired clients out of 6 computers because they are in the same room as the router.  The others are 2 rooms away and work great wirelessly and no holes in the walls.

Wires are great, but do not lend themselves to change very well....

Just a thought.

2nd option- powerline ethernet adapters, eg- 

[http://www.netgear.com/Products/PowerlineNetworking/PowerlineEthernetAdapters/HDX101.aspx](http://www.netgear.com/Products/PowerlineNetworking/PowerlineEthernetAdapters/HDX101.aspx)

Not that this helps the OP anymore, but I just thought I'd chuck this in as well.

---

### Post by Kdar on 2010-04-07
I bought those [http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100117817/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053](http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100117817/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053)
(total 4 of them, one for each room).

Or do you think I just should get those for each room?

[http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100181794/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053](http://www.homedepot.com/Electrical-Wall-Plates/Leviton/h_d1/N-5yc1vZ1xglZbm8mZwc/R-100181794/h_d2/ProductDisplay?langId=-1&storeId=10051&catalogId=10053)

---

