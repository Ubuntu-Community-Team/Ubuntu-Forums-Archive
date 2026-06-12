---
title: "ssh password retry timeout required"
date: 2006-12-22
forum: Server Platforms
---

### Post by sitedesign on 2006-12-22
Is there a way of slowing down the ssh brute force attacks with a password retry timeout?

I have look for a setting in ssh_config that blocks connection for a timeout period if the password is entered incorrectly too many times.

I use webmin on my servers which has the ability to block hosts if they enter the wrong password password too many times.

Even a password retry delay would be good, so if the password is entered wrong then it waits for 30 seconds before allowing another try.

Any help appreciated.

---

### Post by MJN on 2006-12-22
I'm not sure there is - the problem is that whilst you may force a delay on consecutive attempts an attacker can mitigate this by opening multiple connections in parallel.... you're just moving the goalposts and potentially forcing an even worse situation.
 
Besides which, if you've got strong passwords then what have you got to worry about? Sure, it's not nice having someone banging on your door even if the door is locked - however if you really want to stop them block them at a higher level (at the front gate in my crappy analogy!) by using something like Fail2Ban or Denyhosts etc.
 
Mathew

---

