---
title: "Ubuntu Server a fire hazard?"
date: 2007-09-13
forum: Server Platforms
---

### Post by towerofpower256 on 2007-09-13
Hey there all,
My dad is making me turn off my server at night time because 'it could catch on fire'. To put his mind at ease, can anyone give me some pointers to reduce the fire hazard? I live in Eastern Australia so its usually 30* Celsius in the summer (coming up soon) and it seems less dusty at the top of my wardrobe than it is where it used to be (it was so dusty inside that the RAM was *expletive*). So can anyone give me a list of things to do in my situation for a server that would run 24/7 ?

---

### Post by crankcaller on 2007-09-13
You could sit it in a bucket of water?  :lolflag:

*hmm*  I'm not sure what to suggest.  
What's it serving?  web pages or a game server etc?
Does it *need* to be on 24/7

Would a smoke alarm above it appease him?

My girlfriend feels the same way about stuff being left on...
I wanna build a pvr but leaving it on all day to record tv etc would cause arguments i think.

---

### Post by Jolly-Swagman on 2007-09-13
> **towerofpower256 said:**
> Hey there all,
My dad is making me turn off my server at night time because 'it could catch on fire'. To put his mind at ease, can anyone give me some pointers to reduce the fire hazard? I live in Eastern Australia so its usually 30* Celsius in the summer (coming up soon) and it seems less dusty at the top of my wardrobe than it is where it used to be (it was so dusty inside that the RAM was *expletive*). So can anyone give me a list of things to do in my situation for a server that would run 24/7 ?

You could place a an 200mm exhaust above it in your wardrobe { if it is of the built in type} to vent any heat into ceiling cavity and help with airflow,  and make sure that your server pc has at least 120mm space either side and maybe  partition  it off from the rest of top shelf in its own cubical so to keep other things from cluttering it.

Have had a P3 as a firewall box server running like this for about a year  with no problems an it is on 24/7.

AS_ crank_ says depends on what type of server you run do you really need it on 24/7,
I have one only on during business hour and that what the web page also states on it too, actually down for a rebuild at moment


Hope this may be of some help

Jolly Swagman

---

### Post by Brazen on 2007-09-13
sudo apt-get install asbestos ?

---

### Post by towerofpower256 on 2007-09-13
I use it as a web, file and torrent server. I could turn it off but it would be really tedious to turn it on whenever someone wants to use it and then off when they are done.

As for things next to it, between the computer and 'flammables' there is a keyboard and a screen (rarely on unless I need it). That puts bout 30cm between each other. So there's very little for it to set ablaze. the exhaust fan is a good idea though. I'll have to see about that one.

Would rack mounting it be effective? If it's in it's own case wouldn't that help?

---

### Post by cleverselfreferentialname on 2007-09-14
> **towerofpower256 said:**
> I use it as a web, file and torrent server. I could turn it off but it would be really tedious to turn it on whenever someone wants to use it and then off when they are done.

As for things next to it, between the computer and 'flammables' there is a keyboard and a screen (rarely on unless I need it). That puts bout 30cm between each other. So there's very little for it to set ablaze. the exhaust fan is a good idea though. I'll have to see about that one.

Would rack mounting it be effective? If it's in it's own case wouldn't that help?

It's not going to catch on fire unless there's something flammable right on top of it and it's an exceptionally hot day, and that particular surface was very warm. Hardware failure is a concern in exceptionally hot environments, but fire isn't going to happen. When computers overheat, it means a part generally dies, not that they burst into flames. A rackmount wouldn't help too much, they generally cool as effectively as a desktop. If it's exceptionally dusty in there, clean it out every couple months, and the 200mm exhaust fan is a great idea also. Nothing is going to catch on fire, but there is the chance of it overheating.

To eliminate the keyboard and the monitor, you can run cables to a KVM switch at your primary computer, but at 30cm away, I don't think they'll catch fire even if a surface was *exceptionally* hot.

---

### Post by Gordy on 2007-09-14
> **Brazen said:**
> sudo apt-get install asbestos ?

Maybe sudo apt-get install fire department?

---

### Post by lisati on 2007-09-14
Some good ideas in this thread....

I'd probably be more concerned about the kind of people who like having their VCR clock stuck with a a blinking "midnight" display - they're likely to get worked up about trivialities,

---

### Post by towerofpower256 on 2007-09-16
Thanks for all the great replies, I'm getting a shwanky new server case with awesome filters in it today. Still tossing over the exhaust fan idea, if it's needed or not. If dad wants to have a winge, I'll just tell him to look at this thread.

As for the apt-get, I thought about apt-get install asbestos but I think my computer would frown in me giving it cancer. I could really crack a windows joke right there but I'm too tired... but feel free to crack one of your own.:lolflag:

---

### Post by p_quarles on 2007-09-16
In my experience, an overheating computer will simply stop working before it reaches the kind of temperatures that could ignite anything other than highly flammable materials. So -- obviously -- don't store the windex and lighter fuid on top of the server. But the difference between the temperature at which a CPU fails completely (and therefore shuts down and loses heat) and the temperature at which wood ignites is pretty large. 

To be extra safe, I guess, you could buy a really loud smoke alarm, put it on the ceiling above the server, and then mount a fire extinguisher outside the room. I don't think that's necessary, but if it helps assuage fears, then it's helpful. The exhaust fan idea sounds like a *lot* of work for almost no benefit.

And, honestly, the only computers I've ever heard of bursting into flames are laptops with li-on batteries. If you're running a server on one of those then, yes, shut it down while it's unattended.

---

### Post by kokoroexchange on 2007-09-16
Hey,

I put a ventilation system in my attic and have one of the exhaust ports routed over to the spot in my closet just above my server.  It exhausts heat from above the server to keep it cool and works quite well.  The exhaust vent is a 15 cm in diameter vent connected to duct work in the attic.  I did it for heat dissipation but I guess it could be judged as a countermeasure against fire too ;-)

Also contemplating building an enclosure made of drywall as it is fire retardant but it will have to be coated with something so that I don't have the plaster dust from the dry wall all over the place (i.e. inside my computer).

Also, I keep a remote temperature sensor on top of the server.  It's just a normal household temperature and humidity sensor.  It sends a signal to the main readout in our living room every 3 minutes.  I can go up to the main unit and toggle through 3 different sensors.  We have one outside, one above the server, and one in the attic.  

Just some ideas.

Jason

---

### Post by ssam on 2007-09-17
is there a temperature alarm in the bios?

make sure the fans work, there is not too much dust, and plenty of ventilation space.

if it is a laptop, check the battery serial number with manufacturers website, to see that it has not been recalled.

---

### Post by Spazztastic on 2007-09-17
> **p_quarles said:**
> And, honestly, the only computers I've ever heard of bursting into flames are laptops with li-on batteries. If you're running a server on one of those then, yes, shut it down while it's unattended.

Out of all the machines I've worked with, I have NEVER heard of a server catching on fire just from running or overheating. It will shut off, something will burn out, and it will stop running. Odds are you'll smell something burning, but that's nothing more then the processor being burnt to a crisp.

My suggestion is to dust it out regularly (Once every month at least, if not more). Make sure it's properly ventilated. I'd also look into a temperature monitoring system for it. If it gets too high, an SNMP trap or email can be sent.

---

### Post by kokoroexchange on 2007-09-17
Another thing that I forgot to mention in my previous post is that I installed a dedicated electrical line (with a gfi breaker) from the junction box in my house.  This will also ensure that a short causes the breaker to trip thereby eliminating another possible fire cause.  This is a grounded line but my understanding is that for a gfi breaker the ground is not absolutely necessary.

Just another countermeasure for fire to make everyone concerned feel more at ease :-)

Jason

---

### Post by towerofpower256 on 2007-09-17
Heh yea I saw a YouTube video of one of those Li-Ion lappys explode and that's probably what's set my parents off but I think a mate of mine has put their minds at ease;

He told them of a story of how he was really bored once and had an old wooden set of draws at his disposal. He attached some mounting screws and filled each drawer with a mobo, hard drive, PSU and mounted a power button on the front. He made his very own computer farm out of wooden draws. Every time he would open the drawer, he would get smacked with a blast of heat but at no point did *any* of them burst into flames.

And with that, my parents let me keep the computer on 24/7.

---

### Post by eph1973 on 2007-09-17
You could for effect [try this]("http://www.pugetsystems.com/submerged.php") :-P

Or if you don't like that, you could use one of [these]("http://www.cdynamics.com/hazardous-area-computers.html")

---

### Post by vexorian on 2007-09-17
> In my experience, an overheating computer will simply stop working before it reaches the kind of temperatures

The motherboard wants to protect the processor, any over heating sends a terminate signal, I would worry more about the processor than about what's around the computer, doubt things would ignite unless you got some gas or alcohol nearby...

Exploding laptops are a different issue, typically your server is not going to depend on any unstable battery ...

---

### Post by towerofpower256 on 2007-09-18
Hahaha I had a look at the Submersed Computer and I literally 'LOL'ed! That is by far the smartest and grooviest idea I have ever seen with a computer! 3 Thumbs up!

---

### Post by Viruk on 2007-09-18
Do you need keyboard and monitor attached to the server?

You can do almost anything remotely so these may just take up space that could provide more ventilation. I run my servers with only power and network attached. Once in a while it may be necessary to hook up monitor and keyboard as well, but very rarely. 

BTW I run 2 servers are home in a very small cupboard, we don't have the level of ambient temperature in the UK that some countries are blessed with but it can still get pretty warm in the summer months. Both of these run 24/7 and I've had not problems...

---

