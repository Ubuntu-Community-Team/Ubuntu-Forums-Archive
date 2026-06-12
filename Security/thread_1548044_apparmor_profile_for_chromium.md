---
title: "apparmor profile for chromium"
date: 2010-08-07
forum: Security
---

### Post by egrpioneer on 2010-08-07
Please tell me how, and thank you in advance for assistance.

---

### Post by clrg on 2010-08-08
<removed>

---

### Post by egrpioneer on 2010-08-08
If you had read the manual, perhaps you would have had the knowledge and inclination to answer the question! Who rattled your cage today?

---

### Post by ks07 on 2010-08-08
> **clrg said:**
> Rtfm (©)
Anybody else see the irony in that? 

---

Anyway, the apparmor repo seems to be down, so I can't see if there's a pre-made profile for chromium anyway. However, a search turned up [this]("http://articles.techrepublic.com.com/5100-10878_11-6104800.html"). Use ```
genprof /usr/bin/chromium-browser
``` and then follow the guide as it says for firefox. Remember to do everything you would normally do with it, i.e. download files, use plugins like flash, etc. or you may end up blocking those actions in the future! :p Also, check out [the ubuntu wiki page]("https://help.ubuntu.com/community/AppArmor"), which you may find helpful, as well as ```
man genprof
``` in a terminal.

---

### Post by egrpioneer on 2010-08-08
Thanks for your assistance. It is appreciated!!!

---

### Post by bodhi.zazen on 2010-08-08
> **egrpioneer said:**
> Please tell me how, and thank you in advance for assistance.

If you are unfamiliar with apparmor, I suggest you read the apparmor sticky as an introduction.

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

Chromium was an unusual profile and, IMO, browsers are hard to start with.

I have a profile here:

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.lib.chromium-browser.chromium-browser](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.lib.chromium-browser.chromium-browser)

More likely then not you may need to make some modifications depending on your browsing habits, but that should be a start.

---

### Post by ks07 on 2010-08-08
> **bodhi.zazen said:**
> If you are unfamiliar with apparmor, I suggest you read the apparmor sticky as an introduction.

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

Chromium was an unusual profile and, IMO, browsers are hard to start with.

I have a profile here:

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.lib.chromium-browser.chromium-browser](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.lib.chromium-browser.chromium-browser)

More likely then not you may need to make some modifications depending on your browsing habits, but that should be a start.
Just an aside, but I can't access the profile link. Getting a connection timeout error. :( EDIT: Nvm, seems to be a problem on my end, can see the site when viewed through a http proxy. :sigh:

---

### Post by bodhi.zazen on 2010-08-08
> **ks07 said:**
> Just an aside, but I can't access the profile link. Getting a connection timeout error. :( EDIT: Nvm, seems to be a problem on my end, can see the site when viewed through a http proxy. :sigh:

LOL

Post back if you need further assistance, honestly I have not looked at that profile for some time now. It was working when I last updated it ;)

---

### Post by egrpioneer on 2010-08-08
> **bodhi.zazen said:**
> If you are unfamiliar with apparmor, I suggest you read the apparmor sticky as an introduction.

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

Chromium was an unusual profile and, IMO, browsers are hard to start with.

I have a profile here:

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.lib.chromium-browser.chromium-browser](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.lib.chromium-browser.chromium-browser)

More likely then not you may need to make some modifications depending on your browsing habits, but that should be a start.
I appreciate your help and guidance!!!

---

