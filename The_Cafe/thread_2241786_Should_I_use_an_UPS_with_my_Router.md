---
title: "Should I use an UPS with my Router ?"
date: 2014-08-28
forum: The Cafe
---

### Post by linuxyogi on 2014-08-28
Hi,

Yesterday I requested my ISP to enable Auto Login for my account. It simply means that I am always connected unless I logout. 

I know that routers are meant to run 24/7. I have a so called "Home UPS". Its nothing but a sine wave inverter so it can easily run this router which afaik draws max 15 Watts on the AC side.

But as you know almost computer UPS systems has an inbuilt voltage stabilizer and some expensive ones has surge protection circuit built in.

Now my Home UPS may provide uninterrupted power supply to the router but its not going to do the ^^ above things.

Presently I am running my router with my UPS 24/7. In the past I had a chance of testing various electrical/electronic devices with an AC watts meter. When I tested my PC's UPS without any load I found that 
the UPS itself draws about 18 watts (constant).   

So, if I plug in my router directly to my Home UPS which simply another way of plugging it directly to the AC outlet, will that affect the router's longevity ?

---

### Post by TheFu on 2014-08-28
I plug all computing equipment into UPSes here (4 of them).  All power goes through the battery, so it is "conditioned" and all electrical spikes are handled.  router, switches, disk arrays, phones are all on UPSes.

Ok course, if your UPS isn't good, that is a different issue in my mind.

---

### Post by linuxyogi on 2014-08-28
> **TheFu said:**
> I plug all computing equipment into UPSes here (4 of them).  All power goes through the battery, so it is "conditioned" and all electrical spikes are handled.  router, switches, disk arrays, phones are all on UPSes.

Ok course, if your UPS isn't good, that is a different issue in my mind.

No my UPS is pretty good. I purchased it a long time back and back then computer products used to of better quality and comparatively expensive. I have done 3 upgrades since then but this UPS is still running.  I had change the battery 2 times.

This UPS has 3 AC outlets on the back. I have connected one to the Monitor, second to the System Unit and third one to the router.

I am not sure about this but I have heard that even if you shutdown the PC form the OS level some portions of the motherboard still receives power.

I shutdown my PC every night. Now it will be quite troublesome to unplug the PC and Monitor every night and plug them in again the next morning.

As you know the purpose of an UPS is that it gives you time to save your data and shutdown the PC. Its not meant for heavy duty backup.

Now here's the problem suppose I maintain my existing setup i.e. the Monitor, System Unit and Router is connected to the UPS and I plug in the AC input of the UPS to the Inverter's output. 

The main risk with above setup is that when main power is present everything will work fine but as soon as there is a power cut the Inverter will suffer an overload coz the load of the entire apartment is connected to the Inverter. 

This Inverter has an overloading protection system. It makes beep sound in case of an overload and ultimately shuts down. 

But if this keeps happening frequently I don't know what is going to happen.

---

### Post by TheFu on 2014-08-28
The only inverters I have **any** experience with was in Nepal. The inverter was there (Buddhist Monastery) for the network and computers only. We used it as the UPS 6 hrs at a time, 2-times every day.  I was working on my karma - upgrading the wifi network for the monks. ;)  It didn't have any UPS.

I wouldn't connect any monitor to a UPS.  Use a laptop for remote access to the system, if necessary.  Desktop monitors seem to exist to suck power and create heat.

Yes, motherboards draw a tiny bit of power, but so do almost all devices these days. Monitors draw 1W so they can start up quicker. You may recall in the 1970s when TVs took 2 minutes to warm up.  Computers draw power to support WoL and remote boot, and to allow the keyboard to de-sleep/de-hibernate a system.

Seems like some sort of electrical switch for the UPS plug is needed? When on inverter power, disconnect the UPS from upstream power.  Reconnect when real power is back. I'd guess a switch like that must be easily available there.

---

### Post by grahammechanical on 2014-08-28
> [COLOR=#000000]I am not sure about this but I have heard that even if you shutdown the PC form the OS level some portions of the motherboard still receives power.

That is true for my motherboard. There is a switch on the back of the power supply that I can use to switch off power completely to the motherboard. I do not need to use it. I have easy access to the mains socket.

Regards.
[/COLOR]

---

### Post by linuxyogi on 2014-08-29
In case of a power cut when the Inverter is in Backup Mode I don't think there is any chance of power surges. Also, 

this Inverter is designed in such a  way that either it will output 220Volts or it will make a beep sound when the battery 

becomes too low and completely shutdown. So, when a power cut happens I will simply remove the adapter of the 

router form my PC's UPS and connect it to the Inverter.

Change over switches are available here but they are usually very big in size, capable of withstanding high amperage. 

People use these switches to toggle load of their entire apartment between the main supply and generator.

But I will definitely ask if any any brand makes a 5 Amps change over.

Thanks to both.

---

### Post by Richard_Jay on 2015-04-03
[COLOR=#000000][FONT=Arial]In my opinion, connecting UPS to the inverter is not a  good practice. [I would prefer using ups and inverter]("http://www.staticon.ca/product-detail/stativolt-inverter-ups-systems") separately, instead of connecting one to the other. If you want more backup, upgrade the batteries instead of connecting ups to the inverter. I am not saying that something will definitely happen, but something can happen if you continue to use it. The inverter being a sine wave may help, but overload issues may still cause trouble. Some routers are very sensible to sudden power outages and voltage fluctuations. I would suggest not taking risks with them.[/FONT][/COLOR]

---

### Post by sammiev on 2015-04-03
Our power is so bad we have to run our computers and hmi on battery units 100% of the time. No switch from one to the other, the units are expensive to buy.

---

