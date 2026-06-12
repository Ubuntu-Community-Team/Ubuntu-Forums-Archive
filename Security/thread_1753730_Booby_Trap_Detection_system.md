---
title: "Booby Trap Detection system"
date: 2011-05-09
forum: Security
---

### Post by SparTacux on 2011-05-09
Are there any programs out there that scan ports for certain text patterns leaving your computer?

Edit by The Cog:
Sorry, I clicked the wrong button and edited this post instead of quoting it.

---

### Post by CandidMan on 2011-05-09
You might want to look at iptables or tcpdump. I know iptables can filter/log packets based on text patterns and tcpdump can 'dump' packet data.
Personally I would just use apparmor/truecrypt to prevent this access. Apparmor has the benefit of preventing unauthorized access and logging it
Also, if you install apparmor-notify, you'll be instantly told when there's been a denial

Something like 
```
 watch -n 2 lsof -Pn | grep myfilename
```might work as well

EDIT: That doesn't actually work for me, but just to give you an idea

---

### Post by Lars Noodén on 2011-05-09
Take a look at the [Honeynet](http://www.honeynet.org/about) project.  It already does sort of what you are talking about.

---

### Post by SparTacux on 2011-05-09
I hope something like that exists :-)

I'd try it out on an unpatched system, no apparmour, scripts enabled - the lot. Then visit a Jihad Forum and create a file called my Taliban Contacts & see what happens ;-)

I'm not that Technical - it's been a loooooong time since I worked with computers. I'm guessing you couldn't pull off a 'string' search on secure connection ( https ) as the data would already be scrambled and encrypted? Maybe it would have to be implemented when the files are being opened and read. Dunno - maybe some of the die hard here would have a better understanding.

If I wanted to find some info on someone I'd try and lift their email for starters. Some sort of unique code in the email data could be spotted by such a system and give the alert that your system has been breached.

I was just checking out the default directory permissions on Ubuntu - it seems anyone can read each others directory. A quick look in my wife's evolution email folder and have a look for her email. Plain text too ! She's ordered a silk Little Red Riding Hood robe and pure white stockings and suspenders - no underwear ! Look like I'm in for an interesting weekend. I guess I'm playing the part of the Big Bad Wolf ;-) LOL.

---

### Post by Joe of loath on 2011-05-09
> **SparTacux said:**
> 
I was just checking out the default directory permissions on Ubuntu - it seems anyone can read each others directory.

That shouldn't be possible... Did you use sudo?

---

### Post by bodhi.zazen on 2011-05-09
> **Joe of loath said:**
> That shouldn't be possible... Did you use sudo?

Sounds as if you are not familiar with Ubuntu Security Policy:

[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)

Lots of debate on the issue ;)

---

### Post by The Cog on 2011-05-09
> **SparTacux said:**
> Are there any programs out there that scan ports for certain text patterns leaving your computer?


Try ngrep - it might be what you are looking for. It's in the repositories.

> ngrep strives to provide most of GNU grep's common features,
applying them to the network layer.  ngrep is a pcap-aware tool that
will allow you to specify extended regular expressions to match
against data payloads of packets.  It currently recognizes TCP, UDP
and ICMP across Ethernet, PPP, SLIP and null interfaces, and
understands bpf filter logic in the same fashion as more common
packet sniffing tools, such as tcpdump and snoop.

---

### Post by SparTacux on 2011-05-10
> **The Cog said:**
> Try ngrep - it might be what you are looking for. It's in the repositories.

I had a look at it on sourceforge.net. Thanks for that.

It's sort of what I'm looking for and is a step in the right direction. Something like that needs developing into an application that can pop up an alert and give you the option of blocking the connection. NGREP seems to only work with plaintext which is fine for analysing traffic on say port 80 but wouldn't work on port 443. Maybe if it was tied closely with the web browser then it would have access to the encryption algorithm used on a secure connection and possibly check out the data on secure connections? 

It's just an abstract idea - I'm not technical enough to know if it could do that.

---

### Post by SparTacux on 2011-05-10
> **CandidMan said:**
> You might want to look at iptables or tcpdump. I know iptables can filter/log packets based on text patterns and tcpdump can 'dump' packet data.
Personally I would just use apparmor/truecrypt to prevent this access. Apparmor has the benefit of preventing unauthorized access and logging it
Also, if you install apparmor-notify, you'll be instantly told when there's been a denial

Something like 
```
 watch -n 2 lsof -Pn | grep myfilename
```might work as well

EDIT: That doesn't actually work for me, but just to give you an idea

I get the gist of that. By the look of it you could implement it at the file open level and look what applications are opening it and take action depending on the result. As you say Apparmor should stop all unauthorised access providing it has been set up correctly. Sometimes you want to let the thief in to catch him at it - so to speak. I'm pretty new to Linux and haven't by any means really got to grips with it yet.  A little project like this should get me moving :--)

---

