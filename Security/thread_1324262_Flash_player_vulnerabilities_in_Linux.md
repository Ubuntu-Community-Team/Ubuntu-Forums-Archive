---
title: "Flash player vulnerabilities in Linux"
date: 2009-11-12
forum: Security
---

### Post by Jim_in_Germany on 2009-11-12
Hi,
As a former Windows user I was always hearing about newly discovered vulnerabilities in Adobe's Flash Player and that in the worst case scenario, just visiting the wrong website could be enough to compromise your computer.
My question: is Linux also affected by such vulnerabilities?
For example Adobe issued an update to its Shockwave Player today, claiming that all versions prior to 11.5.2.602 were vulnerable to attack.
I'm running a 64 bit Karmic and a quick peek in FireFox about: plugins reveals that I have "Shockwave Flash 10.0 r32" installed.
I believe this is the newest version, but would be interested to hear other people's thoughts on this subject.

---

### Post by Pjotr123 on 2009-11-12
Generally, Linux needs security updates just as much as other operating systems. In this particular case however, we needn't be worried: the security gaps are only in Adobe Shockwave Player, not in Adobe Flash Player. There is even no Adobe Shockwave Player for Linux available...

It's unfortunate that Firefox creates unnecessary confusion: it calls the Flash Player "Shockwave Player", which it most definitely isn't. I don't know why Firefox does this; an oversight from Mozilla?

Zum Schluss: keine Sorgen, es ist in Ordnung. :)

---

### Post by Jim_in_Germany on 2009-11-12
Hi,
danke für die Antwort :)
And thanks for the tip that Mozilla calls the Flash Player "Shockwave player".
Would it be fair to say that one should keep an eye on the latest release of the Flash Player for Linux (in my case the 64 bit version) and update it whenever Abode issues an update for this platform?

---

### Post by cariboo on 2009-11-12
Adobe doesn't seem to update the Flash player very often. You may want to install the 64-bit alpha version available [here]("http://labs.adobe.com/downloads/flashplayer10.html"), it may be a bit newer.

---

### Post by Pjotr123 on 2009-11-12
> **cariboo907 said:**
> Adobe doesn't seem to update the Flash player very often. You may want to install the 64-bit alpha version available [here]("http://labs.adobe.com/downloads/flashplayer10.html"), it may be a bit newer.

I'm not sure if that's a good idea... alpha versions are highly unstable. 

I'd simply stick with the current stable version. It's supposed to be secure.

---

### Post by XCan on 2009-11-12
If the OP is using 64-bit version of Ubuntu, I think he should use the 64-bit version. Stability wise, it has been absolutely more stable than the 32-bit through the wrapper.

---

### Post by rookcifer on 2009-11-12
> **Jim_in_Germany said:**
> Hi,
As a former Windows user I was always hearing about newly discovered vulnerabilities in Adobe's Flash Player and that in the worst case scenario, just visiting the wrong website could be enough to compromise your computer.

This wont happen in Linux because Firefox (and Flash) run with the limited privileges of the user.  With Windows, most people run with escalated privileges at all times, which is why "drive-by-downloads" are usually successful.

But, generally, if there is a vulnerability in Flash, it will affect all OS's the same way -- it's just that some OS's will be more resistant than others in relation to how much damage can be done.  On Linux (and all the *nixes) generally the most that can be done is a compromised user account.  This is serious but certainly not as serious as getting the whole machine pwned.  An easy way to avoid this is to run Noscript or use the Firefox AppArmor profile.

---

### Post by Jim_in_Germany on 2009-11-13
> This wont happen in Linux because Firefox (and Flash) run with the limited privileges of the user.
Isn't it the case though, that by causing a buffer overflow (for example), malicious code can gain elevated privileges, regardless in what kind of account it is running?
Or is this not possible in Linux?

> An easy way to avoid this is to run NoscriptHave been doing this for years. Couldn't be without it nowadays!

> or use the Firefox AppArmor profile.Didn't know about this. Thanks. I will enable the default profile that ships with Karmic.

---

### Post by rookcifer on 2009-11-16
> **Jim_in_Germany said:**
> Isn't it the case though, that by causing a buffer overflow (for example), malicious code can gain elevated privileges, regardless in what kind of account it is running?
Or is this not possible in Linux?

Yes, it can happen in Linux, but I have never heard of any in the wild attack doing this via a browser exploit.  And, again, you can mitigate this threat by utilizing a MAC like AppArmor (which comes installed with Ubuntu, all you need to do is activate the Firefox profile).  Basically a MAC is a whitelisting approach to security, which means you deny a program access to everything except the behavior you know is safe.

---

### Post by rpaco on 2010-06-12
> **Jim_in_Germany said:**
> Hi,
As a former Windows user I was always hearing about newly discovered vulnerabilities in Adobe's Flash Player and that in the worst case scenario, just visiting the wrong website could be enough to compromise your computer.
My question: is Linux also affected by such vulnerabilities?
For example Adobe issued an update to its Shockwave Player today, claiming that all versions prior to 11.5.2.602 were vulnerable to attack.
I'm running a 64 bit Karmic and a quick peek in FireFox about: plugins reveals that I have &quot;Shockwave Flash 10.0 r32&quot; installed.
I believe this is the newest version, but would be interested to hear other people's thoughts on this subject.

 I also have Shockwave Flash 10.0 r32 and got the virus this morning. I was also running Adbock and noscript. I am just about back to normal now. I am running Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9. ....I did try Lucid 10.4 but had too many problems with it and reverted to Karmic.  Where is there a .deb version of flash 10.1 to be had??

---

### Post by rookcifer on 2010-06-12
> **rpaco said:**
> I also have Shockwave Flash 10.0 r32 and got the virus this morning. I was also running Adbock and noscript. I am just about back to normal now. I am running Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.1.9) Gecko/20100401 Ubuntu/9.10 (karmic) Firefox/3.5.9. ....I did try Lucid 10.4 but had too many problems with it and reverted to Karmic.  Where is there a .deb version of flash 10.1 to be had??

Extraordinary claims require extraordinary evidence.  Provide proof that your Ubuntu box "got a virus" because of this Flash vuln.

---

### Post by bodhi.zazen on 2010-06-13
Just to make a more general point ....

All OS have vulnerabilities and your browser is a weak link in more then just Flash.

See:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Search that page for all the instances of firefox or xulrunner.

So while flash may be the most recent one to "hit the press" and has received a bit of hype ...

The take home message should be:

1. We should all be more security conscious. Too many people intstall linux and neglect security. See the security sticky to get you started.

2. You should secure your browser.

See: [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

3. Keep in mind these are potential vulnerabilities. Let's not feed the paranoia. I have not yet seen a credible report of a Linux system compromise with this vulnerability. Does not mean it is not out there, just that I have not seen it yet.

4. I suggest you look at Apparmor. Personally I use apparmor to restrict access to my home directory. Regular permissions are sufficient for system files, but there is not reason firefox needs access to .bashrc ...

5. Do not browse to shady web sites.

---

### Post by ddrichardson on 2010-06-13
> **cariboo907 said:**
> Adobe doesn't seem to update the Flash player very often. You may want to install the 64-bit alpha version available [here]("http://labs.adobe.com/downloads/flashplayer10.html"), it may be a bit newer.

I thought they'd [given up]("http://labs.adobe.com/technologies/flashplayer10/64bit.html") on 64bit Flash 10.1?

---

### Post by bodhi.zazen on 2010-06-13
I do not interpret that information the same way.

> We are fully committed to bringing native 64-bit Flash Player for the  desktop by providing native support for Windows, Macintosh, and Linux  64-bit platforms in an upcoming major release of Flash Player.

IMO, they have security issues and they need to take a deeper look (it seems there is not a quick fix). Although there is not an easy solution they are affirming their intent to support Linux, so we will have to wait for a fix.

---

### Post by cariboo on 2010-06-13
> **ddrichardson said:**
> I thought they'd [given up]("http://labs.adobe.com/technologies/flashplayer10/64bit.html") on 64bit Flash 10.1?

This thread was started in Nov. 09, Things have changed since then.

---

### Post by ddrichardson on 2010-06-13
> **cariboo907 said:**
> This thread was started in Nov. 09, Things have changed since then.
Sorry, I've been away since last November, it's all catch up for me.

---

### Post by ddrichardson on 2010-06-13
> **bodhi.zazen said:**
> I do not interpret that information the same way.



IMO, they have security issues and they need to take a deeper look (it seems there is not a quick fix). Although there is not an easy solution they are affirming their intent to support Linux, so we will have to wait for a fix.
The rest of that line reads "in an upcoming major release of Flash Player", so does that not mean that 10.1 has gone?

---

### Post by bodhi.zazen on 2010-06-13
> **ddrichardson said:**
> The rest of that line reads "in an upcoming major release of Flash Player", so does that not mean that 10.1 has gone?

I do not know what they mean by that statement. Your post made it sound as if they had no further intention to support linux.

---

