---
title: "Got hired as a PC tech"
date: 2009-05-21
forum: The Cafe
---

### Post by Chowzor on 2009-05-21
After working in Pc sales for a year, i had to move city's quickly and got hired at a local bestbuy as a instore tech.  Couple of concerns, i am proficant in hardware ect.  Just not sure of a few things.  If a harddrive fails and you need to do a complete disk image anyone know of a good free (open source preferably) that i can use that for.  

Virus removal..i have some apps from my old place of employment that the tech there used.  I am also familier with manual removal.

Also what other programs do you think i should keep on hand?  Im a little nervous, i know i can do the work i just want to be prepaired for everything.

---

### Post by Rainstride on 2009-05-21
> **Chowzor said:**
> After working in Pc sales for a year, i had to move city's quickly and got hired at a local bestbuy as a instore tech.  Couple of concerns, i am proficant in hardware ect.  Just not sure of a few things.  If a harddrive fails and you need to do a complete disk image anyone know of a good free (open source preferably) that i can use that for.  

Virus removal..i have some apps from my old place of employment that the tech there used.  I am also familier with manual removal.

Also what other programs do you think i should keep on hand?  Im a little nervous, i know i can do the work i just want to be prepaired for everything.

if the harddrive has completely failed, its game over for that drive. a live cd is a great utility to keep around, it comes with memtest(unless something has changed) so you can make sure the ram is fine. also, if you have a drive about to fail you can use a live cd to try and get as much data as possible off it before is craps out.

---

### Post by MaxIBoy on 2009-05-21
> **Chowzor said:**
> After working in Pc sales for a year, i had to move city's quickly and got hired at a local bestbuy as a instore tech.  Couple of concerns, i am proficant in hardware ect.  Just not sure of a few things.  If a harddrive fails and you need to do a complete disk image anyone know of a good free (open source preferably) that i can use that for. Clonezilla. But if the thing has actually failed, the costs are going to be in the tens of thousands to recover the data (probably much more to buy your own equipment for it.)

> Virus removal..i have some apps from my old place of employment that the tech there used.  I am also familier with manual removal.

Also what other programs do you think i should keep on hand?  Im a little nervous, i know i can do the work i just want to be prepaired for everything.More often than not, a full reinstall is just easier. You should still scan all the files after recovery though, because viruses have a habit of embedding themselves in sound files, word documents, etc. They wait for a specific program (usually MS Office, IE, and WMP are the targets) to open them, where they exploit buffer overflows to execute malicious code. 

To scan files for viruses, I'd recommend a combination of scanners. AVG, Avira, and ClamAV are all free-of-charge scanners, but they're proprietary. Pick some combination of two of the above, that should catch almost everything. 

If you absolutely need to keep the existing installation intact, don't count on system restore, which only rarely works (any self-respecting malware made by a 12-year-old script kiddie will automatically delete system restore points.) MalwareBytes AntiMalware is a good tool to get a computer back on its feet, so you can then install some more-sophisticated tools. 




Best idea, though, is to remove the hard drive, stick it in a Linux machine, and run some scanners on it (many virus scanners have Linux versions.)

---

### Post by rob2uk on 2009-05-21
If a drive fails physically, then you don't have much chance of restoring it with software.

a *nix LiveCD is always a useful thing to have around, as is a USB IDE/SATA drive caddy.

Foremost and Scalpel are good for recovering deleted files.

Oh, and I always keep a copy of [PC Wizard]("http://www.cpuid.com/pcwizard.php") on a thumbdrive - comes in handy when trying to solve driver issues on 'doze boxes

---

### Post by Wiebelhaus on 2009-05-21
> **Chowzor said:**
> After working in Pc sales for a year, i had to move city's quickly and got hired at a local bestbuy as a instore tech.  Couple of concerns, i am proficant in hardware ect.  Just not sure of a few things.  If a harddrive fails and you need to do a complete disk image anyone know of a good free (open source preferably) that i can use that for.  

Virus removal..i have some apps from my old place of employment that the tech there used.  I am also familier with manual removal.

Also what other programs do you think i should keep on hand?  Im a little nervous, i know i can do the work i just want to be prepaired for everything.

I don't have time to post what your thread deserves , but I'll come back asap , I have 8 years and 7,000+ service orders under my belt and would be more than happy to speak to you about this , please feel free to PM or email , cheers.

And by the way , I use Linux to do all of my work.

---

### Post by logos34 on 2009-05-21
> **Chowzor said:**
> Also what other programs do you think i should keep on hand?  Im a little nervous, i know i can do the work i just want to be prepaired for everything.

[Ultimate Boot CD (UBCD)]("http://www.ultimatebootcd.com/")

it's packed to the gills with diagnostic apps

---

### Post by MikeTheC on 2009-05-21
If your employer isn't providing you with all the necessary and appropriate tools to do your job, then clearly you shouldn't get yourself mixed up with them.

---

### Post by dmizer on 2009-05-21
> **Chowzor said:**
> If a harddrive fails and you need to do a complete disk image anyone know of a good free (open source preferably) that i can use that for.
Not open source, but fantastic and has helped me out of a lot of jams: [http://www.miray.de/products/sat.hdclone.html](http://www.miray.de/products/sat.hdclone.html)

> **Chowzor said:**
> Virus removal..i have some apps from my old place of employment that the tech there used.  I am also familier with manual removal.
As mentioned, [AVG](http://free.avg.com/) is a good tool. I have also used [avast](http://www.avast.com/) but it requires registration. There are a few good online tools as well:
[LIST]
[*][http://www.spywareguide.com/](http://www.spywareguide.com/)
[*][http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)
[*][http://www.bitdefender.com/scanner/online/free.html/ie.html?url=scan8/ie.html](http://www.bitdefender.com/scanner/online/free.html/ie.html?url=scan8/ie.html)
[/LIST]

> **Chowzor said:**
> Also what other programs do you think i should keep on hand?  Im a little nervous, i know i can do the work i just want to be prepaired for everything.
I always keep a copy of [knoppix](www.knopper.net) in my toolkit. It's packed with tons of great tools including virus scanners, networking utilities, and hard drive utilities.

> **MikeTheC said:**
> If your employer isn't providing you with all the necessary and appropriate tools to do your job, then clearly you shouldn't get yourself mixed up with them.
As with most retail techs, I suspect that what's allowed to be done will be extremely limited. Probably limited to things like simple virus removal, doing a restore, or RTM.

---

### Post by Zzl1xndd on 2009-05-21
I think people have covered most of the basics so far, But I will extend the same offer as Wiebelhaus. 

I spent a number of years as a Tech and in Desktop support if you need any assistance feel free to send an PM.

---

### Post by starcannon on 2009-05-21
> **MikeTheC said:**
> If your employer isn't providing you with all the necessary and appropriate tools to do your job, then clearly you shouldn't get yourself mixed up with them.

I don't know about that. My dad has been a Diesel Mechanic for over 30 years now, and he has always been expected to provide his own tools. Thats life as a tech in most every industry, you bring your own kit, they supply a bench and a safe place to work.

---

### Post by eragon100 on 2009-05-21
> **MaxIBoy said:**
> 

To scan files for viruses, I'd recommend a combination of scanners. AVG, Avira, and ClamAV are all free-of-charge scanners, but they're proprietary. Pick some combination of two of the above, that should catch almost everything. 


ClamAV is open source. From the site: "Clam AntiVirus is an open source (GPL) anti-virus toolkit for UNIX, ... "

---

### Post by Stefanie on 2009-05-21
I think a copy of systemrescuecd could be useful, you can use it to make partition images and to recover lost data.

---

### Post by cariboo on 2009-05-21
Every company I've worked for as a computer tech has provided tools, but the tools a computer tech ususally uses are only worth a couple of hundred dollars, 

A diesel Tech needs between $7,000 and $10,000 worth of tools. My younger brother is a Heavy Equipment mechanic, and he figures he has about $8500 invested in his toolbox, but the company he works for provides any test equipment needed, as well as specialized tools, for instance air conditioning recycling and recharging stations and laptops to tune engines.

I'm an electroincs and computer tech, and over the years I've managed to invest approximately $10,000 in specialized test equipment, I wouldn't expect my employees to provide that sort of equipment just to do their job.

---

### Post by Warpnow on 2009-05-21
I knew some people who worked as techs at best buy and the only tools they used were ones given to them by the store. Best buy has its own set of tools.

---

### Post by Claus7 on 2009-05-21
Hello,

first of all I'm not an expert so I'll try to give you my perspective as a normal user. 

> **Chowzor said:**
> If a harddrive fails and you need to do a complete disk image anyone know of a good free (open source preferably) that i can use that for.  

As people said you can use various things, yet if a hdd fails, simply put: is bad. In order to avoid that I do not know if you are familiar with RAID technology, 
[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

which will anable you to have backup of your data to two hdd, reducing enormously the probability to loose data that are important to you.

So, act before the need arises, if you are able to have such an equipment available of course.

> **Chowzor said:**
> 
Virus removal..i have some apps from my old place of employment that the tech there used.  I am also familier with manual removal.

Also here there were many suggestions. Use whatever antivirus program you wish. I just want to inform you that if any of these programs informs you about a "bad" virus that if you remove it, will harm your computer, just put a live cd of ubu and track it and wipe it out from there. 

> **Chowzor said:**
> 
Also what other programs do you think i should keep on hand?  Im a little nervous, i know i can do the work i just want to be prepaired for everything.

It's nice that you want to be prepared. You cannot have always the necessary experience beforehand. I hope that your work will be paid off.

Regards!

---

### Post by toupeiro on 2009-05-21
Wait a minute....

Are you telling me that Geek Squad charges customers something awful like $99 per hour for in store repairs.. and they expect their techs to provide their own software??

Edit: Nevermind.. read two posts above and it pre-empted my rant. :P

---

### Post by .Maleficus. on 2009-05-21
I work at Geek Squad now and I'll tell you this: providing your own tools is a great way to get fired.  There is list of approved tools and that's it.  Every time it changes, you need to resign a contract that states you will not violate these rules.  We get to use a lot of really nice software, so don't worry about it.  We have cloning software, 15+ AV scanners, diagnostic utilities for every part of the computer...

Please don't take the advice of other people if you value your income.  UBCD is not allowed, Knoppix is not allowed..  Like I said though, you'll find everything you need in the provided tools.


Edit:
> **toupeiro said:**
> Wait a minute....

Are you telling me that Geek Squad charges customers something awful like $99 per hour for in store repairs.. and they expect their techs to provide their own software??

Edit: Nevermind.. read two posts above and it pre-empted my rant. :P
No, Geek Squad does not charge on a per hour basis for in store repairs, nor do they charge per hour on in home repairs.

Edit 2:  While I'm giving you some advice, another thing to make sure of: don't bring a personal flash drive to work.  It is a violation of customer privacy rights and even if it stays in your pocket all day it is a very serious infraction.  You'll be told all of this during your training but it's nice to know in advance too :).

---

### Post by pwnst*r on 2009-05-21
> **Chowzor said:**
> After working in Pc sales for a year, i had to move city's quickly and got hired at a local bestbuy as a instore tech.  Couple of concerns, i am proficant in hardware ect.  Just not sure of a few things.  If a harddrive fails and you need to do a complete disk image anyone know of a good free (open source preferably) that i can use that for.  

Virus removal..i have some apps from my old place of employment that the tech there used.  I am also familier with manual removal.

Also what other programs do you think i should keep on hand?  Im a little nervous, i know i can do the work i just want to be prepaired for everything.

um. they should be providing you with what they use.  it's called best practices and standards.

---

### Post by pwnst*r on 2009-05-21
> **.Maleficus. said:**
> I work at Geek Squad now and I'll tell you this: providing your own tools is a great way to get fired.  There is list of approved tools and that's it.  Every time it changes, you need to resign a contract that states you will not violate these rules.  We get to use a lot of really nice software, so don't worry about it.  We have cloning software, 15+ AV scanners, diagnostic utilities for every part of the computer...

Please don't take the advice of other people if you value your income.  UBCD is not allowed, Knoppix is not allowed..  Like I said though, you'll find everything you need in the provided tools.


Edit:

No, Geek Squad does not charge on a per hour basis for in store repairs, nor do they charge per hour on in home repairs.

Edit 2:  While I'm giving you some advice, another thing to make sure of: don't bring a personal flash drive to work.  It is a violation of customer privacy rights and even if it stays in your pocket all day it is a very serious infraction.  You'll be told all of this during your training but it's nice to know in advance too :).

good info!

---

### Post by Mehall on 2009-05-21
Honestly, I would probably prefer to supply my own tools than use what they use most of the time.

if the tools I currently have (plus google) can't get me to fix a computer, I'm in over my head anyway.

---

### Post by calrogman on 2009-05-21
[Super GRUB Disk]("http://www.supergrubdisk.org/") is useful if you are ever confronted with a trashed MBR.

---

### Post by handy on 2009-05-21
I haven't read all of the this thread, so what I'm about to say may have already been stated.

I was a self employed computer tech' for 10 years.  Rarely were any of the computers I worked on using anything other than a windows.

I used Ghost to clone images of specific customers drives (which certainly included all of my business customers) & kept the compressed images on dedicated drives at my home office.  

When these people had whatever kind of failure, I would salvage any data from their drives, then cast the image & insert their data.

This was the quickest way for me to do my job, so it was cheaper for the customer & easier on my poor windows ridden brain.  (As in I managed to escape seeing so many of those horrible little gray boxes with blue lines in them that creep from left to right)

I also had Ghost images to suit whatever motherboards I was supplying or had previously supplied.  Again, when someones machine went down I could have it up again really fast due to these images, it made my life in the business so much more bearable as well as getting the job done quicker for the customer, & all of the other benefits that go with that.

Another thing that made life easier was having a full tower computer case with 3 IDE drive drawers in it.  This allowed me to change boot drive; drive's containing Ghost images & the clients drive.  

Having (the very cheap to buy) drive drawers saved me a great deal of time & still to this day on what is now my testing machine makes my computer life so much more convenient.

After win95 & win98, I used a corporate copy of winXP, so I could install it on all of my customers computers, some of them, usually business customers, even bought a licensed copy of XP, so they were legally licensed.

---

### Post by Chowzor on 2009-05-21
Thanks for the help everyone!

At my old job it was more of a Get the job done for the tech, kind of nice the give us there own utilities.

Yeah i men if the harddrive was on it's way out not completly gone.

Im pretty excited for this, will be a fun time.

---

### Post by TwiceOver on 2009-05-21
The Geek Squad has their own diagnostic disks.  Very similar to the UBCD.  You won't need anything other than a blank stare and the ability to say "We had to format the ram in the hard drive bay BIOS recovery processor Intel.  That'll be $xxxx.xx"

---

### Post by logos34 on 2009-05-21
> **TwiceOver said:**
> The Geek Squad has their own diagnostic disks.  Very similar to the UBCD.  You won't need anything other than a blank stare and the ability to say "We had to format the ram in the hard drive bay BIOS recovery processor Intel.  That'll be $xxxx.xx"

That reminds me of my experience:  Back in 2001 when I didn't know anything about pcs, I took my machine in to recover data after getting hit by a virus (which one day deleted my files before my very eyes).  All they did is tell me a bunch of gobbledegook and charge me $100.00.  I think all they did is format the drive and reinstall win 95.  I wish I had that money back.

---

### Post by pricetech on 2009-05-21
> **starcannon said:**
> I don't know about that. My dad has been a Diesel Mechanic for over 30 years now, and he has always been expected to provide his own tools. Thats life as a tech in most every industry, you bring your own kit, they supply a bench and a safe place to work.

Big difference between turning wrenches and working on computers.  I know, I've done them both.

Mike is right.  Use what they provide and don't stick your neck (or your wallet) out for them.  You could end up getting fired for trying to do a better job.

---

### Post by t0p on 2009-05-21
> **starcannon said:**
> I don't know about that. My dad has been a Diesel Mechanic for over 30 years now, and he has always been expected to provide his own tools. Thats life as a tech in most every industry, you bring your own kit, they supply a bench and a safe place to work.

Mechanics build up a collection of tools that they use throughout their careers.  Computer techs working for companies like Best Buy are in a completely different situation.  Hell, I'll bet the OP will spend most of his time reinstalling Windoze and sticking RAM in slots.

---

### Post by Claus7 on 2009-05-21
Hello,

> **logos34 said:**
> That reminds me of my experience:  Back in 2001 when I didn't know anything about pcs, I took my machine in to recover data after getting hit by a virus (which one day deleted my files before my very eyes).  All they did is tell me a bunch of gobbledegook and charge me $100.00.  I think all they did is format the drive and reinstall win 95.  I wish I had that money back.

excuse me if I sound too subjective (and out of the subject of the thread), yet I think that you have earned far more than the amount of money you describe. Being now a linux user, you are not considered just an ordinary computer user. With the experience you get, I think that you can understand my perspective and what I mean. 

&#931;&#964;&#949;&#961;&#957;&#942; &#956;&#959;&#965; &#947;&#957;&#974;&#963;&#951; &#957;&#945; &#963;&#949; &#949;&#943;&#967;&#945; &#960;&#961;&#974;&#964;&#945;...
I wish I knew before, yet this is called experience and shows that we are moving on.

Regards!

---

