---
title: "AppArmor v plug-in"
date: 2012-11-10
forum: Security
---

### Post by mike acker on 2012-11-10
at times i've pondered the question: to what extent are the attackers compromising the browser -- rather than the o/s -- to work their trade?

It would appear the answer is "yep" [ according to article pub in Info Week Nov 7 ]("http://www.informationweek.com/security/attacks/malware-tools-get-smarter-to-nab-financi/240062579")

there was this
> 
If you've got $3,931 burning a hole in your pocket, speak Russian, and want to invest in a crimeware toolkit, you're in luck.  That's the price for the latest version of the Citadel malware,  code-named Rain Edition (1.3.5.1), which includes all of the latest  malware mod cons: advanced Firefox and Chrome data-stealing plug-ins,  advanced [Web injection techniques]("http://www.informationweek.com/security/attacks/fast-flux-botnet-nets-fraudsters-78-mill/240009729")  to modify code on targeted websites, and easier updating for Trojan  files that have been used to infect PCs. The malware also sports an  easy-to-use, browser-based interface for running the [command-and-control (C&C) infrastructure]("http://www.informationweek.com/security/attacks/online-criminals-best-friends-malnets/240008264") that sends instructions to infected PCs in the botnet -- and retrieves stolen data -- as well as infection analytics.  
the question here is: to what extent does/can AppArmor prevent  un-authorized modifications to Firefox or Chrome ?

I'm running the Firefox Profile by Jamie Strandboge of Canonical now.

My question is: does this prevent addition of un-authorized plug-ins and if so should i know how to check this in the profile ?

we would need to know -- what components would the hacker need to modify to add an un-authorized plug-in and -- how to we deny access in the AppArmor profile to prevent this

---

### Post by Soul-Sing on 2012-11-10
> My question is: does this prevent addition of un-authorized plug-ins and if so should i know how to check this in the profile ?

Thats a nice one. Afaik Ubuntu supports some add-ons, but I am not sure. So they (ubuntu supported) are safe to use. There were in the past some incidents with the devs of adblock and no-script: [http://hackademix.net/2009/05/04/dear-adblock-plus-and-noscript-users-dear-mozilla-community/](http://hackademix.net/2009/05/04/dear-adblock-plus-and-noscript-users-dear-mozilla-community/) but the was an incident. The overall review of these add ons are outstanding. Watch the community reviews of add-ons here and on the firefox add-on page.
Strandboge comes with default great profiles for firefox, and other apps, you should be fine with them.
Only some extentions you should disable in your browser: java. It is very vulnerable software.

---

### Post by OpSecShellshock on 2012-11-10
It might be somewhat tricky using AppArmor to prevent extension or plug-in installation, because in order to be used for some of its intended purposes (like installing extensions you actually want to install) Firefox needs to be able to write to the directories and files that I would imagine malicious extensions would also use. I think plug-ins are a somewhat different story than extensions, because they tend to be installed as separate applications that just have components which can be called by the browser. As long as the browser is confined in such a way that it can't write to any places those would go, I wouldn't think that was as much of a risk.

---

### Post by Hungry Man on 2012-11-10
The browser and its plugins have long been the primary source for users infections - either through Adobe Flash/Reader plugins, Java, or the browser itself.

Apparmor can do a few things:
1) An attacker may try to write a file and then map it to memory to perform ROP depending on how far along in the attack they are. If they can't write/ mmap the file this will fail.

2) An attacker may try to execute a payload. They can't write the payload, they can't execute a payload, this attack fails.

3) An advanced attacker may run commands from shell. Access to commands is restricted (as access to the files would be restricted) and those commands allowed are either inherited into the profile or set into child profiles, restricting the attacker.

An attacker who wants to monetize a system after compromising an apparmor'd browser has a few options:

1) They already have network access. If they can read the files they want from the browser sandbox they can send the info back to themselves from shell. They can also change specific Firefox files to try to install a malicious extension - this depends on how locked down your profile is.

2) If they can't monetize from within the sandbox they can break out of it either through flaws in the profile (Px, Cx, Ux all can lead to escalation) or by using a local kernel exploit.

2a) Local kernel exploits can be difficult from within a sandbox as there's limited visual attack surface.

---

### Post by maglinu on 2012-11-10
My noob solution to this problem is to use a separate limited rights user account in which the browser has no extensions/ plug-ins, and in which all browsing data is cleared on each exit, for any sensitive web transactions.

I don't know how effective it is, but it makes me feel better.

---

### Post by mike acker on 2012-11-10
> **OpSecShellshock said:**
> It might be somewhat tricky using AppArmor to prevent extension or plug-in installation, because in order to be used for some of its intended purposes (like installing extensions you actually want to install) Firefox needs to be able to write to the directories and files that I would imagine malicious extensions would also use. I think plug-ins are a somewhat different story than extensions, because they tend to be installed as separate applications that just have components which can be called by the browser. As long as the browser is confined in such a way that it can't write to any places those would go, I wouldn't think that was as much of a risk.

this is a Good Point.

the answer is: I would simply put the profile in COMPLAIN mode, install my plug-in or add on or whatever and then put the profile back to enforce mode.

---

