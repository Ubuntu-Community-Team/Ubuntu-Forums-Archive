---
title: "Is Firefox NoScript Add-on useful??"
date: 2009-12-27
forum: Security
---

### Post by PepeLapiu on 2009-12-27
Hey, I'm configuring Firefox right now and wondering if there is any use to install the [No-Script Firefox add-on]("https://addons.mozilla.org/en-US/firefox/addon/722"). 

Can running script pose any danger to my security/privacy when using Ubuntu?

If not, what are the benefits of using such an add-on?

Thanx,
PepeLapiu :)

---

### Post by rookcifer on 2009-12-27
Theoretically scripts can have a negative effect on a Linux box.  However, there are numerous obstacles malicious scripts have to overcome in Linux:

1) People don't run Linux boxes as root, whereas most people run as admin in Windows.  This makes cracking Windows boxes easier than taking candy from a baby.

2) Scripts won't be able to initiate a download and then execute on a Linux box by default because the default umask wont allow it. (See caveat below)

3) Very few scripts are written to exploit Linux (security by obscurity -- though this is not the only reason linux is more secure).

Caveat: Now, it is indeed possible that a script could exploit a browser vulnerability (which would overcome any unmask setting and allow it to execute without user interaction).  To mitigate this, you can:

1) Update the browser when prompted

2) Use AppArmor 

As you will learn, NoScript is a pain to use and it's very annoying to whitelist everything.  Enabling the AppArmor profile is a better and more secure solution.

Bottom line: I would say as long as you keep the browser up to date your chances of falling victim to a malicious script on a Linux box is very slim.  For extra protection use AppArmor.

---

### Post by bodhi.zazen on 2009-12-27
You will get different opinions.

IMO  NoScript is easy to use and I would not browse without it =)

Malignant java scripts run corss platform and at a minimum I find flash and java popups annoying, so IMO it is nice to disable them as a part of adblock strategy.

From a security standpoint, as with all tools, apparmor included, you have to ask yourself are you paranoid enough to want to configure and use it ?

---

### Post by ratcheer on 2009-12-27
To me, NoScript is the most important FF add-on. I will not surf without it.

Tim

---

### Post by lovinglinux on 2009-12-27
I agree with bodhi.zazen, NoScript is easy and I wouldn't browse without it. Apparmor is a superb security tool, but setting up a Firefox apparmor profile for my needs was way too much complicated.

---

### Post by Soul-Sing on 2009-12-27
: [http://arstechnica.com/open-source/news/2009/05/mozilla-ponders-policy-change-after-firefox-extension-battle.ars](http://arstechnica.com/open-source/news/2009/05/mozilla-ponders-policy-change-after-firefox-extension-battle.ars)

quote:
> The conflict is over, but it raises a lot of really tough questions about the implications of the extension system and whether developers can be trusted with the level of access to the program's internals that it affords them. [COLOR="Red"]As always, users need to exercise caution and be mindful of how deep extensions can reach[/COLOR] into their browsing experience.

---

### Post by bodhi.zazen on 2009-12-27
Partially because of this, and partially because I support multiple users on a LAN, I have recently replaced Adblock with a proxy server. Privoxy if nice, as is bfilter, or even squid.

It *may* be a bit of an over kill for a single user, but it is easier to manage then individual FF extensions across multiple users on multiple boxes.

For a single user, I have been pleased with the results of privoxy + Noscript.

bfilter will import the Adblock list, but is no longer in the ubuntu repositories.

Squid is nice with multiple users across multiple workstations, several options w/ squid =)

So "essential" ff extensions are now Privoxy, Noscript, and Customize google.

Sure, not everyone wants to run a proxy, and it brings up another can of worms, but it may be a viable alternate for some =)

---

### Post by PepeLapiu on 2009-12-27
Well, thanx all for your replies. I have used No-Script for years with windoze and I wouldn't leave home without it, ever, while using windoze. But now that I do use Linux I'm not sure if it's required. rookcifer made a good point that it's not AS important with Linux as it would be with windoze. I'm still on the fence here.

But an other aspect is speed and bandwith: I was told that No-Script could very well speed up browsing by not downloading script. So maybe you guys can confirm that. Does No-Script stop script from being doownloaded? Or does it download it and not run it until I let it?

---

### Post by azar555 on 2010-01-04
This is a reliable and secured addon for your web browser. Therefore, you can allow your active content to run only from trusted sites and you can protect yourself against XSS and Click Jacking attacks. Moreover, this is the winner of &#8220;2006 PC World Class Award&#8221; as this is able to provide extra protection for your Firefox. At the same time, it is able to allow JavaScript, Java and other executable content to run only from trusted domains of your choice.
________________________________________
[cuba holidays](http://www.bestatcubaholidays.co.uk/)
[cricket](http://www.thecricfanclub.com)

---

### Post by nanotube on 2010-01-04
fwiw, i use it on my firefox. :)

---

### Post by Jimtheplanner on 2010-01-05
Most of the time I tend to use Mandriva 2010, adjusting the superb MSEC settings to suit my needs. Even with this level of security I still use "No Script" on Firefox.

Jim

---

