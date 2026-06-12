---
title: "&quot;web attack expierience &quot; ?"
date: 2008-06-13
forum: The Cafe
---

### Post by lunaluna on 2008-06-13
i don't know if i'm on right forum...

how many of you do you have a true "web attack experience"... 
   and if you're one of the them could you give some details?   

:popcorn:

---

### Post by cprofitt on 2008-06-13
Could you clarify web attack.

---

### Post by wpshooter on 2008-06-13
> **PrivateVoid said:**
> Could you clarify web attack.

They've been gone for about 5 hours.  I think they had one, whatever it is !!!

---

### Post by Joeb454 on 2008-06-13
> **wpshooter said:**
> They've been gone for about 5 hours.  I think they had one, whatever it is !!!

True, but a web attack could mean getting a virus, or it could mean hacking attempts on a home server.

Which is why I'd quite like to see some clarifcation too :)

---

### Post by hovzio on 2008-06-13
I am also curious as to whether or not anyone has had an security issues concerning intrusion via the internet on an ubuntu desktop. Haven't ever heard of anything but wouldn't mind hearing about some experiences. (I am assuming this is what was meant.. if not sorry )

---

### Post by DirtDawg on 2008-06-13
Web Attack Experience!
[IMG]http://ecx.images-amazon.com/images/I/41QSXGV2SML._SL500_AA280_.jpg[/IMG]

---

### Post by cprofitt on 2008-06-13
> **hovzio said:**
> I am also curious as to whether or not anyone has had an security issues concerning intrusion via the internet on an ubuntu desktop. Haven't ever heard of anything but wouldn't mind hearing about some experiences.

The question still remains -- what kind of intrusion attempt...

trojan / root kit that is web launched?

remote code execution and priv. escalation.

---

### Post by Joeb454 on 2008-06-13
Well as I run a web server from home, which naturally, is the first thing you'll get if you type in my IP address, I'm sure I've had some login attempts made (it runs SSH server too) :)

---

### Post by _sphinx_ on 2008-06-13
I also don't have any such kind of experience but I just wanted to know how could someone do this web attack sort of thing, I mean can anybody give me some overview.

---

### Post by _sphinx_ on 2008-06-13
> **Joeb454 said:**
> Well as I run a web server from home, which naturally, is the first thing you'll get if you type in my IP address, I'm sure I've had some login attempts made (it runs SSH server too) :)

So how could one possibly crack SSH password.

---

### Post by hovzio on 2008-06-13
@ PrivateVoid: Something along the lines of a rootkit. Thats what I had in mind. I must add, my knowledge concerning the subject is minimal.

---

### Post by wpshooter on 2008-06-13
> **hovzio said:**
> I am also curious as to whether or not anyone has had an security issues concerning intrusion via the internet on an ubuntu desktop. Haven't ever heard of anything but wouldn't mind hearing about some experiences.

Well down to the serious side. I have been running various versions of Ubuntu for about 2 to 3 years now and to my knowledge, I have NOT experienced the first security breach of any type.  And this is with only what security is built into the O/S, i.e. no virus protection software or software firewalls.

I would hate to think about how polluted my system would be by now if I had been running that M$ O/S under those same circumstances.

---

### Post by Joeb454 on 2008-06-13
> **_sphinx_ said:**
> So how could one possibly crack SSH password.

It depends what the password is ;) Mine has letters (both cases) numbers and symbols :)

---

### Post by cprofitt on 2008-06-13
> **_sphinx_ said:**
> So how could one possibly crack SSH password.

that all depends on how the SSH sever and client are setup.

Here are some good articles to read:

[http://www.security-hacks.com/2007/05/23/protecting-against-ssh-brute-force-attacks](http://www.security-hacks.com/2007/05/23/protecting-against-ssh-brute-force-attacks)

[http://www.linux.com/articles/60955](http://www.linux.com/articles/60955)

---

### Post by cprofitt on 2008-06-13
> **hovzio said:**
> @ PrivateVoid: Something along the lines of a rootkit. Thats what I had in mind. I must add, my knowledge concerning the subject is minimal.


Here are some links for those:

[http://www.sans.org/reading_room/whitepapers/linux/901.php](http://www.sans.org/reading_room/whitepapers/linux/901.php)

[http://linuxhelp.blogspot.com/2006/12/various-ways-of-detecting-rootkits-in.html](http://linuxhelp.blogspot.com/2006/12/various-ways-of-detecting-rootkits-in.html)

[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)

[http://www.linuxdevcenter.com/pub/a/linux/2001/12/14/rootkit.html](http://www.linuxdevcenter.com/pub/a/linux/2001/12/14/rootkit.html)

---

### Post by kansasnoob on 2008-06-13
Well there are ongoing discussions about security:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

I tend to watch the two little applets I've dropped in my lower panel ..... temp & cpu usage ..... if either seem high then I look further. Of course the first thing I look at is the little leds on my DSL modem to see if there's activity when there shouldn't be.

If something seems afoul I open Firestarter which I've previously dl'ed from synaptic and I can open from either "Internet" or "Administration". Then I can actually see what's going on just by clicking the "events" tab.

The sad thing is I've found no way to log events without editing sudoers to have Firestarter auto-start and that in itself creates a vulnerability.

And I know that ufw is now installed by default, but I'm just too slow minded for cli ............. I need gui!

---

### Post by kansasnoob on 2008-06-13
/home/lance/Desktop/Screenshot-Firestarter lance-desktop.png

---

### Post by Joeb454 on 2008-06-13
I think you'll need to re-upload that ;)

---

### Post by kansasnoob on 2008-06-13
Read this:

[http://ubuntuforums.org/showthread.php?p=5182069#post5182069](http://ubuntuforums.org/showthread.php?p=5182069#post5182069)

In spite of mastering dual boots and a number of other hurdles I'm still just an old fart that can't figure out the forum tools.

Paste that link into your browser and take what you like from my puter ........... maybe! Not much there, it's a fairly new setup.

I guess I at least chose a good screen-name! Noob definitely describes me :)

---

### Post by kansasnoob on 2008-06-13
Joeb454,

You've helped me before, I wouldn't get mad if you helped me again :confused:

---

### Post by aysiu on 2008-06-13
> **lunaluna said:**
> i don't know if i'm on right forum... I've moved it to the Community Cafe, which seems a more appropriate place.

---

### Post by srt4play on 2008-06-13
> **dirtdawg said:**
> web Attack Experience!
[img]http://ecx.images-amazon.com/images/i/41qsxgv2sml._sl500_aa280_.jpg[/img]

Lmao

---

### Post by Joeb454 on 2008-06-13
> **kansasnoob said:**
> /home/lance/Desktop/Screenshot-Firestarter lance-desktop.png

> **Joeb454 said:**
> I think you'll need to re-upload that ;)

That's what I was referring to.

It looked like you were trying to upload an image, but you just pasted it's location on your system :)

---

### Post by Lord Xeb on 2008-06-13
I have not experienced a "web attack" per se, but I have found a root kit that would link a hack to my PC and allow them to control it to their will. It was in a game my brother played here and their. I looked at some records on my firewall and did see an attempt that was supposedly thorted, but it was not and the jerk put it inside his game. e_e not cool.

---

### Post by lemuriaX on 2008-06-13
Hi there...interesting thread.

I'm curious about this one:

> **kansasnoob said:**
> 
The sad thing is I've found no way to log events without editing sudoers to have Firestarter auto-start and that in itself creates a vulnerability.



I thought Firestarter was just a GUI for managing IPTables, how would having it start automatically open a vulnerability?

---

### Post by kansasnoob on 2008-06-13
> **Joeb454 said:**
> That's what I was referring to.

It looked like you were trying to upload an image, but you just pasted it's location on your system :)

Yes!

That's why I posted the link to my asking how to use the Forum tools.

I don't get it????????????

But I'm working on it :confused:

---

### Post by kansasnoob on 2008-06-14
"I looked at some records on my firewall"

How? I've never found a way to access an activity log other than Firestarter and then only if it's running on top of iptables at the time the traffic is ............. uh, trafficking :confused:

Is there a ufw log that can be looked at?

---

### Post by kansasnoob on 2008-06-14
"I thought Firestarter was just a GUI for managing IPTables, how would having it start automatically open a vulnerability?"

I decided it was unwise to edit sudoers. I think that anytime you remove a level of password protection you create a new vulnerability.

Then again, I am a nOOb, therefore the moniker!

---

### Post by lemuriaX on 2008-06-17
> **kansasnoob said:**
> 

I decided it was unwise to edit sudoers. I think that anytime you remove a level of password protection you create a new vulnerability.

Then again, I am a nOOb, therefore the moniker!

Well I´m in the n00b camp myself so would have to let someone more experienced say for sure.

---

### Post by lemuriaX on 2008-06-24
Okay well obviously removing a level of password protection would not be a good idea in general. I'm not too familiar with editing sudoers yet.

I did read some info suggesting that running Firestarter all the time maybe isn't so wise since it runs as root - [http://ph.ubuntuforums.com/showthread.php?t=694198](http://ph.ubuntuforums.com/showthread.php?t=694198)

It is nice to have a GUI for monitoring port activity though, what would be good to use for that instead of Firestarter?

---

### Post by hovzio on 2008-06-24
> **lemuriaX said:**
> Okay well obviously removing a level of password protection would not be a good idea in general. I'm not too familiar with editing sudoers yet.

I did read some info suggesting that running Firestarter all the time maybe isn't so wise since it runs as root - [http://ph.ubuntuforums.com/showthread.php?t=694198](http://ph.ubuntuforums.com/showthread.php?t=694198)

It is nice to have a GUI for monitoring port activity though, what would be good to use for that instead of Firestarter?

I have found myself asking the same question (and the forums) several times. The following link is a thread I started asking the same as above. I must say I haven't gotten too many answers other than netstat.

[http://ubuntuforums.org/showthread.php?t=832108](http://ubuntuforums.org/showthread.php?t=832108)

Netstat kicks out a bunch of information but as a noob I find it hard to fish out the stuff I (think that I) need. :) I'm sure there are commands to filter results but I haven't had time to check it out. (excuses..)

---

### Post by lemuriaX on 2008-06-24
Netstat is an amazing tool which I do want to learn more about. Have used it some but like you don't really know how to interpret a lot of the data.

But even though I plan to develop my skills there more, I still would like a simple GUI that would just monitor port activity. I liked that about using Firestarter, that I could check real quick to see what ports I had connections running on, and it would show a little graphical alert if detecting "events".

---

### Post by tomplast on 2008-06-24
I'm administrating a server which got hacked (or something, at least it tried to DDOS servers or something like that) and after that nobody (except me) is allowed to login, Intrusion Detection Systems over the place, avoiding give out software signatures (like Apache version, FTP version etc).

---

### Post by hovzio on 2008-06-24
> **tomplast said:**
> I'm administrating a server which got hacked (or something, at least it tried to DDOS servers or something like that) and after that nobody (except me) is allowed to login, Intrusion Detection Systems over the place, avoiding give out software signatures (like Apache version, FTP version etc).

Do you how you got hacked? What took place? Are you talking about "security measures" when mentioning intrusion detetection systems and software signatures?

---

### Post by monstermudder78 on 2008-06-24
> **tomplast said:**
> Intrusion Detection Systems over the place, avoiding give out software signatures (like Apache version, FTP version etc).

Huh?  Is this the result or the advice you are giving?

---

### Post by nick09 on 2008-06-24
> **kansasnoob said:**
> Yes!

That's why I posted the link to my asking how to use the Forum tools.

I don't get it????????????

But I'm working on it :confused:

When you post click Manage Attachments in Additional options to upload the png file and Submit your reply.

Or you could use a image host like [imageshack](http://imageshack.us/) and emb using these tags:
```
[img](insert link to image here)[/img]
```

---

### Post by tomplast on 2008-06-25
> **hovzio said:**
> Do you how you got hacked? What took place? Are you talking about "security measures" when mentioning intrusion detetection systems and software signatures?

The only out of the order stuff that I found was some oddly timed logins (in the middle of the night) by one of the students (the server hosts their web pages) and after those logins the outgoing traffic increased exponentially.

Anyway, I do believe that a better firewall policy would have helped but lessons are meant to be learned, and I surely learned mine. Intrusion detection systems, restrict logins on the server was now a must for me.

I surely never wanna get a long piece of paper again that shows that "my server" has attacked others :mad:, and hopefully I will never have to deal with that again.

---

