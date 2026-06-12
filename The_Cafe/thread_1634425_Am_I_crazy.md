---
title: "Am I crazy?"
date: 2010-11-30
forum: The Cafe
---

### Post by scottuss on 2010-11-30
I've decided to take the plunge and get loads of storage to put all of the media in our household onto.

I can't decide whether to build a dedicated box, or use the PC I have hooked up to the TV. It has KVM running a few virtual machine servers for various bits, and is only powered on when being used. However, rather than building a whole new box to be my storage server, I'm thinking of sticking a couple of large disks in and setting up LVM.

So why am I crazy you ask? The box I speak of is a Quad Core Q6600 with 4G RAM. So yes, power hungry. Idle, I don't think it will be *too* bad, but I do expect my energy bills to rise noticably.

What would you guys do? I've asked the Mrs and she gives me a blank look!

Thanks!

---

### Post by czr114 on 2010-11-30
I guess it would depend on the marginal cost of a kWh. What would be the payback period for a very efficient Atom?

Can you make use of WOL?

Could anyone benefit from moving that CPU and mobo away from the TV to replace a slower workstation?

---

### Post by scottuss on 2010-11-30
> **czr114 said:**
> I guess it would depend on the marginal cost of a kWh. What would be the payback period for a very efficient Atom?

Can you make use of WOL?

Could anyone benefit from moving that CPU and mobo away from the TV to replace a slower workstation?

I reckon I could build a cheap little Atom box for bout £200 or so, however I'm not sure what my current box consumes so no idea if (or rather when) the cost is offset. Also, it might be useful to have the one box doing everything, it's quite meaty and I have quite a few things I might like to put on there.

I guess if I want a lot of functionality, I'll have to pay for it (in electricity!)

---

### Post by lukeiamyourfather on 2010-11-30
Count on about 200 watts idle for the whole Q6600 system. Every five hours that would be one kilowatt hour, which is about $0.15 depending on the region. That is $262.80 per year in electricity if left on all the time. An energy efficient system would use less than half of that. Over five years it would come to $657.00 ***difference*** between electricity for the Q6600 versus a energy efficient system.

Long story short, if you plan to leave it on all the time and use it for years to come it would definitely be cheaper to build a more efficient system. Personally I'd build a system with something like a Athlon II X4 615e (energy efficient quad core that uses about 45 watts), or a higher end dual core Atom like the D525 (uses about 13 watts). Note the wattage is just for the processor, not the drives and other components as well.

---

### Post by samalex on 2010-11-30
> **scottuss said:**
> I reckon I could build a cheap little Atom box for bout £200 or so, however I'm not sure what my current box consumes so no idea if (or rather when) the cost is offset. Also, it might be useful to have the one box doing everything, it's quite meaty and I have quite a few things I might like to put on there.

I guess if I want a lot of functionality, I'll have to pay for it (in electricity!)

Good thing you're looking at it from this angle, I hear LOTS of people talk about building home servers and don't take power into account.  For some people with larger severs it's almost cheaper to get a VPS through Linode than host a box at home.  For your case though you need to keep it local so definitely get the least powerful system you can get that can handle the drives you hope to throw into it.  Also I'd suggest getting laptop hard drives which use much less power.  Yeah you'll spend more money for them but you might make-up some of that in power savings over time.

---

### Post by Elfy on 2010-11-30
> **lukeiamyourfather said:**
> ... which is about $0.15 depending on the region...

we use £ in England :)

I've not done any calcualtions - but if the cost of fuel here and cost of it there is anything to go by - we'll pay a lot more for our electrickery :)

I suspect that would change the payback period a bit

---

### Post by scottuss on 2010-11-30
> **samalex said:**
> Good thing you're looking at it from this angle, I hear LOTS of people talk about building home servers and don't take power into account.  For some people with larger severs it's almost cheaper to get a VPS through Linode than host a box at home.  For your case though you need to keep it local so definitely get the least powerful system you can get that can handle the drives you hope to throw into it.  Also I'd suggest getting laptop hard drives which use much less power.  Yeah you'll spend more money for them but you might make-up some of that in power savings over time.

Yeah, I looked at getting a VPS but it makes more sense to keep my stuff local.

I'm an IT guy by trade so I'm always thinking of stuff like power requirements!

If anything, I think I just wanted someone else to agree with what I was secretly trying to convince myself to do anyway lol. Some kind of strange call out for justification I think!

Thanks guys! I'm probably going to build a power efficient system

---

### Post by scottuss on 2010-11-30
> **forestpiskie said:**
> we use £ in England :)

I've not done any calcualtions - but if the cost of fuel here and cost of it there is anything to go by - we'll pay a lot more for our electrickery :)

I was thinking that actually! $262.80 is about £168, which isn't *too* bad per year, if that's actually what it would cost, and it really wouldn't. I'd be thinking more like £250 most likely (close to $400)

---

### Post by Elfy on 2010-11-30
> **scottuss said:**
> ... Some kind of strange call out for justification I think!...

Yea - that is not at all crazy - I'd go for it.

Is that OK? :lol:

---

### Post by Elfy on 2010-11-30
Just checked - I pay £0.115 per unit.

---

### Post by lukeiamyourfather on 2010-11-30
> **forestpiskie said:**
> Just checked - I pay £0.115 per unit.

UK£ 0.115 = 0.178733 U.S. dollars

So the estimate I gave might be a little on the low side in that situation.

---

### Post by scottuss on 2010-11-30
Yikes! I pay about 22p per unit for the first 650kWh in a month then 9p per unit after that (if I've read this thing correctly)

That doesn't seem very good... maybe I need to switch provider! Oh man, the Mrs is gonna go mad. I start off with one "little" project and now I start messing with all sorts of stuff.

Hopefully she'll appreciate that I'm saving us money ;)

---

### Post by msandoy on 2010-11-30
I would not bother building a unit for this use myself. Asus Eee box is what you need. It draws about 20Watts at normal use, has HD streaming capabilities via HDMI, totally quiet and it is made to be fixed to the back of your TV. has a dual core atom cpu. 
I have one, using it as a server at home. I was a bit sceptic before I bought it, but it is just perfect for the job.

---

### Post by forrestcupp on 2010-11-30
Walmart has [this Zotac ZBOX atom minicomputer](http://www.walmart.com/ip/ZOTAC-ZBOX-HD-ID11/15172881) that I'm looking at for $214.  It has 4GB RAM and HDMI, but no hard drive.  I'm thinking about getting that and throwing an old laptop drive in it and getting a 2TB external to rip all of my DVDs to.  Then I'll just throw my DVDs in the attic and watch them from the computer.

It's very efficient and they say it's silent after you do a BIOS update.

---

### Post by lukeiamyourfather on 2010-12-01
> **msandoy said:**
> I would not bother building a unit for this use myself. Asus Eee box is what you need. It draws about 20Watts at normal use, has HD streaming capabilities via HDMI, totally quiet and it is made to be fixed to the back of your TV. has a dual core atom cpu. 
I have one, using it as a server at home. I was a bit sceptic before I bought it, but it is just perfect for the job.

I would avoid systems like that as they don't have room for any hard disks. Putting a Mini ITX board in a full size ATX case would be cheap, energy efficient, and would have ample room for hard disks. A much better way to go for a home "server" IMO.

---

### Post by NCLI on 2010-12-01
> **scottuss said:**
> I've decided to take the plunge and get loads of storage to put all of the media in our household onto.

I can't decide whether to build a dedicated box, or use the PC I have hooked up to the TV. It has KVM running a few virtual machine servers for various bits, and is only powered on when being used. However, rather than building a whole new box to be my storage server, I'm thinking of sticking a couple of large disks in and setting up LVM.

So why am I crazy you ask? The box I speak of is a Quad Core Q6600 with 4G RAM. So yes, power hungry. Idle, I don't think it will be *too* bad, but I do expect my energy bills to rise noticably.

What would you guys do? I've asked the Mrs and she gives me a blank look!

Thanks!
No matter what choice you make, I'd recommended using mdadm to setup the drives with RAID5. It's stable, and safe.

ANyway, I would build it using a mini-itx motherboard with an Atom CPU pre-installed, then mount it in a huge tower cabinet in order to make sure you have enough room to expand. I would also reccomend using 2 TB HDDs to build your RAID; they're the cheapest per GB right now.

---

### Post by forrestcupp on 2010-12-01
> **lukeiamyourfather said:**
> I would avoid systems like that as they don't have room for any hard disks. Putting a Mini ITX board in a full size ATX case would be cheap, energy efficient, and would have ample room for hard disks. A much better way to go for a home "server" IMO.

It would also be big, ugly, and loud. ;)

The Zotac Atom minicomputer that I mentioned earlier has a slot for a 2.5" hard drive.  It can also be mounted to the back of a screen, and it's silent after the BIOS update.

---

### Post by lukeiamyourfather on 2010-12-01
> **forrestcupp said:**
> It would also be big, ugly, and loud. ;)

The Zotac Atom minicomputer that I mentioned earlier has a slot for a 2.5" hard drive.  It can also be mounted to the back of a screen, and it's silent after the BIOS update.

Who cares, not like it will be next to your pillow at night or on your coffee table. Most likely it will be in a closet or basement like every other home server. A single 2.5" hard disk is not sufficient for the home server needs of most people, or if it is then they really don't need a home server. Mounting on the back of a screen is a moot point because it doesn't even need a screen. Perhaps you are thinking of a [home theater PC]("http://en.wikipedia.org/wiki/Htpc") and not a [home server]("http://www.118henrystreet.net/Weblog/images/HomeServer.jpg")? They serve two very different purposes and require different hardware.

---

### Post by forrestcupp on 2010-12-01
> **lukeiamyourfather said:**
> Perhaps you are thinking of a [home theater PC]("http://en.wikipedia.org/wiki/Htpc") and not a [home server]("http://www.118henrystreet.net/Weblog/images/HomeServer.jpg")? They serve two very different purposes and require different hardware.
Good point.  I didn't read the OP closely enough.  I just read the part where he said he wanted it to store all of his media, and my brain just started thinking HTPC.  If he's talking about a server (which he obviously is), then you're right.

---

### Post by Khakilang on 2010-12-01
No you're not but your wife will go crazy.

---

### Post by czr114 on 2010-12-02
Based on those electricity costs, a good, dual core Atom makes financial sense. It'll not only pay for itself in 12-18 months (savings after that go right in your pocket), but it'll free up the current gear for another workstation, or you might even sell it to someone who needs the power to help defray your costs.

Also don't forget that the hot-running system you have now is raising your A/C bills. All that power consumption is being vented as heat right into your living area.

Is the £0.115/kWh an average rate, a base rate, or a marginal rate? Some utilities add in surcharges or extra costs for usage above a threshold. I know it's common in California and many places in Europe where getting people to conserve has become a legislative priority. A friend of mine in San Francisco pays more than $0.40/kWh at the margin, even though the first few hundred kWh are like half of that.

If it were me, I'd go with a dual core Atom, 2GB RAM, RAID 1 (2 disks) or 5 (2+ disks)on Western Digital green label 2TB disks (however many are required), and an NVIDIA GPU capable of decoding 1080p.

Make sure the gfx card supports PowerMizer under your preferred driver. No need wasting electricity running it at full clock/voltage the entire time.

Once you get it set up, aggressively kill off some of the unnecessary background daemons, and be sure and run powertop. Keeping it running the lowest pstates whenever possible will be essential. Make use of Ubuntu's power management to spin those drives down when not in use.

The best part about doing this right, power wise, is that the system is effectively free with what you'll save in the 12-18 months alone, unless you go crazy on the storage.

---

### Post by Paqman on 2010-12-02
For my media centre I used a mini-ITX board with a built in Nvidia card. I dropped one of AMD's energy efficient CPUs (Athlon X2 4840e, 45W TDP) into it. It'll output smooth 1080p video to my TV through XBMC (thanks to VDPAU).

My advice is get a less powerful CPU and an Nvidia card and take advantage of VDPAU so that you aren't using the CPU to render your video. My machine idles at 35W, and hits 55W at full HD playback. Plus it's teeny, so quite happily nestles in the TV stand alongside the home cinema and STB.

Check out [mini-itx.com]("http://www.mini-itx.com/store/"), they've got tons of boards, cases, etc, and lots of advice on what is compatible with what.

I'd recommend against putting a small board in a full ATX case. The mini cases have one major advantage: excellent cooling. If the CPU fan is blowing directly out the side of the case within an inch or two then you won't need case fans and the CPU will run very quiet. You don't want a full ATX case with all it's propellers growling away when you're watching video.

---

### Post by lukeiamyourfather on 2010-12-02
> **Paqman said:**
> For my media centre I used a mini-ITX board with a built in Nvidia card. I dropped one of AMD's energy efficient CPUs (Athlon X2 4840e, 45W TDP) into it. It'll output smooth 1080p video to my TV through XBMC (thanks to VDPAU).

My advice is get a less powerful CPU and an Nvidia card and take advantage of VDPAU so that you aren't using the CPU to render your video. My machine idles at 35W, and hits 55W at full HD playback. Plus it's teeny, so quite happily nestles in the TV stand alongside the home cinema and STB.

Check out [mini-itx.com]("http://www.mini-itx.com/store/"), they've got tons of boards, cases, etc, and lots of advice on what is compatible with what.

I'd recommend against putting a small board in a full ATX case. The mini cases have one major advantage: excellent cooling. If the CPU fan is blowing directly out the side of the case within an inch or two then you won't need case fans and the CPU will run very quiet. You don't want a full ATX case with all it's propellers growling away when you're watching video.

Read the entire post please. This doesn't answer the question from the original poster. #-o

---

### Post by Paqman on 2010-12-03
> **lukeiamyourfather said:**
> Read the entire post please. This doesn't answer the question from the original poster. #-o

You're right, I assumed he was thinking of using the quad-core for the media output rather than storage. It's a overkill using that kind of firepower for video, but it's nuts to use it for serving files. I'd only do it as a stop-gap until you could get some more suitable hardware, although if money was tight it might be cheaper (at least in the short term) to use the existing hardware and just suck up the running costs.

Have a look at what chips your mobo will accept. You might be able to pick up a much more efficient, lower-powered one second hand cheaply. The quad-core chip probably has good resale value, it might not cost you anything to downgrade, and then all the power savings afterwards go straight into your wallet.

---

### Post by scottuss on 2010-12-13
I did it. I built a low power machine, Atom CPU with WD Green HDDs, no optical drives etc.

Hardly uses anything in terms of power!

Thanks to all for suggestions

---

