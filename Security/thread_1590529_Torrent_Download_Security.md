---
title: "Torrent Download Security"
date: 2010-10-08
forum: Security
---

### Post by rCiv on 2010-10-08
Hi guys, quick question, as I am new to Linux I have been spending the last few days riffling through security documentation (mostly found here) and other "security enthusiast" type websites to get a fairly broad perspective on Network security and prioritize my learning schedule.

That being said, I have come to the conclusion that you can generally assume you will be safe for day to day use on your Ubuntu desktop provided you follow the security recommendations conveniently compiled and available on this site. (includes but not limited too, running a hardened kernel, HIDS/NIDS, scanning yourself from another computer on your network, using a router and not forwarding ports, using a proper firewall, locking down firefox and not allowing scripts and what not, all of which I have been working hard on to implement)
 
The list is exhaustive and goes on, but I'm not here to try and regurgitate everything that is so nicely done already on this site, I'm merely trying to illustrate that I have been reading and not sleeping much trying to implement all of these amazing things onto my Ubuntu system and loving the process, and thus, trying not to waste this community's precious time with retarded questions that are already answered here.

A second conclusion I have been able to come to is that being behind a NAT firewall,provided there is no firmware/configuration flaws and also assuming that no other computers on my LAN have been compromised to provide a "bridgehead" into my LAN, I can generally assume that it is 99.99% safe, which leaves the only other opportunities being social engineering "Hey bro click here" or browser/flash script based exploits (basicly getting the user to open up to you from behind the router as far as I am concerned... )

Now here is my question (finally, lol):

Does downloading a torrent from an untrustworthy source (aka demonoid type trackers) count as opening up to someone from behind the router? Assuming Transmission doesn't have a vulnerability, I'm wondering if  that person, if they were sitting there looking at who connects to their torrent with evil intent , if they were to see your IP,  would they be able through some tricks of trade to get passed the router and start looking for holes in your system, or would the whole process be considered "dynamic" on your end and thus not an entry vector.

I'm terribly sorry if this is completely annoying to those of you who actually know what they are talking about, please forgive me, I'm am trying my best to bring some basic knowledge to the table here, but TCP/IP illustrated has 600 pages and I've been busy with the defense basics... 

ANY elaboration or correction or even flames are welcome, I'll read linkage with great attention.

Thanks guys//


*edit: spelling mistakes...sorry

---

### Post by mikewhatever on 2010-10-08
Theoretically, any open connection can present an attack vector. The only 'safe' computer is the one turned off and locked in the closet. Ubuntu provides security updates for Transmission, so keep it and your system uptodate.

PS1: You don't download files from torrent trackers.;)
PS2: You question is perfectly legitimate, so stop apologizing.

---

### Post by Rubi1200 on 2010-10-08
You can also use AppArmor to restrict Transmission.

More about AppArmor:
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

Profiles:
[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

---

### Post by P4man on 2010-10-08
> **rCiv said:**
> 
Does downloading a torrent from an untrustworthy source (aka demonoid type trackers) count as opening up to someone from behind the router? .

Definitely no. That person could only attack transmission on the port that has been opened to him. If transmission has no exploitable vulnerabilities, there is nothing that person could do (at least not that he couldnt do with your public IP anyway, which isnt much by the sound of it ;)).

Of course its not impossible for transmission to have vulnerabilities, so keeping it up to date and following the above advice wont hurt.

---

### Post by rCiv on 2010-10-08
> **P4man said:**
> Definitely no. That person could only attack transmission on the port that has been opened to him. If transmission has no exploitable vulnerabilities, there is nothing that person could do (at least not that he couldnt do with your public IP anyway, which isnt much by the sound of it ;)).
 
Of course its not impossible for transmission to have vulnerabilities, so keeping it up to date and following the above advice wont hurt.
 
I do apparmor it, and my security updates are automatic daily, I often manualy check if I'm bored, I suppose if the actual file I'm downloading would be a risk, ironicly alot of the security series type of training videos going around the trackers are ripped from the DVD and put into a flash video type format, all i see in the description is the guy hosting it saying "Here it is guys, how to protect your PC, all you need is a browser with a flash pluggin, allow the scripts to run", lol... 
 
But thank you for confirming that with me, I understand that "theoreticly speaking" no one is safe anywhere, but realisticlty, I'm sure there will be easier targets out there for someone to stalk, unless they are looking for a challenge or its personal lol.
But from my understanding alot of these "l33tz intersnetz hax0rz" just look for the easy way in and preffer to scan wide ranges of IP's for easy ins and dated vulnerabilities rather than target a specific person using a program that typicaly doesnt have vulnerabilities.
 
Also, in response to PS1 a bit further up, yes I understand that im not downloading the actual file from the tracker, I should have said "downloading files, using torrent files, from untrustworthy trackers", thank you guys for your input on this!
:P

---

