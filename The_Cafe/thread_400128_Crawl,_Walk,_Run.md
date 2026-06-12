---
title: "Crawl, Walk, Run"
date: 2007-04-03
forum: The Cafe
---

### Post by ytene on 2007-04-03
Disclaimer: this post is **not** intended as flame-bait. If the comments that follow cause any offense, please accept my apologies in advance.

Decided to spend some time last weekend testing 7.04 Beta [AMD64]. After a relatively smooth install [I always try both upgrades and fresh installations] I started to hit problems. 

The first of these was that X failed to recognise my GPU and monitor [XFX GeForce7800 and a Samsung 21" TFT]. I've seen this problem with all versions of ubuntu that I have tried to use [starting with Breezy]. In the past I used a cheap-trick fix - I built a machine based on Mandriva 2005LE, extracted xorg.conf, then copied the salient bits into the ubuntu build... I figured that in the next release or so, ubuntu would "get there" with respect to hardware detection and setup. To my surprise [and disappointment] it hasn't. I hit the forums this time, figuring that there must be a tool or utility or helper for me. I found another user with the same problem and a helpful response to try

dpkg-reconfigure ...

Yeah, OK. [I tried it, did my best, it didn't work. Back to plan B tonight]. But here's the thing. Other Linux distros nailed this problem years ago. Mandrival 2005LE [my choice before Breezy] auto-detected and coped with my SMP system, the kernel drivers for my nVidia graphics card, my monitor's 1600x1200 capability, my printer, etc, etc. 

What I don't understand - and this observation is meant with respect, not sarcasm - is that if one member of the FOSS community has come up with a solution for [say] correctly configuring X, why do other distros ignore that solution and write their own code that doesn't work as well? 

Is this the NIH [Not Invented Here] effect? Is this a wish by one distro to not pillage the good work of another? [If so, it seems odd, since we're all enjoying the benefits Linus' hard work!]

As a pragmatist, I understand and accept that one Linux distribution is never going to please all of the people, all of the time. [That's what makes Linux so strong - the fact that it can be hacked about to support such a diverse user community]. But as an idealist, and as someone who uses GNU/Linux because I believe it really is the best OS out there, I get frustrated when I see gaps - I'm reluctant to call them flaws - creep into an otherwise stellar distribution such as ubuntu. 

I guess this has a lot to do with the fact that both users and developers like to work with new, sexy technology. But at the same time I can't fail to note that a certain software distributer based in Redmond, Washington, long ago became obsessed with the new and the sexy at the expense of the basic foundations of reliability, security, stability and performance and has since lost their way in the world.

We're too smart for that.

The greatest structures are built on the strongest foundations.

I use ubuntu, proudly, because I think it's the best GNU/Linux distro available today. At the same time, I would like to see us support [and I code poorly, but donate better!] the core components, and get those foundations perfect.

Wasted effort? Maybe not. Don't forget that a new user to ubuntu can't simply do "apt-get upgrade". They have to start with a fresh install. It's like the old thought that we form lasting impressions of people in the first 15 seconds of meeting someone. Maybe we form lasting impressions of a distro during the first time we install it?

So I was intrigued to read Mark's comments about Beryl packages on his blog. I wonder if that's a step from crawl to run? I think for me that one of the steps of "walk" would be a smooth and automatically configuring installation process. 

And yes, I'd chip in to the bounty for that.

;o)



Serious footnote - I've been using ubuntu for maybe 18months now - since Breezy was released. It's easily the best GNU/Linux platform out there. The Team and contributors have done a terrific job pulling this together and I hope this distro continues to go from strength to strength.

---

### Post by ssam on 2007-04-03
you should file a bug at launchpad.net. point out that it has been solved in other distros, and any information about how.

if you look at the [ ubuntu xorg changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/x/xorg-server/xorg-server_1.2.0-3ubuntu7/changelog") you can see patches taken from fedora, so there is no opposition to work done by other distros.

---

