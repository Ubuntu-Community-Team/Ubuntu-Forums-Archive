---
title: "A general question about Apparmor profiles"
date: 2016-11-22
forum: Security
---

### Post by cogset on 2016-11-22
I've been reading around and trying to figure out Apparmor profiles for a while, yet I still can't quite grasp how do they work. 
I've also tried (some time ago) to use automated tools to generate a profile, but it resulted in something basically useless, a generic profile that didn't really do anything - as I've said, it was a while ago, things may have improved in the meantime but I'm not eager to try that again. 

 What I would really be interested in, would be instead a step-by-step breakdown of an Apparmor profile, something *clearly* explaining in detail what every line means in a sample profile, and ultimately how to build manually your custom profile for an application, like Firefox. 

 I do know that such a profile exists already, but as I've said I'd like to understand how this works and consequently write my own ruleset, furthermore the default profile is meant to confine the standard installation of Firefox, whilst I sometime use alternate installations in different paths - truth to tell, this would be the  very first thing I'd like to learn, i.e. *how to point an existing profile to a different binary*. 

 If there is some reading (aside from the sticky in this section) that I may want to have a look at, please feel free to point me in that direction - OTOH, if anyone here is willing to go over the basics in a concise way, I'd very much appreciate that.

---

### Post by cogset on 2016-12-19
I'll somehow bump this with a specific question: if I have a custom Firefox installation in /opt/firefox , how do I copy the existing default profile for the standard Firefox installation and modify it to point at my custom Firefox installation in /opt ?   I've tried to edit the usr.bin.firefox profile in etc/apparmor.d/ (first I've copied it to usr.bin.custom.firefox and then edited)  and changed the line ```
/usr/lib/firefox/firefox{,*[^s][^h]}
```  to  ```
/opt/firefox/firefox{,*[^s][^h]}
```  then tried to load such modified profile in complain mode, but even if it looks like Apparmor has loaded the new profile (I've checked using aa-status) then all I'm getting is a system error message at the next reboot, and no messages related to this new custom profile is visible in the logs.

---

### Post by &amp;KyT$0P# on 2016-12-19
Does [this thread]("https://ubuntuforums.org/showthread.php?t=2333298") help you at all?

---

