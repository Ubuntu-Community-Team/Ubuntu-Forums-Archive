---
title: "I wish add a delay between login attempts!"
date: 2009-05-30
forum: Security
---

### Post by enok on 2009-05-30
Hello!

As the title says i wish to add a delay between between inputting a password and getting confirmation/denial but inly when logging in through SSH.
This to slow down any bruteforce attacks.
I guess it's possible, but is it doable by myself... I have recently started my explorations of Linux!

It's a Ubuntu 8.04 server... no graphical interfaces, only terminal!

//Stefan

---

### Post by brian_p on 2009-05-30
> **enok said:**
> Hello!

As the title says i wish to add a delay between between inputting a password and getting confirmation/denial but inly when logging in through SSH.
This to slow down any bruteforce attacks.

I'd not bother taking any action myself as a brute force attempt against a good password is totally futile.

However, many people stop such probes in their tracks by using denyhosts. In any case, sshd doesn't provide the easy delay configuration you inquire about.

---

### Post by bodhi.zazen on 2009-05-30
> **enok said:**
> Hello!

As the title says i wish to add a delay between between inputting a password and getting confirmation/denial but inly when logging in through SSH.
This to slow down any bruteforce attacks.
I guess it's possible, but is it doable by myself... I have recently started my explorations of Linux!

It's a Ubuntu 8.04 server... no graphical interfaces, only terminal!

//Stefan

There are many things you can do including applications such as fail2ban or denyhosts.

personally I just add a "simple" rule to iptables -> after so many attempts an ip is blocked for so many minutes.

+ use ssh keys and disable password authentication altogether.

---

### Post by enok on 2009-06-02
OK thank you!

//Stefan

---

### Post by FlaHAM on 2009-06-02
You might consider changing the default port (22) to something else.
I had a rash of attempts to logon to my systems and moved the port number up to an address above the standard addresses. See /etc/services for the standard assignments. 

To accomplish the move.. edit /etc/ssh/sshd_config and change the line
for ports. Restart sshd to put the new port # into service.

---

### Post by sisco311 on 2009-06-02
Never tried myself, but I think you can set the delay in the /etc/pam.d/sshd file:
> auth  optional  pam_faildelay.so  delay=10000000 #=10 seconds

---

### Post by brian_p on 2009-06-02
> **sisco311 said:**
> ```


auth optional pam_faildelay.so delay=10000000 #=10 seconds
```



That works but another connection can always be opened, so whether it would slow down probes would depend on how they are conducted and how sshd is configured.

---

### Post by Trebaruna on 2009-06-03
If you're going to be logging in only from machines that are trustworthy and actually trusted (your own laptop, for instance) you may consider only allowing connections via keys. This way an attacker will automatically be denied access if she does not have the proper key.

Check out _[this wiki page]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")_ for more on how to set up key based access.

---

### Post by bodhi.zazen on 2009-06-03
> **Trebaruna said:**
> If you're going to be logging in only from machines that are trustworthy and actually trusted (your own laptop, for instance) you may consider only allowing connections via keys. This way an attacker will automatically be denied access if she does not have the proper key.

Check out _[this wiki page]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")_ for more on how to set up key based access.

Keys are portable. Put putty + keys on a flash drive.

Also, as you know, you need to then disable password authentication.

---

### Post by Trebaruna on 2009-06-03
> **bodhi.zazen said:**
> Keys are portable. Put putty + keys on a flash drive.
I know. But that doesn't mean you should put your private key onto every machine you find, that's why I suggested trustworthy and trusted machines. If you think you can trust your school's computers then go ahead. Just don't try and use your key on a machine in an internet cafe.

EDIT: And yes, I forgot to mention that in order for this to help get rid of pesky bruteforcers you need to disable password authentication. Sorry :)

---

