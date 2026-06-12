---
title: "Networking Wizards - figure this one out."
date: 2008-07-04
forum: The Cafe
---

### Post by Roasted on 2008-07-04
Anybody here good with wiring? I like wiring a lot, and I find a lot of interest in troubleshooting network problems. I ran into an interesting one today.

I work at a school district. Today, I was setting up a computer and here the connection said unplugged/plugged back in/unplugged/etc about 5 times. Then magically shut off. Hmm, wtf?

First thought - check the cable. 568-B standard wiring. Looks fine. Put it in my tester... pins 3 and 5 crossed. Bad cable. So I replace it with a cable that checks out fine on my tester.

No connection. "Cable Unplugged."

Second thought - check the jack. I pulled the jack from the wall. 568-B standard punch-down. Looked good to me, but hey... let's try it again. So I re-punch a new jack. Perfect text-book punch-down jack... Just to add to the mix, I took a functioning computer and put it in its place and booted it as well.

No connection. "Cable Unplugged."

Thirdly... check the switch. So I go to the closet and find the switch it's plugged into. Switch looks good. Maybe the port blew? I change the ports. Hmm... no lights, even after 3 full minutes. Okay, try another switch all together. So I plugged it in another Netgear 24port switch that was there. 

Nadda.

Okay, let's test the cable. So I bust out my cable tester and the terminator. I put the terminator at one end, the automatic tester at the other. So I'm testing from patch cable to wall jack... wall jack to cable... cable that goes from there to the server closet's patch panel... patch panel to patch cable.

Checked out perfect. All 8 pins. 

Wow, I'm confused.

Two different switches.
An entire run of cable that is tested to be perfectly fine - B standard.
Two computers, both in working order... no connection.

In a weird hunch, I put the old cable back in.

BAM. Connected. 100mb/s. 

WTF? How the hell can you have a full blown B standard network from a 24 port Netgear switch, all the way up to the main office to the computer, and BAM throw in a patch cable that has pins 3 and 5 crossed and MAGICALLY it works?

---

