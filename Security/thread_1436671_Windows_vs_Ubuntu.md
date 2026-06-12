---
title: "Windows vs Ubuntu"
date: 2010-03-22
forum: Security
---

### Post by Thomas_Bates on 2010-03-22
This is going to sound like a very stupid and base question.  
I know a very adept hacker, who isn't really a friend, but an acquaintance who I don't really trust, and he has gotten a hold of my IP via email.  He is a windows user with no experience in linux at all, and my question is, can he hack my machine via just knowing my IP, by using shell or telnet or something?

Can a windows computer hack a linux  computer?

---

### Post by mkvnmtr on 2010-03-23
If you have been e mailing him you probably have his address also. Deny access to that address.
Whether he can hack your machine will depend on how your machine is set up. You might start with the sticky threads at the top of this page. You can probably learn more about how to secure your machine from those threads than anywhere else.

---

### Post by Thomas_Bates on 2010-03-23
Well, he is using a torrented and hacked formed of windows and says that
"You can't get my IP, its hacked."

Now while I'm not sure how you would manage to hack your IP, I'm not sure about it.  Also, I talk to him via Empathy, the email I've sent him are replied to the same way, I haven't gotten an email from him.

---

### Post by mkvnmtr on 2010-03-23
I have etherape installed and have gotten addresses from that. But if it is an email is it not coming from a server. 
I seem to remember readinf somewhere there are headers to an email that might give that imformation. Never tried to search for the  but someone should come along that knows.

---

### Post by a.walker on 2010-03-23
There are two aspects to this problem:

1) Technical - read the stickies in this forum, which can be summarized as follows: don't run vulnerable services such as VNC or SSH (things related to remotely administering your computer) unless you have to, enable your firewall, keep your computer up to date. There is a very big difference between having your IP address and owning your system. I wouldn't worry about it.

2) Personal - just ignore the guy and he will eventually find someone to harass who will give more of a reaction.

---

### Post by uRock on 2010-03-23
Enable your firewall if you haven't already with ```
sudo ufw enable
``` I have run port scans against this firewall and could not find any open ports nor determine the host OS. Let him play his Windows games with Windows users. Any computer can hack any other computer with the right tools, but being he is using Windows to commit his crimes, he probably isn't that great. If you can prove he is doing this, then you may or may not want to go to the authorities.

---

### Post by uRock on 2010-03-23
> **Thomas_Bates said:**
> Well, he is using a torrented and hacked formed of windows and says that
"You can't get my IP, its hacked."

Now while I'm not sure how you would manage to hack your IP, I'm not sure about it.  Also, I talk to him via Empathy, the email I've sent him are replied to the same way, I haven't gotten an email from him.

He's not hacking it, he is most likely using a proxy of some sort, which is hard to track.

---

### Post by jrssystemsnet on 2010-03-23
> **Thomas_Bates said:**
> This is going to sound like a very stupid and base question.  
I know a very adept hacker, who isn't really a friend, but an acquaintance who I don't really trust, and he has gotten a hold of my IP via email.  He is a windows user with no experience in linux at all, and my question is, can he hack my machine via just knowing my IP, by using shell or telnet or something?

Can a windows computer hack a linux  computer?Do you have a router in between your computer and the internet?  Have you forwarded the ports for SSH or for Remote Desktop Sharing through your router?  If the answers are "yes" and "no", then your acquaintance can't do anything to you without you clicking on something he sends to you.  Stop worrying.

If you answered "no" to the first or "yes" to the second, then make sure your passwords for both exist and are secure - more than 8 characters, not your birthday / pet's name / something else easy to guess, contains both lowercase, uppercase, numbers, and maybe some punctuation - and stop worrying.

And for the love of god IGNORE anybody who tells you something like "block his IP in your firewall!", that is neither productive nor a good idea.

---

### Post by HPD2 on 2010-03-23
> **jrssystemsnet said:**
> And for the love of god IGNORE anybody who tells you something like "block his IP in your firewall!", that is neither productive nor a good idea.

Forgive me but how would blocking his IP not be a good idea or productive, what harm can come of it? Wouldn't it be a small measure of local defense if he was stupid enough to attempt to compromise the machine with out using a proxy or bot-net to launch the attack?

Personally i would say block the ip at the router (if you have one) and the machine firewalls as well as change you passwords to be alphanumeric including special characters (!@#$%^&*) and a mix of uppercase and lowercase letters. Also the longer the password and more random it is generally the more secure, following the above.

---

### Post by jrssystemsnet on 2010-03-23
> **HPD2 said:**
> Forgive me but how would blocking his IP not be a good idea or productive, what harm can come of it?Because the IP will likely change within 24 hours anyway, even WITHOUT bringing proxies into it, the OP clearly isn't all that savvy with these things anyway, and you show me a residential user frantically blocking IPs out of paranoia and I'll show you a residential user with major firewall problems and half of his/her network services mysteriously flaky or broken a few weeks later.

---

### Post by Gregorybekkers on 2010-03-23
just put on your firewall...on the  Router and PC

---

### Post by HPD2 on 2010-03-23
> **jrssystemsnet said:**
> Because the IP will likely change within 24 hours anyway, even WITHOUT bringing proxies into it, the OP clearly isn't all that savvy with these things anyway, and you show me a residential user frantically blocking IPs out of paranoia and I'll show you a residential user with major firewall problems and half of his/her network services mysteriously flaky or broken a few weeks later.

That is still 24 hours that the attacker would have to wait out. Granted i may be thinking more in line with my computer forensics/ security teachings, and above the OP abilities, and or understandings. 
Some routers and most decent firewalls will allow a cidr notation(ex. 192.168.215.56/24) or blocking of a range(ex. 192.168.152.45 - 192.168.255.255), so you could block the sub-net he is a part of so even if he gained a new ip it would likely still be blocked.
And wouldn't network services rest more on ports rather than ip ranges, also the firewall entries do not have to be permanent, just long enough to let the attacker get bored. If you concerned about blocking to many ip's, wait a week or two then remove it or shorten the range.

---

### Post by Thomas_Bates on 2010-03-23
Heh, this thread starting little debates.  I've been a computer user for well over 10 years now, I just haven't been all that into linux (at least not Ubuntu) so thats where the questions come from.  I know that he must have a proxy of some sort, and I believe it does reset, so yes, simply blocking the IP would be a bit futile.

---

### Post by bodhi.zazen on 2010-03-23
> **Thomas_Bates said:**
> This is going to sound like a very stupid and base question.  
I know a very adept hacker, who isn't really a friend, but an acquaintance who I don't really trust, and he has gotten a hold of my IP via email.  He is a windows user with no experience in linux at all, and my question is, can he hack my machine via just knowing my IP, by using shell or telnet or something?

The short answer is no. The longer answer would be it depends. Do you have a router ? Did you enable any servers (VNC or SSH)?

> Can a windows computer hack a linux  computer?Yes.

I suggest you probably have nothing to worry about and, IMO, an IP address alone does not mean you can hack a computer. For example, we all know google's ip addresses, they are public.

I suggest you read the stickies in the security section:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by HPD2 on 2010-03-23
I didn't really mean for it to turn in to a debate. They way I see it is, if you know ware your attacker may come from block it. That way you slow him down or stop him depending how determined he is. I'm not trying to say that just adding a firewall entry will stop him, but it will make another hoop he would need to jump through and could slow him down. That's more or less the point I was trying to make.

I agree with bodhi.zazen when he says "I suggest you probably have nothing to worry about and, IMO, an IP address alone does not mean you can hack a computer."

---

### Post by OpSecShellshock on 2010-03-23
To be honest, the guy has already opened a line of communication with you. Most likely if he were truly adept and knew what he was doing, he'd wait for you to ask an operational question, and then he'd send a helpful link to software that will do just what you're looking for, and then he'd walk you through the process of installing it. These things usually happen from the inside out. Don't blindly follow links he sends you, don't open any files, and definitely don't install anything. If he sends you a link to a web page or a file, and you open it/follow the link, and then you get a message telling you that it's an administrative action and requires your password, just cancel.

---

### Post by Thomas_Bates on 2010-03-23
That's what I figured he would do, as he has no knowledge of any of my passwords.  According to Emmanuel Goldstein (2600 The Hacker Quarterly) it is more along the lines of "Social Engineering."

---

### Post by Ubunt2u on 2010-03-23
Thread title "Windows vs Ubuntu" is a little misleading lol but to the point, I would think if you use a little common sense, enabled your firewall, etc etc you shouldn't have too much to worry about. Of course nothing is totally secure, just ask google or the defense dept., but unless this guy is on the payroll of the chinese military, I wouldn't fret it......

---

### Post by OpSecShellshock on 2010-03-23
> **Thomas_Bates said:**
> That's what I figured he would do, as he has no knowledge of any of my passwords.  According to Emmanuel Goldstein (2600 The Hacker Quarterly) it is more along the lines of "Social Engineering."

Just so. People themselves were getting hacked long before computers existed, and in any network they're still the most reliable way in.

---

### Post by _h_ on 2010-03-23
> **Thomas_Bates said:**
> Well, he is using a torrented and hacked formed of windows and says that
"You can't get my IP, its hacked."

Just because he has a pirated copy of Windows, doesn't mean his IP can't show up to the world.

Are you sure he's a hacker at all, or just another script kiddie? Hackers wouldn't hack straight through a Windows machine like that either, they would use a VPN or hijack another persons computer in order to hide their footsteps.

---

### Post by bodhi.zazen on 2010-03-23
> **_h_ said:**
> Just because he has a pirated copy of Windows, doesn't mean his IP can't show up to the world.

Are you sure he's a hacker at all, or just another script kiddie? Hackers wouldn't hack straight through a Windows machine like that either, they would use a VPN or hijack another persons computer in order to hide their footsteps.

Real hackers (crackers) do not brag about their exploits, lol.

---

### Post by rookcifer on 2010-03-23
> **Thomas_Bates said:**
> This is going to sound like a very stupid and base question.  
I know a very adept hacker, who isn't really a friend, but an acquaintance who I don't really trust, and he has gotten a hold of my IP via email.  He is a windows user with no experience in linux at all, and my question is, can he hack my machine via just knowing my IP, by using shell or telnet or something?

Can a windows computer hack a linux  computer?

He wont be able to hack you if you don't have any services listening and if you don't get social engineered.

---

### Post by rookcifer on 2010-03-23
> **_h_ said:**
> Just because he has a pirated copy of Windows, doesn't mean his IP can't show up to the world.

I think what the OP meant was that this guy has hacked into another machine and is bouncing off it (and thus his IP shows up as the hacked machine's IP).

---

### Post by _h_ on 2010-03-23
> **bodhi.zazen said:**
> Real hackers (crackers) do not brag about their exploits, lol.

Which leads me to believe he is nothing but a script kiddie.

---

### Post by Thomas_Bates on 2010-03-24
No, I don't know him very well, I've been interviewing him for a position among a staff of programmers, he seems to think that by telling me what he can do with my IP he has some sort of increased chance of getting in (exact opposite actually).  I'm more adept to believe he is a script kiddie, as, from all of the hackers I know, and this goes back to an earlier post, none of them brag about it, if anything they prefer not to tell people.  Also, his comment of "Do you have any idea of what I can do with your IP" is a bit odd, as you can't really do anything.  Especially since mine is actually the internet provider's.

So this is pretty much resolved, I'd edit the post, but I actually have a different question, and don't know if I need a new thread for it.

When people use a proxy, I always see things about servers and such, I'm generally pretty busy and don't have the time to read these, so, do I need an extra computer to set up a proxy?  And if not, will someone please link me to a simple instruction for setting up a proxy?

---

### Post by OpSecShellshock on 2010-03-24
So yeah, um, don't hire this guy. The inside of your enterprise is not where you want folks like that to be. I don't think he's as scary awesome as he's trying to imply, but even if he's not he seems to have an interest in/affinity for playing around. Put another way, if he knows what he's doing he can cause a lot of damage on purpose, and if he doesn't know what he's doing he can cause a lot of damage by accident.

---

### Post by bodhi.zazen on 2010-03-24
> **opsecshellshock said:**
> so yeah, um, don't hire this guy. The inside of your enterprise is not where you want folks like that to be. I don't think he's as scary awesome as he's trying to imply, but even if he's not he seems to have an interest in/affinity for playing around. Put another way, if he knows what he's doing he can cause a lot of damage on purpose, and if he doesn't know what he's doing he can cause a lot of damage by accident.

+1

---

### Post by jrssystemsnet on 2010-03-24
> **Thomas_Bates said:**
> I've been interviewing him for a position among a staff of programmersGood LORD.  Throw his application in the trash can immediately, because his attitude is entirely wrong and - assuming the things you're saying are reasonably accurate renditions of what he originally said - also because he doesn't know his donkey from a hole in the ground.

You also really, REALLY need to find somebody who you trust and who is more knowledgeable about IT to help you interview prospective hires.

> And if not, will someone please link me to a simple instruction for setting up a proxy? This is like asking somebody how you go about getting "a vehicle" without saying anything about what you intend to use it for.  A bicycle, a dump truck, and airplane, and a rowboat are all vehicles; "proxy" is a similarly non-explicit term.

Maybe you'd be better off starting another thread describing what it is you want to do that you think you need a proxy for.

---

### Post by justanothergreysky on 2010-03-24
> **Thomas_Bates said:**
> Also, his comment of "Do you have any idea of what I can do with your IP" is a bit odd, as you can't really do anything.  

Oh LORD.  This guy is a tool.

I'm going to call up Google on the phone later and say

DO YOU HAVE ANY IDEA OF WHAT I CAN DO WITH YOUR IP?


This thread is humorous, at best.  :-)

:popcorn:

---

### Post by Thomas_Bates on 2010-03-24
lol, thanks everyone, just wanted to be sure.  I'll try to mark this thread as solved, if I can.

---

