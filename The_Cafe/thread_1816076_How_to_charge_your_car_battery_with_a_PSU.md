---
title: "How to charge your car battery with a PSU"
date: 2011-08-01
forum: The Cafe
---

### Post by forrestcupp on 2011-08-01
Well, my van's battery is dead, and I ran across [this blog](http://www.solar1.net/index.php?ind=news&op=news_show_single&ide=29) explaining how to charge a car battery using a computer power supply. Now that's pretty awesome.

Who says that geeks aren't real men?

---

### Post by Bandit on 2011-08-01
LOL my dad and I have done this with old 200-230w PSUs out of old 286 and 386 systems. We also used them for power converters for chrome plating. :)

---

### Post by llua+ on 2011-08-01
> **forrestcupp said:**
> Well, my van's battery is dead, and I ran across [this blog]("http://www.solar1.net/index.php?ind=news&op=news_show_single&ide=29") explaining how to charge a car battery using a computer power supply. Now that's pretty awesome.

Who says that geeks aren't real men?
Link. Of. The. Day.

---

### Post by elliotbeken on 2011-08-01
I am going to try this with an old battery for fun :)

good link

---

### Post by forrestcupp on 2011-08-01
Just keep in mind that it won't work for jump starting. You'll blow your PSU if you try that. This is only for slow charging.

---

### Post by GSF1200S on 2011-08-01
I really REALLY hope this guy's car is an automatic..

---

### Post by Inodoro Pereyra on 2011-08-01
Hmmm... I doubt you could get your battery over 10-10.5 V with a 12.00 V regulated power supply, but I guess, in a pinch, it could be useful. 
Either way, I wouldn't do it regularly. Fast charging the battery (with the car's alternator) from 10.5 V to the normal 12.5~ V does damage it.

---

### Post by forrestcupp on 2011-08-01
> **GSF1200S said:**
> I really REALLY hope this guy's car is an automatic..

If it were a manual, he wouldn't need to charge it all night to get it started.

---

### Post by jerenept on 2011-08-01
> **forrestcupp said:**
> If it were a manual, he wouldn't need to charge it all night to get it started.

People these days don't know about push-starting?

---

### Post by Inodoro Pereyra on 2011-08-01
> **forrestcupp said:**
> If it were a manual, he wouldn't need to charge it all night to get it started.

> **jerenept said:**
> People these days don't know about push-starting?

Push starting only works if your car is carbureted (mechanical fuel pump), or if your battery has enough charge to get the ECU and fuel pump running. If your battery is completely flat, you can push your car all around the world, and it won't start.

---

### Post by GSF1200S on 2011-08-01
> **forrestcupp said:**
> If it were a manual, he wouldn't need to charge it all night to get it started.

It was a joke man- thats why I said what I did. Imagine if he went to all that work when he could have just push started his car. Thats why, im hoping its an automatic ;)

Ive had to push start my car having left the lights on before- Im familiar with this activity ;)

---

### Post by GSF1200S on 2011-08-01
> **Inodoro Pereyra said:**
> Push starting only works if your car is carbureted (mechanical fuel pump), or if your battery has enough charge to get the ECU and fuel pump running. If your battery is completely flat, you can push your car all around the world, and it won't start.

My car is fuel injected and the fuel pump is electric- I simply popped it in neutral, got running with the car as fast as my legs could accomplish, hopped in, pushed in the clutch, threw it in first gear (lower the gear the faster the engine turns per car rate-of-speed), and dropped the clutch. It took a second, but it fired right up, and my battery measured about 4 volts before I started.

---

### Post by LowSky on 2011-08-01
the scariest thing I ever did was drive a manual car 15 miles in heavy traffic with no battery.

The battery was so bad I had to start the car using another car using jumper cable connected to only the dead car's battery cables.

At the time I was still a noob to the almighty clutch and was just pure luck I made it to the auto parts store. thank goodness I never stalled out.

---

### Post by Inodoro Pereyra on 2011-08-01
> **GSF1200S said:**
> My car is fuel injected and the fuel pump is electric- I simply popped it in neutral, got running with the car as fast as my legs could accomplish, hopped in, pushed in the clutch, threw it in first gear (lower the gear the faster the engine turns per car rate-of-speed), and dropped the clutch. It took a second, but it fired right up, and my battery measured about 4 volts before I started.

Which means those 4 V were enough.
Try push starting the car without a battery, and it won't start.

---

### Post by GSF1200S on 2011-08-01
> **Inodoro Pereyra said:**
> Which means those 4 V were enough.
Try push starting the car without a battery, and it won't start.
Hmmm.. I am inclined to disagree with you, though I admit I never took the battery out. This said, I still think the car would start.

Alternators produce AC current- that is, current that changes polarity many times a second (Hz rating determines how many times per second). An alternator uses a 4-way bridge rectifier to produce DC current (by redirecting each phase shift, and further capacitors are used to smooth out any "roughness" in the flow of current). Unlike a DC generator which only produces current for a portion of each revolution, an AC generator is always generating current. Most new cars (with the radio off, air-conditioning set to off, exterior and interior lights turned off, signals off, etc) can maintain a charge on the battery when the engine is turning at most 2500RPM (many cars much less).. That is to say, an alternator can supply all the current to run the electronics (ECM, fuel pump, etc) when it is turning at most about 2500 rpms.

In a push starting situation, the alternator does not need to supply the starter as the engine is being manually spun by the transmission/driveline. All you need to do is get the car moving as fast as you can, jump in quickly, and get the engine spinning at 2500rpms or so for about, at the absolute most, 2 seconds. A fuel pump only takes less than a second to charge the fuel injection system with the necessary pressure, and the ignition system and ECM are ready to go as soon as they have 12 volts.

If the car rolls for 2 seconds, the alternator IS the battery- ECMs and fuel injectors arent prejudiced against alternators ;) This is especially the case today as alternators produce a much better modulated wave..

I could be wrong, but the above is entirely logical and it would make no sense for the car not to start.  
/end off-topic

---

### Post by Inodoro Pereyra on 2011-08-01
Your explanations are roughly right, but your scenario has a few flaws.

1. If you're able to push your car fast enough that the engine will turn at 2500 rpm for 2 seconds, either you're insanely strong and fast, or you live on one hell of a slope. Most of us have to settle for making the engine turn at a few rpm, for a second at most.

2. your timeline is wrong. When you turn the key to the "ON' position, the ECU runs the self diagnostic first. That takes about a second (roughly the time all the lights on your dashboard are on), then, it sends the signal to the F/P to pressurize the system, and THEN it starts injecting. That means you need at least 2-3 seconds of sustained voltage, before the injectors start working at all.

3. Actually, the ECM is VERY prejudiced against alternators, to the point that, if you read your car's owner's manual, I can bet you'll find it says to never run the car without the battery. You were right in your explanation on how the alternator works, with one exception: there's no capacitors in the alternator. The battery is the alternator's capacitor. Running a car without the battery would most likely kill the ECU.

Believe me, I'm an electronics technician by trade, and mechanics has been my hobby since I was 8. And, most important, I've been there. As long as there's a high enough voltage in the system, the car will start when pushed (provided it works, of course ;)), but, with 0V, or no battery, you can push all you want.

---

### Post by GSF1200S on 2011-08-01
> **Inodoro Pereyra said:**
> Your explanations are roughly right, but your scenario has a few flaws.

1. If you're able to push your car fast enough that the engine will turn at 2500 rpm for 2 seconds, either you're insanely strong and fast, or you live on one hell of a slope. Most of us have to settle for making the engine turn at a few rpm, for a second at most.

2. your timeline is wrong. When you turn the key to the "ON' position, the ECU runs the self diagnostic first. That takes about a second (roughly the time all the lights on your dashboard are on), then, it sends the signal to the F/P to pressurize the system, and THEN it starts injecting. That means you need at least 2-3 seconds of sustained voltage, before the injectors start working at all.

3. Actually, the ECM is VERY prejudiced against alternators, to the point that, if you read your car's owner's manual, I can bet you'll find it says to never run the car without the battery. You were right in your explanation on how the alternator works, with one exception: there's no capacitors in the alternator. The battery is the alternator's capacitor. Running a car without the battery would most likely kill the ECU.

Believe me, I'm an electronics technician by trade, and mechanics has been my hobby since I was 8. And, most important, I've been there. As long as there's a high enough voltage in the system, the car will start when pushed (provided it works, of course ;)), but, with 0V, or no battery, you can push all you want.

1) Depends on the gearing of the car I suppose- if its geared really high (that is, where the car doesnt need many RPMs from the engine to sustain vehicle speed), you might run into problems. I am fast, but that has little to do with it ;) I do not proclaim to be able to push start a car uphill..

2) Timeline is wrong? I never mentioned a timeline- I never really explained the order of how things work as I didnt feel that was necessary.. I know that the ECM is responsible for dictating when the coil packs receive spark, when the injectors get current to open, etc.. I can go out to my car right now and start it from the moment the key hits on to engine running in about 2 seconds- much of this time, as you say, is due to the ECM doing its thing, the fuel pump priming the system, etc..

3) Isnt this somewhat based on the car? I KNOW you are right about some cars- the early 90s corvettes had to be towed to the dealer if you disconnected the battery (ive heard this, though not experienced this, from others). I understand that voltage is the potential for movement of electricity while amperage/current is the actual flowing of current; current will flow based on demand (unless voltage is so high with sufficient current that it overcomes the resistance of components, likely "frying" them), however the potential for current flow (voltage) is what is "dirty" in an AC system. I made an assumption about capacitors- the voltage regulator built into an alternator modulates the voltage to be constant at the stator output of the alternator, providing a cleaner output. Since I never used an Oscilloscope on the back of my cars alternator, I might ask if there is a sufficient wave pulse even after its been modulated by the voltage regulator? I have not looked at the schematic of a voltage regulator; I fixed the microelectronics on naval aircraft where this was never an issue (mostly analog-based control circuits).

I must say- I did google searching on not running the car without a battery, and many sources agree with you. Most of my wrenching time comes from cars pre-1990, so I guess times change. That was a pretty easy way to test a cars alternator- pop the battery cable. Alternatively, you could just check for about 13.9-14.2 volts at the battery while the car was running.

I figured you were spouting **** from your butt at first, but it turns out that poo is on me ;)

---

### Post by forrestcupp on 2011-08-01
> **Inodoro Pereyra said:**
> Push starting only works if your car is carbureted (mechanical fuel pump), or if your battery has enough charge to get the ECU and fuel pump running. If your battery is completely flat, you can push your car all around the world, and it won't start.Every manual I've ever had was carbureted. I've never tried it with a fuel injected car. 

> **GSF1200S said:**
> It was a joke man- thats why I said what I did. Imagine if he went to all that work when he could have just push started his car. Thats why, im hoping its an automatic ;)

Ive had to push start my car having left the lights on before- Im familiar with this activity ;)Sorry. I gotcha. I've had to push start cars several times, too. The best was when I was parked on a hill.

---

### Post by speedwell68 on 2011-08-01
> **Inodoro Pereyra said:**
> Push starting only works if your car is carbureted (mechanical fuel pump), or if your battery has enough charge to get the ECU and fuel pump running. If your battery is completely flat, you can push your car all around the world, and it won't start.

I have had plenty of fuel injected cars and push started many of them.

---

### Post by GSF1200S on 2011-08-01
> **speedwell68 said:**
> I have had plenty of fuel injected cars and push started many of them.
Hes saying that as long as your car has a battery in it with some voltage, it will start on a push start. See the above exchange him and I had on this topic.

---

### Post by Inodoro Pereyra on 2011-08-01
> **GSF1200S said:**
> 1) 

I figured you were spouting **** from your butt at first, but it turns out that poo is on me ;)

:lolflag: No poo here. Actually, what you said is very common.
I've worked at Advance Auto Parts for almost 2 years, and 90% of the times a customer ended having to buy a replacement ECU, their consult started with "I disconnected the battery to see if the alternator was working, and now my car won't start." Most of them aren't happy with the answer...;)

---

