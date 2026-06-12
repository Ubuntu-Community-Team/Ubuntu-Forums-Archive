---
title: "? what is Ubuntu Cloud"
date: 2010-09-04
forum: Ubuntu Cloud and Juju
---

### Post by Bushcraft Bill on 2010-09-04
what does it do?
were can I find it?
what do I do with it?
how do I get one?

Bill   :popcorn:

---

### Post by Old_Grey_Wolf on 2010-09-05
Some of tthe answers are on the Ubuntu Enterprise Cloud page [http://www.ubuntu.com/cloud/private](http://www.ubuntu.com/cloud/private)

---

### Post by Rusty au Lait on 2010-09-11
I was told a lot that that's where my head was.
So the clouds are made of water vapor. An instance is created (a drop of water). Inside this drop of water things happen. Sometimes it's a speck of sand, sometimes it's life. It goes on for a while doing it's thing. It's purpose completes and it returns to vapor, or, if needs require, it goes on.

I like better the part where the life form in the drop is a yeast and it's purpose is to go into a vat of malt. That's when you want to have as many instances running at one time as you can.

Old_Gray_Wolf, please stay. Enjoy your beans and beer. There's a real nice place, way over there. Tks.:)

---

### Post by absolutezero1287 on 2010-09-18
Cloud computing uses the internet to provide resources. In other words, if you want to use Ubuntu all you'd need is high speed internet. Your data would be stored on the cloud and all operating system stuff is provided to you via the cloud.

This makes your home PC or laptop a "thin client." It doesn't need to have insane specs. All it needs is an internet connection. If you want to play a very graphics intensive video game via the cloud your home computer doesn't need a powerful graphics card. All the necessary calculations are done for you by servers within the cloud itself.

That being said, I'm not sure whether Ubuntu has a true cloud or some glorified form of offsite storage.

---

### Post by kim0 on 2010-09-20
What is a Cloud ?

Wikipedia defines cloud computing as "Internet-based computing, whereby shared resources, software, and information are provided to computers and other devices on demand, like the electricity grid". Basically this means having many servers (100s) that you can control using an API to very quickly create/destroy servers on demand. This way of thinking (as opposed to buying servers) has interesting business implications on what you can do (say you want 1000 servers today, but none for the rest of the month) with clouds you just pay for what you use and it's flexible enough to meet your needs

Ubuntu Enterprise Cloud (UEC) is a software product that you can install on your own servers to create your own cloud computing environment behind the firewall. UEC provides an Amazon EC2 compatible API interface, such that many tools that configure EC2, can be used readily on UEC. You can install and run UEC on a small number of servers, say 3 or 4 and run your company's workload on top of that. As more virtual servers are needed, you can easily add more virtual servers or more physical server to expand capacity

---

### Post by Fableflame on 2010-10-03
> **absolutezero1287 said:**
> Cloud computing uses the internet to provide resources. In other words, if you want to use Ubuntu all you'd need is high speed internet. Your data would be stored on the cloud and all operating system stuff is provided to you via the cloud.

This makes your home PC or laptop a "thin client." It doesn't need to have insane specs. All it needs is an internet connection. If you want to play a very graphics intensive video game via the cloud your home computer doesn't need a powerful graphics card. All the necessary calculations are done for you by servers within the cloud itself.

That being said, I'm not sure whether Ubuntu has a true cloud or some glorified form of offsite storage.

How could you set it up to play a game from the cloud?
Would the computer hosting the server have to have good specs to play a graphics intensive game?

---

### Post by heyandy889 on 2010-10-10
@FableFlame

That is an interesting point. Could we use a fast computer to run a game in a cloud? Maybe we should consider these points.

Do you have at least one computer that is fast enough to run your game?

Do you have a fast connection between your server computer and your "thin client"? By the way, I LOVE the term thin client! It seems to fit the idea that you would use a fat computer to do the hard work, and connect to the fat computer with a smaller thin client. Love it!

To me, those are the two primary considerations: a fast server, and a fast connection between the server and thin client.

---

### Post by Rusty au Lait on 2010-10-11
My guess as to where games in the clouds is heading is something like:
In World of Warcraft or Second Life (future versions of both) your instance will connect to the really big box. Your instance keeps direct contact with you when you are online and, until you leave the game, runs things while your offline. It can create other instances as they are needed, and terminated when finished. The power of the CPU and the speed of the I/O are as great as the machines running the node (in eucalyptus terms). Of course the cloud does all that. Your thin client will only have to relay your commands to and from your instance. So. To the clouds!

---

