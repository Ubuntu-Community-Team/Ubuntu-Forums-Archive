---
title: "Robotics?"
date: 2008-08-29
forum: The Cafe
---

### Post by ankursethi on 2008-08-29
I didn't really know which category this post would belong to, but here goes.

Me and a friend are getting interested in building toy robots, and I've been looking around the web for information. Mostly we find circuit diagrams and videos of stuff other people have done, but nothing that would help us understand the machine and roll our own.

Assuming we know nothing about electronics and stuff, can somebody give me a rough roadmap of what I should know before I'll be ready to make, say, a simple RC bot, or one of those line finder robots?

I don't want to pick up circuit diagrams and glue the pieces together. I want to understand the electronics behind the entire thing.

Are there any enthusiasts here who could help me out a bit? I don't frequent many other forums, so this is where I turned for help.

---

### Post by Thelasko on 2008-08-29
It might be too simple for you, but [Lynxmotion]("http://www.lynxmotion.com/") has some really awesome kits.  Really, the electronics to a robot aren't much more than some servos and a micro controller.  You can buy just bare bones hardware and add on yourself, or you can buy the whole kit, with the micro controller and everything, it's up to you.

---

### Post by R_T_H on 2008-08-29
I think discrete electronics is the best - it has an elegant simplicity. Pick up any good starter book on electronics, and roll with it! Just read it, and think about what you read, and you should pick it up quickly. Then apply it and, voila, something electronic (hopefully it works and it is a robot :))

---

### Post by t0p on 2008-08-29
You should check out microcontrollers - that's where hobbyist robotics is nowadays.  And there's a whole bunch of software in synaptic for working with the micros.

A few examples: **piklab** and **picasm** for Microchip's **PIC** microcontrollers; **avrp** and **avrprog** for Atmel **AVR** microcontrollers; **lnpd**, a utility that enables communication with the **LEGO Mindstorm RCX**.

This stuff isn't just toys.  Even the LEGO Mindstorm.  These are basic microcontrollers that offer great functionality to any semi-intelligent robot you might have in mind.

---

### Post by Yes on 2008-08-29
Check out the Arduino ([http://www.arduino.cc/](http://www.arduino.cc/)).  Here's an example of a robot you can make with it: [http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1216170455](http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1216170455).  To start learning, I would look around [here](http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?board=projects) for a simple, well documented project and clone it.  There's also some very nice guides that'll teach you how to use the various aspects of your Arduino [here](http://www.arduino.cc/en/Tutorial/HomePage) and [here](http://www.arduino.cc/en/Guide/HomePage).

---

### Post by Thelasko on 2008-08-29
> **R_T_H said:**
> I think discrete electronics is the best - it has an elegant simplicity. Pick up any good starter book on electronics, and roll with it! Just read it, and think about what you read, and you should pick it up quickly. Then apply it and, voila, something electronic (hopefully it works and it is a robot :))

You mean something like [BEAM]("http://en.wikipedia.org/wiki/BEAM_robotics")?  I built a BEAM kit in my high school electronics class.  It was more electrical engineering than computer engineering.  It looked similar to [this]("http://www.techbotics.com/acatalog/BEAM_Parts___Components.html"), but there were no ICs, and it was solar powered.

---

### Post by ankursethi on 2008-08-30
I never thought I'd get any replies :) Building bots seems to be a popular hobby.

Kits might be a great way to learn some basics, but I'm afraid I don't have the luxury of being able to purchase any. I'm in India and getting something shipped from across the globe would cost me about as much as the product I'm ordering. And that's assuming the retailer ships the product to India at all.

As I said, I *could* just get a circuit diagram off the web, glue together the components and call it a robot, but I really want to understand the electronics behind the thing. Even if I build nothing more than a fancy RC car, I want to do it on my own. Sure, in the end I might just copy stuff off a webpage, but I want to understand what I copy.

Discrete electronics? Wikipedia doesn't seem to know anything about that. What I'm looking for is basic electronics knowledge that would help me create my own circuits when (if?) I want to.

---

### Post by Nick Lake on 2008-08-30
I'm interested in getting into robotics and programming robots too. I recently found a magazine called "ROBOT" ([www.botmag.com](www.botmag.com)) which addresses getting started in robotics in their JULY / AUGUST 2008 issue. Check out educational robot systems like VEX and the VEXPLORER.

Let me know how you go - I'd like to share experiences. Where I live it can be hard to get hold of resources for this kind of endeavor.

- Nick

---

### Post by R_T_H on 2008-08-30
> **ankursethi said:**
> Discrete electronics? Wikipedia doesn't seem to know anything about that. What I'm looking for is basic electronics knowledge that would help me create my own circuits when (if?) I want to.

Discrete electronics - anything not IC based (although you could make exceptions for basic logic gates etc :)). The main restriction is that the bhaviour of your robot would be hardwired in the electronics. 
Not the most versatile, but if you want to learn, it's definitely the best way to do it. If you want to do a line finder robot, it would be very simple, basic, and you'd learn a fair amount.

---

### Post by ankursethi on 2008-08-30
Sounds interesting. Can you give me some links?

---

### Post by javafiend on 2008-09-03
Check out [www.societyofrobots.com]("http://www.societyofrobots.com").  They have a $50 robot tutorial based on the AVR ATMEGA8 microcontroller.  It is a great starting point and is expandable.

---

### Post by Geir102 on 2008-09-09
I built a robot for my bachlor degree in electronics. Try [www.societyofrobots.com](www.societyofrobots.com) great site.

---

### Post by elmer_42 on 2008-09-09
Systm did two episodes on robots that I found very interesting. You can find them [here]("http://revision3.com/systm/robots/") (DIY Combat Robot) and [here]("http://revision3.com/systm/robogamesV2").

**e:**You may even want to watch their [latest episode]("http://revision3.com/systm/techshop/") on DIY Segways, it has a few good resources for general robotics in it.

---

### Post by Keen101 on 2008-09-12
I have been involved with FIRST Robotics for four years. They closest thing i have found that is easy for anyone who knows nothing about programming, and is cross platform (works on linux), is the Arduino or Freeduino.

There are tons of projects. 

[http://www.ladyada.net/make/mshield/](http://www.ladyada.net/make/mshield/)

[http://reprap.org/bin/view/Main/Arduino_Breakout_1_2](http://reprap.org/bin/view/Main/Arduino_Breakout_1_2)

[http://www.freeduino.org/buy.html](http://www.freeduino.org/buy.html)

---

