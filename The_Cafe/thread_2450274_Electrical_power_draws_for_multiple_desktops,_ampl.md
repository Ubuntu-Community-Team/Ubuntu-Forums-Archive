---
title: "Electrical power draws for multiple desktops, amplifier, a/c etc."
date: 2020-09-10
forum: The Cafe
---

### Post by ra7411 on 2020-09-10
I've got a number of desktop computers, amplifiers, a/c etc. that have grown up over the years in my office.

Is there any right way to distribute these things across the office/room wiring system to minimize load problems?

Are there any power strips / circuit breaker systems that are designed to handle things like this?

I've got plenty of routine power strips in my current setup, but it's pretty much a mish mash and I'm thinking I need to do something to improve things.

Thanks

---

### Post by CharlesA on 2020-09-10
Moved this to the cafe as it isn't really a Ubuntu question.

As for your question, it depends on the wiring of your house. If you overload the circuit the circuit breakers will trip.

Are you running into issues where the breakers are tripping or are you seeing other issues?

---

### Post by ra7411 on 2020-09-10
> **CharlesA said:**
> Moved this to the cafe as it isn't really a Ubuntu question.

As for your question, it depends on the wiring of your house. If you overload the circuit the circuit breakers will trip.

Are you running into issues where the breakers are tripping or are you seeing other issues?

No issues yet, just a mish mash of power wiring to various devices that I want to get better organized with some improved safety features. This is probably a common issue, but I haven't found much in the way of equipment or advice.

---

### Post by ameinild on 2020-09-10
This is probably total overkill, but there are pretty advanced power rails with LED displays and breakers built-in...

[https://www.amazon.com/CyberPower-PDU41001-Switched-Outlets-Rackmount/dp/B076MHL3VG/ref=psdc_689651011_t4_B07G3DRY8Q](https://www.amazon.com/CyberPower-PDU41001-Switched-Outlets-Rackmount/dp/B076MHL3VG/ref=psdc_689651011_t4_B07G3DRY8Q)

This is a little less overkill:

[https://www.amazon.com/Tripp-Lite-110-127V-Rack-Mount-PDUMH20/dp/B00193ODWS/](https://www.amazon.com/Tripp-Lite-110-127V-Rack-Mount-PDUMH20/dp/B00193ODWS/) or [https://www.amazon.com/Tripp-Lite-200-240V-Rack-Mount-PDUMH20HV/dp/B0052NM4JA/ref=pd_di_sccai_1/138-7324011-1167143](https://www.amazon.com/Tripp-Lite-200-240V-Rack-Mount-PDUMH20HV/dp/B0052NM4JA/ref=pd_di_sccai_1/138-7324011-1167143)

And if you have 3-phase 400V power output, something like this that splits in to 3 phases with separate displays: (this is for EU though)

[https://www.thomann.de/dk/botex_psa_161_power_distributor_16a.htm](https://www.thomann.de/dk/botex_psa_161_power_distributor_16a.htm)

I'm just throwing in some crazy ideas! :D

---

### Post by crip720 on 2020-09-10
The a/c should be on it's own separate circuit, don't plug something else with it.  Would need to know how the outlets are connected in the room, all on same circuit, or have some on a different circuit from the others(one circuit breaker goes off is everything dead).  In N.A. a 15amp circuit(not each outlet on circuit) can carry ~1500w.  Most stuff will have how many watts they use, add them up to see how much a circuit carries, would want less than full circuit capacity.

---

### Post by CharlesA on 2020-09-10
> **ameinild said:**
> This is probably total overkill, but there are pretty advanced power rails with LED displays and breakers built-in...

[https://www.amazon.com/CyberPower-PDU41001-Switched-Outlets-Rackmount/dp/B076MHL3VG/ref=psdc_689651011_t4_B07G3DRY8Q](https://www.amazon.com/CyberPower-PDU41001-Switched-Outlets-Rackmount/dp/B076MHL3VG/ref=psdc_689651011_t4_B07G3DRY8Q)


That looks really fancy!

I've got a [Kill a Watt]("https://smile.amazon.com/P3-P4400-Electricity-Usage-Monitor/dp/B00009MDBU") that I use for measuring power usage per device or per power strip. It's actually fairly cheap, but it can be a bit hard to read if it's stuffed behind a desk.

---

### Post by ameinild on 2020-09-11
> I've got a [Kill a Watt]("https://smile.amazon.com/P3-P4400-Electricity-Usage-Monitor/dp/B00009MDBU") that I use for measuring power

I use something similar myself to measure power. In addition I use this, which is also overkill regarding the fuses:

[https://www.thomann.de/dk/the_t.racks_ms6.htm](https://www.thomann.de/dk/the_t.racks_ms6.htm)

But I use it mainly for the front switches, so I can cycle the power of my networking gear from the front panel if necessary.

---

### Post by sdsurfer on 2020-09-11
May not be the "best" technology but I religiously run every desktop computer with a UPS. Each UPS is dedicated to  one computer and its monitors on the battery, peripherals on the UPS surge protector. I have an old APC that has seen three battery swap outs and it still has saved us from multiple power outages and surges. Even a smaller unit is better than direct wall/surge protector connections.

---

### Post by CharlesA on 2020-09-11
> **sdsurfer said:**
> May not be the "best" technology but I religiously run every desktop computer with a UPS. Each UPS is dedicated to  one computer and its monitors on the battery, peripherals on the UPS surge protector. I have an old APC that has seen three battery swap outs and it still has saved us from multiple power outages and surges. Even a smaller unit is better than direct wall/surge protector connections.

I do the same. Just be sure to test them regularly - they are useless if they have bad batteries. :)

---

### Post by ra7411 on 2020-09-12
>[COLOR=#000000]May not be the "best" technology but I religiously run every desktop computer with a UPS<

Very necessary for a place with a lot of lightening, and/or a power company that sends a lot of power spikes down the line - both in my case.
My system has redundant circuit breakers beyond the APC UPS unit.

>[/COLOR][COLOR=#000000]I do the same. Just be sure to test them regularly - they are useless if they have bad batteries.<

[/COLOR][COLOR=#000000]Right- easy test is to pull the UPS wall power plug and see your system is still running.


[/COLOR]

---

### Post by zebra2 on 2020-09-13
So far as the circuit loading is concerned I would put a watt meter on those systems and see what the load is. It is possible that you can replace those systems for less than the load on your power bill. Do some math.

---

### Post by vidtek on 2020-09-13
> **ra7411 said:**
> I've got a number of desktop computers, amplifiers, a/c etc. that have grown up over the years in my office.

Is there any right way to distribute these things across the office/room wiring system to minimize load problems?

Are there any power strips / circuit breaker systems that are designed to handle things like this?

I've got plenty of routine power strips in my current setup, but it's pretty much a mish mash and I'm thinking I need to do something to improve things.

Thanks

You do not give your geographic location, so it makes it really difficult to advise you.

If you are in the UK, the maximum draw before tripping out the rcd's should be over 10 amps.  The UK is a nominal 240v. 50hz  If you are mainland Europe, a nominal 220v at 50hz.  The US is 110v at 60hz.  The regulations regarding house wiring vary according to local laws/customs.  

If you are in Alaska, your electrical use will be entirely different from a Southern European climate, heaters instead of airconditioners.  

More information is always good when posting questions in forums.  Geographic location is a must for getting proper results.  Put your setup and o/s details in your signature to avoid erroneous answers.

---

### Post by sdsurfer on 2020-09-18
> **CharlesA said:**
> I do the same. Just be sure to test them regularly - they are useless if they have bad batteries. :)

Most of them have low/malfunctioning battery alarms (??) When the APC SLA starts to go bad and won't hold a charge, it sounds off like a house fire alarm, even woke me up one night to tell me it was dying.

---

### Post by Tadaen_Sylvermane on 2020-09-20
> [COLOR=#000000]May not be the "best" technology but I religiously run every desktop computer with a UPS. Each UPS is dedicated to one computer and its monitors on the battery, peripherals on the UPS surge protector. I have an old APC that has seen three battery swap outs and it still has saved us from multiple power outages and surges. Even a smaller unit is better than direct wall/surge protector connections.[/COLOR][COLOR=#000000]

This is the main reason that I pxe boot everything I can with LTSP where Linux is concerned. No worries about random power cuts as everything is technically on the server which has a UPS on it. Probably should get one for my Windows desktop that I use for games though. Thanks for that.[/COLOR]

---

