---
title: "Is Noscript really necessary?"
date: 2018-01-11
forum: Security
---

### Post by linuxyogi on 2018-01-11
Is Noscript really necessary if Firefox is already inside a firejail sandbox ?

---

### Post by QIII on 2018-01-11
Security measures are best deployed in depth.

I still run NoScript in sandboxed VMs.

---

### Post by linuxyogi on 2018-01-11
I am using 57.0.1 (64-bit) Quantam. I had installed Noscript for a brief period.
I found that the settings have changed. I mean there is no settings for ABE which was there before it changed 
to web extensions. Overall this version which is compatible with FF 57 lacks many features 
and its comparatively difficult to configure.

---

### Post by vasa1 on 2018-01-11
> Is Noscript really necessary?is subjective. Some can't live without it. Some don't use it.

There's a NoScript 10 thread at Wilders': [https://www.wilderssecurity.com/threads/noscript-10.397945/](https://www.wilderssecurity.com/threads/noscript-10.397945/) mostly Windows users, but you may some help/advice/opinions there as well.

---

### Post by linuxyogi on 2018-01-11
> **vasa1 said:**
> is subjective. Some can't live without it. Some don't use it.

There's a NoScript 10 thread at Wilders': [https://www.wilderssecurity.com/threads/noscript-10.397945/](https://www.wilderssecurity.com/threads/noscript-10.397945/) mostly Windows users, but you may some help/advice/opinions there as well.

I read that link. Sadly the features of the present Noscript version is quite limitied.

I miss the good old Noscript. :(

---

### Post by vasa1 on 2018-01-11
Even the AdBlock Plus guy seems to have found web extensions a struggle: [https://palant.de/2017/12/20/taking-a-break-from-adblock-plus-development](https://palant.de/2017/12/20/taking-a-break-from-adblock-plus-development)

---

### Post by linuxyogi on 2018-01-11
> **vasa1 said:**
> Even the AdBlock Plus guy seems to have found web extensions a struggle: [https://palant.de/2017/12/20/taking-a-break-from-adblock-plus-development](https://palant.de/2017/12/20/taking-a-break-from-adblock-plus-development)

Fortunately I don't use AdBlock Plus. I use 

Ublock Origin.
Ghostery 
SelfDestroyingCookies

---

### Post by &amp;KyT$0P# on 2018-01-11
> **linuxyogi said:**
> Is Noscript really necessary if Firefox is already inside a firejail sandbox ?
Yes (but see below).  They are two totally different protections.  NoScript protects your browser from Web-based threats.  Firejail protects your computer from your Web browser.

Firejail alone will not stop a malicious website from performing a XSS attack and stealing your bank credentials.

> **linuxyogi said:**
> I am using 57.0.1 (64-bit) Quantam. I had installed Noscript for a brief period.
I found that the settings have changed. I mean there is no settings for ABE which was there before it changed 
to web extensions. Overall this version which is compatible with FF 57 lacks many features 
and its comparatively difficult to configure.
NoScript for Quantum is still missing many features compared to NoScript "Classic".  In its current form, I don't see any big advantage of NoScript for Quantum over other script blockers.

So if you don't like NoScript for Quantum, and if you need to use Firefox 57, you could just go with a different script blocker for now.

Or...
> **linuxyogi said:**
> I miss the good old Noscript. :(
... if you can use one of Firefox 52 ESR, SeaMonkey, Pale Moon, or Waterfox, notice that [NoScript "Classic" is not dead yet]("https://noscript.net/getit").

---

### Post by linuxyogi on 2018-01-11
> **halogen2 said:**
>  Firejail alone will not stop a malicious website from performing a XSS attack and stealing your bank credentials. 
When I log in to my bank's account I always start Firefox with 

```
firejail --private firefox 
```

so its starts with a fresh profile without any addons. Do you think this is risky instead of secure ?


> **halogen2 said:**
>  So if you don't like NoScript for Quantum, and if you need to use  Firefox 57, you could just go with a different script blocker for now. 

I have installed NoScript I will cope with the lack of features

---

### Post by &amp;KyT$0P# on 2018-01-11
> **linuxyogi said:**
> When I log in to my bank's account I always start Firefox with 

```
firejail --private firefox 
```

so its starts with a fresh profile without any addons. Do you think this is risky instead of secure ?
Even if you visit **only** your banking site in that session, I would say yes.

1) Using an isolated browser session for banking is a good idea.  Unfortunately for you, you can't "really" have an isolated browser session in a clean Firefox profile.  Because Firefox's new tab page makes a lot of outgoing requests by default.  And the new tab page is what opens by default in a clean Firefox profile.
I just tested a clean profile of Firefox 57 while running Wireshark, and I saw (among others) googletagmanager, Facebook, Twitter, Reddit, Youtube, Amazon, and "getpocket".  The connections are encrypted, so I can't tell what any of the connections actually are, but it doesn't look good for your usage.
* Upon further inspection, looks like some of the connections I listed might just be DNS prefetching.  And googletagmanager appears to be coming from the Mozilla site that loads on first startup of a new profile, not from the New Tab page.

2) There's also stuff like [this]("https://ubuntuforums.org/showthread.php?t=2380114").  Script blockers won't help you there.  You need a [user.js file]("http://kb.mozillazine.org/User.js_file") to defend against this.
```
user_pref("app.shield.optoutstudies.enabled", false);
user_pref("datareporting.healthreport.uploadEnabled", false);
```

---

### Post by linuxyogi on 2018-01-11
> **halogen2 said:**
> Even if you visit **only** your banking site in that session, I would say yes.

1) Using an isolated browser session for banking is a good idea.  Unfortunately for you, you can't "really" have an isolated browser session in a clean Firefox profile.  Because Firefox's new tab page makes a lot of outgoing requests by default.  And the new tab page is what opens by default in a clean Firefox profile.
I just tested a clean profile of Firefox 57 while running Wireshark, and I saw (among others) googletagmanager, Facebook, Twitter, Reddit, Youtube, Amazon, and "getpocket".  The packets are encrypted, so I can't tell what any of the connections actually are, but it doesn't look good for your usage.

2) There's also stuff like [this]("https://ubuntuforums.org/showthread.php?t=2380114").  Script blockers won't help you there.  You need a [user.js file]("http://kb.mozillazine.org/User.js_file") to defend against this.
```
user_pref("app.shield.optoutstudies.enabled", false);
user_pref("datareporting.healthreport.uploadEnabled", false);
```

1) That's bad news. Do you do any Internet banking ? What  precautions do you take  ?

2) I have already disabled looking glass.

---

### Post by &amp;KyT$0P# on 2018-01-11
> **linuxyogi said:**
> 1) That's bad news. Do you do any Internet banking ? What  precautions do you take  ?
To disable the New Tab page from making those connections, just click the gear in the upper right and un-check everything.

I run Firefox like this -
```
firejail --overlay-tmpfs firefox
```
This lets you start with your existing profile while not writing to your home directory.  Since you're starting with an existing profile, you can disable in advance the stuff I mentioned, and thus get an actually isolated browser session in a firejail.

If you want/need a different profile for banking vs other use, you can [create a new profile]("http://kb.mozillazine.org/Profile_Manager"), then when you want to do banking you would run this -
```
firejail --overlay-tmpfs firefox -P <profilename>
```
replacing [FONT=Courier New]<profilename>[/FONT] with the name you gave your new banking-only profile.

Refer to [FONT=Courier New]man firejail[/FONT] for more info about [FONT=Courier New]--overlay-tmpfs[/FONT].

Hope this helps.

---

### Post by linuxyogi on 2018-01-12
> **halogen2 said:**
> To disable the New Tab page from making those connections, just click the gear in the upper right and un-check everything.

I run Firefox like this -
```
firejail --overlay-tmpfs firefox
```
This lets you start with your existing profile while not writing to your home directory.  Since you're starting with an existing profile, you can disable in advance the stuff I mentioned, and thus get an actually isolated browser session in a firejail.

If you want/need a different profile for banking vs other use, you can [create a new profile]("http://kb.mozillazine.org/Profile_Manager"), then when you want to do banking you would run this -
```
firejail --overlay-tmpfs firefox -P <profilename>
```
replacing [FONT=Courier New]<profilename>[/FONT] with the name you gave your new banking-only profile.

Refer to [FONT=Courier New]man firejail[/FONT] for more info about [FONT=Courier New]--overlay-tmpfs[/FONT].

Hope this helps.

I didn't find the gear icon ...Can you please give me a a screenshot ?

I just replaced the --private with --overlay-tmpfs firefox. Tested it by deleting a bookmark then  launching FF again to see the bookmark is not deleted.

---

### Post by &amp;KyT$0P# on 2018-01-12
> **linuxyogi said:**
> I didn't find the gear icon ...Can you please give me a a screenshot ?
[ATTACH=CONFIG]278157[/ATTACH]

---

### Post by linuxyogi on 2018-01-12
> **halogen2 said:**
> [ATTACH=CONFIG]278157[/ATTACH]

Done. Thanks.

---

### Post by &amp;KyT$0P# on 2018-01-12
You're welcome. :KS

For what it's worth, I looked more into the connections made by a new Firefox profile and updated [my post]("https://ubuntuforums.org/showthread.php?t=2382335&p=13729677&viewfull=1#post13729677").  It's not quite as bad as I first thought, but all my advice still applies.

---

### Post by TheFu on 2018-01-12
For online banking/broker stuff, I boot a LiveCD into a VM on a VM host. The ISO used is updated from time to time, but since it is a 55MB ISO, that is trivial.  Basically, it only has enough OS for a standard web browser to work with those sites. It lacks most of the common OS tools that can be abused.  This is like firejail --private, but since ISO files cannot be written from a running OS, it is easier, well tested, and has been around over a decade.  Before that, I would boot from a CD.

I'm a huge believer in having multiple security protections too.  An ISO running in a VM meets my needs and follows the recommendation of Brian Krebs.  [https://krebsonsecurity.com/online-banking-best-practices-for-businesses/](https://krebsonsecurity.com/online-banking-best-practices-for-businesses/) . 

Firejail is relatively new. There is the theory about it providing security compartments and there is the reality that only comes from time being attacked in the real world. As a CFO at a C-corp for years, being paranoid was important to ensure payroll and 401k money didn't get snagged by attackers. Corporate banking protections are much less than for individuals, legally. Also have used 2FA (nice little token) for the last 18 yrs with broker. 

When I know I don't want/need javascript or SSL/TLS connections, dillo is a nice, lite, browser.

---

### Post by linuxyogi on 2018-01-13
> **TheFu said:**
> For online banking/broker stuff, I boot a LiveCD into a VM on a VM host. The ISO used is updated from time to time, but since it is a 55MB ISO, that is trivial.  Basically, it only has enough OS for a standard web browser to work with those sites. It lacks most of the common OS tools that can be abused.  This is like firejail --private, but since ISO files cannot be written from a running OS, it is easier, well tested, and has been around over a decade.  Before that, I would boot from a CD.

I'm a huge believer in having multiple security protections too.  An ISO running in a VM meets my needs and follows the recommendation of Brian Krebs.  [https://krebsonsecurity.com/online-banking-best-practices-for-businesses/](https://krebsonsecurity.com/online-banking-best-practices-for-businesses/) . 

Firejail is relatively new. There is the theory about it providing security compartments and there is the reality that only comes from time being attacked in the real world. As a CFO at a C-corp for years, being paranoid was important to ensure payroll and 401k money didn't get snagged by attackers. Corporate banking protections are much less than for individuals, legally. Also have used 2FA (nice little token) for the last 18 yrs with broker. 

When I know I don't want/need javascript or SSL/TLS connections, dillo is a nice, lite, browser.

Keeping the ISO up to date is the challenge for me. Which distro(55MB)  do you use ? TinyCore ? Also  in absence of a shared clipboard (from host to guest) typing a 12 character complex password is a challenge.

---

### Post by TheFu on 2018-01-14
> **linuxyogi said:**
> Keeping the ISO up to date is the challenge for me. Which distro(55MB)  do you use ? TinyCore ? Also  in absence of a shared clipboard (from host to guest) typing a 12 character complex password is a challenge.

I automated the monthly download of a new ISO.  wget and cron.

Shared clipboards are a security failure.  Be careful.

12 character passwords aren't sufficient for any use IMHO. 20+ if the site allows.

---

