---
title: "[SOLVED] seriously confused on security"
date: 2008-06-01
forum: Security
---

### Post by minktheshrink on 2008-06-01
I read the security post about how much different security is between Ubuntu and Windows but does this mean I shouldnt be worried about viruses and other threats? If I should be worried what program should I get to scan my computer and how do I install it?

---

### Post by HalPomeranz on 2008-06-01
You don't need to worry about viruses in Ubuntu.

If you would like to run a program occasionally to check to see if your computer has been compromised (unlikely, but possible), you can use either chkrootkit or rkhunter (or both if you want, but it's largely redundant to do so).  Both are available via synaptic (or apt-get on the command-line).

You might also want to peruse the sticky "Ubuntu Security" thread at the top of this forum ([http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)).

---

### Post by tamoneya on 2008-06-01
one of the additional bonuses of the ubuntu repositories is that they are verified.  You arent just downloading some random binary file and installing it in blind faith.  Calling apt-get install is a very secure way of getting a program and only further adds to the security of your linux machine. 

I still scan for virii on my machine not because I fear getting infected myself but because I dont want to pass any infected files onto my windows using friends.  Im guessing they wouldnt be to happy if I did that and I dont really want to find out.

---

### Post by hyper_ch on 2008-06-01
havea  read here:  [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by Pjotr123 on 2008-06-02
I've published a simple explanation of Ubuntu security here:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

Hope this helps.

Greetz. Pjotr.

---

### Post by hyper_ch on 2008-06-02
your article is misleading. The firewall is not called "ufw" but "iptables".

---

### Post by Pjotr123 on 2008-06-02
> **hyper_ch said:**
> your article is misleading. The firewall is not called "ufw" but "iptables".

ufw is the control mechanism of IPtables, that's technically correct. Perhaps I will refine my text. -edit-: I have refined it.

Other reasons to call my article misleading? If none, I resent the term "misleading".

---

### Post by HermanAB on 2008-06-02
Why not just call it Netfilter as the Great Guru Rusty Russel intended?
:)

---

