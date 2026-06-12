---
title: "Is it safer to copy-paste-follow a link than click the link in webpage?"
date: 2011-12-26
forum: Security
---

### Post by newhere_m on 2011-12-26
It so happens at times that after we register for some forum, an activation email is sent and we are asked to click a link provided to activate the account. If we are not sure about the credentials of the website, should we click the link provided or will it be safer to copy the link, paste in address bar and press 'enter'? Though it seems both are effectively same, I would like to get opinions of experts here. In general we are advised not to click on links provided in emails for security reasons. What is the best way to deal with such situations?

---

### Post by Dangertux on 2011-12-26
> **newhere_m said:**
> It so happens at times that after we register for some forum, an activation email is sent and we are asked to click a link provided to activate the account. If we are not sure about the credentials of the website, should we click the link provided or will it be safer to copy the link, paste in address bar and press 'enter'? Though it seems both are effectively same, I would like to get opinions of experts here. In general we are advised not to click on links provided in emails for security reasons. What is the best way to deal with such situations?

Presuming it's not a blind link. [One like this]("http://dangertux.wordpress.com") and the link text actually corresponds to where it's going [http://ubuntuforums.org](http://ubuntuforums.org) . Then it's no different to copy/paste versus click. Where you get in trouble is with the first type of link. Both will trigger your browser to perform a request, usually either GET or POST.

Of course, even a legitimate non-blind link can be abused if a man in the middle condition can be created. So I would say use your best judgement. If it's for something sensitive for instance paypal. They usually have a phone number you can call to verify the validity of the email. First call that number to verify, then call the official support number and reverify. Sometimes simple common sense is the best solution, and high tech methods are not needed. If it's for something trivial just exercise your best judgement, if the remainder of your security configuration is generally sound the amount of damage that can be done in this way should be adequately mitigated.

hope this helps.

---

### Post by mikewhatever on 2011-12-26
If you suspect a link is unsafe, don't click it, and don't copy/paste it.

---

### Post by newhere_m on 2011-12-26
Thanks. In case something bad really happens, can you please explain how this may happen (by clicking a link) and what security measures will mitigate this risk? (like apparmor/iptables etc)? A bit more detailed discussion will be helpful since I am yet to catch up with those advanced tools. I am already using no-script and adblockplus. Would you suggest any other add-on to counter such issues?

---

### Post by Ms. Daisy on 2011-12-26
Regarding your first question, someone answered that well enough in another thread:
[http://ubuntuforums.org/showpost.php?p=11566850&postcount=11](http://ubuntuforums.org/showpost.php?p=11566850&postcount=11)

And NoScript and Adblock are good to run. If you're looking for a detailed discussion, you can go here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by emiller12345 on 2011-12-26
if you copy and paste a link, you might be more apt to see any JavaScript embedded in the url, then if you just click on a link blindly.
+1 dt

---

