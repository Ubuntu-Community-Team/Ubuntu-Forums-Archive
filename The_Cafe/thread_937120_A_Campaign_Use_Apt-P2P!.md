---
title: "A Campaign: Use Apt-P2P!"
date: 2008-10-03
forum: The Cafe
---

### Post by smartboyathome on 2008-10-03
Apt-P2P will basically allow us to share bandwidth in a bittorrent-like fashion. So I propose everyone use it after they upgrade to intrepid!

---

### Post by earthpigg on 2008-10-03
> **smartboyathome said:**
> Apt-P2P will basically allow us to share bandwidth in a bittorrent-like fashion. So I propose everyone **use it after they upgrade to intrepid**!

but that would be to late ;)

i thought about this too from the other thread we where talking in, but major distro updates/upgrades would be the ideal time to make use of something like this.

---

### Post by Bou on 2008-10-03
> **smartboyathome said:**
> Apt-P2P will basically allow us to share bandwidth in a bittorrent-like fashion. So I propose everyone use it after they upgrade to intrepid!

So how would we do that?

---

### Post by mihaiv on 2008-10-03
[http://www.camrdale.org/apt-p2p/install/]("http://www.camrdale.org/apt-p2p/install/")

---

### Post by Paqman on 2008-10-03
Looks like a good idea, but how well has it been tested?

---

### Post by MaxIBoy on 2008-10-03
I'd have to see if Comcast throttles it down.

---

### Post by mips on 2008-10-03
Stupid question but how is security implemented in this? I read the faq but saw nothing about that.

---

### Post by smartboyathome on 2008-10-03
> **earthpigg said:**
> but that would be to late ;)

i thought about this too from the other thread we where talking in, but major distro updates/upgrades would be the ideal time to make use of something like this.

I am seeing if I can backport Apt-P2P and python-twisted-web2 to hardy using my intrepid install, so that the hardy people can use it. Just a word of warning everyone, it does require a forwarded port from your router (if you have one).

> **Bou said:**
> So how would we do that?

Install Apt-P2P from the packages from GIT, from the Intrepid packages (you only need 2), or from the backported packages I create if I can create them.

> **Paqman said:**
> Looks like a good idea, but how well has it been tested?

I don't think it has been since it just made it into Intrepid. and was just released last May. Still, it works for me just fine.

> **MaxIBoy said:**
> I'd have to see if Comcast throttles it down.

I have comcast and am using it. I am not worried, as I probably won't even get near the limit (It would take the equivelent of downloading 2 DVDs a day to get over the limit).

> **mips said:**
> Stupid question but how is security implemented in this? I read the faq but saw nothing about that.

It is implimented through hashes I think, sort of like how bittorrent does it. You can always check [here]("http://en.wikipedia.org/wiki/Kademlia") (it is based off of that).


EDIT: I have set up a brainstorm idea to let us add an option to software sources to use this. It is available [here]("http://brainstorm.ubuntu.com/idea/14040/"), if you want to vote for/against it.

---

### Post by Polygon on 2008-10-04
comcast does not throttle torrents anymore fyi. they got their butts handed to them by the FCC over that. Now they will just cut off your service if you go over like 250 gb a month (which is a lot....)

---

### Post by mips on 2008-10-04
> **Polygon said:**
> comcast does not throttle torrents anymore fyi. 

Are you sure about that? The FCC gave them till the end of the year to change things.

---

### Post by Polygon on 2008-10-04
> **mips said:**
> Are you sure about that? The FCC gave them till the end of the year to change things.

oh. well then, never mind. point was they lost the battle and they will stop throttling torrents....eventually =P

---

