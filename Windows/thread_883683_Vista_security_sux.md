---
title: "Vista security sux"
date: 2008-08-08
forum: Windows
---

### Post by newbie2 on 2008-08-08
> Two security researchers have developed a new technique that essentially bypasses all of the memory protection safeguards in the Windows Vista operating system, an advance that many in the security community say will have far-reaching implications not only for Microsoft, but also on how the entire technology industry thinks about attacks.

In a presentation at the Black Hat briefings, Mark Dowd of IBM Internet Security Systems (ISS) and Alexander Sotirov, of VMware Inc. will discuss the new methods they've found to get around Vista protections such as Address Space Layout Randomization(ASLR), Data Execution Prevention (DEP) and others by using Java, ActiveX controls and .NET objects to load arbitrary content into Web browsers.

By taking advantage of the way that browsers, specifically Internet Explorer, handle active scripting and .NET objects, the pair have been able to load essentially whatever content they want into a location of their choice on a user's machine.

Researchers who have read the paper that Dowd and Sotirov wrote on the techniques say their work is a major breakthrough and there is little that Microsoft can do to address the problems. The attacks themselves are not based on any new vulnerabilities in IE or Vista, but instead take advantage of Vista's fundamental architecture and the ways in which Microsoft chose to protect it.

"The genius of this is that it's completely reusable," said Dino Dai Zovi, a well-known security researcher and author. "They have attacks that let them load chosen content to a chosen location with chosen permissions. That's completely game over.
[http://searchsecurity.techtarget.com.au/articles/26194-Black-Hat-roundup-Vista-security-defeated-IOS-rootkit-DNS-flaw-worse-than-thought-#Vista](http://searchsecurity.techtarget.com.au/articles/26194-Black-Hat-roundup-Vista-security-defeated-IOS-rootkit-DNS-flaw-worse-than-thought-#Vista)
:rolleyes:

---

### Post by Pogeymanz on 2008-08-08
Wow. That's awesome.

We in Linuxland are always preaching that the way Windows handles network security is fundamentally flawed, and now we have some good backup I guess.

---

### Post by Vorian Grey on 2008-08-08
Poor Microsoft. They still can't get security right after all these years. I guess it's back to the drawing board for them. 

At least this will only affect the 5 Vista users.

---

### Post by rockface on 2008-08-08
Unless this vector of attack can be confirmed and examples of this method are seen in the wild, I'd hold your horses before expressing outright condemnation.

This story need to be confirmed from other sources and proven beyond refute before we can point our collective finger at Redmond and giggle like giddy school children.

Affirmation of this information would be interesting if nothing else, we await Microsoft's response.

---

### Post by fiddledd on 2008-08-08
> **rockface said:**
> Unless this vector of attack can be confirmed and examples of this method are seen in the wild, I'd hold your horses before expressing outright condemnation.

This story need to be confirmed from other sources and proven beyond refute before we can point our collective finger at Redmond and giggle like giddy school children.

Affirmation of this information would be interesting if nothing else, we await Microsoft's response.

The voice of reason. :) I agree with you, no details as yet, and seems to be hyping the presentation of their findings at a black hat conference this week.

---

### Post by Vorian Grey on 2008-08-08
I have no doubt it will be confirmed. Look at the guys who made the presentation. They aren't exactly from little known companies.

---

### Post by MaxIBoy on 2008-08-08
I volunteer the school jerk's computer to test this.

---

### Post by tamoneya on 2008-08-08
why does everyone sound so surprised.  You all knew instinctively that vista's security didnt work.  It was all just a matter of time.  What took them so long?

---

### Post by fiddledd on 2008-08-08
> **MaxIBoy said:**
> I volunteer the school jerk's computer to test this.

No need, I'm using Vista now, and have been for months. If I get hacked I'll let you know as soon as I know. :)

---

### Post by MaxIBoy on 2008-08-08
Too bad... I really wanted to display a taunting message on his screen, then flip everything on his screen upside down, permanently. The best part is that even if he rotated his display until it was right side up (a feature on some ATI chips,) everything would also be backwards!


I really hate that kid.

---

### Post by newbie2 on 2008-08-09
[http://www.moviesoundclips.net/movies1/aliens/gameover.wav](http://www.moviesoundclips.net/movies1/aliens/gameover.wav)
:razz::biggrin:

---

### Post by scragar on 2008-08-09
> **fiddledd said:**
> No need, I'm using Vista now, and have been for months. If I get hacked I'll let you know as soon as I know. :)

you wouldn't know, a good crack makes you convinced your computer is just getting slower ever so slowly that you just assume it's a problem with the OS, meanwhile the crack's malicious code is using your computer as a zombie to send out random spam, or DDoS some poor guys server.

---

### Post by lisati on 2008-08-09
The best computer security I know of means completely disconnecting the computer from the outside world, including the user.....

---

### Post by scragar on 2008-08-09
> **lisati said:**
> The best computer security I know of means completely disconnecting the computer from the outside world, including the user.....

you mean unplugging it and storing it in a cupboard? It would stop viruses, although I doubt it'd be very good for searching the ubuntu forums on in that state.

---

### Post by fiddledd on 2008-08-09
> **scragar said:**
> you wouldn't know, a good crack makes you convinced your computer is just getting slower ever so slowly that you just assume it's a problem with the OS, meanwhile the crack's malicious code is using your computer as a zombie to send out random spam, or DDoS some poor guys server.

1: It's not got any slower during the last 5 months I've used Vista.

2: I regularly run checks for Rootkits, Spyware, and Malware, and with more than one program per task. Nothing detected yet.

3: I'm behind a hardware firewall.

4: I have always used a LUA, even in XP.

5: I don't visit Porn or Warez sites.

I use common sense and don't believe all the FUD. There has always been security risks in every OS, and there always will be. Oh, and I don't believe every word published online.

---

### Post by zxscooby on 2008-08-09
Also in recent news smoking is bad for you and 
the leading cause of divorce is getting married.
:lolflag:

---

### Post by scragar on 2008-08-09
> **fiddledd said:**
> 1: It's not got any slower during the last 5 months I've used Vista.

2: I regularly run checks for Rootkits, Spyware, and Malware, and with more than one program per task. Nothing detected yet.

3: I'm behind a hardware firewall.

4: I have always used a LUA, even in XP.

5: I don't visit Porn or Warez sites.

I use common sense and don't believe all the FUD. There has always been security risks in every OS, and there always will be. Oh, and I don't believe every word published online.
I wasn't saying you had been hacked, I was just saying that if you had most people would be very unlikely to even notice,

---

### Post by zxscooby on 2008-08-09
I remember the first time i used windows XP,
 I had just built a new computer and installed Xp for the first time. 
After being connected to the internet for 2 minutes it shutdown
and became totaly useless. The only thing i did was try to download the latest updates. I spent several hours troubleshooting thinking i had put something together wrong. It turns out I got a nasty virus as soon as I connected, before
I even had a chance to download any porn. :mad:

---

### Post by fiddledd on 2008-08-09
> **scragar said:**
> I wasn't saying you had been hacked, I was just saying that if you had most people would be very unlikely to even notice,

I can't really speak for most people, and I have never spoken to anyone who's PC became a Spam Bot. But even if I had it would not be my biggest concern. My main concern is my personal information, so Identity Theft concerns me. Losing all my money from my Bank Account concerns me. Protecting my personal information is not a concern specific to Windows, as most attacks are through the Web Browser. ATM the [DNS Flaw](http://www.techtree.com/India/News/Black_Hat_Kaminsky_Explains_DNS_Flaw/551-91929-580.html) is more worrying than any theoretical exploit in Vista.

---

### Post by rockface on 2008-08-09
> **fiddledd said:**
> 1: It's not got any slower during the last 5 months I've used Vista.

2: I regularly run checks for Rootkits, Spyware, and Malware, and with more than one program per task. Nothing detected yet.

3: I'm behind a hardware firewall.

4: I have always used a LUA, even in XP.

5: I don't visit Porn or Warez sites.

I use common sense and don't believe all the FUD. There has always been security risks in every OS, and there always will be. Oh, and I don't believe every word published online.

'5: I don't visit Porn or Warez sites.'WTF?

Why bother with a computer and internet connection in the first place?:)

---

### Post by fiddledd on 2008-08-09
> **rockface said:**
> '5: I don't visit Porn or Warez sites.'WTF?

Why bother with a computer and internet connection in the first place?:)

lol, yeah, but I didn't say I didn't use Usenet. :)

---

### Post by stinger30au on 2008-08-09
> **tamoneya said:**
> why does everyone sound so surprised.  You all knew instinctively that vista's security didnt work.  It was all just a matter of time.  What took them so long?


probably having fun playing Tux Kart or similar games then to worry about again exposing Microsoft security holes :lolflag:

---

### Post by Krydahl on 2008-08-09
Before laughing too hard at Redmond, note also from the bottom of the article:

> Dai Zovi stressed that the techniques Dowd and Sotirov use do not rely on specific vulnerabilities. As a result, he said, there may soon be similar techniques applied to other platforms or environments.

---

### Post by torry_loon on 2008-08-09
> **rockface said:**
> '5: I don't visit Porn or Warez sites.'WTF?

Why bother with a computer and internet connection in the first place?:)

Everyone knows [The Internet is for Pr0n]("http://www.youtube.com/watch?v=eWEjvCRPrCo")!

---

### Post by Krydahl on 2008-08-11
More detail:

[http://arstechnica.com/news.ars/post/20080811-the-sky-isnt-falling-a-look-at-a-new-vista-security-bypass.html](http://arstechnica.com/news.ars/post/20080811-the-sky-isnt-falling-a-look-at-a-new-vista-security-bypass.html)

---

### Post by fiddledd on 2008-08-11
> **Krydahl said:**
> More detail:

[http://arstechnica.com/news.ars/post/20080811-the-sky-isnt-falling-a-look-at-a-new-vista-security-bypass.html](http://arstechnica.com/news.ars/post/20080811-the-sky-isnt-falling-a-look-at-a-new-vista-security-bypass.html)

lol, yeah, I bet there's a few who posted in this thread that wished they'd waited for day. Or maybe not, I mean FUD is so much more exciting than facts.:)

---

### Post by rockface on 2008-08-11
> **Krydahl said:**
> More detail:

[http://arstechnica.com/news.ars/post/20080811-the-sky-isnt-falling-a-look-at-a-new-vista-security-bypass.html](http://arstechnica.com/news.ars/post/20080811-the-sky-isnt-falling-a-look-at-a-new-vista-security-bypass.html)

Not to defend Microsoft (may Satan's minions consume my soul), but I did say.

---

### Post by rockface on 2008-08-11
> **fiddledd said:**
> lol, yeah, I bet there's a few who posted in this thread that wished they'd waited for day. Or maybe not, I mean FUD is so much more exciting than facts.:)

Before I forget, and get too pissed.

Remember a single fact fiddledd. If this method of exploitation of the operating system was targeted solely at Linux, Microsoft would trumpet this in their 'Get The Facts' campaign. It would become an instrument of FUD the like of which the IT world has never seen.

If the Linux community (incorporating the *BSD people, just for the sake of argument) are capable of FUD, as you say, then Microsoft is just and as guilty and by many orders of magnitude. They do have the funding after all.

IBM (seemingly) invented FUD, Microsoft refined it to an art. 

'I mean FUD is so much more exciting than facts'. This works both ways.

Now, back to the beer.

---

### Post by zmjjmz on 2008-08-11
No matter how much FUD IBM and VMWare put in, it's still a big gaping security hole.

---

### Post by fiddledd on 2008-08-12
> **rockface said:**
> Before I forget, and get too pissed.

Remember a single fact fiddledd. If this method of exploitation of the operating system was targeted solely at Linux, Microsoft would trumpet this in their 'Get The Facts' campaign. It would become an instrument of FUD the like of which the IT world has never seen.

If the Linux community (incorporating the *BSD people, just for the sake of argument) are capable of FUD, as you say, then Microsoft is just and as guilty and by many orders of magnitude. They do have the funding after all.

IBM (seemingly) invented FUD, Microsoft refined it to an art. 

'I mean FUD is so much more exciting than facts'. This works both ways.

Now, back to the beer.

I agree, FUD works both ways. I wasn't defending Microsoft, just pointing out that a few here immediately gave an opinion on the story and bashed Vista before there was any facts. Incidentally, you was not one of those that reacted like that, your post was a reasonable reaction to the lack of facts. 

PS. I bet you got a hangover this morning. :)

/me plays really load bassy music

---

### Post by rockface on 2008-08-12
> **fiddledd said:**
> I agree, FUD works both ways. I wasn't defending Microsoft, just pointing out that a few here immediately gave an opinion on the story and bashed Vista before there was any facts. Incidentally, you was not one of those that reacted like that, your post was a reasonable reaction to the lack of facts. 

PS. I bet you got a hangover this morning. :)

/me plays really load bassy music

LOL!!

I realy should stop posting when I'm half tanked up.

And yes, you are right about the hangover.:(

Spooky you mention loud bassy music, my neighbour has taken it upon herself to annoy me with endless ABBA tracks. Not a good day.

---

