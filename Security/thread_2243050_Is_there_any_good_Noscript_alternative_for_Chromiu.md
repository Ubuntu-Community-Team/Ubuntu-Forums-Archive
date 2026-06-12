---
title: "Is there any good Noscript alternative for Chromium yet ?"
date: 2014-09-05
forum: Security
---

### Post by linuxyogi on 2014-09-05
Hi,

I have always used Firefox as my main browser but lately I am really impressed by Chromium's performance.

I searched the Google web store for Noscript alternatives but almost all of them have received pretty bad reviews.

But I am sure there must a lot of Chrome/Chromium users here. 

So have you managed to find a good script blocking extension for Chromium yet ? 

I dont expect it to be as good as Noscript but its better to have some layer of protection.

---

### Post by bcschmerker on 2014-09-06
The closest Extension to [InformAction® NoScript™](http://www.informaction.com/) that I have found for Chromium™ is [ScriptSafe™](https://chrome.google.com/webstore/detail/scriptsafe/oiigbmnaadbkfbmpbfijlflahbdbdgdf?hl=en), which has certain operational differences.  ScriptSafe acts more stringently concerning components of Web pages compared to NoScript™.

---

### Post by linuxyogi on 2014-09-06
Installed it. Seems pretty good. Thanks.

---

### Post by vasa1 on 2014-09-06
[http://www.wilderssecurity.com/threads/ublock-a-lean-and-fast-blocker.365273/](http://www.wilderssecurity.com/threads/ublock-a-lean-and-fast-blocker.365273/)

[https://chrome.google.com/webstore/detail/http-switchboard/mghdpehejfekicfjcdbfofhcmnjhgaag?hl=en-US](https://chrome.google.com/webstore/detail/http-switchboard/mghdpehejfekicfjcdbfofhcmnjhgaag?hl=en-US)

I don't use either and am not sure they're for Linux.

---

### Post by linuxyogi on 2014-09-06
> **vasa1 said:**
> [http://www.wilderssecurity.com/threads/ublock-a-lean-and-fast-blocker.365273/](http://www.wilderssecurity.com/threads/ublock-a-lean-and-fast-blocker.365273/)

[https://chrome.google.com/webstore/detail/http-switchboard/mghdpehejfekicfjcdbfofhcmnjhgaag?hl=en-US](https://chrome.google.com/webstore/detail/http-switchboard/mghdpehejfekicfjcdbfofhcmnjhgaag?hl=en-US)

I don't use either and am not sure they're for Linux.



Installed ublock. Its actually 3mb in size ! I thought it will cause major slow down. I tested by closing Chromium and starting it. There is a 

slight increase in load time but there is absolutely no increase in page loading time.

Thanks.

---

### Post by linuxyogi on 2014-09-06
> **vasa1 said:**
>  [https://chrome.google.com/webstore/detail/http-switchboard/mghdpehejfekicfjcdbfofhcmnjhgaag?hl=en-US](https://chrome.google.com/webstore/detail/http-switchboard/mghdpehejfekicfjcdbfofhcmnjhgaag?hl=en-US)


Sorry I missed that but since Scriptsafe is working pretty fine dont wanna install ^^ that. Frankly its too much detail to handle.

---

### Post by Hungry Man on 2014-09-08
What you want is HTTPSwitchBoard. You can ignore those details and just use it like NoScript. There is a setting for this

---

### Post by linuxyogi on 2014-09-09
> **Hungry Man said:**
> What you want is HTTPSwitchBoard. You can ignore those details and just use it like NoScript. There is a setting for this

Some weird things happened lately. My bank a/c password got changed, /et/resolv.conf  could not be modified as root and system was getting very slow.

Although rarely I sometimes used Tor but I made the mistake of not confining it within a chroot. That may be a possible cause. Port forwarding was enabled for 

Deluge. May be Deluge was compromised and ultimately the the entire filesystem,

I wiped out everything, no longer dual booting with Manjaro coz I don't wanna run any network facing app without apparmor.

I wanted a restrictive profile for my browser that the profile included by default. A member helped me out. Atm I am using FF with Noscript, Https Everywhere, 

Ghostery, WOT, Bluhell. I will be adding another 2GB of Ram very soon and replace bluhell with Adblock plus.

Now I can create apparmor profiles for myself. They may not be perfect but at least I can add some extra security for my /home apart from the root.

All the default apparmor profiles IMHO are designed mainly to protect the root and pays almost no attention to user's data.

I will create an apparmor profile for Chromium today and then try HTTPSwitchBoard.

Thanks.

---

