---
title: "Gozi Bank Heist"
date: 2013-01-23
forum: Security
---

### Post by mike acker on 2013-01-23
Suggested Reading

[https://krebsonsecurity.com/2013/01/three-men-charged-in-connection-with-gozi-trojan/#more-6878](https://krebsonsecurity.com/2013/01/three-men-charged-in-connection-with-gozi-trojan/#more-6878)

Excerpt
> Investigators say Gozi also was used to inject content directly into the  bank&#8217;s Web page as displayed by the victim&#8217;s browser, allowing  attackers to spoof the victim&#8217;s bank balance: In such attacks, the  crooks could empty an account of all available funds, and yet force the  victim&#8217;s browser to display the original balance before the robbery.notes

when you read the article you will note the attackers used customized obfuscation so that the malware -- used to effect the fraud described above -- would evade AV software

generally malware is 'injected' into the victim's O/S. In Linux/Ubuntu that's going to be hard to do. We have our own app library and system updates require the admin password .

still there is the question of browser plug-ins . these were a real pain in a windows system. i used to run a tool called WinPatrol.  This created a little guard dog called "Scotty". Scotty would bark every time somebody wanted to add a start up program -- or add to the browser . which was often . very often .  and a main reason i'm running Linux today .

hopefully it is not possible for a web page to add anything to either Firefox or to Chrome -- in the Linux/Ubuntu environment .  I'd like to see this discussion turn into a forum "sticky" as browser attacks are a main concern .

The Question posed here then is this: What prevents a web page from installing a "plug-in" for either Firefox or for Chrome ?

Another serious concern is what is known as "code injection"  .  

For code injection the attacker identified a system component -- likely a ".dll" -- that is loaded into the application's address space .  the idea then is to just re-linkedit the .dll -- in memory, adding whatever functionality ios needed . and gaining the privilege level of that .dll  . to prevent this the .dll should have been written as "re-enterable" (parm.lked=("RENT, ) -- so that the program can be stored in exec-only pages that are not modifyable by the app program ...

i used to run a PC Tools item on Windows called "ThreatFire".  this "injection" alarm went off.... again.... rather often . some application software wouldn't run unless the injection was allowed . bad way to run a railroad .

if Firefox is loaded into the application address space I hope it is thus protected... ( isn't that what RING1 and 2 were for ?? ) .

---

