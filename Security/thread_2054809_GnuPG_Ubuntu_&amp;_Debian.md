---
title: "GnuPG Ubuntu &amp; Debian"
date: 2012-09-08
forum: Security
---

### Post by ek0s on 2012-09-08
Hi Everyone, 

I am a long time reader but first time poster at Ubuntu Forums. I am curious what eveyone thinks when it comes to keeping your private gpg key safe. 

Aside from a decent GPG password, full disk encryption (aes-cbc-essiv:sha256), and good defaults in .gnupg/gpg.conf before keys are created, is there anything else that you recommend?

Are there any reaons why Debian or Ubuntu might be better than the other when keeping your private keys safe and generating quality keys are ONLY things that matters? 

Even without a graphical environment (or something light, like openbox, so mouse movment can help /dev/random ??) Debian and Ubuntu ship with differnt softare. Ubuntu's apparmor seems to try protect dhclient, which is good thing since I want network access, but does Ubuntu have or Debian have any other software differnces that are significant? I have seen Ubuntu doing network things ( as seen by ```
sudo netstat -anp | grep -e tcp -e udp
``` or ```
sudo lsof -i
``` ), that are not dhclient (I don't have CUPs, Avahi, or auto updates), and I kind of don't like that, but don't know if that is rational. I am not a programmer.

---

### Post by thnewguy on 2012-09-08
If you are really paranoid about the safety of your private keys you could keep them on a separate drive, like a USB thumb drive. And keep that locked in a desk drawer or something. Or, for that matter, you could use a live CD (like Ubuntu or Knoppix) whenever you had to use your private keys and, again, keep your keys on a separate drive. To me that seems like over-kill, but it would keep your keys away from the network.

As for Debian or Ubuntu being better for security, neither is going to have a big advantage over the other. Ubuntu is based on Debian so you are basically using the same packages for the underlying system. Ubuntu just tries to set things up in a way that is easier for end users.

Chances are, if your disk is encrypted, your software is up to date and you are careful not to install software from outside the official repositories, you should be relatively safe.

---

### Post by mike acker on 2012-09-11
I think the real concern to look at here is the Thunderbird address space.  Clearly Thunderbird has access to your public and private keyrings -- through GnuPG

so the concern would be: if you open an e/mail that launches a java script ... and that java continues running instead of terminating -- maybe you just left that window open ?

and then you write a memo needing a signature...

now we have that java-script running ... while you access GunPG ... from the same active address space...    it is GnuPG that should be prompting you for the passphrase though and that should be running from "userland"... which should prevent the java-script from snooping

i think the "userland" aspect of Linux is very important to security and I need t learn more about it

---

