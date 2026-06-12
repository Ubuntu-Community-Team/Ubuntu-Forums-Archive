---
title: "Linux Mint alert"
date: 2016-02-21
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2016-02-21
[http://news.softpedia.com/news/linux-mint-website-hacked-users-pointed-to-download-isos-with-backdoors-in-them-500707.shtml](http://news.softpedia.com/news/linux-mint-website-hacked-users-pointed-to-download-isos-with-backdoors-in-them-500707.shtml)
and
[http://blog.linuxmint.com/?p=2994](http://blog.linuxmint.com/?p=2994)
From the second link:> I&#8217;m sorry I have to come with bad news.

We were exposed to an intrusion today. It was brief and it shouldn&#8217;t impact many people, but if it impacts you, it&#8217;s very important you read the information below.

---

### Post by Habitual on 2016-02-21
17.3 Cinnamon only.
“Once in the live session, if there is a file in /var/lib/man.cy, then this is an infected ISO.”

---

### Post by bapoumba on 2016-02-21
Ah, was about to post that, thanks vasa1 :)

---

### Post by mikodo on 2016-02-21
Disconcerting! vasa1 or mods, maybe post that here too: [Forum Mint]("http://ubuntuforums.org/forumdisplay.php?f=453")

---

### Post by bapoumba on 2016-02-21
> **mikodo said:**
> Disconcerting! vasa1 or mods, maybe post that here too: [Forum Mint]("http://ubuntuforums.org/forumdisplay.php?f=453")

Yeah, thanks, this is where I was to post it. Linked here from a closed sticky.

---

### Post by buzzingrobot on 2016-02-21
Forums were also compromised, i.e., a dump of the entire database.  That's usernames, (encrypted) passwords, posts, email addresses, private messages, etc.

Anyone who used a username/password combination there that they also used anywhere else that they do not want to be at risk, change 'em.

---

### Post by ajgreeny on 2016-02-21
I see the LinuxMint forum itself is down at the moment, no doubt trying to clean everything up.

---

### Post by Habitual on 2016-02-21
> **buzzingrobot said:**
> Forums were also compromised, i.e., a dump of the entire database.  That's usernames, (encrypted) passwords, posts, email addresses, private messages, etc.Where did you get that info?

---

### Post by buzzingrobot on 2016-02-21
> **Habitual said:**
> Where did you get that info?

 Here -- [http://blog.linuxmint.com/](http://blog.linuxmint.com/)

and here -- [http://news.softpedia.com/news/linux-mint-forums-completely-compromised-users-need-to-change-their-passwords-500724.shtml](http://news.softpedia.com/news/linux-mint-forums-completely-compromised-users-need-to-change-their-passwords-500724.shtml)

---

### Post by QIII on 2016-02-21
The perverse drive to do this sort of thing is mind-boggling and frustrating.

Probably less likely a purely "theft" motive than an adolescent "street cred" motive for bragging rights.

Doing wrong is easy and anyone can do it.  Doing right is much harder.  I'd be happy to find bragging rights in the latter.

---

### Post by poorguy on 2016-02-21
People who do things as this should be hanged until dead.
IMO they have no use in life other than to destroy and therefore serve no purpose.

---

### Post by Crimple on 2016-02-22
Do you think that this questions security at distro level?
I know it's not directly related but my reasoning is: *if* this situation reveals some permissiveness from Mint's team when it comes to the site's security can they be somewhat lax with the rest as well?

---

### Post by vasa1 on 2016-02-22
More: [https://news.ycombinator.com/item?id=11143162](https://news.ycombinator.com/item?id=11143162) and the "parent" link: [https://news.ycombinator.com/item?id=11142986](https://news.ycombinator.com/item?id=11142986)

---

### Post by Morbius1 on 2016-02-22
> **poorguy said:**
> People who do things as this should be hanged until dead.
IMO they have no use in life other than to destroy and therefore serve no purpose.
I don't know if I would go that far but you have to wonder about the motive.

One would want to target Microsoft because Windows owns the desktop space and you have the potential to access 90% of the population. 
One would want to target Apple because it's users are wealthier than everyone else even though their numbers are smaller. 
One would want to target Linux on the desktop because .... um ....

---

### Post by CharlesA on 2016-02-22
> **Morbius1 said:**
> I don't know if I would go that far but you have to wonder about the motive.

One would want to target Microsoft because Windows owns the desktop space and you have the potential to access 90% of the population. 
One would want to target Apple because it's users are wealthier than everyone else even though their numbers are smaller. 
One would want to target Linux on the desktop because .... um ....

Reasons! Obviously... :P

---

### Post by buzzingrobot on 2016-02-22
These kind of attacks are done for money.  Data in forum database dumps -- email addresses, usernames, passwords (subject to brute force decryption) are advertised online and sold.

Any server on the net is subject to attack.  Linux distribution ISO's are files on servers. If bad actors acquire access to a server, they could even change the checksums the site displays to match the checksums generated by their bogus install images.

And, in the Mint case, all the attackers needed to do was redirect one URL on Mint's Wordpress site to point to their server. To be accurate, Mint's site does list dozens of mirrors that apparently remained safe to use, and the attack only affected one link to 17.3 Cinnamon images.

I've seen various ideas about improving things, often based around PGP.  I tend to think effective use of PGP is not viable in the mainstream. Anything that means users cannot just download, burn, and boot a single install image isn't likely to have a chance.

---

### Post by vasa1 on 2016-02-22
[Interesting read]("https://lwn.net/Articles/676613/") which has opinions, if not facts, about how Mint is built.

---

### Post by Habitual on 2016-02-22
> **QIII said:**
> The perverse drive to do this sort of thing is mind-boggling and frustrating.

Probably less likely a purely "theft" motive than an adolescent "street cred" motive for bragging rights.

Doing wrong is easy and anyone can do it.  Doing right is much harder.  I'd be happy to find bragging rights in the latter.
[http://www.zdnet.com/article/hacker-hundreds-were-tricked-into-installing-linux-mint-backdoor/](http://www.zdnet.com/article/hacker-hundreds-were-tricked-into-installing-linux-mint-backdoor/)

> **buzzingrobot said:**
> Here -- [http://blog.linuxmint.com/](http://blog.linuxmint.com/)
Thanks. Things are very fluid, so I read about it "late".

---

### Post by buzzingrobot on 2016-02-22
> **vasa1 said:**
> [Interesting read]("https://lwn.net/Articles/676613/") which has opinions, if not facts, about how Mint is built.

I searched Google on 'Linux" for the last 24 hours.  It's full of hyped reports from the usual places, with bogus claims of all Mint's ISO being replaced, etc.  Plus, "I thought open source was supposed to be secure??". 

There's an obvious issue here that pertains to any OS that posts install images for download, including Microsoft. Many in the LWN thread take their comments into a broader area, though.

Unfortunately, most people will not come away with an accurate understanding of what happened. Mint's reputation, and that of Linux in general, will take a hit.

---

### Post by montag dp on 2016-02-22
Hm, I guess they probably got my email address.  I used to run Mint and I have an account on their forums.  Oh well, at the worst I guess I might get more spam now.

---

### Post by Crimple on 2016-02-22
> **vasa1 said:**
> [Interesting read]("https://lwn.net/Articles/676613/") which has opinions, if not facts, about how Mint is built.
Yes, it is an interesting read, even if only opinion based;
it gave me a new light into Mint's world.

---

### Post by sudodus on 2016-02-22
> **vasa1 said:**
> [Interesting read]("https://lwn.net/Articles/676613/") which has opinions, if not facts, about how Mint is built.

> **zemartins said:**
> Yes, it is an interesting read, even if only opinion based;
it gave me a new light into Mint's world.

+1

---

### Post by poorguy on 2016-02-22
> **Morbius1 said:**
> I don't know if I would go that far but you have to wonder about the motive.

One would want to target Microsoft because Windows owns the desktop space and you have the potential to access 90% of the population. 
One would want to target Apple because it's users are wealthier than everyone else even though their numbers are smaller. 
One would want to target Linux on the desktop because .... um ....

The motive is theft and nothing else.
I know my statement is radical one and may seem extreme. 
IMO this is no different than any other form of criminal activity.
This is done with malice and intention only to exploit and steal from another.

---

### Post by QIII on 2016-02-22
Thanks for the link to the zdnet article, Habitual.  That IS disturbing.

---

### Post by Habitual on 2016-02-22
> **QIII said:**
> Thanks for the link to the zdnet article, Habitual.  That IS disturbing.
You're welcome. Dubious content IMO. Like all spyware/trojans/hack attacks, the idea is not to be found out and this guy is beating his chest about it?
"Look at me! I'm somebody." mentality. Surely a sign of immaturity. Too many Mr. Robot episodes.

> **montag dp said:**
> Hm, I guess they probably got my email  address.  I used to run Mint and I have an account on their forums.  Oh  well, at the worst I guess I might get more spam  now.Check it at [https://haveibeenpwned.com/](https://haveibeenpwned.com/) </grain_of_salt>

I'm willing to bet the LinuxMint isn't "just a hobby" for Clem any longer.

---

### Post by poorguy on 2016-02-22
So now the real question is how secure are the other Linux forums and servers.

---

### Post by Morbius1 on 2016-02-22
Although it never got to the point that the actual ISO was tampered with the Ubuntu forums suffered the same problem - not that long ago:

Ubuntu forums hacked; 1.82M logins, email addresses stolen: [URL="http://www.omgubuntu.co.uk/2013/07/ubuntu-forum-hacked-users-advised-to-change-passwords"]http://www.omgubuntu.co.uk/2013/07/ubuntu-forum-hacked-users-advised-to-change-passwords

[/URL][URL="http://www.omgubuntu.co.uk/2013/07/ubuntu-forum-hacked-users-advised-to-change-passwords"]This is why we all use Ubuntu One to log into the forums these days.
[/URL][URL="http://www.omgubuntu.co.uk/2013/07/ubuntu-forum-hacked-users-advised-to-change-passwords"]


[/URL]

---

### Post by bashiergui on 2016-02-22
> **poorguy said:**
> So now the real question is how secure are the other Linux forums and servers.
Nothing is secure. Assume everything is breached. Even ubuntu forums was breached a few years ago. (Edit: Morbius snuck the link in I was too lazy to dig up, so thanks :-)

No organization has any incentive to run a tight ship. There is every incentive to push out the newest product as fast as possible on the existing insecure platform. No one is incentivized to upgrade old hardware. No one wants to spend the money to migrate to an upgraded OS or platform. Just bolt on some ****** php code so it will do the newest greatest thing. "We can't upgrade some god awful wordpress plugin because it will break our ****** old website. "

As long as no one has any incentive to do things properly and securely (which will be eternally from where I'm sitting), assume everything is breached. Use unique complex passwords across every site and replace passwords periodically.

---

### Post by SantaFe on 2016-02-22
> **Morbius1 said:**
> [URL="http://www.omgubuntu.co.uk/2013/07/ubuntu-forum-hacked-users-advised-to-change-passwords"]

[/URL][URL="http://www.omgubuntu.co.uk/2013/07/ubuntu-forum-hacked-users-advised-to-change-passwords"]This is why we all use Ubuntu One to log into the forums these days.
[/URL][URL="http://www.omgubuntu.co.uk/2013/07/ubuntu-forum-hacked-users-advised-to-change-passwords"]


[/URL]

Yeah, but what happens if Ubuntu One gets hacked?  Seems like too tempting a target for Hackers if you ask me.  (And even if you don't ask me I'll tell you anyway so there.) ;)

---

### Post by yoshii on 2016-02-22
To whoever posted the link to:  [https://lwn.net/Articles/676613/](https://lwn.net/Articles/676613/)
Thanks!  That was an informative read.  I didn't read all of it, but there's some good points about Mint's upkeep flaws.  
I'm so glad I didn't go with Mint, but I sure hope they reorganize their efforts in a way that makes them more secure as well as with fewer design flaws.

---

### Post by poorguy on 2016-02-22
> **bashiergui said:**
> Nothing is secure. Assume everything is breached. Even ubuntu forums was breached a few years ago. (Edit: Morbius snuck the link in I was too lazy to dig up, so thanks :-)

No organization has any incentive to run a tight ship. There is every incentive to push out the newest product as fast as possible on the existing insecure platform. No one is incentivized to upgrade old hardware. No one wants to spend the money to migrate to an upgraded OS or platform. Just bolt on some ****** php code so it will do the newest greatest thing. "We can't upgrade some god awful wordpress plugin because it will break our ****** old website. "

As long as no one has any incentive to do things properly and securely (which will be eternally from where I'm sitting), assume everything is breached. Use unique complex passwords across every site and replace passwords periodically.

Doesn't sound very good but I can sure dig being a realist about the present state of affairs.
I understand nothing is bulletproof and can be compromised.
Risky at best. Seems nothing is secure anymore.
Guess it's the price we pay for the world at our fingertips.

---

### Post by Morbius1 on 2016-02-22
My user name, email address, physical address, medical records, and lord knows what else has already been compromised from may different sources. It's possible someone who has already posted in this topic is in possession of some of that information. And this isn't counting whatever information the NSA, MI6, whatever the KGB is called today, and some 14 year old in China has on me. 

I'm in a constant battle to reduce the amount of stupid in my life. I have had some but not impressive success in the things I personally have control over but the things I have no control over - not so much.

---

### Post by poorguy on 2016-02-22
It is a bummer that people do stuff like this but there really isn't anyway to prevent it from happening.
It would be a good thought to use all of that brain power for a better cause towards the Linux world.

---

### Post by Habitual on 2016-02-22
> **bashiergui said:**
> Nothing is secure. Assume everything is  breached. Even ubuntu forums was breached a few years ago. (Edit:  Morbius snuck the link in I was too lazy to dig up, so thanks :smile:

No organization has any incentive to run a tight ship. There is every  incentive to push out the newest product as fast as possible on the  existing insecure platform. No one is incentivized to upgrade old  hardware. No one wants to spend the money to migrate to an upgraded OS  or platform. Just bolt on some ****** php code so it will do the newest  greatest thing. "We can't upgrade some god awful wordpress plugin  because it will break our ****** old website. "

As long as no one has any incentive to do things properly and securely  (which will be eternally from where I'm sitting), assume everything is  breached. Use unique complex passwords across every site and replace  passwords periodically.
I like the way you think. You could come to work for me anytime. I just wish I had a position for you.

"All of a sudden" users are now concerned with md5sum digests?

---

### Post by Habitual on 2016-02-22
> **Habitual said:**
> I like the way you think. You could come to work for me anytime. I just wish I had a position for you.

"All of a sudden" users are now concerned with md5sum digests?

from [http://www.zdnet.com/article/hacker-hundreds-were-tricked-into-installing-linux-mint-backdoor/](http://www.zdnet.com/article/hacker-hundreds-were-tricked-into-installing-linux-mint-backdoor/)
> "Who the f**k checks those anyway?" the hacker said.

If he knows users don't check md5sum digests why bother changing published values?

I have my doubts about the zdnet article.

---

### Post by bashiergui on 2016-02-22
> **Habitual said:**
> from [http://www.zdnet.com/article/hacker-hundreds-were-tricked-into-installing-linux-mint-backdoor/](http://www.zdnet.com/article/hacker-hundreds-were-tricked-into-installing-linux-mint-backdoor/) If he knows users don't check md5sum digests why bother changing published values?Probably to avoid detection for a while. But he bungled that. He bungled the botnet he was trying to build too. The malicious file wouldn't ever execute unless manually changed to execute by the user. LOL. [http://www.csoonline.com/article/3035743/security/linux-mint-hacked-compromised-data-up-for-sale-iso-downloads-backdoored.html](http://www.csoonline.com/article/3035743/security/linux-mint-hacked-compromised-data-up-for-sale-iso-downloads-backdoored.html)

> I have my doubts about the zdnet article.What are your doubts?

---

### Post by goofprog on 2016-02-22
> **Morbius1 said:**
> I don't know if I would go that far but you have to wonder about the motive.
One would want to target Linux on the desktop because .... um ....

Computer users can survive off of nothing.. (evil grin)

---

### Post by night_sky2 on 2016-02-23
Very bad. I hope they get back online soon. I run Mint but not prob for me since my medium was booted from a ISO file I downloaded 2 months ago.

> **montag dp said:**
> Hm, I guess they probably got my email  address.  I used to run Mint and I have an account on their forums.  Oh  well, at the worst I guess I might get more spam now.

I am glad I used a junk mail.

---

### Post by vasa1 on 2016-02-23
Can someone please explain the consequences of the hacker stealing the database of the Linux Mint Forum?

So they get my username, possibly my login password, and the e-mail address I provided at the time of registering. How can the hacker or whoever buys the database then "pwn" my e-mail account as [illustrated here]("https://i.imgsafe.org/f0b046e.png") by a poster @ [Wilders]("http://www.wilderssecurity.com/threads/linux-mint-website-hacked-users-tricked-into-downloading-isos-with-backdoors.383981/page-2#post-2566938")?

^^^ That's a genuine question. I don't know which is why I'm asking.

---

### Post by maglin2 on 2016-02-23
Unless your mint forum password was the same as or similar to your e-mail password I can't personally see why this would make your e-mail account more likely to be hacked (or even spoofed) by this lot than by any of the other bad guys and spammers who already probably have your email address by many other means (lots certainly have mine). 

But I await comment with interest.

---

### Post by vasa1 on 2016-02-23
> **maglin2 said:**
> Unless your mint forum password was the same ...
Thank you! I should have mentioned that my email password and forum password are always different. Not only that, but I don't use my "important" email address for registering on such sites.

---

### Post by maglin2 on 2016-02-23
Reading some of the links posted here it seems that anyone who routinely installed an AV as part of their new set-up would have rapidly discovered the compromised iso. The trojan used was well known and detected by sophos and presumably other AVs. This seems to get reported as a fairly inept hack generally though, so I don't know if much comfort can be taken from that.

---

### Post by yoshii on 2016-02-23
I assume you mean anti-virus, and not audio-visual.  :D

---

### Post by Habitual on 2016-02-23
> **maglin2 said:**
> Reading some of the links posted here it seems that anyone who routinely installed an AV as part of their new set-up would have rapidly discovered the compromised iso. The trojan used was well known and detected by sophos and presumably other AVs. This seems to get reported as a fairly inept hack generally though, so I don't know if much comfort can be taken from that.

By the time they installed the OS, they are infected, so then installing and "using" A/V would only force a re-install of the same polluted OS.
One could hope that after 2 installs of an infected ISO, the "user" would then check the md5sum against published values and then conclude
the ISO is dirty.
But we all know users don't think logically nor have anyone to think for them in such an extreme case.

Ultimately, it's the user's responsibility to verify what they've downloaded before they install, not after.
That is my opinion.

---

### Post by sammiev on 2016-02-23
> **Habitual said:**
> Ultimately, it's the user's responsibility to verify what they've downloaded before they install, not after.
That is my opinion.

+1 Well spoken.

---

### Post by Crimple on 2016-02-23
> **Habitual said:**
> Ultimately, it's the user's responsibility to verify what they've downloaded before they install, not after.
The hacker posted both the link to the compromised ISO *and* a fake checksum,
I had the chance to see it just before the site was taken off.

---

### Post by maglin2 on 2016-02-24
> **Habitual said:**
> By the time they installed the OS, they are infected, so then installing and "using" A/V would only force a re-install of the same polluted OS.
One could hope that after 2 installs of an infected ISO, the "user" would then check the md5sum against published values and then conclude
the ISO is dirty.
But we all know users don't think logically nor have anyone to think for them in such an extreme case.

Ultimately, it's the user's responsibility to verify what they've downloaded before they install, not after.
That is my opinion.

I agree. As noted above though, the hacker may also have modified the published md5sum to match the compromised iso.

---

### Post by berk6 on 2016-02-24
Yeah I too heard about this. I believe it took the links to other sources for 'hacked' isos.

---

### Post by olduse78802 on 2016-02-25
In all the years i have been using ubuntu , mint , fedora , red hat , pclinuxos etc I dont think i ever used the chk sum to check the downloaded img.  I usually just download it and use a windows machine using nero burning rom to burn it.  I still have a cd of caldera linux .  Couple of years ago i tried to install it on an older machine .  Ran into the old video driver problems.  Made me appreciate what linux has become now.  I also have a copy of windows 3.11 and got that to run barely.  It was a hoot to compare it with windows xp and 7.

It is probably because i am a little lazy .  I am using mint 17.3  Cinnie  at the moment.  As far as i can tell the repos were not affected because i have a couple of updates installed that day.

Just as a side i scanned it with a av scanner and nothing showed up .  I just heard about it yesterday evening.

---

### Post by Habitual on 2016-02-25
No repos were harmed in the making of this hack.
*Only **one** link was altered and no md5sums were edited* at or under [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

All returning members to [http://forums.linuxmint.com](http://forums.linuxmint.com) are now re-directed to [https://forums.linuxmint.com](https://forums.linuxmint.com)
The blog is https also. As is the Community page.

Screws have been turned and things tightened up.
As for the Monday Morning Quarterbacks... LM does not need to recover its "credibility".

The core of its credibility comes from Clem himself.

**Full Disclosure**: Thu Feb 25, 2016 -  5:20:37 PM EST
md5sums were edited. I was not privy to that info and the info is not seen on any public post.

---

### Post by montag dp on 2016-02-25
> **olduse78802 said:**
> In all the years i have been using ubuntu , mint , fedora , red hat , pclinuxos etc I dont think i ever used the chk sum to check the downloaded img.  I usually just download it and use a windows machine using nero burning rom to burn it.  I still have a cd of caldera linux .  Couple of years ago i tried to install it on an older machine .  Ran into the old video driver problems.  Made me appreciate what linux has become now.  I also have a copy of windows 3.11 and got that to run barely.  It was a hoot to compare it with windows xp and 7.

It is probably because i am a little lazy .  I am using mint 17.3  Cinnie  at the moment.  As far as i can tell the repos were not affected because i have a couple of updates installed that day.

Just as a side i scanned it with a av scanner and nothing showed up .  I just heard about it yesterday evening.If you installed from an ISO downloaded sometime during the time frame from January to last weekend, you should probably reinstall just to be safe.  If not, then there's nothing to be worried about.

---

### Post by Crimple on 2016-02-25
> **Habitual said:**
> As for the Monday Morning Quarterbacks... LM does not need to recover its "credibility".
I'd say it needs something of that kind.



> **Habitual said:**
> The core of its credibility comes from Clem himself
And why should we feel reassured with that?

---

### Post by rewyllys on 2016-02-25
> **montag dp said:**
> If you installed from an ISO downloaded sometime during the time frame from January to last weekend, you should probably reinstall just to be safe.  If not, then there's nothing to be worried about.
The attack occurred on Saturday, February 20, and was recognized by the Linux Mint tean within just a few hours.  If your ISO was downloaded on February 19 or earlier, you can rest easy.

---

### Post by buzzingrobot on 2016-02-25
The real security problem here was Wordpress, which has a long history of being exploited, especially via its plugins, and with its configuration by Mint. That's why the attacker was able to alter one of the site's files to point one URL to his bogus ISO on another server.  Once he had access, it was just a quick edit.

Lax web site security does not translate to bad distribution security. After all, almost everything in a Mint install comes from a Canonical repository.

Mint published the name and location of the single file installed by the altered image. It's easily found and removed.  

Yes, similar attacks may have happened earlier that went undetected.  But, the same accusation could be made against any distribution.  Undetected attacks are just that: undetected attacks.

The current state of the art requires **users** to jump through some hoops if they want to try to ensure the safety of the Linux images they download.  Most probably don't want to do that. (And way too many are happy to download almost anything from almost any web site without paying much attention at all to where it's actually coming from.)

---

### Post by kansasnoob on 2016-03-01
It's been so long since I used it I'd forgotten but I had a forums account and got a PM this AM:

> Hello,
You are receiving this message because you have an account registered on
forums.linuxmint.com:

    Username: kansasnoob
    Email: <snip>

The Linux Mint forums software was compromised by an external attacker. As a result, the
attacker has gained access to read your username, email address and an encrypted (hashed
and salted) copy of your password from the forum database.

If you have used this password and email address to authenticate at any other website, you
are urged to reset the password on those accounts immediately as the attacker may be able
to use the compromised personal information to access these other accounts. It is
important to have a distinct password for different accounts.

Please also take the time to change your forums.linuxmint.com account password.

For any queries or questions related to this incident, please visit the following topic:

[https://forums.linuxmint.com/viewtopic.php?f=60&t=217506](https://forums.linuxmint.com/viewtopic.php?f=60&t=217506)

We apologize for any inconvenience to the Linux Mint community, thank you for your
understanding.

The Linux Mint administration team.


I never use the same password in two places so not worried :)

---

