---
title: "Browser security"
date: 2010-05-02
forum: Security
---

### Post by Bear number one on 2010-05-02
I've been reading a few concerns about cross platform applications and linux security just lately, in fact it seems to be becoming a subject of some interest.  One of main topics appears to be browser vulnerability and I was wondering how different browsers compare security wise on linux.

Would a linux only browser be safer than, for instance, firefox, or when a cross platform browser is used on a linux system is it less vulnerable to attack than when on windows?
Are extensions such as no script and adblock necessary security tools on the linux platform and, indeed, can they be trusted?  After all the browser is the window to the world wide web and, as such, should be placed at a high level in the security hierarchy.
Thoughts and experiences appreciated.

---

### Post by Rubi1200 on 2010-05-02
Hi,
I have seen a lot of users mention using the Firefox extension NoScript.
You may also want to read the sticky about AppArmor. Although it is disabled by default in 9.10 (do not know about 10.4) it can be easily enabled and configured for personal needs.

---

### Post by uRock on 2010-05-02
Firefox and Chrome in Linux is very safe. The ploys being used by attackers only work on Windows systems. It does help to use the AppArmor as an extra bit of protection.

---

### Post by lovinglinux on 2010-05-02
NoScript is awesome. See other security/Privacy extensions [here](https://addons.mozilla.org/en-US/firefox/collection/securityandprivacy).

---

### Post by olive.ewe on 2010-05-03
noscript is awesome, even worth the relatively minor hassle of whitelisting each safe site you may regularly visit. its not just good for security but can also speed browsing up with its automatic blocking of crap like flash advertising or some other forums I visit where users post numerous flash videos which all slow page load (just either click individual videos as you wish or whitelist them all). 
WOT (web of trust) is another I like since it gives a damn good site rating easily seen by the colour of the icon in your browser (greeen orange, red) and when hitting a site with a poor red rating the page is blocked by a page giving a warning and link to the reason why. it even adds the rating symbols to google searches (just try a search for something like free screensavers and you'll see :P)
Cookiesafe, Ghostery (blocks web bugs) and Better Privacy (gets rid of flash super cookies) are some of the others I also have in Firefox

---

### Post by Bear number one on 2010-05-03
Firefox seems popular as ever and the extensions seem well thought of and trusted.  I will definitely check out apparmor thanks.  Does anyone actually use linux only browsers with the intention that they should be more secure, i:e as a completely linux only system?

---

### Post by lovinglinux on 2010-05-03
> **Bear number one said:**
> Firefox seems popular as ever and the extensions seem well thought of and trusted.  I will definitely check out apparmor thanks.  Does anyone actually use linux only browsers with the intention that they should be more secure, i:e as a completely linux only system?

I'm not an expert on the subject, but I don't think there is any difference if you run a browser that is developed to run only on Linux and another one that has a Linux version. Firefox and Chromium have both Linux versions. Is not like they have been hacked to work in Linux. They run natively because they have been developed and compiled to work with Linux. 

Any browser has security flaws so if you are too worried, then perhaps you should use Chromium/Chromium, which runs most processes on a sandbox. Beware of extensions tho. Chrome/Chromium extensions do not get the same level scrutiny by the browser developers like Firefox does. In fact, the way Chrome/Chromium is designed, the extensions are safer then Firefox, because they have very limited access to your system. Nevertheless, what controls the access permissions is a file inside the extension that "says" what the extension can access. This is a pretty good concept, but since Chrome/Chromium extensions are not reviewed by the browser developers (i.e. Google), then someone could easily distribute a malicious extension with all the permissions it needs.

I personally prefer Firefox, since I use more than 50 extensions and like the level of customization it offers. Chrome will take some time to have an extension gallery like Firefox. Besides, Chrome doesn't even work for me.

---

### Post by wilee-nilee on 2010-05-03
> **olive.ewe said:**
> noscript is awesome, even worth the relatively minor hassle of whitelisting each safe site you may regularly visit. its not just good for security but can also speed browsing up with its automatic blocking of crap like flash advertising or some other forums I visit where users post numerous flash videos which all slow page load (just either click individual videos as you wish or whitelist them all). 
WOT (web of trust) is another I like since it gives a damn good site rating easily seen by the colour of the icon in your browser (greeen orange, red) and when hitting a site with a poor red rating the page is blocked by a page giving a warning and link to the reason why. it even adds the rating symbols to google searches (just try a search for something like free screensavers and you'll see :P)
Cookiesafe, Ghostery (blocks web bugs) and Better Privacy (gets rid of flash super cookies) are some of the others I also have in Firefox

I use all you mention but cookiesafe. noscript deposits page accept and re-block in the panel customize list I just put those in the top panel with some others that are provided by toolbar buttons. The accept doesn't just clear all but one at a time or with some algorithm that I have no clue of. cookie culler is another, but I have FF set to save for 1 day but clear everything on closing, and no 3rd party cookies, and I also use optimizegoogle,

---

### Post by Bear number one on 2010-05-03
Many thanks for the replies, I will be checking out apparmor and Chrome and taking a good look at the Firefox extensions.

I may also make a similar post in the community forums regarding how many people use linux based browsers instead of cross platform.

Unfortunately I've forgotten how to mark this post resolved :confused: and can't find the 'button' for looking, can somebody help please??

---

### Post by Rubi1200 on 2010-05-03
Near the top right hand of the page you will see Thread Tools; you can mark the thread Solved from there.

---

### Post by Bear number one on 2010-05-04
Many thanks.

---

