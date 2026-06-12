---
title: "Firefox hack scenario"
date: 2009-12-04
forum: Security
---

### Post by itmozart on 2009-12-04
How does firefox hacks from the internet general work?

If somebody exploits a vulnerability, generically speaking, will he be able to use my system through the user owning the firefox process (e.g. launching bash)?
How remote is the possibility that though a regular use of the net (I don't generally go into illegal sites etc.) somebody hacks into my computer? Same as being hit on the road (!!!)?
Is it reasonable to launch the firefox process as a user with limited permissions?

Thanks!
Saverio

---

### Post by cdenley on 2009-12-04
The chance of somebody getting root access to your system is very unlikely. If you allow random websites to execute javascript or flash programs on your system and don't enable an Apparmor profile for firefox, there is a possibility that your firefox profile can be corrupted. Technically, your home directory can also be modified, but malicious websites don't typically target linux systems.

---

### Post by itmozart on 2009-12-04
Thank you for the answer, I don't need any special security measure then - I specify though that even a non-root access to my home (that is, bash access as the firefox process owner) would be very harmful to me.

---

### Post by cdenley on 2009-12-04
> **itmozart said:**
> Thank you for the answer, I don't need any special security measure then - I specify though that even a non-root access to my home (that is, bash access as the firefox process owner) would be very harmful to me.

Well, there are occasionally vulnerabilities that could allow websites to execute arbitrary code such as executing a shell. Enabling an Apparmor profile would prevent this. It also usually requires that you allow flash or javascript. Such vulnerabilities tend to be cross-platform, and they almost always target Windows. It is unlikely that you will a visit a site that attempts to exploit a browser vulnerability, that vulnerability isn't patched in ubuntu, and they attempt to run linux-specific code to execute a command shell. It is a possibility, though, if you don't take "special security measures".

---

### Post by bodhi.zazen on 2009-12-04
There are vulnerabilities and patches reported for firefox on a regular basis :

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

See : [http://www.ubuntu.com/usn/USN-853-1](http://www.ubuntu.com/usn/USN-853-1)

Now it is possible that such a vulnerability allows shell access, and in that event you are in deep doggie-do.

Now you, the user, can make it worse, by say eliminating the need for sudo to ask for a password. It is amazing how many people stubbornly insist they are the only user with access to their systems, yet here they are, browsing the internet ...

Or you can make it more secure with things such as Apparmor. Starting with 9.10 there is *finally* an apparmor profile for firefox =)

In general, keep your system up to date ;)

---

