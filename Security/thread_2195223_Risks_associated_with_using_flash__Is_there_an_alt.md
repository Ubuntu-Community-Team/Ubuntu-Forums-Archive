---
title: "Risks associated with using flash | Is there an alternative ?"
date: 2013-12-23
forum: Security
---

### Post by linuxyogi on 2013-12-23
Hi,

I watched a video on youtube in which Richard Stallman was saying using flash is not a good idea. He mentioned flash amongst other things like malicious software, backdoors, etc.

 Coz RS is saying thing I am a bit worried. 

So what are the risks of using flash ?

Is there an alternative ?

---

### Post by Lars Noodén on 2013-12-23
I'm not sure about games, but the workaround for video is to use sites that show their video in actual video formats not wrapped in Flash.  Youtube for example now supports HTML5 for most videos.  The Flash wrapper is extraneous and only introduces incompatiblities and security holes and maybe some privacy issues.  

The security record for Flash is apparently on par with ActiveX.  Additionally, it has full access to your keyboard, microphone, camera, and other peripherals and lets the remote site do anything with them.  

Further, being a blob, there is no source code to allow it to be ported to other, better architectures.   Anything which promotes lock-in like that hurts.

---

### Post by linuxyogi on 2013-12-23
> **Lars Noodén said:**
> I'm not sure about games, but the workaround for video is to use sites that show their video in actual video formats not wrapped in Flash.  Youtube for example now supports HTML5 for most videos.  The Flash wrapper is extraneous and only introduces incompatiblities and security holes and maybe some privacy issues.  

The security record for Flash is apparently on par with ActiveX.  Additionally, it has full access to your keyboard, microphone, camera, and other peripherals and lets the remote site do anything with them.  

Further, being a blob, there is no source code to allow it to be ported to other, better architectures.   Anything which promotes lock-in like that hurts.

Problem is youtube offer HTML5 for newer videos only. 

I don't have camera or microphone but if the remote site has access to my keyboard thats a big issue. 

I don't really want to stay away from using flash coz its simply too inconvenient.

Do you think installing Xubuntu inside virtualbox and using the VM for flash related sites will minimize the risk ?

---

### Post by Lars Noodén on 2013-12-23
If you make a snapshot and launch from that clean snapshot each time, then it is unlikely that problems can accumulate.  Just be sure to use that clean snapshot before updating the vm's system.  

AppArmor might help there too.

---

### Post by Hungry Man on 2013-12-23
If you're worried about Flash security, use Chrome.

---

### Post by cariboo on 2013-12-23
> **Hungry Man said:**
> If you're worried about Flash security, use Chrome.

It may help, if you explain why you think that Google's version of flash is any more secure than the original.

---

### Post by linuxyogi on 2013-12-23
> **Lars Noodén said:**
> If you make a snapshot and launch from that clean snapshot each time, then it is unlikely that problems can accumulate.  Just be sure to use that clean snapshot before updating the vm's system.  

AppArmor might help there too.


You say this coz the flash plug in stores something on the computer ? If thats so please have a look at this addon

[https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/?src=search](https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/?src=search)

> Remove or manage a new and uncommon kind of cookies, better known as  LSO's.The BetterPrivacy safeguard offers various ways to handle  Flash-cookies set by Google, YouTube, Ebay and others...

---

### Post by Lars Noodén on 2013-12-23
> **linuxyogi said:**
> You say this coz the flash plug in stores something on the computer ? 

I say it because there's more than cookies that can go wrong with a Flash instance.  Using a clean snapshot reduces the probability that something was changed or added, cookies aside.  The add-on helps but only with cookies not the bazillion other problems.

---

### Post by Hungry Man on 2013-12-23
"It may help, if you explain why you think that Google's version of flash is any more secure than the original."It has no access to the file system and runs with seccomp mode 2 filters with virtually no access to system calls. An exploit in Flash in Chrome leads to no file access and a very hard time escaping the sandbox. Google also often pushes out Flash patches before Adobe does.

---

### Post by DuckHook on 2013-12-24
Here's what I do:

1. I use FF as my full-fledged browser, but only sparingly. When I do use it, it is fully hardened with Adblock Plus, a Cookie Manager, WOT, Better Privacy, and most importantly, NoScript. This last, stops *all* scripting dead in its tracks. Everything is defaulted to "deny". I only whitelist sites that I absolutely have to, like my banking sites. If anything else is permitted, it is one-time and temporary (see below). NoScript has the added advantage of prohibiting cross-site scripting and a few other tricks that scumbags use to crack browsers.

2. The majority of my browsing is conducted through Links2 in graphics mode. This is a hyper-light, primitive browser that is actually incapable of accepting/storing cookies or running any script including flash. Obviously, it can't show many sites in their full obese pigged-out glory, but I don't care, as I am after the content and not the eye/ear-candy.

3. For sites that simply will not load without flash, I make a decision: if I *must* access the site, then I fire up FF, temporarily permit it in NoScript and let it drop back to "deny" when I'm finished. In 95% of the cases, I decide that such a site is not important enough to risk permitting scripting to run and I take the attitude that if the designer cannot engage my interest without forcing his scripts down my throat, he doesn't deserve my viewership/patronage. Stated so baldly, it sounds rather arrogant I'm afraid, but I'm not trying to be arrogant; just safe.

I'm convinced that my browser will not be compromised so long as I adhere to these stringent rules.

They aren't for everyone, and even my wife won't put up with this level of paranoia. Her browser is structured far less stringently than mine, but I am convinced that hers is also far more vulnerable. And, to be honest, her surfing habits make me cringe anyway, so I'm not sure browser hardening would do much. In the end, by far the biggest risk factor is the user, and all of these tools are worthless if such users are intent on behaving like fools.

 You have to make your own decision on the basis of your risk tolerance, your perception of how bad things are out there and how hungry you are for eye/ear-candy.

**EDIT**

I failed to mention that I have an apparmor profile defined for FF and I actually turn it on (it comes off by default). Mine is not the canned profile, but a custom profile that I've trained. Unfortunately, this is a complicated process and far beyond the scope of this thread, but it is a critical component to contain any breakout which my prior steps may have failed to safeguard.

I take further steps too, but we risk getting lost in a general security discussion when what you want is a quick and simple set of suggestions to cover off the biggest holes in flash.

---

### Post by clearski on 2013-12-24
"NOTE: Adobe Flash Player 11.2 will be the last version to target Linux  as a supported platform. Adobe will continue to provide security  backports to Flash Player 11.2 for Linux." *(source:  [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/))*

The current version of Flash Player for Windows is 11.9. Do I understand correctly that Adobe does no longer support Flash for Linux?

---

### Post by cariboo on 2013-12-24
> **clearski said:**
> "NOTE: Adobe Flash Player 11.2 will be the last version to target Linux  as a supported platform. Adobe will continue to provide security  backports to Flash Player 11.2 for Linux." *(source:  [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/))*

The current version of Flash Player for Windows is 11.9. Do I understand correctly that Adobe does no longer support Flash for Linux?

You understand right, Adobe no longer develops flash for Linux. Mozilla and Google have come up with their own versions of flash.

---

### Post by linuxyogi on 2013-12-24
Created a VM > Cloned it > updated it .

But I am facing audio/video sync issues while playing flash videos.

> **Hungry Man said:**
> If you're worried about Flash security, use Chrome.

Chromium is open source but Google Chrome is not. So who knows whats written in there !

---

### Post by bashiergui on 2013-12-24
> **linuxyogi said:**
> Chromium is open source but Google Chrome is not. So who knows whats written in there !Have you reviewed all the source code for Chromium?

---

### Post by linuxyogi on 2013-12-24
> **bashiergui said:**
> Have you reviewed all the source code for Chromium?

No I haven't but if start suspecting even the open source projects then I will become uncomfortable with Ubuntu even.

After all these projects are maintained by large communities and I think its very unlikely (almost impossible) that a community that comprises of independent developers  will indulge in unethical practices. Even if someone does something wrong someone else will surely point it out.

---

### Post by monkeybrain20122 on 2013-12-24
> **cariboo907 said:**
> You understand right, Adobe no longer develops flash for Linux. Mozilla and Google have come up with their own versions of flash.

Mozilla?

---

### Post by bashiergui on 2013-12-24
Mozilla = Firefox

---

### Post by monkeybrain20122 on 2013-12-24
> **bashiergui said:**
> Mozilla = Firefox

When did firefox come up with its own version of flash?

---

### Post by bashiergui on 2013-12-25
I assume this is what Cariboo907 was referring to
[http://www.webdesignerdepot.com/2013/10/mozilla-takes-on-flash/](http://www.webdesignerdepot.com/2013/10/mozilla-takes-on-flash/)

---

### Post by Hungry Man on 2013-12-26
Adobe *does* support Flash on Linux, but only 12.2  for non-Chromium based browsers. It still gets security updates.Mozilla does not support Flash on its own, they are not patching it or anything like that. The patches are still from Adobe.

> Chromium is open source but Google Chrome is not. So who knows whats written in there !

Just about every part of Chrome is actually open source. The only parts that aren't are the PDF viewer and Flash.

---

### Post by cariboo on 2013-12-26
@Hungryman, I don't know where you are getting your information from, but according to [this]("http://www.adobe.com/software/flash/about/") page, the latest flash version for Linux is 11.2.202.332, and for Chrome it's 11.9.900.170

---

### Post by Hungry Man on 2013-12-26
Yes, that is true. I don't think I said otherwise?

Adobe supports Flash on Linux using NPAPI for 11.2. Mozilla does not support it itself. Chrome and Adobe jointly support PPAPI Flash.

---

