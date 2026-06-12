---
title: "Are all rackmount servers this LOUD?"
date: 2011-07-04
forum: Server Platforms
---

### Post by kenquad on 2011-07-04
This isn't Ubuntu-specific, but I hope it will be okay since it's server-related and there are so many server experts around here :p

We just purchased our first rackmount server for the home office, an HP Proliant, ~7 years old with dual 3.2Ghz Xeons and dual SCSI hard drives.  When we turned it on for the first time, it sounded like a blowdryer, if not a vacuum cleaner.  This noise throttled down after a few seconds, but as the server began to get hot an hour or two later it kicked back up.  

Is this normal?  If so, a data center at peak usage must sound like the main runway at LAX ;)

Since this is the first rackmount box we've ever used (always used repurposed desktop towers before), we want to make sure there isn't something wrong with it.

Thanks server people!

---

### Post by ian dobson on 2011-07-04
Hi,

Rackmount servers are loud. They're normally installed in air condition rooms where noone works, so noise isn't really a problem. Saying that your "new" server is 7 years old and it could well be that the fans are old and dusty/screwed bearings.

Regards
Ian Dobson

---

### Post by mjo1989 on 2011-07-04
It's normal for the fans to spin at full speed when you first turn it on.

They shouldn't be spinning at full speed in normal use unless your putting some extreme load on it. Sounds like it's getting a bit hot so make sure it and the room is getting sufficient cooling..

---

### Post by Gyokuro on 2011-07-04
Your new toy has it's age ;) - you can try to clean it from dust and normally you have them in server racks which have cooling and noise reduction and you administer them from a remote place :-). Maybe you can find a small second hand 19" rack with a door where you can host your HP Proliant. 

Have fun with it - it's a good workhorse

---

### Post by arrrghhh on 2011-07-04
Yup, everyone is right here.  Try cleaning the beast out... but no matter how you slice it, the thing will be loud.

Server rigs they put usually a lot more fans in, and usually beefier fans to move air better.  Again, most rack mounted servers are in a data center that noise is not a problem - our data center is pretty loud, and I've heard/been in way worse DC's.

---

### Post by 1clue on 2011-07-04
Rack mount hardware, they focus on getting as much as possible into the smallest possible space.  The fans are designed to be effective, not quiet.

Another thing that doesn't seem to be directly addressed is that a server room is supposed to have external climate control (both temperature and humidity) that is drier and colder than where the people sit.  Walk into a properly set up server room and you'll want a sweater.  Stay there awhile and you'll notice the dry air.  Try to talk with somebody and you'll need to raise your voice to the verge of yelling.

There are climate controlled racks, but even used they will be more than you spent on your server.

Running your server in a "normal" room will tax its ability to keep cool.  The fans will run faster, longer than they would if it were properly cooled.  They will probably be able to keep up, but if your fans were used hard like that for the entire life of the machine then chances are they might be the first thing to die.

There are 2 reasons for a server like that to come onto the market.  The first is that the company has upgraded the server, which probably means they feel that the hardware might be worn out and prone to failure soon.  This would be bad for you.  The second reason is that the company went out of business and the hardware might be good yet, which would be good for you.

You said 7 years though, which gives me the impression that your hardware comes from a small to medium size company that is just starting to get into the groove of organized IT management.  So probably you have worn out hardware that might have failures soon.

---

### Post by kenquad on 2011-07-04
Thanks to all for the quick and informative feedback.  I kinda figured this was normal, though I'd rather believe it isn't ;)  Despite its age, the server (which was reconditioned by the way) is VERY clean inside, so I'm afraid the current noise level is what we're left with.  Unless, of course, we pursue replacing the fans, which I doubt we will as the sound it's making doesn't seem like bad bearings to me.

Thanks again.

---

### Post by psusi on 2011-07-04
Rack mount servers are made to be small, so they use small fans.  Small fans have to spin much faster to move the same volume of air, which makes much more noise.

I hope you didn't pay more than $50 or so for such an old system that otherwise was on its way to the recycle bin.  At 7 years of age, those hard disks are likely to fail soon.  You should run the long SMART diagnostics on them fairly regularly to hopefully detect the failure before it becomes catastrophic.  See the smartmontools package.

Then again, 7 year old hard disks are probably only what?  20-30 gb?  I'd say you should probably just replace them, but you said they are scsi, so finding a scsi replacement at a reasonable price might not be easy these days.  I don't think they even make them anymore.

---

### Post by 1clue on 2011-07-04
Chances are you won't find a fan that's much quieter and still able to put out the same amount of air.  Those fans are "built to spec" and designed to be replaced with some other fan of the same spec.  That spec includes volume of air moved at a certain voltage/current.

One promising fact is that more recently manufacturers have realized that efficient fans are quieter in the same situation, and that efficient fans use less energy than inefficient ones.

---

### Post by kenquad on 2011-07-04
BTW, I gave the age of the server incorrectly.  I was going on the release date of the processor, which is 2004, but the copyright on the BIOS has the year 2006, so the unit can't actually be more than 5 years old.  The hard drives are 73GB.  I've got them mirrored with RAID 1+0, so I'm not too awfully worried about disastrous failure :p

---

### Post by tgalati4 on 2011-07-04
I have a couple of Dell PowerEdge 1750's that are 2004 vintage.  They have 7 fans in them and they spin at 15,000 RPM at boot then throttle down to ~6300 RPM during use.  The BIO will spin up the fans to max as a test and if any fan fails during use, it will also spin up the fans to maximum speed to compensate.  That way, if one of your servers is blinking (due to a hardware failure), you can query it with a tool (Dell's OMSA, which runs fine under Ubuntu server) to see which fan went bad or which component is acting up.

For the noise problem, I set up a small rack in my garage and I have them powered on remotely using wake-on-lan and only use them for development work, otherwise they are asleep.  I used asphalt shingles hung around them; that makes an effective noise dampener.

Although I do have a small monitor in the garage, I use them in headless mode, so I can wake them with a small script from my laptop:

wakeup.sh


#!/bin/sh
# Super cheesy script to wake my server and put up a notification to that effect
#
/usr/bin/wakeonlan xx:11:43:xx:4f:f1
sleep 3
/usr/bin/wakeonlan xx:11:43:xx:4f:f1
sleep 3
/usr/bin/wakeonlan xx:11:43:xx:4f:f1 
sleep 2
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "Drupal7-dev Server is Booting"  "You'll be up in 3 minutes."
sleep 200
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "Drupal7-dev Server is Alive" "You can login now."
echo "The current time is:"
DISPLAY=:0.0; notify-send -i clock "$(date +"%H:%M")"
exit 0

They do use some power.  A dual-Xeon (4 cores total) 2.8 GHz will run ~200 watts at idle and 240 watts when compiling code.  That is why the push to virtualization.  10 machines running at 10% load can be crammed into one machine at 90% load and the power savings becomes significant.

---

### Post by psusi on 2011-07-05
> **tgalati4 said:**
> They do use some power.  A dual-Xeon (4 cores total) 2.8 GHz will run ~200 watts at idle and 240 watts when compiling code.  That is why the push to virtualization.  10 machines running at 10% load can be crammed into one machine at 90% load and the power savings becomes significant.

Then why did you have those 10 machines in the first place?  I have never seen a company in the habit of buying more servers than they need, so if they could run everything on one server they would, and you don't need virtualization for that.

---

### Post by Lloyd_mcse on 2011-07-05
Rackmounted servers tend to use Passive heatsinks and therefore requires a greater airflow from the fans.
My old Dell Poweredge 2600 Pedastal server has passive heatsinks and boy is that loud :s

---

### Post by yakatz on 2011-07-05
> **psusi said:**
> Then why did you have those 10 machines in the first place?  I have never seen a company in the habit of buying more servers than they need, so if they could run everything on one server they would, and you don't need virtualization for that.

Sure they do. I worked with a financial services company that bought a new server for every server-based product (I was decommissioning the servers when the firm closed). Most of the servers spent most of their time doing nothing.
There was an exchange server, a blackberry enterprise server, an active directory domain controller, then four other servers each with a single specialized financial program running on it.
Each specialized server had an account for the vendor's support staff to log in (having separate servers also helps compartmentalize the vendors).
They could have done it all on a single server using virtualization.

---

### Post by psusi on 2011-07-06
> **yakatz said:**
> Sure they do. I worked with a financial services company that bought a new server for every server-based product (I was decommissioning the servers when the firm closed). 

I guess that explains why they went out of business.  The successful companies don't hire incompetent people that waste resources like that.

> **yakatz said:**
> They could have done it all on a single server using virtualization.

They also could have done it all on a single server without virtualization, and its associated overhead.  That's how people used to do things before virtualization got all popular.

---

### Post by yakatz on 2011-07-06
This is a bit off topic...

> **psusi said:**
> I guess that explains why they went out of business.  The successful companies don't hire incompetent people that waste resources like that.
Nope. They closed after making a decent profit and the partners whanted to move on to something else. They closed with money left over after they had paid ALL the investors. This is evidently a common practice with hedge funds.

> **psusi said:**
> They also could have done it all on a single server without virtualization, and its associated overhead.  That's how people used to do things before virtualization got all popular.
Not only can you not compartmentalize each program and each remote access channel on a Windows server...  when you give a 3rd party administrator access to any server (as part of their maintenance contact, so they can install updates, which also seems to be standard practice in many parts of the finance industry), you can't run anything else on that server. Period. No matter what operating system it has.

---

