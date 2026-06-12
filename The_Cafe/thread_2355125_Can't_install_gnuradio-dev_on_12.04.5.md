---
title: "Can't install gnuradio-dev on 12.04.5"
date: 2017-03-09
forum: The Cafe
---

### Post by aguilasainz on 2017-03-09
Hi there.

I've been asked at work, to setup an ubuntu 12.04.5 machine and install gnuradio + gnuradio-dev, and some other packages for GSM audit. Anyway, the thing is that I have a recipe to install all needed packges, and almost all have to be installed from source, and that's the way for gnuradio 3.4.2, everything has been working like a charm, until I'm asked to install [B]gnuradio-dev.

[/B]The recipe I have is asking me to install that package using apt, but it is not included in the repositories. I just can't find the way to install it, because all the packages I've found are for newer Ubuntu versions (14+).

I've been searching for some hours for the source package of gnuradio-dev, but the only source I've found is for gnuradio.

To be honest, I'm a linux user since a lot of years ago, but I've been working always with updated distros and never handled this kind of problems. I don't know why people here want to use old specific versions, and the guy who could explain me is sick as hell and won't come to office in a little while :( 

Can anyone help me?
Thank you so much!

---

### Post by TheFu on 2017-03-09
12.04.5 support ends in a month. That means ZERO security patches. Zero help from these forums then.

I wouldn't install it at this point. 14.04 or 16.04 are what you want. Don't know if gnuradio works with any of them or not.  If they insist, I'd get the 12.04.5 install requirement in writing with a risk acceptance letter signed by an officer of the company.  Nobody under that level can accept this risk, IMHO.

---

### Post by aguilasainz on 2017-03-09
> **TheFu said:**
> 12.04.5 support ends in a month. That means ZERO security patches. Zero help from these forums then.

I wouldn't install it at this point. 14.04 or 16.04 are what you want. Don't know if gnuradio works with any of them or not.  If they insist, I'd get the 12.04.5 install requirement in writing with a risk acceptance letter signed by an officer of the company.  Nobody under that level can accept this risk, IMHO.


Definitely any 14.04 or newer version will solve my problems, I already asked another junior engineer who has been involved in the creation of the recipe, but he definitely doesn't know why has to be 12.04 and no any other distro (because I've installed on a virtual machine using Debian, didn't take me more that 2 hours to complete the installation).

Thank you for your replay TheFu.

---

### Post by TheFu on 2017-03-09
The only reason I can think of is they are trying to setup a honeypot to be hacked. **Definitely get the risk acceptance letter in writing AND signed BEFORE you do it.** Please learn from my mistakes as a younin'.  After the fact, everyone else will have selective memory and you'll be left with all the responsibility.  Sharing it with a junior person won't help.  

Plus it might get more people hired to do the devops stuff, if that is why a recipe is being followed instead of devops.  At this point, every organization with more than 20 system should be doin' the devops (even if it is a pirate operation).


IMHO.

---

### Post by aguilasainz on 2017-03-09
You are right, I'll start with the letter right now. And you are totally right, there should be someone else doing this work, it's not even part of my job (lol), but since they found out I use linux (because I asked permission to install openSUSE instead of windows in my work machine), they started to ask me some specific tasks.

I just realized I should write down that in the acceptance letter.

Thank you again.

---

### Post by TheFu on 2017-03-09
Well, you want to be helpful, flexible, and work on priorities for the entire company. But you want to make certain that higher ups know when risky behaviors are being requested. 

It is called a "Risk Acceptance Letter" - basically, someone who is authorized to accept the risks you spell out in the letter can sign it. In most corporations, that would be S-VP or above. In some, it is a corporate officer - so COO, CIO, CEO, CMO.  Usually, my boss was happy to help with the letter, but don't let them minimize the risks.
* Risks
* Short-Term Mitigation and Issues with each of those
* Long-Term Solution to completely remove the risks

If funding is needed to remove the risks, a rough amount should be included for the signature to include. That doesn't mean it will get any budget, of course.

If you still find that getting help here is needed, please use code tags and include the actual commands and **relevant parts** showing the issues.  I saw a gnuradio build wiki with some odd requirements about which BOOST libraries worked and which didn't. Seems they don't support all of them that are new than X.y.z, only highly specific versions.

---

### Post by DuckHook on 2017-03-09
Not technical support request so *thread moved to **The Cafe** as the more appropriate forum.*

Though not strictly technical, some excellent career and HR advice here from TheFu.

---

