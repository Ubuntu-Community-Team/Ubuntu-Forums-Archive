---
title: "On Clean Install of Trusty no ehrrr Precise"
date: 2014-07-25
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2014-07-25
For some time, the Update Manager had been offering new Hardware Updates. I tried on several occasions to sort it out. No luck. So, as July 24th had arrived, I thought 14.04.1 LTS (Trusty Tahr) would be available. 

I did a clean install of 12.04, updating the hardware, etc. Then I tried to install Tahr via terminal and upgrade -d. That balked. Mid-way through install time, I was told the install balked and asked permission to send a report with my password. I sent the report. I wish I hadn't. When Tahr finished the upgrade/updates something was wrong. I got a message about the Keyring password being different from -some other password- . The password now fails to get to past the login screen. 

So, netsearching I found what I thought was a way to reset the unix admin password in Ubuntu/Debian/14.04. Nope. Only from the Recovery Mode drop to Terminal could I use that password (what? Run Level 1?). Nowhere else. I posted a help request in Installation, but got but one reply about the "caps lock" being on. Trust me when I say: I wrote the password down before rebooting. I tried the new pw with, without and with the keyboard tilted sideways and caps and no caps, every which way before posting a help request for something seemingly so mundane.

I tried to fix the pw problem using a remount command string. I was seeing an "authentication token manipulation error" and eventually found a Launchpad entry with then 6, now 7 users reporting a problem.

I have long awaited Trusty. I guess I'll have to wait a few more days.

---

### Post by mooreted on 2014-07-25
I have never had much luck with upgrades, I always back up my data and do a clean install.

You probably already saw this one:

[http://askubuntu.com/questions/91188/authentication-token-manipulation-error](http://askubuntu.com/questions/91188/authentication-token-manipulation-error)

---

### Post by cariboo on 2014-07-26
Why not just do a clean install of 14.04.1, instead of installing 12.04 first?

---

### Post by pretty_whistle on 2014-07-26
> **cariboo907 said:**
> Why not just do a clean install of 14.04.1, instead of installing 12.04 first?

+1  That should solve it.

---

