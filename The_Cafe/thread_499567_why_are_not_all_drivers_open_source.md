---
title: "why are not all drivers open source"
date: 2007-07-12
forum: The Cafe
---

### Post by guillaume.darkwalker on 2007-07-12
Hi,

Lately, i was wondering about that. Because i can understand why some (most?) compagnies want to keep their source closed. They have their reason (i don't agree with all their reasons but...)

But, when it comes to drivers, i seems really really odd :confused:
The driver is useful only if you have a copy of the hardware... so as long as you have to sell the hardware it's no big deal if the source of the driver is open.

Do you know of reasonable or legitimate reasons for computer hardware constructors not to make their drivers open source?

---

### Post by Nikron on 2007-07-12
Well, for wireless devices it is a bit iffy because open drivers would allow you to do things that are illegal.  IE, go on to restricted channels.

---

### Post by old_geekster on 2007-07-12
I am certain that some of the reason is the companies don't want to give support for other drivers.  They no doubt have enorgh problems with the Windows drivers.

---

### Post by guillaume.darkwalker on 2007-07-12
but there are open source driver for wifi (they jsut don't work very well sometimes...) and i don't go on forbiden channel with my desktop computer

And i don't ask them to port the drivers to all OS, just to make their existing drivers open source

---

### Post by stmiller on 2007-07-12
To open source your drivers means to give the exact hardware specs to the open. So in other words, the millions of dollars a company spends on R&D for that product would be given away to a competitor.

For example if Nvidia released their sources, then ATI or other graphics companies could use their hard earned development work.

I really don't mind companies like Nvidia who develop Linux drivers. This is what all companies do for Mac and Windows: develop drivers for their products. More companies just need to take the effort to do this for Linux, especially for pro audio devices.

---

### Post by FuturePilot on 2007-07-12
The drivers sometimes contain specs relating to the hardware, so if the drivers were open source then the hardware details would get out and other companies would use that to better they're products. 
That's one of the big reasons why Nvidia won't give us open source drivers. The source code would reveal some of their top secrets and then other people like ATI would get a hold of that.

That's how I understand it.
I wish more companies would give us good drivers like Nvidia does. Kudos to Nvidia.
stmiller beat me to it:)

---

### Post by Freddy on 2007-07-12
If I made some piece of hardware (lets say graphic card) I wouldn't want my opponent to be able to look through my coding and implement my intelligent solutions on their own drivers. My main goal would be to stay ahead of the competitors not helping them.

I'm one of those that have no problem with proprietary drivers and I think it would be foolish to expect that  every piece of software I will aver use to be open source, that will never happen.

/Freddan

---

### Post by guillaume.darkwalker on 2007-07-12
ok, the spec of the hardware comes with the drivers. I didn't know that.

@freddy: i'm not a open source extremist;) it's just that i'd like more drivers for linux and since the hardware constructors don't do their job for linux, it would have made it easier for us

---

### Post by BoyOfDestiny on 2007-07-12
> **guillaume.darkwalker said:**
> ok, the spec of the hardware comes with the drivers. I didn't know that.

@freddy: i'm not a open source extremist;) it's just that i'd like more drivers for linux and since the hardware constructors don't do their job for linux, it would have made it easier for us

I don't really want to comment too much. My feeling is companies are just used to do it this way. If a simple driver could really reveal all the hardware secrets... I'm skeptical. 

Anyway, you might like this idea, as there is an effort to keep what a company wants to be a secret, a secret (via Non-Disclosure Agreement.)

[http://www.kroah.com/log/linux/free_drivers.html](http://www.kroah.com/log/linux/free_drivers.html)

FAQ

"Q: How are you going to write a GPL driver by signing an NDA? Is it going to require a binary blob or some other way of obfuscating the code?

A: No, not at all. I have written many drivers after signing NDAs with companies. They are usually signed either to keep information about the device private until it is announced at a specific date, or to just keep the actual specification documents from being released to the public directly. All code created by this NDA program is to be released under the GPL for inclusion in the main kernel tree, nothing will be obfuscated at all."
[http://www.kroah.com/log/linux/free_drivers_faq.html](http://www.kroah.com/log/linux/free_drivers_faq.html)

Anyway, I'll take a Free driver any day of the week over a closed one. Out of the box support, works even if the company drops support for the hardware, and may work on more architectures. I try and favor hardware that has working Free drivers, or where they have an open source one (i.e. intel graphics)

However, I like Ubuntu's approach, offer the closed driver if the hardware wouldn't work at all without it.

---

### Post by jpkotta on 2007-07-12
Not all drivers are created equal.  From what I understand, modern video drivers are extremely complex.  They do things like compile shader language code in addition to mundane things like copy data.  There are things in the drivers like licensed patents that only $COMPANY can use legally.  And so on.  Beyond that, it doesn't make too much sense to me.  Simple drivers are generally not "valuable ip", they're a cost that cuts into profits.  Why not just let someone else do it (for free)?

---

### Post by rolando2424 on 2007-07-18
> **FuturePilot said:**
>  and other companies would use that to better they're products. 

And is that a bad thing (for the user of course :D )

We should be moving forward, not sideways.

---

### Post by Sporkman on 2007-07-18
A neat solution that will never be implemented would be for companies to implement their drivers in machine-independent bytecode (sort of like Java), then have them run via machine-specific "virtual machines". That way their sercrets are protected, and their driver can be deployed to any OS & architecture, it's just up to others to maintain the virtual machines to run them.

---

