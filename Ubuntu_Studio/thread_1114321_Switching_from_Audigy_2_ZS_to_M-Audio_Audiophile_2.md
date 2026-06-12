---
title: "Switching from Audigy 2 ZS to M-Audio Audiophile 2496 makes sense in my case?"
date: 2009-04-02
forum: Ubuntu Studio
---

### Post by teel on 2009-04-02
Hi,
I am trying to set up an amateur studio at my desktop, which is build up of:
- Athlon XP 2000+ 1,66 GHz processor
- 1GB RAM
- chipset nForce2
- Creative Audigy 2 ZS (SB0350).
- Line6 PODxt
- Ubuntu Studio 8.04.2

Although running realtime kernel and realtime mode of Jack sometimes I get xruns or without any particular reason drums in Hydrogen or sound fonts via qsynth start to sound metalic and distorted.

I know the Creative Audigy 2 ZS card is not the pro-audio one and I started thinking about switching to inexpensive M-Audio Audiophile 2496 about which I've read a lot of good opinions.

The question is the following: will it help with my audio distortion (it is connected with Jack because resetting Jack causes this problem to disappear for a while) and with xruns or it is just a poor desktop hardware responsible for it?

I've noticed Audigy 2 does not allow for many Jack parameters modification, like periods, just works on "2", else the Jackd does not start.

teel

---

### Post by ToFue on 2009-09-11
I know the post is aged, but I would guess that it's your 'puter hardware; the 1.66ghz would be the bottleneck IMO;

 You'll want to check out your fsb and see what other bottlenecks exist on your mobo,  reassessing from there. Real-time audio processing is as quick as your slowest hardware component(s), and requires a 'can-do' system for heavy sessions no matter if it's windows, linux or osx..  I had rendering problems on a system with a 3.2ghz p4 w/ 800mhzFSB on 1g of ram, until I upgraded the graphics card from a tnt2 to a gforce 5950 ultra, and made sessions do-able, and that was with the audigy2 platinum ex, not zs, so the sound card is fine for stereo tracking..

If jack works on a reset, it may be a buffer issue, so you'll want to investigate that as well..  Please post the solution if/when your issue gets resolved.. :)

---

