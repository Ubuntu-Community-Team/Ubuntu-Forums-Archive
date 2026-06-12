---
title: "ubuntu cloud networking troubles"
date: 2010-10-13
forum: Ubuntu Cloud and Juju
---

### Post by martin.eugen on 2010-10-13
Hello there!

Recently I got 3 powerful servers and decided to install ubuntu cloud, I did that manually, through packages. But, I'm somewhat new to both linux and eucalyptus and, naturally, I got into lots of troubles. :)

Here's roughly how it went. Since those three servers have lots of processors, ram and disks I decided to take advantage of that. But rather than running three single-node clouds I thought it might be more manageable if I reuse another, older server for CLC and walrus (as far as I understand, there's no way to run 3 walruses on the more powerful servers rather than on the CLC, correct?). This meant I had to go for a multi-cluster setup, running CC, SC and NC on each of the new servers. The very first question I have is if that's actually advisable, I couldn't find any references to such setups on the internet?

So, currently, the clusters are connected through a single ethernet controller, they're running ubuntu 10.04.1, cloud is in managed-novlan mode (although there's no particular reason to prefer that rather than any other mode), both pubinterface and privinterface are set to the bridge (br0), and the rest is pretty much default settings.

I can run instances and so on (I use hybridfox) and everything is generally fine, except that the whole LAN starts to behave oddly.
Sometimes random nodes disappear for like 10 mins or so, sometimes ping on the public ip of a virtual machine goes to the correct VM, sometimes it goes to another. Sometimes nat rules for a VM are set properly, sometimes I can see missing rules. Sometimes ping on the LAN gets very high delay, sometimes it's ok.

After some experimenting I noted that even though I had spanning-tree off on the br0's it was somehow turned on again. As STP is running on the lan, I thought that could be the problem. I switched it off manually (brctl stp br0 off), but somehow, it got back on. I did that several times and annoyingly, every time it gets back on. So I killed it from the switch (which is some sort of a dell switch) - turned it off and made the switch filter STP packets on all ports. Didn't help at all. 

And now I'm kind of running out of ideas. Anyone running a similar cloud setup? Any suggestions on what can I do at least to figure out better what's going on?

---

### Post by Rusty au Lait on 2010-10-16
I am going on the assumption that these three machines have nothing on them now.
I would start this way. Clean all three and install 10.04 with Node Controllers (NC). Install the CLC and the other aC's on any machine with enough disk space. All your muscle should be directed to your nodes.

---

### Post by martin.eugen on 2010-10-17
Hey, thanks for your reply!

Up to a point, it was my original idea to run a single cluster, but I got somewhat tempted by the 3x4TB these servers have and I'd like to make these available to instances. 

As far as I understand, this can only be done through SC's (correct?) and there can only be a single SC per cluster (again, correct?).

Is there some other way to still have all of that disk space available on a single cluster?

---

### Post by philipprince on 2010-10-26
Thank you for this discussion! I, too, have put all of my big disks on the CC/SC for the EBS and smaller disks on the NCs for the instance vm image (probably for the reasons Martin noted).

Is it better to have a large store for EBS use smaller disk images or is it better to have larger disk images and use EBS more sparingly?

---

### Post by omarly on 2010-11-03
i had almost given it up, and no big issue for me, but syncing my contacts in evolution has been on hold for a while.

then i tried the ubuntu one page, and found this link that did the trick!

[https://wiki.ubuntu.com/UbuntuOne/FAQ/WhyArentMyContactsInEvolutionSyncing]("https://wiki.ubuntu.com/UbuntuOne/FAQ/WhyArentMyContactsInEvolutionSyncing")

i love my ubuntu :)

---

