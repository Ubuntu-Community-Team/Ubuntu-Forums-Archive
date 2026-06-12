---
title: "DNSChanger Trojan"
date: 2012-03-02
forum: The Cafe
---

### Post by sunewbie on 2012-03-02
Just heard this news: 

[DNS Changer virus / Trojan March 8th](http://techcrawlers.com/dns-changer-virus-march-8th/)

[Internet to be shutdown by FBI on 8th March 2012](http://www.hackread.com/read/hackread/1768)

[Easily Remove DNSChanger Trojan Virus on Windows 7, Vista, XP and Mac](http://technojourney.com/softwares/easily-remove-dnschanger-trojan-virus-windows7-vista-mac-removal-repair-tool/)

[Internet Doomsday March 8 - The truth about DNSChanger viruses](http://features.techworld.com/security/3338782/internet-doomsday-march-8-truth-about-dnschanger-viruses/)

[DNSChanger, March 8th and You](http://www.infosecisland.com/blogview/20509-DNSChanger-March-8th-and-You.html)

Will it affect Linux?

---

### Post by quinne on 2012-04-23
Bumping this because I have the same question -- Does this effect Linux?  My guess is that it doesn't, but would like to hear from someone who knows for sure.

---

### Post by nerdopolis on 2012-04-23
From what I can tell DNSChanger changes the DNS server settings to some rouge DNS server on some Windows boxes. 

What it seems they are going to to in July is shutdown this rouge DNS server in July, so any box set to use the rouge DNS server will no longer be able to resolve addresses. 

I think DNSChanger is Windows malware that used *Windows* exploits to get the permissions to change the DNS settings...

---

### Post by sunewbie on 2012-04-24
AFAIK, since it exploits browser security, it can penetrate FF or any other browser in Linux also.

Since Linux has different way of working, so I am not sure if it can change DNS settings for Linux based systems.

I also posted it on Mint forums. Here is the link

[http://forums.linuxmint.com/viewtopic.php?f=58&t=96098](http://forums.linuxmint.com/viewtopic.php?f=58&t=96098)

Hope this helps

---

### Post by stmiller on 2012-04-25
Does not effect Linux. This malware changes Windows registry settings to change the DNS settings in Windows (only). 

It does not attack the browser as someone mentioned. Cheers,

---

### Post by Bandit on 2012-04-25
> **stmiller said:**
> Does not effect Linux. This malware changes Windows registry settings to change the DNS settings in Windows (only). 

It does not attack the browser as someone mentioned. Cheers,

This.. Also it can not change your DNS under linux without you running it under root by surfing the net as root and then it must be written for linux..

---

### Post by Old_Grey_Wolf on 2012-04-25
> **stmiller said:**
> Does not effect Linux. This malware changes Windows registry settings to change the DNS settings in Windows (only). 

It does not attack the browser as someone mentioned. Cheers,

+1

In Ubuntu, it would have to change the Network Manager's IPv4 or IPv6 DNS server settings. That requires root or sudo. The DNS settings in Linux are not part of the browser settings. As Bandit has said, you have to be root and the malware has to be able to run on the Linux kernel to change the Network Manager's DNS settings.

---

### Post by sunewbie on 2012-04-26
Thank you all for reply. 

I am not technical, just an end user. Posting in forums helps me understand Linux better, thanks to fantastic opensource community.

Cheers

---

### Post by stetteo on 2012-05-30
I just discovered that DNSchanger actually affects Ubuntu.

---

### Post by VE6EFR on 2012-05-30
> **stetteo said:**
> I just discovered that DNSchanger actually affects Ubuntu.

Do you have a link to your source? From what I understand that's not the case.

---

### Post by stetteo on 2012-05-30
> **VE6EFR said:**
> Do you have a link to your source? From what I understand that's not the case.

I have to change the previous statement: DNSChanger affected the router via Windows :)
It happened to a friend of mine.

---

### Post by Bandit on 2012-05-30
> **stetteo said:**
> I have to change the previous statement: DNSChanger affected the router via Windows :)
It happened to a friend of mine.

Not sure how a virus can effect a password protected router. Then again my router has nothing to do with my DNS routing anyway.

---

### Post by sammiev on 2012-05-30
For something that was going to happen March 8 and shut down the Internet by the FBI that did not happen and come back to life, I would suggest closing this thread.

---

### Post by sunewbie on 2012-05-31
> **sammiev said:**
> For something that was going to happen March 8 and shut down the Internet by the FBI that did not happen and come back to life, I would suggest closing this thread.

me too thinks that it should have happened in march, when I posted.

Looks like it's risen from dead or time to close this thread.

But I do not have rights to close the thread. only a mod can close it :)

---

### Post by Elfy on 2012-05-31
Like this :)

---

