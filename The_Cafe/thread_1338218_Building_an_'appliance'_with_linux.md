---
title: "Building an 'appliance' with linux"
date: 2009-11-26
forum: The Cafe
---

### Post by Nerd King on 2009-11-26
So far I've managed to get this running with ubuntu + arora web browser (any better suggestions? It needs to be able to cope with modern web apps and be small and fast) + fluxbox + abiword + idesk running pretty quick on a 64MB machine. It typically tops out at 80MB so we use a bit of swap but I can live with that. I'm trying to get it smaller. However it's also going to need Wine on it to run MS Reader for some ebook reading (unless anyone has any native suggestions). The idea is to get a bunch of machines from a skip and make them useful at a local school who don't have many resources.

The plan is to make it more an appliance than a computer as such, in that it requires zero maintenance. I intend to have it boot with 6 icons on the desktop, Files, internet, word processor, dictionary (useful as English is 2nd language), Video Player and Books. I'd like to put a lighter alternative to apache on there too if possible, but php is a must as it'd allow me to do lots of cool things to make certain things happen when using the browser.

I'm in the process of testing out a Lenny-based install along similar lines to see if it makes any difference (I don't need any fancy proprietary drivers as such so it should be good, and the added stability of Debian appeals in this case, it needs to be 100% indestructable, or very close to it).

So.. any advice/questions/ideas/fail chaps? Just wondering if anyone else out there has tried something similar and could offer some experience.

---

### Post by Paqman on 2009-11-26
The school themselves should be the ones who decide what apps they're going to need. It's them that'll be using it, they should set the spec. How you meet that brief is up to you, obviously.

I'm assuming from the zero maintenance requirement that nobody at the school is willing/able to provide support, and that you can't do it yourself?

---

### Post by Nerd King on 2009-11-26
This is a freebie and this is based on what they're after (ie they're trying to get books/net/word processor etc but have zero cash, this is not in the West guys, this is out in the sticks where money doesn't grow on trees!).

I've spoken to teachers and management and the teachers would certainly have uses for an ebook collection in the classroom, and the other facilities (along with some educational software I've built to help kids with times tables, number bonds, etc) will help them tremendously. I've got the human side, I have a reasonably good technical side, I'm just wondering if I can make the technical side better.

On the zero maintenance thing. This is primarily that I don't want this to become a day job for me. I want it to be something I can just image the hard drive and copy from machine to machine and if it breaks just re-image it. I can teach people how to do that so that if I get hit by a bus they're not dependent upon me. I would love it if it was even possible to just stick it on a flash drive and run from that. This (and the headaches they've had in the past with maintaining windows machines) is the reason for going linux, and some of why I'm considering vanilla debian instead of ubuntu.

---

### Post by SR_ELPIRATA on 2009-11-27
Not sure if you have heard of this but there's a software out there that allows you to make a powerful computer with ability to connect 10 monitors and the software allows all users to perform 'basic' stuff with them, 10 monitors, 10 keyboards and 10 mouse.

I forget the name but I remember that after you get the software (which you have to pay for) they do all the support remotely. I mentioned 'basic' because all 10 users would be sharing resources, but not necesarily means that only can use the web/office.

The package appears on the Software Centre of 9.10.

ELP

---

### Post by Nerd King on 2009-11-27
I've heard of that, though for the life of me i can't think of the name, but the paying bit is the challenge here. The budget is literally "find-computers-from-skip-and-make-them-useful". I'll investigate further though to see if it's something doable.

---

