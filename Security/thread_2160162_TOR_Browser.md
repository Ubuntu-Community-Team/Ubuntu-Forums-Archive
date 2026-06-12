---
title: "TOR Browser"
date: 2013-07-05
forum: Security
---

### Post by Maxiejoe on 2013-07-05
Is anyone using the TOR Browser?  It seems it is more secure than Firefox but before I try it I would like some input from someone using it.  Thanks

---

### Post by uRock on 2013-07-05
TOR isn't a browser for security. It is for anonymity. It works great for its purpose. Most importantly, TOR is a protocol through which their tweaked Firefox runs through.

---

### Post by Stonecold1995 on 2013-07-06
Tor is like a multi-hop proxy, the Tor browser is just Firefox configured to use Tor out-of-the-box.

It is of course slower because it routes everything through 3 random nodes scattered all over the world.  For this reason I use Chromium through a VPN for normal browsing, and Tor when I need extra security.

The security of Tor is a whole subject by itself, so I suggest you look on the official website for more information than can be given here.

---

### Post by KaosuX on 2013-07-06
TOR will reduce your overall security by a large margin. Why? Well, because it is very easy to set yourself up as an exit node and sniff the traffic. Since SSLStrip is also pretty easy to use, you're only asking to have your account stolen when using TOR. Sure, you may use it and not reach a malicious exit node, but you will one day. Using TOR and accounts you care about just does not make sense. 

TOR is a tool used for anonymity NOT security. Even then, it is not bullet proof and is subject to all kinds of attacks;

- Timing attacks over a fixed time structure to eventually isolate the user
- Malicious exit nodes that sniff/log your traffic (SSLStrip is handy here)
- Digital fingerprinting of web resources to track someone
- Tagging attacks

Those are just a handful of attack vectors. As you can see, the system is not as anonymous or secure as people seem to believe. Sure, it will improve your anonymity in many cases, but you have to be really careful about how and when you use the system.

I would advise against using TOR as a whole if you're trying to do something sensitive. However, if you're just trying to get around geographical locks or research a taboo topic then TOR will work fairly well for that. Don't go around using it all the time to check your bank account, email accounts, etc. If you do that, it is only a matter of time before those accounts are stolen.

If you have been using TOR like this, I suggest you check or request logs from your email provider to see the last 20 logged in IP addresses. If any of those don't match an address you use, then TOR has already screwed you.

---

### Post by Frogs Hair on 2013-07-06
The FF version in the Tor bundle if you install that way is not up to date .

---

### Post by Bashtard on 2013-07-07
> **Frogs Hair said:**
> The FF version in the Tor bundle if you install that way is not up to date .
Which is an excellent demonstration of privacy but not security. If you really want to be anonymous then you wantyour browser   to be indistinguishable from all the other Tor browsers. But for security you'd want it fully updated. I don't know how Tor could possibly keep up with Mozilla's patching schedule. I swear there are Firefox updates daily.

---

### Post by Stonecold1995 on 2013-07-07
> **KaosuX said:**
> TOR will reduce your overall security by a large margin. Why? Well, because it is very easy to set yourself up as an exit node and sniff the traffic. Since SSLStrip is also pretty easy to use, you're only asking to have your account stolen when using TOR. Sure, you may use it and not reach a malicious exit node, but you will one day. Using TOR and accounts you care about just does not make sense. 

TOR is a tool used for anonymity NOT security. Even then, it is not bullet proof and is subject to all kinds of attacks;

- Timing attacks over a fixed time structure to eventually isolate the user
- Malicious exit nodes that sniff/log your traffic (SSLStrip is handy here)
- Digital fingerprinting of web resources to track someone
- Tagging attacks

Those are just a handful of attack vectors. As you can see, the system is not as anonymous or secure as people seem to believe. Sure, it will improve your anonymity in many cases, but you have to be really careful about how and when you use the system.

I would advise against using TOR as a whole if you're trying to do something sensitive. However, if you're just trying to get around geographical locks or research a taboo topic then TOR will work fairly well for that. Don't go around using it all the time to check your bank account, email accounts, etc. If you do that, it is only a matter of time before those accounts are stolen.

If you have been using TOR like this, I suggest you check or request logs from your email provider to see the last 20 logged in IP addresses. If any of those don't match an address you use, then TOR has already screwed you.

Just because Tor is theoretically vulnerable to timing attacks doesn't mean it gives you LESS security, in fact it would give you more in that respect.

Malicious nodes are a problem, but a well secured website (like a bank) should not be affected by SSLStrip.

Digital fingerprinting is made HARDER by Tor, not easier.

As are tagging attacks.

The only think you would have to worry about is a bad Tor node either sniffing or modifying traffic on an unencrypted site, or an encrypted site that is affected by SSLStrip.  Other than that Tor provides much higher security.  Not to mention the fact that bad nodes are a huge rarity.

---

### Post by KaosuX on 2013-07-07
> **Stonecold1995 said:**
> Just because Tor is theoretically vulnerable to timing attacks doesn't mean it gives you LESS security, in fact it would give you more in that respect.

Malicious nodes are a problem, but a well secured website (like a bank) should not be affected by SSLStrip.

Digital fingerprinting is made HARDER by Tor, not easier.

As are tagging attacks.

The only think you would have to worry about is a bad Tor node either sniffing or modifying traffic on an unencrypted site, or an encrypted site that is affected by SSLStrip.  Other than that Tor provides much higher security.  Not to mention the fact that bad nodes are a huge rarity.


I disagree completely and here is why:

1. Timing attacks have become much easier to perform. Before hand you would need a lot of resources (think state sponsored) which most attackers couldn't get their hands on. However, a new breed of timing attack has been developed that specifically attacks anonymous communication networks (The Onion Router, and similar.) making it more than possible to isolate sensitive information from a user. Granted, there are many forms of timing attacks and the most notable was based on research published a long time ago that used statistical analysis combined with huge resources to isolate specific targets, but this was largely impractical unless a state sponsored attacker was trying to isolate you. One of the most effective and easiest new timing attacks is called a replay attack. For more information about this particular replay attack and how to directly use it against communication networks like TOR, please read: [http://www.cs.uml.edu/~xinwenfu/paper/ICC08_Fu.pdf](http://www.cs.uml.edu/~xinwenfu/paper/ICC08_Fu.pdf)

It is believed that one compromised cell is enough to destroy the entire chain of privacy if an attacker deploys a replay attack like the aforementioned one.

While this particular instance may not directly impact security per-say, it does negate the core reason for using an anonymous communication network in the first place (Assuming you're using TOR in an attempt to evade against a professional team) and needlessly taking on other risks associated with using this type of network for sensitive activity.

2. I will agree that the success of SSLStrip does rely on certain variables, all of which aren't in the complete control of an attacker. However, the core problem is that you're basically placing all of your trust into these exit nodes, assuming it should be safe because a malicious node is "rare". Granted, you could use TOR for 10,000 hours and only encounter a single malicious node, but that does not mean that one time won't completely screw you. In addition to this, advancements are being made all the time when it comes to intercepting "secure" traffic. What might be considered "secure" today is likely going to be obsolete and you will still be placing all of your trust into a network that has no guarantee you won't run into a malicious node that is actively logging everything you do.

I think any system that forces you to trust unknown user-hosted services does decrease your security. You may not agree with that or have any problems, but it does decease your overall security because you're placing blind trust in a system that many people love to abuse to attack those who place blind trust in the system to begin with.

Also, malicious nodes are more common than you think. Just because you don't notice anything wrong does not mean someone out there has not logged your account information, built a profile on you and sold it to a third-party (Since the traffic you send can likely contain personal information within that same session, allowing them to take what little information they have logged and attach it to some identifying piece of information so they can later sell it), or any other nefarious act you used the system to avoid in the first place. 

3. Digital fingerprinting techniques designed specifically against anonymous communication networks (TOR, etc.) are now commonplace. While many people *THINK* TOR makes digital fingerprinting harder, it doesn't by very much in reality. Here is a full paper on the subject: [http://lorre.uni.lu/~andriy/papers/acmccs-wpes11-fingerprinting.pdf](http://lorre.uni.lu/~andriy/papers/acmccs-wpes11-fingerprinting.pdf)

4. For tagging attacks see answer #1 and the replay attack.

For more reading:

[https://blog.torproject.org/blog/one-cell-enough](https://blog.torproject.org/blog/one-cell-enough)
[https://blog.torproject.org/category/tags/attacks](https://blog.torproject.org/category/tags/attacks)
[https://blog.torproject.org/blog/tor-and-beast-ssl-attack](https://blog.torproject.org/blog/tor-and-beast-ssl-attack)
[http://www.defcon.org/images/defcon-17/dc-17-presentations/defcon-17-gregory_fleischer-attacking_tor.pdf](http://www.defcon.org/images/defcon-17/dc-17-presentations/defcon-17-gregory_fleischer-attacking_tor.pdf)
[http://homes.cs.washington.edu/~yoshi/papers/Tor/wpes25-bauer.pdf](http://homes.cs.washington.edu/~yoshi/papers/Tor/wpes25-bauer.pdf) *INTERESTING READ*

TOR's main purpose is to provide anonymous communication, not security. Security and anonymity are two different things. These articles demonstrate that TOR can not only decrease your overall security, but also fail miserably to preserve your privacy against a dedicated attacker. Therefore, I stand by my statements that;

1. TOR sucks at trying to evade government snooping
2. TOR sucks at trying to avoid a policed state from spying on your communications (Which sadly is what it was originally designed for)
3. TOR sucks at handling sensitive information (Because you never really know who is listening on the other end of the connection)
4. TOR is pretty good at bypassing geographical blocks
5. TOR is pretty good at protecting your privacy against almost anyone else besides a skilled/dedicated attacker or state sponsored team
6. TOR is great for avoiding being profiled by automated systems, etc.

I am not saying TOR is useless, I am just saying that is isn't that great when privacy means life or death (Unless your attackers are not sophisticated) and it does decrease your overall level of security since you are possibly allowing the connection to be sniffed due to a malicious node.

Aside from malicious nodes and the such, there are other attack surfaces that negate the core reason for using the system to begin with. Check out the aforementioned link: [http://www.defcon.org/images/defcon-17/dc-17-presentations/defcon-17-gregory_fleischer-attacking_tor.pdf](http://www.defcon.org/images/defcon-17/dc-17-presentations/defcon-17-gregory_fleischer-attacking_tor.pdf)


I am not saying you're wrong and I am right. I respect your opinion, but these are the reasons why I stand by my opinion as well. Readers are free to come read this discussion, follow the links, do some research and decide for themselves if TOR is a good option for them. 

Thanks for the discussion.

---

### Post by Stonecold1995 on 2013-07-10
> **KaosuX said:**
> I disagree completely and here is why:

1. Timing attacks have become much easier to perform. Before hand you would need a lot of resources (think state sponsored) which most attackers couldn't get their hands on. However, a new breed of timing attack has been developed that specifically attacks anonymous communication networks (The Onion Router, and similar.) making it more than possible to isolate sensitive information from a user. Granted, there are many forms of timing attacks and the most notable was based on research published a long time ago that used statistical analysis combined with huge resources to isolate specific targets, but this was largely impractical unless a state sponsored attacker was trying to isolate you. One of the most effective and easiest new timing attacks is called a replay attack. For more information about this particular replay attack and how to directly use it against communication networks like TOR, please read: [http://www.cs.uml.edu/~xinwenfu/paper/ICC08_Fu.pdf](http://www.cs.uml.edu/~xinwenfu/paper/ICC08_Fu.pdf)

It is believed that one compromised cell is enough to destroy the entire chain of privacy if an attacker deploys a replay attack like the aforementioned one.

While this particular instance may not directly impact security per-say, it does negate the core reason for using an anonymous communication network in the first place (Assuming you're using TOR in an attempt to evade against a professional team) and needlessly taking on other risks associated with using this type of network for sensitive activity.

2. I will agree that the success of SSLStrip does rely on certain variables, all of which aren't in the complete control of an attacker. However, the core problem is that you're basically placing all of your trust into these exit nodes, assuming it should be safe because a malicious node is "rare". Granted, you could use TOR for 10,000 hours and only encounter a single malicious node, but that does not mean that one time won't completely screw you. In addition to this, advancements are being made all the time when it comes to intercepting "secure" traffic. What might be considered "secure" today is likely going to be obsolete and you will still be placing all of your trust into a network that has no guarantee you won't run into a malicious node that is actively logging everything you do.

I think any system that forces you to trust unknown user-hosted services does decrease your security. You may not agree with that or have any problems, but it does decease your overall security because you're placing blind trust in a system that many people love to abuse to attack those who place blind trust in the system to begin with.

Also, malicious nodes are more common than you think. Just because you don't notice anything wrong does not mean someone out there has not logged your account information, built a profile on you and sold it to a third-party (Since the traffic you send can likely contain personal information within that same session, allowing them to take what little information they have logged and attach it to some identifying piece of information so they can later sell it), or any other nefarious act you used the system to avoid in the first place. 

3. Digital fingerprinting techniques designed specifically against anonymous communication networks (TOR, etc.) are now commonplace. While many people *THINK* TOR makes digital fingerprinting harder, it doesn't by very much in reality. Here is a full paper on the subject: [http://lorre.uni.lu/~andriy/papers/acmccs-wpes11-fingerprinting.pdf](http://lorre.uni.lu/~andriy/papers/acmccs-wpes11-fingerprinting.pdf)

4. For tagging attacks see answer #1 and the replay attack.

For more reading:

[https://blog.torproject.org/blog/one-cell-enough](https://blog.torproject.org/blog/one-cell-enough)
[https://blog.torproject.org/category/tags/attacks](https://blog.torproject.org/category/tags/attacks)
[https://blog.torproject.org/blog/tor-and-beast-ssl-attack](https://blog.torproject.org/blog/tor-and-beast-ssl-attack)
[http://www.defcon.org/images/defcon-17/dc-17-presentations/defcon-17-gregory_fleischer-attacking_tor.pdf](http://www.defcon.org/images/defcon-17/dc-17-presentations/defcon-17-gregory_fleischer-attacking_tor.pdf)
[http://homes.cs.washington.edu/~yoshi/papers/Tor/wpes25-bauer.pdf](http://homes.cs.washington.edu/~yoshi/papers/Tor/wpes25-bauer.pdf) *INTERESTING READ*

TOR's main purpose is to provide anonymous communication, not security. Security and anonymity are two different things. These articles demonstrate that TOR can not only decrease your overall security, but also fail miserably to preserve your privacy against a dedicated attacker. Therefore, I stand by my statements that;

1. TOR sucks at trying to evade government snooping
2. TOR sucks at trying to avoid a policed state from spying on your communications (Which sadly is what it was originally designed for)
3. TOR sucks at handling sensitive information (Because you never really know who is listening on the other end of the connection)
4. TOR is pretty good at bypassing geographical blocks
5. TOR is pretty good at protecting your privacy against almost anyone else besides a skilled/dedicated attacker or state sponsored team
6. TOR is great for avoiding being profiled by automated systems, etc.

I am not saying TOR is useless, I am just saying that is isn't that great when privacy means life or death (Unless your attackers are not sophisticated) and it does decrease your overall level of security since you are possibly allowing the connection to be sniffed due to a malicious node.

Aside from malicious nodes and the such, there are other attack surfaces that negate the core reason for using the system to begin with. Check out the aforementioned link: [http://www.defcon.org/images/defcon-17/dc-17-presentations/defcon-17-gregory_fleischer-attacking_tor.pdf](http://www.defcon.org/images/defcon-17/dc-17-presentations/defcon-17-gregory_fleischer-attacking_tor.pdf)


I am not saying you're wrong and I am right. I respect your opinion, but these are the reasons why I stand by my opinion as well. Readers are free to come read this discussion, follow the links, do some research and decide for themselves if TOR is a good option for them. 

Thanks for the discussion.

So are you saying, that if you are trying to evade government spying, it would be better to NOT use Tor?  At least with Tor there's a very good chance that the exit node is not malicious, but with pretty much every ISP out there there is practically no chance it will not log you.

Plus, I think the most important thing is that it is very difficult, if not impossible, for a government to use timing attacks and the like on *everyone* using Tor.  Sure, if they focus on you (or a small group of people), Tor may not protect you sufficiently, but if you are just one in thousands (or more), it should be sufficient.  Also, for things like timing attacks where a bad node sends covert information using pauses in sending packets, etc, it will be found out eventually, so it will only work for so long.  The more practical method is just passive monitoring using the ISPs of good nodes, although this will be less accurate for them than owning a malicious node.

On some levels government snooping is sufficiently blocked.  There was a news report a while ago about the FBI being unable to track down a child pornography website because it was operating behind a Tor hidden service.  I think still today, the FBI is unable to "break" Tor.  If by "government" you mean something like the NSA then yes, of course they have the means to track you, but I still think it would be hard to track everyone simultaneously using entirely passive monitoring.

The fact that the US government is working with MasterCard (I think) and Visa to ban VPN providers just shows how helpless the government is on large scale spying when security is used.  A VPN is probably one of the weakest security measures, but apparently it's still enough to require them to try to reduce the amount of people actually using it.

---

### Post by KaosuX on 2013-07-14
> **Stonecold1995 said:**
> So are you saying, that if you are trying to evade government spying, it would be better to NOT use Tor?  At least with Tor there's a very good chance that the exit node is not malicious, but with pretty much every ISP out there there is practically no chance it will not log you.

Plus, I think the most important thing is that it is very difficult, if not impossible, for a government to use timing attacks and the like on *everyone* using Tor.  Sure, if they focus on you (or a small group of people), Tor may not protect you sufficiently, but if you are just one in thousands (or more), it should be sufficient.  Also, for things like timing attacks where a bad node sends covert information using pauses in sending packets, etc, it will be found out eventually, so it will only work for so long.  The more practical method is just passive monitoring using the ISPs of good nodes, although this will be less accurate for them than owning a malicious node.

On some levels government snooping is sufficiently blocked.  There was a news report a while ago about the FBI being unable to track down a child pornography website because it was operating behind a Tor hidden service.  I think still today, the FBI is unable to "break" Tor.  If by "government" you mean something like the NSA then yes, of course they have the means to track you, but I still think it would be hard to track everyone simultaneously using entirely passive monitoring.

The fact that the US government is working with MasterCard (I think) and Visa to ban VPN providers just shows how helpless the government is on large scale spying when security is used.  A VPN is probably one of the weakest security measures, but apparently it's still enough to require them to try to reduce the amount of people actually using it.

The FBI not being able to snoop on Tor users isn't that much of a surprise considering they are not a real intelligence agency, so their technical resources are rather limited. Tor would be more than enough to provide strong privacy against technically limited attackers (Local police, FBI, etc.) and that isn't much of a surpirse. My point was that Tor is not a strong option (or even a good option) when dealing with intelligence agencies or even sophisticated attackers. However, you make a valid point that these attack vectors are likely above and beyond the technical limitations of most people that work in the security field. I don't mean that as an insult, but personal experience has proven that most people are in it for a paycheck and don't care to go beyond the bare minimum their job requires, so don't expect them to put in a lot of time/effort outside of the basics they learned in school.

When reading my previous post just keep in mind that when I say government snooping I am talking about intelligence agencies and not incompetent sub-branches.

I think the rest of both posts just boils down to what a person is comfortable with and risks they are willing to take. You say that a malicious node will be discovered and not last too long, so you're not worried. That's a valid point. However, I personally see it as there being a potential risk of a malicous node collecting my data before it is shut down. Again, that is a valid concern. No matter how you look at it there is no clear right or wrong, but simply how comfortable someone is with using Tor for sensitive information. I feel that it shouldn't be used like that due to the potential risks, and you feel that the risks are so minimal that they are not worth worrying about. Let's just agree to disagree because both opinions are valid and we won't change  the other persons mind.

Do you have any links to the government working with major credit card companies to block VPN providers? Just wondering.

I wouldn't give those branches too much credit, though. The technical limiations of the FBI (From what the public knows) are a joke. They are so behind the times that it isn't even funny (Kind of scary). It is of no surprise any defensive measure would stop them as their response teams rely heavily on documented and published exploits, dictionary attacks, and rudimentary forensic examination/data recovery for almost all of their investigations. They are no better or worse than a group of lower to mid tier security researchers, but certainly nothing to be concered with if you wish to hide something from them, unless you are just careless. I say lower to mid tier because this is where you usually find people that are simply in it for a paycheck and don't do much beyond the bare minimum. 

Anyway, thanks again for the discussion.

---

### Post by Stonecold1995 on 2013-07-16
EDIT: crap, double post....

How do I delete posts again?

---

### Post by Stonecold1995 on 2013-07-16
> **KaosuX said:**
> The FBI not being able to snoop on Tor users isn't that much of a surprise considering they are not a real intelligence agency, so their technical resources are rather limited. Tor would be more than enough to provide strong privacy against technically limited attackers (Local police, FBI, etc.) and that isn't much of a surpirse. My point was that Tor is not a strong option (or even a good option) when dealing with intelligence agencies or even sophisticated attackers. However, you make a valid point that these attack vectors are likely above and beyond the technical limitations of most people that work in the security field. I don't mean that as an insult, but personal experience has proven that most people are in it for a paycheck and don't care to go beyond the bare minimum their job requires, so don't expect them to put in a lot of time/effort outside of the basics they learned in school.

When reading my previous post just keep in mind that when I say government snooping I am talking about intelligence agencies and not incompetent sub-branches.

I think the rest of both posts just boils down to what a person is comfortable with and risks they are willing to take. You say that a malicious node will be discovered and not last too long, so you're not worried. That's a valid point. However, I personally see it as there being a potential risk of a malicous node collecting my data before it is shut down. Again, that is a valid concern. No matter how you look at it there is no clear right or wrong, but simply how comfortable someone is with using Tor for sensitive information. I feel that it shouldn't be used like that due to the potential risks, and you feel that the risks are so minimal that they are not worth worrying about. Let's just agree to disagree because both opinions are valid and we won't change  the other persons mind.

Do you have any links to the government working with major credit card companies to block VPN providers? Just wondering.

I wouldn't give those branches too much credit, though. The technical limiations of the FBI (From what the public knows) are a joke. They are so behind the times that it isn't even funny (Kind of scary). It is of no surprise any defensive measure would stop them as their response teams rely heavily on documented and published exploits, dictionary attacks, and rudimentary forensic examination/data recovery for almost all of their investigations. They are no better or worse than a group of lower to mid tier security researchers, but certainly nothing to be concered with if you wish to hide something from them, unless you are just careless. I say lower to mid tier because this is where you usually find people that are simply in it for a paycheck and don't do much beyond the bare minimum. 

Anyway, thanks again for the discussion.
I understand that a powerful determined adversary will not be stopped by Tor, for long.  But it is still very effective for defeating dragnet surveillance, and unless you're already being closely watched, they won't focus on you, and you'll be free.  Of course, as the Tor Project states, if you don't use Tor correctly, it won't help you.  Which is why just foolishly connecting to non-SSL sites with Tor and entering highly sensitive information is of course dangerous, but using it correctly gives it the ability to be far more secure.

Also just fyi it's Tor, not TOR.  The Tor Project seems to get annoyed when people use TOR, dunno why though.

As for links about the government working to block VPN payments, there's a lot revealed with a simple search:
[https://startpage.com/do/search?query=vpn+credit+card+block&with_date=m](https://startpage.com/do/search?query=vpn+credit+card+block&with_date=m)

It's more of an anti-piracy thing on the surface, but it is being backed by the American government.

---

### Post by Pippa2 on 2013-07-16
On the internet there is no anonimity. If you get involved with anonimity, you will descover that anonimity isn't a fancy tor webbrowser, but it is a system. An overall complex of measures,  being extra ordinary clever, being inhuman. Have fun being no-one, being "smart", at the end you loose. Mostly having fun, enjoying using the internet. Thats what you loose. Ubuntu has nothing to do with ananomity, it is an op system, no rebel distro. In fact it is adware/spyware.

---

### Post by SchnappiJedi on 2013-07-18
> **Pippa2 said:**
> On the internet there is no anonimity. If you get involved with anonimity, you will descover that anonimity isn't a fancy tor webbrowser, but it is a system. An overall complex of measures,  being extra ordinary clever, being inhuman. Have fun being no-one, being "smart", at the end you loose. Mostly having fun, enjoying using the internet. Thats what you loose. Ubuntu has nothing to do with ananomity, it is an op system, no rebel distro. In fact it is adware/spyware.

Ubuntu is not adware/spyware...when was the last time Ubuntu server tried to install an add-on toolbar for you?

---

### Post by Stonecold1995 on 2013-07-19
> **Pippa2 said:**
> On the internet there is no anonimity. If you get involved with anonimity, you will descover that anonimity isn't a fancy tor webbrowser, but it is a system. An overall complex of measures,  being extra ordinary clever, being inhuman. Have fun being no-one, being "smart", at the end you loose. Mostly having fun, enjoying using the internet. Thats what you loose. Ubuntu has nothing to do with ananomity, it is an op system, no rebel distro. In fact it is adware/spyware.
I take security seriously, but I haven't lost the ability to have fun on the internet.  I do it all the time!  And you can have very good, if not near-perfect anonymity depending on which adversaries you are trying to avoid.  You can avoid hackers and the FBI quite well, and you can avoid NSA dragnet surveillance (to the best of my knowledge at least, for all I know they have perfected quantum computers and have made even 4096-bit RSA totally obsolete, which would of course break Tor security by revealing the AES-128 keys it uses).

Although I do agree with the adware/spyware, to a certain extent.  And not just because of the Amazon <snip>, but because Ubuntu does seem to be moving towards a system that makes it harder to do anything Canonical doesn't want you to do (e.g. with Mir, Unity, etc). While that technically isn't "advertising", it tries to accomplish the exact same thing, but in a less obvious way.

---

### Post by HermanAB on 2013-07-20
"Ubuntu is not adware/spyware...when was the last time Ubuntu server tried to install an add-on toolbar for you?"
It is called the 'lense' and it is installed when you install Ubuntu.

Xubuntu and Lubuntu are free from this malware though.

[Only Three hops between you and the Gulag]("http://www.aeronetworks.ca/search/label/Security")
:)

---

### Post by SchnappiJedi on 2013-07-31
> **HermanAB said:**
> "Ubuntu is not adware/spyware...when was the last time Ubuntu server tried to install an add-on toolbar for you?"
It is called the 'lense' and it is installed when you install Ubuntu.

Xubuntu and Lubuntu are free from this malware though.

[Only Three hops between you and the Gulag]("http://www.aeronetworks.ca/search/label/Security")
:)

I am only familiar with Ubuntu Server and I don't think what you are referring to applies to the server version.

---

### Post by vuarnet on 2013-07-31
First, let's agree: Tor is not a perfect (unbreakable) form of either security or privacy (anonymity). Now that we have that out the way, let's also agree that the truth about Tor's security and privacy (anonymity) lies in the gray area between (a) Tor offers no security / privacy and is therefore worthless, and (b) Tor offers perfect privacy / security.

Third, let's agree that the Tor Browser Bundle (TBB) is *one way* to use Tor. Tor can be used in lots of ways, some of which are more secure, others that are less secure than the TBB. It just depends on how you're setup. For instance, using Tor with an SSH tunnel routing traffic to an encrypted, shared intermediary proxy that censors header information (e.g. privoxy) can increase your anonymity greatly. Still not perfect, but much better. Logging into Facebook over Tor while you're doing something you think is "private"... not so much.

There has to be an understanding of the continuum of ways to use Tor, and in connection with other services, to provide a commensurate level of anonymity and/or security for your needs at the moment. Without that, you're just another ignorant propagandist saying Tor is either gold or crap, never understanding that it can be both *and *neither.

Using the TBB by itself will not provide you NSA-proof technology, because the timing attacks introduced through an ultra-low latency network like Tor are a very real threat and entirely possible with a relatively low amount of resources (for a nation-state adversary). But it will provide most users with an otherwise unattainable high level of anonymity, given a proper understanding of its limitations and the behavior patterns that should be changed when using Tor (such as not logging into your bank account as mentioned above). And while cryptanalysis is unfeasible under current technology, indefinite storage of data by the NSA and similar agencies means that your traffic need not only be today-proof but (ideally) forever-proof. Don't fool yourself -- this is practically impossible. But with patience, education and work, using Tor properly can get you better anonymity on the Internet than almost any other readily available technology on the planet.

/rant

---

