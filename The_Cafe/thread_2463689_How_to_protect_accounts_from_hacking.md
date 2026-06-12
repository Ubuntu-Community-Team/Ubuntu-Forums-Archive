---
title: "How to protect accounts from hacking?"
date: 2021-06-16
forum: The Cafe
---

### Post by gabsont on 2021-06-16
What methods do you use to protect your social media accounts? Do I need to use two-factor authentication and does it protect against hacking? Because my accounts have been hacked a lot lately.

---

### Post by TheFu on 2021-06-16
> **gabsont said:**
> What methods do you use to protect your social media accounts? Do I need to use two-factor authentication and does it protect against hacking? Because my accounts have been hacked a lot lately.

Follow the Basic Security links in my signature. These point to Ubuntu managed security mitigations and techniques.  Read the "Sticky" threads at the top of the Security sub-forum in these forums.  Have automatic, daily/weekly, versioned backups.

Yes, you should use 2FA from a hardware device (yukikey is the most well known, but any FIDO or FIDO2 device should be fine) and only connect using devices that fully support 2FA.  Some of your devices probably won't work with the hardware device due to certain limitations.  For example, trying to get a USBc yukikey to work with a cell phone can be a challenge. Just because a plug fits, that doesn't mean the protocol will work.

If you know the password, then it isn't complex enough. Use a password manager with very long, random, passphrases. Never expect to memorize it and never expect to type it in.

As for password manager, if they post your passwords on the internet, might be a good idea to check your common sense level. Stuff you expect to be "secret" shouldn't be posted to the internet.
Never use password managers that are built-into any browser. Don't.  Just Don't.  Browsers are so complex they are full of clear bugs that get fixed 10 times over and over - the same failure, just a different bug. Expecting them to be good at something like keeping passwords secure is asking too much. They often get Private Browsing wrong - that's just 1 example. Browsers are just too complex to trust.

Use a different email and password for every account.  This is most important for things connected to your money, finances, purchases and professional reputation. Those all need different email accounts and definitely different passwords, so if any one gets compromised, the others aren't immediately at risk.

If you are a target (wealthy, well-know, celebrity, govt policy employee, NGO, or a systems admin anywhere), then multiple, inconvenient efforts are necessary, like don't connect your cell phone to any social media accounts.  Setup the accounts without your name/identity connected - have a company or trust own the devices and phone contracts.

Don't click "Yes" to all questions in a browser.  No is the better answer 90% of the time.  True Security online usually requires a small inconvenience.

---

### Post by jolibe on 2021-06-20
Yes I agree. These are the basic rules to follow. But I think if there is a specific goal to hack your account, someone can still do it. You can see on the darknet at the [http://wtj5psom5zufu4yo.onion](http://wtj5psom5zufu4yo.onion) forum what services are available for hacking accounts. There are many hacking specialists.

---

### Post by TheFu on 2021-06-20
> **jolibe said:**
> Yes I agree. These are the basic rules to follow. But I think if there is a specific goal to hack your account, someone can still do it.

For most people, using 2FA devices blocks account hacks completely.  Avoid using a program on a cell device for 2FA. You want to use a separate USB key.  Google did a study and found something like 97% of hacks stopped when people enabled 2FA on their accounts.  That is sufficient for almost everyone, including celebrities, but it is a little inconvenient.

The only hacks my website accounts have experienced were due to poor choices for security setups by the company running those websites, never due to my password being cracked individually.  I've not been targeted.  

Most people are unwilling to be inconvenienced the same way that I am.  Back in the mid-1990s, one of my computers got hacked.  That changed my stance on computer security.  Around 2000, another computer got hacked, which changed everything again. I was 3 months behind on patching a home server. It was a different world back then.  

Only 1 of my systems has been hacked since. I was at a security conference. The system was freshly installed and patched the day before the conference. I had not connected to any network.  However, the default Ubuntu install enabled bluetooth. A guy at the conference hacked in over bluetooth and dropped a file as proof that I wouldn't miss.  I was anti-bluetooth before then, but never thought it would be enabled by default by Canonical.  Since then, I added to some boot scripts to disable bluetooth and unload the bluetooth kernel modules automatically. Periodically, I'll purge bluez* from my systems.  Did that yesterday after seeing a package get updated on one system.

Security is about mitigating risks and avoiding risks that cannot be mitigated.
Use a 2FA device if you don't want to be hacked online.

---

### Post by jolibe on 2021-06-23
But still, I'm sure almost any account can be hacked if necessary. On the darknet, people can do everything.

---

### Post by civilpolisen on 2021-06-23
If you're an important person, the hacking is much more fun. Someone manage to figure out Donald Trumps password to Twitter, maga2020 ... sort of easy for people interested in D. Trump! I'm not.

To use an generic and general anonymous e-mail address, along with a Firefox browser generated password , kZ3yMW3efb8nD32 , makes it more difficult to hack.Of-course, not to use the same password on many sites! :-)

Depending on the kind of information, security is not always an issue. It's a difference between a forum discussing plant and gardening and access to the bank...!  For me, I don't think a gardening forum would require a third party USB key... But that's for you to decide!

---

### Post by scorp123 on 2021-06-25
> **gabsont said:**
> Do I need to use two-factor authentication ...

Always.


> **gabsont said:**
>  ... and does it protect against hacking?

It's better to have it than to not have it. 2-Factor authentication would require a hacker to also somehow steal e.g. your mobile phone or USB token (or whatever device is used for 2FA), so it drastically increases the obstacle someone needs to overcome.


> **gabsont said:**
> Because my accounts have been hacked a lot lately.

You also have to question your own habits then. Do you accept friend requests from completely unknown people? Do you accept chat requests from completely unknown people? Do you click on anything anyone (known friend or not) sends to you without questioning it? Do you never browse in "Private Mode"? Do you never regularly completely wipe your browser cookies and browsing history? Do you have any ports open on your firewall or do you have any IoT devices in your home that might let traffic from the Internet into your own network at home? Do you use separate web browsers for separate activities? e.g. Firefox for e-banking, Chromium for everything else? Are you sure the passwords you use are strong enough, complex enough and long enough?

If you get hacked a lot as you say, then please take a close look at your habits and change them accordingly.

---

### Post by consulweb on 2021-06-29
> **gabsont said:**
> What methods do you use to protect your social media accounts? Do I need to use two-factor authentication and does it protect against hacking? Because my accounts have been hacked a lot lately.

i personaly use [Google Authenticator]("https://biz.pm/ggauth") with fingerprint to protect my social media accounts so if someone wants to hack my smartphone, they have to cut my finger off
):P

---

### Post by TheFu on 2021-06-29
> **consulweb said:**
> i personaly use [Google Authenticator]("https://biz.pm/ggauth") with fingerprint to protect my social media accounts so if someone wants to hack my smartphone, they have to cut my finger off
):P

Probably not.  The iPhone fingerprint reader was found to authenticate access after testing of 20-50 "master" fingerprints. No need for an actual finger to be used.  Plus, we leave fingerprints all around the world, daily, constantly. 
Many other attacks are also possible. Some $2 silly putty and we have a replacement finger. [https://arstechnica.com/information-technology/2013/09/defeating-apples-touch-id-its-easier-than-you-may-think/](https://arstechnica.com/information-technology/2013/09/defeating-apples-touch-id-its-easier-than-you-may-think/)

In short, best to avoid using a fingerprint for any access controls, besides to a cookie jar holding cookies.

The idea that finger prints are unique has been proven false, regardless of what TV/movies claim. Duplicates are extremely rare, but have been discovered in the wild outside identical twins.  Most fingerprint readers and software greatly simplify the resulting print. Collisions between those simplified prints happens millions of times in the real world, which is why a human interpretation is needed to match fingerprints and not just a computer matching 20 or 100 creases from an image.

There are many other lies on TV and in movies that have been accepted by average people. Some are extremely outlandish - like gun silencers. They aren't like shown in TV. Not at all. A loud noise still happens, just the peak is reduced about 10dB.  The best suppressors reduce that peak output by 15dB.  Still extremely loud for anyone in the area (say 1 mile).

---

