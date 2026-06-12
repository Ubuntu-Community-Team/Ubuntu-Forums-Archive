---
title: "Financial Data privacy and security"
date: 2011-04-22
forum: Security
---

### Post by markMDW on 2011-04-22
Privacy Question from Newbies regarding Ubuntu, Linux and FOSS applications where privacy protects one's personal property:

With Ubuntu Trusted Applications, What type of measures are taken to insure that a program in the Ubuntu Software Center or other Linux package managers, does not transmit data to an awaiting lurker bent on theft?   

What if there is an undocumented feature that collects private data and transmits it to a hosting charlatan?  

Suppose a mischievous organization created a small Fork of a FOSS financial application that transmitted someones credentials and account information to their waiting computer, Then the user discovered later that their account had been cashed out? Has that ever happened? 

I suppose major distributions check their packages to make certain there isn't any spyware loaded inside an otherwise reputable Linux Program?  I understand we are "free" to look at the source-code but most of us aren't programmers.     Would something like that be easy to catch?

With Non-Free software usually some corporation "owns" the program and their reputation is at stake.  Still, that's not to say that some Software CEO is not at this very moment lurking through private data for the fun of it, because of a privileged undocumented feature, invisible in their binary, that only an elite few know about.   I wouldn't be surprised by that.  But I'm not too scared of them because in such cases they probably would not want to steal anything, just snoop or analyze for a new market strategy.

On the other hand, with Forks in Free and Open Software, is there a danger that crackpot con-artists are out stealing identities and bank accounts?  I'm scared to try out some Linux financial type software even though it does everything I want it too, because I don't know who tinkered with it.  Instead I guess I will use something prepared by Uncle Sam and the Treasury Department using WINE.  Yes, I trust government more.

---

### Post by Ryan Dwyer on 2011-04-22
It all depends which repositories you have enabled.

Everything in main and universe can be trusted to be safe, as they are open source and everything is approved by trusted people (eg. repository maintainers or synced straight from Debian's repos).

I believe the restricted repository is mostly binary drivers so they could really contain anything. Use at your own risk.

Launchpad PPAs don't really have any quality control on them. I believe the PPA author (ie. whoever set it up) can upload whatever they want to it. For this reason you should be cautious when using Launchpad PPAs.

There are also third parties who host their own repositories, but it all comes down to which companies you trust.

---

### Post by markMDW on 2011-04-22
Thanks, I have Ubuntu as a Trusted Repository site. :-)

---

