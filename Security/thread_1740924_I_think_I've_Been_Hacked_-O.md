---
title: "I think I've Been Hacked :-O"
date: 2011-04-27
forum: Security
---

### Post by TheNewbieGeek on 2011-04-27
The computer went into low graphics mode all by itself and then later threw a error that said 

incompatible processor system halted!

the computer was getting really slow and made alot of noise.

later the computer did something stranger..

it restarted but normally when my computer normally restarts it bypasses the password page setup in bios of the computer. This time I still had to enter a password before it could reboot.

Another thing...when it the ethernet cable was connected to the computer (internet connection was  on) it was slow when it was unplugged it was not.

I have read that unless you're running a server or something it is highly unlikeley you'll be hacked.

The computer completely froze up when online.

Have I been hacked!!

---

### Post by Skaggz on 2011-04-27
After reading through some of the other threads that you have started, it seems apparent that you are rather paranoid about internet security.  However, in this case, I think you are confusing hardware (and maybe even software) problems with getting "hacked".

> the computer was getting really slow and made alot of noise.
What kind of noise?  Was it a fan maybe?  Check your CPU temps.  What was your CPU load?  Could have even been a fan bearing that is getting noisy.  Could have been a fan that was working full speed for an extended amount of time due to CPU temperatures.

> it restarted but normally when my computer normally restarts it bypasses the password page setup in bios of the computer. This time I still had to enter a password before it could reboot.
So, you have a BIOS password stored, but usually never have to enter it?  In this case you had to enter a password before the operating system even began to load?  The way its worded is kind of confusing...

> Another thing...when it the ethernet cable was connected to the computer (internet connection was on) it was slow when it was unplugged it was not.
Did you check incoming and outgoing traffic?  You should have next to none at idle.

> The computer completely froze up when online.
The fact that it froze while online could have been a coincidence that it froze due to a hardware/software error.

> Have I been hacked!!
[COLOR="DarkGreen"]The question mark key is on the other corner of the keyboard.[/COLOR]
No, it is not likely that you are being hacked.  Remember getting "hacked" is NOT the same as being infected by a virus/trojan/worm/etc.

It is entirely possible that you may have a corrupt BIOS or a failing motherboard.  Especially with the "incompatible processor system halted!" error.

---

### Post by Rubi1200 on 2011-04-28
Check the logs for signs of hardware issues:

```
dmesg | less
```

Pretty much everything else has already been said by Skaggz.

---

### Post by mutinystudios on 2011-04-28
Okay you have NOT been hacked, you filled up too much junk on your PC or your computer over heated, or you mesed up a system file in root or a number of other things, but i repeate YOU HAVE NOT BEEN HACKED unless of course you check the logs and some ones been connectiong to your ports.[-X

---

### Post by HermanAB on 2011-04-28
Sorry to break this to you, but the fact is that you are simply not interesting enough that a script kiddie would want to try to hack your machine...
;)

You messed something up.  Figure it out and fix it.  Start by reading the log files.  That is the way to learn with Linux.

---

### Post by TheNewbieGeek on 2011-04-28
> **HermanAB said:**
> Sorry to break this to you, but the fact is that you are simply not interesting enough that a script kiddie would want to try to hack your machine...
;)

You messed something up.  Figure it out and fix it.  Start by reading the log files.  That is the way to learn with Linux.

ARE YOU GUYS TROLLS...THIS IS A SECURITY FORUM...WHATS UP WITH THE CRITICISM...I assure you I am interesting but that really doesn't have anything to do with whether my computer was hacked or not.

---

### Post by CandidMan on 2011-04-28
> Listen you nerds I asked for your opinion. Leave your nerdy remarks to  yourself. You guys are probably bored because you lives revolove around  my computer. Go get laid or something. I assure you I am interesting but  that really doesn't have anything to do with whether my computer was  hacked..er excuse me virused....sorry I am not boring. 	
I think it should be fairly obvious from the post that HermanAB meant your particular PC isn't very interesting to a hacker unless it's vulnerable

I'm sure HermanAB will clarify in good time :)

---

### Post by RJARRRPCGP on 2011-04-28
The error may be from using a system with bad caps. 

If you have bulging caps, that's your problem.

[http://badcaps.net](http://badcaps.net)

---

### Post by Skaggz on 2011-04-28
> Listen you nerds I asked for your opinion. Leave your nerdy remarks to yourself. You guys are probably bored because you lives revolove around my computer. Go get laid or something. I assure you I am interesting but that really doesn't have anything to do with whether my computer was hacked..er excuse me virused....sorry I am not boring.> ARE YOU GUYS TROLLS...THIS IS A SECURITY FORUM...WHATS UP WITH THE CRITICISM...I assure you I am interesting but that really doesn't have anything to do with whether my computer was hacked or not.
Man, you need to step back and chill out.  Nobody was attacking your character here.  By saying that you are not interesting, his is simply saying that it is unlikely that someone singled out your IP address, scanned it for open ports, determined if there is a known exploit on at least on of the ports, took advantage of said exploit, and gained access to your home PC.

While this does happen from time to time on someone's home PC, most people that think they are being "hacked" are not.  Its a case of paranoia (as is evident in your previous posts here) along with a touch of narcissism.  These people jump to the conclusion that the evil black-hats in the world are singling them out.  When in reality, their issue is due to a hardware problem or a software conflict.

Take some time to gather data on every statement in my first post that ends in a question mark.  As well as what Rubi1200 said.  Then we can help you come to a conclusion as to whether your rig is the problem, or there is actually an intrusion.

Nobody here was trolling you.  Nobody here was attacking your character.  However, you attacked everyone with your statements I quoted above.  I suppose that makes you feel like you're better than all of us.

---

