---
title: "Does AppArmor make up for lack of Chromium updates?"
date: 2016-06-28
forum: Security
---

### Post by soft22dvd3 on 2016-06-28
Chromium on Ubuntu gets security updates pretty slowly compared to Debian. I am wondering if enabling the default App Armor profile (apparmor-profile) for Chromium makes up for this. 

Which is more secure?
1. A frequently updated Chromium without app armor
2. Ubuntu's infrequently updated Chromium with Ubuntu's default App Armor profile (apparmor-profiles)

---

### Post by DuckHook on 2016-06-28
It may help to think of this in a different way.

Security is not an either/or proposition. This is unfortunately a mindset that the Windows antivirus industry has perpetrated: "Our AV is better than theirs!"

Rather, effective and proper security is a collection of complementary and layered tactics and practices that reinforce each other so that bad guys have to penetrate multiple safeguards at the same time before your data is truly at risk. Think of the process more like those multi-drug cocktails that defeat a bad disease because the bug would have to undergo three different simultaneous mutations in order to defeat the drug cocktail.

If you look at it that way, Chromium updates and Apparmor profiles aren't substitutes for each other. Instead, they address very different things and work *together* to harden your system. Updates patch known security holes because only what is known can be patched; but once patched, that hole is definitely*closed*. Apparmor, on the other hand, looks after zero-day exploits, preventing unknown processes from accessing parts of your system that a browser simply has no business accessing; it doesn't close any holes because it can't know what holes there are in advance&#8213;it just sandboxes the app from the get-go to limit any potential damage.

You can take this philosophy and continue to virtuously expand on it: *noscript* prevents *any* scripts from running (unless you consciously whitelist it), cookie managers delete all tracking cookies at app shutdown, *WOT* warns you from accessing bad sites to start with, etc. None are "substitutes" for any other. They work in tandem to harden your browser layer by layer.

FWIW, the default Chromium apparmor profile is very loose. Some would say it's so loose as to be almost useless. I wouldn't go that far, but I can't blame the developers for permitting perhaps more than I would like: they have to account for the broadest possible use-cases or else users will complain when their Apparmor profile prevents them from running some video codec, for example. If you want a tighter apparmor profile, you will have to home-spin one yourself. Instructions [here]("https://help.ubuntu.com/community/AppArmor").

You may also find the following useful: while I have all of my browsers hardened eighteen ways to Sunday, I've taken the additional step of running "questionable" browser sessions inside a virtual machine. This is the ultimate sandboxing and makes it exponentially harder for malware to break out and infect the rest of my system. And by "questionable", I mean *any* site that I haven't visited before and of which I have an already very high confidence. These VM browsers are still hardened with all of the aforementioned tools.

One last note&#8213;the most important one of all&#8213;all of the above are just tactics. They do not replace good habits. The biggest security hole in any system is the dummy sitting at the keyboard (this is not meant to be pejorative&#8213;I include myself in that description). There is absolutely no app, alarm or process that can protect you from yourself. To cover off that hole, it all starts with cultivating good habits.

Since I've said all of this before, I'll just point you to [this old thread]("http://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795") instead of repeating myself.

For a wealth of further info on security, see the link in my sig: "Security Basics".

---

### Post by HermanAB on 2016-06-29
Also, the probability of getting infected with malware on a Linux system is extremely low. I have not had one of my machines compromised in more than a decade.  So the security stance of Ubuntu is pretty hard as is and adding something else, probably won't make a discernable difference, unless you are one of the extremely unlucky few that attract malware like Velcro...

---

### Post by haplorrhine on 2016-06-30
I believe the apparmor profiles get updated too, but you probably could update just the profiles with something like "apt-get update apparmor-profiles".  The same goes for your browser, but I don't know which will take longer.
You may have to reload the profiles into the kernel after updating them. The command is something like "sudo apparmor_parser -r /etc/apparmor.d/usr.bin.chromium-browser".  You can see the actual apparmor profile filename with "ls -l /etc/apparmor.d/".

---

### Post by uRock on 2016-06-30
I would drop Chromium and go for a more frequently updated browser. The browser is on the front line contacting tens or hundreds of browsers a minute when surfing the web. Of course that depends on what sites you are visiting, 

Open a terminal and run **netstat -at** while opening web pages. You'll see all of the connections that are being made. The browser is the first line of defense when connecting to those servers.

AppArmor profiles are awesome, but they may require tweaking. Visit this [thread]("http://ubuntuforums.org/showthread.php?t=1008906") for more info on AppArmor.

---

### Post by bashiergui on 2016-06-30
> Does $tool make up for lack of $app updates? Nope. Never does.

---

