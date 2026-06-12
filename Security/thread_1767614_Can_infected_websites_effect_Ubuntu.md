---
title: "Can infected websites effect Ubuntu?"
date: 2011-05-25
forum: Security
---

### Post by 0Io1 on 2011-05-25
Let's assume a website has a virus on it, or some kind of code for spyware.

Can the website effect Ubuntu? I mean from just visiting the website, no downloads or anything.

---

### Post by bodhi.zazen on 2011-05-26
> **0Io1 said:**
> Let's assume a website has a virus on it, or some kind of code for spyware.

Can the website effect Ubuntu? I mean from just visiting the website, no downloads or anything.

Short answer:

In theory, yes. In practice, not seen it.

Long answer: "effect Ubuntu" how ? If a site has malignant javascript, yes that can affect your browsing. If firefox is compromised it can access anything in home.

If the compromises leads to root access the system could be affected.

There are tons of vulnerabilities for say firefox listed here:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Be aware that those are potential vulnerabilities and theoretical problems. An exploit would then need to be designed to take advantage of such a vulnerability.

---

### Post by Drenriza on 2011-05-26
Ubuntu desktop has less Them 3 procent of the global market, unless things seriusly changed since last time. So you are As a victim not a prioteri using ubuntu.

---

### Post by 3rdalbum on 2011-05-26
> **0Io1 said:**
> Let's assume a website has a virus on it, or some kind of code for spyware.

Can the website effect Ubuntu? I mean from just visiting the website, no downloads or anything.

If the website can take advantage of a security problem in Firefox, then yes, the Firefox program could be made to do anything that your user account can do. Possibly. It's not as easy to perform this on Ubuntu as it is on Windows XP or Mac OS X due to Address Space Randomization.

Anyway, it's highly unlikely that any exploitive websites will be able to insert the correct instructions for Linux, and if you keep your Firefox up-to-date with the Update Manager then you should be safe enough not to worry about it.

---

### Post by Telengard C64 on 2011-05-26
> **bodhi.zazen said:**
> Long answer: "effect Ubuntu" how ? If a site has malignant javascript, yes that can affect your browsing. If firefox is compromised it can access anything in home.

If the compromises leads to root access the system could be affected.

^ This.

As suggested, keep your system up to date. Using the [NoScript](http://noscript.net/) extension will help by blocking all scripts except the ones you choose to allow.

Another thing that should help is enabling the [AppArmor](https://help.ubuntu.com/community/AppArmor) profile for Firefox. That way even if a malicious script could take control of Firefox the damage is limited further.

---

### Post by Kinstonian on 2011-05-26
In addition to the possibility of your web browser being exploited, you also have to be concerned with 3rd party browser plugins which can include things such as; Flash, Java or PDF.

The reasons why are debatable, but most would probably agree that you're not at as much risk as if you're using Windows.  In addition, the risks can be further mitigated by things like; keeping up-to-date with all patches and using AppArmor or FF plugins like NoScript and WOT.

---

### Post by sammiev on 2011-05-26
Been using Linux for sometime now and I have a virus scanner as I share files between Linux and Windows. To date I have never found a virus yet but I also use Noscript with Adblock Plus on Firefox. GL :)

---

### Post by emiller12345 on 2011-05-26
> **bodhi.zazen said:**
> 
If firefox is compromised it can access anything in home.

is there a tighter form of the firefox apparmor profile that will deny access to most of the items in home?

---

### Post by bodhi.zazen on 2011-05-26
> **emiller12345 said:**
> is there a tighter form of the firefox apparmor profile that will deny access to most of the items in home?

You have to write your own.

You can use my profiles as templates if you wish:

[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

I have not maintained them is a while, but look at what I did with home ;)

---

### Post by SparTacux on 2011-05-26
> **bodhi.zazen said:**
> You have to write your own.

You can use my profiles as templates if you wish:

[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

I have not maintained them is a while, but look at what I did with home ;)

I'll have to have a look at that myself.

Do you have apparmor profiles for Evolution and Thunderbird as well. I've got a feeling these applications should be protected as well.

---

### Post by bodhi.zazen on 2011-05-26
> **SparTacux said:**
> I'll have to have a look at that myself.

Do you have apparmor profiles for Evolution and Thunderbird as well. I've got a feeling these applications should be protected as well.

I have one for thunderbird.

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.lib.thunderbird.thunderbird](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.lib.thunderbird.thunderbird)

---

