---
title: "why not central home computing?"
date: 2020-04-30
forum: The Cafe
---

### Post by anotherChris on 2020-04-30
I personally have really old hardware.  But recently I was thinking about the best way to watch movies in the home, and I thought, *this is house is crazy!*

We have multiple computers lying around.  The laptops need to be moved from the dinner table all the time but then they and all the papers around them have to be temporarily put somewhere else.  External hard drives and other peripherals all have to be connected by wires. Tons of wires, and lots of storage space taken up by hardware and wires.  I never take my laptop out of the house because a portable mini-computer called a smartphone.  Why am I living like this?

Why don't people have central computing?

Like, why doesn't System 76 make a single-source computer/Wi-Fi router/hub thingy that sits between the Internet and some varieties of terminals (whether they be TVs or monitors or whatever)?  

-All the fans, heat and noise would moved to single place away from people.
-terminals could be more lighter, larger, and more ergonomically flexible than laptops.
-computers could share back-up space and a single central computer could be extensible in terms of the number of terminals it served.

I want a giant, big flat-screen display with an ergonomic keyboard that I can move around easier than a laptop within the house without being necessarily able to be moved out of the house, and I want all wires for HDD etc to be gone, and I want all hardware besides monitors and keyboards in a single place.

Why aren't people doing this?  I mean, my parents just bought two new laptops, so they now have 4 laptops for 2 people in their living room.  Plus a desktop downstairs and other stuff.  That's crazy.

---

### Post by QIII on 2020-04-30
People who are interested in such things set them up for themselves all the time.  They use any OS they wish.  The ability to easily create nearly infinite configurations makes a "canned" product unmarketable.  Many of us who haunt these forums are well versed in home networking. Instruction and advice are free here.  Hardware capable of doing what you want can be had for a song.

On the upper end:  I have one machine that has 13 virtual machines available, each with its own private NIC.  Those all run through a gigabit switch and could be configured to accept connections over wifi from specific machines.  With the host's 32 cores and 128GB of memory divided between them, each of those VMs is actually pretty powerful.  I could use cheap Raspberry Pis as pretty capable terminals to remote into them.

Even with a much more modest machine with six cores and two or three VMs, one could use an RPi to remote in.

A simple solution for movies:  Connect your smart TV, laptop, Raspberry Pi, etc, via wifi to a home media server built of spare parts and duct tape to stream content.  There is certainly no need for an expensive commercial product for that.

Caveat: one has to be aware of DRM laws in their jurisdictions to avoid legal issues.

---

### Post by CatKiller on 2020-04-30
As QIII says, there are a bajillion different ways to have thin-client or thin-client-like setups. WiFi makes it particularly useful.

For your scenario, it sounds like you'd particularly like a [NAS](https://en.wikipedia.org/wiki/Network-attached_storage). They're simple to set up and use, and pretty cheap. I've got a Synology unit that holds my backups, distributes media files to all the machines in the house (including tablets, laptops, phones, HTPC behind the TV, stereo in the bedroom), and seeds torrents. I can also stream games around the house from my gaming rig to my HTPC or laptop using Steam's In-Home Streaming. And having cloud computing, cloud storage, and all the other ways that things are simply done online is also very thin-client-like.

---

### Post by anotherChris on 2020-04-30
Yes, that NAS sounds like what I was thinking about!!

---

### Post by anotherChris on 2020-04-30
Sounds cool.  As you can probably tell, I am pretty ignorant about such things.  I should learn more and trying making something for myself!

---

### Post by CatKiller on 2020-04-30
I like the Synology boxes. You can definitely go cheaper or more flexible, but you can't have as nice, or as easy, for cheaper. You configure it just through a web page.

As well as the actual storage part, the other part that you'd probably be interested in is [DLNA](https://en.wikipedia.org/wiki/Digital_Living_Network_Alliance). That lets machines on the network discover each other, negotiate capabilities, and share files in a straightforward way.

If you built your own box you could have a big gaming machine with lots of drives that could serve as a game & media streaming machine that also does file storage and hide it away (somewhere cool). Or you could break those tasks up over multiple machines. Or just do some tasks and some completely different tasks. Everyone has their own capabilities and priorities: one person's solution might be completely inappropriate for someone else.

But, now that you know that these things exist, you should be able to find out enough about different approaches to choose which one fits you best.

---

### Post by Tadaen_Sylvermane on 2020-05-01
I set up kodi machines throughout my home for local media use. All media is on the main server in the guest room. The individual machines all boot from a single image on the server. No hard drives in any of them. They aren't mobile though. Mounted on wall behind screens. Wired networking required. But it is all centralized.

Different options. How far down the rabbit hole do you want to go?

---

### Post by Hwæt on 2020-05-01
I've got an Intel NUC I use as a build server, with a RPI in the other room for some experimentation with a USB camera I bought. It works well. I host some git repositories on the NUC, as well as host FTP in addition to using it as a build server. If I have to use Windows, I can use CLion's remote development tools to just hook into the NUC box or the RPI.

---

### Post by anotherChris on 2020-05-02
Is that diphthong medieval church Latin pronunciation, or classical Latin pronunciation?

---

### Post by QIII on 2020-05-02
Probably the Old English pronunciation, where it rhymes with "sat".  It's the first word of ***Beowulf***.

---

### Post by mörgæs on 2020-05-02
In Icelandic the Æ is alive and well today. It's pronounced like the English I.

Off topic, I know. Switching back to lurk mode.

---

### Post by anotherChris on 2020-05-02
> **mörgæs said:**
> In Icelandic the Æ is alive and well today. It's pronounced like the English I.

That would be the same as classical Latin.  In classical Latin, the name Caesar is pronounced like the German word Kaiser (for king).  The usual English pronunciation "see-zur" is based on medieval church Latin.

---

### Post by Hwæt on 2020-05-02
> 
Probably the Old English pronunciation, where it rhymes with "sat". It's the first word of Beowulf.


This is correct - it is the æsc from Old English. :)

Though I'm notoriously inconsistent on pronouncing it.

---

### Post by TheFu on 2020-05-02
I've been doing remote computing for about 25 yrs. It has gotten better and better as networking has improved.
The easiest way is using remote X11 from one Unix-like OS to another.

```
$ ssh -X userid@ip  run-some-command
```

So, if I want to run firefox on a different system, but have the "window" shown on the system I'm on, I'd use
```
ssh -X  hadar  firefox &
```
That "run-some-command" can be almost anything, except a full desktop or a command that needs direct access to the GPU. Gnome3 doesn't work, for example, but xterm, firefox, thunderbird, and too many other programs to name do.

Then there are NX-based remote desktops.  There are free, F/LOSS and commercial versions. Most fo them are incompatible between the different vendors/projects. NoMachine makes a commercial version and a limited version that's closed.  x2go makes a F/LOSS version that works really, really well.  I use this almost all day, every day to access my primary desktop.  That desktop runs inside a modest KVM VM under a modest physical machine. That VM host machine runs about 10 other VMs too. They all fit well within 16G of RAM and there is plenty of CPU left over.  In fact, there's so much CPU left over, I've ordered 16G more RAM ($70) to better utilize the hardware.  10 VMs and 3 LXD containers running on that since sub-$500 box.  Audio mostly works fine. Video playback works if the data is transferred, not the images.  Streaming video systems send the data to be rendered by the client machine for best viewing.  That's why a $40 raspberry pi can playback 1080i HiDef videos fine.
NX uses ssh tunnels. This is part of the NX protocol, so if you have ssh working between the client and server, then you've done the hard part ... which actually isn't very hard at all.

Then there are the popular, but highly, highly, non-secure RDP and VNC options. Once I found NX (x2go), I never looked at VNC again. 

For a while, there was a single-computer and multi-head solution. A "head" is short for keyboard, video, mouse connections back to a computer.  Our typical desktops today could probably support over 100 ssh connections, provided they don't use a GUI.   I remember the says when a mainframe had 8MB of RAM and 300 users too.  If a GUI is needed, then assume 1 GPU for each "head."  There was a project "LTSP" for this. Think that died.   The main issue I saw was that video doesn't like long cable runs.  

I suspect the LTSP guys all moved over to using small, smart clients, like raspberry pi computers to do stuff these days.  A raspberry pi v4 is pretty impressive, if a little overpriced.  We are paying for the PI community. There are cheaper, faster, ARM-based computers, but they lack the Pi community. It matters.

There are some other techniques, but those are completely dependent on having specific hardware, specific commercial licenses, for the solution to work.  "Commercial" doesn't interest me at all.  I'm thinking about nvidia having a network-based remote GPU solution. They aren't charging home users for the licenses, but I understand the license must be requested and only their higher-end GPUs support it.  My $70 nvidia 1030 won't.

On the same LAN, use **ssh -X**.  It is so very easy, very secure, and hides some complexities that would confuse new users.  Over the internet, use x2go.

---

### Post by DuckHook on 2020-05-02
> **CatKiller said:**
> I like the Synology boxes. You can definitely go cheaper or more flexible, but you can't have as nice, or as easy, for cheaper. You configure it just through a web page.
*Provided* you bother to configure it correctly. Many (if not most) owners of Synology boxes whom I know do not bother to do so. They succumb to what I call "appliance disease", thinking that a Synology box is basically a toaster—just plug & play. Begging to be pwned.
> **TheFu said:**
> On the same LAN, use **ssh -X**.  It is so very easy, very secure, and hides some complexities that would confuse new users.  Over the internet, use x2go.
I tried *ssh -X* between a powerful host and a RPi 4 and it wasn't a smooth experience. Perhaps because one leg was over WIFI, but it was a strong 5Ghz signal, so I doubt that was the bottleneck. You've mentioned x2go many times in the past, so that will be my next experiment.

---

### Post by TheFu on 2020-05-03
> **DuckHook said:**
> * I tried [I]ssh -X* between a powerful host and a RPi 4 and it wasn't a smooth experience. Perhaps because one leg was over WIFI, but it was a strong 5Ghz signal, so I doubt that was the bottleneck. You've mentioned x2go many times in the past, so that will be my next experiment.

I think of rpis for media players.  Have a v2 and v3 doing just that both running osmc (kodi distro).  The arm cpu isn't a problem because all video streams are converted to h.264 by a more powerful plex server.  never used either for desktops.  Also, I don't use wifi.  Designed wifi deployments at work and learned when deploying over 1200 locations that wifi always sucks.  always.  The signals are always fluctuating even in the best situations. Best to just avoid wifi.  Plug in an ethernet cable and see how the rpi performs.  I use powerline ethernet rather than wifi. Powerline provides consistent throughput.  Consistency is more important than peak bandwidth.

x2go has a few limitations.  No android client.  No iOS client.  The linux, windows, osx clients work well.  By tuning the bandwidth and image compression settings, the performance can be excellent over most networks and distances.  Choose ISDN for the network and x2go should fly.

That limitation changed how  travel.  Was using a 4" Nokia tablet, then tried using a 10" android tablet, but for the last decade, have been taking a laptop.  Would love to travel with a 7 inch tablet and mini-keyboard, but x2go is a necessary fallback for me still. Android just isn't enough OS for me and running a Linux desktop inside a chroot under android wasn't very good all sorts of issues.  For travel, the best solution I found was a light laptop (sub-3lbs), usually an 11-13 inch chromebook running ubuntu-fvwm w/ a USB3-GigE adaptor. ChromeOS wiped.

For around the house, there are just so many choices. Usually a laptop or I'll just work in my home-office.  For media control, bubble-upnp controls the systems in 3 rooms from any android device. I don't have a way  to synchronize playback for more than 1 room, however. Haven't really looked for that.

---

### Post by Shibblet on 2020-05-05
I think it's habitual.  We all get set in our ways (seems like around age 40) about how we do things.

For example: My mother just recently asked to borrow my laptop, so she could log into TurboTax to do her taxes.  I asked her why she doesn't just use the app on her smartphone?  To which she replied... "Well, I didn't know you could."

Online Banking is not something your grandparents will ever use.  They don't want to make payments over the phone, or on-line.  They are perfectly happy spending the entire day running all over town, going from place to place, paying bills.  I mean, who writes checks, when you have a perfectly good Debit/Credit Card?

A lot of it is generational, sure, but a lot of people just like doing things the way that they learned how.  This is why Windows took such a beating from the public when they made Windows 8.  All of the standards they had put in place since Windows 95 were all somewhere else now.

---

### Post by SeijiSensei on 2020-05-06
> **Shibblet said:**
> Online Banking is not something your grandparents will ever use.
I've yet to see any grandchildren, but I am over seventy and have been using online banking for years.

The extent of ageism in forums like these is pretty disturbing.

---

### Post by EuclideanCoffee on 2020-05-06
> **SeijiSensei said:**
> The extent of ageism in forums like these is pretty disturbing.

I'm sad to hear this as you certainly are one of the most knowledgeable users here.

I don't think age is really the concern, just some form of bigotry or ignorance.

---

### Post by DuckHook on 2020-05-06
I'm sure Shibblet *intended* no offence, although I also understand SeijiSensei's point: that ageism does not require intent and is problematic precisely because it is so pervasive as to be offensive even when presented without malice.

Speaking *as* a grandparent then, I was not offended by Shibblet's comment. I took it as a figure of speech that is based on a generalization. As most generalizations go, it has a statistical basis in being *largely* true while failing in *specific* instances. Most—but not all—people old enough to be grandparents are also more resistant to adopting the latest IT craze. I know very few people my age (and I know a lot of people my age) who twitter, instagram, online bank or are IT savvy in general. The few who do, like SeijiSensei (or me), are outliers.

It behooves us to remember that there is a balance to these things. The same generalization that relegates older people to the ranks of the IT-challenged also ascribe more life experience and wisdom to us. This is just as much a generalization as the other, but in reverse. It is also just as problematic when instantiated: I know far too many old fools.

Perhaps it's best to take a deep breath and try to remain charitable in these fraught times. We all stumble. When it's my turn, I hope that you will all extend a hand and help me pick myself back up.

To get back on topic:

Thanks to TheFu's introduction, I've recently discovered the joys and tribulations of RPis. After getting them working, they're fantastic. But it was certainly an adventure getting them working. I didn't want to use Raspbian, so the adventurous part was getting Ubuntu (actually, XFCE) working. The server image is not hard, but the DE was more challenging. There's not a lot of info to be found on line. But after cobbling together hints and workarounds from many sources, I've finally kicked them into shape. Three RPi 4B+ running everything from a micro NAS to a LibreElec streaming box to a full desktop replacement. All three combined have set me back less than what I would have spent for one machine in the past. It's been a very interesting rollout. When it's time to upgrade Mrs DuckHook's computer, I will likely go the thin provisioning route with an RPi. If all one uses it for is surfing, playing audio/visual and the occasional document, it has enough power to get the job done.

---

### Post by TheFu on 2020-05-06
Please don't blame me for any rpi use as a desktop.  ;)  rpi hw is pretty expensive for what we actually get.  Check out odroid and pine64 options for much more powerful systems at similar prices. If you are in the US, Ameridroid has many of the systems.  Tell them I said hello.

Did you ever try x2go?  How's that working?

---

### Post by DuckHook on 2020-05-06
> **TheFu said:**
> Please don't blame me for any rpi use as a desktop.  ;)  rpi hw is pretty expensive for what we actually get.  Check out odroid and pine64 options for much more powerful systems at similar prices. If you are in the US, Ameridroid has many of the systems.  Tell them I said hello.

Did you ever try x2go?  How's that working?
Now my interest is piqued in these other platforms. You will be the ruin of me yet. :P

x2go works quite nicely. There's still lag, but less of it than with pure *ssh -X*. I don't have a choice on the WIFI front. The RPi must be situated in a place that has no ethernet cabling. I'm actually okay with this for my use case. I'm used to the pure CLI environment these days, so the GUI access was more for curiosity than for anything else.

I'm finding that the main advantage of RPi is the huge community that is behind it. If I'm overpaying a bit for the HW vs competitive HW like odroid or pine64, the community resources more than make up for it. But now that you've got me interested in tinkering with these things again, I doubt I'll be able to resist either odroid or pine64. Goodness knows I have enough time on my hands these days.

---

### Post by Shibblet on 2020-05-06
> **SeijiSensei said:**
> I've yet to see any grandchildren, but I am over seventy and have been using online banking for years.

The extent of ageism in forums like these is pretty disturbing.

Clearly this is just a generalization.

---

### Post by 1clue on 2020-05-07
You basically just described ChromeOS. Only with local storage and possibly local processing.

One typical vendor of hardware that does this (apps, not chrome specifically) would be Synology. They market NAS, but those systems can add apps as well, so it's pretty point-and-click to setup your local services. Another vendor is Antsle.

If you like you can configure a VPN on your router so you can get to your app server from outside your home wifi. Be careful about security!

Seriously though, you should add up all the power your old devices use and consider getting a well-chosen newer system or systems. The sort of services needed in a home don't need a monster CPU, but often benefit more from a bunch of really small cores. Antsle uses Intel Atom, their antsle 1 is a c2750 I think, which is 8 cores and it's based on Gentoo Linux. I have pretty close to the same hardware, I like it a lot. The Antsle box is fanless so it's silent. My build has fans but they're pretty quiet, and very low power consumption.

---

### Post by Tadaen_Sylvermane on 2020-05-07
> **SeijiSensei said:**
> I've yet to see any grandchildren, but I am over seventy and have been using online banking for years.

The extent of ageism in forums like these is pretty disturbing.

I agree it can be. However I also know from personal experience that you are in the minority in regards to "older ones" being comfortable, daresay knowledgeable about tech of any kind from my perspective. My grandparents for example can't figure out why the internet dies on their laptop every few days. So I trot over there and press the airplane mode button on the laptop. They think I'm a genius. For the record, I have explained this concept to them many times. Another older lady I helped out has had several tablets all "break, they're junk". Problem was she was downloading everything she could find and didn't comprehend that these things have limited storage space. She was also going to throw her computer away that I had put Xubuntu on because it was "trash and broken". She had logged out of Xubuntu and changed from her user to the Other user option, therefore anything she tried didn't work. Maybe that was my fault not to setting an automatic foolproof login. This happened a couple times. I have many other incidents like these involving quite a number of people in my area.

Point being, yes people do automatically assume older ones don't know or want to know stuff like this. Sad part is that is my reality. The only person I know > 60 who doesn't seem to be afraid of anything electronic, does like to tinker and try random stuff where his computer and devices are concerned is my father. And he has been doing everything online for awhile now as well. Maybe he passed that tinkering thing to me and here I am.

---

### Post by TheFu on 2020-05-07
Perhaps comfort w/ technology is related to education and vocation more than age?  Almost everyone in my extended family uses computers for their jobs and most are in technology fields. A few are quite savvy about multiple OSes and others just use computers as tools.   Most of them have  a home server, usually linux.  4 of us run servers on the internet.

I&#8217;ve come across so many college students, in EE and CS majors who were pretty clueless about computers.  They have the misconception that being a user makes them some expert. it does not. it is a case where a little perceived knowledge is a dangerous thing.

---

### Post by QIII on 2020-05-07
And now a word from the "management":

Much of what people are saying here about people having trouble with things tech applies to both young computer users and old.  I run into just as many youngsters who can't figure things out or don't understand the most basic of concepts -- teenagers included.

We Boomers were around for the advent of the personal computer and have been using them since.  We're producing grandchildren.  My Dad, well into his 80s and a ***great-grandfather*** multiple times over before he died, was a computer whiz.

If I were to hazard a guess, I'd say that the average age of the Staff on the forums is in the range of 50 and the Admins are in the range of 60.

Even as a figure of speech, when it comes to tech a phrase like "... your grandparents ..." is inaccurate and ageist.  Let's just remove any such concepts (and sexism, for that matter) from what we write here on the Ubuntu Forums.  OK?

Back to the original discussion, please.

You may now return to your normally scheduled programming.

---

### Post by Shibblet on 2020-05-07
> **QIII said:**
> Even as a figure of speech, when it comes to tech a phrase like "... your grandparents ..." is inaccurate and ageist.  Let's just remove any such concepts (and sexism, for that matter) from what we write here on the Ubuntu Forums.  OK?

Back to the original discussion, please.

I mean, it's easy for you to say... you're not the one being blamed for "ageist" comments.

I personally would call this a "cherry picked" argument, and that someone intentionally wanted to be offended.  They didn't look at the part that said "over 40."  How old would that make my Grandparents?
Secondly, I did say "your grandparents," and ironically the person that responded was in his 70's.  How old would "your grandparents" be, if you are 70?  Did they ever use online banking?

Personally, I don't appreciate the "ageist" comments.

---

### Post by Irihapeti on 2020-05-07
This thread has run its course. Closed.

---

