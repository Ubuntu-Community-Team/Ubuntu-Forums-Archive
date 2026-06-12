---
title: "Offensive Anti-Virus:  Rambo v1.0."
date: 2010-07-10
forum: The Cafe
---

### Post by McRat on 2010-07-10
Well, malware production and infection continues to climb with no end in sight.

It's perhaps time to rethink the whole issue from scratch.

Most malware has two things in common:

1) They inject executable code on the machine

2) They have a destination to retrieve data from the infected machine.

Most anti-malware software warns and deletes suspicious files.

But there is a Better Way:

Rambo v1.0 -

Rambo loads on the client machine and creates a small virtual machine using Linux (Fight Box). When Rambo sees a malware file, it deliberately loads it into the Fight Box. It single steps through the program with emulation.

Rambo downloads 1 x 10^9 copies of the malware.

Rambo looks for payload destination, and transmits a random data stream at it.

Rambo transmits to the Strategic Attack center and passes the connection info to any available machines with Rambo that are idle. They do saturation bombing on the target in the background without risking running the malware itself.

Rambo would chew up the Malware HQ's bandwidth and bloat their HDD's with garbage. In the process, it would dilute the ability of the malware to milk victim sites who have already been infected.

---

### Post by JohnnyC35 on 2010-07-10
sounds like a great program that should be a Windows default

---

### Post by CharlesA on 2010-07-10
Only problem would be that you'd get screwed cuz it would be running DDoS attacks.

---

### Post by chris200x9 on 2010-07-10
wouldn't that chew up your bandwidth as well? Especially if you have multiple malware programs.

---

### Post by McRat on 2010-07-10
> **CharlesA said:**
> Only problem would be that you'd get screwed cuz it would be running DDoS attacks.

It's not Denial of Service if they "asked" for it.  :D

It would be like saying AT&T got a DoS attack when they were flooded with iPhone orders.

The malware distributor wanted data, and wanted to distribute his program, so you just help them.

---

### Post by McRat on 2010-07-10
> **chris200x9 said:**
> wouldn't that chew up your bandwidth as well? Especially if you have multiple malware programs.

The Fightbox works like distributed computing apps work, only when the CPU has time for it.

---

### Post by chris200x9 on 2010-07-10
> **McRat said:**
> The Fightbox works like distributed computing apps work, only when the CPU has time for it.

What? I'm talking about bandwidth, you say eat up their harddrive space so I'm assuming you are sending alot of data. In reality wouldn't you be doing yourself more harm? Depending on the amount of malware on your computer and your cap size you would be killing your cap, and slowing down your whole network by sending huge amounts of junk data.

---

### Post by McRat on 2010-07-10
> **chris200x9 said:**
> What? I'm talking about bandwidth, you say eat up their harddrive space so I'm assuming you are sending alot of data. In reality wouldn't you be doing yourself more harm? Depending on the amount of malware on your computer and your cap size you would be killing your cap, and slowing down your whole network by sending huge amounts of junk data.

That's where the distributed computing comes into play.  Many malware organizations are now very large enterprises, and one computer running full blast wouldn't have a lot of effect anyhow.  One malware company alone had over 1,000,000 victims over the span of 4 years.  

Realistically, writing an application like this would be like guerilla warfare.  You really wouldn't want to sign your name on it.  I don't imagine the idea has never crossed the minds of the 500 anti-malware companies.

Truth is, since malware normally DOES have a destination to it, it really isn't impossible to find the perp, but apparently that is done very rarely unless the victim is a Fortune 500.

It would be really simple to reduce internet crime, but it increases instead.

---

### Post by fatality_uk on 2010-07-10
I think you should look deeper how these botnets actually work and distribute themselves. Many years ago, they would have a hub PC/SERVER doing all the work, i.e, your target PC.

Current bot nets have sub nets, sub controllers, and networks within networks and also employ some very impressive encryption techniques. Rarely does all this start from a single PC/SERVER (IP ADDRESS).

Your application could actually be targeting a 2nd tier controller PC sat in some kids bedroom that doesn't actually do the farming but just sends control data to the infected client PC's.

---

### Post by McRat on 2010-07-10
> **fatality_uk said:**
> I think you should look deeper how these botnets actually work and distribute themselves. Many years ago, they would have a hub PC/SERVER doing all the work, i.e, your target PC.

Current bot nets have sub nets, sub controllers, and networks within networks and also employ some very impressive encryption techniques. Rarely does all this start from a single PC/SERVER (IP ADDRESS).

Your application could actually be targeting a 2nd tier controller PC sat in some kids bedroom that doesn't actually do the farming but just sends control data to the infected client PC's.

Yeah, it would target "victims" as well, but SOMETHING is coming from and going to the origin.  It would hit both.  Nothing wrong with taking somebodies computer off-line that is doing destructive things to it's neighbors, even if they aren't aware of it.

Like destroying a dog that bites children.  It's not the dog's fault, but you need to remove the danger.

---

### Post by fatality_uk on 2010-07-10
> **McRat said:**
> Yeah, it would target "victims" as well, but SOMETHING is coming from and going to the origin.  It would hit both.  Nothing wrong with taking somebodies computer off-line that is doing destructive things to it's neighbors, even if they aren't aware of it.

Like destroying a dog that bites children.  It's not the dog's fault, but you need to remove the danger.

These networks aren't passive you know! This could very quickly become Internet Armageddon!! They have heuristics that can detect "threats" and can DIRECTLY attack the source of these threats.

If 10,000 bot nets see the Rambo network as a threat, I wouldn't want to see the bandwidth bill the Rambo network would rack up.

---

### Post by chris200x9 on 2010-07-10
> **McRat said:**
> That's where the distributed computing comes into play.  Many malware organizations are now very large enterprises, and one computer running full blast wouldn't have a lot of effect anyhow.  One malware company alone had over 1,000,000 victims over the span of 4 years.  

Realistically, writing an application like this would be like guerilla warfare.  You really wouldn't want to sign your name on it.  I don't imagine the idea has never crossed the minds of the 500 anti-malware companies.

Truth is, since malware normally DOES have a destination to it, it really isn't impossible to find the perp, but apparently that is done very rarely unless the victim is a Fortune 500.

It would be really simple to reduce internet crime, but it increases instead.

right, I know what a ddos attack is. I'm just saying wouldn't you be harming yourself? i.e using your own bandwidth to stick it to them?

---

### Post by McRat on 2010-07-10
Well, it is little more than a pipe-dream.:twisted:

I'm not a good enough programmer to write such an app, nor would I want to go to court over doing the job of the paid Law Enforcement personnel.](*,)

It would require a large number of folk, some with solid tech backgrounds in A/V technology, to build and deploy such an app and even a larger number to agree that internet crime needs to stop, and run Rambo machines.

---

### Post by V for Vincent on 2010-07-10
I really get the impression this'd be illegal...

---

### Post by McRat on 2010-07-10
> **V for Vincent said:**
> I really get the impression this'd be illegal...

The problem today, is doing legal things aren't all that much safer than doing illegal things.

No, it would not be illegal in California, but could be in other places.  You won't gain deceptive access to their system, and they requested the data.  The problem would be getting sued.  Even if you're in the right, doesn't mean you're safe.

---

### Post by earthpigg on 2010-07-10
> **V for Vincent said:**
> I really get the impression this'd be illegal...

headquarter the company somewhere that it would *not* be illegal, and somewhere that doesn't frequently extradite.

people contributing code and whatnot are, naturally, doing it "for studying purposes" and "not intended to be actually used" et cetera.

meanwhile, officially regard the deployable fork as 'rogue' and 'we do not support this' et cetera. 

i suggest BSD license.

---

### Post by McRat on 2010-07-10
> **earthpigg said:**
> headquarter the company somewhere that it would *not* be illegal, and somewhere that doesn't frequently extradite.

people contributing code and whatnot are, naturally, doing it "for studying purposes" and "not intended to be actually used" et cetera.

meanwhile, officially regard the deployable fork as 'rogue' and 'we do not support this' et cetera. 

i suggest BSD license.

You could even make a Game out of it, with Rankings and Prizes.  "Rambo [COLOR="Red"]!=h4kOr[/COLOR] is l33t #1 in Area 51.  A new HP Color Printer is on it's way, courtesy of FinalJustice Inc.  CONGRATS!!!"

---

### Post by Steve603z on 2010-07-10
[IMG]http://imgs.xkcd.com/comics/network.png[/IMG]
[http://xkcd.com/350/](http://xkcd.com/350/)

---

