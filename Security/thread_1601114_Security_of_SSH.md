---
title: "Security of SSH"
date: 2010-10-19
forum: Security
---

### Post by Revengeofblu on 2010-10-19
Hi, I am very new to Ubuntu but have already fallen in love with it!  That being said I was having some issues with my network (people stealing my wifi) and my friend offered to install some stuff on my computer to make sure they were not getting back on.  I checked these programs out(not listing them on purpose) and they were all fine.  He told me a few steps to open up an SSH connection for him to help out.  I trust him completely, but I was wondering if having port forwarding on my router on and having an SSH client installed offered any major security threats from other users? I did a search in the forums for things related to this question but couldn't find anything.  I understand its frowned upon highly to double post and if I have done so my apologies.  It takes a bit to get used to a new forum and the right places to search!  -Thanks for your help!     :)

---

### Post by CharlesA on 2010-10-19
It would be so much simpler for you to just properly [secure yer wifi]("http://www.labnol.org/internet/secure-your-wireless-wifi-network/10549/") instead of having a friend "install some stuff" on yer PC.

Anyway, the default config of openSSH-server isn't that secure - 2 minute timeout, allows root logins, etc.

As long as you are using a strong password, you should be ok, but I prefer key auth, since they can't exactly be bruteforced.

---

### Post by WinstonChurchill on 2010-10-19
> **Revengeofblu said:**
> Hi, I am very new to Ubuntu but have already fallen in love with it!  That being said I was having some issues with my network (people stealing my wifi) and my friend offered to install some stuff on my computer to make sure they were not getting back on.  I checked these programs out(not listing them on purpose) and they were all fine.  He told me a few steps to open up an SSH connection for him to help out.  I trust him completely, but I was wondering if having port forwarding on my router on and having an SSH client installed offered any major security threats from other users? I did a search in the forums for things related to this question but couldn't find anything.  I understand its frowned upon highly to double post and if I have done so my apologies.  It takes a bit to get used to a new forum and the right places to search!  -Thanks for your help!     :)
SSH itself is pretty universally considered to be very secure. If you use password authentication, it's very important to make sure that you have a good password. Running SSH (or port-forwarding to it from) a non-standard port (like 19487, for example) will significantly cut down on the amount of crap you get from automated SSH scanners in China. (Why are they always from China? It's kind of amusing...)

The most secure way to go is to use public key authentication - but if you're planning on using this from many different computers, passwords are likely more convenient: just be certain that your passwords are not easily guessed.

---

