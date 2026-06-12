---
title: "A hacker’s marginal security helps return stolen computer"
date: 2010-12-26
forum: The Cafe
---

### Post by zer010 on 2010-12-26
[http://hackaday.com/2010/12/25/a-hackers-marginal-security-helps-return-stolen-computer/](http://hackaday.com/2010/12/25/a-hackers-marginal-security-helps-return-stolen-computer/)

> Gather round and hear the story of how a hacker outsmarts a criminal.  [Zoz] was robbed and they got his desktop computer. Gone, right? Nope.  Because of a peculiar combination of his computer’s configuration, and  the stupidity of the criminal, he got it back. He shares the tale during  [his Defcon 18 talk]("https://www.defcon.org/images/defcon-18/dc-18-presentations/Zoz/Zoz-Pwned-by-the-Owner.pdf") (PDF), the video is embedded after the break.
 [Zoz's] first bit of luck came because he had set up the machine to  use a dynamic DNS service, updated via a script. Since the criminal  didn’t wipe the hard drive he was able to find the machine online. From  there he discovered that he could SSH into it, and even use VNC  to eavesdrop on the new owner. This, along with a keylogger he  installed, got him all the information he needed; the guy’s name, birth  date, login and password information for websites, and most importantly  his street address. He passed along this juicy data to police and they  managed to recover the system.


---

### Post by Verbeck on 2010-12-26
> ~and  the stupidity of the criminal~~~Since the criminal didn&#8217;t wipe the hard drive~just his luck

---

### Post by handy on 2010-12-26
He does a great video presentation.

Good story.

Thanks for the link. ;)

---

### Post by zer010 on 2010-12-26
Yeah, it was a good presentation. I thought he was quite resourceful and as some know, stolen property is rarely ever found and returned.

---

### Post by NMFTM on 2010-12-26
I was frankly blown away by the fact that he didn't require use of the root password for the two years that he owned the computer. Even on OSX, you need it just to apply updates. But, I guess a criminal dumb enough to not wipe the HD would probably not put much thought into updating his OS.

---

### Post by kevdog on 2010-12-26
Good story -- Not much informational value -- but good for one or two laughs for sure.

---

### Post by Old_Grey_Wolf on 2010-12-26
I've actually thought about adding something to the conky script on my laptop that would get a piece of data from my server every hour when the laptop is on. That way I could track the IP address it was used from. Then ssh or vnc into the computer.

I've opted for a strong password and encrypted HDD. Even if I gave the police all the info they needed, I don't really think I would get my laptop back. I could mess with the person that stole it; however, I could be charged with a crime it I did anything to mischievous.

---

### Post by ki4jgt on 2010-12-26
I think I would've got on a tor client or some other network :-) :-) and posted all the personal information I'd gathered about the person on craigslist. Signed him up for a bunch of weird magazines. Placed a couple of seeking someone ads out on websites where they didn't belong and then told the cops about him after all that. :-) found some way to say a hacker had gotten into my computer the same way I did.

Nah, this guy did it good, but I don't know, there's just something about people who steal other people's stuff that irks me.

---

### Post by witeshark17 on 2010-12-26
A fun story, nice video! :popcorn:

---

### Post by Cuddles McKitten on 2010-12-27
This makes me wonder about the (CPU's?) serial number.  How can you find it?  If it's the CPU serial he was talking about, it's not listed in /proc/cpuinfo

---

### Post by earthpigg on 2010-12-27
> **Cuddles McKitten said:**
> This makes me wonder about the (CPU's?) serial number.  How can you find it?  If it's the CPU serial he was talking about, it's not listed in /proc/cpuinfo

i think its the sticker on the side that he was talking about.

---

