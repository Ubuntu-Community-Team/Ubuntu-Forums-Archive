---
title: "Ubuntu Servers &amp; Saving Energy"
date: 2012-11-01
forum: Server Platforms
---

### Post by jlacroix on 2012-11-01
Hello everyone. I have two servers in my home that are running Ubuntu 12.04 Server. They are both Dell Precision T3400 workstations. I got a good deal on them from Craigslist for $100 each. They both run off a single UPS. I've used them primarily for a home lab to learn things on, but I've since grown very reliant on them. For example, I backed up my entire DVD collection to one of them that has a 2TB drive, that is now somewhere over half full. My other server is used for the purposes of learning virtualization.

My electric bill has been quite high, and these servers are the only things I can think of that are running it up. I live alone, and both of my personal computers are laptops. In hindsight, using Precision Workstations was probably a bad idea. They are probably energy hogs from the get go. I bet I could probably use lesser hardware and still have everything run good.

I thought of some possible solutions. Maybe there's another solution that I'm over-looking? My needs are low energy usage, high hard drive space, ability to handle large network traffic (Gigabit) for large backups.

1.) Use laptops for servers
Laptops take little energy. Maybe I could just use one or two laptops for my home server(s). The downside here is that laptop drives max out around 1TB, and I need more space than that.

2.) Use Mac Minis
I don't like the idea of buying Apple hardware, but I think they supposedly offer good cost savings. However, maybe they'll have the same issue with available drive space as #1. Of course I would make them run Linux.

3.) Buy a Nettop
I'm not sure if the Atom processor would choke on large file backups or not. They seem to choke on everything else, but use little power.

Any thoughts/tips?

---

### Post by thnewguy on 2012-11-01
My first tip would be to make sure the servers are the problem. Run both servers for a day, check your electric usage, then leave them off for a day and check your electric usage again. See how much of a difference it makes.

After that, what about just running one server? Can you attach all of your hard drives to just one server and run off that? One server should use a good deal less power than two.

Do you turn off your servers at night? Or at least leave them in sleep mode? Playing around with wake on LAN and scheduled sleep/wake commands can save a lot of electricity.

A laptop's internal hard drive is limited in size, but you can attach external drives to the laptops. Three external drives with 2TB each would give you 6TB, that's a pretty good home file server.

You seem willing to spend money on new laptops or a Mac mini, which makes me wonder just how high is your electric bill? Make sure you're not spending more on a fix than you are for electricity. Both servers together probably shouldn't be using more than $10-$20 bucks a month, it would take some time to catch up to the price of a new computer at that rate. A new computer which will have its own power consumption to factor in.

---

### Post by rubylaser on 2012-11-01
I'd buy a [Kill-a-watt]("http://www.amazon.com/P3-International-P4400-Electricity-Monitor/dp/B00009MDBU") and check your power draw on one of them. 

 An Atom would be perfectly fine for fileserver, but I'd build something based off the Intel [G530]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116409") as a simple home fileserver.  It's much more powerful, and still uses very little power. A simple [motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138332") and some [RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231424") and you can build a very nice / capable machine for less than $150 (you'll still probably want a case, and an energy efficient PSU though).

Also, you'll probably want to add a second hard drive to backup your files, because ripping your DVD collection again in the case of a drive failure is terrible. Maybe even by (2) more drives to add to your existing drive to build a RAID1 + a backup drive.

---

### Post by jlacroix on 2012-11-01
> **thnewguy said:**
> My first tip would be to make sure the servers are the problem. Run both servers for a day, check your electric usage, then leave them off for a day and check your electric usage again. See how much of a difference it makes.

I can do that, but I don't see anything else it could be. My TV for example is only powered on around 5 hours a week.

> **thnewguy said:**
> After that, what about just running one server? Can you attach all of your hard drives to just one server and run off that? One server should use a good deal less power than two.
I'm thinking about it. I wrote that both run Ubuntu, but should have been more specific. Actually the first one runs Ubuntu, though the second one is VMWare ESXi with Ubuntu VMs (one of them is my DNS/DHCP server). I edited the first post. Perhaps I can move the VMs from Server 2 to Server 1, if I install KVM. If I installed KVM on Server 1 and then moved the VMs to it, that would help. Hopefully it's not too hard. Maybe I'll do that, at least to start off.

> **thnewguy said:**
> Do you turn off your servers at night? Or at least leave them in sleep mode? Playing around with wake on LAN and scheduled sleep/wake commands can save a lot of electricity.
I don't ever turn them off, or let them go to sleep. Server 1 has Crashplan installed, and it backs up at night. This one wouldn't be hard to turn off, but it needs to be available. It runs Crashplan from 12am to 7am. Server 2 is ESXi, and would be kind of annoying to power down all VMs and then power the server down every night. I have experimented with wakeonlan on that server, but failed miserably.

> **thnewguy said:**
> A laptop's internal hard drive is limited in size, but you can attach external drives to the laptops. Three external drives with 2TB each would give you 6TB, that's a pretty good home file server.
That's a good point.

> **thnewguy said:**
> You seem willing to spend money on new laptops or a Mac mini, which makes me wonder just how high is your electric bill?
I can't actually run out and buy anything right now, but tax return time isn't too far away. But if something would give me long term savings, I may be convinced to buy something. An older Mac Mini can be had on Craigslist for not too much money. My electric bill is around $350 a month in the summer, though the last two months it's been under $200. My best friend has five people living in his house and only spends $90 (larger house) which is making me wonder.

> **thnewguy said:**
> Make sure you're not spending more on a fix than you are for electricity. Both servers together probably shouldn't be using more than $10-$20 bucks a month, it would take some time to catch up to the price of a new computer at that rate. A new computer which will have its own power consumption to factor in.
Good point. I was thinking that maybe Dell Precision workstations use more power than standard desktop computers. They're probably overkill for what I want to do.

> **rubylaser said:**
> I'd buy a [Kill-a-watt]("http://www.amazon.com/P3-International-P4400-Electricity-Monitor/dp/B00009MDBU") and check your power draw on one of them.
Good point, I'll consider getting one.

> **rubylaser said:**
> An Atom would be perfectly fine for fileserver, but I'd build something based off the Intel [G530]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116409") as a simple home fileserver.  It's much more powerful, and still uses very little power. A simple [motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138332") and some [RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231424") and you can build a very nice / capable machine for less than $150 (you'll still probably want a case, and an energy efficient PSU though).
I think I want to avoid building something, but that is not out of the question.

> **rubylaser said:**
> Also, you'll probably want to add a second hard drive to backup your files, because ripping your DVD collection again in the case of a drive failure is terrible. Maybe even by (2) more drives to add to your existing drive to build a RAID1 + a backup drive.
I use Crashplan on Server 1 now, and it also backs up to two external hard drives in addition. There is about 1TB or so in use on that server, and it took a LONG TIME for Crashplan to grab it all, but I'm happy to report it all made it to Crashplan. I am not worried about losing data (everything is on Crashplan and two external drives) but I don't want to set it all up all over again, and back up to Crashplan all over again (I think that took four-six months to finish, something like that).

---

### Post by Slug71 on 2012-11-01
I'll second switching to one server. Then look into one of the Earthwatts PSUs from Antec for it. I'll also second putting your server to Sleep Mode at night and set it to back-up during the day when you're not there or just after 'waking up' or before going into sleep mode.

---

### Post by jlacroix on 2012-11-02
> **Slug71 said:**
> I'll second switching to one server. Then look into one of the Earthwatts PSUs from Antec for it. I'll also second putting your server to Sleep Mode at night and set it to back-up during the day when you're not there or just after 'waking up' or before going into sleep mode.
I'm going to see if I can consolidate it to just one server.

Is there a ready to purchase solution I can use as a server that has a very small energy footprint? I may want to buy something in the next several months. I could buy a laptop if all else fails.

---

### Post by CharlesA on 2012-11-02
> **rubylaser said:**
> I'd buy a [Kill-a-watt]("http://www.amazon.com/P3-International-P4400-Electricity-Monitor/dp/B00009MDBU") and check your power draw on one of them.

+1. Those things are handy. ;) 

>  An Atom would be perfectly fine for fileserver, but I'd build something based off the Intel [G530]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116409") as a simple home fileserver.  It's much more powerful, and still uses very little power. A simple [motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138332") and some [RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231424") and you can build a very nice / capable machine for less than $150 (you'll still probably want a case, and an energy efficient PSU though).

That would probably work for a file server, but if they are doing virtualization, they might need a beefier machine. Atoms are really good at simple stuff like serving files and whatnot.

> Also, you'll probably want to add a second hard drive to backup your files, because ripping your DVD collection again in the case of a drive failure is terrible. Maybe even by (2) more drives to add to your existing drive to build a RAID1 + a backup drive.

Agreed. I have my dvds set up in the same way - they are sitting on my server, but also backed up to an external drive.

---

### Post by jlacroix on 2012-11-02
Okay guys, here's an update. (And another question).

I set up KVM on Server 1, and I migrated my DNS/DHCP server to it, and it worked fine. In order to get my DHCP/DNS Server VM to contact my local network, I had to activate bridge mode, I followed this guide to do that:
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

But then, I figured it was silly to run a DHCP/DNS server as a VM on Server 1, so I deleted it, and set up DHCP and DNS on the server itself without a VM.

Now that I have DHCP/DNS running locally, should I disable bridge mode? I may run VMs in the future on KVM. BUT, will having bridge mode enabled on the host cause DHCP/DNS to have trouble? Or is it okay to leave it enabled in case I want to run VMs later on?

I also ordered the Kill-a-Watt thingie. Will see what my server uses very soon.

---

### Post by CharlesA on 2012-11-02
Go for it. If you don't have the bridge set up, you'd have to do it again if/when you set up another VM and want it accessible from the same network.

---

### Post by jlacroix on 2012-11-02
> **CharlesA said:**
> Go for it. If you don't have the bridge set up, you'd have to do it again if/when you set up another VM and want it accessible from the same network.
Thanks. I was just wondering if that would be a detterent to DHCP/DNS or any kind of related performance.

I think the last thing I need is any other recommendations on something Ubuntu friendly I can buy that would support two 2TB hard drives, have a Gigabit card, and be relatively low on power consumption. 

Thanks for the help everyone!

---

### Post by CharlesA on 2012-11-02
I've been using 3TB Seagate external drives for a while now. As for internal drives, you could try those Western Digital Green drives - the ones that spin at 5400 RPM.

As for the system itself, you could look into a nettop, but the ones I looked at only had 1 or 2 2.5" drive bays, so you would need to get notebook hard drives instead of desktop drives.

---

### Post by Slug71 on 2012-11-03
> **jlacroix said:**
> I'm going to see if I can consolidate it to just one server.

Is there a ready to purchase solution I can use as a server that has a very small energy footprint? I may want to buy something in the next several months. I could buy a laptop if all else fails.

[http://www.antec.com/productPSU.php?id=704512&pid=11](http://www.antec.com/productPSU.php?id=704512&pid=11)

[http://store.antec.com/Category/power_supply-earthwatts.aspx](http://store.antec.com/Category/power_supply-earthwatts.aspx)

I currently have the EA-380D in my testbox which i'm typing this from. Can't really speak for savings as I didn't really have anything to compare it to. My old PSU died and needed a replacement, so got this.

It's currently powering a P4 2.8GHz system with 2 CD-Roms, 3 HDDS, a Floppy drive(just had it in here), PCI sound card, 3 case fans, PCI Wirless adapter.

---

